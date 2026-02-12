---
tags:
  - math
  - 凸优化
  - 泛函分析
  - 大学数学竞赛
---

> [!question] 问题0 
> $0\leq f(x)\leq 1$为一个单调不减函数，并且满足$\int_{0}^{1}f(x)\,dx = \frac{1}{2}$证明$$\int_{0}^{1}\min\{x,f(x)\}\,dx \geq \frac{3}{8}$$


> [!note] 引理1:Bauer极大原理（1958）
> 设$X$是一个局部凸的拓扑向量空间，$K\subset X$一个紧凸集，$f:K\to \mathbb{R}$连续凸。则$f$在$K$上的最大值在$K$的extreme point处取得。

* 这个结果有一个对偶的结果:如果$f$是连续凹函数，那么其在紧凸集$K$上的最小值也在extreme point处取得。

此处我们之所以引用Bauer的结果，是因为我们可以给原本的“问题0”建立一个凸优化的场景：

> [!tip] 转换为一个优化问题
> 令$$M:=\left\{f\in L^1([0,1]):0\leq f\leq 1并且单调不减，\int_{0}^{1}f(x)\,dx = \frac{1}{2}\right\}$$泛函$$F(f):=\int_{0}^{1}\min\{x,f(x)\}\,dx$$我们的问题等价于，在线性赋范空间$L^1([0,1])$上的子集$M$上最小化函数$F$。

而我们之所以考虑Bauer的结果是因为：

* 首先$M$是一个凸集：对于任意的$f,g \in M$以及$\lambda\in (0,1)$由于$0\leq \lambda f +(1-\lambda)g \leq 1$，保持单调性并且$$\int_{0}^{1}\lambda f +(1-\lambda)g =\frac{1}{2}$$因此$\lambda f +(1-\lambda)g\in M$，所以$M$是一个凸集。
* 其次$F$是一个凹函数：因为对于任意的$f,g \in L^1([0,1])$以及$\lambda\in (0,1)$都有$$\min\{x,\lambda f +(1-\lambda)g \}\geq\lambda \min\{x,f\}+(1-\lambda)\min\{x,g\}$$于是$$F(\lambda f +(1-\lambda)g )\geq \lambda F(f)+(1-\lambda)F(g)$$


那么剩下的，如果我们可以验证$M$的紧性，以及$F$的连续性，那么依照Bauer的结果，我们就可以知道$F$的最小值一定在$M$的extreme point处取得。对于$M$而言，其extreme point一定形如$f^{*}(x):=1_{[c,1]}(x)$*的形式，其中由于$f^{*}$的积分为$1/2$那么$c=1/2$，于是$$f^{*}(x):=1_{[\frac{1}{2},1]}(x)$$此时$$F(f^{*})=\int_{0}^{1}\min\{x,1_{[\frac{1}{2},1]}(x)\}\,dx=\int_{\frac{1}{2}}^{1}x\,dx=\frac{3}{8}$$因此"问题0"便得到了解决。

---

以上讨论成立还需要两个条件$M$紧且$F$连续。

首先证明$M$的紧性。容易证明$M$是一个闭集，那么我们要做的就是证明$M$的相对紧性，这在$L^1$这种度量空间内等价于证明其列紧性。

所谓列紧性，我们需要证明一列$f_n\in M$存在一个子列$f_{n_k}$收敛到某个极限$f$并且$f\in M$。此处由于$f_n$具有单调不减，并且一致有界，那么这正好满足Helly选择定理，那么一定存在子列$f_{n_k}$收敛到某个单调不减的极限函数$f$。此外$f$作为极限函数其积分依旧为$1/2$。因此$M$列紧。

最后我们需要验证$F$的连续性。实际上我们可以得到更强的结果：$F$满足Lipschitz连续。由于对于任意的$x,y,z\in \mathbb{R}$都有$$|\min\{x,z\}-\min\{y,z\}|\leq |x-y|$$因此对于任意的$f,g\in L^1([0,1])$都有$$\begin{aligned}|F(f)-F(g)|&\leq \int_{0}^{1} |\min\{x,f(x)\}-\min\{x,g(x)\}|\,dx \\&\leq \int_{0}^{1} |f(x)-g(x)| \,dx \\&= ||f-g||_{L^1}\end{aligned}$$因此$F$自然是连续的。

---

接下来我们来看该问题的一个离散版本：

> [!question] 问题2 
>  序列$0\leq a_1\leq a_2\leq \cdots \leq a_n\leq 1$，并且满足$\sum_{k=1}^n a_k = \frac{n+1}{2}$证明$$\sum_{k=1}^n \left|a_k-\frac{k}{n}\right|\leq \frac{n}{4}$$

为了把问题转换为同样的问题，我们可以把目标和当中的绝对值改写成$\min$的形式：

