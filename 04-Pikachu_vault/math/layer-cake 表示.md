---
tags:
  - math
  - 概率论
  - 实分析
---

> [!note] 定理0：Layer-Cake 表示
> 令$(X,\mu)$为测度空间，函数$f$为此空间当中的可测函数，定义$$m_f(t):=\mu(\{x\in X:|f(x)|>t\})$$那么$$\int_X |f|^p \,d\mu = p\int_{0}^{\infty} t^{p-1}m_f(t)\,dt,\quad p\in (0,\infty)$$

* 这里的等式建立在扩展实数系当中，如果$|f|^p$不可积，那么左右两边都为$+\infty$，等式依然成立。
* 这个式子有概率版本：假设$Y\geq 0$是概率空间当中的一个随机变量，那么$$\mathbb{E}(Y^p)=p\int_{0}^{\infty} t^{p-1}\mathbb{P}(Y>t)\,dt$$
通过$$|f(x)|^p=\int_{0}^{|f(x)|^p} 1\,ds$$那么我们可以把命题中左边的积分改写为一个双重积分，那么交换积分次序再辅以积分换元就可以得到：$$\begin{aligned}\int_{X} |f(x)|^p\,d\mu(x)&=\int_X \int_{0}^{|f(x)|^p} 1\,ds\,d\mu(x)\\&=\int_X \int_{\mathbb{R}} 1_{|f(x)|^p>s>0}\,ds\,d\mu(x)\\&= \int_{\mathbb{R}} \int_X1_{|f(x)|^p>s>0}\,d\mu(x)\,ds\\&=\int_{0}^{\infty} \mu(\{x\in X:|f(x)|^p>s\})\,ds\\&\xlongequal{t=s^p} p \int_{0}^{\infty}  t^{p-1}\mu(\{x\in X:|f(x)|>t\})\,dt\\&=p\int_{0}^{\infty} t^{p-1}m_f(t)\,dt\end{aligned}$$
* 此处交换次序用的是Tonelli定理，对于非负函数而言，即便积分为$+\infty$也成立，因此事先不需要假设可积性。（参考[[Fubini-Tonelli定理的例子与反例]])


### 1. 典型的运用

#### 1.1 Chebyshev不等式

> [!note] Chebyshev不等式
> 令$(X,\mu)$为测度空间，函数$f$为此空间当中的可测函数。对任意$\varepsilon>0$都有$$\mu(\{x\in X:|f(x)|>\varepsilon\})\leq \frac{\int_{X} |f|^p \,d\mu}{\varepsilon^p},\quad p>0$$

借助于Layer-Cake表示：
$$\int_X |f|^p \,d\mu = p\int_{0}^{\infty} t^{p-1}m_f(t)\,dt$$我们可以直接在$t=\varepsilon$的部分截断，从而$$\int_X |f|^p \,d\mu \geq  p\int_{0}^{\varepsilon} t^{p-1}m_f(t)\,dt\geq m_f(\varepsilon)p\int_{0}^{\varepsilon} t^{p-1}\,dt=\varepsilon^pm_f(\varepsilon)$$其中$m_f(\varepsilon)=\mu(\{x\in X:|f(x)|>\varepsilon\})$。

#### 1.2 p范数的极限

在[[函数p范数与无穷范数之间的关系]]当中我们需要证明$$\lim _{p \rightarrow \infty}\|f\|_{L^p}=\|f\|_{L^\infty}$$其中$||f||_{L^\infty}:=\inf \{r \in \mathbb{R}:\mu(\{x:|f(x)| \geq r\})=0\}$。其中关键在于下界的估计，即对任意$\varepsilon>0$都有$$\liminf_{p\to \infty} ||f||_{L^p}\geq \|f\|_{L^\infty}-\varepsilon\tag{1}$$借助于Layer-Cake表示我们可以容易地看出其中动机：对于积分$\int_{0}^{\infty} t^{p-1}m_f(t)\,dt$我们从$t=||f||_{L^{\infty}}-\varepsilon$处直接截断，于是$$||f||_{L^p}^p \geq p\int_0^{||f||_{L^{\infty}}-\varepsilon}t^{p-1}m_f(t)\,dt\geq (||f||_{L^{\infty}}-\varepsilon)^pm_f(||f||_{L^{\infty}}-\varepsilon)$$其中由$||f||_{L^{\infty}}$的定义，$m_f(||f||_{L^{\infty}}-\varepsilon)>0$。于是$$ ||f||_{L^p}\geq (\|f\|_{L^\infty}-\varepsilon)m_f(||f||_{L^{\infty}}-\varepsilon)^{1/p}$$两边取下极限，我们便得到了$(1)$。

#### 1.3 用于验证函数可积

首先是在概率论当中，很多随机变量我们只知道它值的分布信息，并不知道其具体的表达形式，因此想要通过直接对其$L^p$积分进行估计，从而判断其可积性是困难的。不过依照Layer-Cake表示，我们依旧可以判断其可积性。


