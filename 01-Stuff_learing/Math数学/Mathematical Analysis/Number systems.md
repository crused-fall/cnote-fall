# Real field and rational field

## Introduction

> **Definition - Least upper bound property**
>
> An **ordered set** $S$ is said to have the **least-upper-bound property** iff:
>
> $\forall E\sub S$, where $E\ne \empty$ and $E$ is bounded above, then $\sup E\in A$. 



**Example**
Let $A$ be the set of all positive rationals $p$ such that $p^2 < 2$,
let $B$ consist of all positive rationals p such that $p^2 > 2$.
Then $A$ contains no **largest** number and $B$ contains no **smallest**.

> *Proof*.
> Construct $p$,$q$, s.t.
> $$
> q=p-\frac{p^2-2}{p+2}=\frac{2p+2}{p+2}
> $$
> Then
> $$
> q^2-2=\frac{2(p^2-2)}{(p+2)^2}
> $$
>
> - If $p\in A$, $q>p$ and $q\in A$
> - If $p\in B$, $q<p$ and $q\in B$
>
> $\square$ 

> [!note]
>
> This example shows that $\Q$ does not have least-upper-bound property

---



> **Theorem - The equivalence between least-upper-bound & greatest-lower-bound**
>
> For $S$ has least-upper bound property and $B\sub S$ is bounded below. Let $L$ be the set if all lower bounds of $B$. Then $\alpha =\sup L=\inf B\in S$ (Greatest-lower-bound property).



> *Proof*.
>
> It is obvious that $L$ is bounded above. 
>
> Thus by the least-upper-bound property of $S$, $L$ has a supremum in $S$ called $\alpha$.
>
> For $γ < α$ then $γ$ is not an upper bound of $L$, hence $γ \notin B$. It follows that $α ≤ x$ for every $x ∈ B$. Thus $α ∈ L$.
>
> If $α < β$ then $β \notin L$, thus $\alpha=\inf B$.
>
> $\square$

---



## Construction of $\R$

> **Definition - Field**
>
> A field is a set \( \mathbb{F} \) with two operations,called **addition** and **multiplication**, which satisfy the following so-called "field axioms" (A), (M),and (D):
>
> (A) Axioms for addition
>
> - (A1) \( x \in  \mathbb{F} \) and \( y \in  \mathbb{F} \) ,then their sum \( x + y \) is in \( \mathbb{F} \) .
> - (A2) Addition is commutative: \( x + y = y + x \) for all \( x,y \in  \mathbb{F} \) .
> - (A3) Addition is associative: \( \left( {x + y}\right)  + z = x + \left( {y + z}\right) \) for all \( x,y,z \in  \mathbb{F} \) .
> - (A4) \( \mathrm{F} \) contains an element 0 such that \( 0 + x = x \) for every \( x \in  \mathbb{F} \) .
> - (A5) To every \( x \in  \mathbb{F} \) corresponds an element \( - x \in  \mathbb{F} \) such that \( x + \left( {-x}\right)  = 0. \)
>
> (M) Axioms for multiplication 
>
> - (M1) If \( x \in  \mathbb{F} \) ,then their product \( {xy} \) is in \( \mathbb{F} \) .
> - (M2) Multiplication is commutative: \( {xy} = {yx} \) for all \( x,y \in  \mathbb{F} \) .
> - (M3) Multiplication is associative: \( \left( {xy}\right) z = x\left( {yz}\right) \) for all \( x,y,z \in  \mathbb{F} \) .
> - (M4) F contains an element \( 1 \neq  0 \) such that \( {1x} = x \) for every \( x \in  \mathbb{F} \) .
> - (M5) If \( x \in  \mathbb{F} \) and \( x \neq  0 \) then there exists an element \( 1/x \in  \mathbb{F} \) such that \( x \cdot  \left( {1/x}\right)  = 1 \)
>
> (D) The distributive law
>
> - \( x\left( {y + z}\right)  = {xy} + {xz} \) holds for all \( x,y,z \in  \mathbb{F} \) .

---

