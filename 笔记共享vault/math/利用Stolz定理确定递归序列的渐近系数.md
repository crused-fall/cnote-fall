---
tags:
  - math
  - 微积分
  - 大学数学竞赛
  - 考研
---
 
> [!问题1]
> 数列$\{x_n\}_{n\geq 1}$的初值为$1$,并且满足递推关系$$x_{n+1}=x_{n}+3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}$$求$$\lim_{n\to \infty}\frac{x_n}{n^2}$$


### 1. 猜答案

> [!为什么猜答案是很有用的?]
> 如果把解决问题比喻为在无穷的空间当中搜索一条正确的路径，那么猜出合理的结果以后，我们搜索的范围就极大地缩小了。

首先用计算机猜一个答案:

```wolfram
m = 5000000;
data = RecurrenceTable[{x[n + 1] == x[n] + 3.0*Sqrt[x[n]] + n/Sqrt[x[n]], x[1] == 1}, x, {n, 1, m}];
ListPlot@Table[data[[k]]/k^2, {k, 1, m}]
ListPlot@data
```

![[递归序列的渐近.png]]

从数据中我们能猜测两个结果：
1. 极限就是$\frac{9}{4}=2.25$
2. $\frac{x_n}{n^2}$是一个单调增加并且有上界的序列

### 2. 假设极限存在，那么极限是多少?

假设这个极限是存在的，并且等于$a$，也就是说$$x_n = an^2+o(n^2)$$观察到，***序列的递归定义当中实际上给出了序列的差分的表达***，于是我们有理由去考虑借助Stolz公式(证明可以参考[[Cesaro-Stolz定理]])$$\lim_{n\to \infty}\frac{x_n}{n^2}=\lim_{n\to \infty }\frac{x_{n+1}-x_n}{2n+1}=a$$同时由于序列递归的定义，我们可以在极限存在的假设下，得到$x_{n+1}-x_n$的渐近表达：$$\begin{aligned}x_{n+1}-x_n&=3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}\\&= 3\sqrt{an^2+o(n^2)}+O(1)\\&= 3\sqrt{a}n+o(n)\end{aligned}$$于是我们知道$$\lim_{n\to \infty }\frac{x_{n+1}-x_n}{2n+1}=\frac{3\sqrt{a}}{2}=a$$于是解得，$a = \frac{9}{4}$。

所以剩下需要处理得问题就只有一个，那就是证明极限得存在性。

### 3. 为什么极限是存在的?

#### 3.1 在此问题中单调性实际上是更强的结果

> [!主要想法]
> 既然我们猜到了结果，那么反过来验证结果的合理性就行了。毕竟这个序列的前500万的数据告诉我们，$\frac{x_n}{n^2}$是单调增加到$\frac{9}{4}$去的，那么为什么我们不直接使用归纳法去验证，$$x_n\leq \frac{9}{4}n^2$$

首先需要证明一个辅助的结果，即$x_n$的下界，否则接下来使用归纳法证明$x_{n+1}$成立的时候没办法放缩$\frac{x}{\sqrt{x_n}}$。我们首先证明$x_n\geq n^2$。

* 首先$n=1$的时候是成立的。
* 其次假设$x_n$是成立的，那么$$\begin{aligned}x_{n+1}&\geq x_n+3\sqrt{x_n}\\&\geq n^2+3n \\&\geq (n+1)^2\end{aligned}$$因此下界是成立的。

接下来同样使用归纳法证明其上界的成立：

* 首先$n=1$这个命题显然是成立的。
* 现在假设$x_n\leq \frac{9}{4}n^2$那么由于序列的递归定义$$\begin{aligned}x_{n+1}&\leq x_n+3\sqrt{x_n}+1\\& \leq\frac{9}{4}n^2 +\frac{9}{2}n+1\\&\leq \frac{9}{4}(n+1)^2 \end{aligned}$$
那么按照道理来说，接下来只需要验证$\frac{x_n}{n^2}$的单调性，那么问题就应该可以解决了。

但是如果我们用上述不等式去检验单调性，最终我们需要验证$$3n^2+\frac{n^3}{x_n}>(2n+1)\sqrt{x_n}$$如果此时再使用$x_n$的上界的不等式去缩小左边或者放大右边，我们最终需要验证$$x_n<\left(\frac{3n^2+\frac{4}{9}n}{2n+1}\right)^2$$这虽然是对的，但是我们如果估计等式右边的渐近展开，会得到$$\frac{9}{4}n^2-\frac{19}{12}n+O(1)$$这就需要我们对$x_n$得到更为精确的不等式，至少要达到关于$n$这一项的系数的精度才行，这显然要比求$x_n/n^2$的极限还要强。

