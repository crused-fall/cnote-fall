---
tags:
  - math
  - 数论
  - 实分析
  - 丢番图逼近
---
> [!序列均匀分布的概念]
> 实数列$u_n$称之为在闭区间$[a,b]$上均匀分布(uniformly distributed/equidistributed)的,如果$$\lim_{N\to \infty}\frac{|\{n:1\leq n\leq N ,u_n \in [c,d]\}|}{N}=\frac{d-c}{b-a}$$其中$[c,d]\subseteq [a,b]$，即前$N$个序列$u_n$当中的落在闭区间$[c,d]$当中的元素的个数。

> [!实数模1的概念]
> 实数$x$可以表示为$$x=E(x)+\varepsilon(x)$$其中$E(x)$是一个整数,$\varepsilon(x) \in [-\frac{1}{2},\frac{1}{2})$称之为实数$x$模1的余数。

* 这里和通常的“整数模整数”的习惯不同，$\varepsilon(x)$并非是实数$x$减去其下整或者上整的结果，而是$x$减去离$x$最近的整数的结果。比如$2.8$可以表示为$3+(-0.2)$,此时$-0.2 \in [-\frac{1}{2},\frac{1}{2})$，因此$\varepsilon(2.8)=-0.2$。这样定义不同于通常的$\{x\}=x-\lfloor x\rfloor$的定义，这样定义下$\{x\}\in [0,1)$。
* 我们还可以定义一个实数模$a>0$的余数。我们可以把实数$x$表示为$$x=E_a(x)+\varepsilon_a(x)$$其中$E_a(x)\in a\mathbb{Z}$,$\varepsilon_a(x)\in [-\frac{a}{2},\frac{a}{2})$。因为$\frac{E_a(x)}{a}\in \mathbb{Z},\frac{\varepsilon_a(x)}{a}\in [-\frac{1}{2},\frac{1}{2})$,于是我们立刻能知道$$\varepsilon\left(\frac{x}{a}\right)=\frac{\varepsilon_a(x)}{a}$$

> [!序列模1均匀分布的概念]
> 实数列$u_n$称之为模1均匀分布的,如果$$\lim_{N\to \infty}\frac{\nu(a,b,N;u_n)}{N}=b-a$$其中$[a,b]\subseteq [-1/2,1/2]$。此处$$\nu(a,b,N;u_n):=|\{n:\varepsilon(u_n)\in [a,b],1\leq n\leq N\}|$$表示序列$u_n$模$1$形成的序列$\varepsilon(u_n)$的前$N$项目落在闭区间$[a,b]$中的个数。

* 如果是模$r>0$的序列是否均匀分布问题，我们可以稍做处理把它转换为模1是否均匀分布的问题。比如假设我们想要研究序列$\varepsilon_{\pi}(n)$是否在$[-\frac{\pi}{2},\frac{\pi}{2})$当中均匀分布，即$n$模$\pi$是否均匀分布，因为$\varepsilon_{\pi}(n)=\varepsilon\left(\frac{n}{\pi}\right)$，那么$[a,b]\subseteq [-\frac{\pi}{2},\frac{\pi}{2})$当中有多少个$\varepsilon_{\pi}(n),n\leq N$的元素，实际上等于$[a',b']\subseteq [-\frac{1}{2},\frac{1}{2})$中$\varepsilon\left(\frac{n}{\pi}\right),n\leq N$的元素的个数。于是$n$是否模$\pi$均匀分布，实际上就是$\frac{n}{\pi}$是否模1均匀分布。


对于模1均匀分布概念的直观的感受：
1.  **比稠密性更强**：假设$\xi_n$是一个模1均匀分布的序列，那么集合$A=\{\xi_n:n\geq1\}$在$[-\frac{1}{2},\frac{1}{2})$当中是稠密的。因为显然任意开区间$(a,b)\cap A$都是一个无限的交集。
2.  **均匀分布**：落在任何一个开区间当中的元素的占比最后极限都一样，也就是说没有哪个地方多或者少，基本都"差不多"。

什么样的序列是模1均匀分布的？我们试图从反面来理解这个概念：

