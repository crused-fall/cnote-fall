---
tags:
  - math
  - 数论
  - 丢番图逼近
---
### 1. 证明序列$\eta_n$在$[0,1]$当中稠密

> [!问题1]
> 证明，序列$\eta_n = \left\{\frac{n}{2\pi}\right\}$形成的集合作为$[0,1]$区间当中的稠密子集。

针该问题的证明，其中一个思路是可以用过Weyl判别去证明一个加强版本的命题，即证明其均匀分布。(参考[[模1均匀分布与Weyl判别]])

不过我们还可以通过丢番图逼近的想法来证明这件事，也就是kronecker的定理。

> [!kronecker定理]
> 对于给定的无理数$\alpha$，以及$\forall \beta\in\mathbb{R}$，任意$\varepsilon > 0$那么存在正整数$q$以及整数$p$使得$$|q\alpha-\beta-p|<\varepsilon$$
> 

这里我们会好奇，假设我们固定一个$p$，那么此处存在的$q$会是与$q,\alpha,\beta$有怎么样关系的一个整数?其实就是离$q\alpha -\beta$最近的整数，当$\varepsilon>0$足够小的时候，Kronecker定理告诉我们$|q\alpha-\beta-p|<\varepsilon$。也就是说$p$作为一个整数，距离实数$q\alpha -\beta$的距离不足$\varepsilon$，这只有距离此实数最近的那个整数才能做到。因此Kronecker定理还可以叙述为:

对于实数$x\in \mathbb{R}$我们可以借用$||x||$来定义距离$x$与最近的整数的距离，形式上来说$$||x||:=\min\{|x-n|:n\in \mathbb{Z}\}$$由定义我们立刻知道:
1. $||x|| \in [0,\frac{1}{2}]$
2. $||x|| = \min\{\{x\},1-\{x\}\}$

用该定义，我们还可以把Kronecker定理叙述为:

> [!kronecker定理(版本2)]
> 对于给定的无理数$\alpha$，以及$\forall \beta\in\mathbb{R}$，对任意足够小的$\varepsilon > 0$存在正整数$q_{\varepsilon}$使得$$||q_{\varepsilon}\alpha-\beta||<\varepsilon$$

此时如果令$\beta=0$,那么这便是Dirichlet定理：

> [!Dirichlet定理]
> 对于无理数$\alpha$以及任意的$\varepsilon>0$存在正整数$q_{\varepsilon}$使得$$||q_{\varepsilon}\alpha||<\varepsilon$$

回到“问题1”，我们发现，如果我们可以证明Kronecker定理成立，那么我们可以令$\alpha=\frac{1}{2\pi}$,于是由于这是一个无理数，所以对于$\forall \beta\in(0,1)$以及任意足够小的$\varepsilon$，那么一定存在一个正整数$p_{\varepsilon}>0$以及整数$p_{\varepsilon}$使得$$|q_{\varepsilon}\alpha-\beta-p_{\varepsilon}|<\varepsilon$$于是“问题1”中的稠密性就会成立。这是因为我们发现：

> [!一个观察]
> 在Kronecker定理当中，当我们选取一个***足够小的***$\varepsilon$，从而确定好一个对应的$q_{\varepsilon}$以后，此时Kronecker定理中的$p_{\varepsilon}$恰好是$q_{\varepsilon}\alpha$的下整，从而从而$$q_{\varepsilon}\alpha-p_{\varepsilon}=\{q_{\varepsilon}\alpha\}$$

因为Kronecker定理讲的是不等式$$p_{\varepsilon}+\beta-\varepsilon<q_{\varepsilon}\alpha<p_{\varepsilon}+\beta+\varepsilon$$那么根据观察$q_{\varepsilon}\alpha-p_{\varepsilon}=\{q_{\varepsilon}\alpha\}$于是我们得到$\{q_{\varepsilon}\alpha\}\in (\beta-\varepsilon,\beta+\varepsilon)$，这便是我们想要证明的序列$\{n\alpha\}$的稠密性的含义。而要做到$q_{\varepsilon}\alpha-p_{\varepsilon}=\{q_{\varepsilon}\alpha\}$我们只需要选取足够小的$\varepsilon$，满足$$\beta+\varepsilon<1,\beta-\varepsilon>0$$所以，整个问题我们可以转换为证明Kronecker定理。

> [!Kronecker定理（版本3）]
> 若实数$\frac{\beta}{\alpha} \not \in \mathbb{Q}$，那么集合$\alpha \mathbb{Z}+\beta \mathbb{Z}$在实数中稠密（欧氏拓扑）。

