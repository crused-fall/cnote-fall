---
tags:
  - math
  - 线性代数
---
> [!note] 命题0（Jacobi's formula）
> $A\in M_n(\mathbb{C})$那么$$\det(e^{A})=e^{\text{Tr}(A)}$$

### 1. an epsilon of room风格的证明

> [!tip] 基本想法1.1
> 根据[[an epsilon of room在线性代数中的运用]]，我们首先想到这个命题对于$M_n(\mathbb{C})$的一个稠密子集$D$，全体可对角化矩阵成立。因为如果$B\sim \Lambda:=\text{diag}\{d_1,\cdots,d_n\}$那么自然$\exp(A)\sim \exp(\Lambda)$,而行列式是相似不变量,于是$$\det(\exp(A))=\det(\exp(\Lambda))=\det(\text{diag}\{d_1,\cdots,d_n\})=\prod_{i=1}^n e^{d_i}=e^{\text{Tr}(\Lambda)}$$所以我们最终为了使用[[identity theorem]]，我们只需要验证映射$$f:M_n(\mathbb{C})\ni X\mapsto \det(e^{X})-e^{\text{Tr}(X)}$$在矩阵范数下是连续的。如果这件事成立，那么我们由可逆矩阵的情况就可以自然推广到整个$M_n(\mathbb{C})$上。

因为我们知道$e^x,\text{Tr}(X),\det(X)$以及两个$M_n(\mathbb{C})\to \mathbb{C}$的连续映射做差也是连续的，所以其实我们唯一要验证的就是$e^X$的连续性。

> [!note] 引理1.2
> $X,Y\in M_n(\mathbb{C})$对于任意矩阵范数有:
> $$||\exp(X+Y)-\exp(X)||\leq ||Y|| \exp(||X||)\exp(||Y||)$$

这就能帮助我们说明$\exp(X)$的连续性，因为对任意$1>\varepsilon>0$，都有假设$||X-Y||<\delta_{\varepsilon}=\min\{\frac{\varepsilon}{L},1\}$,其中$L=\exp(||X||+1)$。那么由于引理，我们得到$$\begin{aligned}||\exp(X)-\exp(Y)||&\leq ||X-Y|| \exp(||X-Y||)\exp(||X||)\\&<\delta_{\varepsilon} e^{\delta_{\varepsilon}}\exp(||X||)\\&<\varepsilon \end{aligned}$$
* 甚至我们还知道$X\mapsto \exp(X)$是Lipschitz连续的映射。

因此由[[an epsilon of room在线性代数中的运用]]中的想法"命题0"成立。

---

如果想要避免"引理1.2",我们可以用更简单的方式利用[[identity theorem]]。

我们想到对于任意的矩阵$A$，按照[[可对角化矩阵在复矩阵空间当中稠密#1. Schur分解的做法]]当中的构造，对$A$考虑Schur分解$$A=UTU^{\dagger}$$然后令$$A_t:=U(T+t\Lambda)U^{\dagger}$$
其中$\Lambda:=\text{diag}\{d_1,\cdots,d_n\}$其对角线元素各不相同。此时$A_t$是一个可对角化矩阵，并且可以通过调整$t$，使得在范数上$A_t$任意接近$A$。

那么我们可以考虑$$g(t):=\det(e^{A_t})-e^{\text{Tr}(A_t)}$$我们的目标是证明$g(0)=0$。然后我们已知的是$t\neq 0$的时候$g(t)=0$。那么只要$g(t)$在包含$0$的一个开区间上是连续的，那么[[identity theorem]]就告诉我们，$f(t)$在此开区间上恒等于0，于是自然有$g(t)=0$。由于$$\begin{aligned}g(t)&=\det(e^A)\det(e^{t\Lambda})-e^{\text{Tr}(A)}e^{t\text{Tr}(\Lambda)}\\&=e^{t\text{Tr}(\Lambda)}(\det(e^A)-e^{\text{Tr}(A)}) \end{aligned}$$这当然是一个关于$t$的连续函数，因为$e^{ta}$关于$t$是连续的，于是$g(t)$自然是连续的。

于是"identity theorem"告诉我们$g(0)=0$，于是命题成立。

### 2. 直接利用Schur分解证明

