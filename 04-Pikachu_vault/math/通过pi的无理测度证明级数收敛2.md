---
tags:
  - math
  - 数论
  - 丢番图逼近
---
> [!note] 命题0 
> 级数$$\sum_{n\geq 1} \frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n}<\infty$$

* 该问题可追溯至 Borwein–Bailey–Girgensohn 的著作 《Experimentation in Mathematics: Computational Paths to Discovery》（A K Peters, 2004）第56页 Problem 35。随后在 2004 年 12 月 AoPS 论坛出现[讨论帖](https://artofproblemsolving.com/community/c7h22093p142115)。2020 年，Ravi B. Boppana 在 arXiv 发布[预印本](https://arxiv.org/abs/2007.11017)声称解决了该问题。

---

### 1. 参考Tao的思路的一个解答

整个证明参考[[通过pi的无理测度证明级数收敛性]]当中Tao的思路。

给定一个足够小的$\varepsilon>0$，当$\sin(n)<1-\varepsilon$的时候，由于幂级数$\sum_{n\geq 1}\frac{x_n}{n}$的收敛半径为$1$，从而目标级数收敛。定义$$A_{\varepsilon}:=\{n\geq 1:\sin(n)<1-\varepsilon\}\tag{1}$$于是我们主要考虑$\sum_{n\in A_{\varepsilon}^{c}} *$上的情况。

本质上我们是要估计$$\begin{aligned}\eta_n&:=\text{dist}(n,\frac{\pi}{2}+2\pi \mathbb{Z})\\&= \inf_{k\in \mathbb{Z}}\left|n-\frac{\pi}{2}-2k\pi\right|\\&=2\pi \inf_{k\in \mathbb{Z}}\left|\frac{n}{2\pi}-\frac{1}{4}-k\right|\\&=2\pi \text{ dist}(\frac{n}{2\pi},\frac{1}{4}+ \mathbb{Z})\\&= 2\pi \delta_n\end{aligned}$$最后这个$\delta_n$。

> [!tip] 想法1.1
> 根据[[通过pi的无理测度证明级数收敛性]]当中的经验，我们现在要：
> 1. 参考[[通过pi的无理测度证明级数收敛性#^57d4f2]],我们需要把$A_{\varepsilon}^c$上的情况变成形如$\sum_n \frac{e^{-nx_n}}{n}$形式的级数。然后我们需要进行dyadic分解，并按照$x_n$的值的分布进行划分，得到类似于$$\sum_{n\in B_k}\frac{e^{-nx_n}}{n}\leq \frac{1}{2^k}\sum_{j\geq 0} e^{-j}\#\left\{n\in B_k:x_n<\frac{j+1}{2^k}\right\}$$的结果。其中$B_k=[2^k,2^{k+1})$。
> 2. 然后我们剩下的步骤便是估计$\#\left\{n\in B_k:x_n<\frac{j+1}{2^k}\right\}$。令$$E(I;\rho):=\left\{n\in I:\delta_n\leq \rho\right\},\quad \rho<1$$实际上我们要估计的是$\#E(I;\rho)$。而这个估计主要是依靠[[通过pi的无理测度证明级数收敛性#^8f9f99]]，然后结合$\pi$的无理测度得到。其中关键是要得到$\delta_n$的一个下界估计，从而导出任意$n,m \in E(I;\rho)$的误差$|n-m|$的一个下界。

---

我们设$\mu=\mu(\pi)$是$\pi$的无理测度，根据[2020年的一个结果](https://arxiv.org/pdf/1912.06345)$2\leq \mu<7.2<\infty$。此外，$\mu(2\pi)=\mu(\pi)$于是，根据定义对任意$r>0$存在一个正实数$C_r>0$使得$$\left| \frac{p}{q}-2\pi\right|> \frac{C_r}{q^{\mu+r}}$$对任意正整数$p,q$成立。取$q^{*}$是使得$|\frac{p}{2\pi}-q|$最小的$q$。那么$$\text{dist}\left(\frac{p}{2\pi},\mathbb{Z}\right)=\left|\frac{p}{2\pi}-q^{*}\right|=\frac{q^{*}}{2\pi}|2\pi-\frac{p}{q^{*}}|\gtrsim_r (q^{*})^{-(\mu-1+r)}$$对于那些使得$\left|\frac{p}{2\pi}-q^{*}\right|<1$的$p,q^{*}$而言$q^{*}\asymp p$从而$$\text{dist}\left(\frac{p}{2\pi},\mathbb{Z}\right)\gtrsim_r p^{-(\mu-1+r)}\tag{2}$$现在考虑两个不同的整数$n,m\in E(I;\rho)$也就是说$\delta_n,\delta_m<\rho<1$，即存在两个整数$a,b$使得$$\left| \frac{n}{2\pi}-(\frac{1}{4}+a)\right|\leq \rho,\quad \left| \frac{m}{2\pi}-(\frac{1}{4}+b)\right|\leq \rho$$那么当我们考虑$\frac{n}{2\pi} \text{ mod }1,\frac{m}{2\pi} \text{ mod }1$这两个$\mathbb{R}/\mathbb{Z}$上的元素的差$\frac{n-m}{\pi} \text{ mod }1$到整数的距离$$\text{dist}\left(\frac{n-m}{2\pi},\mathbb{Z}\right)\le \left| \frac{n}{2\pi}-(\frac{1}{4}+a)\right|+\left| \frac{m}{2\pi}-(\frac{1}{4}+b)\right|\leq 2\rho\tag{3}$$令$p=|n-m|$结合$(2),(3)$我们得到$$p^{-(\mu-1+r)}\leq 2\rho\implies p\gtrsim_r \rho^{-\alpha}$$其中$\alpha=\frac{1}{\mu-1+r}$。

于是根据[[通过pi的无理测度证明级数收敛性#^8f9f99]]我们知道$$\# E(I;\rho)\lesssim_r(1+L\rho^{\alpha})\tag{4}$$其中$I$是一个区间，$L=|I|,\quad \alpha=\frac{1}{\mu-1+r}$。

---

由于$n=\frac{\pi}{2}+2k\pi +u$其中$|u|=2\pi \delta_n\in (0,\pi)$于是由于$\sin(n)=1-\cos(u)$此外$$\frac{1}{2}u^2\geq 1-\cos(u)\geq \frac{2}{\pi^2}u^2$$于是$$1-\sin(n)\asymp \delta_n^2\tag{5}$$于是根据$(1)$我们考虑的$n$是当$\sin(n)\approx 1$的那些正整数，此时$$(\frac{2}{3}+\frac{1}{3}\sin(n))^n=\exp(n\log(1-\frac{1}{3}(1-\sin(n))))\lesssim e^{-\frac{n}{3}(1-\sin(n))}\tag{6}$$令$$T_{k,j}:=\left\{n\in B_k:1-\sin(n)\in [\frac{j}{2^k},\frac{j+1}{2^k})\right\}$$那么根据$(5)$我们有$$T_{k,j}\subseteq E(B_k;\rho_{k,j}),\quad \rho_{k,j}:=C\sqrt{\frac{j+1}{2^k}}$$
* 理论上$\rho_{k,j}$可以很大，大于1，但此时$T_{k,j}$实际上是一个空集，因为$1-\sin(n)$就根本不可能大于1，所以也就不考虑这种情况了。

于是根据$(4)$,$$\begin{aligned}\#T_{k,j}&\leq \#E(B_k;\rho_{k,j})\\&\lesssim_r(1+2^k\rho_{k,j}^{\alpha})\\&\lesssim_r(1+C^{\alpha}2^{k(1-\alpha/2)}(j+1)^{\alpha/2}) \end{aligned}$$从而结合$(6)$，参照[[通过pi的无理测度证明级数收敛性#^57d4f2]]有$$\begin{aligned}\sum_{n\in B_k\cap A_{\varepsilon}^c}  \frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n}&\leq \frac{1}{2^k}\sum_{n\in B_k\cap A_{\varepsilon}^c} e^{-\frac{n}{3}(1-\sin(n))}\\&= \frac{1}{2^k}\sum_{n\in  B_k\cap A_{\varepsilon}^c}\sum_{j\geq 0} 1_{1-\sin(n)\in [\frac{j}{2^k},\frac{j+1}{2^k})}e^{-j/3}\\&\leq\frac{1}{2^k}\sum_{j\geq 0} e^{-j/3}\#\left\{n\in B_k\cap A_{\varepsilon}^c:1-\sin(n)<\frac{j+1}{2^k}\right\}\\&\leq \frac{1}{2^k}\sum_{j\geq 0} e^{-j/3}\#T_{k,j} \\&\lesssim_r \frac{1}{2^k}\sum_{j\geq 0} e^{-j/3}(1+C^{\alpha}2^{k(1-\alpha/2)}(j+1)^{\alpha/2}) )\\&\lesssim_r \frac{1}{2^k}+ 2^{-k\alpha/2}\end{aligned}\tag{7}$$因此$$\sum_{n\geq 1} \frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n}=\sum_{n\in A_{\varepsilon}}*+\sum_{n\in A_{\varepsilon}^{c}}*$$其中：
* 一开始我们便知道对于足够小的给定的$\varepsilon$都有$\sum_{n\in A_{\varepsilon}}\frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n}$收敛。
* 然后通过$(7)$我们知道$$\sum_{n\in A_{\varepsilon}^c}\frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n}=\sum_{k\geq 1}\sum_{n\in B_k \cap A_{\varepsilon}^c}\frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n} \lesssim_r \sum_{k\geq 1} \frac{1}{2^k}+2^{-k\alpha/2}<\infty$$
于是综上所述，目标级数收敛。

* 这个问题单纯通过对正整数集进行dyadic分解并不足以完成估计。在得到$$\frac{1}{2^k}\sum_{n\in B_k\cap A_{\varepsilon}^c} e^{-\frac{n}{3}(1-\sin(n))}$$之后，由于$1-\sin(n)\in (0,\varepsilon)$并且整体上震荡，我们不能根据单调性直接给出每个$B_k$块上的估计。不过由于$\{\frac{n}{2\pi}\}$在单位圆周上的性质，我们倒是可以根据$$\#\left\{n\in B_k\cap A_{\varepsilon}^c:1-\sin(n)<\frac{j+1}{2^k}\right\}$$给出上界信息。此外如果我们要得到下界信息，一开始我们的放缩可以变成$$\begin{aligned} \frac{1}{2^{k+1}}\sum_{n\in B_k\cap A_{\varepsilon}^c} e^{-\frac{n}{3}(1-\sin(n))}&=\frac{1}{2^{k+1}}\sum_{n\in  B_k\cap A_{\varepsilon}^c}\sum_{j\geq 0} 1_{1-\sin(n)\in [\frac{j}{2^k},\frac{j+1}{2^k})}e^{-j/3}\\&= \frac{1}{2^{k+1}}\sum_{j\geq 0} e^{-j/3}\#\{n\in B_k\cap A_{\varepsilon}^c:1-\sin(n)\in [\frac{j}{2^k},\frac{j+1}{2^k})\}\end{aligned}$$

### 2. 附带的一些问题

> [!note] 命题2.1
> 存在一个正实数$c>0$以及无穷多个正整数$n$使得$$\frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n}>\frac{c}{n}$$

* 这个结果可以解释为什么“命题0”并不平凡。我们无法通过把目标级数与$\sum_n \frac{1}{n^p},\quad p>1$来比较的方式得到目标级数的收敛性。

借助[[实数被一列超越数逼近的定量问题#^868b6e]]我们知道，存在无穷多个$n$使得$$\sin(n)>1-\frac{3}{n}$$于是$$\frac{2}{3}+\frac{1}{3}\sin(n)>\frac{2}{3}+\frac{1}{3}(1-\frac{3}{n})=1-\frac{1}{n}$$那么存在无穷多个$n$使得$$(\frac{2}{3}+\frac{1}{3}\sin(n))^n>(1-\frac{1}{n})^n\tag{A}$$那么由于$(1-\frac{1}{n})^n\to e^{-1}$，因此存在一个实数$c>0$对于足够大的$n$都有$(1-\frac{1}{n})^n>c$。因此存根据$(A)$，存在无穷多个正整数$n$使得$$\frac{(\frac{2}{3}+\frac{1}{3}\sin(n))^n}{n}>\frac{c}{n}$$

> [!note] 命题2.2  
> 令$a_n := (\frac{2}{3}+\frac{1}{3}\sin(n))^n$那么$$\limsup_{n\to \infty} a_n =1,\quad \liminf_{n\to \infty} a_n =0$$

* 这个结果可以解释为什么“命题0”并不平凡。如果我们考虑用root test去判断目标级数的收敛与发散性，由当前这个结果我们便知道$\sum_n \frac{a_n}{n} z^n$的收敛半径为1，从而无法通过收敛半径判断级数$\sum_n \frac{a_n}{n}$是否收敛。

首先说明下极限。

根据[[证明正弦函数在整数上取值的序列的极限是不存在的#^8ddc54]]序列$\sin(n)$在区间$[-1,1]$上稠密,因此存在无限多个$n$使得$\sin(n)\leq c<1$从而$$a_n \leq (\frac{2}{3}+\frac{c}{3})^n \to 0$$于是存在一个该序列的子列$a_{n_k}\to 0$，那么根据序列下极限的意义(参考[[序列的上下极限]])我们知道$$\liminf_{n\to \infty} a_n =0$$
然后说明上极限。

由于$$a_n =\left(1-\frac{1-\sin(n)}{3}\right)^n$$如果我们可以证明，存在无穷多个$n$使得$1-\sin(n)=o(1/n)$那么就会存在一个子列$a_{n_j}\to 1$，从而证明序列的上极限大于等于1，从而证明上极限就是1。

联想到上一节为了证明级数收敛得到的中间结果$$1-\sin(n)\asymp \delta_n^2\tag{B}$$其中$\delta_n:=\text{ dist}(\frac{n}{2\pi},\frac{1}{4}+ \mathbb{Z})=||\frac{n}{2\pi}-\frac{1}{4}||$。根据[[实数被一列超越数逼近的定量问题#^1e4722]]这个Khinchine的非齐次逼近的结果，令$d>\frac{1}{\sqrt{5}}$那么存在无穷多个$n$使得$$||\frac{n}{2\pi}-\frac{1}{4}||\leq \frac{d}{n}$$那么结合$(B)$我们知道存在无穷多个$n$使得$$1-\sin(n)=O(\frac{1}{n^2})$$因此根据前面的分析，一定存在一个子列$1-\sin({n_j})=O(\frac{1}{n_j^2})$从而使得$a_{n_j}\to 1$，因此序列$a_n$的上极限为1。



> [!question] 猜想3.3  
> 令$a_n := (\frac{2}{3}+\frac{1}{3}\sin(n))^n$那么序列在$[0,1]$当中稠密。
