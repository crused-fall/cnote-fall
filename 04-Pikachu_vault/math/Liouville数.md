---
tags:
  - math
  - 数论
  - 丢番图逼近
---
虽然早在1768年[Lambert](https://en.wikipedia.org/wiki/Johann_Heinrich_Lambert)证明了$\pi,e$的无理性以后就猜测这两个数也并非代数数，但是人类历史上第一个被严格证明超越性的数，还要等到1844年。

> [!note]  定义1:Liouville数
> 令$b$是一个大于等于2的正整数，$a_k \in \{0,1,2,\cdots,b-1\},\forall k\in \mathbb{N}$那么$$L:=\sum_{k\geq 1} \frac{a_k}{b^{k!}}$$就称之为一个Liouville数。

这个数产生的动机来自于Liouville的工作：

> [!note]  引理2:Liouville定理（1844）
> 如果$\alpha$是一个d次代数数($d\geq 2$)，那么存在一个常数$C(\alpha)>0$使得不等式$$\left|\alpha-\frac{p}{q}\right|>\frac{C(\alpha)}{q^d}$$对任意正整数$q$以及任意整数$p$成立。

* 参考[[无理测度的定义以及基本的命题#3. 代数数的无理测度]]当中的“定理3.1"。

按照我们现代的语言来说，Liouville发现所有代数数的无理测度的一个上界是代数数的次数，那么是否存在无理测度为无穷的数？

> [!note]  定理3
> 任意Liouville数的无理测度都是无穷大，即$$\mu(L)=\infty$$

参考[[无理测度的定义以及基本的命题]]，要证明$\mu(L)=\infty$我们就需要证明对任意正整数$n$不等式都$$\left|L-\frac{p}{q}\right|<\frac{C(L)}{q^n}$$存在无穷多组互素的$(p,q)$，$q>0$的整数解。此处$C(L)$是一个只与$L$有关的常数。

因为$L$本身就是用级数的形式定义的，那么该级数的部分和就是一个天然的有理逼近，于是我们就从这里入手。令$$\frac{p_n}{q_n}=\sum_{k\leq n}\frac{a_k}{b^{k!}}$$于是$$\begin{aligned}\left|L-\frac{p_n}{q_n}\right|&=\sum_{k=n+1}^{\infty} \frac{a_k}{b^{k!}}\\&\leq \sum_{k=n+1}^{\infty} \frac{b-1}{b^{k!}}\\&= \frac{b-1}{b^{(n+1)!}}\sum_{m\geq 0}\frac{1}{b^m}\\&=\frac{b}{b^{(n+1)!}}\\&<\frac{b^{n!}}{b^{(n+1)!}}=\frac{1}{b^{nn!}}\leq \frac{1}{q_n^n}\end{aligned}$$虽然我们不知道$\frac{p_n}{q_n}=\sum_{k\leq n}\frac{a_k}{b^{k!}}$的分母的确切的值，但是其分母是一定不能超过$b^{n!}$的，于是我们才构思了上面的放缩。通过上面的放缩我们知道对任意的正整数$m$只要满足$n>m$，那么对应的理数$\frac{p_n}{q_n}$都有$$\begin{aligned}\left|L-\frac{p_n}{q_n}\right|<\frac{1}{q_n^n}<\frac{1}{q_n^m}\end{aligned}$$因为满足这样条件的$p_n,q_n$有无穷多个，于是按照无理测度的定义$$\mu(L)\geq m,\forall m\in \mathbb{Z}^{+}\implies \mu(L)=\infty$$

---

那么根据Liouville的引理：

> [!note]  推论4
> 任意Liouville数都是超越数。


