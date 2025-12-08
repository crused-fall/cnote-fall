# Stuff about e

## Basic definition

There are different types of definitions of **Nature constant**

1. Derivative

$$
\left.\frac d{dx}e^x\right|_{x=0}=1
$$

2. Limitation

$$
e=\lim_{n\to\infty}\left(1+\frac1n\right)^n
$$

3. Series

$$
e=\sum_{n=0}^\infty\frac1{n!}=1+\frac1{1!}+\frac1{2!}+\frac1{3!}+\cdots 
$$



## Prove of equivalence of different definitions

### 1. $\to$ 3.

Since it is satisfied that
$$
\frac{\mathrm d}{\mathrm dx}e^x=e^x \quad, \text{at } x=0
$$
Thus it can be deduced that
$$
\frac{\mathrm d^n}{\mathrm d x^n}e^x=e^x\quad , \text{at }x=0\quad\forall n\in\N
$$
Then by Taylor expansion
$$
e^1=\sum_{i=0}^\infty\frac{1^i}{i!}\left.\frac{\mathrm d^i}{\mathrm dx^i}e^x\right|_{x=0}=\sum_{n=0}^\infty\frac{1}{n!}
$$

### 3. $\to$ 2.

Set
$$
a_n=\left(1+\frac{1}{n}\right)^n
$$

1. Expand
   $$
   a_n
   =\sum_{k=0}^{n}\binom{n}{k}\left(\frac{1}{n}\right)^k
   =\sum_{k=0}^{n}\frac{n(n-1)\cdots(n-k+1)}{k!}\frac{1}{n^k}.
   $$
   Thus
   $$
   a_n=\sum_{k=0}^{n}c_{n,k}\frac{1}{k!},
   \quad c_{n,k}:=\frac{n(n-1)\cdots(n-k+1)}{n^k}.
   $$

2. For fixed $k$
   $$
   c_{n,k}=\prod_{j=0}^{k-1}\left(1-\frac{j}{n}\right)\xrightarrow[n\to\infty]{}1.
   $$

3. Compare with $e=\sum_{k=0}^\infty \frac{1}{k!}$ 
    $\forall$ $\varepsilon>0$。
    Choose $m$ s.t.
   $$
   \sum_{k>m}\frac{1}{k!}<\frac{\varepsilon}{3}.
   $$
   For $k=0,1,\dots,m$，since $c_{n,k}\to1$, $\exist n\ge N$：
   $$
   |c_{n,k}-1|<\frac{\varepsilon}{3(m+1)\,C},
   $$
   其中 $C:=\max_{0\le k\le m}\frac{1}{k!}$

4. Estimate the difference
   $$
   |a_n-e|
   =\left|\sum_{k=0}^{n}c_{n,k}\frac{x^k}{k!}-\sum_{k=0}^{\infty}\frac{x^k}{k!}\right|
   $$
   Divide into three parts
   $$
   \le \underbrace{\sum_{k=0}^{m}|c_{n,k}-1|\frac{|x|^k}{k!}}_{(I)}
      +\underbrace{\biggl|\sum_{k=m+1}^{n}c_{n,k}\frac{x^k}{k!}\biggr|}_{(II)}
      +\underbrace{\sum_{k>n}\frac{|x|^k}{k!}}_{(III)}.
   $$

   - For (I)：
     $$
     (I)\le \sum_{k=0}^{m}\frac{\varepsilon}{3(m+1)}=\frac{\varepsilon}{3}.
     $$

   - For (II)：
     $$
     (II)\le \sum_{k>m}\frac{|x|^k}{k!}<\frac{\varepsilon}{3}.
     $$

   - For (III)：
     $$
     (III)\le \sum_{k>m}\frac{|x|^k}{k!}<\frac{\varepsilon}{3}.
     $$

   Thus，
   $$
   |a_n(x)-E(x)|<\varepsilon.
   $$

Thus
$$
\lim_{n\to\infty}\left(1+\frac{x}{n}\right)^n=E(x).
$$



## Properties about $e$

