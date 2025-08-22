---
tags:
  - math
  - 微积分
---
### 1. 想法的来源

> [!问题1.1]
> 求不定积分$$\int e^x\sin(x)\,dx$$

一个常见的做法是利用分部积分公式。这里我们换一种视角，如果我们从欧拉公式入手：

> [!引理1.2：欧拉公式]
> $$e^{ix}=\cos(x)+i\sin(x)$$

我们考虑$e^{ix}e^x$的不定积分。这个积分是容易的，因为它可以写成$$e^{(i+1)x}$$通过理解$e^z$的导数的结果，我们很容易得到:

> [!引理1.3：指数函数的不定积分]
> $\omega \in \mathbb{C},\omega\neq 0$那么
> $$\int e^{\omega x}\,dx = \frac{1}{\omega}e^{\omega x}+C$$

回到"问题1.1",利用"引理1.3"我们得到$$\int e^{(i+1)x}\,dx = \frac{1}{i+1}e^{(i+1)x}+C$$同时被积函数可以利用欧拉公式拆开，从而得到$$\int e^{(i+1)x}\,dx = \int \cos(x)e^x\,dx +i\int \sin(x)e^x\,dx$$而积分结果也可以通过欧拉公式进行实部与虚部的分离，从而得到$$\frac{1}{i+1}e^{(i+1)x}=\frac{1}{2}e^x(\cos(x)+\sin(x))+i\left[\frac{1}{2}e^x(-\cos(x)+\sin(x))\right]$$
于是我们得到:
1. $$\int e^x\sin(x)=\frac{1}{2}e^x(-\cos(x)+\sin(x))+C$$
2. $$\int e^x\cos(x)=\frac{1}{2}e^x(\cos(x)+\sin(x))+C$$
带着这样的想法我们来看下面的问题：

> [!问题1.4]
> 求不定积分：
> $$\int x\sin(x)e^x\,dx,\int x\cos(x)e^x\,dx$$

按照上面同样的想法，考虑
$$f(x):=xe^{ix}e^x=xe^{(i+1)x}$$通过通常的分部积分法，我们得到$$\int f(x)\,dx = -\frac{i}{2}e^{(i+1)x}((1+i)x-1)+C$$
而$f(x)$可以写成$$f(x)=x\cos(x)e^x+ix\sin(x)e^x$$那么其不定积分还可以写成是$$\int x\cos(x)e^x\,dx +i\int x\sin(x)e^x\,dx $$
所以通过分离实部与虚部，我们得到:
3. $$\int x\cos(x)e^x\,dx =\frac{1}{2}e^x(x\cos(x)-\sin(x)+x\sin(x))+C$$
4. $$\int x\sin(x)e^x\,dx =\frac{1}{2}e^x(\cos(x)-x\cos(x)+x\sin(x))+C$$
> [!问题1.5]
> 求不定积分：
> $$\int x\cos(2x)\sin(x)e^x\,dx$$

我们此处需要稍微变通一下，需要对欧拉公式与$\sin(x)$有一个新的理解。

> [!引理1.6 ]
> 令$\sinh(x):=\frac{e^{x}-e^{-x}}{2},\cosh(x):= \frac{e^{x}+e^{-x}}{2}$于是由欧拉公式可以得到$$-i\sinh(ix)=\sin(x),\cosh(ix)=\cos(x)$$

这样我们就可以处理被积函数当中同时有$\sin,\cos$并且相乘的技术困难。因为只要我们把被积函数转换为多个$P(x)e^{\omega x}$（其中$P(x)$是多项式）的形式，那么我们就可以通过重复使用分部积分法来解决问题。最后我们把所有的积分结果加起来就是最终的结果。

现在我们考虑函数$$g(x):=x(-i\sinh(ix))(\cosh(2ix))e^x$$我们把这个函数按照$e^{\omega x}$的形式展开，于是得到$$g(x)=-\frac{i}{4}xe^{(3i+1)x}+\frac{-i}{4}xe^{(1-i)x}+\frac{i}{4}xe^{(1+i)x}+\frac{i}{4}xe^{(1-3i)x}$$
因为后面我们需要多次重复利用同一个积分，这里我们不妨直接计算出其公式来，$$\int xe^{\omega x}\,dx = \frac{1}{\omega^2}(\omega x-1)e^{\omega x}+C$$
于是经过一番机械式的复数运算，我们得到$$\begin{aligned}\int g(x)\,dx &=\frac{1}{100}e^x\left[(25x-1)\cos(x)+(-15x+3)\cos(3x)-25x\sin(x)+(5x+4)\sin(3x)\right]\end{aligned}$$
所以我们总结一下思路：

> [!思路1.7：通过欧拉公式计算不定积分的技巧]
> 首先我们可以通过不断分部积分得到如下形式的不定积分$$\int P(x)e^{\omega x}\,dx$$其中$\omega \in \mathbb{C},\omega\neq 0$以及$P(x)$是一个多项式。而如果我们遇到形如$$\int P(x)\left(\prod_m \sin(a_mx)^{t_m}\right)\left(\prod_j \cos(b_jx)^{r_j}\right)e^{cx}\,dx$$的不定积分。我们可以通过$$-i\sinh(ia_mx)^{t_m}=\sin(a_mx)^{t_m},\cosh(ib_jx)^{r_j}=\cos(b_jx)^{r_j}$$把上述积分变成有限个$\int P(x)e^{\omega x}\,dx$形式的积分的线性组合，最后通过欧拉公式化简便可以得到最后的积分的结果。结果形如$$e^x\left(\sum_{i}p_i(x)\sin(\gamma_ix)+q_i(x)\cos(\gamma_ix)\right)+C$$
> 当然如果被积对象是特殊的，例如$P(x)\cos(ax)e^x,P(x)\sin(ax)e^x$的形式，我们不必用$\sinh,\cosh$去替换，而是可以直接考虑$\int P(x)e^{\omega x}\,dx$的积分，然后取其中的实部或者虚部，正如“问题1.1”，“问题1.4”中那样处理。

