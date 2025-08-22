---
tags:
  - math
  - 实分析
  - 泛函分析
---
> [!问题1]
> 全体复三角多项式组成的集合在$L^p([a,b]\to \mathbb{C}),1\leq p<\infty$当中稠密。


> [!主要想法]
> 主要的思路是：
> 1.  复三角多项式在$C(\mathbb{T}\to \mathbb{C})$当中稠密的。（在一致范数意义下）
> 2.  $C(\mathbb{T}\to \mathbb{C})$在$C([a,b]\to \mathbb{C})$当中是稠密的。(在$L^p$度量的意义下)
> 3.  $C([a,b]\to \mathbb{C})$在$L^p([a,b]\to \mathbb{C})$当中是稠密的。(这部分是已知的，我们甚至可以做到光滑逼近,参考[[紧支光滑函数在Lp空间当中稠密]])
> 
> 如果以上三点都正确，那么对于某个固定的$f \in L^p([a,b]\to \mathbb{C})$：
> 
> 1. 对任意的$\varepsilon>0$存在一个$g_{\varepsilon}\in C([a,b]\to \mathbb{C})$使得$$||f-g_{\varepsilon}||_{L^p}<\varepsilon$$
> 2. 那么也存在一个$h_{\varepsilon}\in C(\mathbb{T}\to \mathbb{C})$使得$$||g_{\varepsilon}-h_{\varepsilon}||_{L^P}<\varepsilon$$
> 3. 也存在一个复三角多项式$T_{\varepsilon}$使得$$||T_{\varepsilon}-h_{\varepsilon}||_u<\varepsilon\implies ||T_{\varepsilon}-h_{\varepsilon}||_{L^p}<(b-a)\varepsilon$$
> 于是我们便可以得到:$$\begin{aligned}||f-T_{\varepsilon}||_{L^p}&\leq ||f-g_{\varepsilon}||_{L^p}+||g_{\varepsilon}-h_{\varepsilon}||_{L^P}+||T_{\varepsilon}-h_{\varepsilon}||_{L^p}\\&<2\varepsilon+(b-a)\varepsilon \\&=(b-a+2)\varepsilon\end{aligned}$$
> 这对任意的$\varepsilon>0$成立，因此稠密性可以得到证明。

### 1. 复三角多项式在$C(\mathbb{T}\to \mathbb{C})$当中稠密

首先我们可以直接用[[Stone-Weierstrass定理]]来说明，这一点在[[模1均匀分布与Weyl判别]]的1.2当中已经做了说明。当然一个更为构造性的证明，可以在[[Dirichlet核不是逼近单位，Fejer核是逼近单位元]]的第二节的“推论2.5”中看到。这个定理告诉我们，我们可以通过让$f$与Fejer和做卷积来制造出这样一个具体的一致逼近于$f$的三角多项式。

### 2. $C(\mathbb{T}\to \mathbb{C})$在$C([a,b]\to \mathbb{C})$当中是稠密

$f \in C([a,b]\to \mathbb{C})$如果函数满足$f(a)=f(b)$那么我们是可以找到一个对应的函数$F \in C(\mathbb{T}\to \mathbb{C})$从而使得二者的值相等，即$$F(e(x))=f(x)$$其中$e(x)\in \mathbb{T}$是单位圆周上的元素。闭区间$[a,b]$上的连续函数未必满足两个端点是相等的，即有可能$f(b)\neq f(a)$。不过虽然函数在端点处高度有差距，但是函数围城的"面积"(也就是积分)可以非常靠近。

这里面证明是构造性的，也就是对于任意的一个$f\in C([a,b])$,我都能找到一个$\{f_n(x)\}\subseteq C(\mathbb{T})$,使得:$$||f_n(x)-f(x)||_{L^2}\to0$$这里面的想法是简单的，两个函数空间里面的函数唯一的差别主要是端点位置上是否相等。

对于任意的一个$f(x)$,为了使得它的端点是相等的，我们可以固定比如$f(b)$,然后函在$[a,a+\frac{1}{n})$里面，把点$(a+1/n,f(a+1/n))$与点$(a,f(b))$连接起来，这样组成的新的函数$f_n(x)$在$[a+1/n,b]$这个范围内是完全相等的，差异主要在$[a,a+\frac{1}{n})$里面。因为这个构造，后面部分是直线，因此可以写出来这里面的构造:$$f_n(x)=\begin{cases}f(x)&b\geq x\geq a+1/n\\f(b)+nx(f(a+1/n)-f(b))&a+1/n>x\geq a\end{cases}$$考虑范数下的收敛:$$||f_n(x)-f(x)||_{L^2}\leq\frac{2||f||_{u}}{\sqrt{n}}\to0$$这里的差距很小是因为$L^p$范数差不多相当于函数与x轴形成的面积的大小，可以参考下面的图形:
![[复三角多项式在Lp空间中的稠密性 pic1.png]]

