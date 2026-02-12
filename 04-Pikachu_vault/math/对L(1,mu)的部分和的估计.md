---
tags:
  - math
  - 数论
---

> [!question]  问题0
> 估计$$M(x):=\sum_{n\leq x} \frac{\mu(n)}{n}$$

### 1. 一个简单的上界估计


> [!note]  命题1.1
> $$\left|\sum_{d \leq x}\frac{\mu(d)}{d}\right|\leq 1$$当$x\geq 2$的时候，不等式是严格的。

证明的思路如下：

1. 首先我们知道Mobius函数的Dirichlet卷积的结果$$\mu*1=\varepsilon$$其中$\varepsilon(n)$是Dirichlet卷积的单位元。
2. 然后[[把条件函数展开为新的求和然后换序#1.1 卷积法的基本形式]]的"卷积法的特殊形式1"中的公式告诉我们$$\sum_{n\leq x}\varepsilon(n)=\sum_{n\leq x}\mu(n)\left\lfloor\frac{x}{n}\right\rfloor$$这个式子左边始终等于1，因为$\varepsilon(1)=1$如果$n\neq 1,\varepsilon(n)=0$。于是$$1=\sum_{n\leq x}\mu(n)\left\lfloor\frac{x}{n}\right\rfloor$$
3. 不过上面的等式与我们想要的结果还是有一定的差距的，由于$\left\lfloor\frac{x}{n}\right\rfloor=\frac{x}{n}-\{\frac{x}{n}\}$，然后带入上述式子当中，于是得到$$\sum_{n\leq x}\frac{\mu(n)}{n}=\frac{1}{x}\left(1+\sum_{n\leq x}\mu(n)\left\{\frac{x}{n}\right\}\right)$$所以我们只需要给$f(x):=\sum_{n\leq x}\mu(n)\{\frac{x}{n}\}$一个上界即可。一个非常粗糙的估计就是直接考虑三角不等式结合逐项放缩，因为$|\mu(n)\{\frac{x}{n}\}|<1$，从而得到$|f(x)| < \lfloor x \rfloor$不过“命题1.1”需要的是在$x\geq 2$的情况下，$|f(x)|<x-1$。这其实只需要考虑到，$\mu(n)$其中某一项为0即可，如此一来$f(x)$在不考虑这一项的基础上就有$$|f(x)|<\lfloor x\rfloor-1\leq x-1$$实际上，只要$x\geq 4$，$\mu(4)=0$，于是$f(x)$当中至少$n=4$这一项会消失，从而使得上述不等式成立。
4. 于是我们只需要验证对于$4> x\geq 2$的时候$|f(x)|<x-1$依旧成立，那么"命题1.1"也就得到了证明。这是容易验证的，我们只需要分别考虑$3>x\geq 2$的时候$\{x\}-\{x/2\}<x-1$以及$4>x\geq 3$的时候$\{x\}-\{x/2\}-\{x/3\}<x-1$即可，这是容易验证的。

### 2. 素数定理告诉我们的结果

* 根据[[素数定理的一些等价命题]]当中的“等价命题6”，我们知道，由素数定理我们可以知道$M(x)=o(1)$。