> [!非均匀分布的例子]
> 简单的例子$u_n=\frac{1}{n}$,其模1以后，$$\varepsilon(u_1)=0,\varepsilon(u_1)=-\frac{1}{2},\varepsilon(u_n)=\frac{1}{n},n\geq 3$$首先这个序列组成的集合根本不在$[-1/2,1/2)$中稠密，比如考察$[-1/2,0]$这样一个区间当中，其中只包含$-1/2$这样一个元素，那么序列在此区间当中比例的极限为0，而不是$1/2$。

那如果序列模1后在$[-\frac{1}{2},\frac{1}{2})$当中稠密，有可能不是模1均匀分布的吗？

> [!非模1均匀分布的例子2]
> 假设$r_n$是对$[-\frac{1}{2},\frac{1}{2})$之间的有理数的一种枚举方式。然后定义$$\xi_n:=\begin{cases}r_{n}&100|n\\0&\text{otherwise}\end{cases}$$比如考察区间$[\frac{1}{4},\frac{1}{5}]$，前$N$个序列$\xi_n$的元素当中有不超过$N/100$个元素落在此区间里面。于是最后比例的极限肯定是小于等于区间长度$1/4-1/5 = 1/20$的。不过和之前的例子不同的是，此序列在$[-\frac{1}{2},\frac{1}{2})$当中是稠密的。
> 
> 这里我们虽然用$100|n$这个条件增加了$\xi_n =0$的频率，减少了其落在$[-\frac{1}{2},0),(0,\frac{1}{2})$的频率，但是因为有理数的稠密性，序列$\xi_n$对应的集合依旧是稠密的。

### 1. 一个充要条件：Weyl判别

#### 1.1 Weyl判别的叙述

> [!Weyl判别,1916]
> 以下三者等价：
> 1.  $u_n$模1均匀分布
> 2.  对于任意非零整数$k$    $$\frac{1}{N}\sum_{n=1}^{N}e^{2\pi ik u_n}\to0$$
> 
>  3.  对于任意连续函数$f:[-\frac{1}{2},\frac{1}{2}]\to\mathbb{C}$有$$\frac{1}{N}\sum_{n=1}^{N}f(\varepsilon(u_n))\to\int_{-1/2}^{1/2}f(x)dx$$

* 有的地方对实数$x$模1的余数的定义是$\{x\}\in [0,1)$的，那么最后的条件相应的就需要修改为$$\frac{1}{N}\sum_{n=1}^{N}f(\{u_n\})\to\int_{0}^{1}f(x)dx$$
 * 关于第三点，也可以拓展为对任意黎曼可积的函数成立，但不能扩展其为更广义的积分。例如假设现在考虑Lebesgue可积，定义集合$A=\{\xi_n,\xi_n>0\text{ and }n=1,2....\}$,$1_{A}(x)$是集合的特征函数，那么显然是L可积的。然而式子的左边$\frac{1}{N}\sum_{n=1}^{N}1_A(\xi_n)=1$,式子的右边因为$A$可数因此零测度，所以积分为0。（闭区间$[0,1]$上L可积未必R可积，但是如果R可积，那么一定L可积并且相等)
 * 关于第二点在验证的时候可以只验证$k>0$的情况。因为如果$$\sum_{n=1}^{N}e^{2\pi ik u_n}=o(N),\forall k\in \mathbb{Z}^{+}$$那么我们很容易验证对$k$为负整数的时候成立，因为$k$为相反的整数的时候，整个和与原来的和之间的关系是复共轭的。共轭复数之间的模是相等的，于是也满足条件2。
 * 最终常用于验证序列模1均匀分布的条件是第二条，因为如果序列是给定的，带有具体信息的，那么我们可以把问题转换为对指数和的具体估计的问题。


#### 1.2 用三角多项式一致逼近函数：$2\iff 3$

> [!引理1.2.1]
> $f\in C(\mathbb{T}\to \mathbb{C})$那么对任意的$\varepsilon>0$存在一个多项式$P_{\varepsilon}(z)$使得$$||f-P_{\varepsilon}||_{u}<\varepsilon$$

