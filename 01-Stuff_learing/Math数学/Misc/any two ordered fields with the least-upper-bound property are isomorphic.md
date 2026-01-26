# 定理

设 $F$ 和 $G$ 是两个具有**上确界性质（LUBP）**的有序域。
 则存在唯一的序域同构
$$
\varphi : F \longrightarrow G.
$$
换句话说：**任何两个满足上确界性质的有序域都是同构的**。

证明思路：证明每个这样的域都与“标准模型”——由 Dedekind 切割构造的实数域 $\mathbb{R}$——同构。

------

# 1. 每个满足 LUBP 的有序域都是阿基米德域

## 引理 1（阿基米德性）

若 $F$ 是一个具有上确界性质的有序域，则对任意 $x \in F$，
 存在整数 $n \in \mathbb{Z}$ 使得
$$
|x| \le n.
$$
等价地：自然数集合 $\mathbb{N} \subset F$ 在 $F$ 中无上界。

**证明**：
 假设 $\mathbb{N}$ 在 $F$ 中有上界。令 $A = \mathbb{N}$。
 LUBP 保证 $u = \sup A$ 存在。

则 $u - 1$ 不是上界，所以存在整数 $n$ 满足
$$
n > u - 1 \quad\Rightarrow\quad n + 1 > u.
$$
但 $n+1 \in A = \mathbb{N}$，而 $u$ 是上界，应满足 $n+1 \le u$。
 矛盾。

因此 $\mathbb{N}$ 无上界，阿基米德性成立。∎

------

# 2. $\mathbb{Q}$ 在任意有序域中的嵌入与稠密性

## 引理 2（$\mathbb{Q}$ 的唯一嵌入）

在任意有序域 $F$ 中，都存在唯一的保序域嵌入
$$
\iota_F : \mathbb{Q} \hookrightarrow F.
$$
通常将 $\iota_F(\mathbb{Q})$ 直接视为 $F$ 中的“有理子域”。

## 引理 3（阿基米德有序域中的稠密性）

若 $F$ 是阿基米德有序域，则对任意 $a < b$ 在 $F$ 中，存在 $q \in \mathbb{Q}$ 使得
$$
a < q < b.
$$
证明与经典分析教材完全一致，这里略述：利用阿基米德性找到足够大的 $n$，再用整数划分即可。∎

------

# 3. 固定一个标准模型：Dedekind 实数域 $\mathbb{R}$

由 Dedekind 切割构造的实数域 $\mathbb{R}$ 已知：

- 是一个有序域；
- 具有上确界性质；
- 可以自然嵌入 $\mathbb{Q}$；
- 其加法与乘法满足切割的定义。

我们的目标：给定任意满足 LUBP 的有序域 $F$，构造同构
$$
F \xrightarrow{\sim} \mathbb{R}.
$$

------

# 4. 从 $F$ 的元素构造对应的 Dedekind 切割

将 $\mathbb{Q}$ 视为 $F$ 的子域。
 对每个 $x \in F$ 定义集合
$$
\alpha_x := \{ q \in \mathbb{Q} : q < x \ \text{（在 }F\text{ 中）}\}.
$$

## 引理 4

对每个 $x\in F$，$\alpha_x$ 是一个 Dedekind 切割，因此是 $\mathbb{R}$ 的元素。

证明：

- (I) 非空且非全体 $\mathbb{Q}$：由阿基米德性，可找到 $n$ 使 $-n < x$，因此 $-n \in \alpha_x$。也可找到 $m>x$，于是 $m \notin \alpha_x$。
- (II) 向下封闭：若 $p，且 $q，则 $q。
- (III) 无最大元：若 $p，利用 $\mathbb{Q}$ 的稠密性找到 $p，则 $r\in\alpha_x$。

于是定义映射
$$
\Phi : F \to \mathbb{R}, \qquad \Phi(x) = \alpha_x.
$$

------

# 5. $\Phi$ 保序且单射

## 引理 5

若 $x 在 $F$ 中，则 $\alpha_x < \alpha_y$ 在切割序中。

证明：任何 $q 都满足 $q，故 $\alpha_x\subseteq \alpha_y$。
 利用稠密性可找到 $x，从而 $q\notin\alpha_x$，$q\in\alpha_y$，故为真包含。∎

因此：

- $x\ne y \Rightarrow \Phi(x)\ne \Phi(y)$；
- $\Phi$ 是严格保序的单射。

------

# 6. $\Phi$ 是域同态

需证明：
$$
\Phi(x+y)=\Phi(x)+\Phi(y),\qquad \Phi(xy)=\Phi(x)\Phi(y).
$$
关键点：

- 当 $x,y\in\mathbb{Q}$ 时，成立，因为 Dedekind 构造中切割的运算与 $\mathbb{Q}$ 的运算一致。
- 对一般 $x,y\in F$ 使用：
  - $\mathbb{Q}$ 在 $F$ 中稠密；
  - 加法与乘法在 $F$ 与 $\mathbb{R}$ 中均保序、连续（以 Dedekind 切割的方式）；
  - 通过逼近论证即可将等式从有理数推广到所有 $F$ 的元素。

因此 $\Phi$ 是**保序的域同态**。

------

# 7. 通过上确界性质证明 $\Phi$ 是满射

给定任一切割 $\alpha\in\mathbb{R}$。
 把它视为 $\mathbb{Q}\subset F$ 的子集
$$
S = \alpha \subset F.
$$
则：

- $S$ 非空；
- $S$ 在 $F$ 中有上界（由阿基米德性）。

由 LUBP，$\sup_F S = s \in F$ 存在。

我们断言：
$$
\Phi(s) = \alpha_s = \alpha.
$$
证明：

- 若 $q 且 $q\in\mathbb{Q}$，而 $q\notin\alpha$，则 $q$ 是 $S=\alpha$ 的上界，但严格小于上确界 $s$，矛盾──因此 $q\in\alpha$。
   得到 $\alpha_s\subseteq\alpha$。
- 若 $q\in\alpha$，则 $q\le s$。若 $q=s$，因为 $\alpha$ 无最大元，可在 $q$ 左边找到更大的有理数，使得 $q。因此 $q，故 $q\in\alpha_s$。
   得到 $\alpha\subseteq\alpha_s$。

因此
$$
\alpha_s = \alpha.
$$
所以每个切割都是某个 $s\in F$ 的像，$\Phi$ 是满射。

------

# 8. 最终结论：唯一的序域同构

对任意两个具有 LUBP 的有序域 $F$ 和 $G$：

- 上述构造给出
  $$
  \Phi_F : F \to \mathbb{R}, \qquad 
  \Phi_G : G \to \mathbb{R}.
  $$

- 于是
  $$
  \varphi := \Phi_G^{-1} \circ \Phi_F : F \to G
  $$
  是序域同构。

唯一性来自：嵌入 $\mathbb{Q}$ 唯一、保序唯一、上确界唯一，从而整个同构唯一。



# 结论

**任何两个具有上确界性质的有序域都是唯一同构的。**
 换言之：

> 满足 Dedekind 完备性的有序域只有一个（在结构意义上）。