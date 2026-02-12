---
tags:
  - math
  - 数论
---

> [!question]  问题1
> $d(n)$是数论当中的divisor function，估计：$$F(x):=\sum_{n\leq x}\frac{d(n)}{n}$$要求精度至少为$o(1)$。

### 1. [[Dirichlet's hyperbola trick]]

首先基于[[把条件函数展开为新的求和然后换序#1.1 卷积法的基本形式]]我们把$d$表示为Dirichlet卷积的形式，即$d=1*1$，于是$$F(x)=\sum_{n\leq x}\frac{d(n)}{n}=\sum_{n\leq x}\frac{1}{n}\sum_{q|n}1$$令$rq=n$，这样我们便能把$F(x)$表示为适合使用Dirichlet hyperbola方法的形式$$\begin{aligned}F(x)&=\sum_{n\leq x}\frac{1}{n}\sum_{q\leq x}1_{q|n} \\&= \sum_{q\leq x}\sum_{qr\leq x,r\leq x}\frac{1}{qr}\\&= \sum_{q,r\le x,qr\leq x}\frac{1}{qr}\end{aligned}$$然后其中我们知道$\sum_{q\leq x}\frac{1}{q}=\sum_{r\leq x}\frac{1}{r}=H(x)$的渐近结果，参考[[自然数的r次幂的部分和估计#3. $r=1$的情况]]$$H(x)=\log(x)+\gamma+O(1/x)$$于是Dirichlet Hyperbola方法告诉我们，对于$1\leq y\leq x$有$$F(x)=\sum_{q\leq y}\frac{1}{q}H(x/q)+\sum_{r\leq x/y}\frac{1}{r}H(x/r)-H(y)H(x/y)$$
为了简单起见，这里直接选择$y=\sqrt{x}$从而$$\begin{aligned}F(x)&=2\sum_{q\leq \sqrt{x}}\frac{1}{q}H(x/q)-H(\sqrt{x})^2 \end{aligned}$$其中$$\begin{aligned}\sum_{q\leq \sqrt{x}}\frac{1}{q}H(x/q)&=H(\sqrt{x})\log(x)-\sum_{q\leq \sqrt{x}}\frac{\log(q)}{q}+\gamma H(\sqrt{x})+O(1/\sqrt{x})\\&= \frac{1}{2}\log^2(x)+\gamma\log(x)+O\left(\frac{\log(x)}{\sqrt{x}}\right)\\&-\frac{1}{8}\log^2(x)+\frac{1}{2}\gamma\log(x)+\gamma^2\\&= \frac{3}{8}\log^2(x)+\frac{3\gamma}{2}\log(x)+\gamma^2-\gamma_1+O\left(\frac{\log(x)}{\sqrt{x}}\right)\end{aligned}$$
* 此处这里我们用Euler-Maclaurin公式（[[和的积分估计#2.如果函数是光滑的，那么则有更好的估计，即Euler-Maclaurin求和估计]]）得到对$\sum_{q\leq \sqrt{x}}\frac{\log(q)}{q}$的估计，得到$$\sum_{q\leq \sqrt{x}}\frac{\log(q)}{q}=\frac{1}{8}\log^2(x)+\gamma_1+O\left(\frac{\log(x)}{\sqrt{x}}\right)$$其中$\gamma_1$是[Stietjes常数](https://en.wikipedia.org/wiki/Stieltjes_constants)的其中一个，更一般的常数可以定义为$$\gamma_n = \lim_{k\to \infty} \left(\sum_{q\leq k}\frac{\log^n(q)}{q}-\int_1^k \frac{\log^n(t)}{t}\,dt\right)$$此处就是$n=1$的情况，而欧拉常数$\gamma=\gamma_0$。

然后
$$H(\sqrt{x})^2= \frac{1}{4}\log^2(x)+\gamma\log(x)+\gamma^2+O\left(\frac{\log(x)}{\sqrt{x}}\right)$$

合起来我们得到$$F(x)=\frac{1}{2}\log^2(x)+2\gamma\log(x)+\gamma^2-2\gamma_1+O\left(\frac{\log(x)}{\sqrt{x}}\right)$$

### 2. Hyperbola方法结合连续分部求和法

因为目标和具有$\sum_n \frac{a_n}{n}$的形式，那么如果我们知道$a_n$的和的足够精确的渐近估计，那么$\sum_n \frac{a_n}{n}$的精度也就可以达标。但实际上这个做法依旧绕不开Dirichlet hyperbola method，因为$$\begin{aligned}D(x):=\sum_{n\leq x}d(n) = x\log(x)+x(2\gamma-1)+R(x)\end{aligned}$$其中$R(x)=O(\sqrt{x})$就是用hyperbola method得到的。

建立在这个结果的基础上，我们得到$$\begin{aligned}F(x)&=\frac{D(x)}{x}+\int_1^x \frac{D(t)}{t^2}\,dt\\&= \log(x)+(2\gamma-1)+\frac{R(x)}{x}\\&+\frac{1}{2}\log^2(x)+(2\gamma-1)\log(x)+\int_{1}^{\infty} \frac{R(t)}{t^2}\,dt -\int_{x}^{\infty}\frac{R(t)}{t^2}\,dt \\&=\frac{1}{2}\log^2(x)+2\gamma\log(x)+C+O(1/\sqrt{x}) \end{aligned}$$其中$C=2\gamma-1+\int_{1}^{\infty}\frac{R(t)}{t^2}\,dt$。

这个方法理论上来说可以得到比第一节中的渐近结果更精确的余项$O(1/\sqrt{x})$但是，因为$R(t)$本身并不容易计算从而导致常数项$C$，不像第一节当中那么容易计算。毕竟Stieltjes常数是有着高效率的计算方法的。

不过由于两种方法本质上都是得到了精度为$o(1)$的渐近展开，那么常数项必然相等，也就是说$$C=\gamma^2-2\gamma_1$$于是我们最终得到了更精确的结果$$F(x)=\frac{1}{2}\log^2(x)+2\gamma\log(x)+\gamma^2-2\gamma_1+O\left(\frac{1}{\sqrt{x}}\right)$$
* 这里也体现了，用两种不同方法对同一个对象渐近展开从更好地确定一些渐近系数地思路。