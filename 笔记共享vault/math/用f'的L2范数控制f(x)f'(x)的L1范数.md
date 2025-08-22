---
tags:
  - math
  - 微积分
---

> [!问题1]
> $f:[0,a]\to \mathbb{C}$,并且$f'$分段连续，并且$f(0)=0$，证明$$\int_0^a|f'(t)f(t)|\,dt\leq \frac{a}{2}\int_{0}^a |f'(t)|^2\,dt$$

$$\begin{aligned}|f(t)|&=|f(0)+\int_{0}^t f'(s)\,ds|\\&\leq \int_{0}^{t}|f'(s)|\,ds\end{aligned}$$如果假设$F(t):=\int_{0}^t |f'(s)|\,ds$于是这个函数满足：
1. $F(0)=0$
2. $|f(t)|\leq F(t)$
3. $F'(t)=|f'(t)|$

于是$$\begin{aligned}\int_0^a|f'(t)f(t)|\,dt&\leq \int_{0}^a F(t)F'(t)\,dt\\&= \int_{0}^a\frac{1}{2}(F^2(t))'\,dt\\&= \frac{1}{2}F^2(a)\end{aligned}$$而柯西不等式告诉我们：
$$\frac{1}{2}F^2(a)=\frac{1}{2}\left(\int_{0}^a |f'(t)|\,dt\right)^2\leq \frac{a}{2}\int_{0}^a |f'(t)|^2\,dt$$于是我们得到最终的不等式:$$\int_0^a|f'(t)f(t)|\,dt\leq \frac{a}{2}\int_{0}^a |f'(t)|^2\,dt$$

我们可以推广这个问题：

> [!命题1：问题1的推广]
> $f:[0,a]\to \mathbb{C}$,并且$f'$分段连续，并且$f(0)=0$，那么对于任意的$p\geq 1$都有$$\int_0^a|f'(t)||f(t)|^p\,dt\leq \frac{a^p}{p+1}\int_{0}^a |f'(t)|^{p+1}\,dt$$

我们可以重复同样的过程，
$$\begin{aligned}\int_0^a|f'(t)||f(t)|^p\,dt&\leq \int_{0}^a F^p(t)F'(t)\,dt\\&= \int_{0}^a\frac{1}{p+1}(F^{p+1}(t))'\,dt\\&= \frac{1}{p+1}F^{p+1}(a)\end{aligned}$$

利用Holder不等式，考虑$q=1+\frac{1}{p}$,这样就能得到$$\frac{1}{p+1}+\frac{1}{q}=1$$于是我们得到$$\begin{aligned}\frac{1}{p+1}F^{p+1}(a)&=\frac{1}{p+1}\left(\int_{0}^a |f'(t)|\,dt\right)^{p+1}\\&\leq \frac{1}{p+1}\left(||1||_{q}\cdot||f'||_{p+1}\right)^{p+1}\\&=\frac{1}{p+1}a^{\frac{p+1}{q}}\int_{0}^a |f'(t)|^{p+1}\,dt\\&=\frac{a^p}{p+1}\int_{0}^a |f'(t)|^{p+1}\,dt\end{aligned}$$