* 此处的多项式形如$$P(z):=\sum_{|k|\leq K}c_{k}z^k,z\in \mathbb{T},c_k \in \mathbb{C}$$这种定义在单位圆周上的多项式称之为三角多项式。之所以称之为三角多项式是因为，如果我们把单位圆周上的复数给参数化(当然这里有很多种参数化的方式)，比如令$z = e^{2\pi i x}=e(x)$，那么现在可以得到一个实变量的函数$$T(x):=P(e(x))=\sum_{|k|\leq K}c_{k}e^{2\pi i kx},x \in [0,2\pi)$$这就是其称之为三角多项式的原因。


我们可以验证所有这样的三角多项式上定义加法，乘法，数乘并且装备上一致范数，构成$C(\mathbb{T}\to \mathbb{C})$的一个Banach子代数，记为$\mathcal{P}$并且满足[[Stone-Weierstrass定理]]的条件：
1. $\mathcal{P}$是一个$*-\text{sub algebra}$。这里注意，$z \in \mathbb{T}$是非常重要的，因为只有在单位圆周上的复数才能满足$\overline{z}=z^{-1}$,从而实现对共轭的封闭性。
2. $\mathcal{P}$分离$\mathbb{T}$上的点。这一点同样很重要，如果不是在单位圆周上而是某一个包含一个周期的区间上，那么三角多项式就无法分离一个周期的两个端点。
3. $\mathcal{P}$在$\mathbb{T}$上不消失。

于是由[[Stone-Weierstrass定理]]，我们知道$\mathcal{P}$在$C(\mathbb{T}\to \mathbb{C})$上是稠密的。当然这是软分析的证明，我们还可以具体构造出来逼近的函数，这在某些需要定量分析的情况下会有用处，可以参考[[复三角多项式在Lp空间中的稠密性]]当中的证明。


> [!引理1.2.2]
> $f\in C([-1/2,1/2]\to \mathbb{C})$并且满足$f(-1/2)=f(1/2)$那么对任意的$\varepsilon>0$存在一个三角多项式$P_{\varepsilon}\in \mathcal{P}$使得我们可以定义$T_{\varepsilon}(x):=P_{\varepsilon}(e^{2\pi i x})$使得
> $$||f-T_{\varepsilon}||_{u}<\varepsilon$$

* 此引理正是由引理1.2得到。因为满足条件的连续函数一定可以找到对应的单位圆周上的函数$F \in C(\mathbb{T}\to \mathbb{R})$然后$F$可以被单位圆周上的多项式$P_{\varepsilon}$逼近，最后给单位圆周上的元素参数化，于是便得到了三角多项式$T_{\varepsilon}(x)$对$f$的一致逼近。

我们考虑闭区间上端点取值相同的连续被三角多项式逼近的原因是因为，我们可以在Weyl判别当中的函数$f \in C([-1/2,1/2]\to \mathbb{C})$的基础上构造函数$F(x):=f(\varepsilon(x))$，这是一个连续且在端点处取值相同的函数。于是对任意的$\varepsilon>0$可以找到一个三角多项式$$T_{\varepsilon}(x):=\sum_{|k|\leq K_{\varepsilon}} c_{k,\varepsilon}e(kx)$$使得$$\sup_{x\in [-1/2,1/2]}|F(x)-T_{\varepsilon}(x)|<\varepsilon$$而三角多项式$T_{\varepsilon}(x)$可以验证满足Weyl判别的等价条件3，因为$$\begin{aligned}\frac{1}{N}\sum_{n=1}^{N}T_{\varepsilon}(u_n)&=\sum_{|k|\leq
K_{\varepsilon}}
c_{k,\varepsilon}\frac{1}{N}\sum_{n=1}^{N}e(ku_n)\end{aligned}$$由于Weyl判别的等价条件2，于是如果我们对$N$取极限，我们会发现$$\frac{1}{N}\sum_{n=1}^{N}T_{\varepsilon}(u_n)\to c_{0,\varepsilon}$$而一致收敛导致积分的收敛，因此我们知道$$\left|\int_{-1/2}^{1/2} F(x)\,dx-\int_{-1/2}^{1/2} T_{\varepsilon}(x)\,dx\right|<\varepsilon$$其中:
1. $$\int_{-1/2}^{1/2} F(x)\,dx=\int_{-1/2}^{1/2} f(\varepsilon(x))\,dx=\int_{-1/2}^{1/2} f(x)\,dx$$
2. $$\int_{-1/2}^{1/2} T_{\varepsilon}(x)\,dx=c_{0,\varepsilon}$$因为在$[-1/2,1/2]$内$e(kx),k\neq 0$的积分为0。