这个版本的定理由Kronecker定理的第一个版本很容易得到：
1. 上述定理的定量版本为：对任意的实数$r$以及任意的$\varepsilon>0$存在一对整数$p,q$使得$$|p\alpha+q\beta-r|<\varepsilon$$
2. 而Kronecker定理告诉我们，因为$\frac{\alpha}{\beta}$是无理数，所以对于任意的实数$t$以及任意的$\varepsilon'>0$存在一个正整数$a$以及整数$b$使得$$|a\frac{\alpha}{\beta}-b-t|<\varepsilon'$$这当然与我们想要的结果有一定的差距，我们可以调整上述表达为$$|a\alpha-b\beta-t\beta|<\varepsilon'\beta$$所以实际上我们只需要令$\varepsilon'=\frac{1}{\beta}\varepsilon,$$t=\frac{1}{\beta}r$那么此时$p=a,q=-b$从而由Kronecker定理得到了我们想要的定量版本的结果。

* [[利用连续函数的identity theorem证明函数方程]]:此文章中的“问题2”中，我们利用$\sqrt{2}\mathbb{Z}+\sqrt{3}\mathbb{Z}$在实数中稠密性，加上连续函数$f$在此集合上取值为常数，从而证明函数在整个实数集上是常数。
* [[周期函数的和还是周期函数吗？]]：其中“命题3”，我们用如同上面例子的方法，结合Kronecker定理（版本3），可以证明两个非常数的连续周期函数$f,g$如果最小正周期的比值是无理数，那么$f+g$不会是一个周期函数。
### 1. 经由Dirichlet定理证明Kronecker定理

针对一维的特殊形式的Kronecker定理，可以经由Dirichlet定理来证明。下面我们假设$\beta \in (0,1)$,并且不失一般性假设无理数 $\alpha>0$。只要能证明这种情形下的Kronecker定理，那么就不难把它推广到整个实数上。

现在如果假定Dirichlet定理成立，那么存在一对整数$p_{\varepsilon}'>0$以及正整数$q_{\varepsilon}'$使得$$p'_{\varepsilon}-\varepsilon<q'_{\varepsilon}\alpha<p'_{\varepsilon}+\varepsilon$$令$h_{\varepsilon}=q'_{\varepsilon}\alpha-p'_{\varepsilon}$，那么其落在区间$(-\varepsilon,\varepsilon)$。

