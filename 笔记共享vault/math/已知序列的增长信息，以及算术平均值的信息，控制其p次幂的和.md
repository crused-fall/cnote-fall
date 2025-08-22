---
tags:
  - math
  - 微积分
  - 考研
  - 大学数学竞赛
---

> [!问题1]
> $x_k>0$，满足增长条件$\lim_{k\to \infty}\frac{x_k}{k}=0$，并且序列$\frac{1}{n}\sum_{k\leq n}x_k$有界，证明对于$p>1$有$$\lim_{n\to \infty} \frac{1}{n^p}\sum_{k\leq n}x_k^p=0$$

如果我们把这个问题视为一个和的估计问题，我们要达到的目的是和$$S_n:=\sum_{k\leq n}x_k^p=o(n^p)$$那么因为知道$x_k=o(k)$,于是被求和对象$x_k^p,p>1$便在k靠近于$n$以及$k$靠近$1$的部分有不同的增长，因此[[分段估计]]是可以考虑的增加估计精度的手段。

对任意$\varepsilon>0$，存在正整数$N_{\varepsilon}$使得任意$k>N_{\varepsilon}$的部分$x_k<\varepsilon k$,于是我们把$1$到$N$的正整数分为两个部分：
1. 前半部分$$S_1:=\sum_{k\leq N_{\varepsilon}} x_k^p\leq N_{\varepsilon}M_{\varepsilon}^p$$其中$M_{\varepsilon}$是序列$x_n$前$N_{\varepsilon}$项当中最大的一项。
2. 后半部分$$\begin{aligned}S_2&:=\sum_{N_{\varepsilon}<k\leq n} x_k^p\\&<\varepsilon^p \sum_{N_{\varepsilon}<k\leq n}k^p \\&=\varepsilon^p O(n^{p+1})=o(n^{p+1})\end{aligned}$$
于是我们发现，这样至多能达到$o(n^{p+1})$的估计，而不能达到目标精度。但是在这个问题当中我们还有一个信息没有利用，即$\frac{1}{n}\sum_{k\leq n}x_k$有界的信息。这个信息能使得$S_2$的估计更为精确，因为我们可以考虑[[基于分部求和法的和的估计]]。但具体怎么操作呢？

* 方案1：
直接考虑$\sum x_k x_k^{p-1}$,假设$A_n:=\sum_{k\leq n}x_k$已知$A_n<Cn$。可是这里有一个需要解决的根本问题，$x_k^{p-1}-x_{k+1}^{p-1}$要怎么估计?直接按照$|x_k^{p-1}-x_{k+1}^{p-1}|<2(k+1)^{p-1}$来做误差还是太大了。但是直接按照telescoping sum来处理，试图放缩成$\sum_k x_k^{p-1}-x_{k+1}^{p-1}$的和，从而达到$O(p-1)$的精度？可是这里根本没有单调性的条件，我们根本无法保证$x_k^{p-1}-x_{k+1}^{p-1}$是否会变号。

所以方案1被否决掉。

* 方案2：
先逐项放缩一下$x_k^{p-1}$
$$\begin{aligned}S_2&:=\sum_{N_{\varepsilon}<k\leq n} x_kx_k^{p-1}\\&\leq \varepsilon^{p-1}\sum_{k\leq n}k^{p-1}x_k\end{aligned}$$这样我们面对的和就是$\sum_{k\leq n}k^{p-1}x_k$只要这个和是$O(n^p)$即可。而如果对这部分做分部求和，问题就简单多了，因为“方案1”当中的差分问题立刻就被解决了。毕竟$k^{p-1}-(k+1)^{p-1}$对我们而言是简单的。

那么采用这种方案，我们来估计$S_2':=\sum_{k\leq n}k^{p-1}x_k$：$$\begin{aligned}S_2'&=\sum_{k\leq n}k^{p-1}x_k \\&= A_nn^{p-1}+\sum_{k\leq n-1}A_k(k^{p-1}-(k+1)^{p-1})\\&\leq Cn^p+\sum_{k\leq n-1}O(k^{p-1})\\&=Cn^p+O\left(\sum_{k\leq n-1}k^{p-1}\right) \\&= Cn^p+O(n^p)\\&= O(n^p)\end{aligned}$$
因此我们知道$S_2 \leq \varepsilon^{p-1}O(n^p)$,因此$S_n = o(n^p)$。
* Landau符号的参考:[[从几个极限问题去理解Landau符号]]
