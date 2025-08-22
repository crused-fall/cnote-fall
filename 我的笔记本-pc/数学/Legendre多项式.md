# Legendre Polynomial's Origin

## 1.motivation

Find a polynomial $X_n$ with n degree, s.t. $\forall Q(x)$ of less than n degree, following equality holds true $\forall a,b\in \mathbb{R}$ :

![image-20250822110757586](C:\Users\19006\AppData\Roaming\Typora\typora-user-images\image-20250822110757586.png)

## 2. analysis

take $X_n$ as the $n$-th derivative of $R(x)$, so $R(x)$ can be obtained by performing the integral operation n times on $X_n(x)$.

Meanwhile, it can be assured that following statement is true:
$$
R(a)=0, R'(a)=0, \cdots,R^{(n-1)}(a)=0
$$
thus:
$$
\begin{aligned}\int_a^bR^{(n)}(x)Q(x)dx&=\left[Q(x)R^{(n-1)}(x)-Q^{\prime}(x)R^{(n-2)}(x)+\cdots\right.\\&\pm Q^{(n-1)}(x)R(x)\bigg]\bigg|_a^b\mp\int_a^bQ^{(n)}(x)R(x)dx\end{aligned}
$$
equivalent to:
$$
R(b)=0,R'(b)=0,\cdots,R^{(n-1)}(b)=0
$$
for $Q(x)$ is arbitrary selected.

Therefore $R(x)$ has $a,b$ as $n$-th roots, thus:
$$
X_n(x)=c_n\frac{d^n}{dx^n}\left[(x-a)^n(x-b)^n\right]
$$

# Legendre Polynomial

Set $a=-1,b=1$, we get **Legendre Polynomial**
$$
X_n(x)=c_n\frac{d^n(x^2-1)^n}{dx^n}
$$

## Legendre polynomials have n different roots in [-1,1]

For $R(x)= (x-1)^n(x+1)^n$, $\forall m\in \{1,2,\cdots n-1\}R^{(m)}(-1)=R^{(m)}(1)=0$,thus by **Rolle's theorem**:

- $R'$ has one root in $(-1,1)$
- $R''$ has two roots in $(-1,1)$
- $\cdots$
- $R^{(n-1)}$ has $n-1$ roots in $(-1,1)$
- $X(x)=R^{(n)}$ has n roots in $(-1,1)$

## Value of Legendre polynomial at -1 and 1

Set $c_n=1$, apply **Leibniz's formula**
$$
\begin{aligned}X_n(x)&=(x+1)^n\cdot\frac{d^n(x-1)^n}{dx^n}+C_n^1\cdot\frac{d(x+1)^n}{dx}\cdot\frac{d^{n-1}(x-1)^n}{dx^{n-1}}+\cdots\\&+\frac{d^n(x+1)^n}{dx^n}\cdot(x-1)^n\end{aligned}
$$
thus :
$$
X_n(x)=2^n\cdot n!\qquad X_n(-1)=(-1)^n\cdot 2^n \cdot n!
$$
Therefore if define $c_n= \frac{1}{2^n\cdot n!}$ , we get the **most commonly used Legendre polynomial** whose characteristic is $P_n(1)=1,P_n(-1)=(-1)^n$

## The differential equation satisfied by Legendre polynomial

