# 1. 基本判别法

## 1.1 收敛必要条件

若数列 $a_n$ 收敛，则必有
$$
\lim_{n\to\infty} a_n \text{ 存在且有限},\qquad \text{特别地： } a_n\to L\Rightarrow a_n\text{ 有界},\ a_n\text{ 为Cauchy列}
$$
常用形式：

- 收敛 ⇒ 必有 **有界且趋于某极限**。
- **发散常用反证**：若 $a_n$ 无界或 $\lim a_n$ 不存在，可直接说明发散。

------

# 2. 单调有界收敛判别（最常用）

若 $a_n$ **单调递增** 且 **有上界**，则 $a_n$ 收敛。
 若 $a_n$ **单调递减** 且 **有下界**，则 $a_n$ 收敛。

关键形式：

- 单调性：$a_{n+1}\ge a_n$ 或 $a_{n+1}\le a_n$
- 有界性：存在 $M$ 使 $|a_n|\le M$

典型应用：递推数列极限。

------

# 3. 夹逼定理（Sandwich Rule）

若
$$
b_n \le a_n \le c_n,\qquad \lim b_n=\lim c_n=L
$$
则
$$
\lim a_n = L
$$
主要用于：含振荡因子（$(-1)^n$、$\sin n$）、含根号等的估计。

------

# 4. 比较判别法

适用于非负数列 $a_n\ge0$。

## 4.1 直接比较法

若 $0\le a_n\le b_n$ 且 $b_n\to 0$，则 $a_n\to0$。

## 4.2 比值比较法

若 $\displaystyle \lim_{n\to\infty}\frac{a_n}{b_n}=c$ 且 $c\ne0,\infty$，
 则二者收敛/发散性质一致。

------

# 5. 比例与根式判别法（通常用来判断是否趋零）

## 5.1 比例判别法（Ratio Test for sequences）

若
$$
\lim_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|=q
$$

- 若 $q<1$，则 $a_n\to 0$（一定收敛）。
- 若 $q>1$，则 $a_n$ 发散。
- 若 $q=1$，无法判断。

应用：含阶乘、指数、幂的复杂数列。

## 5.2 根式判别法

若
$$
\lim_{n\to\infty} \sqrt[n]{|a_n|}=q
$$

- $q<1$ ⇒ $a_n\to0$
- $q>1$ ⇒ 发散
- $q=1$ ⇒ 不确定

适用于指数型、n 次方型、阶乘等难直接分析的项。

------

# 6. Cauchy 收敛准则

数列收敛 ⇔
$$
\forall\varepsilon>0,\ \exists N\ \text{s.t.}\ \forall m,n>N,\ |a_n-a_m|<\varepsilon
$$
通常用于抽象证明，不常在计算题出现。

------

# 7. 特殊类型数列的判别（常用技巧）

## 7.1 振荡数列

如：$a_n = (-1)^n b_n$

若 $b_n\to 0$，则 $a_n\to 0$。
 若 $b_n\not\to 0$，则一般发散。

## 7.2 形如 $n^\alpha r^n$, $r^n$, $n^k a^n$

结论：指数级主导幂函数级

- 若 $|r|<1$：$r^n\to0$
- 若 $|r|>1$：$|r^n|\to\infty$
- $n^\alpha r^n$ 若 $|r|<1$ 一定趋零
- $a^n/n!\to 0$

## 7.3 连分数、递推定义数列

多数通过单调有界 + 递推不动点求极限。

------

# 8. Cesàro 平均判别

若 $a_n\to L$，则 Cesàro 平均
$$
s_n=\frac{a_1+\cdots+a_n}{n}\to L
$$
反之不成立。

常用来处理部分“振荡但可平均”的数列。

------

# 9. Stolz–Cesàro 定理（强力工具）

若 $b_n$ **严格单调递增且无界**，则
$$
\lim_{n\to\infty}\frac{a_n}{b_n}
  = \lim_{n\to\infty}\frac{a_{n+1}-a_n}{b_{n+1}-b_n}
$$
（若右侧极限存在）。

适用范围：含 $\frac{\log n}{n}$、$\frac{\sum k^2}{n^3}$ 等复杂比值数列。

------

# 10. 上下极限

若
$$
\liminf a_n = \limsup a_n = L
$$
则收敛。

主要用于振荡、难直接处理的数列。

------

# 11. 实用极限模板（做题时直接使用）

## 11.1 常用极限

$$
\lim_{n\to\infty} n(\sqrt[n]{a_n}-1)=\ln a
$$

## 11.2 与“趋零”常用等价

$$
\sqrt[n]{n}\to1,\qquad
\ln n = o(n^\epsilon),\qquad n!=o(n^n)
$$

------

# 12. 绝对收敛 / 条件收敛

若 $|a_n|\to0$ 但 $a_n$ 本身不收敛 → 振荡。
 若 $|a_n|\not\to0$ → 发散。