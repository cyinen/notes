## 优化

无脑上Adam、大部分情况不会差

使用预先处理好的特征可能效果要比直接使用原始数据更好（可以把传统的图像处理方法用来做数据预处理）

Empirical rule of thumb: If you increase the batch size by N, also scale the initial learning rate by N

lr应该随着Batchsize增大

