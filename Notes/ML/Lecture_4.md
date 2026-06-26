---
tags:
  - 机器学习
  - 笔记
---
## 4-1 多功能
> Multiple features
> Multivariate linear regression 多元线性回归

$n$：特征数量
$x^{(i)}$：第 i 个训练样本的输入特征值 - vector
$x^{(i)}_j$：第 i 个训练样本中第 j 个特征值
Hypothesis：
$$
\begin{aligned}
h_\theta(x) &= \theta_0 + \theta_1 x_1 + \theta_2 x_2 + ... + \theta_n x_n \\
&= \theta^\intercal x
\end{aligned}
$$
+ 添加 $x^{(i)}_0 = 1$

## 4-2 多元梯度下降法
Cost function：
$$
J(\theta) = J(\theta_0,\theta_1,...,\theta_n) = \frac{1}{2m} \sum^{m}_{i = 1} (h_\theta(x^{(i)}) - y^{(i)})^2
$$
Gradient descent：
$$
\theta_j := \theta_j - \alpha \underbrace{\frac{1}{m} \sum^{m}_{i = 1} (h_\theta(x^{(i)}) - y^{(i)}) x_j^{(i)}}_{\frac{\partial}{\partial \theta} J(\theta)}
$$

### 4-2-1 特征缩放
> Feature Scaling

Make sure features are on a similar scale.
将特征值的取值约束到 $-1 \le x_i \le 1$（接近这个范围），能==更快收敛==
**均值归一化** mean normalization
$$
x_j := \frac{x_j - \mu_j}{s_j}
$$
+ $\mu_j$：$x_j$ （特征值）的平均值
+ $s_j$：特征值的范围：$\max - \min$

### 4-2-2 学习率
如果 $J(\theta)$ 在上升，或反复上下，梯度下降没有工作，应当使用更小的 $\alpha$
只要 $\alpha$ 足够小，$J(\theta)$ 一定会下降。但太小会导致收敛很慢

## 4-3 特征和多项式回归
可以自由选择特征或将特征的组合运算作为新的特征
可以使用更复杂的函数拟合数据

## 4-4 [[最小二乘法|正规方程]]
### 4-4-1 区别于迭代方法的直接解法
> Normal equation
> Method to solve for $\theta$ analytically

能更好（一步）的求出 $\theta$ 最优质的方法
+ 梯度下降是迭代求法
ecost function：$J(\theta) = a \theta^2 + b \theta + c$
使代价函数最小化的 $\theta$：$\theta = (X^\intercal X)^{-1} X^\intercal y$
> [!tip]-
> **使用正规方程不需要特征缩放，不需要 $\alpha$  学习率**，但是当特征数量大（$n \ge 10000$）时，矩阵的逆运算计算很慢，更适合用梯度下降法

### 4-4-2 矩阵不可逆
1. 查看特征中是否有多余特征，比如两个特征之间存在线性关系
2. 检查是否有过多的特征，样本数少于特征数