于是我们知道$$\begin{aligned}\left|\frac{1}{N}\sum_{n=1}^{N}F(u_n)-\int_{-1/2}^{1/2} F(x)\,dx\right|&\leq \left|\frac{1}{N}\sum_{n=1}^{N}F(u_n)-\frac{1}{N}\sum_{n=1}^{N}T_{\varepsilon}(u_n)\right|\\&+\left|\frac{1}{N}\sum_{n=1}^{N}T_{\varepsilon}(u_n)-\int_{-1/2}^{1/2} F(x)\,dx\right|\\&<\left|\frac{1}{N}\sum_{n=1}^{N}F(u_n)-\frac{1}{N}\sum_{n=1}^{N}T_{\varepsilon}(u_n)\right|+\varepsilon\\ &<\frac{1}{N}\sum_{n=1}^{N}|F(u_n)-T_{\varepsilon}(u_n)|+\varepsilon \\ &<2\varepsilon\end{aligned}$$对任意$\varepsilon>0$成立。因此我们验证了Weyl判别当中的$2\implies 3$。当然$3\implies 2$就很简单了，只需要对连续函数$\cos(2\pi k x),\sin(2\pi k x)$验证第三个条件，于是就能得到等价条件2。

#### 1.3 用连续函数逼近黎曼可积函数：$3\implies 1$

> [!引理1.3.1]
> $f$是$[-1/2,1/2]$上实值的黎曼可积的函数，那么对任意$\varepsilon>0$存在一个$g_{\varepsilon} \in C([-1/2,1/2]\to \mathbb{C})$使得$$\int_{-1/2}^{1/2}|f(x)-g_{\varepsilon}(x)|\,dx<\varepsilon$$

* 如果一来我们就可以把Weyl判别中的等价条件3中的连续函数推广到黎曼可积函数。

我们现在的目标是估计$$S_{N,\varepsilon}:=\frac{1}{N}\sum_{n=1}^{N}|f(\varepsilon(u_n))-g_{\varepsilon}(\varepsilon(u_n))|$$因为$\varepsilon(u_n)$是$[-1/2,1/2)$当中的$N$个值，那么$S_{N,\varepsilon}$实际上可以看作是$|f(x)-g_{\varepsilon}(x)|$在$[-1/2,1/2]$上的一个黎曼和。那么根据黎曼可积的Darboux判别(参考[[黎曼积分的定义以及黎曼可积的判别]])，于是$$\limsup_{N\to \infty}S_{N,\varepsilon}\leq \int_{-1/2}^{1/2}|f(x)-g_{\varepsilon}(x)|\,dx<\varepsilon$$$$\begin{aligned}\left|\frac{1}{N}\sum_{n=1}^{N}f(\varepsilon(u_n))-\int_{-1/2}^{1/2} f(x)\,dx\right|&\leq \left|\frac{1}{N}\sum_{n=1}^{N}f(\varepsilon(u_n))-\frac{1}{N}\sum_{n=1}^{N}g_{\varepsilon}(\varepsilon(u_n))\right|\\&+\left|\frac{1}{N}\sum_{n=1}^{N}g_{\varepsilon}(\varepsilon(u_n))-\int_{-1/2}^{1/2} g_{\varepsilon}(x)\,dx\right|\\&<\left|\frac{1}{N}\sum_{n=1}^{N}f(\varepsilon(u_n))-\frac{1}{N}\sum_{n=1}^{N}g_{\varepsilon}(\varepsilon(u_n))\right|+\varepsilon\\ &<S_{N,\varepsilon}+\varepsilon \end{aligned}$$如果两边取上极限，我们就能得到:$$\limsup_{N\to \infty}\left|\frac{1}{N}\sum_{n=1}^{N}f(\varepsilon(u_n))-\int_{-1/2}^{1/2} f(x)\,dx\right|\leq 2\varepsilon,\forall \varepsilon>0$$
所以我们知道，Weyl的等价条件3也可以扩展到实黎曼可积函数。

