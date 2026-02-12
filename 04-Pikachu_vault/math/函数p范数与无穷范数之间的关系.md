---
tags:
  - math
  - 实分析
---

> [!note] 定理0
> $f \in L^{\infty}(\mathbb{R}^n)$并且其支集是一个有限可测集，那么$f \in L^p(\mathbb{R}^n),p\geq 1$并且
> 
> $$\lim _{p \rightarrow \infty}\|f\|_p=\|f\|_{L^\infty}$$ 
> 其中$\|f\|_{L^\infty}:=\sup \{r \in \mathbb{R}:\mu(\{x:|f(x)| \geq r\})>0\}$ 也可以定义为
> $||f||_{L^\infty}:=\inf \{r \in \mathbb{R}:\mu(\{x:|f(x)| \geq r\})=0\}$

这个问题的本质是让我们认识到当p增加的时候，这种范数对函数较大的值越来越灵敏，即当p增大的时候范数反应的更多是函数在极值处的行为。

### 1. 证明

从$||f||_{L^\infty}$的定义就可以看出来，$f\leq ||f||_{L^\infty}$几乎处处成立，又因为函数有一个有限测度的支集，那么存在一个有限测度的集合$E$使得，
$$\|f\|_{L^p}=\left(\int_E|f(x)|^p d \mu\right)^{1 / p}
\leq\left(\int_E\|f\|_{L^{\infty}}^p d \mu\right)^{1 / p}
\leq\|f\|_{L^{\infty}} \mu(E)^{1 / p}$$取上极限的话:
$$\limsup_{p \to \infty} ||f||_p \leq
\|f\|_{L^{\infty}}$$
所以整个证明重要的是在另外一边不等式的证明。

根据$L^{\infty}$范数的定义，对任意$\varepsilon>0$存在一个正实数$\delta_{\varepsilon}$，使得$E_{\varepsilon}:=\left\{x:|f(x)| >\|f\|_{L^{\infty}} -\varepsilon\right\}$满足$$\mu(E_{\varepsilon})\geq\delta_{\varepsilon}$$于是$$\begin{aligned}\int|f|^p\,d\mu &= \int_{E_{\varepsilon}}|f|^p\,d\mu\\&\geq \int_{E_{\varepsilon}}(\|f\|_{L^{\infty}} -
\varepsilon)^p\,d\mu\\& \geq 
\delta_{\varepsilon}(\|f\|_{L^{\infty}} -
\varepsilon)^p \end{aligned}$$
于是我们得到:
$$\liminf_{p \to \infty} ||f||_p \geq
\|f\|_{L^{\infty}} - \varepsilon,\forall \varepsilon
>0$$这也就意味着:
$$\liminf_{p \to \infty} ||f||_p \geq
\|f\|_{L^{\infty}}$$于是极限存在且等于$\|f\|_{L^{\infty}}$.

* 这里的想法是典型的an epsilon of room的想法,我们把无穷问题转换为带$\varepsilon$的有限问题来讨论：$||f||_{p} = A(p),B'=\|f\|_{L^{\infty}}$,我们想要证明:$$A(\infty)\geq B'$$我们入手的点是
$$A(p)\geq B_{\varepsilon}(p)=\delta_{\varepsilon}
^{1/p}(\|f\|_{L^{\infty}} - \varepsilon)$$然后对p取极限，
$$\liminf_{p\to\infty} A(p)\geq B'-\varepsilon
$$


### 2.紧集上的连续函数

此外如果$f\in C(E)$,其中$E$是一个紧集。那么上述命题中，无穷范数实际上就是一致范数，也就是函数的最大值。对于连续函数而言，如果不引入无穷范数，命题可以叙述为:

> [!note] 命题2.1：连续版本的命题
> $f\in C(E)$,其中$E$是一个$\mathbb{R}^n$的紧子集并且在Lebesgue测度m下是有限测度,假设函数在此集合上$|f|$的最大值为$M$,那么$$\lim _{p \rightarrow \infty}\|f\|_p=M$$

同样的证明考虑$E_{\varepsilon}:= \{x:|f(x)| >M-\varepsilon\}$,然后由于$$\int|f|^pd\mu \geq m(E_{\varepsilon})
(\|f\|_{L^{\infty}} -
\varepsilon)^p$$
于是和上面一样的论断，得到$$\liminf _{p \rightarrow \infty}\|f\|_p\geq M-\varepsilon$$
* 但是这里有一个问题，是否对于任意$\varepsilon>0$都有$m(E_{\varepsilon})>0$？会不会有某个$\varepsilon$使得$m(E_{\varepsilon})=0$，这样上面的证明就失去意义了。答案是不会，因为$f$是连续的。$$E_{\varepsilon}=|f|^{-1}((M-\varepsilon,\infty))$$这是一个开区间关于连续映射$|f|$的原像，那么也是一个开集。作为一个欧氏拓扑下的开集，其内部必然包含一个开球，如果这个开集是0测度的，那么其必然是空集。否则其内部包含一个半径不为0的开球，而这个开球的Lebesgue测度不会是0，这导致矛盾。因此，如果这个集合是0测度的，那么它就是空集。这意味着$E$当中所有元素都使得$|f|$小于$M-\varepsilon$，这与$M$是$|f|$在$E$上的最大值矛盾。

### 3. 一些相关的问题

> [!note] 问题3.1  
> 设$f$是闭区间$[a,b]$上的一个严格单调增加的，连续非负函数，且存在序列$x_n$满足$$f(x_n)^n=\frac{1}{b-a}\int_{a}^{b} f^n(x)\,dx$$求$\lim_{n\to \infty} x_n$。

结合$$f(x_n)=\left(\frac{1}{b-a}\int_{a}^{b} f^n(x)\,dx\right)^{\frac{1}{n}}\to \max_{x\in [a,b]} f(x)=f(b)$$这一条我们立刻想到，会不会$x_n \to b$？

> [!tip] 想法3.2
> 如果$f$存在逆映射，且逆映射连续就好了。比如$f$是$[a,b]\to f([a,b])$之间的一个同胚映射就好了。因为这样，我们可以假设$f(x_n)=y_n,f^{-1}:=g$于是由于$g$的连续性，于是$$x_n=g(y_n)\to g(f(b))=f^{-1}\circ f(b)=b$$

所以$f$是同胚映射吗？当然是，因为它连续并且**严格单调**。