$$\sum_{k=1}^n \left|a_k-\frac{k}{n}\right|=\sum_{k=1}^{n} a_k+\sum_{k=1}^{n}\frac{k}{n}-2\sum_{k=1}^{n}\min\{a_k,\frac{k}{n}\}\tag{1}$$于是问题被转换为求证$$S_n:=\sum_{k=1}^{n}\min\{a_k,\frac{k}{n}\}\geq \frac{3}{8}n+\frac{1}{2}$$

> [!tip] 想法3
> 借助于[[layer-cake 表示]]我们可以把离散的问题转换为连续的序列对应的值的分布函数的问题。只要我们选择一个合适的离散的测度，那么我们便可以把该问题转换为两个序列$a_k,\frac{k}{n}$分别对应的值的分布函数的类似于"问题0"的优化问题。

令$(\Omega_n,\mathcal{F},\mu)$是一个测度空间，其中$\Omega_n:=\{1,2,\cdots,n\}$,$\mathcal{F}$是$\Omega_n$的所有子集组成的sigma代数$$\forall A \in \mathcal{F},\mu(A)=\frac{|A|}{n}$$定义函数$h(t):=\mu(\{k\in \Omega_n:a_k>t\}),g(t):=\mu(\{k\in \Omega_n:\frac{k}{n}>t\})$分别为序列$a_k,\frac{k}{n}$的分布函数。

根据“问题2”的条件$$\sum_{k=1}^{n}a_k = n\int_{\Omega_n} a_k \,d\mu(k) \implies \int_{\Omega_n} a_k \,d\mu(k) = \frac{1}{2}+\frac{1}{2n}$$于是根据[[layer-cake 表示]]:$$\int_{0}^{1} h(t)\,dt=\int_{\Omega_n}a_k \,d\mu(k)=\frac{1}{2}+\frac{1}{2n}\tag{2}$$其次由于序列$a_k,\frac{k}{n}$是两个单调增加的序列，那么集合$Q_{n,t}:=\{k\in \Omega_n:a_k>t\},P_{n,t}:=\{k\in \Omega_n:\frac{k}{n}>t\}$实际上是嵌套在一起，其中一个包含另一个的集合。根据Layer-Cake表示$$\frac{1}{n}\sum_{k=1}^{n}\min\{a_k,\frac{k}{n}\}=\int_{0}^{1} \mu(Q_{n,t}\cap P_{n,t})\,dt=\int_{0}^{1} \min\{h(t),g(t)\}\,dt\tag{3}$$
于是根据$(1),(2),(3)$我们可以把“问题2”转换为:

> [!question] 问题4
> 令$$T:=\left\{h\in L^1([0,1]):h单调不增，并且\int_{0}^{1} h(t)\,dt=\frac{1}{2}+\frac{1}{2n}\right\}$$证明在此集合上，函数
> $$G(h):=\int_{0}^{1} \min\{h(t),g(t)\}\,dt\geq \frac{3}{8}+\frac{1}{2n}$$

按照"问题0"的证明方法，我们可以证明$G(h)$是一个连续凹泛函，并且$T$是一个紧凸集，那么根据Bauer的结果，$G(h)$在$T$上必能在$T$的extreme point上取得最小值。于是$$h^{*}(t):=1_{[0,d)}(t)$$此外由于$T$这个集合对积分的要求，$d=\frac{1}{2}+\frac{1}{2n}$。令$r(t):=\lceil nt \rceil$带入$G$当中得到极小值$$\begin{aligned}G(h^{*})&=\int_{0}^{1} \min\{h^{*}(t),g(t)\}\,dt\\&=\int_{0}^{1} g(t)1_{[0,d]}(t)\,dt \\&=\int_{0}^{d}g(t)\,dt \\&= \int_{0}^{d} \frac{n-r(t)+1}{n} \,dt\end{aligned}$$通过对被积函数进行分段求积分(分为长度为$\frac{1}{n}$的区间)，我们可以证明当$n$为偶数的时候$G(h^{*})=\frac{3}{8}+\frac{1}{2n}$，当$n$为奇数的时候$G(h^{*})>\frac{3}{8}+\frac{1}{2n}$。

回到“问题2”，于是$S_n \geq \frac{3}{8}n+\frac{1}{2}$从而根据$(1)$，得到对任意满足条件的序列$a_k$都有$$\sum_{k=1}^n \left|a_k-\frac{k}{n}\right|\leq \frac{n}{4}\tag{4}$$并且我们还知道，只有$n$为偶数，且对应分布函数为$h^{*}(t):=1_{[0,d)}(t)$的时候，这个式子才能取等号。

