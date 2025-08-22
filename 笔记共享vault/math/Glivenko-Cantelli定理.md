---
tags:
  - math
  - 概率论
---

> [!Glivenko-Cantelli定理(1933)]
> $X_m$是概率空间$(\Omega,\mathcal{F},\mathbb{P})$上的一列独立同分布的随机变量。这一列随机变量的经验分布函数(Empirical distribution functions)可以定义为$$F_n(x):=\frac{1}{n}\sum_{m\leq n}1_{X_m\leq x}$$如果假设这列随机变量的累积分布函数为$F(x)$，那么$$\sup_{x \in \mathbb{R}}|F_n(x)-F(x)|\xrightarrow{a.e.}{0}$$



* ***关于经验分布函数的理解***:首先它是指标函数$1_{X_m\leq x}(\omega),\omega \in \Omega$序列的一个算术平均值。此处指标函数的含义是$$1_{X_m(\omega)\leq x}:=\begin{cases}1&X_m(\omega)\leq x \\ 0 &\text{Otherwise}\end{cases}$$也就是说$1_{X_m\leq x}$是一个随机变量，而$F_n(x)$实际上是$n$个随机变量的算术平均值，也是一个随机变量,我们可以更详细地写作$F_n(x,\omega)$。那么这个定理实际上说的是$\sup_{x \in \mathbb{R}}|F_n(x,\omega)-F(x)|$作为一个随机变量，它几乎处处收敛到0。
* ***从强大数定律的角度来看***：当$x_0 \in \mathbb{R}$固定下来的时候$F_n(x_0,\omega)$可以视为$1_{X_m\leq x_0}(\omega)$的算术平均值，这自然让我们想起强大数定律。而可测集合序列$$A_m:=\{\omega:1_{X_m(\omega)\leq x_0}=1\}=\{\omega:X_m(\omega)\leq x_0\},B_m:=\{\omega:1_{X_m(\omega)\leq x_0}=0\}=\{\omega:X_m(\omega)>x_0\}$$向我们表明$$\mathbb{P}(A_i\cap A_j)=\mathbb{P}(A_i)\mathbb{P}(A_j),\mathbb{P}(B_i\cap B_j)=\mathbb{P}(B_i)\mathbb{P}(B_j)$$以及$$\mathbb{P}(A_i)=\mathbb{P}(A_j),\mathbb{P}(B_i)=\mathbb{P}(B_j)$$因为随机变量序列$X_m$是独立的。因此我们知道$Y_m:=1_{X_m\leq x_0}$是一列独立同分布的随机变量序列。然后我们计算$F_n(x_0,\omega)$的期望:$$\begin{aligned}\mathbb{E}(F_n(x_0))&=\frac{1}{n}\sum_{m\leq n}\mathbb{E}(1_{X_m\leq x_0})\\&=\frac{1}{n}\sum_{m\leq n}\mathbb{P}(A_m)\\&= \frac{1}{n}\sum_{m\leq n}\mathbb{P}(X_m\leq x_0) \\&= F(x_0)\end{aligned}$$于是强大数定律告（参考[[Etemadi关于强大数定律的证明]]）诉我们当$x_0 \in \mathbb{R}$固定下来的时候$$F_n(x_0,\omega)\xrightarrow{a.e.}{F(x_0)}$$

### 1. 定理的证明

* ***从函数逼近的角度思考***：从以上的基本分析告诉我们，对于逐个固定的参数$x_0$，随机变量$F_n(x_0,\omega)$是几乎处处收敛到实数$F(x_0)$的。但是此处的定理实际上在参数$x$的部分实际上是给出了更强的结果。现在反过来思考，假设$N\subset \Omega$是一个零测度集，在$\Omega':=\Omega\setminus N$上任意固定一个$\omega_0$那么$f_n(x):=F_n(x,\omega_0)$是一个关于$x$的实函数列，我们已知$$f_n(x)\to F(x),\forall x\in \mathbb{R}$$现在需要把这个收敛加强到一致收敛。这里$f_n(x)$可以看成是一列，自身是不减的有界函数列，而极限函数是一个右连续的有界不减函数(上界为1)，那么我们要说明的无非是，这样的条件可以保证收敛被加强到一致收敛。

#### 1.1 连续的情况

我们可以先考察一个简单的情况:

> [!命题1]
> 假设$f_n(x):\mathbb{R}\to \mathbb{R}$是一列由不减的函数组成的有界实函数列，并且此函数列逐点收敛到极限函数$f(x)$,并且$f(x)$是一个有界连续的不减函数，那么此收敛是一致的。

* 证明或者判断是否一致收敛可以认为是针对$\sup_{x \in \mathbb{R}}|f_n(x)-f(x)|$的估计，要求估计精度为$o(1)$。

> [!主要想法1]
> 对于任意的$\varepsilon>0$,因为$f(x)$的有界性以及连续性以及单调性，我们可以把整个$\mathbb{R}$分割为$m_{\varepsilon}$个部分，分别是$$I_1:=(-\infty,x_1],\cdots,I_k:=(x_{k-1},x_k],\cdots ,I_{m_{\varepsilon}}:=(x_{m_{\varepsilon}-1},+\infty)$$然后我们可以保证每一段上面，函数的振幅不超过$\varepsilon$，即$$f(x_{k})-f(x_{k-1})\leq \varepsilon$$此处我们约定$f(x_0),f(x_{m_{\varepsilon}})$为函数各自的下确界，以及上确界。
> 
> 这样做的好处是，我们可以在每一段上对$\sup_{x \in \mathbb{R}}|f_n(x)-f(x)|$进行估计,从而简化问题。

