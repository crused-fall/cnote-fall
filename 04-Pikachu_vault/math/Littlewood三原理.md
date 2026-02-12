---
tags:
  - math
  - 实分析
---
> [!note] Littlewood三原则
> 1. 所有Lebesgue可测集都“几乎”是有限个"区间"的并。
> 2. 所有几乎处处收敛的Lebesgue可测函数列“几乎”是一致收敛的。（Egorov定理）
> 3. 所有Lbesgue可测函数都“几乎”是连续的。（Lusin定理）

### 1. Lebesgue可测的正则性


### 2. Egorov定理

> [!note] Egorov定理（1911）
> 假设$f_k$是一列定义在有限测度的可测集合$E\subset \mathbb{R}^d$上的Lebesgue可测函数，并且$f_k$在$E$上几乎处处收敛到$f$。那么对于任意$\varepsilon>0$，我们都可以找到$E$的一个闭子集$A_{\varepsilon}$使得$m(E-A_{\varepsilon})\leq \varepsilon$并且在$A_{\varepsilon}$上函数列$f_k$一致收敛到$f$。

我们的目标是要对任意的$\varepsilon>0$构造一个闭子集$A_{\varepsilon}$，在满足$m(E-A_{\varepsilon})\leq \varepsilon$的同时，使得$$\sup_{x\in A_{\varepsilon}}|f_k(x)-f(x)|\to 0$$我们发现实际上闭子集这个条件一开始也不需特别在意。因为只要我们可以找到一个可测集合$A_{\varepsilon}'$满足函数列一致收敛的条件，$$m(E-A'_{\varepsilon})<\frac{\varepsilon}{2}$$那么由于Lebesgue可测的内正则性，我们总是可找到一个闭子集$A_{\varepsilon}\subseteq A_{\varepsilon}'$从而$m(A_{\varepsilon}'-A_{\varepsilon})<\frac{\varepsilon}{2}$。那么由于$$E-A_{\varepsilon}=(E-A_{\varepsilon}')\cup(A_{\varepsilon}'-A_{\varepsilon})$$于是$$m(E-A_{\varepsilon})\leq m(E-A_{\varepsilon}')+m(A_{\varepsilon}'-A_{\varepsilon})<\varepsilon$$
* 以上过程可以推广为，在外测度的意义下，假设$C\subseteq B\subseteq A$，那么$$\mu^{*}(A-C)\leq \mu^{*}(A-B)+\mu^{*}(B-C)$$形式上看起来有点像某种三角不等式。

所以一开始的重点主要是，如何构造满足与$E$的测度的逼近条件，以及一致收敛的可测集合$A_{\varepsilon}'$。

我们的出发点是$f_k(x)\to f(x)$在$E$上几乎处处成立，不失一般性我们可以找到一个$E'\subseteq E$使得$f_k(x)$在$E'$上处处收敛到$f(x)$。

那么现在的问题是，要如何做才能在某个集合上把逐点收敛强化到一致收敛？

