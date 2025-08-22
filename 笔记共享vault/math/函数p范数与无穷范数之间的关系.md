---
tags:
  - math
  - 实分析
---

> [!问题]
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

根据定义，对任意的$\varepsilon >0$都存在一个$\delta_{\varepsilon}>0$有:$$\mu\left(\left\{x:|f(x)| >\|f\|_{L^{\infty}} -\varepsilon\right\}\right)\geq\delta_{\varepsilon}$$
因为 $\|f\|_{L^\infty}$是这样的集合测度$\mu(\{x:|f(x)|\geq r\})>0$的上确界，那么任意比这个更小的正实数都会使得这样的集合测度为正。于是:
$$\int|f|^pd\mu \geq \delta_{\varepsilon}
(\|f\|_{L^{\infty}} -
\varepsilon)^p$$
于是我们得到:
$$\liminf_{p \to \infty} ||f||_p \geq
\|f\|_{L^{\infty}} - \varepsilon,\forall \varepsilon
>0$$这也就意味着:
$$\liminf_{p \to \infty} ||f||_p \geq
\|f\|_{L^{\infty}}$$于是极限存在且等于$\|f\|_{L^{\infty}}$.

这里的想法是典型的an epsilon of room的想法:
$||f||_{p} = A(p),B'=\|f\|_{L^{\infty}}$,我们想要证明:
$$A(\infty)\geq B'$$我们入手的点是
$$A(p)\geq B_{\varepsilon}(p)=\delta_{\varepsilon}
^{1/p}(\|f\|_{L^{\infty}} - \varepsilon)$$
然后对p取极限，
$$\liminf_{p\to\infty} A(p)\geq B'-\varepsilon
$$



### 2. 下界估计的想法的来源

这里实际上就是Chebyshev不等式，$L^{\infty}$范数的定义当中$$\mu\left(\left\{x:|f(x)| >\|f\|_{L^{\infty}} -\varepsilon\right\}\right)\geq\delta_{\varepsilon}$$翻译成分布函数的弱形估计的语言(参考[[an epsilon of room证明集合为0测度的策略]]的0.1节)就是$$\lambda_f(\|f\|_{L^{\infty}} -\varepsilon)\geq \delta_{\varepsilon}$$但同时我们又知道$$\lambda_f(x)\leq \frac{||f||_{L^p}^p}{x^p},\forall x>0$$于是结合两个不等式就立刻得到$$\int|f|^pd\mu \geq \delta_{\varepsilon}
(\|f\|_{L^{\infty}} -
\varepsilon)^p$$
 
### 3.紧集上的连续函数

此外如果$f\in C(E)$,其中$E$是一个紧集。那么上述命题中，无穷范数实际上就是一致范数，也就是函数的最大值。对于连续函数而言，如果不引入无穷范数，命题可以叙述为:

> [!连续版本的命题]
> $f\in C(E)$,其中$E$是一个$\mathbb{R}^n$的紧子集并且在Lebesgue测度m下是有限测度,假设函数在此集合上$|f|$的最大值为$M$,那么$$\lim _{p \rightarrow \infty}\|f\|_p=M$$

同样的证明考虑$E_{\varepsilon}:= \{x:|f(x)| >M-\varepsilon\}$,然后由于$$\int|f|^pd\mu \geq m(E_{\varepsilon})
(\|f\|_{L^{\infty}} -
\varepsilon)^p$$
于是和上面一样的论断，得到$$\liminf _{p \rightarrow \infty}\|f\|_p\geq M-\varepsilon$$
* 但是这里有一个问题，是否对于任意$\varepsilon>0$都有$m(E_{\varepsilon})>0$？会不会有某个$\varepsilon$使得$m(E_{\varepsilon})=0$，这样上面的证明就失去意义了。答案是不会，因为$f$是连续的。$$E_{\varepsilon}=|f|^{-1}((M-\varepsilon,\infty))$$这是一个开区间关于连续映射$|f|$的原像，那么也是一个开集。作为一个欧氏拓扑下的开集，其内部必然包含一个开球，如果这个开集是0测度的，那么其必然是空集。否则其内部包含一个半径不为0的开球，而这个开球的Lebesgue测度不会是0，这导致矛盾。因此，如果这个集合是0测度的，那么它就是空集。这意味着$E$当中所有元素都使得$|f|$小于$M-\varepsilon$，这与$M$是$|f|$在$E$上的最大值矛盾。

