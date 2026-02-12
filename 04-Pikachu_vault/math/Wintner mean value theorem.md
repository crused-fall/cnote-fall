---
tags:
  - math
  - 数论
---
### 1. 定理的证明

对算术函数$f$，定义
1. $$M_x(f):=\frac{1}{x}\sum_{n\leq x}f(n)$$
2. $$M(f):=\lim_{x\to +\infty}M_{x}(f)$$
> [!note] 定理1.1:Wintner mean value theorem,20世纪初
> 如果算术函数$f$是另外一个算术函数$g$的Dirichlet卷积意义下的和，即$$f=1*g$$并且级数$\sum_{n\geq 1}\frac{g(n)}{n}$绝对收敛，那么$f$的平均值$M(f)$就是该级数收敛到的值,即：$$M(f)=\sum_{n\geq 1}\frac{g(n)}{n}$$

> [!tip] 想法1.2
> 我们无非就是要估计和$S(x):=\frac{1}{x}\sum_{n\leq x}f(n)$精度要求至少是$o(1)$。因为$f=1*g$因此我们可以利用[[把条件函数展开为新的求和然后换序#1.1 卷积法的基本形式]]的"Dirichlet卷积法特殊形式1"，这样的话主项当中是关于$\sum_{n\leq x} \frac{g(n)}{n}$的，余项中主要是$\sum_{n\leq x}g(n)$。而我们知道$\frac{g(n)}{n}$的级数的收敛性，那么可以用[[Kronecker's lemma]]来得到余项的估计。

于是$$\begin{aligned}xS(x)&=\sum_{n\leq x}g(n)\left\lfloor \frac{x}{n}\right\rfloor \\&=\sum_{n\leq x}g(n)\left(\frac{x}{n}+O(1)\right)\\&= x\sum_{n\leq x} \frac{g(n)}{n}+ O\left(\sum_{n\leq x}|g(n)|\right)\\&= x\sum_{n\leq 1}\frac{g(n)}{n}+o(x)\end{aligned}$$

* 注意，此处之所以要求$\sum_{n\geq 1}\frac{g(n)}{n}$是绝对收敛是因为上述推导当中$\left\lfloor \frac{x}{n}\right\rfloor=\frac{x}{n}+O(1)$这个表达式的实际含义是：$\left\lfloor \frac{x}{n}\right\rfloor=\frac{x}{n}+R(x/n)$，然后存在一个与$n,x$无关的常数$C$使得$|R(x/n)| \leq C$。而后面余项的累积按照$R$的写法就应该是$$\text{error}(x)=\sum_{n\leq x}g(n)R(x/n)$$我们估计$\text{error}(x)$的时候，由于我们未必能保证$g(n)$是同号的，于是我们直接用三角不等式来控制从而$$\text{error}(x)\leq C\sum_{n\leq x}|g(n)|$$
最后一步我们利用了Kronecker的一个结果:

> [!note] 引理1.3:Kronecker's lemma
> 对于算术函数$f$，如果存在一个$s,\text{Re}(s)>0$使得$$\sum_{n\ge 1} \frac{f(n)}{n^s}<\infty$$那么$$\frac{1}{x^s}\sum_{n\leq x} f(n)\to 0$$

因此如果$\sum_{n\geq 1}\frac{g(n)}{n}$是绝对收敛的，那么$M(|g|)=0$，因此最后的误差项为$o(1)$。

我们还可以从算术函数的Dirichlet生成函数的角度来理解Wintner的平均值定理：

> [!note] 命题1.4:从Dirichlet生成函数理解
> 因为如果$f=g*1$，那么这个关系体现在Dirichlet生成函数上就是$$L(f,s):=\sum_{n\geq 1}\frac{f(n)}{n^s}=\zeta(s)\sum_{n\geq 1}\frac{g(n)}{n^s},\text{Re}(s)>1$$然后$g$满足级数$\sum_{n\geq 1}\frac{g(n)}{n}$绝对收敛那么$M(f)$存在且等于$\sum_{n\geq 1}\frac{g(n)}{n}$

这样考虑当然没有什么本质的区别，不过是Dirichlet卷积在生成函数上的体现罢了。但往往用Dirichlet生成函数更容易找到$f$的卷积关系。


### 2. 如果$\sum_{n\geq 1}\frac{g(n)}{n}$是条件收敛？

#### 2.1 Axer定理及其证明

> [!note] 定理2.1.1:Axer 1910
> 如果算术函数$f$是另外一个算术函数$g$的Dirichlet卷积意义下的和，即$$f=1*g$$如果：
> 1. $\sum_{n\geq 1}\frac{g(n)}{n}$条件收敛
> 2. $\sum_{n\leq x}|g(n)|=O(x)$
> 
> 那么$f$的平均值$M(f)$就是该级数收敛到的值,即：$$M(f)=\sum_{n\geq 1}\frac{g(n)}{n}$$
* 还有一种表述是定义$$H(x):=\sum_{n\leq x} \frac{|g(n)|}{n}$$然后说$\limsup_{x\to \infty}H(x)<\infty$。这个条件要比"定理2.1"的表述要强一些，因为如果假设$H(x)$的上极限为$U$那么任意$\infty>U'>U$都有$$\frac{1}{x}\sum_{n\leq x}|g(n)|\leq \sum_{n\leq x}\frac{|g(n)|}{n}\leq U'$$对任意足够大的$x$成立。于是自然有$\sum_{n\leq x}|g(n)|=O(x)$。


参照“想法1.2”，我们得到$$\begin{aligned}S(x)&= \sum_{n\leq x}\frac{g(n)}{n}+\frac{1}{x}\sum_{n\leq x}g(n)R(x/n)\end{aligned}$$其中$R(n,x)=\left\lfloor \frac{x}{n}\right\rfloor-\frac{x}{n}=\left\{\frac{x}{n}\right\}=O(1)$。

令$$E(x):=\frac{1}{x}\sum_{n\leq x}g(n)R(x/n)$$和第一节不同的是，我们现在要在没有$\sum_n \frac{|g(n)|}{n}$收敛的条件下估计$E(x)$，当然精度要求不变依旧是$o(1)$。此处的困难在于，如果没有绝对收敛，我们就不能对$\frac{|g(n)|}{n}$利用"引理1.3"(Kronecker's lemma),也就是说我们没法直接对$E(x)$使用三角不等式然后逐项估计从而直接达到精度要求$o(1)$。

不过Kronecker's lemma并非全然无用，至少$\frac{g(n)}{n}$组成的级数的收敛性告诉我们，$\sum_{n\leq x}\frac{g(n)}{n}=o(x)$。而这可以导出关于$\sum_{n\leq x}g(n)$的估计：

> [!note] 引理2.1.2
> 复数列$a_n$构成的级数$\sum_{n\geq 1}\frac{a_n}{n}$收敛，那么其部分和$\sum_{n\leq N}a_n =o(N)$。

* 这个结果用[[基于分部求和法的和的估计]]可以直接得到。此处我们要估计的目标和是$A_N:=\sum_{n\leq N}a_n$。我们可以假设$\frac{a_k}{k}$的前n项和为$S_n$那么“引理2.2”的条件告诉我们，$S_n=S+o(1)$。也就是说我们已知的和的估计是$\frac{a_k}{k}$的和。于是我们想到下面的基于分部求和的和的估计$$\begin{aligned}A_N&=\sum_{n\leq N}\frac{a_n}{n}n\\&= S_1+\sum_{n=2}^N (S_{n}-S_{n-1})n\\&= NS_N-(S_1+S_2+\cdots+S_{N-1})\\&= N(A+o(1))-NA+o(N)\\&= o(N)\end{aligned}$$这里我们用到了$$\frac{S_1+\cdots+S_{N-1}}{N-1}\to A$$其证明可以参考[[用分段估计解决几个序列的极限问题#1. 问题1]]。
* 利用这个结果我们可以得到$A(x):=\sum_{n\leq x}g(n)=o(x)$。

不失一般性为了简化问题，下面我们主要估计$$E(N):=\frac{1}{N}\sum_{n\leq N}g(n)R(N/n)$$
由上面的分析我们得到$\frac{1}{N}A(N)\to 0$。这让我们想到对$E(N)$做[[基于分部求和法的和的估计]]。

---

我们当然要做分段估计，因为只有当$n$足够大的时候$|A(n)|$才会被$\varepsilon$控制起来，比如$n>N_{\varepsilon}$的时候。不过这个思路要成功首先要保证分出去的前半段$$\frac{1}{N}\sum_{n\leq N_{\varepsilon}}g(n)R(N/n)$$的部分也可以被$\varepsilon$级别的正实数控制起来。一个简单的思考就是，直接三角不等式逐项放缩，得到$$\frac{1}{N}\left|\sum_{n\leq N_{\varepsilon}}g(n)R(N/n)\right|\leq \frac{1}{N}\sum_{n\leq N_{\varepsilon}}|g(n)|$$然后考虑到$\sum_{n\leq x}|g(n)|\leq Cx$，于是只要$N$足够大那么第一段的误差就能符合我们对精度的要求。

其次是第二段估计，我们要处理一个$$\frac{1}{N}\sum_{n=N_{\varepsilon}+1}^{N-1}A(n)\left(R\left(\frac{N}{n}\right)-R\left(\frac{N}{n+1}\right)\right)$$的误差上限，并且要求上限是$\varepsilon$级别。这里为了利用$|A(n)|<\varepsilon n$的条件，自然就是要做三角放缩。那么我们就需要估计$$\sum_{n=N_{\varepsilon}+1}^{N-1}\left|R\left(\frac{N}{n}\right)-R\left(\frac{N}{n+1}\right)\right|$$这里对误差上限的要求是$O(1)$。这时候就不能单纯利用$r_N(n):=\left|R\left(\frac{N}{n}\right)-R\left(\frac{N}{n+1}\right)\right|$的粗糙上界估计$O(1)$，因为这样得到的整个和的上界为$O(N)$，远超我们要求的精度。因此此处需要做更为精细的估计。

![[n比m取小数差分值的分布示意图.png]]
* 此图当中$N=100$，$n$从1取到$N-1$。

从图中我们能看出来如果我们选择用$O(1)$作为每一项的上界误差实在太大，事实上大多数项的值是随着$n$增加而减少，除了少数一些项以外。所以很自然地，我们要把$r_N(n)$当中的$n$分为两类：跳跃的以及正规的。那么造成这两种现象背后的原因是什么呢？

$\lfloor \frac{N}{n}\rfloor\neq \lfloor \frac{N}{n+1}\rfloor$这时候$r_N(n)$的点会发生跳跃。但是从图中我们能直观感受到，这样的点应该是比较少的。我们能给一个数量的上界估计吗？此时我们又发现，在$N_{\varepsilon}+1$到$N-1$之间不好确定跳跃点数量的上界。因为一个粗糙的估计是基于，$$\lfloor \frac{N}{n}\rfloor\in \left\{1,2,\cdots,\lfloor N/(N_{\varepsilon}+1)\rfloor\right\}$$所以在$N_{\varepsilon}+1$到$N-1$之间至多发生$O(N)$级别次跳跃。这完全超出了我们需要的误差精度。

下面我们来看，Axer是如何处理这里的难点：

---

引入一个与$\varepsilon$有关的参数$\delta_{\varepsilon}<1$，使得整个分段估计形如:

$$1--N_{\varepsilon}'--N_{\varepsilon}''--\delta_{\varepsilon}N-----N$$
首先还是按照基于分部求和的估计$$\begin{aligned}|E(N)|&\leq  \frac{1}{N}\sum_{n\leq \delta_{\varepsilon}N}|g(n)|+\frac{1}{N}|A_{\lfloor \delta_{\varepsilon}N\rfloor}|+\frac{1}{N}\sum_{n=\lfloor \delta_{\varepsilon}N\rfloor+1}^{N-1}|A(n)|\left|R\left(\frac{N}{n}\right)-R\left(\frac{N}{n+1}\right)\right|\end{aligned}$$
* 第一项：$$\frac{1}{N}\sum_{n\leq \delta_{\varepsilon}N}|g(n)|\leq C\delta_{\varepsilon}$$所以我们只要固定一个$\delta_{\varepsilon}$满足$$C\delta_{\varepsilon}\le \varepsilon,\delta_{\varepsilon}<1$$即可满足这一段对估计精度的要求。
* 第二项：因为$A_n/n\to 0$因此对于任意$\varepsilon>0$存在一个正整数$N_{\varepsilon}'$使得任意$n>N_{\varepsilon}'$都有$|A_n|<\varepsilon n$。因此只要$N$足够大，对于已经固定好的$\delta_{\varepsilon}$有$\lfloor \delta_{\varepsilon}N\rfloor >N_{\varepsilon}$，那么因为$$\frac{1}{N}|A_{\lfloor \delta_{\varepsilon}N\rfloor}|<\frac{1}{N}\varepsilon\lfloor \delta_{\varepsilon}N\rfloor\leq \varepsilon \delta_{\varepsilon}<\varepsilon$$即可满足这一段对估计精度的要求。
* 第三项，关键的关于$r_N(n)$部分的估计：添加了参数以后在$\lfloor \delta_{\varepsilon}N\rfloor+1$到$N-1$当中，按照上文相同的估计思路，至多有$\frac{1}{\delta_{\varepsilon}}+2$个跳跃点，此时我们用$2$作为$r_N(n)$的上界。那么剩下的项因为整数部分是相等的，于是$$r_N(n):=\left|R\left(\frac{N}{n}\right)-R\left(\frac{N}{n+1}\right)\right|=\frac{N}{n(n+1)}\leq \frac{1}{\delta_{\varepsilon}^2N}$$于是$$\frac{1}{N}\sum_{n=\lfloor \delta_{\varepsilon}N\rfloor+1}^{N-1}r_N(n)\le K(\delta_{\varepsilon})$$其中$K(\delta_{\varepsilon})=\left(\frac{2}{\delta_{\varepsilon}}+4+\frac{1-\delta_{\varepsilon}}{\delta_{\varepsilon}^2}\right)\geq 4$。然后由于$|A(n)|/n\to 0$那么对于任意$\frac{\varepsilon}{K(\delta_{\varepsilon})}>0$存在一个正整数$N_{\varepsilon}''$使得任意$n>N_{\varepsilon}''$都有$|A_n|<\frac{\varepsilon}{K(\delta_{\varepsilon})} n<\frac{\varepsilon}{4}n$。因为这个条件比之前的更苛刻一些，因此$N_{\varepsilon}''\geq N_{\varepsilon}'$。对于足够大的$N$使得对于第一步固定好的$\delta_{\varepsilon}$有$\delta_{\varepsilon}N>N_{\varepsilon}''$，那么$$\frac{1}{N}\sum_{n=\lfloor \delta_{\varepsilon}N\rfloor+1}^{N-1}|A(n)|\left|R\left(\frac{N}{n}\right)-R\left(\frac{N}{n+1}\right)\right|< \varepsilon $$

综上所述，对于任意$\varepsilon>0$，存在一个$0<\delta_{\varepsilon}<\min\{\varepsilon/C,1/2\}$对于足够大的$N$，即$N>N_{\varepsilon}''$都有$$|E(N)|<3\varepsilon$$因此$$\begin{aligned}S(x)&= \sum_{n\leq x}\frac{g(n)}{n}+o(1)\end{aligned}$$于是我们便证明了Axer的结果。




### 3. 应用

> [!example] 例子3.1
> 定义算术函数$$P_{\alpha}(n)=\sum_{d|n} \sin(2\pi d\alpha)$$其中$\alpha\not \in \mathbb{Z}$。求极限$$\lim_{N\to \infty} \frac{1}{N}\sum_{n\leq N} P_{\alpha}(n)$$

按照Wintner mean value theorem(WMVT)的语境下，我们注意到$P_{\alpha}=1*\sin(2\pi d \alpha)$然后我们要求的就是$M(P_{\alpha})$。于是我们想到是否可以利用WMVT来得到最终的结果，因为毕竟级数$\sum_{d\geq 1}\frac{\sin(2\pi d\alpha)}{d}$是一个我们已知的傅里叶级数，我们知道$$\sum_{d\geq 1}\frac{\sin(2\pi d\alpha)}{d}=-\pi(\{\alpha\}-1/2)$$所以我们剩下的问题就是，我们是否能得到$M(P_{\alpha})$就是此级数收敛到的极限？

1. 首先当$\alpha\not \in \mathbb{Z}$的时候，级数$\sum_{d\geq 1}\frac{\sin(2\pi d\alpha)}{d}$并不绝对收敛。当然由于下面一步Axer定理条件的满足，这一步究竟是不是绝对收敛已经不重要了。
2. 那么我们接着考察Axer的结果是否成立，即是否$\sum_{d\leq N}|\sin(2\pi d\alpha)|=O(N)$。这是当然成立的。

于是由Axer定理，我们知道$$\lim_{N\to \infty} \frac{1}{N}\sum_{n\leq N} P_{\alpha}(n)=-\pi(\{\alpha\}-1/2)$$

---

