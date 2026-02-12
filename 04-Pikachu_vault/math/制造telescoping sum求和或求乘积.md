---
tags:
  - math
  - tool_idea
---
### 1. 求和的例子

> [!note] telescoping sum
> 但凡我们制造出$f(k+1)-f(k)=g(k)$的形式，我们是有办法直接表示出来$f(k)$的和的。也就是说，我们可以通过函数在整数点处的所有差分的信息还原出函数本身。从这个角度上来说，telescoping sum比较**类似于离散类型的，微积分基本定理**。

#### 1.1 一个复级数求和

> [!note] 复级数求和
> $|z|<1$，求和
> $$\sum_{n \geq 1} \frac{z^{n-1}}{(1-z^n)(1-z^{n+1})}$$

* **观察到求和项目可以列开是这个问题的关键**：
$$\frac{z^{n-1}}{(1-z^n)(1-z^{n+1})} = -\frac{1}{(1-z)z} \left(\frac{1}{1-z^{n+1}} - \frac{1}{1-z^{n}}\right)$$
从而可以形成一个telescoping sum,从而立刻知道求和的结果是:
$$-\frac{1}{(1-z)z}\left(1-\frac{1}{1-z}\right) = \frac{1}{(1-z)^2}$$
#### 1.2 关于Fibonacci数的级数

> [!note] 关于Fibonacci数的求和
> 其中$F_n$是第n个Fibonacci数，$$\sum_{n \geq 1} \frac{1}{F_nF_{n+4}}$$

这个例子告诉我们，有时候发现Telescoping sum也不是那么顺利的，可能会需要多次使用这样的技巧（特别是当分母出现:$f(n)f(n+k)$的时候)

比如这个问题的关键是配出,$$\frac{1}{F_nF_{n+4}} = \frac{1}{3F_{n+2}} \left(\frac{1}{F_n} +\frac{1}{F_{n+4}} \right)$$
这个结果当然不是观察到的，而是设未知数去凑出来的形式。不过这个形式还不能直接发现telescoping sum的形式，而是需要进一步地计算。

我们可以先看一个非常类似但是相对简单的问题，从中找一些经验：
> [!note] 关于Fibonacci数的求和，简单版本
> 其中$F_n$是第n个Fibonacci数，$$\sum_{n \geq 1} \frac{1}{F_nF_{n+2}}$$


$$\begin{aligned} \sum_{n=1}^{\infty} \frac{1}{F_n F_{n+2}} & =\lim _{N \rightarrow \infty} \sum_{n=1}^N \frac{1}{F_n F_{n+2}} \\ & =\lim _{N \rightarrow \infty} \sum_{n=1}^N \frac{F_{n+1}}{F_n F_{n+1} F_{n+2}}=\lim _{N \rightarrow \infty} \sum_{n=1}^N \frac{F_{n+2}-F_n}{F_n F_{n+1} F_{n+2}} \\ & =\lim _{N \rightarrow \infty} \sum_{n=1}^N\left(\frac{1}{F_n F_{n+1}}-\frac{1}{F_{n+1} F_{n+2}}\right) \\ & =\lim _{N \rightarrow \infty}\left(\frac{1}{F_1 F_2}-\frac{1}{F_{N+1} F_{N+2}}\right) \\ & =\frac{1}{F_1 F_2}=1 \end{aligned}$$
从解决这个问题的经验中我们知道，首先相差4的可以分拆成两个相差2的，然后相差2的分拆成相差1的，最后一个变成telecscoping sum .于是，这里我们可以把$F_nF_{n+1}$视为一个整体:
$$\begin{align}\sum_{n \geq 1} \frac{1}{F_nF_{n+4}} &= \sum_{n \geq 1} \frac{1}{3F_{n+2}} \left(\frac{1}{F_n} +\frac{1}{F_{n+4}} \right) \\ &= \frac{1}{3} \sum_{n \geq 1} \frac{1}{F_nF_{n+2}} + \frac{1}{3} \sum_{n \geq 1} \frac{1}{F_{n+2}F_{n+4}} \\ &=\frac{1}{3} +\frac{1}{3} \left(\sum_{n \geq 1} \frac{1}{F_{n}F_{n+2}} - \frac{1}{F_1 F_3} - \frac{1}{F_2 F_4}\right) \\&=\frac{1}{3} + \frac{1}{3} \left(\frac{1}{6}\right)\\&=\frac{7}{18}\end{align}$$

