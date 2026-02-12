---
tags:
  - math
  - 复分析
  - 数论
---
黎曼猜想：

这个主题的终极目标：

> [!note]  Riemann hypothesis(1859)
> $\zeta(s)$的所有非平凡零点都分布在$\text{Re}(s)=\frac{1}{2}$上。


### 1. Critical Strip之外没有非平凡零点

#### 1.1 $\text{Re}(s)>1$上没有非平凡零点

> [!note]  定理1.1.2(Euler)
> $$\zeta(s)=\sum_{n=1}^{\infty}\frac{1}{n^s}=\prod_{p\text{ prime}}\frac{1}{(1-p^{-s})}$$以上两个级数都在$\text{Re}(s)>1$的时候绝对收敛，并且成立等式。

* 然后我们看到等式最右边的欧拉乘积，其中被乘积对象$$|1-p^{-s}|\geq 1-p^{-\sigma}>0$$其中$\sigma=\text{Re}(s)>1$，于是这个连乘积绝不可能收敛到0。因此在$\text{Re}(s)>1$范围内$\text{zeta}(s)$没有零点。

#### 1.2 $\text{Re}(s)=1$上没有零点


> [!tip]  核心想法(de la Vallée Poussin,1896)
>$$f(x):=\left|\zeta(x)^3\zeta(x+iy_0)^4\zeta(x+2iy_0)\right|$$
>这里假设函数存在一个零点$(1,y_0),y_0\neq0$。于是当$x\to1^{+}$的时候，$$f(x)=O(|x-1|)$$因为函数$\zeta(s)$在$s=1+iy_0$的位置取得零点，那么按照解析函数的性质，一定有：$\zeta(s)=O(|s-(1+iy_0)|)$，然后如果我们固定$s=x+iy_0$，那么一定有$\zeta(x+iy_0)=O(|x-1|)$。然后$\zeta(s)$在$s=1$的位置是一个简单极点，于是就可以得到上面的结论。但是这种构造给我们一个矛盾的结论：$$f(x)\geq1,x>1,\forall y_0\neq0$$关于如何导出此矛盾：从欧拉乘积出发，把$f(x)$写成乘积，然后展开为和，最后估计和。

* 为什么不直接用$\zeta(s),\text{Re}(s)>1$的求和级数的表示，而要用等价的欧拉乘积表示?无非就是看中了对数化以后的和的表示，然后展开为双重求和$$\log\zeta(s)=-\sum_p\log\left(1-p^{-s}\right)=\sum_{p,n}\frac{p^{-ns}}{n}$$并且$$\begin{aligned}\left|\zeta(x+iy)\right|&=\left|\exp\left(\sum_{n,p}\frac{1}{n\cdotp^{nx}}\cdotp^{-iny}\right)\right|\\&=\left|\exp\left(\sum_{n,p}\frac{\cos(ny\cdot\log(p))}{n\cdot p^{nx}}+i\cdot M\right)\right|\\&=\exp\left(\sum_{n,p}\frac{\cos(ny\cdot\log(p))}{n\cdotp^{nx}}\right)\end{aligned}$$最后一部分$\exp(iM)$的模是1，因此消去。所以,$$\left|\zeta(x)^3\zeta(x+iy)^4\zeta(x+2iy)\right|=\exp\left(\sum_{n,p}\frac{3+4\cos(ny\log p)+\cos(2ny\log p)}{np^{nx}}\right)$$最后注意到(实际上3，4，1是提前设计好的，就是要为了配方)里面的三角函数可以配方:$$3+4\cos\phi+\cos2\phi=2(1+\cos\phi)^2\geq0$$于是便完成了证明。

#### 1.3 $\text{Re}(s)\leq 0$中没有非平凡零点

