---
tags:
  - math
  - 组合学
---

具体来说$$(i+1)^{k+1}-i^k=\sum_{j=0}^{k}\binom{k+1}{j}i^j$$对此式子$i=0,1,\cdots,n$进行求和得到$$\begin{aligned}(n+1)^{k+1}&=\sum_{i=0}^n \sum_{j=0}^{k}\binom{k+1}{j}i^j \\&= \sum_{j=0}^{k}\binom{k+1}{j}\sum_{i=0}^n i^j\\&=\sum_{j=0}^{k}\binom{k+1}{j}S_j(n)\end{aligned}$$整理这个式子我们会得到$$S_k(n)=\frac{1}{k+1}\left((n+1)^{k+1}-\sum_{j=0}^{k-1}\binom{k+1}{j}S_j(n)\right)$$根据归纳假设，我们知道$S_k(n)$就是一个关于$n$的$k+1$此多项式，并且最高次项系数为$\frac{1}{k+1}$。

---