####  1.3 更多的例子

* [[全纯函数沿着两条同伦的连续曲线积分结果一致]]这部分证明当中通过换元发现了telescoping sum的结构，从而完成证明。

### 2. telescoping product

> [!tip] 想法2.1
> 如果我们想要求$\prod _{k=1}^n c_k$，而我们又发现$c_k=a_k\cdot \frac{b_k}{b_{k+1}}$那么其中$\prod_k a_k$是简单的或者已知的，那么$$\prod _{k=1}^n c_k=\left(\prod_{k=1}^n a_k \right) \prod_{k=1}^n \frac{b_k}{b_{k+1}}=\left(\prod_{k=1}^n a_k \right)\frac{b_1}{b_{n+1}}$$

一些例子：

> [!example] 例子2.2
> $$\prod_{k=2}^{n}\left(1-\frac{1}{k^2}\right)=\frac{n+1}{2n}$$

* 这是因为$$1-\frac{1}{k^2}= \frac{k^2-1}{k^2}=\frac{\frac{k-1}{k}}{\frac{k}{k+1}}$$也就是说令$a_k \equiv 1,b_k = \frac{k-1}{k}$于是$$\prod_{k=2}^{n}\left(1-\frac{1}{k^2}\right)=\prod_{k=2}^n \frac{b_k}{b_{k+1}}=\frac{b_2}{b_{n+1}}=\frac{n+1}{2n}$$
---

> [!example] 例子2.3
> $$\prod_{n\geq 0} (1+a^{2^n})=\frac{1}{1-a},\quad \forall |a|<1$$

* 注意到$$1+x=\frac{1-x^2}{1-x}$$那么在此例子当中$$1+a^{2^n} = \frac{1-a^{2^{n+1}}}{1-a^{2^n}}$$也就是说令$b_n:=1-a^{2^n}$于是$$\prod_{n=0}^{N} (1+a^{2^n})=\prod_{n=0}^{N} \frac{b_{n+1}}{b_n}= \frac{b_{N+1}}{b_0}$$然后令上式当中$N\to \infty$，于是$$\prod_{n\geq 0} (1+a^{2^n})=\frac{1}{1-a}$$


让我们再来看一个经典的例子：

> [!example] 例子2.4
> 
> $$\prod_{n\geq 0} \cos\left(\frac{x}{2^{n+1}}\right)=\frac{\sin(x)}{x}$$
> 
> * 考虑到正弦函数的二倍角公式$$\sin(x)=2\sin(x/2)\cos(x/2)$$这个式子在当前情境下可以写成$$\cos\left(\frac{x}{2^{n+1}}\right)=\frac{\sin\left(\frac{x}{2^{n}}\right)}{2\sin\left(\frac{x}{2^{n+1}}\right)}$$于是$$\prod_{n= 0}^{N} \cos\left(\frac{x}{2^{n+1}}\right)=\frac{1}{2^{N+1}}\prod_{n=0}^{N}\frac{\sin\left(\frac{x}{2^{n}}\right)}{\sin\left(\frac{x}{2^{n+1}}\right)}=\frac{1}{2^{N+1}}\frac{\sin(x)}{\sin\left(\frac{x}{2^{N+1}}\right)}\to \frac{\sin(x)}{x}$$



现在让我们来用这个思路来推广“例子2.3”:

> [!example] 例子2.5
> 令$q\geq 2$是一个正整数实数$a$满足$|a|<1$那么$$\prod_{n\geq 0}(1+a^{q^n}+\cdots+a^{(q-1)q^n})=\frac{1}{1-a}$$


* 事实上，如果我们把$a^{q^n}$当作一个整体$u_n$，那么$$\begin{aligned}1+a^{q^n}+\cdots+a^{(q-1)q^n}&=1+u_n+\cdots+u_n^{q-1}\\&=\frac{1-u_{n}^{q}}{1-u_n}=\frac{1-a^{q^{n+1}}}{1-a^{q^n}}\end{aligned}$$于是目标乘积可以看成是一个telescoping product于是$$\begin{aligned}\prod_{n= 0}^{N}(1+a^{q^n}+\cdots+a^{(q-1)q^n})&=\prod_{n=0}^{N}\frac{1-a^{q^{n+1}}}{1-a^{q^n}}\\&=\frac{1-a^{q^{N+1}}}{1-a}\to \frac{1}{1-a}\end{aligned}$$