下面我们来分析，使得$(4)$等式成立的$a_k$的具体形式。由分布函数$h^{*}$我们知道$|Q_{n,t}|=n1_{[0,d)}$于是当$t\leq d$的时候所有$a_k,k\in \Omega_n$都满足$a_k>t$那么$$a_k\geq d,\forall k \in \Omega_n$$同样的道理，当$t\geq d$的时候$|Q_{n,t}|=0$因此$$a_k\leq d,\forall k \in \Omega_n$$于是我们知道此时$$a_1=a_2=\cdots =a_n=\frac{1}{2}+\frac{1}{2n}$$

---

> [!question] 问题5
> 函数$0\leq f,g\leq 1$单调不减并且满足$$\int_{0}^{1} f(x)\,dx = \int_{0}^{1} g(x)\,dx $$求证$$\int_{0}^{1}|f(x)-g(x)|\,dx \leq \frac{1}{2}$$

> [!tip] 想法6
> 同样的思路，我们可以把最后的优化目标写成是$$||f-g||_{L^1}=\int_{0}^{1} f(x)\,dx + \int_{0}^{1} g(x)\,dx-2\int_{0}^{1} \min\{f(x),g(x)\}\,dx$$如果我们固定$\int_{0}^{1} f(x)\,dx=\int_{0}^{1} g(x)\,dx=m\in [0,1]$于是我们的优化目标实际上是$$H(f,g):=2m-2\int_{0}^{1} \min\{f(x),g(x)\}\,dx$$联想到一些基本事实$$\sup_{(x,y)\in X\times Y}F(x,y) =\sup_{y\in Y}\left(\sup_{x\in X} F(x,y)\right)=\sup_{x\in X}\left(\sup_{y\in Y} F(x,y)\right)$$以及$$\inf_{(x,y)\in X\times Y}F(x,y) =\inf_{y\in Y}\left(\inf_{x\in X} F(x,y)\right)=\inf_{x\in X}\left(\inf_{y\in Y} F(x,y)\right)$$以及如果$I$是一个索引集$\{A_i\}_{i\in I}$是一族非空集合，并且$A:=\cup_{i\in I}(\{i\}\times A_i)$那么对于任意$F:A\to \mathbb{R}\cup \{\pm\infty\}$都有$$\sup_{(i,a)\in A}F(i,a)=\sup_{i\in I}\sup_{a\in A_i}F(i,a),\quad \inf_{(i,a)\in A}F(i,a)=\inf_{i\in I}\inf_{a\in A_i}F(i,a)$$设$M$为满足"问题5"题目中的函数的集合$$R_m:=\left\{f\in L^1([0,1]):0\leq f\leq 1,\int_{0}^{1} f(x)\,dx =m,函数单调不减\right\}$$那么$$M=\bigcup_{m\in [0,1]}\left(\{m\}\times R_m\times R_m\right)$$
> 于是问题可以转换为$$\begin{aligned}\sup_{(f,g)\in M} H(x,y)&=\sup_{m\in [0,1]} \sup_{(f,g)\in R_m\times R_m}\left(2m-2\int_{0}^{1} \min\{f(x),g(x)\}\,dx\right)\\&=\sup_{m\in [0,1]} \left(2m-2\inf_{(f,g)\in R_m\times R_m}\int_{0}^{1} \min\{f(x),g(x)\}\,dx\right)\\&=\sup_{m\in [0,1]} \left(2m-2\inf_{g\in R_m}\inf_{f\in R_m}\int_{0}^{1} \min\{f(x),g(x)\}\,dx\right)\end{aligned}$$如此一来，我们便可以把多元的优化问题转换为累次的一元优化问题，并且可以借助前面几个问题的经验。

下面我们将从最内层开始一层层进行优化。

* 最内层：对于固定的$g\in R_m$参考"问题0"的解决过程，$G(x,g)$是一个连续凹函数，它在凸紧集$R_m$上的最小值存在，且在extreme point处取得，于是$f^{*}(x)=1_{[1-m,1]}(x)$的形式。
* 带入$f^{*}$，下一步我们面对的优化目标是$$G(f^{*},g)=\int_{0}^{1}1_{[1-m,m]}(x)\cdot g(x)\,dx$$由于两个函数都是单调不减的函数，这让我们想起连续版本的[Chebyshev's sum inequality](https://en.wikipedia.org/wiki/Chebyshev%27s_sum_inequality)，从而$$G(f^{*},g) \geq \left(\int_{0}^{1} 1_{[1-m,m]}(x)\,dx\right)\cdot\left(\int_{0}^{1} g(x)\,dx\right) =m^2 \tag{5}$$
* 我们最终的优化目标是函数$$\sup_{m\in [0,1]}2m-2m^2=\frac{1}{2}$$

于是我们知道$$\forall (f,g)\in M \quad ||f-g||_{L^1} \leq \frac{1}{2}$$

