---
tags:
  - math
  - 线性代数
  - 大学数学竞赛
---

> [!note] 命题0（大学生数学竞赛）
> $A,B\in M_n(\mathbb{C})$为两个Hermitian矩阵，那么$$\text{Tr}((AB)^2)\leq \text{Tr}(A^2B^2)$$

* 如果$AB=BA$那么$$(AB)^2=ABAB=A^2B^2$$不等式在这种情况下取等。
* 其次，这里的不等式首先需要保证$(AB)^2,A^2B^2$分别对应的trace是实数。这一点能保证，是因为$AB,A^2,B^2$都是Hermitian矩阵,Hermitain矩阵的乘积的trace总是实数。


> [!note] 引理1:Hermitain矩阵乘积的trace为实数
> $A,B\in M_n(\mathbb{C})$为两个Hermitian矩阵那么$$\text{Tr}(AB)\in \mathbb{R}$$

* 我们首先可以按照trace的定义证明$$\begin{aligned}\text{Tr}((AB)^{\dagger})&=\text{Tr}(\overline{(AB)^{T}})\\&=\overline{\text{Tr}((AB)^{T})}\\&=\overline{\text{Tr}(AB)} \end{aligned}$$另一方面$$\begin{aligned}\text{Tr}((AB)^{\dagger})&= \text{Tr}(B^{\dagger}A^{\dagger})\\&=\text{Tr}(BA) \\&= \text{Tr}(AB)\end{aligned}$$于是我们知道$$\overline{\text{Tr}(AB)}=\text{Tr}(AB)$$于是就有$\text{Tr}(AB)\in \mathbb{R}$。

然后我们来证明目标不等式，我们需要估计的是$$\text{Tr}((AB)^2)- \text{Tr}(A^2B^2)\leq 0$$针对估计两个trace差的上界，我们想到最好是通过trace的线性性质把它变成一个矩阵的trace的上界估计，这样问题会更简单一些。

于是我们的目标是搞清楚矩阵$(AB)^2-A^2B^2=ABAB-AABB$的上界估计。关于这个矩阵，我们联想到一个恒等式$$[A,B]^2=(AB-BA)^2=ABAB-ABBA-BAAB+BABA$$
因为trace对于矩阵交换性的不变性，对于多个矩阵相乘的trace就是循环不变性。于是上面的恒等式以及一开始的问题中涉及的5个矩阵如果按照trace相等划分等价类，那么$ABAB,BABA$是一类，$ABBA,AABB,ABBA$是一类。于是$$\text{Tr}((AB-BA)^2)=2\text{Tr}(ABAB-AABB)=2\text{Tr}((AB)^2-A^2B^2)$$这样做的好处是，我们实际上知道$[A,B]^2$trace的上界。

转换为$[A,B]^2$的trace的估计，是因为$[A,B]$是skew-Hermitian矩阵，关于这样的矩阵的平方的trace有下面的结果：

> [!note] 引理2
> $A\in M_n(\mathbb{C})$是一个skew-Hermitian矩阵，那么$$\text{Tr}(A^2)\leq 0$$

为了证明这件事，我们还需要：

> [!note] 引理3
> $C\in M_n(\mathbb{C})$是一个半正定的Hermitian矩阵当且仅当存在一个$B\in M_n(\mathbb{C})$使得$$C=B^{\dagger}B$$


> [!note] 引理4
> $A\in M_n(\mathbb{C})$是一个Hermitian矩阵那么$A^2$是半正定矩阵。

* 按照半正定矩阵的定义，对于任意$x\in \mathbb{C}^n$我们需要证明$x^{\dagger}A^2x$是非负的。由于$(Ax)^{\dagger}=x^{\dagger}A^{\dagger}=x^{\dagger}A$因此如果令$y=Ax$，那么$$x^{\dagger}A^2x=(Ax)^{\dagger}(Ax)=y^{\dagger}y\geq 0$$
---

现在我们来证明“引理2”。

在“引理2”中，因为$A$是skew-Hermitian矩阵，那么存在一个Hermitain矩阵$H$，使得$A=iH$，从而$A^2=-H^2$。于是$$\text{Tr}(A^2)=-\text{Tr}(H^2)$$由于"引理4"，我们知道$H^2$是一个半正定的Hermitian矩阵，那么按照“引理3”,存在$B\in M_n(\mathbb{C})$使得$$\text{Tr}(A^2)=-\text{Tr}(H^2)=-\text{Tr}(B^{\dagger}B)$$而我们可以断言$\text{Tr}(B^{\dagger}B)\geq 0$，从而$\text{Tr}(A^2)\leq 0$。

而之所以$\text{Tr}(B^{\dagger}B)\geq 0$，我们可以从trace的定义得到。因为$$\text{Tr}(B^{\dagger}B)=\sum_{i=1}^n (B^{\dagger}B)_{ii}$$其中$$\begin{aligned}(B^{\dagger}B)_{ii}&=\sum_{k=1}^{n}B^{\dagger}_{ik}B_{ki}\\&=\sum_{k=1}^{n}\overline{B_{ki}}B_{ki}\\&= \sum_{k=1}^{n}|B_{ki}|^2\geq 0 \end{aligned}$$从而最后得到trace非负。

---

最后综上所述：$$\begin{aligned}\text{Tr}((AB)^2)- \text{Tr}(A^2B^2)&= \text{Tr}((AB-BA)^2)\end{aligned}$$其中因为$(AB-BA)$为skew-Hermitian矩阵，因此平方的trace是非正实数，从而$$\text{Tr}((AB)^2)- \text{Tr}(A^2B^2)\leq 0$$