既然可以扩展到黎曼可积函数，那么对于任意的闭区间$[a,b]\subseteq [-1/2,1/2]$，考虑Weyl判别的等价条件3成立于函数$1_{[a,b]}(x)$，这是一个黎曼可积的函数。于是$$\frac{1}{N}\sum_{n=1}^{N}1_{[a,b]}(\varepsilon(u_n))\to\int_{-1/2}^{1/2}1_{[a,b]}(x)dx$$也就是说$$\lim_{N\to \infty}\frac{\nu(a,b,N;u_n)}{N}=b-a$$于是我们便证明了$3\implies 1$。


#### 1.4 用step function逼近逼近连续函数：$1\implies 3$

如果Weyl判别成立，这意味着在任意的闭区间$[a,b]\subseteq [-1/2,1/2]$上定义的指标函数$1_{[a,b]}(x)$满足Weyl判别的第三个条件。那么对于任意的step function ，即形如$$\varphi_n(x):=\sum_{k\leq n}a_k1_{I_k}(x)$$都成立Weyl判别的第三个条件。而下面这个结果就可以直接帮助我们完成整个证明：

> [!引理1.4.1]
> $f$闭区间$[a,b]$上的Riemann可积函数，对任意的$\varepsilon>0$存在一个$[a,b]$上定义的step function $\varphi_{\varepsilon}:=\sum_{k\leq n_{\varepsilon}}1_{I_k}(x)$，其中$I_k\subseteq [a,b]$，使得$$\sup_{x \in [a,b]}|f(x)-\varphi_{\varepsilon}(x)|<\varepsilon$$

于是重复与上面类似的证明，我们便可以证明$1\implies 3$。

### 2.Weyl's Criterion能处理的典型问题
#### 2.1 序列$b\log(n)$不是模1均匀分布的序列

> [!命题2.1.1]
> $u_n=b\log(n)$对任意的$b$，此序列都不会是模1均匀分布的。

对于此问题我们只需要证明，对于任意的非0整数$k$,$$\frac{1}{N}\sum_{n=1}^{N}e^{ic\log(n)}\text{不会趋于0},c=2\pi bk$$其基本方法是用Euler-Maclaurin求和公式。这是非常自然的，因为最后无非就是要确认此求和是否为$o(N)$的求和，从而除以$N$以后的整体是否为$o(1)$，因此使用求和估计的工具。由求和公式：$$\sum_{n=1}^{N}f(n)=\int_{1}^{N}f(x)\,dx+{\frac{f(1)+f(N)}{2}}+\int_{1}^{N}\left(\{x\}-{\frac{1}{2}}\right)f^{\prime}(x)\,dx$$此处$f(x):=e^{ic\log(x)}$。第一项$\int_{1}^{N}f(x)dx=\frac{i-iN\cdot N^{ic}}{-i+c}$,第一项如果除以$N$那么最后因为$N^{ic}$是没有极限的。然后看后面两项，如果没有其他问题，那么可以证明这个序列不是均匀分布的。第二项因为是$O(1)$所以除以$N$以后一定是$o(1)$.第三项，$|\{x\}-1/2|\leq1/2$，然后$|f'(x)|=\frac{c}{2x}$于是第三项除以$N$之后等于$O(\log(N)/N)$.综上所述，最后极限不存在，因此此序列不可能是均匀分布的。

不过

> [!命题2.1.2]
> $\log(n)$模1的余数再对应的区间中是稠密的。

如果余数定义为$\{\log(n)\}$，那么余数在$[0,1)$当中稠密。而如果是$\varepsilon(\log(n))$意义下，那么余数序列在$[-1/2,1/2)$当中稠密。这个证明的秘诀在于：

如果序列的子列是稠密的，那么序列本身也是稠密的。而序列$\log(n)$有一个特殊的子列$\log(2^n)=n\log(2)$。由于$e$的超越性，我们知道$\log(2)$是无理数，从而Kronecker定理告诉我们$n\log(2)$模1的余数序列是稠密的,因此$\log(n)$模1的余数序列稠密。(参考[[Kronecker定理，Dirichlet定理及其应用]])

