---
tags:
  - math
  - 代数基础
---
### 1. $\mathbb{Z}[x]$并非PID的证明

#### 1.1 从定义出发，给出一个反例

> [!例子1.1.1]
> $\langle 2,x\rangle$是$\mathbb{Z}[x]$的一个理想，但它并非主理想。

也就是说，不存在任意$p(x)\in \mathbb{Z}[x]$从而使得$$(2,x)=(p(x))$$如果存在，那么$2 \in \langle p(x)\rangle$于是存在多项式$q(x)\in \mathbb{Z}[x]$使得$$2=p(x)q(x)$$这意味着$$0=\deg p(x) +\deg q(x)$$也即是说这两个多项式都是常系数多项式，即整数。所以$p(x)$为$1,-1,2,-2$当中的一个。但这些都是不可能的：
* 如果$p(x)=2$,这意味着$(2,x)=(2)$,也即是说$x \in (2)$,这意味着$2|x$这是不可能的。
* 如果$p(x)=1$，这意味着$(2,x)=(1)=\mathbb{Z}[x]$。这也是不可能的。
* 其余情况都可以用类似的理由说明。


### 2. 推广的命题：$R[x]$为PID的条件

> [!定理2.1]
> 对于一个整环$R$上建立的多项式环$R[x]$，其为PID等价于$R$是一个域。

* [参考证明](https://proofwiki.org/wiki/Polynomial_Forms_over_Field_form_Principal_Ideal_Domain)