* 同样的对函数列约定$f_n(x_0),f_n(x_{m_{\varepsilon}})$为函数的下确界和上确界。

对任意的$x\in \mathbb{R}$其一定落在某个$I_k$当中，那么此时$f_n(x)-f(x)\geq f_n(x_{k-1})-f(x_{k})$,又因为$f(x_k)-f(x_{k-1})\leq \varepsilon$，因此$$f_n(x)-f(x)\geq f_n(x_{k-1})-f(x_{k-1})+\varepsilon$$同样的道理，我们可以得到上界的估计$$f_n(x)-f(x)\leq f_n(x_{k})-f(x_{k})+\varepsilon$$这也就意味着在$I_k$当中$$\sup_{x \in I_k}|f_n(x)-f(x)|\leq \max\{|f_n(x_{k-1})-f(x_{k-1})|,|f_n(x_{k})-f(x_{k})|\}+\varepsilon$$那么$$\begin{aligned}\sup_{x \in \mathbb{R}}|f_n(x)-f(x)|&=\max_{0\leq k\leq x_{m_{\varepsilon}}}\{|f_n(x_{k})-f(x_{k})|\}+\varepsilon\end{aligned}$$而逐点收敛向我们保证$f_n(x_k)\to f(x_k)$。（在有界性的限制下，上下确界也是保证收敛的）因此$$\lim_{n\to \infty}\sup_{x \in \mathbb{R}}|f_n(x)-f(x)|\leq \varepsilon ,\forall \varepsilon >0$$因此函数列一致收敛。

#### 1.2 右连续的情况

首先意识到，如果函数不是连续的，那么1.1的想法是无法实现的。因为对于一个右连续函数$f$而言，$f(\mathbb{R})$不是连通的，中间可能有跳跃的部分。

不过右连续的有界不减函数可以做到:
> [!引理1.2.1 ：关于右连续的不减有界函数的性质]
> 假设$f(x)$是一个右连续，不减，有界函数。那么对于任意的$\varepsilon>0$我们可以把整个$\mathbb{R}$分割为$m_{\varepsilon}$个部分，分别是$$I_1:=(-\infty,x_1],\cdots,I_k:=(x_{k-1},x_k],\cdots ,I_{m_{\varepsilon}}:=(x_{m_{\varepsilon}-1},+\infty)$$使得$$f(x_{k}^{-})-f(x_{k-1})\leq \varepsilon$$这里约定$f(x_0),f(x_{m_{\varepsilon}}^{-})$分别是函数$f$的下确界以及上确界。

这个结果告诉我们，我们依旧可以做分割，虽然不是相邻两个点的差距被$\varepsilon$控制起来，但是可以通过右连续实现类似的控制。这种控制在Galivenko-Cantelli定理的证明中就足够有用了，因为我们可以定义$$F_n(x^{-},\omega):=\frac{1}{n}\sum_{m\leq n}1_{X_m(\omega)< x}$$从而我们可以证明当我们固定$x=x_0$的时候$F_n(x_0^{-},\omega)$这个随机变量由强大数定律，从而保证几乎处处收敛到$F(x_0^{-})$。于是我们可以在排除一个零测度的$\Omega$的子集以后，保证对于固定的$\omega_0$使得$f_n(x^{-}):=F_n(x^{-},\omega_0)$逐点收敛到$F(x^{-})$。

那么对于任意的$x \in \mathbb{R}$,必然存在$I_k$使得$x \in I_k$。在这个区间上，$$f_n(x_{k-1})\leq f_n(x)\leq f_n(x_{k}^{-})$$以及$$f(x_{k-1})\leq F(x)\leq F(x_{k}^{-})$$从而得到上界估计$$\begin{aligned}F(x)-f_n(x)&\leq F(x_k^{-})-f_n(x)\\&=F(x_k^{-})-f(x_{k-1})+f(x_{k-1})-f_n(x)\\&\leq \varepsilon+F(x_{k-1})-f_n(x) \\&\leq  \varepsilon+F(x_{k-1})-f_n(x_{k-1})\end{aligned}$$同样的道理我们还能得到$$\begin{aligned}F(x)-f_n(x)&\geq F(x_{k-1})-f_n(x)\\&=F(x_{k-1})-F(x_k^{-})+F(x_k^{-})-f_n(x)\\&\geq -\varepsilon+F(x_k^{-})-f_n(x)\\&\geq -\varepsilon+F(x_k^{-})-f_n(x_k^{-})\end{aligned}$$由于$f_n(x)$逐点收敛到$F(x)$,以及$f_n(x^{-})$逐点收敛到$F(x^{-})$,于是两边取极限$$ \sup_{x\in \mathbb{R}}|f_n(x)-F(x)|\leq \varepsilon$$因此一致收敛成立。
