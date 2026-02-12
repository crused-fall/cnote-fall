---
tags:
  - math
  - 微积分
  - 考研
---

> [!question] 问题0（考研数学1）
> $f\in C[0,1]$并且满足$$\left|\int_0^x \frac{f(t)}{\sqrt{x-t}}\,dt\right|\leq 1,\forall x\in [0,1]$$求$|\int_0^1 f(t)\,dt|$的最佳上界。

### 1. Abel变换角度的解答

#### 1.1 Abel逆变换表示$f(t)$

我们从一般的角度上来考虑“问题0”：

> [!tip] 基本想法
> 考虑一个关于$f$的积分变换$T$，其形式为:$$(Tf)(x):=\int_{t_1}^{t_2}f(t)K(t,x)\,dt$$现在假设我们知道$Tf$的（一致）上界$$\sup_{x\in [x_1,x_2]}|(Tf)(x)|\leq M$$然后我们要使得线性泛函$$L(f):=\int_{x_1}^{x_2} f(t)\,dt$$
> 绝对值的最大化。
> 
> 一个基本的想法是，如果积分变换可逆，比如说积分核$K$存在逆，也就是说我们有$$f(t)=\int_{x_1}^{x_2}(Tf)(x)K^{-1}(x,t)\,dx$$那么如此一来就可以得到$L(f)$的一个上界$$|L(f)|\leq M\int_{t_1}^{t_2}\int_{x_1}^{x_2}|K^{-1}(x,t)|\,dx\,dt$$然后我们去验证这样得到的上界是否是最佳上界。

此处“问题0”当中涉及的积分核为Abel变换的积分核，其逆变换有命题：

> [!note] 命题1
> $f\in C[0,1]$并且满足$$g(x):=\int_0^x \frac{f(t)}{\sqrt{x-t}}\,dt$$那么$$f(x)=\frac{1}{\pi}\frac{d}{dx}\int_0^x \frac{g(u)}{\sqrt{x-u}}\,du$$

借助这个结果，令$H(x):=\int_0^x \frac{g(u)}{\sqrt{x-u}}\,du$，那么$$\int_{0}^{1}f(x)\,dx = \frac{1}{\pi}H(1)=\frac{1}{\pi}\int_{0}^{1}\frac{g(u)}{\sqrt{1-u}}\,du$$其中我们知道$\sup_{x\in [0,1]}|g(x)|$小于等于1,于是我们知道$$\left|\int_{0}^{1}f(x)\,dx\right|\leq \frac{1}{\pi}\int_{0}^{1}\frac{1}{\sqrt{1-u}}\,du=\frac{2}{\pi}$$然后我们要证明$\frac{2}{\pi}$是最佳上界，相当于说明$\frac{2}{\pi}$为集合$$S:=\{|L(f)|:f\in C[0,1],\sup_{x\in [0,1]}|g(x)|\leq 1\}$$的上确界为$\frac{2}{\pi}$。我们现在确实证明了$\frac{2}{\pi}$为其上界，那么其究竟是否为上界呢？

> [!tip] 想法1.1.1
> 如果我确实可以找到这样一个具体的$f_0$使得$L(f_0)=\frac{2}{\pi}$那么自然这就是$S$的上确界。这样一来相当于要求$g(x)=1$，根据Abel Inversion此时的$f_0$应该是$\frac{1}{\pi\sqrt{x}}$，但是这样的函数并不属于$C[0,1]$。那么此时我们还想到一种情况，如果我们可以找到一列$f_n(x)\in C[0,1]$使得$L(f_n)$收敛到$L(f_0)$，那么我们同样可以证明$\frac{2}{\pi}$就是$S$的上确界。

这里逼近的目标函数是$\frac{1}{\pi\sqrt{x}}$，其符合要求的主要原因是因为$x=0$的位置不好。那么一个可以借鉴的经验来自于：[[复三角多项式在Lp空间中的稠密性#2. $C( mathbb{T} to mathbb{C})$在$C([a,b] to mathbb{C})$当中是稠密]]。就是说我们构造一个分段函数$$f_n(x):=\begin{cases}\frac{1}{\pi\sqrt{x}}&x\in [\frac{1}{n},1]\\\frac{n^{3/2}}{\pi}x&x\in [0,\frac{1}{n})\end{cases}$$![[把不连续的函数变得连续.png]]
这样构造相当于在$t= \frac{1}{n}$处强行截断$\frac{1}{\pi\sqrt{x}}$，然后把断开的部分用与原点连接的一条线段替代，从而使得$f_n(x)$一方面保持连续性，另一方面满足$\int_{0}^1|f_n(x)-f_0(x)|\,dx \to 0$，从而使得$L(f_n)\to \frac{2}{\pi}$。

#### 1.2 证明Abel Inversion（“命题1”）

实际上这类逆变换公式的推导大体上的思路是差不多的，因为积分变换差不多都可以看作是$f$与积分核的卷积，我们要做的就是再做一次类似的卷积，然后在Fubini定理的意义下交换积分，从而得到关于$f$的积分表达式。

此处Abel变换的诀窍在于，再做一次同核的卷积：
$$g(x):=\int_0^x \frac{f(t)}{\sqrt{x-t}}\,dt=\int_{\mathbb{R}} \frac{f(t)}{\sqrt{x-t}} 1_{0\leq t\leq x\leq 1}\,dt$$那么同核的卷积就是$$\begin{aligned}\int_{0}^x \frac{g(u)}{\sqrt{x-u}}\,du&= \int_{\mathbb{R}} \frac{g(u)}{\sqrt{x-u}}1_{0\leq u\leq x\leq 1}\,du\\&= \int_{\mathbb{R}}\int_{\mathbb{R}}f(t)(u-t)^{-1/2}(x-u)^{-1/2}1_{0\le t\leq u\leq 1}1_{0\leq u\leq x\leq 1}\,dt \,du\\&= \int_{\mathbb{R}}f(t)\int_{\mathbb{R}}(u-t)^{-1/2}(x-u)^{-1/2}1_{0\le t\leq u\leq x\leq 1}\,du \,dt\\&= \int_{0}^{x}f(t)\left(\int_{t}^{x}(u-t)^{-1/2}(x-u)^{-1/2}\,du \right)\,dt \end{aligned}$$
* 中间利用Fubini定理交换了积分次序。

现在我们准备化简中间的积分$\int_{t}^{x}(u-t)^{-1/2}(x-u)^{-1/2}\,du$。首先想到的是，我们可以对区间$[t,x]$中的变量$u$进行伸缩变换把积分区间变成$[0,1]$。于是令$$u=(x-t)v+t,v\in [0,1]$$从而$v=\frac{u-t}{x-t}$。对原来的积分做变量替换得到$$\begin{aligned}\int_{t}^{x}(u-t)^{-1/2}(x-u)^{-1/2}\,du&=\int_{0}^{1}v^{-1/2}(1-v)^{-1/2}\,dv\\&=B(1/2,1/2)=\pi\end{aligned}$$于是原本的积分就变成了$$\int_{0}^x \frac{g(u)}{\sqrt{x-u}}\,du=\pi\int_{0}^x f(t)\,dt$$所以我们得到$$f(x)=\frac{1}{\pi}\frac{d}{dx}\int_0^x \frac{g(u)}{\sqrt{x-u}}\,du$$