> **Theorem - Construction of $\R$ and $\Q$**
>
> There exists an ordered field $\R$ which has the least-upper-bound property.
>
> Moreover, $\R$ contains $\Q$ as a subfield.



> *Proof*.
>
> **Step 1**
>
> The members of $R$ will be certain subsets of $\mathbb{Q}$, called **cuts**.
>  A **cut** is, by definition, any set $\alpha \subseteq \mathbb{Q}$ with the following three properties:
>
> **(I)** $\alpha$ is not empty, and $\alpha \neq \mathbb{Q}$.
>
> **(II)** If $p \in \alpha$, $q \in \mathbb{Q}$, and $q < p$, then $q \in \alpha$.
>
> **(III)** If $p \in \alpha$, then $p < r$ for some $r \in \alpha$.
>
> The letters $p, q, r, \ldots$ will always denote rational numbers, 
>
> and $\alpha, \beta, \gamma, \ldots$ will denote cuts.
>
> 
>
> Note that (III) simply says that $\alpha$ has no largest member.
> Property (II) implies two facts which will be used freely:
>
> - If $p \in \alpha$ and $q \notin \alpha$, then $p < q$.
> - If $r \notin \alpha$ and $r < s$, then $s \notin \alpha$.
>
> **Step 2**
>
> Define “$\alpha < \beta$” to mean: **$\alpha$ is a proper subset of $\beta$.**
>
> This is well-defined because:
>
> 1. If $\alpha < \beta$ and $\beta < \gamma$, it is clear that $\alpha < \gamma$
>
> 2. It is also clear that at most one of the three relations
>    $$
>    \alpha < \beta,\qquad \alpha = \beta,\qquad \beta < \alpha
>    $$
>    can hold for any pair $\alpha, \beta$.
>
>    
>
>    To show that **at least one** holds, assume that the first two fail.
>    Then $\alpha$ is not a subset of $\beta$. Hence there is a $p \in \alpha$ with $p \notin \beta$. If $q \in \beta$, it follows that $q < p$ (since $p \notin \beta$), hence $q \in \alpha$, by (II). Thus $\beta \subset \alpha$. Since $\beta \neq \alpha$, we conclude $\beta < \alpha$.
>
>    Thus $R$ is now an ordered set.
>
> **Step 3**
>
> The ordered set $R$ has the **least upper bound property**.
>
> To prove this, let $A$ be a nonempty subset of $R$, and assume that $\beta \in R$ is an upper bound of $A$.
>  Define $\gamma$ to be the union of all $\alpha \in A$.
>  In other words,
> $$
> p \in \gamma \quad \text{iff} \quad p \in \alpha \ \text{for some}\ \alpha \in A.
> $$
> We shall prove that $\gamma \in R$ and that $\gamma = \sup A$.
>
> Since $A$ is not empty, there exists an $\alpha_0 \in A$.
>  This $\alpha_0$ is not empty. Since $\alpha_0 \subset \gamma$, $\gamma$ is not empty.
>  Next, $\gamma \subset \beta$ (since $\alpha \subset \beta$ for every $\alpha \in A$), and therefore $\gamma \neq \mathbb{Q}$.
>  Thus $\gamma$ satisfies property (I).
>
> To prove (II) and (III), pick $p \in \gamma$.
>  Then $p \in \alpha_1$ for some $\alpha_1 \in A$.
>  If $q < p$, then $q \in \alpha_1$, hence $q \in \gamma$; this proves (II).
>  If $r \in \alpha_1$ is chosen so that $r > p$, then $r \in \gamma$, and therefore $\gamma$ satisfies (III).
>
> Thus $\gamma \in R$.
>
> It is clear that $\alpha \le \gamma$ for every $\alpha \in A$.
>
> Suppose $\delta < \gamma$.
>  Then there is an $s \in \gamma$ such that $s \notin \delta$.
>  Since $s \in \gamma$, $s \in \alpha$ for some $\alpha \in A$.
>  Hence $\delta < \alpha$, and $\delta$ is not an upper bound of $A$.
>
> This gives the desired result:
> $$
> \gamma = \sup A.
> $$
> **Step 4**
>
> If $\alpha, \beta \in R$, we define
> $$
> \alpha + \beta = \{\, r + s : r \in \alpha,\ s \in \beta \,\}.
> $$
> We define $0^\ast$ to be the set of all negative rational numbers.
>  It is clear that $0^\ast$ is a cut.
>
> We verify that the axioms for addition hold in $R$,
>  with $0^\ast$ playing the role of $0$.
>
> **(A1)**
>
> > We have to show that $\alpha + \beta$ is a cut.
> >
> > It is clear that $\alpha + \beta$ is a nonempty subset of $\mathbb{Q}$.
> >  Take $r' \notin \alpha$, $s' \notin \beta$.
> >  Then $r' + s' > r + s$ for all $r \in \alpha$, $s \in \beta$.
> >  Thus $r' + s' \notin \alpha + \beta$.
> >  Hence $\alpha + \beta$ has property (I).
> >
> > Pick $p \in \alpha + \beta$.
> >  Then $p = r + s$ with $r \in \alpha$, $s \in \beta$.
> >  If $q < p$, then $q - s < r$, so $q - s \in \alpha$, and
> > $$
> > q = (q - s) + s \in \alpha + \beta.
> > $$
> > Thus (II) holds.
> >
> > Choose $t \in \alpha$ so that $t > r$.
> >  Then $p < t + s$ and $t + s \in \alpha + \beta$.
> >  Thus (III) holds.
>
> **(A2)**
>
> > By the definition of addition,
> > $$
> > \alpha + \beta = \{ r + s \},\qquad  
> > \beta + \alpha = \{ s + r \}.
> > $$
> > Since $r+s = s+r$ for all rationals,
> > $$
> > \alpha + \beta = \beta + \alpha.
> > $$
>
> **(A3)**
>
> > Associativity follows from associativity in $\mathbb{Q}$.
>
> **(A4)**
>
> > If $r \in \alpha$ and $s \in 0^\ast$, then $r + s < r$, hence $r + s \in \alpha$.
> >  Thus $\alpha + 0^\ast \subset \alpha$.
> >
> > To obtain the opposite inclusion, pick $p \in \alpha$, and pick $r \in \alpha$ with $r > p$.
> >  Then $p - r \in 0^\ast$, and
> > $$
> > p = r + (p - r) \in \alpha + 0^\ast.
> > $$
> > Thus $\alpha \subset \alpha + 0^\ast$.
> >  Hence
> > $$
> > \alpha + 0^\ast = \alpha.
> > $$
>
> **(A5)**
>
> > Fix $\alpha \in R$.
> >  Let $\beta$ be the set of all $p$ with the following property:
> >
> > **There exists $r > 0$ such that $-p - r \notin \alpha$.**
> >
> > In other words, some rational number smaller than $-p$ fails to be in $\alpha$.
> >
> > We show that $\beta \in R$ and that $\alpha + \beta = 0^\ast$.
> >
> > - If $s \notin \alpha$ and $p = -s - 1$, then $-p - 1 \notin \alpha$, hence $p \in \beta$.
> >    So $\beta$ is not empty.
> > - If $q \in \alpha$, then $-q \notin \beta$.
> >    So $\beta \neq \mathbb{Q}$.
> >    Hence $\beta$ satisfies (I).
> >
> > Pick $p \in \beta$ and $r > 0$ so that $-p - r \notin \alpha$.
> >  If $q < p$, then $-q - r > -p - r$, hence $-q - r \notin \alpha$.
> >  Thus $q \in \beta$, and (II) holds.
> >
> > Put $t = p + (r/2)$.
> >  Then $t > p$ and $-t - (r/2) = -p - r \notin \alpha$, so $t \in \beta$.
> >  Hence (III) holds.
> >
> > Thus $\beta \in R$.
> >
> > If $r \in \alpha$ and $s \in \beta$, then $-s \notin \alpha$, hence $r < -s$,
> >  so $r + s < 0$.
> >  Thus
> > $$
> > \alpha + \beta \subset 0^\ast.
> > $$
> > To prove the opposite inclusion, pick $v \in 0^\ast$, put $w = -v/2$.
> >  Then $w > 0$, and there is an integer $n$ such that $nw \in \alpha$ but
> >  $(n+1)w \notin \alpha$.
> >  (This uses the Archimedean property of $\mathbb{Q}$!)
> >  Put $p = -(n+2)w$.
> >  Then $p \in \beta$, since $-p - w \notin \alpha$, and
> > $$
> > v = nw + p \in \alpha + \beta.
> > $$
> > Thus
> > $$
> > 0^\ast \subset \alpha + \beta.
> > $$
> > We conclude that
> > $$
> > \alpha + \beta = 0^\ast.
> > $$
> > This $\beta$ will of course be denoted by $-\alpha$.
>
> **Step 5**
>
> Having proved that addition satisfies axioms (A)
>
> **If $\alpha, \beta, \gamma \in R$ and $\beta < \gamma$, then $\alpha + \beta < \alpha + \gamma$.**
>
> Indeed, from the definition of $+$ we have $\alpha + \beta \subset \alpha + \gamma$.
>  If equality held, the cancellation law would imply $\beta = \gamma$.
>
> It also follows that
> $$
> \alpha > 0^\ast \quad \text{iff} \quad -\alpha < 0^\ast.
> $$
> **Step 6**
>
> Multiplication is more troublesome than addition, since products of negative rationals are positive.
> For this reason, we first restrict ourselves to
> $$
> R^+ = \{\alpha \in R : \alpha > 0^\ast \}.
> $$
> If $\alpha, \beta \in R^+$, we define **$\alpha\beta$** to be the set of all
> $$
> p \le rs
> $$
> for some choice of $r \in \alpha, s \in \beta$ with $r > 0, s > 0$.
>
> We define $1^\ast$ to be the set of all $q < 1$.
>
> Then axioms (M) and (D) of Definition 1.12 hold, with $R^+$ in place of $F$, and $1^\ast$ as $1$.
>
> The proofs are similar to those in Step 4 and are omitted.
>
> In particular, 
>
> **If $\alpha > 0^\ast$ and $\beta > 0^\ast$, then $\alpha\beta > 0^\ast$.**
>
> **Step 7**
>
> We complete multiplication by setting
> $$
> \alpha 0^\ast = 0^\ast \alpha = 0^\ast,
> $$
> and
> $$
> \alpha\beta =
> \begin{cases}
> (-\alpha)(-\beta), & \alpha < 0^\ast,\ \beta < 0^\ast,\\[4pt]
> -[( -\alpha)\beta], & \alpha < 0^\ast,\ \beta > 0^\ast,\\[4pt]
> -[\alpha(-\beta)], & \alpha > 0^\ast,\ \beta < 0^\ast.
> \end{cases}
> $$
> The products on the right were defined in Step 6.
>
> Having proved the axioms (M) in $R^+$, they now follow in $R$ by repeated application of
> $$
> \gamma = -(-\gamma)
> $$
> which is part of Proposition 1.14 (Step 5).
>
> The distributive law
> $$
> \alpha(\beta + \gamma) = \alpha\beta + \alpha\gamma
> $$
> breaks into cases. For example, suppose $\alpha > 0^\ast$, $\beta < 0^\ast$, $\beta + \gamma > 0^\ast$.
>  Then $\gamma = (\beta + \gamma) + (-\beta)$, and (since distributivity holds in $R^+$):
> $$
> \alpha\gamma = \alpha(\beta + \gamma) + \alpha(-\beta).
> $$
> But $\alpha(-\beta) = -(\alpha\beta)$.
>  Thus
> $$
> \alpha\beta + \alpha\gamma = \alpha(\beta + \gamma).
> $$
> Other cases are handled similarly.
>
> We have now completed the proof that **$R$ is an ordered field with the least upper bound property**.
>
> **Step 8**
>
> For $r \in \mathbb{Q}$, associate the cut
> $$
> r^\ast = \{ p \in \mathbb{Q} : p < r \}.
> $$
> Each $r^\ast$ is a cut, i.e. $r^\ast \in R$.
>
> These cuts satisfy:
>
> **(a)** $r^\ast + s^\ast = (r + s)^\ast$
>
> **(b)** $r^\ast s^\ast = (rs)^\ast$
>
> **(c)** $r^\ast < s^\ast$ iff $r < s$
>
> Proof of (a):
>  If $p \in r^\ast + s^\ast$, then $p = u + v$ with $u < r, v < s$, hence $p < r+s$, so $p \in (r+s)^\ast$.
>
> Conversely, suppose $p \in (r + s)^\ast$.
>  Then $p < r+s$.
>  Choose $t$ so that $2t = r + s - p$, put
> $$
> r' = r - t,\qquad s' = s - t.
> $$
> Then $r' \in r^\ast$, $s' \in s^\ast$, and $p = r' + s'$, so $p \in r^\ast + s^\ast$.
>  This proves (a).
>  The proof of (b) is similar.
>
> If $r < s$, then $r \in s^\ast$, but $r \notin r^\ast$; hence $r^\ast < s^\ast$.
>  If $r^\ast < s^\ast$, then there is a $p \in s^\ast$ such that $p \notin r^\ast$.
>  Hence $r \le p < s$, so $r < s$.
>  This proves (c).
>
> **Step 9**
>
> From Step 8, replacing rational numbers $r$ by their corresponding cuts $r^\ast \in R$ preserves sums, products, and order.
>  Thus the ordered field $\mathbb{Q}$ is **isomorphic** to the ordered field
> $$
> \mathbb{Q}^\ast = \{ r^\ast : r \in \mathbb{Q} \}.
> $$
> Although $r^\ast$ is not literally the same as $r$, the arithmetic and order are identical.
>  This identification allows us to regard $\mathbb{Q}$ as a **subfield** of $R$.
>
> It is a fact (not proved here) that **[[any two ordered fields with the least-upper-bound property are isomorphic]]**.



