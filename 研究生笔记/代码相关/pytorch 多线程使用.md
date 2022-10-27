```python
import os

import cv2 as cv

import warnings

from mp4Writer import VideoWriter

from multiprocessing import Pool

import threading

warnings.simplefilter("always")

from tqdm import tqdm

root = "/data02/v-yinc/Gopro/1/videos"

def get_lists(path):

    lists = os.listdir(path)

    lists.sort()

    return [path + '/' + file for file in lists]

def generateVideo(imagesPath,savePath,fps):

    print

    images = get_lists(imagesPath)[5400:]

    print(f"There {len(images)} images now!!!")

    img = cv.imread(images[0])

    print(img.shape)

    height, width, c = img.shape

    vw = VideoWriter(savePath, width, height,fps)

    font = cv.FONT_HERSHEY_SIMPLEX

    for i in tqdm(range(len(images)-1)):

        img = cv.imread(images[i])

        # if i % 2==1:

        #     gt = cv.imread(images[i])

        #     cv.putText(img, f'VFI {fps} fps', (50, height-100), font, 2, (0,0,255), 2)

        #     frame = cv.hconcat([gt,img])

        #     vw.write(frame)

        # else:

        #     gt = cv.imread(images[i+1])

        #     cv.putText(img, f'VFI {fps} fps', (50, height-100), font, 2, (0,0,255), 2)

        #     frame = cv.hconcat([gt,img])

        #     vw.write(frame)

        vw.write(img)

    vw.close()

    print(f"gererated {savePath}")

def worker(video):

    imagesPath = root + "/" + str(video)

    savePath = f"{root}/{video}.mp4"

    generateVideo(imagesPath,savePath,30)

if __name__=="__main__":

    videos = os.listdir(root)[3]

    print(videos)

    pool = Pool(processes=2)

    pool.map_async(worker, videos)

    pool.close()

    pool.join()
```