---
tags:
  - math
  - 微积分
---
这种积分是在黎曼积分的基础上，对黎曼积分的一种推广。下面我们参考[[黎曼积分的定义以及黎曼可积的判别]]，来定义R-S积分。

### 1. 关于Riemann-Stieltjes可积的基本概念

> [!概念1.1：Riemann-Stieltjes和]
> 对于$[a,b]$上的函数$f$以及一个实值函数$g$，点列$$a=x_0<x_1<\cdots <x_n=b$$称之为$[a,b]$的一个划分$P$，令$\Delta \alpha_i:=\alpha(x_i)-\alpha(x_{i-1})$，$x_i^{*}\in [x_{i-1},x_i]$是闭区间中当中任意的一点,记所有固定的这样的每个区间的代表元的集合为$\xi:=\{x_1^{*},...,x_n^{*}\}$。那么函数$f$在区间$[a,b]$上的R-S和定义为:$$S_f(P,\xi,\alpha):=\sum_{i\leq n} f(x_i^{*})\Delta \alpha_i$$
* 这里不要求$f$一定是实值的，但是要求$\alpha$一定是实值的。

> [!概念1.2:R_S可积，以及R_S积分]
> 对任意的$\varepsilon>0$存在$\delta_{\varepsilon}$使得任意对区间$[a,b]$的划分$P$满足直径$\lambda(P)<\delta_{\varepsilon}$都满足存在一个实数$I$使得$$\left|I-S_f(P,\xi,\alpha)\right|<\varepsilon$$那么我们称$I$为函数$f$在区间$[a,b]$上关于$\alpha$的R-S积分，表示为$$I:=\int_{a}^{b}f(x)\,d\alpha(x)$$我们称$f$在区间$[a,b]$上关于函数$\alpha$是R-S可积的。

* 我们之所以称R-S可积是对Riemann可积的推广，因为我们只需要令$\alpha(x):=x$，那么以上定义就是黎曼积分。

下面是R-S积分最基本的性质：

> [!Riemann_Stieltjes积分最基本的性质]
> 1. 线性性1：假设$f,g$都是闭区间$[a,b]$上关于函数$\alpha$可积的函数，那么函数$f+g$在此闭区间上关于函数$\alpha$是可积的,并且满足:$$\int_{a}^b (f+g)\,d\alpha=\int_a^{b}f\,d\alpha+\int_{a}^{b}g\,d\alpha$$对于任意实数$c$，$cf,cg$都是关于$h$可积的，并且满足$$\int_a^{b}cf\,d\alpha=c\int_{a}^bf\,d\alpha$$
> 2. 线性性2：假设$f$在闭区间$[a,b]$上关于函数$\alpha,\beta$都可积，那么函数$f$在此闭区间上关于函数$\alpha+\beta$也是可积的，并且满足$$\int_{a}^{b}f\,d(\alpha+\beta)=\int_{a}^{b}f\,d\alpha+\int_{a}^{b}f\,d\beta$$以及对于任意实数$c$，$f$关于$c\alpha$也是可积的，并且满足$$\int_{a}^{b}f\,d(c\alpha)=c\int_{a}^{b}f\,d\alpha$$
> 3. 对积分区间的拆分：假设$b \in (a,c)$，并且函数$f$在闭区间$[a,c]$上关于函数$\alpha$是可积的，那么函数分别在闭区间$[a,b],[b,c]$上关于$\alpha$都是可积的，并且满足:$$\int_{a}^c f\,d\alpha=\int_{a}^b f\,d\alpha+\int_{b}^c f\,d\alpha$$
> 4. 单调性：如果两个函数$f,g$在闭区间$[a,b]$上关于**单调不减**的函数$\alpha$可积，并且$f(x)\leq g(x)$那么它们的积分满足$$\int_{a}^b f\,d\,\alpha\leq \int_a^b g\,d\alpha$$并且如果$\alpha$是严格单调增加的函数，并且$f,g$都是连续函数，那么上述积分不等式成立，当且仅当$f(x)=g(x),\forall x \in [a,b]$
> 5. 基本的积分不等式：如果$f$在闭区间$[a,b]$上关于**单调不减**的函数$\alpha$可积，那么$$\left|\int_{a}^b f\,d\,\alpha\right|\leq \int_{a}^b |f|\,d\,\alpha$$以及$$(\alpha(b)-\alpha(a))\inf_{x \in [a,b]}f(x)\leq \int_{a}^b f\,d\,\alpha\leq (\alpha(b)-\alpha(a))\sup_{x \in [a,b]}f(x)$$

(此处需要补充证明)
### 2. 中值定理与微积分基本定理

我们也可以把积分中值定理和微积分基本定理拓展到Riemann-Stieltjes积分当中。

### 3. 分部积分与换元法

#### 3.1 两种积分之间的关系

