---
tags:
  - math
  - 数值分析
---

> [!question]  问题0
> $$R_n:=\sqrt{1+\sqrt{\frac{1}{2}+\sqrt{\frac{1}{3}+\cdots+\sqrt{\frac{1}{n}}}}}$$证明$$\lim_{n\to \infty} R_n<\frac{2(\pi+1)\log(2)}{1+4\log(2)}$$

首先由于$$R_{n+1}=\sqrt{1+\sqrt{\frac{1}{2}+\sqrt{\frac{1}{3}+\cdots+\sqrt{\frac{1}{n}+\sqrt{\frac{1}{n+1}}}}}}$$由于第n层根号当中$\frac{1}{n}+\sqrt{\frac{1}{n+1}}>\frac{1}{n}$然后由于函数$\sqrt{a+x}>\sqrt{a}$对任意正实数$a,x$成立，所以序列$R_n$是一个单调增加的序列。此外很容易找到此序列的一个上界$$S_n:=\sqrt{1+\sqrt{1+\cdots+\sqrt{1}}},一共n层根号$$这里$S_n$是一个单调增加且具有上确界$\frac{\sqrt{5}+1}{2}$的序列。因此由于$R_n<S_n$因此$R_n$也是一个单调并且有上界的序列，因此$R_n$的极限存在，假设为$$R:=\sqrt{1+\sqrt{\frac{1}{2}+\sqrt{\frac{1}{3}+\cdots+\sqrt{\frac{1}{n}+\cdots}}}}$$
通过下面的代码我们可以计算$R_n$的具体取值，并且比较它和目标上界$\frac{2(\pi+1)\log(2)}{1+4\log(2)}$的差距。

```mathematica
ClearAll[R]

(*生成第 n 级的嵌套根式，保持有理数精度*)
R[n_Integer?Positive] := 
 Fold[Sqrt[#2 + #1] &, Sqrt[1/n],(*最内层 \[Sqrt](1/n)*)
  Reverse@Table[1/k, {k, 1, n - 1}]]
```

然后我们发现$R$与目标上界之间的误差在$10^{-8}$级别，因此我们需要为$R_n$找到一个足够精确的上界，这样才能与目标上界对比。

* 当然这里我们假设目标上界并没有什么深刻含义，因为通常除了少数组成这种从左往右的nested radical的序列具有周期性的时候，否则这种nested radical的极限是没有封闭表达式的。比如更著名的$$\sqrt{1+\sqrt{2+\sqrt{3+\cdots+\sqrt{n+\cdots}}}}$$目前为止就不知道任何封闭形式的表达式。上面这个表达式极限的确是存在的，因为$n^{\frac{1}{2^n}}$是有界的，所以Herschfeld的收敛定理告诉我们极限存在。

---
* 下面的证明参考了[MSE上用户Yuriy S的回答](https://math.stackexchange.com/questions/576110/how-to-find-this-limit-a-lim-n-to-infty-sqrt1-sqrt-frac12-sqrt-fr?noredirect=1)。

> [!note]  引理1
> $$T_n:=\sqrt{a+\sqrt{a+\sqrt{a+\cdots+\sqrt{a}}}},n层根号$$序列$T_n$单调增加并且具有上确界$$T=\frac{1+\sqrt{1+4a}}{2}$$

* 归纳法可以验证$T_n<T$，然后$T$是递归表达式$T_{n+1}^2=T_n^2+a$的其中一个不动点，因此引理1是成立的。

然后我们会发现:
1. $$\begin{aligned}R^2-1&=\sqrt{\frac{1}{2}+\sqrt{\frac{1}{3}+\cdots+\sqrt{\frac{1}{n}+\cdots}}}\\&<\sqrt{\frac{1}{2}+\sqrt{\frac{1}{2}+\sqrt{\frac{1}{2}+\cdots+\sqrt{\frac{1}{2}+\cdots}}}}\\&<\frac{1+\sqrt{3}}{2}\end{aligned}$$令$b_1=\frac{1+\sqrt{3}}{2}$也就是说$$R<\sqrt{1+b_1}$$
2. 同样的道理$$(R^2-1)^2-\frac{1}{2}<\sqrt{\frac{1}{3}+\sqrt{\frac{1}{3}+\sqrt{\frac{1}{3}+\cdots+\sqrt{\frac{1}{3}+\cdots}}}}=\frac{1+\sqrt{\frac{7}{3}}}{2}$$定义$b_2=\frac{1+\sqrt{\frac{7}{3}}}{2}$于是$$R<\sqrt{1+\sqrt{\frac{1}{2}+b_2}}$$
3. 以此类推，$b_n:=\frac{1+\sqrt{1+\frac{4}{n+1}}}{2}$然后$$R<\sqrt{1+\sqrt{\frac{1}{2}+\cdots+\sqrt{\frac{1}{n}+b_n}}}$$

于是通过计算，我们得到$$R<\sqrt{1+\sqrt{\frac{1}{2}+\cdots+\sqrt{\frac{1}{20}+b_{20}}}}<\frac{2(\pi+1)\log(2)}{1+4\log(2)}$$
上界的计算可以用下面的代码实现:
```mathematica
Q[n_Integer?Positive] := 
 Module[{inner = Sqrt[1/n + b[n]],(*\[Sqrt](1/n+b_n)*)
   list = Reverse@Table[1/k, {k, 1, n - 1}]}, 
  Fold[Sqrt[#2 + #1] &, inner, list]       (*依次包根号*)]
```

---

从以上结果来看其实上界$\frac{2(\pi+1)\log(2)}{1+4\log(2)}$并不是一个多么有意义的上界。实际上这个上界是来自于[MSE 用户Lucian](https://math.stackexchange.com/questions/576110/how-to-find-this-limit-a-lim-n-to-infty-sqrt1-sqrt-frac12-sqrt-fr)通过计算$R_n$的浮点数的值，然后通过[RIES](https://www.mrob.com/pub/ries/index.html)（RILYBOT Inverse Equation Solver）得到的近似表达式。其基本原理类似于，通过算法将“常量集合”（诸如$\pi,\sqrt{2},\frac{3}{2},\log(2)$这些常见常数)与“常见表达式集合”（诸如$x,\log(x),\sqrt{x},x^2$等等常见的表达式）进行组合，从而“凑”出与给定数值（例如本文当中的数值$1.52189038686423$）足够接近的表达式。

我们完全还可以凑出别的上界，例如$$R<\log(\frac{1}{9}(4\sqrt{2}-3e+e^2-\pi+4\pi^2))$$