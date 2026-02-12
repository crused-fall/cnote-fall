---
tags:
  - tool_idea
  - math
---

***这是一种非常特殊的方法，并不通用。*** 此方法首先基于Dirichlet卷积法，假设$f=g*h$然后我们已知$g$的和$G(x):=\sum_{a\leq x} g(a)$的估计,以及$h$的和$H(x):=\sum_{a\leq x} h(a)$的估计，现在想要得到$F(x):=\sum_{a\leq x} f(a)$的估计。参照卷积法的思路，但是中间对和的处理不同$$\begin{aligned}F(x)=\sum_{n\leq x}f(n)&=\sum_{n\leq x}\sum_{d|n}g(d)h(n/d)\\&= \sum_{n\leq x}\sum_{qd=n}g(d)h(q)\\&= \sum_{\begin{aligned}q,d&\leq x\\qd&\leq x \end{aligned}}g(d)h(q)\end{aligned}$$
* 这里也可以写成是$$F(x)=\sum_{q,d\leq x}g(d)h(q)1_{qd\leq x}$$
* 所有这种$g*h$卷积的和的估计都可以用Dirichlet hyperbola方法来优化估计结果。
* 值得注意的是，这样的一个双重求和并不能直接写成累次求和，主要是因为限制条件$1_{qd\leq x}$这个条件的限制。因此我们有必要去理解$(q,d)$对应的几何区域，从而想办法把双重求和写成累次求和的形式，从而利用一些已知的和来提升整体估计的精度。

此时的和$F(x)$相当于我们是在一个如下图的区域当中的所有整数格点上取二元函数值$g(d)h(q)$然后求和。

![[dirichlet hyperbola method figure.png]]
(图中我们把横轴设定为d,纵轴设定为q。中间蓝色正方形的区域是$d\leq y,q\leq \frac{x}{y}$的部分)

* 此处选择一个$1\ll y\ll x$的另一个原因是为了提升估计的精度。因为在逐项估计中，我们主要是利用“底乘以高”的方式来得到和的上界。对于数论函数而言，每一个对象的逐项放缩的高我们很难改进，因为这些函数往往很复杂。但是底我们可以进行改进，如果我们选用一个增长速度远低于$x$的随着$x$变大而变大的$y$作为逐项估计的底，那么整体逐项估计的误差还能下降到更小。

==为了把二元的求和转换为一元的求和==，同时想到，我们可以让被求和对象进行累次求和来实现我们的目的。于是我们想到下面的技巧：

我们可以把求和分为三个部分的组合，分别是$$\sum'=\sum_{d\leq y}\sum_{q\leq x/d},\sum''=\sum_{q\leq \frac{x}{y}}\sum_{d\leq x/q},\sum'''=\sum_{d\leq y}\sum_{q\leq \frac{x}{y}}$$于是根据图形的对称性,以及$\sum',\sum''$当中都包含了$\sum'''$当中的点，于是上图中所有整个格点的数目应该是$$\sum_{\begin{aligned}q,d&\leq x\\qd&\leq x \end{aligned}}1 = \sum'+\sum''-\sum'''$$那么当我们的数论函数$g(d)h(q)$在这样的区域上求和的时候，我们也可以做这样的估计,从而使得$$\begin{aligned}F(x)&= \sum_{\begin{aligned}q,d&\leq x\\qd&\leq x \end{aligned}}g(d)h(q)\\&= \sum_{d\leq y}\sum_{q\leq x/d}g(d)h(q)+\sum_{q\leq \frac{x}{y}}\sum_{d\leq x/q}g(d)h(q)-\sum_{d\leq y}\sum_{q\leq \frac{x}{y}}g(d)h(q) \\&=\sum_{d\leq y}g(d)H(x/d)+ \sum_{q\leq \frac{x}{y}}h(q)G(x/q)-G(y)H(x/y)\end{aligned}$$
现在**我们实现了“把二元求和转换为一元求和”的目的，但也为此付出了代价**，这个代价就藏在$G(y)H(x/y)$当中。

* 常见情况下，我们会选择$y=\sqrt{x}$从使式子变得更为简单$$F(x)=\sum_{d\leq \sqrt{x}}g(d)H(\sqrt{x})+\sum_{q\leq \sqrt{x}}h(d)G(\sqrt{x})-G(\sqrt{x})H(\sqrt{x})$$

---

一些具体的应用：
* [[对算术函数平均值的渐近#1.2 用 Dirichlet's hyperbola trick 改进误差]]：在这里我们需要估计$$\sum_{n\leq x}d(n)=\sum_{\begin{aligned}dq&\leq x\\q,d&\leq x\end{aligned}}1$$于是想到借助hyperbola's trick，相当于$h(x)=g(x)=1$然后$H(x)=G(x)=\lfloor x\rfloor$，并未为了使得最后的误差最小化令$y=\sqrt{x}$从而最后得到$$\begin{aligned}\sum_{n\leq x}d(n) &= \sum_{d\leq \sqrt{x}}g(d)H(\sqrt{x})+\sum_{q\leq \sqrt{x}}h(d)G(\sqrt{x})-G(\sqrt{x})H(\sqrt{x})\\&=x\log(x)+x(2\gamma-1)+O(\sqrt{x})\end{aligned}$$
* [[divisor函数的倒数加权和的估计#1. Dirichlet hyperbola 方法]]:此处我们需要对估计$$\begin{aligned}F(x)&=\sum_{n\leq x}\frac{d(n)}{n}=\sum_{q,r\le x,qr\leq x}\frac{1}{qr}\end{aligned}$$于是想到利用hyperbola's trick，并令$$\sum_{q\leq x}\frac{1}{q}=\sum_{r\leq x}\frac{1}{r}=H(x)$$于是$$F(x)=\sum_{q\leq y}\frac{1}{q}H(x/q)+\sum_{r\leq x/y}\frac{1}{r}H(x/r)-H(y)H(x/y)$$并且令$y=\sqrt{x}$优化误差和简化渐近式子，最后得到$$F(x)=\frac{1}{2}\log^2(x)+2\gamma\log(x)+\gamma^2-2\gamma_1+O\left(\frac{\log(x)}{\sqrt{x}}\right)$$此外如果有限对$\sum_{n\leq x}d(n)$利用hyperbola's trick然后再借助分部求和，最终可以得到更好的余项。