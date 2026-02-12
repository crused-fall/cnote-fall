---
tags:
  - math
  - 实分析
  - 调和分析
---
### 1. 弱型估计

##### 1.1 Vitali覆盖引理的思路

> [!note] 定义1.1.1
> 令$f\in L^1_{loc}(\mathbb{R}^d)$，定义$$Mf(x):=\sup_{r>0}\frac{1}{|B(x,r)|}\int_{B(x,r)}|f(y)|\,dy$$其中$|E|$表示$d$维的Lebesgue测度。


> [!note] 定理1.1.2:Maximal函数的弱型估计(Hardy-Littlewood ,1930)
> 对任意正整数$d$，存在一个正实数$C_d$使得对任意$\alpha>0,f\in L^1(\mathbb{R}^d)$都有$$m(\{x:Mf(x)>\alpha\})<\frac{C_d}{\alpha}||f||_{L^1(\mathbb{R}^d)}$$

> [!tip] 想法1.1.3
> 其基本想法是一种广义程度上的“逐项估计”。令$E_{\alpha}:=\{x:Mf(x)>\alpha\}$那么任意$x\in E_{\alpha}$按照定义一定存在一个包含$x$的球$B_x$使得$$\frac{1}{m(B_x)}\int_{B_x} |f(y)|\,dy>\alpha\implies m(B_x)<\frac{1}{\alpha}\int_{B_x} |f(y)|\,dy$$如此一来我们便建立起了集合$E_{\alpha}$的任意一个点的邻域上对应测度的上界估计，接下来如果我们可以把这种估计合起来，变成一种全局的估计，问题就可以被解决。
> 
> 这里的关键想法是，结合[[an epsilon of room#4. 版本3的实践：考虑更简单的对象]]的想法，对于$E_{\alpha}$这样一个Lebesgue可测的集合的上界估计，由于这种可测集的内正则性，我们可以考虑控制其内部的任意一个紧子集$K$。如果任意的紧子集$K$存在一个共同的上界，那么这个上界也可以控制$E_{\alpha}$。而这里之所以考虑$K$是因为$K$一定可以被$\cup_{x\in E_{\alpha}} B_x$给覆盖，那么一定存在有限的子覆盖$$K\subset \bigcup _{k=1}^{N}B_k$$于是自然地我们会想要尝试$$\begin{aligned}m(K)\leq m\left(\bigcup _{k=1}^{N}B_k\right)&\leq \sum_{k=1}^{N}m(B_k)\\&\leq \frac{1}{\alpha}\sum_{k=1}^{N}\int_{B_k} |f(y)|\,dy\quad \quad \quad \quad (1)\end{aligned} $$我们真正想要建立的是$$\color{red}\sum_{k=1}^{N}\int_{B_k} |f(y)|\,dy\leq \int_{\cup_{k=1}^N{B_k}}|f(y)|\,dy \leq ||f||_{L^1}$$但这是不对的，因为$B_k$之间可能会有重叠，除非...这些$B_k$互相之间是互不相交的。但一般情况下$B_k$里面不可能都不相交，很容易就可以给出反例。我们转念一想，我们也未必需要全部的$B_1,\cdots,B_N$只要可以从中找到一族互不相交的球，并且使得他们的测度可以控制住$m\left(\bigcup _{k=1}^{N}B_k\right)$，最后就可以实现。
> 
> 假设我们可以从原本的一族覆盖$K$的$N$个球里面选出$B_{k_1},\cdots,B_{K_L}$个互不相交的球，并且它们测度满足$$m\left(\bigcup _{k=1}^{N}B_k\right)\leq C_d\sum_{j=1}^{L} m(B_{k_j})$$于是现在我们便可以修补$(1)$当中的问题了：$$\begin{aligned}m(K)\leq m\left(\bigcup _{k=1}^{N}B_k\right)&\leq C_d\sum_{j=1}^{L} m(B_{k_j})\\&\leq \frac{C_d}{\alpha}\sum_{j=1}^{L}\int_{B_{k_j}} |f(y)|\,dy\\&\leq \frac{C_d}{\alpha}\int_{\cup_{j=1}^{L}B_{k_j}}|f(y)|\,dy \\&\leq \frac{C_d}{\alpha}||f||_{L^1}\end{aligned} $$所以唯一的问题就是，如何得到证明这样一个覆盖的结论。


> [!note] 引理1.1.4:Vitali覆盖引理（Vitali,1908）  
> 设$\mathcal{B}:=\{B_1,\cdots,B_N\}$是$\mathbb{R}^d$当中的$N$个开球，那么$\mathcal{B}$当中存在$L$个不互不相交的球$B_{k_1},\cdots,B_{k_L}$满足$$m\left(\bigcup _{k=1}^{N}B_k\right)\leq 3^d\sum_{j=1}^{L} m(B_{k_j})$$

整个证明基于下面的想法实现：

> [!tip] 想法1.1.5
> 如果$B,B'$是两个相交的球，并且其中$B$的半径大于等于$B'$的半径，那么这两个球都可以被包含在一个以$B$的球心为球心，半径是$B$的三倍的大球$\tilde{B}$当中。如图所示：
> 
> ![[vitali covering lemma 的示意图.png]]
> 
> 那么对于$\mathcal{B}$当中的球，我们可以挑选一个半径最大的$B_{k_1}$，按照图中的原理，所有与$B_{k_1}$相交的球，其半径都不超过$B_{k_1}$的半径，并且都被包含在$3B_{k_1}$当中。
> 1. 如果$\mathcal{B}$当中所有球都与$B_{k_1}$相交，那么$\bigcup _{k=1}^{N}B_k\subset 3B_{k_1}$于是$$m\left(\bigcup _{k=1}^{N}B_k\right)\leq m(3B_{k_1})$$
> 2. 如果$\mathcal{B}$当中有些球与$B_{k_1}$不相交，那么可以在$\mathcal{B}$当中去除$B_{k_1}$以及所有与$B_{k_1}$相交的球之后剩下的球当中，再挑选一个半径最大的球，设为$B_{k_2}$。那么根据上面的原理，所有与$B_{k_2}$相交的球包括$B_{k_2}$本身都会被包含在$3B_{k_2}$当中，并且$B_{k_1},B_{k_2}$不相交。
> 3. 以此类推，我们可以选出$B_{k_1},B_{k_2},\cdots,B_{k_L}$，它们两两互不相交，并且$$\bigcup _{k=1}^{N}B_k\subset \bigcup _{j=1}^{L}3B_{k_j}$$于是$$\begin{aligned}m\left(\bigcup _{k=1}^{N}B_k\right)&\leq m\left(\bigcup _{j=1}^{L}3B_{k_j}\right)\\&\leq \sum_{j=1}^{L}m(3B_{k_j})\\&\le 3^d\sum_{j=1}^{L} m(B_{k_j})\end{aligned}$$