---

## Properties of $\R$

> **Theorem - Archimedean property of $\R$**
>
> If x ∈ R, y ∈ R, and x > 0, then there is a positive integer n 
>
> such that
> $$
> nx > y.
> $$



> **Theorem - $\Q$ is dense in $\R$**
>
> If x ∈ R, y ∈ R, and x < y, then there exists a $p ∈ \Q$ such that x < p < y.  

---

> **Theorem - Uniqueness of roots in $\R$**
>
> For every real x > 0 and every integer n > 0, there is one and only one positive real y such that $y^n = x$.



>*Proof*.
>
>*Proof of uniqueness*
>
>Since $0<y_1<y_2$, then $y_1^n<y_2^n$.
>
>
>
>*Proof of existence*
>
>Let E be the set consisting of all positive real numbers t such that $t^n < x$.
>
>- If $t=\frac{x}{1+x}$, then $t^n<t<x$. Thus $t\in X$ and $E$ is not empty.
>
>- If $t>1+x$, then $t^n>t>x$. Thus $t\notin E$, implying $1+x$ is an upper bound of E. Hence implies the existence of $y=\sup E$
>
>Show $y^n=x$ by conflict of $y^n>x$ and $y^n<x$.
>
>1. Assume $y^n<x$
>
>   Choose $h \in (0,1)$ and
>   $$
>   h<\frac{x-y^n}{n(y+1)^{n-1}}
>   $$
>   Then
>   $$
>   (y+h)^n-y^n<hn(y+h)^{n-1}<hn(y+1)^{n-1}<x-y^n.
>   $$
>   Thus $(y+h)^n<x$ and $y<y+h\in E$. Contradict to $y$ being the upper bound of E.
>
>2. Assume $y^n>x$
>
>   Choose $k$ s.t.
>   $$
>    \mathrm{k}=\frac{y^n-x}{ny^{n-1}}.
>   $$
>   Then $0<k<y$. For $t\ge y-k$
>   $$
>   y^n-t^n\leq y^n-(y-k)^n<kny^{n-1}=y^n-x.
>   $$
>   Thus $t^n>x$ and $t\notin E$, showing that $y-k<y$ is an upper bound of E. 
>
>   Contradict to $y$ being the least upper bound of $E$.
>
>$\square$





