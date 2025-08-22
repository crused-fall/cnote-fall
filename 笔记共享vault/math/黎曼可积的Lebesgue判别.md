---
tags:
  - math
  - 实分析
---
> [!黎曼可积的Lebesgue等价条件，Lebesgue& Vitali 1907]
> 闭区间$[a,b]$上的有界函数$f$黎曼可积当且仅当函数$f$是在此闭区间上几乎处处连续的。

* 关于黎曼积分，以及黎曼可积函数的基本内容参考[[黎曼积分的定义以及黎曼可积的判别]]。

这里我们假设我们已知函数黎曼可积的Darboux充要条件，那么我们只需要证明Lebesgue充要条件与Darboux条件的等价性即可。

#### 1. 如果黎曼可积，那么函数几乎处处连续

从振幅的观点来说，所谓几乎处处连续，也就是说集合$$C:=\{x\in I_{a,b}:\omega_f(x)>0\}$$这个集合是Lebesgue零测度的。那么按照[[an epsilon of room证明集合为0测度的策略]]中的策略，我们无非就是要证明等价的命题，即对于任意的$r>0$集合$$C_r:=\{x\in I_{a,b}:\omega_f(x)\geq r\}$$是Lebesgue零测度的，因为相对而言后者会更好操作一些。那么现在我们无非就是要通过达布条件来得到一个对$C_r$的覆盖，并证明这种覆盖的Lebesgue外测度可以小于任意$\varepsilon>0$。（就像我们在[[无理测度的定义以及基本的命题]]中1.3中做的一样）

黎曼可积的达布条件告诉我们，我们可以通过调整划分$P$，$$U(f,P)-L(f,P)=\sum_{k=1}^n (M_k-m_k)|I_k|$$使得达布上和与下和的差任意小。

现在假设$a\in C_r$那么此点一定在某个$I_{k_0}$里面，那么由于振幅的基本性质，于是$$r\leq \omega_f(a)\leq M_{k_0}-m_{k_0}$$这也就是说，如果有某一个$I_{k_0}$包含了$C_r$中任何一个点，那么这个区间上函数上确界与下确界之差至少是$r$。那么为了让覆盖$C_r$的区间的总测度任意小，我们可以对任意$r\varepsilon>0$选取一个划分$P_{r\varepsilon}$使得$$U(f,P_{r\varepsilon})-L(f,P_{r\varepsilon})=\sum_{k=1}^n (M_k-m_k)|I_k|<r\varepsilon$$这样一来，所有含有$C_r$中元素的子区间$I_{k_i}$组成的和有$$\sum_{I_{k_i}\cap C_r\neq 0} (M_{k_i}-m_{k_i})|I_{k_i}|\leq \sum_{k=1}^n (M_k-m_k)|I_k|<r\varepsilon$$如此一来由于$M_{k_i}-m_{k_i}\geq r$那么$$\sum_{I_{k_i}\cap C_r\neq 0} |I_{k_i}|<\varepsilon$$
这就是我们想要的结果，覆盖$C_r$的集合的测度是任意小的，于是$C_r$是零测度的，这对于任意$r>0$成立，于是$C$是零测度的，于是$f$是几乎处处连续的函数。

#### 2. 如果函数几乎处处连续，那么黎曼可积

我们的目标无非是说，对于任意的$\varepsilon$我们都可以找到一个对区间$[a,b]$的划分$P_{\varepsilon}$都有$U(f,P_{\varepsilon})-L(f,P_{\varepsilon})<\varepsilon$。

而我们现在知道的是，任意的$C_r$是零测度的。很快我们就会发现，我们有必要分开处理划分$P_{\varepsilon}$中的两种不同的区间，因为那些覆盖$C_r$的区间其区间长度的总和可以任意小，而剩下的区间中，区间上函数的振幅可以非常小。所以[[分段估计]]$U(f,P_{\varepsilon})-L(f,P_{\varepsilon})$这个和是非常必要的。

我们现在可以把划分$P$分为两个部分，$A$是那些与$C_r$交集不为空的区间组成的集合，而$B$则是剩下的区间。

* 对于与$C_r$不交的这部分:
我们为了让$\sum_{I_k\in B} (M_{k}-m_{k})|I_{k}|$足够小,此时我们能做的是通过选择合适的$r_{\varepsilon}$来使得$M_{k}-m_{k}$尽可能小。

因为此时区间$I_k$不包含任意$C_{r_{\varepsilon}}$的点，因此任意$x \in I_k$都有$\omega_f(x)<r_{\varepsilon}$，于是由振幅的基本性质$$M_k-m_k=\omega_f(I_k)\leq r_{\varepsilon}$$我们可以选择$r_{\varepsilon}= \frac{\varepsilon}{2(b-a)}$，从而$$\sum_{I_k\in B} (M_{k}-m_{k})|I_{k}|\leq r_{\varepsilon}\sum_{I_k\in B} |I_{k}|\leq\frac{\varepsilon}{2(b-a)}(b-a)=\frac{\varepsilon}{2} $$
* 对于覆盖$C_r$的这部分：
我们为了让$\sum_{I_k\in A} (M_{k}-m_{k})|I_{k}|$足够小，我们需要利用覆盖$C_{r_{\varepsilon}}$的区间长度总和任意小这一点来控制$(M_{k_i}-m_{k_i})|I_{k_i}|$的上界。我们可以令$|I_{k}|$的总和小于$\frac{\varepsilon}{2M}$，如此一来$$\sum_{I_k\in A} (M_{k}-m_{k})|I_{k}|\leq M\sum_{I_k\in A} |I_{k}|<\frac{\varepsilon}{2}$$
当然我们这里需要补充说明，$C_{r_{\varepsilon}}$因为是一个紧集，因此我们可以对其进行有限覆盖，因此我们才可以找到有限个体积总和任意小的$\{I_{k}\}$对其进行覆盖。

那么满足这样的条件的划分$P_{\varepsilon}$就是我们需要的合适的划分，于是最后我们可以得出结论，对任意的$\varepsilon>0$存在划分$P_{\varepsilon}$使得$$\begin{aligned}U(f,P_{\varepsilon})-L(f,P_{\varepsilon})&=\sum_{I_k\in A} (M_{k}-m_{k})|I_{k}|+\sum_{I_k\in B} (M_{k}-m_{k})|I_{k}|\\&<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}=\varepsilon\end{aligned}$$