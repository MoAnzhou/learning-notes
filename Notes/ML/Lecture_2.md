---
tags:
  - 机器学习
  - 笔记
---
## 2-1 模型描述
$m$：训练集样本数
$x$：输入
$y$：输出
$h_\theta(x) = \theta_0 + \theta_1 x$：Hypothesis

## 2-2 代价函数
> The cost function

在 linear regression 中，修改 $\theta_0、\theta_1$ 使 $h(x)$ 更好的拟合数据
+ 关于 $\theta_0、\theta_1$ 对函数 $J(\theta_0,\theta_1)$ 求最小值

**平方误差函数**：解决<u>回归问题</u>最常用手段
如果直接把误差相加会正负相互抵消，所以需要把误差平方 ^541c51
+ Cost function
$$
J(\theta_0,\theta_1) = \frac{1}{2m} \sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})^2
$$
+ Goal
$$
\underset{\theta_0,\theta_1}{\text{min}} \ \underbrace{J(\theta_0,\theta_1)}_{cost \ function}
$$

## 2-3 梯度下降
> Gradient descent algorithm

repeat until convergence $\theta_j := \theta_j - \alpha \frac{\partial}{\partial \theta_j} J(\theta_0,\theta_1)$
$\alpha$：learning rate
+ $\alpha$ 过大可能无法收敛
> [!warning]- Correct
> Simultaneous update $\theta_0$ and $\theta_1$

靠近局部最低点，slope 减小，移动的幅度会自动变得越来越小
+ So, no need to decrease $\alpha$ over time

![[Pasted image 20260623214219.png|480]]
=="Batch" Gradient Descent==
+ "Batch": Each step of gradient descent uses all the training examples
