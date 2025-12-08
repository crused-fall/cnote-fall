# Bernoulli inequality

## 1. Basic Bernoulli inequality

$\forall x>-1,\forall r\ge 1$
$$
(1+x)^r \ge 1+rx,\qquad x>-1.
$$
Equality holds only when $x=0$ or $n=1$

------

## 2. Sharper Estimates with Remainders

If $x>-1$ and $r>1$, Taylor expansion yields:
$$
(1+x)^r
= 1 + rx + \frac{r(r-1)}{2}x^2 + \cdots
\ge 
1+rx+\frac{r(r-1)}{2}x^2.
$$
This gives a stronger lower bound than the basic Bernoulli inequality.

------

## 3. General Convexity-Based Extension（Idea of Karamata/Jensen）

For a convex function $f$,

$$
f(1+x) \ge f(1) + x f'(1).
$$
Applying $f(t)=t^r$ produces the most general form of the Bernoulli inequality.



# Power Mean Inequality (幂平均不等式)

## 1. Definition of Power Means

Given positive numbers $x_1,\dots,x_n>0$ and a real parameter $r\in\mathbb{R}$, the **power mean of order $r$** is defined as
$$
M_r(x_1,\dots,x_n)
=
\left(\frac{1}{n}\sum_{i=1}^n x_i^r\right)^{1/r},
\qquad r\neq 0.
$$
For $r=0$, the definition is the limit case (geometric mean):
$$
M_0 =(\prod_{i=1}^\infty x_i)^\frac{1}{n}
$$
Special cases:

- $r=1$: arithmetic mean
- $r=0$: geometric mean
- $r=-1$: harmonic mean
- $r\to+\infty$: maximum
- $r\to-\infty$: minimum



**If $r > s$, then**
$$
M_r \ge M_s,
$$
with equality if and only if all $x_i$ are equal.

This gives the common chain:
$$
\min x_i 
\le
M_{-\infty}
\le 
M_{-1}
\le
M_0
\le
M_1
\le
M_2
\le
M_{+\infty}
\le
\max x_i.
$$

---

## 2. Weighted Power Means

Let $w_i>0$ with $\sum w_i = 1$. Define
$$
M_r(x) 
= 
\left( \sum_{i=1}^n w_i x_i^r \right)^{1/r}.
$$
Then still
$$
r > s \implies M_r \ge M_s.
$$

------

## 3 Power Means of Functions (Integral Form)

Define a continuous analogue on an interval:
$$
M_r(f)
=
\left(\frac{1}{b-a}\int_a^b f(x)^r\,dx\right)^{1/r}.
$$
Still satisfies
$$
r>s \implies M_r(f)\ge M_s(f).
$$


# Triangle Inequality

------

## 1. Basic Triangle Inequality

For any real or complex numbers $x,y$,
$$
|x+y|\le |x|+|y|.
$$
In normed vector spaces (including inner product and Banach spaces),
$$
\|x+y\|\le \|x\|+\|y\|.
$$
Equality holds exactly when $x$ and $y$ point in the same direction (or are positively linearly dependent).

------

## 2. Reverse Triangle Inequality

A direct consequence of the triangle inequality:
$$
\big|\,\|x\|-\|y\|\,\big|\le \|x-y\|.
$$
Equality occurs when $x$ and $y$ have the same (or opposite) direction with certain geometric alignment.





# Cauchy-Schwarz Inequality

## 1 Inner product spaces

For any vectors $x,y$ in an inner product space:
$$
|\langle x, y\rangle|
\le 
\|x\|\,\|y\|.
$$
Equality holds iff $x$ and $y$ are linearly dependent.

------

## 2 Euclidean form

For real or complex sequences $(a_i)$, $(b_i)$:
$$
\left|\sum_{i=1}^n a_i b_i\right|
\le 
\left( \sum_{i=1}^n a_i^2 \right)^{1/2}
\left( \sum_{i=1}^n b_i^2 \right)^{1/2}.
$$

------

## 3 Integral form

For measurable functions:
$$
\left| \int_a^b f(x)\,g(x)\,dx \right|
\le 
\left(\int_a^b |f|^2 \right)^{1/2}
\left(\int_a^b |g|^2 \right)^{1/2}.
$$

------



# Weierstrass Inequality

$\forall a_i>-1$
$$
\prod_{i=1}^n (1+a_i) \ge 1 + \sum_{i=1}^n a_i.
$$
The equality holds iff at most $1$ $a_i\ne0$ 