---
tags:
  - math
  - 组合学
  - 概率论
  - 数论
---
> [!定理1，Erdos(1965)]
> 任意的不包含0的n个整数构成的集合$S$必然存在一个元素个数大于n/3的sum-free的子集。

* $A\subset \mathbb{Z}$称之为一个sum-free set，如果对于任意的$a,b,c\in A$方程$a+b=c$都不能被满足。比如说$\{1,2,4\}$这样的集合。
* 我们可以把这个结果推广到任意的交换群$(G,+)$上。$A\subset G$称之为sum-free的，如果$$(A+A)\cap A=\varnothing$$其中$A+A:=\{a+b:a,b\in A\}$。或者简写为$2A\cap A=\varnothing$。
* 一些简单的观察会发现，因为群$G$本身是有着加法结构的，那么当子集$A$的元素个数很大的时候，它就越不太可能是一个sum-free的子集，但问题是，sum-free子集究竟能有多大呢？这里Erdos给出了一个解答，指出至少可以找出一个尺寸至少$\frac{n}{3}$的sum-free的子集。
* [Alon and Kleitman(1990)](https://mathscinet.ams.org/mathscinet/relay-station?mr=1117002):“定理1”可以提升到$\frac{n+1}{3}$
* [Bourgain(1997)](https://mathscinet.ams.org/mathscinet/relay-station?mr=1441239):“定理1”还可以提升到$\frac{n+2}{3}$。这是目前为止最好的结果。
* 人们猜测，我们可以找到一个函数$f$，满足$f(n)\to +\infty$，使得上述结果提升到$\frac{n+f(n)}{3}$。目前这还是一个公开问题。

### 1. 思路1：概率法

如果我们可以找到一个足够大的素数$p$使得$S\subset \mathbb{Z}$当中任意两个元素模p都不在同一个剩余类当中。也就是说我们可以把$S$通过一个同态映射$$\psi_p:\mathbb{Z}\to \mathbb{Z}_p$$使得$$S':=\psi_p(S)$$并且使得$|S|=|S'|$。

* 比如说$S:=\{1,2,3,4,5\}$，我们选用一个素数$p=11$，那么对应到$\mathbb{Z}_{11}$的一个子集$S':=\{\mathbf{1},\mathbf{2},\mathbf{3},\mathbf{4},\mathbf{5}\}$当中。

这样做并不影响$S$的sum-free的子集$B$的尺寸。我们可以定义$B\subset S$经过映射$\psi_p$以后的集合$B':=\psi_p(B)$只要$p$足够大，我们就有$|B|=|B'|$，并且$$2B\cap B=\varnothing \iff 2B'\cap B'=\varnothing$$于是我们便可以在$\mathbb{Z}_p$当中讨论整个问题。

下面我们将看到整个证明过程中，我们多次利用$\mathbb{Z}_p$作为一个有限域的性质，无论是构造随机变量还是考虑元素的逆元等等。

* 这一点在[[EGZ定理的证明]]当中亦有体现。

此时如果我们可以证明在$S'$当中随机选取一个sum-free的子集，然后如果可以证明其对应的集合尺寸的随机变量的期望大于$n/3$，那么根据[[通过求期望证明具有某种性质的结构的存在性]]的想法，我们就能$S'$当中存在一个尺寸大于$n/3$的sum-free子集。

Erdos给出的构造思路：

如果我们选取一个足够大的形如$3k+2$的素数$p$，使得我们可以把$\mathbb{Z}_p\setminus\{0\}$分为两个部分(最后多一个元素出来):$$\mathbb{Z}_p\setminus\{0\}=\{\mathbf{-k},\cdots,\mathbf{-1},\mathbf{1},\cdots,\mathbf{k}\}\cup \{\mathbf{k+1},\cdots,\mathbf{2k+1}\}$$从而使得$$S' \subset \{\mathbf{-k},\cdots,\mathbf{-1},\mathbf{1},\cdots,\mathbf{k}\}$$当中。

令$\omega \in \mathbb{Z}_p\setminus\{0\}$是一个可逆元素，由于$\{\mathbf{k+1},\cdots,\mathbf{2k+1}\}$是$\mathbb{Z}_p\setminus\{0\}$的一个sum-free的子集，那么$\omega\cdot \{\mathbf{k+1},\cdots,\mathbf{2k+1}\}$也是sum-free的，而sum-free子集的子集也一定是sum-free的，那么$$\begin{aligned}B&:=S'\cap \omega\cdot \{\mathbf{k+1},\cdots,\mathbf{2k+1}\}\\&= \{s\in S':s\omega^{-1}\in\{\mathbf{k+1},\cdots,\mathbf{2k+1}\} \}\end{aligned}$$也是一个sum-free的子集。接下把问题赋予概率意义：

以$\mathbb{Z}_p\setminus \{\mathbf{0}\}$为样本空间，幂集为sigma代数，定义均匀概率测度$$\forall a \in \mathbb{Z}_p\setminus \{\mathbf{0}\},P(\{a\})=\frac{1}{p-1}$$进一步任意子集$A\subseteq \mathbb{Z}_p\setminus \{\mathbf{0}\}$,$$P(A)=\frac{|A|}{p-1}$$
如此一来$|B|:\mathbb{Z}_p\setminus\{0\}\to \mathbb{N}$可以构造成一个随机变量。$|B|$的期望可以写成：$$\begin{aligned}\mathbb{E}(|B|)&=\mathbb{E}\left(\sum_{s\in S'}1_{s\in B}\right)\\&=\sum_{s\in S'}\mathbb{E}(1_{s\in B})\\&= \sum_{s\in S'}P(s\in B)\\&= \sum_{s\in S'}P(s\omega^{-1}\in \{\mathbf{k+1},\cdots,\mathbf{2k+1} \})\\&= \sum_{s\in S'}\frac{k+1}{3k+1}\\&>\frac{|S'|}{3}\end{aligned}$$
* 令$A:=\{\mathbf{k+1},\cdots,\mathbf{2k+1} \}$那么对于固定的$s$，$P(s\omega^{-1} \in A)$满足条件的$\omega$的集合实际上就是$sA^{-1}$，假设$A^{-1}$为$A$中元素的逆元构成的集合。如此一来$s\neq \mathbf{0}$，于是$|sA^{-1}|=|A|$，于是由于概率测度的定义$$P(s\omega^{-1} \in A)=\frac{|A|}{p-1}=\frac{k+1}{3k+1}>\frac{1}{3}$$最后的不等式用“糖水不等式”一眼能看出来。参考：[[收敛的连乘积的上界估计与糖水不等式]]

于是由[[通过求期望证明具有某种性质的结构的存在性]]中总结的想法，既然随机变量的期望是大于$n/3$的，那么一定存在样本空间当中的某个固定的$\omega_0$，对应一个具体的$$\begin{aligned}B_0&:=S'\cap \omega_0\cdot \{\mathbf{k+1},\cdots,\mathbf{2k+1}\}\end{aligned}$$其为一个sum-free子集，并且$|B_0|>\frac{n}{3}$，如此一来便证明了这样的集合的存在性。