此外这个例子也可以告诉我们，非模1均匀分布的序列可能存在均匀分布的子列。

#### 2.2 一次多项式，非常数项系数为无理数的序列是模1均匀分布的

> [!命题2]
>  $u_n=n\gamma$,其中$\gamma$是任意的一个正无理数，该序列是模1均匀分布的。

 
 这个例子可以作为Weyl Criterion的一个动机。因为如果我们按照定义来说，此时$$\frac{1}{N}\#\{1\leq n\leq N:\varepsilon(u_n)\in(a,b)\}=\frac{1}{N}\sum_{n=1}^{N}1_{(a,b)}(\varepsilon(u_n))$$右边恰好就是$b-a=\int_{-1/2}^{1/2}1_{(a,b)}(x)dx$。于是此序列是否均匀分布只需要验证，是否:$$\frac{1}{N}\sum_{n=1}^{N}1_{(a,b)}(\varepsilon(u_n))\to\int_{-1/2}^{1/2}1_{(a,b)}(x)dx$$然后Weyl's criterion告诉我们，只需要估计指数和，而当前状况下指数和并不算困难$$\frac{1}{N}\sum_{n=1}^{N}e(kn\gamma)=\frac{e(kn\gamma)}{N}\frac{1-e(kn\gamma)}{1-e(k\gamma)}\to0$$

#### 2.3 命题3

> [!命题3]
>  $u_n=an^{b},a\neq0,b\in(0,1)$,那么这个序列是模1均匀分布的。

 也就是说我们实际上需要估计求和，$$\frac{1}{N}\sum_{n=1}^{N}e(cn^b),e(x)=e^{2\pi ix},c=ak$$由Euler-Maclaurin求和公式，其中我们需要估计两个积分。第一个$$\int_{1}^{N}e(cx^b)dx=O(N^{1-b})$$这其中一个关键的技巧是分部积分。然后是对余项的估计，也就是$$M\int_{1}^{N}(x-\{x\})x^{b-1}e(cx^b)dx=O\left(\int_{1}^{N}x^{b-1}dx\right)=O(N^{b})$$于是$$\frac{1}{N}\sum_{n=1}^{N}e(cn^b)=O(N^{-b})+O(N^{b-1})$$因此$u_n$是模1均匀分布的序列。

#### 2.4 还可以利用这种结论证明一些极限问题

> [!命题4]
> $$\frac{\sum_{n=1}^{N}|\cos(n^2)|}{N}\to\frac{2}{\pi}=\frac{1}{2\pi}\int_{0}^{2\pi}|\cos(x)|dx$$

这里我们只用证明下面这个命题即可：

> [!命题5]
> $n^2$模$2\pi$在$[0,2\pi]$当中均匀分布

不过这里不用估计指数和，而是利用

> [!van der Corput's difference theorem,1931]
> 如果序列$u_{n+h}-u_n$是模1均匀分布的对任意正整数$h$成立，那么$u_n$也是模1均匀分布的。

借助这个定理，我们知道$n^2$的差分的序列因为命题2是模1均匀分布的，因此其本身也是模1均匀分布的。
#### 2.5. 使用Weyl判别当中的第二条

如果序列不是光滑函数的形式，那么就不能用对光滑函数的求和估计的方法对$\frac{1}{N}\sum_{n=1}^{N}e^{2\pi iku_n}$的估计。

> [!命题6]
> 比如$\{\frac{0}{1},\frac{0}{2},\frac{1}{2},\frac{0}{3},\frac{1}{3},\frac{2}{3},\dots\frac{k-1}{k},...\}$的序列是模1均匀分布的。

这样就不能用Weyl的第一条判别方法。但是可以用第二条判别，即如果对于任意连续函数都有求和的极限趋近函数的积分，那么也可以判断序列是模1均匀分布的。

具体证明可以参考:
https://math.stackexchange.com/questions/3591743/show-that-the-sequence-frac01-frac02-frac12-frac03-fra


