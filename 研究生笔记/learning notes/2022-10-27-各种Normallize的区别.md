[详解深度学习中的Normalization，BN/LN/WN - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/33173246)
## 1、BatchNormalization

对于给定的输入 $X=\begin{bmatrix}x_1\\x_2\\...\\x_N\end{bmatrix}$, 
 $$
 \begin{align}

& \mu=\frac{1}{N}\sum_{k=1}^N x_k  &  v=\frac{1}{N}\sum_{k=1}^N (x_k-\mu)^2 \\

& \sigma=\sqrt{v+\epsilon}         &  y_i=\frac{x_i-\mu}{\sigma}

\end{align}
 $$
反向传播

![[Pasted image 20221027173017.png]]
最终

![[Pasted image 20221028161324.png]]

## Inline Question 1:

Describe the results of this experiment. How does the weight initialization scale affect models with/without batch normalization differently, and why?

## Answer:

有Batch normalization后、模型对初值没有像之前那么敏感，在较大的区间之内都能有比较好的性能

没有Batch normalization的模型对初始值敏感、只在1e-2~1e-1之间有不错的表现

## Inline Question 2:
![[Pasted image 20221028162246.png]]
Describe the results of this experiment. What does this imply about the relationship between batch normalization and batch size? Why is this relationship observed?


## Answer:

[FILL THIS IN]
Batchsize越大、batch normalization的效果越好。
因为Batchsize越大越接近整个数据集的分布、batchsize得到的均值和方差也就更接近真实数据的分布


## 2、**Layer Normalization —— 横向规范化**