---
tags:
  - math
  - 数论
  - 丢番图逼近
---
> [!note] 命题0（Terence Tao,2017）
> 级数$$\sum_{n\geq 1} \frac{|\sin(n)|^n}{n}<\infty$$

* 2017年这个问题被收入到新《[Lviv Scottish Book](http://www.math.lviv.ua/szkocka/)》当中。2017-6-22，由弗罗茨瓦夫理工大学（Wroclaw Polytechnica）Hugo Steinhaus中心的几位博士生重新提出这个问题，并承诺任何解出该题者可以获得一瓶蜂蜜蜜酒。该问题随后以"Lviv Scottish Book"的名义发布在数学问答网站MathOverflow上。
* [Terence Tao](https://en.wikipedia.org/wiki/Terence_Tao)于2017-9-29在[MatheOverflow上给出该问题的证明思路](https://mathoverflow.net/questions/282259/is-the-series-sum-n-sin-nn-n-convergent)。
* 2023-08-09，Tao在华沙访问期间由“Lviv Scottish Book”的代表现场颁发了那瓶蜂蜜蜜酒与纪念章；[Tao 本人在 Mastodon 留有贴文](https://mathstodon.xyz/@tao/110858903422243734)，官方亦发布了[颁奖视频](https://www.youtube.com/watch?v=Gs9ZQ9fYMFQ)与[帖文](http://www.math.lviv.ua/szkocka/viewproblem.php?prob=282259)。

![[陶获得的一瓶蜂蜜酒.png]]

### 1. 陶的做法

#### 1.1 问题的重点

^872ac2

> [!tip] 想法1.1:真正重要的n 
> 首先我们观察到，真正重要的$n$必定是那些使得$\sin(n)$距离$1$足够接近的正整数。否则对于任意的$\varepsilon>0$,如果$|\sin(n)|\leq 1-\varepsilon$那么由于$$\frac{|\sin(n)|^n}{n}\le \frac{(1-\varepsilon)^n}{n}$$由于$\sum_n\frac{x^n}{n}$的收敛半径为$1$，那么当$|x|$严格小于1的时候级数都是绝对收敛的。也就是说目标级数在$A_{\varepsilon}:=\{n\geq 1:|\sin(n)|\leq 1-\varepsilon\}$这个集合上的和一定是收敛的。所以我们真正关心的是$$\sum_{n\in A_{\varepsilon}^c}\frac{|\sin(n)|^n}{n}$$的情况。

---

考虑某个正整数$n$对应的$|\sin(n)|$与$1$的距离问题，实际上就是考虑$n$与集合$\frac{\pi}{2}+\pi \mathbb{Z}$的最小距离问题。具体而言，这个距离可以定义为$$\eta_n:=\text{dist}\left(n,\frac{\pi}{2}+\pi \mathbb{Z}\right)=\inf_{k\in \mathbb{Z}}\left|n-\frac{\pi}{2}-k\pi\right|$$对于此类问题，我们可以采用丢番图逼近当中的一种几何化的视角，把问题转换为单位圆周上的距离问题，从而让问题更简单。


> [!note] 实数取小数到单位圆周的对应关系
> * 实数$x$取小数一般用符号$\{x\}$来表示。这样的对象可以建立等价关系：$$x\sim y \iff x-y \in \mathbb{Z}$$有等价关系就可以定义等价类。比如所有小数部分为$1/2$的实数，我们就可以表示为$\frac{1}{2}+\mathbb{Z}$。
> * 有了等价关系以后，我们就可以用这个等价关系来划分实数集，得到一个商集$$\mathbb{R}/\mathbb{Z}:=\{x+\mathbb{Z}:x\in \mathbb{R}\}$$此外我们还可借助$x\mapsto \{x\}$的投影，借助实数的拓扑结构按照商拓扑建立$\mathbb{R}/\mathbb{Z}$商的拓扑结构。
> * 此外我们还可以借助实数的加法运算，定义$\mathbb{R}/\mathbb{Z}$商的加法运算$$\{x\}+\{y\}:=\{x+y\}$$
> * 我们还可以在$\mathbb{R}/\mathbb{Z}$定义距离，从而把它当成一个度量空间：$$\text{dist}(\{x\},\{y\}):=\inf_{k\in \mathbb{Z}}|x-y-k|$$
> * 最后我们说$\mathbb{R}/\mathbb{Z}$的结构与单位圆周等价。考虑映射同胚映射$$\phi:\mathbb{R}/\mathbb{Z}\to \mathbb{T}:=\{z\in \mathbb{C}:|z|=1\},\quad \phi(\{x\})=e^{2\pi i x}$$

所以按照此处的理解，我们实际上考虑的是单位圆周上的点$\{\frac{n}{\pi}\}$到圆周上一个定点$\frac{1}{2}+\mathbb{Z}$之间的距离问题。

令$\delta_n:=\text{dist}\left(\frac{n}{\pi},\frac{1}{2}+ \mathbb{Z}\right)$，我们可以把$\eta_n$换一种方式来写$$\eta_n=\pi \inf_{k\in \mathbb{Z}}\left|\frac{n}{\pi}-\frac{1}{2}-k\right|=\pi\delta_n\tag{a}$$

#### 1.2 对和的估计的想法

> [!example] 例子1.2.1: 一个辅助理解的玩具模型
> 设有一列正项序列$x_n$并且我们知道，对于任意长度为$L$的整数区间$I$都有$$\# \{n\in I:x_n\leq \rho\}\lesssim L\rho^{\alpha},\quad \alpha>0\tag{1}$$然后我们要估计级数$$S:=\sum_{n\geq 1} \frac{e^{-nx_n}}{n}$$现在我们尝试结合$(1)$的信息来估计级数：
> 
> * 首先我们对全体正整数进行dyadic分解,令$B_k:=[2^k,2^{k+1})$于是级数在每一段$B_k$上可以得到估计$$\sum_{n\in B_k}\frac{e^{-nx_n}}{n}\le \frac{1}{2^k}\sum_{n\in B_k}e^{-nx_n}\tag{2}$$
> * 然后为了利用$(1)$得到的信息，我们在$B_k$上还可以对$x_n$按照值的分布进行分段。具体来说，我们可以把$\{n:n\in B_k\}$划分为$$\{n:n\in B_k\}=\bigcup_{j\geq 0}\{n:x_n\in [\frac{j}{2^k},\frac{j+1}{2^k}),n\in B_k\}$$这样的话在每一个更小的集合上$nx_n\geq j$从而结合$(2)$，然后交换求和次序，我们得到$$\begin{aligned}\sum_{n\in B_k}\frac{e^{-nx_n}}{n}&\le \frac{1}{2^k}\sum_{n\in B_k}e^{-nx_n}\\&\leq \frac{1}{2^k}\sum_{n\in B_k}\sum_{j\geq 0} 1_{x_n\in [\frac{j}{2^k},\frac{j+1}{2^k})}e^{-j}\\&\leq \frac{1}{2^k}\sum_{j\geq 0} e^{-j}\#\left\{n\in B_k:x_n<\frac{j+1}{2^k}\right\}\end{aligned}\tag{3}$$
> * 根据$(1)$由于$|B_k|=2^k,\rho= \frac{j+1}{2^k}$于是$$\#\left\{n\in B_k:x_n<\frac{j+1}{2^k}\right\}\ll2^k\left(\frac{j+1}{2^k}\right)^{\alpha}=2^{k(1-\alpha)}(j+1)^{\alpha}$$带入这个估计到$(3)$当中，我们得到$$\sum_{n\in B_k}\frac{e^{-nx_n}}{n}\ll 2^{-k}\cdot 2^{k(1-\alpha)}\sum_{j\geq 0}(j+1)^{\alpha}e^{-j}\ll 2^{-\alpha k}\tag{4}$$
> * 于是最终我们得到$$\begin{aligned}S&:=\sum_{n\geq 1} \frac{e^{-nx_n}}{n}\\&= \sum_{k\geq 0}\sum_{n\in B_k}\frac{e^{-nx_n}}{n} \\&\ll \sum_{k\geq 0} 2^{-\alpha k}<\infty\end{aligned}$$
> 
> 于是我们得到结论$S$是一个收敛的级数。

^57d4f2


对于我们此处要估计的对象$|\sin(n)|^n$,我们可以写成$$|\sin(n)|^n=\exp(n\log(|\sin(n)|))$$其中我们只考虑$|\sin(n)|\approx 1$的情况也就是第一节说的选取一个小的$\varepsilon>0$然后只考虑$n\in A_{\varepsilon}^c$的时候，那么$$n\log(|\sin(n)|)\leq- n(1-|\sin(n)|)$$于是我们可以得到上界估计$$|\sin(n)|^n\leq e^{-n(1-|\sin(n)|)}\tag{b}$$此处在$|\sin(n)|\approx 1$也就是$n$非常靠近$\frac{\pi}{2}+\pi\mathbb{Z}$，按照第一节$(a)$的记号$\delta_n$足够小的时候，由$\sin(\frac{\pi}{2}+x)$的Taylor展开$$\sin(\frac{\pi}{2}+x)=1-\frac{1}{2}x^2 +O(x^4)$$于是当$\delta_n$足够小的时候我们得到$$1-|\sin(n)|\asymp \delta_n^2\tag{c}$$

---


我们定义$$E(I;\rho):=\left\{n\in I:\delta_n\leq \rho\right\}$$我们只要能得到$\# E(I;\rho)$，并且这个估计还比较不错的话，我们就可以完成整个证明。

#### 1.3 转换为一个丢番图逼近问题

> [!note] 引理1.3.1
> 令$$E(I;\rho):=\left\{n\in I:\delta_n\leq \rho\right\},\quad \rho<1$$对任意$r>0$都有$$\# E(I;\rho)\lesssim_r(1+L\rho^{\alpha})$$其中$I$是一个区间，$L=|I|,\quad \alpha=\frac{1}{\mu-1+r},\quad \mu=\mu(\pi)<\infty$为$\pi$的irrationality measure(具体定义可以参考[[无理测度的定义以及基本的命题]]）。

^d7d82a

有了这个信息以后，我们仿照“例子1.2.1”这个玩具模型的思路。设$$A_{k,j}:=\left\{n\in B_k:1-|\sin(n)|\in [\frac{j}{2^k},\frac{j+1}{2^k})\right\}$$由1.2节当中的$(c)$，我们知道$$A_{k,j}\subseteq E(B_k;\rho_{k,j}),\quad \rho_{k,j}:=C\sqrt{\frac{j+1}{2^k}}$$
* 理论上$\rho_{k,j}$可以很大，大于1，但此时$A_{k,j}$实际上是一个空集，因为$1-|\sin(n)|$就根本不可能大于1，所以也就不考虑这种情况了。


于是根据“引理1.3.1”，$$\begin{aligned}\#A_{k,j}&\leq \#E(B_k;\rho_{k,j})\\&\lesssim_r(1+2^k\rho_{k,j}^{\alpha})\\&\lesssim_r(1+C^{\alpha}2^{k(1-\alpha/2)}(j+1)^{\alpha/2}) \end{aligned}$$根据这个结果，仿照“例子1.2.1”的玩具模型$$\begin{aligned}\sum_{n\in B_k\cap A_{\varepsilon}^c} \frac{|\sin(n)|^n}{n}&\leq \frac{1}{2^k}\sum_{j\geq 0} e^{-j}\#A_{k,j}\\&\lesssim_r \frac{1}{2^k}\sum_{j\geq 0} e^{-j}(1+C^{\alpha}2^{k(1-\alpha/2)}(j+1)^{\alpha/2}) )\\&\lesssim_r \frac{1}{2^k}+ 2^{-k\alpha/2}\end{aligned}\tag{d}$$因此$$\begin{aligned}\sum_{n\geq 1} \frac{|\sin(n)|^n}{n}&=\sum_{n\in A_{\varepsilon} }*+\sum_{n\in A_{\varepsilon}^c }*\end{aligned}$$其中:
* 由第一节的“想法1.1”我们知道，对任意足够小的$\varepsilon$都有$\sum_{n\in A_{\varepsilon} }\frac{|\sin(n)|^n}{n}$收敛。
* 由$(d)$我们知道$$\sum_{n\in A_{\varepsilon}^c }\frac{|\sin(n)|^n}{n}=\sum_{k\geq 1}\sum_{n\in B_k \cap A_{\varepsilon}^c} \frac{|\sin(n)|^n}{n} \lesssim_r \sum_{k\geq 1} \frac{1}{2^k}+2^{-k\alpha/2}<\infty$$
结合以上两种情况，目标级数收敛。

---

下面证明“引理1.3.1”。

引理的证明主要考虑到：

> [!note] 引理1.3.2：由区间长度以及区间内元素的分离程度推断该区间中元素个数的上界
> 
> 设区间$I$的长度$|I|=L$然后序列$x_1,\cdots ,x_k\in I$并且各不相同。现在如果我们知道任意$x_i,x_j$之间的距离至少为$D$，那么问$k$的上界如何？
> 
> 我们可以对$x_i$这个序列进行重排，按照$y_1< y_2< \cdots <y_k\in I$的方式单调排列。考虑到$x_i$的最小间距的信息，我们知道$$y_{i+1}-y_i \geq D $$对这个结果进行求和，我们知道$$y_k-y_1\geq (k-1)D$$此外考虑到区间长度的信息，我们知道$y_k-y_1\leq L$于是综上所述$$k\leq 1+\frac{L}{D}$$

^8f9f99


> [!tip] 想法1.3.3 
> 首先$\pi$的无理测度的信息可以告诉我们单位圆周上的任意形如$\frac{p}{\pi}\text{ mod }1$的元素距离固定点$\mathbb{Z}$的距离的一个下界估计。
> 
> 然后我们想到，如果两个单位圆周上的元素$\frac{n}{\pi} \text{ mod }1,\frac{m}{\pi} \text{ mod }1$并且$n,m\in I$如果它们到$\frac{1}{2}+\mathbb{Z}$的距离都小于给定的$\rho$,也就是说$n,m\in E(I;\rho)$那么两个元素在单位圆周上的差对应的圆周上的元素$\frac{n-m}{\pi}$距离$\mathbb{Z}$就会有一个上界。
> 
> 以上两个信息可以告诉我们如果$n,m\in E(I;\rho)\subset I$那么二者在整数上距离有某种下界，也就是说我们可以得到$E(I;\rho)$的分离的信息，再加上$|I|$的信息，根据“引理1.3.2”，我们便可以推断出$\#E(I;\rho)$的上界信息。

这里最关键的是关于$\pi$的无理测度的信息。此处我们设$\mu=\mu(\pi)$是$\pi$的无理测度，根据[2020年的一个结果](https://arxiv.org/pdf/1912.06345)$2\leq \mu<7.2<\infty$。根据无理测度的定义(参考[[无理测度的定义以及基本的命题]])我们知道对任意$r>0$存在一个正实数$C_r>0$使得$$\left| \frac{p}{q}-\pi\right|> \frac{C_r}{q^{\mu+r}}$$对任意正整数$p,q$成立。这个信息能告诉我们$\frac{p}{\pi}$这样的单位圆周上的点到单位圆周上的定点$0+\mathbb{Z}$的距离的下界估。取$q^{*}$是使得$|\frac{p}{\pi}-q|$最小的$q$。那么$$\text{dist}\left(\frac{p}{\pi},\mathbb{Z}\right)=\left|\frac{p}{\pi}-q^{*}\right|=\frac{q^{*}}{\pi}|\pi-\frac{p}{q^{*}}|\geq \frac{C_{r}}{\pi} (q^{*})^{-(\mu-1+r)}$$对于那些使得$\left|\frac{p}{\pi}-q^{*}\right|<1$的$p,q^{*}$而言$q^{*}\asymp \frac{p}{\pi}$从而$$\text{dist}\left(\frac{p}{\pi},\mathbb{Z}\right)\gtrsim_r p^{-(\mu-1+r)}\tag{B}$$现在考虑两个不同的整数$n,m\in E(I;\rho)$也就是说$\delta_n,\delta_m<\rho<1$，即存在两个整数$a,b$使得$$\left| \frac{n}{\pi}-(\frac{1}{2}+a)\right|\leq \rho,\quad \left| \frac{m}{\pi}-(\frac{1}{2}+b)\right|\leq \rho$$那么当我们考虑$\frac{n}{\pi} \text{ mod }1,\frac{m}{\pi} \text{ mod }1$这两个$\mathbb{R}/\mathbb{Z}$上的元素的差$\frac{n-m}{\pi} \text{ mod }1$到整数的距离$$\text{dist}\left(\frac{n-m}{\pi},\mathbb{Z}\right)\le \left| \frac{n}{\pi}-(\frac{1}{2}+a)\right|+\left| \frac{m}{\pi}-(\frac{1}{2}+b)\right|\leq 2\rho\tag{C}$$令$p=|n-m|$结合$(B),(C)$我们得到$$p^{-(\mu-1+r)}\leq 2\rho\implies p\gtrsim_r \rho^{-\alpha}$$其中$\alpha=\frac{1}{\mu-1+r}$。

那么按照“引理1.3.2”，我们得到$$\# E(I;\rho)\lesssim_r(1+L\rho^{\alpha})$$