#### 3.2 继续使用Stolz但是更具技巧性

如同我们在[[一个递推序列的渐近问题]]当中遇到的那样，如果我们可以在连续使用Stolz的时候，利用稍微粗糙一些的估计来使得一些麻烦的项目的极限为0，从而在考虑差分的极限的时候使得差分的极限是可以直接计算出来的，那么Stolz定理就自然成立了。

我们在2.1当中计算极限的时候，考虑的是，在极限存在的情况下
$$\lim_{n\to \infty}\frac{x_n}{n^2}=\lim_{n\to \infty }\frac{x_{n+1}-x_n}{2n+1}=\lim_{n\to \infty}\frac{3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}}{2n}$$那么实际上我们要考虑的就是$\frac{n}{\sqrt{x_n}}$的极限是否存在的问题。那我们不妨继续考虑该极限，并对该序列的极限使用Stolz定理：

$$\begin{aligned}\lim_{n\to \infty} \frac{n}{\sqrt{x_n}}&=\lim_{n\to \infty}\frac{1}{\sqrt{x_{n+1}}-\sqrt{x_n}}\\&= \lim_{n\to \infty}\frac{\sqrt{x_{n+1}}+\sqrt{x_n}}{x_{n+1}-x_n}\\&=\lim_{n\to \infty}\frac{\sqrt{x_{n+1}}+\sqrt{x_n}}{3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}} \\&= \lim_{n\to \infty}\frac{\sqrt{x_n+3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}}+\sqrt{x_n}}{3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}} \end{aligned}$$
看起来最后的这个极限依旧是不能确定存在性的，似乎是徒劳，但实际上这个极限的存在性对$x_n$的估计要求并不高，因为$$\frac{\sqrt{x_n+3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}}+\sqrt{x_n}}{3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}}=\frac{\sqrt{1+\frac{3}{\sqrt{x_n}}+\frac{n}{x_n\sqrt{x_n}}}+1}{3+\frac{3}{x_n}}$$其中首先因为3.2当中的下界估计，我们知道$x_n\to \infty$，并且$\frac{n}{x_n}\to 0$因此实际上，上面这个式子的极限我们是知道的，就等于$\frac{2}{3}$。也就是说$$\lim_{n\to \infty} \frac{n}{\sqrt{x_n}}=\frac{2}{3}$$那么前面的Stolz得到的结果也是成立的，于是$$\lim_{n\to \infty}\frac{x_n}{n^2}=\lim_{n\to \infty}\frac{3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}}{2n}=\frac{9}{4}$$
#### 3.3 考虑上下极限

如果我们定义$$a = \liminf_{n\to \infty}\frac{x_n}{n^2},b=\limsup_{n\to \infty} \frac{x_n}{n^2}$$那么我们只要证明$$\frac{9}{4}\leq a\leq b\leq \frac{9}{4}$$就能完成整个命题的证明。

> [!主要想法]
> 我们主要的想法是利用[[Cesaro-Stolz定理]]当中1.2提到的广义的定理提供的关于序列上下极限，以及差分版本的序列的上下极限，并结合递归关系得到的不等式，从而得到关于$a,b$的不等式。

$$\begin{aligned}a=\liminf_{n\to \infty}\frac{x_n}{n^2}&\geq \liminf_{n\to \infty }\frac{x_{n+1}-x_n}{2n+1}\\&=\liminf_{n\to \infty}\frac{3\sqrt{x_n}+\frac{n}{\sqrt{x_n}}}{2n}\\&=\liminf_{n\to \infty}\frac{3\sqrt{x_n}}{2n}\end{aligned}$$由于下极限的性质，参考[[关于上下极限的几个错误命题]]当中正确命题2。我们知道$$a\geq \liminf_{n\to \infty}\frac{3\sqrt{x_n}}{2n}=\frac{3}{2}\sqrt{a}$$这个不等式等价于说$$a\geq \frac{9}{4}$$同样的方式我们还可得到$$b\leq \frac{9}{4}$$因此问题也可以被解决。


