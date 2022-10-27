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

## 2、**Layer Normalization —— 横向规范化**