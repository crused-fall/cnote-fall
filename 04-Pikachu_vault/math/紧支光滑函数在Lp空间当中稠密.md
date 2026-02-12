---
tags:
  - math
  - 实分析
  - 调和分析
---
> [!note] 命题0
> $C_c^{\infty}(\mathbb{R}^d)$在$L^p(\mathbb{R}^d)$当中稠密。

我们想到对任意一个$f \in L^p(\mathbb{R}^d)$存在一个函数$g_{\varepsilon}$使得$||f-g_{\varepsilon}||_{L^p}<\varepsilon$，其中$g_{\varepsilon}\in C_c^{\infty}(\mathbb{R}^d)$。既然要光滑逼近，那么很自然想到[[通过添加参数让目标更光滑化#1.1 让函数与Mollifier做卷积]]，也就是说找到一个Mollifier $\psi_{\lambda}\in C_c^{\infty}(\mathbb{R}^d)$。如果我们直接考虑$f*\psi_{\lambda}$，这个函数倒是获得了光滑性，并且可以$L^p$逼近$f$。但是这并不保证$f*\psi_{\lambda}$是紧支的函数，比如下面的例子：

> [!example] 例子1
> 考虑$f(x):=1_{[0,1]}(x)$这是一个紧支的函数。然后考虑$g(x)=1,x\in \mathbb{R}$这不是一个紧支的函数。二者的卷积$$f*g(y):=\int_{\mathbb{R}}f(x)g(y-x)\,dx=\int_{[0,1]}1\,dx=1,\forall y\in \mathbb{R}$$$\text{supp}(f*g)\subseteq \overline{\text{supp }f+\text{supp }g}$ 的确是满足的，因为$[0,1]+\mathbb{R}=\mathbb{R}$然后$\mathbb{R}\subseteq \mathbb{R}$也确实没问题。

所以我们希望搭建一个即能$L^p$逼近$f$又具有紧支的函数作为中间的桥梁：
1. 令$f_{R}:=f1_{|x|\leq R}$。积分的绝对连续性向我们保证，这个函数$L^p$逼近到$f$。同时这个函数是具有紧支的。
2. 根据[[函数卷积的基本性质#1.4 卷积支集的性质]]，$f_{R}*\psi_{\lambda}$具有紧支。

那么我们可以利用三角不等式完成证明：

首先对任意的$\varepsilon >0$都存在一个截断函数$f_{R_\varepsilon}$其具有紧支集，并且使得$$||f-f_{R_\varepsilon}||_{L^p}<\frac{\varepsilon}{2}$$然后因为$f_{R}*\psi_{\lambda}$依$L^p$范数收敛到$f_R$，于是相应的存在$\lambda_{\varepsilon}$使得
$$||\psi_{\lambda_{\varepsilon}}*f_{R_\varepsilon}-f_{R_\varepsilon}||_{L^p}<\frac{\varepsilon}{2}$$因此由三角不等式可以,对任意的$\varepsilon>0$存在$\psi_{\lambda_{\varepsilon}}*f_{\varepsilon} \in C_c^{\infty}$，由三角不等式满足$$\begin{aligned}||f-\psi_{\lambda_{\varepsilon}}*f_{R_\varepsilon}||_{L^p}&\leq ||f-f_{R_\varepsilon}||_{L^p}+||\psi_{\lambda_{\varepsilon}}*f_{R_\varepsilon}-f_{R_\varepsilon}||_{L^p} \\&<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}=\varepsilon\end{aligned}$$令$g_{\varepsilon}:=\psi_{\lambda_{\varepsilon}}*f_{R_\varepsilon}$这是一个$C_c^{\infty}(\mathbb{R}^d)$当中的函数，因此$C_c^{\infty}(\mathbb{R}^d)$在$L^p(\mathbb{R}^d)$当中稠密。

