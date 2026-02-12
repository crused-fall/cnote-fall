---
tags:
  - math
  - 组合学
  - 数论
---

### 1. 问题的基本背景

> [!note] 定义1.1
> $A=\{a_1,a_2,a_3,\cdots\}$是正整数的一个子集，并且满足对任意的$a_i+a_j,\forall  i\leq j$都不同，那么我们称$A$为一个[Sidon集](https://en.wikipedia.org/wiki/Sidon_sequence)序列$a_n$为一个Sidon序列。

> [!example] 例子1.2 
> $\{1,2,5,7\}$是一个Sidon集。

下面是一个直接根据定义来写的，判断一个有限集是否为Sidon集的代码：

```mathematica
Clear[SidonQ];
SidonQ[A_List] := 
 Module[{B = Sort@DeleteDuplicates@A, sums}, 
  If[Length@B != Length@A, Return[False]];
  sums = 
   Flatten@Table[
     B[[i]] + B[[j]], {i, Length@B}, {j, i, 
      Length@B}];(*i\[LessEqual]j*)
  Length@sums === Length@DeleteDuplicates@sums
  (*===表示判断左右两侧表达式的结果在mathematica语法中是否完全一致*)]
```

用这段程序我们可以构造出许多其他的Sidon集，比如：

> [!example] 例子1.3
> $$\{6,7,25,40,57,68,92\}$$$$\{3, 4, 13, 16, 32, 43, 74, 79, 94\}$$ $$\{50, 85, 138, 213, 282, 461, 522, 670, 725, 730, 840, 932, 944, 947, 958\}$$
> 都是Sidon集。

以上Sidon集的例子都是通过"随机试验"的方式构造的，具体来说就是：
1. 从集合$\{1,\cdots,N\}$当中随机抽取$m$个不同的正整数组成集合$A$。
2. 判断$A$是否为Sidon集，如果是则停止程序，如果不是退回到第一步。


> [!note] 定义1.4
> 令$A$是一个Sidon集，定义$$f_A(N):=|A\cap \{1,\cdots,N\}|$$定义$$f(N):=\max_{A\text{ is Sidon}} f_A(N)$$


可是这样我们就需要搞清楚一件基本的事：

> [!question] 问题1.5
> 前$N$个正整数当中，最大能容纳多大尺寸的Sidon集合？即$f(N)$的上界估计问题。
> 

否则的话就可能像下面这样：

```mathematica
Table[data = Sort@RandomSample[Range[1, 100], 20]; 
 If[SidonQ@data, data, Nothing], {k, 1, 5000000}]
```

耗费算力，重复五百万次随机抽取，为了试图从$\{1,\cdots,100\}$当中筛选出一个大小为$20$的Sidon集，然而这根本就是不可能的。因为$$f(100)<20$$即任意Sidon集$A$，对应的$f_A(100)<20$也就是说，任意$A\subset \{1,\cdots,100\}$为Sidon集，其元素个数不可能达到20个或者更多。


> [!question] 问题1.6
> 函数$f(N)$的渐进估计是怎样的？函数尺寸接近$f(N)$的Sidon集长什么样子？

### 2. Sidon集尺寸的上界估计

> [!note] 命题2.1:$F_N$的一个粗上界 
> $$f(N)< 2\sqrt{N}$$

* 这里的想法非常简单：如果$A\subset \{1,\cdots,N\}$是一个Sidon集，假设$|A|=m$。然后我们想，这$m$个元素一共能制造出多少个不同的和？一共是$\binom{|A|}{2}$个不同$a_i+a_j$的组合，以及$m$个$a_i+a_i$的组合。这些和的上界与下界都是什么？这些和最小可能是$1+1=2$最大可能是$N+N=2N$。于是接下来就是一个抽屉原理：由于$[2,2N]\cap \mathbb{Z}$当中有$2N-1$个元素，因此一定有$$\binom{m}{2}+m=\frac{m(m+1)}{2}\leq 2N-1$$于是我们可以得到一个粗糙的估计$$m<2\sqrt{N}$$
* 这个结果也能解释上一节中，为什么我们不可能从$\{1,\cdots,100\}$当中选出一个大小为$20$的Sidon集。
* 换一个角度来说，如果我们把Sidon集$A$当中的元素从小到大写成一个序列$a_1,a_2,\cdots,a_n,\cdots$那么这里的估计能告诉我们关于序列的增长速度的下界信息。比如当我们考虑$\{a_1,\cdots,a_n\}$的时候，这也是一个Sidon集，然后$$\binom{n}{2}+n=\frac{n(n+1)}{2}\leq 2a_n-2a_1+1$$于是我们得到$$a_n \gtrsim n^2$$

Paul Erdos与Paul Turan得到过一个渐进的结果:

> [!note] 命题2.2：Erdos-Turan,1941
> $$F_N\leq\sqrt{N}+o(\sqrt{N})$$

* Erdos, P., & Turán, P. (1941). On a problem of Sidon in additive number theory, and on some related problems. Journal of the London Mathematical Society, s1-16(4), 212–215.

### 3. greedy Sidon集的尺寸

我们先不要想maximum Sidon集，我们先退而求其次，尝试构造任意尺寸的Sidon集。 

Abdul Majid Mian和 Sarvadaman Chowla借助贪心算法构造了[Mian-Chowla序列](https://en.wikipedia.org/wiki/Mian%E2%80%93Chowla_sequence)这个序列对应的集合称之为greedy Sidon集：

> [!note] 定义3.1:greedy Sidon集
> $$a_1:=1，\quad a_{n+1}:=\min\{s>a_n:\{a_1,\cdots,a_n,s\}\text{为 Sidon 集}\}$$我们称集合$$G:=\{a_1,\cdots,a_n,\cdots\}$$为greedy Sidon集。

* 之所以说是greedy Sidon集，是因为$a_n$的每一步都是选取所有可能当中数当中最小的那一个。

然后我们想要知道这样构造出来的Sidon集的大小的估计。

> [!note] 命题3.2 
> 令$G$是greedy Sidon集，那么$$f_{G}(N)\gtrsim N^{1/3}$$

^99285c

整个证明思路是证明$$a_n \lesssim n^3$$如果这是对的，那么由$a_n\leq N$我们可以导出$n\gtrsim N^{1/3}$从而得到我们想要证明的结果。

下面给出证明：

我们令$G_n:=\{a_1,\cdots,a_n\}$为包含了$G$的从小到大排列的前$n$个元素的集合。

现在假设我们已经得到了$G_{n-1}$，然后现在要去到下一个$G$当中的元素$a_n$。此时令$$P_{n-1}:=\{a_i+a_j:1\leq i\leq j\leq n-1\}$$这是$G_{n-1}$当中能产生的所有二元和组成的集，这个集合具有容量限制$$|P_{n-1}|=\frac{n(n-1)}{2}$$而现在新选择的$a_n$被定义为$$a_n:=\min(\mathbb{Z}_{\geq 1}\setminus F_n)$$
1. 其中$$F_n:=\left[\bigcup_{j=1}^{n-1}(P_{n-1}-a_j)\right]\bigcup \frac{1}{2}P_{n-1}$$
2. 其中$$P_{n-1}-a_j:=\{s-a_j:s\in P_{t-1}\},\quad \frac{1}{2}P_{n-1}:=\{x\in \mathbb{Z}:2x\in P_{n-1}\}$$
也就是说，所有满足与$G_{n-1}$当中的元素相加，以及自己与自己相加不会产生$G_{n-1}$当中原本的元素已经出现过的二元和都不同的，这样的元素当中最小的那一个。

由于$G_{n-1}$是Sidon集，从而$P_{n-1}-a_j$这些集合互相之间都不相交，从而在贪心选择下$$\begin{aligned}a_n &\leq |F_n|+1\\ &\leq \left(\sum_{j=1}^{n-1}|P_{n-1}-a_j|\right)+|P_{n-1}|\\&\leq \left(\sum_{j=1}^{n-1}|P_{n-1}|\right)+|P_{n-1}|\\&= n|P_{n-1}|=\frac{n^3-n^2}{2}\end{aligned}$$因此$$a_n \lesssim n^3$$

---

那么greedy Sidon集是一个maximum Sidon集吗？

> [!question] 猜想3.3:Erdos问题 340
> 对任意$\varepsilon>0$以及足够大的正整数$N$都有：
> $$f_G(N)\gg N^{1/2-\varepsilon}$$

* 该问题的状态更新页面：[Erdos problem 340](https://www.erdosproblems.com/340)







