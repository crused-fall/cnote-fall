---
tags:
  - math
---
1.  对于无理数$\alpha$其irrational measure $\mu(\alpha)\geq2$,这是Dirichlet定理告诉我们的.
2.  Thue-Siegel-Roth定理(1955)证明所有的代数无理数其irrational measure为2(因此获得菲尔兹奖).
3.  目前为止唯一一类知道irrational measure严格大于2的数是Liouville数,$\mu(L) = \infty$.
4.  不过所有irrational measure严格大于2的实数的集合其Lebesgue measure是0.




1.  不失一般性，单纯考虑$[0,1]$当中的情况。假设$A =\{\alpha \in[0,1]:\mu(\alpha)>2\}$,其中$\mu$是irrational measure.
2.  按照[[an epsilon of room]]的想法，我们可以先证明$A_{\varepsilon} =\{\alpha\in[0,1]:\mu(\alpha)>2+\varepsilon\}$的Lebesgue测度$m(A_{\varepsilon})= 0$.因为我们可以有这样的表达式 $A = \cup_{n\geq 1} A_{1/n}$ ,从而如果任意的$A_{\varepsilon}$是零测度的，那么会导致$A$也是零测度的。而证明$A_{\varepsilon}$是零测度的，基本的想法是:"**如果我们要证明一个集合是零测度，那么不妨先找一个能覆盖此集合的集合，然后试着缩小这种覆盖，如果能把这种覆盖在测度的意义下缩小到0，那么便证明了被覆盖的集合的零测度。**"
3.  按照irrational measure的定义，对任意$\alpha \in A_\varepsilon$都存在无数多对$0<p<q$的互素的整数，使得$$|\alpha-\frac{p}{q}|<\frac{1}{q^{2+\varepsilon}}$$这意味着符合条件的$q$的集合其上确界是无限大，否则的话只有有限对$p,q$能满足上述不等式。这意味着如果我们给定$M>0$一定存在一个$q>M$以及与之互素的$p$，使得$$\alpha
    \in
    I(p,q)=\left(\frac{p}{q}-\frac{1}{q^{2+\varepsilon}},\frac{p}{q}+\frac{1}{q^{2+\varepsilon}}\right)$$不过我们不知道也很难知道，给定$\alpha$对应的具体的$p,q$是什么，但是没有关系这个问题不需要知道确切的这方面的信息，因为我们只需要给出覆盖$A_{\varepsilon}$的一个合适的上界的估计即可。
4.  **覆盖$A_{\varepsilon}$的集合其测度的上界估计**:给定$M$，$\forall \alpha \in A_{\varepsilon }$，$\alpha \in I(p_{\alpha},q_{\alpha}),q_{\alpha}>M$，虽然具体是什么很难说，但是一定有$$\forall
    \alpha \in \bigcup_{q> M \text{ and } p<q}
    I(p,q)$$那么$$\begin{aligned}m(A_{\varepsilon})&\leq
    \sum_{q> M \text{ and } p<q} m(I(p,q))\\ & =
    \sum_{q=M+1}^{\infty}\sum_{p=1}^{q-1}
    \frac{2}{q^{2+\varepsilon}} \\
    &\leq\sum_{q=M+1}^{\infty}\frac{2}{q^{1+\varepsilon}}
    \\&=\int_{M+1}^{\infty}\frac{1}{x^{1+\varepsilon}}dx+O\left(\frac{1}{M^{1+\varepsilon}}\right)
    \\ &=
    O\left(\frac{1}{M^{\varepsilon}}\right)\end{aligned}$$因为$M$是任意正整数，令$M \to +\infty$于是$m(A_{\varepsilon}) = 0$.当然上述命题也可以通过[[Borel-Cantelli lemma]]去证明。


