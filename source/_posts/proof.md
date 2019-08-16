---
title: proof
date: 2019-08-14 13:52:56
tags:
---
Some mathmatics proof
* Binomial distribution
<!--more-->

## Binomial distribution

$$
p(x)=C_k^nn^p(n-k)^{(1-p)}=\frac{n!}{k!(n-k)!}p^k(1-p)^{(n-k)}
$$

$$
\begin{align}
E(x)&=\sum_{k=1}^{n}k\frac{n!}{k!(n-k)!}p^k(1-p)^{(n-k)} \\
&= \sum_{k=1}^{n}k\frac{n(n-1)!}{k(k-1)!(n-k)!}p p^{k-1}(1-p)^{(n-k)} \\
&= np\sum_{k=1}^{n}\frac{(n-1)!}{(k-1)!(n-k)!}p^{k-1}(1-p)^{(n-k)}
\end{align}
$$

Let $a = k-1$, $b=n-1$ $\Rightarrow k=a+1, n=b+1$ 
$$
\begin{align}
E(x)&= np\sum_{k=1}^{n}\frac{(n-1)!}{(k-1)!(n-k)!}p^{k-1}(1-p)^{(n-k)} \\
&= np\sum_{a=0}^{b}\frac{b!}{a!(b-n)!}p^{a}(1-p)^{(b-a)} 
\end{align}
$$
Where $\sum_{a=0}^{b}\frac{b!}{a!(b-n)!}p^{a}(1-p)^{(b-a)}$ is the sum of all the probabilities which equals to 1.

Hence the $E(x)$ is $np$ 