# Other number system

## The extended real number system

> **Definition - The extended real number system**
>
> The extended real number system consists of the real field $\R$ and two symbols, $+∞$ and $-∞$. We preserve the original order in $\R$ and define 
> $$
> -∞ < x < +∞
> $$
> for every $x ∈ \R$.



The extended real number system has following conventions:

1. If x is real
   $$
   x+\infty=+\infty,\quad x-\infty=-\infty,\quad\frac{x}{+\infty}=\frac{x}{-\infty}=0.
   $$

2. If x>0
   $$
   x\cdot(+\infty)=+\infty,\:x\cdot(-\infty)=-\infty.
   $$

3. If x<0
   $$
   x\cdot(+\infty)=-\infty,\:x\cdot(-\infty)=+\infty.
   $$

> [!note]
>
> The extended real number system does not form a field, since:
>
> - $+\infty+(-\infty)$ is not defined,
> - $0\cdot (+\infty)$ is not defined,
> - $+\infty$ and $-\infty$ have not inverse,
> - If above is defined, it will conflict with existing axioms.



## Complex field

> **Definition - Complex number**
>
> A complex number is an ordered pair (a, b) of real numbers. “Ordered” means that (a, b) and (b, a) are regarded as distinct if $a \ne b$.
>
> Let x = (a, b), y = (c, d) be two complex numbers. We write x = y iff a = c and b = d.
>
>  We define
> $$
> x + y = (a + c, b + d)\\
> xy = (ac - bd, ad + bc).
> $$



