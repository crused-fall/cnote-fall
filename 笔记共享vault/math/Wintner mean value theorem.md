---
tags:
  - math
  - 数论
---
### 1. 定理的证明

对算术函数$f$，定义
1. $$M_x(f):=\frac{1}{x}\sum_{n\leq x}f(n)$$
2. $$M(f):=\lim_{x\to +\infty}M_{x}(f)$$
> [!Wintner mean value theorem,20世纪初]
> 如果算术函数$f$是另外一个算术函数$g$的Dirichlet卷积意义下的和，即$$f=1*g$$并且级数$\sum_{n\geq 1}\frac{g(n)}{n}$绝对收敛，那么$f$的平均值$M(f)$就是该级数收敛到的值,即：$$M(f)=\sum_{n\geq 1}\frac{g(n)}{n}$$

> [!主要想法]
> 我们无非就是要估计和$S(x):=\frac{1}{x}\sum_{n\leq x}f(n)$精度要求至少是$o(1)$。因为$f=1*g$因此我们可以利用[[把条件函数展开为新的求和然后换序]]当中第一节的"Dirichlet卷积法特殊形式1"，这样的话主项当中是关于$\sum_{n\leq x} \frac{g(n)}{n}$的，余项中主要是$\sum_{n\leq x}g(n)$。而我们知道$\frac{g(n)}{n}$的级数的收敛性，那么可以用Kronecker's lemma来得到余项的估计。

于是$$\begin{aligned}xS(x)&=\sum_{n\leq x}g(n)\left\lfloor \frac{x}{n}\right\rfloor \\&=\sum_{n\leq x}g(n)\left(\frac{x}{n}+O(1)\right)\\&= x\sum_{n\leq x} \frac{g(n)}{n}+ O\left(\sum_{n\leq x}|g(n)|\right)\\&= x\sum_{n\geq 1}\frac{g(n)}{n}+o(x)\end{aligned}$$

* 注意，此处之所以要求$\sum_{n\geq 1}\frac{g(n)}{n}$是绝对收敛是因为上述推导当中$\left\lfloor \frac{x}{n}\right\rfloor=\frac{x}{n}+O(1)$实际上我们应该写成$\left\lfloor \frac{x}{n}\right\rfloor=\frac{x}{n}+R(n,x)$，然后存在一个与$n,x$无关的常数$C$使得$|R(n,x)| \leq C$。而后面余项的累积按照$R(n,x)$的写法就应该是$$\text{error}(x)=\sum_{n\leq x}g(n)R(n,x)$$而我们估计$\text{error}(x)$的时候，由于我们未必能保证$g(n)$是同号的，于是我们直接用三角不等式来控制从而$$\text{error}(x)\leq C\sum_{n\leq x}|g(n)|$$
最后一步我们利用了Kronecker的一个结果:

> [!引理1,Kronecker's lemma]
> 对于算术函数$f$，如果存在一个$s,\text{Re}(s)>0$使得$$\sum_{n\ge 1} \frac{f(n)}{n^s}<\infty$$那么$$\frac{1}{x^s}\sum_{n\leq x} f(n)\to 0$$

因此如果$\sum_{n\geq 1}\frac{g(n)}{n}$是绝对收敛的，那么$M(|g|)=0$，因此最后的误差项为$o(1)$。

我们还可以从算术函数的Dirichlet生成函数的角度来理解Wintner的平均值定理：

> [!从Dirichlet生成函数理解]
> 因为如果$f=g*1$，那么这个关系体现在Dirichlet生成函数上就是$$L(f,s):=\sum_{n\geq 1}\frac{f(n)}{n^s}=\zeta(s)\sum_{n\geq 1}\frac{g(n)}{n^s},\text{Re}(s)>1$$然后$g$满足级数$\sum_{n\geq 1}\frac{g(n)}{n}$绝对收敛那么$M(f)$存在且等于$\sum_{n\geq 1}\frac{g(n)}{n}$

这样考虑当然没有什么本质的区别，不过是Dirichlet卷积在生成函数上的体现罢了。但往往用Dirichlet生成函数更容易找到$f$的卷积关系。

例子1.1: 

$f(n)=\mu(n)^2$，现在我们考虑$M(f)$。 
### 2. 如果$\sum_{n\geq 1}\frac{g(n)}{n}$是条件收敛？

> [!Wintner mean value theorem(2)]
> 如果算术函数$f$是另外一个算术函数$g$的Dirichlet卷积意义下的和，即$$f=1*g$$如果：
> 1. $\sum_{n\geq 1}\frac{g(n)}{n}$条件收敛，
> 2. $\lim\sup_{x\to +\infty} \sum_{n\leq x}\frac{|g(n)|}{n}<\infty$
> 
> 那么$f$的平均值$M(f)$就是该级数收敛到的值,即：$$M(f)=\sum_{n\geq 1}\frac{g(n)}{n}$$

 * 条件2是不能被去掉的，否则会存在反例。