> [!example] 例子1.3.1  
> 随机变量符合次高斯分布，即$$\mathbb{P}(|X|\geq t) \leq 2e^{-\frac{t^2}{K^2}}$$我们要判断其是否$L^p$可积，一个自然的思考角度便是从Layer-Cake表示出发：$$\mathbb{E}(|X|^p) = p\int_{0}^{\infty}t^{p-1}\mathbb{P}(|X|>t)\,dt\lesssim \int_{0}^{\infty}t^{p-1}e^{-\frac{t^2}{K^2}}\,dt=\frac{1}{2}K^{p}\Gamma(\frac{p}{2})$$于是我们便知道，这种随机变量总是$L^p,p>0$可积的。我们还可以通过Stirling公式知道$$\mathbb{E}(|X|^p)^{1/p}\lesssim \sqrt{p}$$

类似的道理，在实分析，调和分析当中有的函数同样难以求得具体表达，但其弱型估计是已知的（参考[[对Hardy-Littlewood Maximal函数的估计]]）。比如[Hardy-Littlewood极大函数](https://en.wikipedia.org/wiki/Hardy%E2%80%93Littlewood_maximal_function)

> [!note] 定理1.3.2: Hardy-Littlewood极大函数的强型估计
> 函数$f:\mathbb{R}^d \to \mathbb{C}$是局部$L^p,\quad p\geq 1$可积的函数,定义$$Mf(x):=\sup_{r>0}\frac{1}{|B(x,r)|}\int_{B(x,r)}|f(y)|\,dy$$为函数$f$的极大函数，那么存在与$p,d$有关的常数$C_{p,d}$使得$$||Mf||_{L^p}\leq C_{p,d}||f||_{L^p},\quad p\in (1,+\infty]$$

例如我们可以在Layer-Cake表示的基础上借助于dyadic估计，参考[[柯西凝聚判别法#^5269ef]]: $$\int |Mf|^p \,dx \asymp _{p} \sum_{k\in \mathbb{Z}} 2^{kp} m\{x\in \mathbb{R}^d:Mf>2^k\} \tag{1} $$这里为了与$|f|^p$进行比较，我们不直接利用弱(1,1)型估计，而是借助于引理:

> [!note] 引理1.3.3
> $$m(Mf>2^k)\leq \frac{C_d}{2^k}\int|f|1_{|f|>2^{k-1}}\,dx$$

* 令$g:=f\cdot1_{\{|f|\le \frac{\lambda}{2}\}},h:=f\cdot 1_{\{|f|> \frac{\lambda}{2}\}}$这样我们相当于把$f$按照值$\frac{\lambda}{2}$分成了两部分，即$$f=g+h$$如此一来便有$$Mf\leq Mg+Mh$$从而根据分布函数的性质$$m(\{Mf>\lambda\})\leq m(\{Mg>\frac{\lambda}{2}\})+m(\{Mh>\frac{\lambda}{2}\})\tag{a}$$同时注意到$$||Mg||_{L^{\infty}}\leq ||g||_{L^{\infty}}\leq \frac{\lambda}{2}$$于是$Mg(x)\leq \frac{\lambda}{2}$几乎处处成立，于是根据$(1)$得到$$m(\{Mf>\lambda\})\leq m(\{Mh>\frac{\lambda}{2}\})\tag{b}$$然后根据极大函数的弱(1,1)型估计$$m(\{Mh>\frac{\lambda}{2}\})\leq \frac{C_d}{\lambda/2}||h||_{L^1}=\frac{2C_d}{\lambda}\int|f(x)|1_{\{|f|>\frac{\lambda}{2}\}}(x)\,dx\tag{c}$$综合$(2),(3)$我们得到$$m(\{Mf>\lambda\})\leq \frac{2C_d}{\lambda}\int|f(x)|1_{\{|f|>\frac{\lambda}{2}\}}(x)\,dx$$然后我们只需要取$\lambda = 2^k$，便完成了对引理的证明。

根据此引理并结合上文提到的凝聚判别法$$\begin{aligned}\sum_{k\in \mathbb{Z}} 2^{kp} m\{x\in \mathbb{R}^d:Mf>2^k\}&\lesssim_d \sum_{k\in \mathbb{Z}}2^{k(p-1)}\int|f|1_{|f|>2^{k-1}}\,dx\\&=\int|f|\sum_{k:2^{k-1}<|f(x)|}2^{k(p-1)} \,dx\\&\asymp \int|f|\cdot |f|^{p-1}\,dx=||f||_{L^p}^p \end{aligned}$$于是根据$(1)$得到$$||Mf||_{L^p} \lesssim _{d,p} ||f||_{L^p},\quad p>1$$
* 此处用到了关于几何级数的估计$$\sum_{k:2^{k-1}<s}2^{k(p-1)}\asymp s^{p-1},\quad p>1$$








