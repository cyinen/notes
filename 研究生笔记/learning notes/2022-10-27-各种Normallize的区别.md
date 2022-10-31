[详解深度学习中的Normalization，BN/LN/WN - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/33173246)

## 1、BatchNormalization

BatchNorm技术是用来加速网络训练的，手段就是通过“Reducing Internal Covariate Shift（减小内部协变量偏移）

主要是用来解决梯度消失的问题

对于给定的输入 $X=\begin{bmatrix}x_1\\x_2\\...\\x_N\end{bmatrix}$, 
 $$
 \begin{align}

& \mu=\frac{1}{N}\sum_{k=1}^N x_k  &  v=\frac{1}{N}\sum_{k=1}^N (x_k-\mu)^2 \\

& \sigma=\sqrt{v+\epsilon}         &  y_i=\frac{x_i-\mu}{\sigma}

\end{align}
 $$
为了不降低模型的表达能力、使用了$\gamma$和$\beta$ 
$$y_o=\gamma * y_i + \beta$$
反向传播

![[Pasted image 20221027173017.png]]

#### BatchNorm 在不同layer上的作用效果

![[Pasted image 20221030160659.png]]

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

### BatchNorm的优缺点如下
	- 需要较大的batch以体现整体数据分布
	- 训练阶段需要保存每个batch的均值和方差，以求出整体均值和方差在infrence阶段使用
	- 不适用于可变长序列的训练，如RNN
## 2、**Layer Normalization —— 横向规范化**

对每一个$X_i$进行归一化，对样本就行归一化、与整体的数据无关

克服了 *BatchNorm*的第一个缺点、需要较大的batchsize, 不依赖batchsize
同样存在可以学习的参数$\gamma$和$\beta$
但是只是在特征维度上进行缩放


![[Pasted image 20221030160954.png]]