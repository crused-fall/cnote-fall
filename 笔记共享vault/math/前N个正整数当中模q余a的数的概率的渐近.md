---
tags:
  - math
  - 概率论
  - 数论
---

> [!问题1]
> 给出函数$$F(N;q,a):=\frac{\#\{n:1\leq n\leq N,n \text{ mod }q=a\}}{N}$$的渐近表达，精确到$O\left(\frac{1}{N}\right)$。

当然这个问题是初等的，不过这里我们尝试从概率的角度理解这个问题。

### 1. 概率角度的解答
#### 1.1 问题的概率背景

我们可以从概率论的角度看待这个问题。首先我们需要构建一个概率空间:
1. $\Omega_N:=\{1,\cdots,N\}$作为样本。
2. 样本$\Omega_N$的所有子集的集合$\mathcal{P}(\Omega_N)$组成一个$\sigma$代数，在离散拓扑的意义下，实际上$\mathcal{P}(\Omega_N)=\mathcal{B}(\Omega_N)$是$\Omega_N$的Borel代数。
3. 概率测度$\mathbb{P}$用离散的均匀分布对应的测度来进行定义,即任意$A \in \mathcal{B}(\Omega_N)$,对应的概率为$$P_N(A):=\frac{|A|}{N}$$
有了这样一个概率空间以后，我们就可以把“问题1”转换为一个概率问题。我们可以把$F(N;q,a)$的分子上的集合视为是Borel代数$\mathcal{B}(\Omega_N)$当中的一个元素，或者说一个"事件"。那么$F(N;q,a)$实际上就是某个事件在此概率空间下的概率问题。

进一步我们可以考虑一个映射$$\pi_q:\mathbb{Z}\to \mathbb{Z}/q\mathbb{Z}$$这是环$\mathbb{Z}$到环$\mathbb{Z}/q\mathbb{Z}$的环同态，也称之为modulo reduction，其中$\pi_q(n):=\overline{n}$，也就是说把$n$映射到$n$模$q$的剩余类。当我们把$\pi_q$限制在集合$\mathbb{Z}$上的时候定义$$X_N:=\pi_q|_{\Omega_N}$$因为实际上$X_N$是一个$\Omega_N$到$\mathbb{Z}/q\mathbb{Z}$(这里的sigma代数依旧是离散拓扑下的Borel代数，即幂集)的Borel可测函数。因此我们可以把$X_N$视为$\Omega_N$到$\mathbb{Z}/q\mathbb{Z}$的一个随机变量。

既然有了随机变量，那么我们可以定义其分布$\mu_N$也就是$X_N$的pushforward测度,这是一个定义在$\mathbb{Z}/q\mathbb{Z}$上的概率测度，$$\mu_N(A):=P_N(X_N\in A)$$其中$A\in \mathcal{B}(\mathbb{Z}/q\mathbb{Z})$。那么我们可以把"问题1"翻译为一个概率问题:

> [!问题2(问题1的概率版本)]
> 给出概率$$\mathbb{P}(X_N=\mathbf{a})=\mu_N(\{\mathbf{a}\})$$的渐近表达，精确到$O\left(\frac{1}{N}\right)$。其中$\mathbf{a}\in \mathbb{Z}/q\mathbb{Z}$整数模$q$余$a$的剩余类。



然后我们想到在概率论当中：

> [!主要想法]
> 如果直接对付$P_N$的某些计算比较困难，而我们又知道$P_N$弱收敛于$\mu$，并给出定量估计，那么我们可以用$\mu$意义下的概率来近似$P_N$下的概率。

所谓知道弱收敛并给出定量估计，也就是对任意的连续有界映射$$f:\mathbb{Z}/q\mathbb{Z}\to \mathbb{C}$$（当然在此时离散拓扑，以及有限集合的意义下，就是任意映射）我们知道$$\left|\int_{\mathbb{Z}/q\mathbb{Z}}f(x)\,d\mu_N(x)-\int_{\mathbb{Z}/q\mathbb{Z}}f(x)\,d\mu(x)\right|$$的某种定量估计。其中第一个积分还可以通过pushforward写成$$\int_{\mathbb{Z}/q\mathbb{Z}}f(x)\,d\mu_N(x)=\int_{\Omega_N}f(X_N)\,d\mathbb{P}=\mathbb{E}(f(X_N))$$因此随机变量$X_N$弱收敛于$\mu$的定量估计，也就是对$$|\mathbb{E}(f(X_N))-\mathbb{E}(f)|$$的定量估计。

如果我们已经得到了这样的估计，那么我们只需要令$f(x)=1_{\mathbf{a}}(x)$,即一个单纯判断$x$是否等于$\mathbf{a}$。那么也就可以用$$\mathbb{E}(1_{\mathbf{a}})=\int_{\mathbb{Z}/q\mathbb{Z}}1_{\mathbf{a}}(x)\,d\mu(x)$$来近似$P_N(\{\mathbf{a}\})$。而后者是相对简单的，因为$\mathbb{Z}/q\mathbb{Z}$毕竟是一个固定尺寸的，与参数$N$无关的有限集合。

所以接下来需要研究的就是对$P_N$弱收敛于$\mu$的定量分析问题。

#### 1.2 $\mu_N$弱收敛于$\mu$的定量分析

> [!命题1.2]
> 概率测度$\mu_N$弱收敛于$\mu$,其中$\mu$为$\mathbb{Z}/q\mathbb{Z}$上的均匀分布。此外对任意映射$$f:\mathbb{Z}/q\mathbb{Z}\to \mathbb{C}$$都有$$|\mathbb{E}(f(X_N))-\mathbb{E}(f)|\leq \frac{2}{N}||f||_{L^1}$$

* 具体地讲，此处$$\mathbb{E}(f(X_N))=\int_{\Omega_N}f(X_N)\,dP_N=\frac{1}{N}\sum_{n\leq N}f(\pi_q(n))$$以及$$\mathbb{E}(f)=\int_{\mathbb{Z}/q\mathbb{Z}}f(x)\,d\mu(x)=\frac{1}{q}\sum_{\mathbf{r}\in \mathbb{Z}/q\mathbb{Z}}f(\mathbf{r})$$最后$$||f||_{L^1}=\int_{\mathbb{Z}/q\mathbb{Z}}|f(x)|\,d\mu(x)=\sum_{\mathbf{r}\in \mathbb{Z}/q\mathbb{Z}}|f(\mathbf{r})|$$
首先为了让$\mathbb{E}(f(X_N))$与$\mathbb{E}(f)$做[[逐项估计]]（参考[[逐项估计]]第四节），我们需要把前者的和改造成与后者一致的形式。一个基本的方式就是分组。因为如果$\pi_q(n)=\mathbf{r}$那么此时$\mathbb{E}(f(X_N))$的被求和对象就是$f(\mathbf{r})$,只不过前面还有一个权重。按照这种想法$$\mathbb{E}(f(X_N))=\frac{1}{N}\sum_{n\leq N}f(\pi_q(n))=\frac{1}{N}\sum_{\mathbf{r}\in \mathbb{Z}/q\mathbb{Z}}f(\mathbf{r})\sum_{n\leq N,\pi_q(n)=\mathbf{r}}1$$我们如果令$N_{\mathbf{r}}=\sum_{n\leq N,\pi_q(n)=\mathbf{r}}1$,那么做逐项估计的时候我们比较的是$$\left|\frac{N_{\mathbf{r}}}{N}-\frac{1}{q}\right|$$于是我们需要搞清楚$N_{\mathbf{r}}$的估计。

$N_{\mathbf{r}}$实际上就是当$n\leq N$的时候，对应的满足$n=qm+r$的$m$的数目。所以我们知道$$\frac{N-1}{q}-1\leq N_{\mathbf{r}}\leq \frac{N-1}{q}+1$$所以$$\left|\frac{N_{\mathbf{r}}}{N}-\frac{1}{q}\right|\leq \frac{1}{N}(1+\frac{1}{q})$$于是执行分段估计，我们得到$$\begin{aligned}|\mathbb{E}(f(X_N))-\mathbb{E}(f)|&=\left|\frac{1}{N}\sum_{\mathbf{r}\in \mathbb{Z}/q\mathbb{Z}}f(\mathbf{r})\sum_{n\leq N,\pi_q(n)=\mathbf{r}}1-\frac{1}{q}\sum_{\mathbf{r}\in \mathbb{Z}/q\mathbb{Z}}f(\mathbf{r})\right|\\&\leq \sum_{\mathbf{r}\in \mathbb{Z}/q\mathbb{Z}}|f(\mathbf{r})|\left|\frac{N_{\mathbf{r}}}{N}-\frac{1}{q}\right|\\&\leq \frac{1}{N}(1+\frac{1}{q})\sum_{\mathbf{r}\in \mathbb{Z}/q\mathbb{Z}}|f(\mathbf{r})|\\&= \frac{1}{N}(1+\frac{1}{q})||f||_{L^1}\\&\leq \frac{2}{N}||f||_{L^1}\end{aligned}$$
#### 1.3 结论

按照第一节的分析，我们现在只需要令“命题2.1”当中的$f$为$1_{\mathbf{a}}$，那么$$|\mathbb{E}(f(X_N))-\mathbb{E}(f)|\leq \frac{2}{N}||f||_{L^1}$$也就等价于$$|\mathbb{P}(X_N=\mathbf{a})-\frac{1}{q}|\leq \frac{2}{N}$$于是我们知道"问题1"当中$$\begin{aligned}F(N;q,a)&:=\frac{\#\{n:1\leq n\leq N,n \text{ mod }q=a\}}{N}\\&=P_N(X_N=\mathbf{a})\\&= \frac{1}{q}+O\left(\frac{1}{N}\right) \end{aligned}$$





### 2. 命题1.2的高维推广



