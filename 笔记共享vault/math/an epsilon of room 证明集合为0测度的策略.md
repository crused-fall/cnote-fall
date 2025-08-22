---
tags:
  - math
---
  何为[[an epsilon of room]] ?

### 基本的思路

1. 在测度空间当中，我们要证明一个集合$A$为零测度，即$m(A) =0$。但是这件事并不好直接展开。
2. 于是转而把命题修改为，证明$A_{\varepsilon}$这个集合对于$\forall \varepsilon >0$都有$m(A_{\varepsilon})=0$.
3. **证明的思路无非就是，用一些更大的集合去覆盖$A_{\varepsilon}$，然后证明这种覆盖其测度的上界可以任意小。或者利用一些现成的对集合的控制，比如一些weak-type的不等式。**
### 1. 几个简单的问题

> [!问题1]
> 证明在sigma-finite的测度空间$(\Omega,\mathcal{F},\mu)$上，**对于非负可测函数$f$，在一个测度为正的集合$E$上的积分$\int_{E}f\,d\mu =0$那么$f =0$在集合$E$上几乎处处成立。**

1. 这个问题可以翻译为证明$A = \{x:f(x)\chi_E(x)>0\}$的这个集合是零测度的。
2. 可以等价于证明$A_{\varepsilon} = \{x:f(x)\chi_E(x)\geq\varepsilon\}$对于$\forall \varepsilon >0$都有$m(A_{\varepsilon})=0$，因为$$A = \bigcup_{n\geq 1} A_{1/n}$$
3. 而估计$A_{\varepsilon}$可以采用Chebyshev不等式(weak type的估计)，$$m(A_{\varepsilon}) \leq \frac{1}{\varepsilon}\int_{A_{\varepsilon}}  f\,d\mu \leq \frac{1}{\varepsilon}\int_{E}  f\,d\mu =0 $$
于是函数$f\chi_E$在$\Omega$上几乎处处为0，那么这意味着函数$f$在集合$E$上几乎处处为0(集合E内部函数不为0的点的测度为0).

---

在更为复杂的问题当中，也可以采用类似的策略，只不过步骤繁琐一些。

> [!问题2]
> 证明连续函数$f:\mathbb{R}\to \mathbb{R}$的图像$$G:=\{(x,y):y=f(x)\}$$在$\mathbb{R}^2$的Lebesgue测度下是零测度的。

1. **Fubini-Tonelli的做法**
一个直接的做法是，我们可以借助[[n维球体的体积]]当中第一个命题提到的"切片的办法"。不过运用这个方法之前，我们必须首先确定$G$的可测性。

这部分的思路是证明集合是Borel集，因为Borel集都是$\mathbb{R}^2$当中的Lebesgue可测集合。我们知道对于连续函数而言在任何闭区间$I$上的像$f(I)$是闭集，那么$I\times f(I)$可以视为函数图像的一部分，这个部分是闭集，因此是Borel集合。而整个函数的图像可以视为是$$G=\bigcup_{i}I_i \times f(I_i)$$
也就是说可数个Borel集合的并，那自然也还是一个Borel集，因此可测。

接下来进行切片，$G_x:=\{(x,y)\in G\}=\{(x,f(x))\}$因此显然$m(G_x)=0$，于是$$m(G)=\int_{\mathbb{R}}m(G_x)\,dx=0$$
2. **直接按照定义来**
按照定义，那就是要用矩形来覆盖$G$,并且证明这种覆盖可以无限小，那么按照外测度定义$G$是这种覆盖的"面积"的下确界，那么由于Lebesgue测度的完备性，这个集合可测并且就是零测度。

因为可数个零测度的并依旧是零测度，那么实际上我们只需要考虑在闭区间$I =[a,b]$上的图像$G'$是零测度即可。这一点可以利用一致连续性。

由一致连续性，对于任意的$\varepsilon>0$，存在$\delta_{\varepsilon}$只要$|x-y|<\delta_{\varepsilon}$都有$|f(x)-f(y)|<\varepsilon$。那么我们只需要至多不超过$N<3\frac{|I|}{\delta_{\varepsilon}}$个(这里的3是粗略的放大，实际上用不到，不过我们也不需要这样精确)长度不超过$\delta_{\varepsilon}$的开区间就能覆盖$I'$（表示闭区间去掉两个端点形成的开区间，在图像上去掉有限个点不影响测度）。那么每个小区间对应的函数的图像，可以被一个面积不超过$\varepsilon \delta_{\varepsilon}$的矩形覆盖，那么最终整个开区间$I'$对应的函数的图像$G'$可以被面积不超过$$N\varepsilon \delta_{\varepsilon}<3|I|\varepsilon$$的矩形覆盖(对任意的$\varepsilon>0$成立)。这意味着，$G'$的外测度为0，因此其测度为0.

### 2. [[Irrational measure严格大于2的实数是Lebesgue零测度的]]
这个例子当中，利用irrational measure的定义，给出了覆盖$\alpha \in A_{\varepsilon}$的集合，然后估计了这个覆盖的测度的上界。
### 3. [[Lebesgue微分定理]]

这个例子当中我们借助，连续函数的Lebesgue微分定理，放大有关的函数。
$$\begin{aligned}\limsup_{\begin{aligned}m(B)&\to 0 \\x\in
B\end{aligned}}\left|\frac{1}{m(B)}\int_{B}
f(y)dy-f(x)\right|&\leq
(f-g_{\varepsilon})^{*}(x)+|g_{\varepsilon}(x)-f(x)|
\end{aligned} $$
我们知道**对于$\{\omega:X>a\}$这样的集合的测度的估计，放大$X$就是放大集合，反过来如果大的集合都是0测度的，或者说符合条件的，那么小的集合自然符合。这就是为什么一开始会考虑放大目标函数。**
同时这样操作以后，后面单独的集合的估计，有现成的weak type的估计。

### 4. 证明函数列几乎处处收敛

证明函数列几乎处处收敛也可以视为证明某个集合是零测度，只不过现在这个集合变成了不收敛的那些点形成的集合。

这其中比较有代表性的一个方法是利用[[Borel-Cantelli lemma]]来完成这件事。

假设所有使得函数列不收敛到极限函数的点的集合为$G$,但是我们不直接证明$G$是零测度的，因为这并不好做，而是转换为考虑集合$$A_{n,\varepsilon}:=\{x:|f_n(x)-f(x)|\geq\varepsilon\}$$
可以证明如果对于任何$\varepsilon>0$此集合的上确界$\limsup_{n\to \infty} A_{n,\varepsilon}$是零测度的，那么我们可以证明函数列是几乎处处收敛的。而为了完成最后一步，我们可以借助于Borel-Cantelli lemma,通过估计每一个$m(A_{n,\varepsilon})$，如果其上界形成的级数是收敛的，那么整个证明也就可以完成。

