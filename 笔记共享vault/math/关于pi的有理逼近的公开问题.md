---
tags:
  - 数论
  - math
  - 丢番图逼近
---

> [!问题1]
> 函数列$$a_n:=\frac{1}{n\sin(n)}$$是否是有界的?

* $a_n$是有上界，等价于$|n\sin(n)|$有下界。
* $a_n$没有上界，等价于我们可以找到一个正整数的子列$p_n$使得$$p_n\sin(p_n)\to 0$$
而以上两个问题都取决于，当$\sin(n)\approx 0$的时候，这个值与0有多靠近？（为何$\sin(n)$存在子列收敛到0？因为它稠密，参考[[证明正弦函数在整数上取值的序列的极限是不存在的]]）而我们知道$\sin(x)$的零点的集合为$\pi \mathbb{Z}$,于是我们就有必要知道，对于$n$而言，我们选取一个对应的$m$，那么$|n-m\pi|$究竟有多小的问题。也就是说$\pi$能以何种程度被有理数逼近。

### 1. 如果$\mu(\pi)=2$：

#### 1.1 如果$\pi$是Badly approximable的，那么$a_n$有界

如果$\pi$是badly approximable的，那么存在一个常数$C>0$使得对于所有的有理数$\frac{p}{q}$满足$$\left|\pi-\frac{p}{q}\right|\geq  \frac{C}{q^2}$$此时对任意的正整数$p$,都可以找到一个对应的$q$使得$p=p+q\pi -p$并且$|q\pi -p| < \frac{\pi}{2}$,也就是说$q\pi$是$\pi\mathbb{Z}$当中离$p$最近的那个。由$|x|<\frac{\pi}{2}$内满足的不等式$|\sin(x)|>\frac{2}{\pi}|x|$，那么$$p|\sin(p)|=p|\sin(q\pi -p)|>\frac{p}{q}C>\frac{p}{\frac{p}{\pi}+\frac{1}{2}}C$$因此$$\inf_{p\geq 1} p|\sin(p)|>C $$
#### 1.2 如果$\mu(\pi)=2$但是并非badly approximable：

这是最困难的部分。不过按照[[无理测度的定义以及基本的命题]]当中的1.4节的描述，从Lebesgue测度的角度上来说，大多数无理数都属于是这一种情况。如果$\pi$是如此寻常的一个无理数，那么情况会更加微妙。





### 2. 如果$\mu(\pi)>2$：$a_n$无界

如果$\mu(\pi)>2$,那么这意味着我们存在一个$\varepsilon_0>0$使得不等式$$\left|\pi-\frac{p}{q}\right|<\frac{1}{q^{2+\varepsilon_0}}$$有无数组$p,q$互素的整数解。那么我们给这样的解按照分母的大小，从小到大地列出这样的序列$q_n$以及其对应的$p_n$，那么按照$p_n=p_n-q_n\pi+q_n\pi$于是$$\sin(p_n)=\sin(p_n-q_n\pi)$$由于$|\sin(x)|\leq |x|,x>0$那么$$|\sin(p_n)|\leq |p_n-q_n\pi|<\frac{1}{q_n^{1+\varepsilon_0}}$$这意味着$$p_n|\sin(p_n)|<\frac{1}{q_n^{\varepsilon_0}}$$那么当$q_n\to \infty$的时候此序列$p_n|\sin(p_n)|\to 0$。这意味着对于这个子列而言$$\frac{1}{p_n\sin(p_n)}$$是无界的。因此序列$\frac{1}{n\sin(n)}$无界。
