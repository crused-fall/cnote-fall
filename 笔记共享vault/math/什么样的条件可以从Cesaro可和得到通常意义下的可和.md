---
tags:
  - math
  - 实分析
---
### 1. $S_n$非负不减

> [!定理1.1]
> 序列$a_n$如果是Cesaro可和的，并且其对应的部分和$S_n$非负不减少，那么$a_n$是可和的，其部分和$S_n$的极限存在且与Cesaro和相等。

对于不减的实数序列$S_n$想要证明其极限的存在，我们只需要证明其具有上界即可。

令$$\sigma_N:=\frac{S_0+\cdots+S_{N-1}}{N}$$表示$a_n$的Cesaro和。对于任意的正整数$N,p$有：
$$\begin{aligned}\sigma_{N+p}&= \frac{1}{N+p}\sum_{k=0}^{N-1} S_{k}+\frac{S_{N}+...+S_{N+p-1}}{N+p}\\&\geq\frac{1}{N+p}\sum_{k=0}^{N-1} S_{k}  +\frac{p}{N+p}S_{N} \end{aligned}$$

于是如果此时对$p$取下极限，那么我们得到$$\liminf_{n\to \infty}\sigma_n=\liminf_{p\to \infty}\sigma_{N+p}\geq S_N$$而因为$a_n$是Cesaro可和的，因此我们知道$\liminf_{n\to \infty}\sigma_n$是存在的并且有限。因此对于任意的正整数$N$而言，$S_N$都存在一个上界$\liminf_{n\to \infty}\sigma_n$，因此$S_N$此时是一个不减的有界序列，因此极限必然存在。

### 2. 如果$a_n = O(1/n)$

> [!定理2.1]
> 如果$a_n=O(1/n)$并且Cesaro可和，那么序列部分和收敛到其Cesaro和。

本质上来说，这一点是利用Littlewood-Tauberian定理的结果。因为只要加上这个条件，并且假设$a_n$是Cesaro可和的，那么其一定Abel可和。而Littlewood-Tauberian定理告诉我们，在$a_n = O(1/n)$的情况下，Abel可和可以直接导出序列的部分和收敛到相同的结果。