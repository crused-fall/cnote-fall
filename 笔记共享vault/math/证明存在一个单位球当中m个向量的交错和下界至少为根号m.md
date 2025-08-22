---
tags:
  - math
  - 概率论
  - 线性代数
  - 组合学
  - 中学数学竞赛
---

> [!问题1]
> $v_1,...,v_m$是$\mathbb{R}^n$当中的m个单位向量，证明存在这样一组整数$r_1,...,r_m \in \{-1,1\}$使得:$$||r_1v_1+...+r_mv_m||_2 \geq \sqrt{m}$$

对于这种存在性的问题考虑[[通过求期望证明具有某种性质的结构的存在性]]：

1.  **问题要证明的存在的结构**:$Y = r_1v_1+...+r_mv_m$
2.  **这个结构需要满足的性质**:$||r_1v_1+...+r_mv_m|| \geq \sqrt{m}$
3.  **如何把这个结构所包含的性质转换为一个随机变量?**

首先把结构给随机化，把$r_i$替换为参数为1/2的Bernoulli随机变量$\xi_i$的取值,即考虑$\xi_i:\Omega \to \{-1,1\}$，$\xi_i(\omega) = r_i$，这是m个独立同分布的随机变量。然后定义$$X(\omega) =
    ||\xi_1(\omega)v_1+...+\xi_m(\omega)v_m||^2$$为一个新的随机变量,那么现在只需要证明:$$E(X)
    \geq m$$
4.  **算期望**，并意识到线性性的存在:$$\begin{aligned}X
    &= \left\langle \sum_{i = 1}^{m} \xi_iv_i,\sum_{i = 1}^{m}
    \xi_iv_i\right\rangle \\ &= \sum_{1\leq i,j\leq m}
    \xi_i\xi_j \langle v_i,v_j \rangle
    \end{aligned}$$然后我们意识到，在求期望的过程中$E(\xi_i) = 0,E(\xi_i^2)=1$，于是我们意识到区分$E(\xi_i\xi_j),i\neq j$以及$E(\xi_i^2)$的必要性，于是$$X =
    \sum_{i=1}^{m}\xi_i^2||v_i||^2 + \sum_{i\neq
    j}\xi_i\xi_j \langle v_i,v_j \rangle$$于是$$E(X) =
    \sum_{i=1}^{m} E(\xi_i^2) = m$$
5.  **结论**：一定存在$\omega_0\in \Omega$使得:$$X(\omega_0) = \xi_1(\omega_0)v_1+...+\xi_m(\omega_0)v_m
    = r_1v_1+...+r_mv_m$$使得值$X(\omega_0) \geq m$成立。

（如果该问题当中的范数不是2范数而是p范数，那么期望应该如何计算，或者如何估计？参考[Khintchine inequality](https://en.wikipedia.org/wiki/Khintchine_inequality)）

当然利用$E(X)=m$这个结果，我们还可以证明一定存在这样一组整数$r_1,...,r_m \in \{-1,1\}$使得:$$||r_1v_1+...+r_mv_m||_2 \leq \sqrt{m}$$


