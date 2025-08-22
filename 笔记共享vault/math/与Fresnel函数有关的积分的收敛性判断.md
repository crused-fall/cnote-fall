---
tags:
  - math
  - 微积分
  - 考研
---

> [!问题]
> 判断积分收敛性$$\int_{1}^{\infty}\sin(x^2)dx$$

实际上我们通过换元法，可以问题可以转换为$$f(x):=\int_{1}^x \frac{|\sin(u)|}{2\sqrt{u}}du$$以及$$g(x):=\int_{1}^x \frac{\sin(u)}{2\sqrt{u}}du$$做估计。其中我们要证明$f(x)$无下界，以及$g(x)$的渐近展开具有形式$$g(x)=A+o(1)$$
### 1. 绝对收敛性

$$f(x) =
\int_{1}^{x}\frac{|\sin(u)|}{2\sqrt{u}}du$$类似的带有周期的积分都可以三步走(把积分转换为求和来做估计),对于$N_x=\lceil x\rceil$都有:
$$\begin{aligned}\int_{1}^{x}\frac{|\sin(u)|}{2\sqrt{u}}du
&>
\sum_{k=1}^{N_x}\int_{k\pi}^{k\pi+\pi}\frac{|\sin(u)|}{2\sqrt{u}}du
\\
&=\sum_{k=1}^{N_x}\int_{0}^{\pi}\frac{|\sin(s)|}{2\sqrt{k\pi
+s}}ds \\ &=
\int_{0}^{\pi}\sum_{k=1}^{N_x}\frac{|\sin(s)|}{2\sqrt{k\pi
+s}}ds \\ &>\int_{0}^{\pi}|\sin(s)|\frac{1}{2\sqrt{\pi}} ds
\sum_{k=2}^{N_x+1}\frac{1}{\sqrt{k}}\\&=
\frac{1}{\sqrt{\pi}}\sum_{k=2}^{N_x+1}\frac{1}{\sqrt{k}}\end{aligned}$$由于最后的求和是一个不收敛的技术的部分和，因此此积分不是绝对收敛的。

### 2.条件收敛的判断:

1. 针对变形以后的形式，
$$\int_{1}^{x}\frac{\sin(u)}{2\sqrt{u}}\,du =
\frac{1}{2}\cos(1)-\frac{1}{4}\int_{1}^{x}\frac{\cos(u)}{u^{3/2}}du
$$
后者绝对收敛，因此积分是条件收敛的。用分部积分的办法剥离掉一些对收敛性不影响的，最后留下一个容易判断收敛性的项目的办法和用渐近展开判断积分绝对收敛性是类似的想法。

2. 当然还有更简单的做法，直接用Abel -Dirichlet判别，因为这是两个函数相乘的积分，而且意识到其中有一个单调收敛到0。而另一个是有界的，因此符合判别要求的条件，于是最后得到结果是条件收敛的。此外Abel - Dirichlet判别当中用到的是，**第二积分中值定理**。对于一些更复杂的，但是不好直接使用Abel -Dirichlet判别的问题，可以从积分中值定理入手。