1. 假设$h_{\varepsilon}>0$,也就是说$p'_{\varepsilon}$就是$q'_{\varepsilon}\alpha$的下整，并且$h_{\varepsilon}\in (0,\varepsilon)$。现在我们可以把$(0,1)$的区间分为$n_{\varepsilon}$个长度不超过$h_{\varepsilon}$的区间$$(0,h_{\varepsilon}],\cdots,((n_{\varepsilon}-1)h_{\varepsilon},1)$$那么$\beta$必然在其中某一个区间上。假设$\beta$属于从左到右的第$k$个区间上，由于每个区间的长度最多不过$h_{\varepsilon}$,于是$\beta$距离区间左端点的距离必然满足$$|kh_{\varepsilon}-\beta|<h_{\varepsilon}<\varepsilon,k\in \{0,\cdots,n_{\varepsilon}-1\}$$那么此不等式展开就是$$|(kq_{\varepsilon}')\alpha-kp_{\varepsilon}'-\beta|<\varepsilon$$那么我们只需要令$q_{\varepsilon}=kq_{\varepsilon}',p_{\varepsilon}=kp_{\varepsilon}'$那么就可以得到Kronecker定理想要的不等式。
2. 如果$h_{\varepsilon}<0$，但由于$\beta\in (0,1)$,因此我们可以考虑用$-h_{\varepsilon}$去分割区间$(0,1)$然后重复上面的证明。

所以最终我们需要证明的无非就是Dirichlet定理。
### 2. 证明Dirichlet定理

首先我们给出一个定量版本的Dirichlet定理

> [!Dirichlet定理(版本2)]
> $\alpha$是无理数，对于任意正整数$n$存在正整数$q\leq n$使得$$0<||q\alpha||<\frac{1}{n}$$

#### 2.1 Dirichlet定理的推论

这个版本的Dirichlet定理的结果相较于“版本1”是更强的。因为我们可以从中获得下面的推论：

> [!Dirichlet定理(版本2)的推论1]
> 对于无理数$\alpha$以及任意的$\varepsilon>0$存在无限多个正整数$q$使得$$||q\alpha||<\varepsilon$$

我们现在来考虑序列$||n\alpha||$的下确界$\inf_{n\geq 1}||n\alpha||$。如果"推论1"不对，那么存在一个$\varepsilon_0$使得集合$A:=\{n\geq1 :||n\alpha||<\varepsilon_0\}$是有限的，这意味着序列$||n\alpha||$存在最最小值$r>0$，于是$$\inf_{n\geq 1}||n\alpha||=\inf_{n\in A}||n\alpha||=r>0$$但是“版本2的Dirichlet定理”分明告诉我们自然数当中存在一个子列$q_n$使得$$||q_n\alpha||<\frac{1}{n}$$那么$$\inf_{n\in \mathbb{Z}^{+}}||n\alpha||\leq \inf_{n\geq 1}||q_n\alpha||\leq \inf_{n\geq 1}\frac{1}{n}=0$$这是矛盾的。

* 注意这里得到的不过是$$\inf_{n\geq 1}||n\alpha||=0$$而不是说$||n\alpha||$的极限的性质。通过[[模1均匀分布与Weyl判别]]当中2.2我们知道$\varepsilon(n\alpha)$是区间$[-1/2,1/2)$当中均匀分布的数列，而$||n\alpha||=|\varepsilon(n\alpha)|$因此实际上这个序列的极限是不存在的。

经过这个证明我们还可以得到下面的推论：

> [!Dirichlet定理(版本2)，推论2]
> 对于无理数$\alpha$存在无数多个正整数$q$使得$$q||q\alpha||<1$$
* 当然我们还可以叙述为，存在无数多对互素的整数(防止无穷多个相同的有理数)$p,q$，其中$q>0$满足不等式$$\left|\alpha-\frac{p}{q}\right|<\frac{1}{q^2}$$按照[[无理测度的定义以及基本的命题]]中对无理测度的定义，这告诉我们无理数的无理测度至少是2。

#### 2.2 Dirichlet定理(版本2)的证明

整个证明基于[[鸽笼原理]]。

我们把$||x||$表示为$$||x||=E(x)+\varepsilon(x)$$其中$E(x)$为整数而$\varepsilon(x)\in [-1/2,1/2)$称之为$x$模1的余数，此时$||x|| = |\varepsilon(x)|$。

此处的基本想法是基下面的观察：

> [!一个观察]
> 如果两个数$x,y$模$1$的余数的差小于一个足够小的$r>0$，那么$||x-y||<r$。因为$$|\varepsilon(x)-\varepsilon(y)|<r\iff |x-y-(E(x)-E(y))|<r$$此时如果$r<\frac{1}{2}$，这便意味着$x-y$这个实数与$E(x)-E(y)$这个整数的距离小于$r<\frac{1}{2}$,这意味着$E(x)-E(y)$就是距离$x-y$最近的整数，从而$$||x-y||<r$$

> [!证明的主要想法]
> 那么根据这个观察，我们如果能在正整数的某个子集$A_n$里面，找到两个$q_1\alpha,q_2\alpha$他们彼此之间模1的余数的距离小于$\frac{1}{n}$，并且保证$1\leq q_2-q_1\leq n$那么我们也就完成了对Dirichlet定理的证明。

那么这实际上是一个组合问题。如果我们把区间$[-1/2,1/2)$进行$n$等分，那么根据[[鸽笼原理]]，$k\alpha$模1的余数形成的序列$\varepsilon(k\alpha),k\in \{1,\cdots,n+1\}$必然有两个元素落在同一个区间当中。这个序列当中元素互不相同，因为$\alpha$是无理数。假设这两个不同的序列中的元素分别是$\varepsilon(q_1\alpha),\varepsilon(q_2\alpha)$并且为了方便假设$q_2>q_1$,于是$$0<|\varepsilon(q_1\alpha)-\varepsilon(q_2\alpha)|<\frac{1}{n}$$假设$n\geq 2$（$n=1$的时候是平凡的）,那么由于$$1\leq q_2-q_1\leq n$$根据上面的“观察”与“主要想法”，我们便完成了整个证明。

#### 2.3 定量版本的Kronecker定理

既然我们在2.2证明了定量版本的Dirichlet，那么我们也可以重复1当中经由Dirichlet定理证明Kronecker定理的过程，从而得到定量版本的Kronecker定理:

> [!kronecker定理的定量版本(版本3)]
> 对于给定的无理数$\alpha$，以及$\forall \beta\in\mathbb{R}$，对任意足正整数$n$存在正整数$|q|\leq n^2$使得$$||q\alpha-\beta||<\frac{1}{n}$$

本质上就是把第一节当中证明的Dirichlet定理替换为“定量版本的Dirichlet定理"然后把$\varepsilon$替换为$\frac{1}{n}$，然后重复一遍类似的论证过程。

此定理能得到推论:

> [!Dirichlet定理(版本3)的推论1]
> 对于无理数$\alpha$以及任意的实数$\beta$以及$\varepsilon>0$存在无限多个正整数$q$使得$$||q\alpha-\beta||<\varepsilon$$

整个论证过程也类似于2.1节Dirichlet定理推论的证明。