此处关键的构造在集合$$E_k^{n}:=\{x\in E':|f_j(x)-f(x)|<\frac{1}{n},\forall j>k\}$$
1. 我们想要的$A'_{\varepsilon}$实际上就在$E_k^n$关于$n$的集合列的交集当中。因为对任意的$\delta>0$我们都可以选择一个n使得$\frac{1}{n}<\delta$使得对任意的正整数$k$都有,当$j>k$的时候$$\sup_{x\in E^n_{k}}|f_j(x)-f(x)|\leq \frac{1}{n}<\delta$$
2. 但是我们显然不能随便选一个$k$，然后令$A'_{\varepsilon}$就是$\cap_{n\geq 1}E_k^n$。因为此处还有一个限制，需要$A'_{\varepsilon}$任意逼近$E'$。此处我们考虑到，如果固定$n$考虑关于$k$的集合列$E_k^n$。这是一个关于$k$自下而上逼近$E'$的集合列，根据[[测度论的基础概念#1.2 测度的基本性质]]那么$E_k^n$的测度是可以任意逼近$E'$的测度。那么对于任意的$\varepsilon/2$我们总是可以选择一个$N_{\varepsilon}$，以及一个k的子列$k_n$，使得$m(E'-E^n_{k_n})<\frac{1}{2^n}$以及$\sum_{n\geq N_{\varepsilon}}\frac{1}{2^n}<\frac{\varepsilon}{2}$，从而构造$$A'_{\varepsilon}:=\bigcap_{n\geq N_{\varepsilon}}E_{k_n}^n$$这样的构造能够满足$$m(E-A_{\varepsilon}')\leq \sum_{n\geq N_{\varepsilon}} m(E'-E^n_{k_n})<\frac{\varepsilon}{2}$$
再根据前面的分析我们就找到了对应的构造$A_{\varepsilon}$，从而证明了Egorov定理。

### 3.Lusin定理

> [!note] Lusin定理（1912）
> 假设$f$是一个Lebesgue可测函数，并且在一个有限测度（Lebesgue测度）集合$E\subset \mathbb{R}^d$上取值有限。那么对任意的$\varepsilon>0$存在一个闭集$F_{\varepsilon}$使得$$F_{\varepsilon}\subset E， m(E-F_{\varepsilon})<\varepsilon$$并且使得$f|_{F_{\varepsilon}}$是连续的。

* 此处要注意Lusin定理最后表述的为，$f$限制在$F_{\varepsilon}$上的时候连续，而不是在$x\in F_{\varepsilon}$的点上连续。这两者的区别在于拓扑的不同。我们从连续函数的拓扑定义上来看待这个问题的话，所谓$X\to Y$的连续函数$h$，指的是对任意拓扑空间$Y$当中的开集$V\subset Y$其原像$h^{-1}(V)$是拓扑空间$X$当中的开集。此处：
  1. 第一种情况下令$f|_{F_{\varepsilon}}=g$这是一个定义在$F_{\varepsilon}\to \mathbb{R}^d$的函数，其中$F_{\varepsilon}\subset \mathbb{R}$装备的是子集的拓扑。在这个拓扑当中对于$F_{\varepsilon}$当中的某个子集$W$，如果存在某个$\mathbb{R}^d$当中的开集$U\subset \mathbb{R}$使得$W$可以表示为$F_{\varepsilon}\cap U$那么$W$就是$F_{\varepsilon}$当中的开集。所以回到连续性上来说，现在只要对任意的$V\subset \mathbb{R}^d$都能使得$$g^{-1}(V):=\{x\in F_{\varepsilon}:f(x)\in V\}$$是$F_{\varepsilon}$当中的开集，那么$g$就是在$F_{\varepsilon}$上的连续函数。
  2. 第二种情况下，要求的是$f$在任意的$x\in F_{\varepsilon}$上保持$\mathbb{R}$的欧氏拓扑意义下的连续性。也就是说，对于任意$x\in F_{\varepsilon},f(x)=y$需要保证任意的关于$y$的开邻域$V_y\subset \mathbb{R}$其原像$f^{-1}(V_y)$是一个关于$x$的开邻域，即找到一个开邻域$U_x$使得$U_x=f^{-1}(V_y)$。
* 在度量空间当中我们也可以从点列的角度理解这件事：$f|_{F_{\varepsilon}}$的连续性指的是对任意$F_{\varepsilon}$上的序列$x_k$以及$x\in F_{\varepsilon}$，如果$x_k\to x$那么$f(x_k)\to f(x)$。也就是说，限制在$F_{\varepsilon}$上的连续性只用$F_{\varepsilon}$上点列和点来检验$f(x_k)\to f(x)$这一条规则即可。而如果是单纯考虑在整个度量空间$X$上的某个点$x\in F_{\varepsilon}$上连续，那么任意的$X$当中的序列$x_k$无论是否全部包含在$F_{\varepsilon}$上，只要$x_k\to x$那么一定需要保证$f(x_k)\to f(x)$。

> [!example] 例子3.1
> [Dirichlet函数](https://en.wikipedia.org/wiki/Dirichlet_function)
> $$f(x):=\begin{cases}1&x\in \mathbb{Q}\\0 &x\not\in \mathbb{Q}\end{cases}$$
> 1. 首先函数是一个处处不连续的函数（证明见wiki词条[Dirichlet函数](https://en.wikipedia.org/wiki/Dirichlet_function)），因此$f$在任何无理点处都不是连续的（当然任何有理点处也不是连续的）。
> 2. 如果我们考虑$f|_{\mathbb{Q}}$那么此函数在有理数子集的拓扑意义下是连续的。如果开集$V\subset \mathbb{R}$不包含$1$，那么$(f|_{\mathbb{Q}})^{-1}(V)=\varnothing$。因为$$\varnothing\cap \mathbb{Q}=\varnothing$$其中空集自然是在实数的欧氏拓扑当中作为开集，那么按照子拓扑当中开集的定义，空集也是子拓扑的开集。然后如果开集$V\subset \mathbb{R}$包含$1$，那么$(f|_{\mathbb{Q}})^{-1}(V)=\mathbb{Q}$。因为$$\mathbb{R}\cap \mathbb{Q}=\mathbb{Q}$$其中实数集合本身当然也是实数欧氏拓扑当中的开集，于是有理数集本身也是子集拓扑当中的开集。因此$f|_{\mathbb{Q}}$是连续的。

* 从点列上来理解二者的不同：我们如果要检验$f$是否在$x=1$处连续，我们就需要保证所有的收敛到$1$的实数列$x_k$，无论$x_k$是否全部由有理数构成。比如我们可以找到一列收敛到$1$的无理数列（因为无理数集是稠密的）$x_k$，从而$f(x_k)=0$，但是$f(1)=1$于是$f(x_k)$并不是收敛到$f(1)$的,从而在通常意义下是不连续的。但如果我们谈论的是$f|_{\mathbb{Q}}$那么，我们只需要保证任何收敛到$1$的有理序列$x_k$，是否能满足$f(x_k)\to f(1)$，这当然是成立的。

---

接下来我们来证明Lusin定理。和Egorov定理一样，我们先不必关注$F_{\varepsilon}$的闭集性质，只要找到与$E$足够接近的子集$F_{\varepsilon}'$满足$f$限制此集合上连续即可。因为Lebesgue可测集的正则性向我们保证，我们一定可以在$F_{\varepsilon}'$的子集当中找到我们想要的闭的$F_{\varepsilon}$。

然后我们发挥[[an epsilon of room]]当中的想法，我们可以先验证这件事对更简单更容易的函数成立，然后想办法把这种性质过渡给可测函数$f$。当然这个思考过程并非是，我们决定要用这种思路然后才找更简单的对象，而是我们联想到，对于一个Lebesgue可测函数而言，我们可以找到一列简单函数列几乎处处逼近它。而恰好Lusin定理对于简单函数而言是容易验证的。

---

令$$\phi(x):=\sum_{k=1}^m a_k 1_{A_k}(x)$$是定义在$E$上的一个简单函数。其中$A_k$是一列有限测度的，两两互不相交且并集为$E$的一族集合。$\phi|_{A_k}$因为是常函数，自然是连续的，但是如果我们考虑两个相邻的并且贴在一起的$A_i,A_j$那么就会有问题，此时$\phi|_{A_i\cup A_j}$就并不连续。比如下面的例子：

> [!example] 例子3.2
> $$f(x)=\begin{cases}1&[0,1)\\0&[1,2]\\3&(3,4]\end{cases}$$
> 其中$f|_{[0,2]}$并不连续。因为我们可以找到一个序列，其中$x_k$从左到右收敛到$1$，但是$f(x_k)=1$并不收敛到$f(1)=0$。
> 
> 但是如果我们令$A:=[0,1/2]\cup[1,2]$那么$f|_A$是连续的。因为对于$x\in A$以及序列$x_k\in A$，一定有$f(x_k)\to f(x)$。究其原因是因为，$[0,1/2],[1,2]$是两个距离大于0的集合，从而如果$x_k\to x$那么存在一个$N$使得$|x_k-x|<1/4$，不失一般性假设$x \in [0,1/2]$那么$x_k,k>N$的时候必定全部落在$[0,1/2]$当中，从而保证了$f(x_k)\to f(x)$。

那么对于一般的简单函数（上文提到的）$\phi$，我们也要实现类似的情况，我们想到了Lebesgue可测函数的正则性，对于任意的$\varepsilon>0$每一个集合$A_k$都存在一个闭子集$F_k$使得$$m(A_k\setminus F_k)<\frac{\varepsilon}{m}$$因为我们是在欧氏空间当中讨论问题，因此$F_k$都是紧集，所以对任意不同的$F_i,F_j$由于二者互不相交，那么$\text{dist}(F_i,F_j)>0$。于是令$$F=\bigcup_{k=1}^m F_k$$于是我们说，在$E$当中存在一个闭集$F$使得$\phi|_F$是连续的，并且$m(E\setminus F)<\varepsilon$对任意的$\varepsilon>0$成立。于是我们验证了，Lusin定理对任意定义在$E$上的简单函数是成立的。

---

现在我们要把简单函数的这个性质过渡到可测函数上。令$\phi_n(x)$是定义在$E$上的一列几乎处处收敛到$f$的简单函数列。然后我们思考，如何把连续性过渡给$f$呢？我们想到了一致收敛性，连续函数列满足一致收敛的话其极限函数也是连续的。然后我们想到Egorov定理告诉我们，几乎处处收敛当中某种程度上来说蕴含着一致收敛。

我们会发现这样的一列函数的每一个我们都可以找到一个$E$的闭子集$F_n$，使得:
1. $m(F_n)<\frac{\varepsilon}{2^{n+1}},n\geq 1$。
2. $\phi_n$限制在$E\setminus F_n$上的时候连续。
此外Egorov定理告诉我们对任意的$\varepsilon>0$，$\phi_n$在某个闭子集$F_0,m(E\setminus F_0)<\frac{\varepsilon}{2}$上一致收敛到$f$。于是定义$$F:=\bigcap _{n\geq 0}F_n$$于是连续函数$\phi_n|_F$一致收敛到$f|_F$那么$f|_F$也是一个连续函数，并且$$m(E\setminus F)\leq \sum_{n\geq 0}m(E\setminus F_n)\leq \varepsilon$$因此我们也验证了对于Lebesgue可测函数的Lusin定理。




