---
tags:
  - math
---

> [!Borel-Cantelli lemma]
> $(X,\mathcal{F},\mu)$是一个测度空间，$E_1,E_2,E_3,...\in \mathcal{F}$并且满足测度的和收敛，$$\sum_{n\geq 1}\mu(E_n)<\infty$$
> 那么几乎所有$x\in X$都包含在至多有限个$E_n$当中。换句话说，$$\mu(\limsup_{n\to\infty}E_n)=0$$或者说$$\mu\left(\bigcup_{n\geq N}E_n\right)\to0$$

这里最后结果的等价是因为，有这么一个单调增加的集合的包含关系
$$ \limsup_{n\to\infty}E_n\subseteq ...\subseteq \cup_{n\geq 2}E_n \subseteq \cup_{n\geq 1}E_n$$
也就是说$\cup_{n\geq N}E_n\downarrow \limsup_{n\to\infty}E_n$ 于是$$\mu(\cup_{n\geq N}E_n)\downarrow \mu(\limsup_{n\to\infty}E_n)$$因此最后的结果是等价的。同时$$\mu(\cup_{n\geq N}E_n) \leq \sum_{n\geq N} \mu(E_n)<\varepsilon$$
因此便证明了Borel-Cantelli lemma。

### 1. 此lemma在序列的几乎处处收敛上的应用

> [!常用引理1]
> 定义集合$A_{n,\varepsilon}:=\{x:|f_n(x)-f(x)|\geq\varepsilon\}$，如果$\forall \varepsilon > 0$都有
> $$\sum_{n\geq1}m(A_{n,\varepsilon})<\infty$$那么可以得到结论
> $$m\left(\limsup_{n\to\infty}A_{n,\varepsilon}\right)=0$$于是
> $$f_n(x) \to f(x) \text{ a.e. }x$$

因为
$$ \limsup_{n\to\infty}A_{n,\varepsilon}\subseteq ...\subseteq \cup_{n\geq 2}A_{n,\varepsilon} \subseteq \cup_{n\geq 1}A_{n,\varepsilon}$$
所以如果$x\not\in \limsup_{n\to\infty}A_{n,\varepsilon}$那么一定存在一个$N_{\varepsilon,x}$使得$x\not\in \cup_{n\geq N_{\varepsilon,x}}A_{n,\varepsilon}$,于是$x\not\in A_{n,\varepsilon}$对任意$n\geq N_{\varepsilon,x}$成立，这意味着对任意$n\geq N_{\varepsilon,x}$有$$|f_n(x)-f(x)|<\varepsilon$$
由于以上逻辑建立在对任意$\varepsilon >0$的基础上，因此$f_n(x)\to f(x)$几乎处处成立。



> [!常用引理2]
> $$A_{n}:=\{x:|f_n(x)-f(x)|\geq \varepsilon_n\}$$其中$\varepsilon_n \downarrow 0$，并且同时$$\sum_{n\geq 1}\mu(A_n)<\infty$$
> 于是按照上面同样的做法，如果$x \not \in \limsup_{n\to\infty} A_{n}$那么存在一个$N$使得$\forall n >N$都有$$|f_n(x)-f(x)|< \varepsilon_n$$同样能表示$f_n(x)\to f(x)$，那么同样能得到结论，$$f_n(x)\to f(x)$$几乎处处成立。

这两个命题以及类似的证明逻辑**可以用来证明一系列关于函数列几乎处处逐点收敛的命题**：

1. [[函数列几乎处处有界与Borel-Cantelli lemma的应用]]这个例子当中把函数列几乎处处有界的条件转换为了集合与测度的形式，然后精心构造了一个可以适用于Borel-Cantelli引理的结构，从而证明了命题。
2. 

### 2.在概率论当中的应用
#### 2.1 第二Borel-Cantelli引理

在概率论当中集合$A_n$的上极限会被表示为$$\limsup_{n\to\infty}A_n=\{\omega:\omega \in A_n\text{ i.o.}\}$$在考虑这个上确界集合的测度的时候还会进一步简写为$$P(\limsup_{n\to\infty}A_n)=P(A_n \text{ i.o.})$$在概率论的主题当中引入了sigma代数当中两个元素独立的概念，即$A,B \in \mathcal{F}$我们说二者独立，当且仅当$P(A\cap B)=P(A)P(B)$.引入这个概念以后有第二Borel-Cantelli lemma：

> [!The second Borel-Cantelli lemma]
> 集合列$A_1,..,A_n,..\in\mathcal{F}$互相之间是独立的，并且其测度形成的集合不收敛$$\sum_{n\geq 1}P(A_n)=\infty$$
> 那么$$P(\limsup_{n\to\infty}A_n)=P(A_n \text{ i.o.})=1$$

这里因为要证明$P(A_n \text{ i.o.}) =1$而我们知道$P(\cup_{n\geq N}A_n)\downarrow P(A_n \text{ i.o.})$,那么我们实际上就是要证明对于任意的正整数$N$,$P(\cup_{n\geq N}A_n)=1$.反过来也就是要证明$P(\cap_{n\geq N}A_n^{c})=0$。

转换为一个有限问题，最后再做极限处理。
$$\begin{aligned}P\left(\bigcap_{n=M}^{N} A_n^c\right) &= \prod_{n=M}^{N} (1 - P(A_n)) \leq \prod_{n=M}^{N} \exp(-P(A_n)) \\&= \exp\left(- \sum_{n=M}^{N} P(A_n)\right) \to 0 \text{ as } N \to \infty \end{aligned}
$$
这其中用到了独立性的条件，以及使用了$1-x\leq e^{-x}$的放缩。

#### 2.2 具体应用

因为概率论相对于一般的测度加入了有限测度,sigma代数当中元素的独立性等等条件，从而可以导出一些更好的结果：
1. 在[[依测度收敛的等价命题]]这个问题当中，我们首先证明了依照测度收敛的充要条件，其中必要条件是用Borel-Cantelli引理证明的。而这个结论的一个应用告诉我们，在有限测度的意义下，依照测度收敛可以被连续函数保持。
2. 在[[Borel-Cantelli lemma证明某种版本下的强大数定律]]当中，我们通过一个额外的关于随机变量$L^4$模存在的条件下，我们先给出随机变量和的平均值$\frac{S_n}{n}$的弱估计的更好的上界。根据这个更好的上界，我们可以得到$$\sum_{n\geq 1} P\left(\left\{\omega:\left|\frac{S'_n(\omega)}{n}\right| >\varepsilon\right\}\right)<\infty$$由此引出Borel-Cantelli lemma，从而根据拓展版本的引理，得到几乎处处收敛的结果，得到所谓的强大数定律。此外第二lemma还在此笔记中证明了强大数定律要成立，期望的有限性是必要条件。
3. [[单位区间内10进制小数中含有无数个7的小数的Lebesgue测度为1]]在这个问题当中我们把关于Lebesgue测度的问题转换为概率问题，因为我们知道10进制表示当中每一位数都是独立同分布的$U(\{0,1,...,9\})$的随机变量。然后我们观察到，问题当中说的十进制小数中包含无穷多个7，我们很快想到了这等于是求$P(\omega \in A_k \text{ i.o.})$。这样我们只需要考虑每一位为7的事件的概率，以及这些事件是否独立，而这些条件显然可以被满足，因此考虑使用第二Borel-Cantelli lemma.



