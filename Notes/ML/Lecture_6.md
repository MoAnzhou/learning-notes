---
tags:
  - 机器学习
  - 笔记
---
## 6-1 分类
二分类：$y \in \{0, 1\}$
Logistic Regression Model Want：$0 \le h_\theta(x) \le 1$
- **逻辑回归**是一种<u>分类算法</u>

## 6-2 假设陈述
==Sigmoid function==(Logistic function)：$g(z) = \frac{1}{1 + e^{-z}}$
![[Excalidraw/Drawing 2026-06-27 15.31.40.excalidraw|200]]
Hypothesis：
$$
h_\theta(x) = g(\theta^\intercal x) = \frac{1}{1 + e^{-\theta^\intercal X}}
$$
二分类问题：
$$
P(y = 0 | x;\theta) + P(y = 1 | x;\theta) = 1
$$

## 6-3 决策界限
> decision boundary

当 $\theta^\intercal X \ge 0$ 时，$h_\theta(x) = g(\theta^\intercal x) \ge 0.5$，此时分类为 $y = 1$.
> [!tip]-
决策界限是假设函数的属性，取决于其参数，不是数据集的属性

## 6-4 代价函数
以[[Lecture_2#^541c51|平方误差函数]]作为代价函数，在逻辑回归中会变成参数 $\theta$ 的**非凸函数**，存在很多局部收敛点
> non-convex function

Logistic regression cost function：
$$
Cost(h_\theta(x),y) = \begin{cases} 
-\log(h_\theta(x)) & if \; y=1 \\
-\log(1 -h_\theta(x)) & if \; y=0
\end{cases}
$$
![[Excalidraw/Drawing 2026-06-27 17.49.20.excalidraw|600]]
以 $y=1$ 为例：
1. 当 $h_\theta(x)=1$ 时，$cost = 0$，预测准确；
2. 当 $h_\theta(x) \to 0$ 时，$cost \to \infty$，即预测 $P(y = 1 | x;\theta) = 0$，$y=1$ 的概率为 $0$。但事实上 $y=1$，我们需要用非常大的代价值惩罚这个学习算法。

## 6-5 简化代价函数与梯度下降
$y$ 的取值只有 $1,0$，将两个式子合并：
$$
cost(h_\theta(x),y) = -y \log(h_\theta(x)) - (1 - y) \log(1 - h_\theta(x))
$$
logistic 回归的代价函数：
$$
\begin{align}
J(\theta) &= \frac{1}{m} \sum_{i=1}^{m} Cost(h_\theta(x^{(i)}),y^{(i)})\\
&=-\frac{1}{m} \sum_{i=1}^{m} [ y^{(i)} \log(h_\theta(x^{(i)})) + (1 - y^{(i)}) \log(1 - h_\theta(x^{(i)})) ]
\end{align}
$$
> 极大似然函数




## 6-6 高级优化

