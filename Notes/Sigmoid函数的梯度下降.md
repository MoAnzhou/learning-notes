> 吴恩达机器学习 6-5 导数推导

Sigmoid： $g(z) = \frac{1}{1 + e^{-z}}$
$$
h_\theta(x) = g(\theta^\intercal x) = \frac{1}{1 + e^{-\theta^\intercal X}}
$$
$$
\begin{align}
J(\theta) &= \frac{1}{m} \sum_{i=1}^{m} Cost(h_\theta(x^{(i)}),y^{(i)})\\
&=-\frac{1}{m} \sum_{i=1}^{m} [ y^{(i)} \log(h_\theta(x^{(i)})) + (1 - y^{(i)}) \log(1 - h_\theta(x^{(i)})) ]\\
J(\theta) &= -\frac{1}{m} \sum_{i=1}^{m} [y^{(i)} \log(g(z^{(i)})) + (1 - y^{(i)}) \log(1 - g(z^{(i)}))]
\end{align}
$$
简写：$G = y \log(g(z)) + (1 - y) \log(1 - g(z))$
求导：
$$
\begin{align}
\frac{dG}{d\theta} &= \frac{dG}{dz} \frac{dz}{d\theta} \\
\end{align}
$$
$$
\begin{align}
\frac{dG}{dz} &= \frac{d}{dz} [y \log(g(z)) + (1 - y) \log(1 - g(z))] \\
&= \frac{y \frac{dg(z)}{dz}}{g(z)} - \frac{(1 - y) \frac{dg(z)}{dz}}{1 - g(z)} \\
&= \frac{[y - g(z)] \; \frac{dg(z)}{dz} }{g(z) \; [1 - g(z)]} \\
\frac{dz}{d\theta} &= x
\end{align}
$$
其中：
$$
\begin{align}
\frac{dg(z)}{dz} &= \frac{d}{dz} \frac{1}{1 + e^{-z}} \\
&= \frac{e^{-z}}{(1 + e^{-z})^2} \\
&= \frac{1}{1 + e^{-z}} · (1 - \frac{1}{1 + e^{-z}}) \\
\frac{dg(z)}{dz} &= g(z)·[1 - g(z)]
\end{align}
$$
带回 $\frac{dG}{dz}$：
$$
\begin{align}
\frac{dG}{dz} &= \frac{[y - g(z)] \; \frac{dg(z)}{dz} }{g(z) \; [1 - g(z)]} \\
&= y - g(z)
\end{align}
$$
梯度下降：
$$
\begin{align}
\theta_j :&= \theta_j - \alpha \frac{\partial}{\partial \theta_j}J(\theta) \\
&= \theta_j - \frac{\alpha}{m} \sum_{i = 1}^{m} [h_\theta(x^{(i)}) - y^{(i)}] x_j^{(i)}
\end{align}
$$