> [!定理3.1.1:Riemann积分与Riemann_Stieltjes积分之间的关系]
> 假设定义在闭区间$[a,b]$上的函数$f$有界，并且$g$黎曼可积$$\alpha(x):=\alpha(a)+\int_{a}^{x}g(t)\,dt$$那么$f$在闭区间$[a,b]$上关于函数$\alpha$是Riemann-Stieltjes可积,当且仅当$fg$在闭区间$[a,b]$上可积。如果可积，两种积分之间的关系为$$\int_{a}^b f\,d\alpha =\int_{a}^b fg\,dx$$

首先，如果$fg$可积，那么令$I := \int_{a}^b fg\,dx$那么为了证明$f$关于$\alpha$是R-S可积的，我们无非就是要证明对任意$\varepsilon>0$，存在一个$\delta_{\varepsilon}>0$使得任意带标志点的$(P,\xi)$满足$\lambda(P)<\delta_{\varepsilon}$的带标志点的划分，都有$$|S_f(P,\xi,\alpha)-I|<\varepsilon$$为了估计上面的式子，我们可以考虑分段估计$$\begin{aligned}|S_f(P,\xi,\alpha)-I|&\leq |I-S_{fg}(P,\xi)|+|S_{fg}(P,\xi)-S_f(P,\xi,\alpha)|\\&< \frac{1}{2}\varepsilon+|S_{fg}(P,\xi)-S_f(P,\xi,\alpha)|\end{aligned}$$
* 其中$S_{fg}(P,\xi)$是函数$fg$的黎曼和。$|I-S_{fg}(P,\xi)|<\frac{1}{2}\varepsilon$来自于$fg$黎曼可积的定义。
* 此处之所以考虑如此分段，是因为后面$|S_{fg}(P,\xi)-S_f(P,\xi,\alpha)|$可以做逐项估计，这样会比原本的式子更容易操作。

$$\begin{aligned}|S_f(P,\xi,\alpha)-S_{fg}(P,\xi)|&\leq \sum_{i=1}^n |f(\xi_i)|\left|\alpha(x_{i})-\alpha(x_{i-1})-g(\xi_i)(x_i-x_{i-1})\right|\\&=\sum_{i=1}^n|f(\xi_i)|\left|\int_{x_{i-1}}^{x_{i}}g(t)\,dt-g(\xi_i)(x_i-x_{i-1})\right| \\&\leq \sum_{i=1}^n|f(\xi_i)|\omega_{g}([x_{i-1},x_i])(x_i-x_{i-1})\\&\leq M\sum_{i=1}^n\omega_{g}([x_{i-1},x_i])(x_i-x_{i-1})\\&<M\varepsilon\end{aligned}$$
* 该估计的第三行当中我们用到了“振幅”的概念，其定义为$$\omega_f(E):=\sup_{x,y\in E}|f(x)-f(y)|$$就是说在某个集合当中，两个实值得函数差的绝对值的上确界。此处$$\begin{aligned}\left|\int_{x_{i-1}}^{x_{i}}g(t)\,dt-g(x_i^{*})(x_i-x_{i-1})\right|&\leq \int_{x_{i-1}}^{x_{i}}|g(t)-g(x_i^{*})|\,dt \\&\leq \omega_{g}([x_{i-1},x_i])(x_i-x_{i-1}) \end{aligned}$$这是典型的[[逐项估计]]的第四节当中提到的$|\int X-Y|$类型的估计。
* 最后我们利用函数$g$的黎曼可积性，参考[[黎曼积分的定义以及黎曼可积的判别]]

因此我们得到$$|S_f(P,\xi,\alpha)-I|<(\frac{1}{2}+M)\varepsilon$$于是$f$关于$\alpha$是R-S可积的。

反过来，如果$f$关于$\alpha$是R-S的，那么我们大可以假设其积分的结果为$$J:=\int_a^b f\,d\alpha$$然后因为$|S_f(P,\xi,\alpha)-J|$是可以任意小的，并且由之前的证明，我们知道$|S_f(P,\xi,\alpha)-S_{fg}(P,\xi)|$可以被很好的控制起来，因为$g$的黎曼可积性。那么由于$$\begin{aligned}|S_{fg}(P,\xi)-J|&\leq |J-S_{f}(P,\xi,\alpha)|+|S_f(P,\xi,\alpha)-S_{fg}(P,\xi)|\\&< \frac{1}{2}\varepsilon+|S_{fg}(P,\xi)-S_f(P,\xi,\alpha)|\\&<\frac{1}{2}\varepsilon+M\varepsilon\end{aligned}$$于是说明黎曼和$S_{fg}(P,\xi)$关于$\lambda(P)\to 0$的极限是$J$这就说明$$\int_{a}^b f\,d\alpha =\int_{a}^b fg\,dx$$

#### 3.2 R-S积分的分部积分公式

> [!定理3.2.1：分部积分公式]
> 函数$f$在闭区间$[a,b]$上关于$\alpha$是R-S可积的，当且仅当函数$\alpha$在闭区间$[a,b]$上关于$f$是R-S可积的。此外二者满足公式$$\int_{a}^b f\,d\alpha +\int_{a}^b \alpha\,df=f(b)\alpha(b)-f(a)\alpha(a)$$

### 4. R-S可积的黎曼判别法

#### 4.1 有界变差函数

