---
title: The exponential family
date: 2019-08-06 11:21:35
tags:
math: true
---
Introduction of exponential family
<!--more-->
# The exponential family

$$
p(y;\eta) = b(y) exp(\eta^T T(y) - \alpha(\eta))
$$

where
* $\eta$ is natural parameter
* $T(y)$ is sufficient statistic
* $\alpha(\eta)$ is log partition function

If $T(y) = y$, then we want to know $E(y|x)$. Hence the expected outcome $y=E(y|x)=h(x)$ 


## Gaussian distribution

$$
\begin{aligned}
p(y,\mu)&=\frac{1}{\sqrt{2\pi}}exp(-\frac{(y-\mu)^2}{2}) \\
&= \frac{1}{\sqrt{2\pi}} exp(-\frac{1}{2}y^2+y\mu -\frac{1}{2}\mu ^2) \\
&= \frac{1}{\sqrt{2\pi}} exp(-\frac{1}{2}y^2)exp(y\mu-\frac{1}{2}\mu ^2)
\end{aligned}
$$

Hence 
$$
\begin{aligned}
b(y)&=\frac{1}{\sqrt{2\pi}} exp(-\frac{1}{2}y^2) \\
\eta&=\mu \\
T(\mu) &= y \\
\alpha &= \frac{1}{2}\mu^2
\end{aligned}
$$
