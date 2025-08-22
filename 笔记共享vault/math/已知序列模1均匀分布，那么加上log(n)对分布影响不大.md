---
tags:
  - math
  - 数论
  - 丢番图逼近
---

> [!命题1，Rindler 1972]
> 假设$x_n$是模1均匀分布的序列，证明$x_n+\log(n)$也是模1均匀分布的。

本质上我们还是遵循Weyl判别去做(参考[[模1均匀分布与Weyl判别]])，我们无非就是要做一个和的估计：$$\frac{1}{N}\sum_{n\leq N}e(kx_n+k\log(n))=o_k(1),\forall k\in \mathbb{Z}^{+}$$
* 此处$e(x):=e^{2\pi i x}$。

并且我们已知$$\frac{1}{N}\sum_{n\leq N}e(kx_n)=o_k(1),\forall k\in \mathbb{Z}^{+}$$首先我们观察到我们的被求和对象$$e(kx_n+k\log(n))=e(kx_n)e(k\log(n))$$具有乘法的结构,那么我们就猜测是否可以用[[基于分部求和法的和的估计]]来完成整个证明。对于使用分部求和做估计，我们已经知道其中$e(kx_n)$的和的估计，那么我们接下来还需要验证，是否$e(k\log(n))$的差分有好的估计？

假设$S_N:=\sum_{n\leq N}e(kx_n)$,那么由于$x_n$的模1均匀分部性质，由Weyl判别我们知道$S_N=o_k(N)$。而对于差分$$|e(k\log(n+1))-e(k\log(n))|<2k\pi\log(1+1/n)=O_k\left(\frac{1}{n}\right)$$而基于分部求和法的和的估计里面我们最关心的是$\sum_{n=1}^{N-1}S_{n}\Delta e(k\log(n))$是否有好的估计。不过看到差分的上界估计以后最后的担心就消除了，因为我们知道$$\begin{aligned}\left|\sum_{n=1}^{N-1}S_{n}\Delta e(k\log(n))\right|&\leq \sum_{n=1}^{N-1}|S_{n}\Delta e(k\log(n))|\\&=\sum_{n=1}^{N-1}o_k(1)\\&=o_k(N)\end{aligned}$$于是我们知道分部求和法是可以给到我们想要的估计的，因为$$\begin{aligned}\left|\sum_{n\leq N}e(kx_n+k\log(n))\right|&=\sum_{n\leq N}\left|e(kx_n)e(k\log(n))\right|\\&= \left|S_Ne(k\log(N))-\sum_{n=1}^{N-1}S_n\Delta e(k\log(n))\right|\\&\leq |S_Ne(k\log(N))|+\left|\sum_{n=1}^{N-1}S_n\Delta e(k\log(n))\right|\\&=o_k(N)+o_k(N)=o_k(N)\end{aligned}$$于是我们知道$$\frac{1}{N}\sum_{n\leq N}e(kx_n+k\log(n))\to 0,\forall k\in \mathbb{Z}^{+}$$于是由Weyl判别，$x_n+\log(n)$是模1均匀分布的序列。