> **Theorem - Complex numbers form a field**
>
> These definitions of addition and multiplication turn the set of all complex numbers into a field, where (0, 0) and (1, 0) in the role of 0 and 1.



> *Proof*
>
> Omit.



## Euclidean spaces

> **Definition - Euclidean spaces**
>
> Let $n \in \mathbb{N}$ with $n \ge 1$.
>  The **Euclidean space of dimension $n$** is the pair
> $$
> \big(\mathbb{R}^n, \langle \cdot, \cdot \rangle \big),
> $$
> where:
>
> 1. **Underlying set.**
>    $$
>    \mathbb{R}^n = \{ (x_1,\dots,x_n) : x_i \in \mathbb{R} \}.
>    $$
>
> 2. **Vector space structure.**
>     $\mathbb{R}^n$ is equipped with coordinatewise addition and scalar multiplication:
>    $$
>    (x_1,\dots,x_n)+(y_1,\dots,y_n)=(x_1+y_1,\dots,x_n+y_n),
>    $$
>
>    $$
>    \lambda(x_1,\dots,x_n) = (\lambda x_1,\dots,\lambda x_n) \quad (\lambda\in\mathbb{R}).
>    $$
>
> 3. **Inner product.**
>     The **standard Euclidean inner product** is the map
>    $$
>    \langle \cdot, \cdot \rangle : \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}
>    $$
>    defined by
>    $$
>    \langle x, y \rangle = \sum_{i=1}^{n} x_i y_i.
>    $$
>
> 4. **Norm and metric (induced).**
>     The inner product induces:
>
>    - the Euclidean norm
>      $$
>      \|x\| = \sqrt{\langle x, x \rangle},
>      $$
>
>    - the Euclidean distance
>      $$
>      d(x,y)=\|x-y\|.
>      $$



> **Theorem - Basic properties of Euclidean space**
>
> Suppose $x, y, z ∈ \R^k$, and α is real. Then  
>
> 1. $|x|\ge0$
> 2. $|x|=0\iff \mathbf x=0$
> 3. $|\alpha x|=|\alpha||\mathbf x|$
> 4. $|\mathbf{x}\cdot\mathbf{y}|\leq|\mathbf{x}|\:|\mathbf{y}|$
> 5. $|\mathbf{x}+\mathbf{y}|\leq|\mathbf{x}|+|\mathbf{y}|$
> 6. $|\mathbf{x}-\mathbf{z}|\leq|\mathbf{x}-\mathbf{y}|+|\mathbf{y}-\mathbf{z}|$









