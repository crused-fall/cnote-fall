---
tags:
  - math
  - 数论
---

> [!问题1]
> 函数$$g(n):= \begin{cases}1&\text{n is square-free}\\0&\text{otherwise}\end{cases}$$是square-free的整数的特征函数。定义
> $$S(N)=\frac{1}{N}\sum_{n\leq N}g(n)$$求$S(N)$的渐近表达，要求精度为$o(1)$。


### 1. 问题1的解答

我们发现其实可以把这个判断是否为square-free的函数表达为一个新的求和:
$$g(n) = \sum_{ d^2|n} \mu(d)$$
* 因为假设$n=m^2r$,那么如果$d^2|n$那么$d|m$那么于是$$\sum_{ d^2|n} \mu(d)=\sum_{d|m}\mu(d)=1*\mu(m)=e(m)$$其中$$e(x):=\begin{cases}1&x=1\\0& \text{otherwise}\end{cases}$$因此当$m=1$的时候，$n$是square-free的整数，此时和的结果为1,否则n不是square-free，此时和的结果为0.于是就证明了上面的结果。
* 这里的$g(n)$还可以表示为$\mu(n)^2$。因为$\mu$除了判断$n$是否square-free，其次还要判断$n$里面有多少个不同的素因子，不过取平方以后则变成了单纯判断是否square-free。

$$\begin{aligned}S(N)&=\frac{1}{N}\sum_{n\leq N}\sum_{d^2|n}
\mu(d) \\ &= \frac{1}{N}\sum_{n\leq N} \sum_{d\leq N}
\mu(d)1_{d^2|n}(d) \\&= \frac{1}{N}\sum_{d\leq
N}\mu(d)\sum_{n\leq N}1_{d^2|n}(d) \\ &=
\frac{1}{N}\sum_{d\leq
N}\mu(d)\left\lfloor\frac{N}{d^2}\right\rfloor
=\frac{1}{N}\sum_{d\leq
\sqrt{N}}\mu(d)\left\lfloor\frac{N}{d^2}\right\rfloor \\&=
\sum_{d\leq
\sqrt{N}}\frac{\mu(d)}{d^2}+O\left(\frac{1}{N}\sum_{d\leq
\sqrt{N}}\mu(d)\right) \\ &=
\frac{6}{\pi^2}+O\left(\frac{1}{\sqrt{N}}\right)\end{aligned}$$
* 其中倒数第二行我们用到了$$\sum_{d\leq x}\mu(d)=o(x)$$这等价于“素数定理”。


* 按照概率数论当中的语言来表述这个问题就是，所有square-free的自然数这个集合对应的natrual density 或者asmyptotic density是多少? 按照该问题的结论，我们知道其natrual density是$\frac{1}{\zeta(2)}=\frac{6}{\pi^2}$.
* 如果定义$M(g):=\lim_{x\to \infty}\frac{1}{x}\sum_{n\leq x}g(n)$，那么根据上面的结果，我们知道$M(g)=M(\mu^2)=\frac{6}{\pi^2}$。

### 2.对"问题1"的推广：k-free的整数的密度

定义一个函数，$$g_k(n):= \begin{cases}1&\text{n is k-free}\\0&\text{otherwise}\end{cases}$$所谓$k$-free($k\geq 2$),就是说不存在某个非1的整数$m$使得$m^k|n$。

我们现在要计算，$$S_k(N)=\frac{1}{N}\sum_{n\leq N}g_k(n)$$和上面一样的思路，我们把$g_k$通过Dirichlet卷积展开为一个和。利用和1.2类似的证明，可以验证$$g_k(n)=\sum_{d^k|n}\mu(d)$$于是$$\begin{aligned}S(N)&=\frac{1}{N}\sum_{n\leq N}\sum_{d^k|n}
\mu(d) \\ &= \frac{1}{N}\sum_{n\leq N} \sum_{d\leq N}
\mu(d)1_{d^k|n}(d) \\&= \frac{1}{N}\sum_{d\leq
N}\mu(d)\sum_{n\leq N}1_{d^k|n}(d) \\ &=
\frac{1}{N}\sum_{d\leq
N}\mu(d)\left\lfloor\frac{N}{d^k}\right\rfloor
=\frac{1}{N}\sum_{d\leq
N^{1/k}}\mu(d)\left\lfloor\frac{N}{d^k}\right\rfloor \\&=
\sum_{d\leq
N^{1/k}}\frac{\mu(d)}{d^k}+O\left(\frac{1}{N}\sum_{d\leq
N^{1/k}}\mu(d)\right) \\ &=
\frac{1}{\zeta(k)}+O\left(N^{1-\frac{1}{k}}\right)\end{aligned}$$