# 0. 级数基本定义（用来理解判别法）

给定级数
$$
\sum_{n=1}^\infty a_n,
$$
令部分和
$$
s_n=\sum_{k=1}^n a_k.
$$
若 $s_n$ 收敛，则称级数收敛；否则发散。

最重要必要条件：
$$
\sum a_n\ \text{收敛} \quad\Rightarrow\quad a_n\to 0.
$$
（反之不行，如调和级数）

------

# 1. 最常用三大判别法（所有题目优先尝试）

## 1.1 **比较判别法**（Direct Comparison Test）

若 $0\le a_n\le b_n$ 且 $\sum b_n$ 收敛，则 $\sum a_n$ 收敛。
 若 $a_n\ge b_n\ge 0$ 且 $\sum b_n$ 发散，则 $\sum a_n$ 发散。

------

## 1.2 **极限比较判别法**（Limit Comparison Test）

对非负项级数：
$$
\lim_{n\to\infty} \frac{a_n}{b_n}=c,\quad 0<c<\infty
$$
则 $\sum a_n$ 与 $\sum b_n$ 同敛散。

（最重要、最常用）

------

## 1.3 **柯西根式（Root）判别法**

$$
L=\lim_{n\to\infty}\sqrt[n]{|a_n|}
$$

- 若 $L<1$：绝对收敛
- 若 $L>1$：发散
- 若 $L=1$：无法判断

适合：指数型、幂指数混合、根式项。

------

# 2. 与根式法并列的核心判别法

## 2.1 **比例（Ratio）判别法**（d’Alembert）

$$
L=\lim_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|
$$

- $L<1$：绝对收敛
- $L>1$：发散
- $L=1$：不确定

适合：阶乘、幂、指数、Gamma、组合数。

------

## 2.2 Raabe 判别法（升级版比例法）

若
$$
\lim_{n\to\infty} n\left(\frac{a_n}{a_{n+1}}-1\right)=R
$$

- 若 $R>1$：收敛
- 若 $R<1$：发散
- $R=1$：不确定

能处理比值法不定型 $L=1$ 的情况。

------

## 2.3 Bertrand 判别法

比 Raabe 更强，用于 $n(\frac{a_n}{a_{n+1}}-1)\to1$ 的边界情形。

------

# 3. 积分判别法（适用于正项级数）

若 $f(x)$ 单调递减、非负，且 $f(n)=a_n$，则：
$$
\sum_{n=1}^\infty a_n \text{ 与 } \int_1^\infty f(x)\,dx \text{ 同敛散}.
$$
适合：$\frac{1}{n^p}$、$\frac{1}{n(\ln n)^p}$ 等。

------

# 4. 绝对收敛与条件收敛

## 4.1 绝对收敛

若 $\sum |a_n|$ 收敛，则 $\sum a_n$ 收敛（绝对收敛）。

## 4.2 条件收敛

若 $\sum a_n$ 收敛但 $\sum |a_n|$ 发散 → 条件收敛。
 经典例子：
$$
\sum (-1)^{n-1}\frac{1}{n}.
$$

------

# 5. 交错级数判别法（Leibniz Test）

若 $a_n>0$，满足

1. $a_n$ 单调递减
2. $a_n\to 0$

则交错级数
$$
\sum (-1)^n a_n 
$$
收敛（但通常是**条件收敛**）。

收敛速度公式亦可用（误差小于下一项）。

------

# 6. 狄利克雷（Dirichlet）判别法（交错的一般化）

$$
\sum a_n b_n
$$

若

1. $A_n=\sum_{k=1}^n a_k$ 有界
2. $b_n$ 单调且 $b_n\to 0$

则 $\sum a_n b_n$ 收敛。

适合：$\sum \frac{\sin n}{n}$。

------

# 7. 阿贝尔（Abel）判别法（Dirichlet 的加强）

级数 $\sum a_n b_n$ 收敛若

1. $\sum a_n$ 收敛
2. $b_n$ 单调有界

典型模型：幂级数边界处理。

------

# 8. Cauchy Condensation Test（柯西拆项判别法）

适用于下降的正项级数：

若 $a_n$ 单调递减且 $a_n\ge0$，则
$$
\sum a_n \text{ 与 } \sum 2^n a_{2^n} \text{ 同敛散}.
$$
例：调和级数
$$
\sum \frac{1}{n}
\quad\Leftrightarrow\quad
\sum 2^n\frac{1}{2^n}= \sum 1
\text{ 发散}。
$$
适合：$\frac{1}{n(\ln n)^p}$、$\frac{1}{n^p}$。

------

# 9. p-级数（p-series）与对数型级数（log-series）

## 9.1 p-级数

$$
\sum\frac{1}{n^p}
$$

- $p>1$：收敛
- $p\le1$：发散

## 9.2 带对数的级数

$$
\sum\frac{1}{n(\ln n)^p}
$$

使用柯西拆项或积分判别法判断。

------

# 10. 特殊高级判别法

## 10.1 Abel 部分求和（Abel Summation）

离散版分部积分，用于构造估计上界下界。

## 10.2 Tauberian 判别法

分析级数收敛与其变换之间的关系（较高级，一般不出现在基础分析中）。

## 10.3 Kummer 判别法

更强的一类比较法，用于边界情况下的对比。

------

# 11. 级数技巧（非判别法，但必备）

## 11.1 项级别极限恒等式

$$
a_n\not\to0\Longrightarrow \sum a_n\text{ 发散}
$$

## 11.2 去掉有限项不改变敛散性

若改变前若干项，级数敛散性不变。

## 11.3 可比较模型

- 幂函数：$\frac{1}{n^p}$
- 对数：$\frac{1}{n(\ln n)^p}$
- 指数比：$\frac{n^p}{a^n}$（趋零）
- 阶乘比：$\frac{1}{n!}$（绝对收敛）