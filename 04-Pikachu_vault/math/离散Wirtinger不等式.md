---
tags:
  - math
  - 调和分析
---
> [!note]  定理0(离散Wirtinger不等式,I. J. Schoenberg,Ky fan 1950-1955)
> 令$x_1,x_2,\cdots,x_n$是$n$个复数并且满足$\sum_{k=1}^n x_k=0$，此外约定$x_{n+1}=x_1$那么$$\sum_{k=1}^n |x_k|^2\leq \frac{1}{4\sin^2\left(\frac{\pi}{n}\right)}\sum_{k=1}^{n}|x_{k+1}-x_k|^2 $$不等式取等当且仅当$$z_k=A\cos(2\pi k/n)+B\sin(2\pi k/n)$$

* 回忆经典的[[Wirtinger不等式]]:如果$f$是周期为$T$的连续周期函数($f(0)=f(T)$),并且分段$C^{1}$,以及$\int_0^Tf(t) d t=0$那么:$$\displaystyle \int_0^T|f(t)|^2 d t \leq \frac{T^2}{4\pi^2} \int_0^T\left|f^{\prime}(t)\right|^2 d t$$ 即 $$ ||f||^2_{L^2} \leq \frac{T^2}{4\pi^2}||f^{\prime}||^2_{L^2}$$上面的离散形式的Wirtinger不等式就像是经典Wirtinger不等式的离散化。如果我们把$x_k:=f(k)$的话这也是一个定义在$\mathbb{Z}$上的周期为$n$的函数，此外$\sum_{k=1}^n |x_k|^2$可以理解为离散形式的$L^2$范数的平方，$\sum_{k=1}^{n}|x_{k+1}-x_k|^2$当中的被求和对象$x_{k+1}-x_k$可以理解为离散的微分，那么这里可以理解为离散形式的$f'$的$L^2$范数。如此一来在精神上，依旧是符合Wirtinger的思路：周期函数$f$的$L^2$范数会被其微分$f'$的$L^2$范数控制起来，即$||f||^2_{L^2} \leq C||f^{\prime}||^2_{L^2}$其中$C$只与$f$的周期有关。
* 最后我们观察到离散形式的Wirtinger不等式当中的系数$$\frac{1}{4\sin^2\left(\frac{\pi}{n}\right)}\to \frac{n^2}{4\pi^2}$$刚好与经典形式的Writinger对的上。


我们现在把已知条件翻译到群$G:=\mathbb{Z}/n\mathbb{Z}$以及此群上建立的Hilbert空间$L^2(\mu,G\to\mathbb{C})$（其中$\mu$是单位化了的计数测度）：
1. 首先$x_k:=f(k)$的周期性使得我们可以把$f$视为$G$上的一个函数。
2. 其次$\sum_{k=1}^n x_k=0$表明函数在$G$上关于计数测度的积分为0，即$$\int_{G} f(k)\,d\mu=\frac{1}{n}\sum_{k=1}^{n}x_k =0$$
3. 对函数进行傅里叶展开$$f(k)=\sum_{m=1}^n \widehat{f}(m)\chi_m(k)=\sum_{m=1}^n \widehat{f}(m)e^{2\pi i\frac{mk}{n} }$$其中$$\widehat{f}(m)=\langle f,\chi_m\rangle=\frac{1}{n}\sum_{m=1}^n f(k)e^{-2\pi i \frac{mk}{n}}$$
4. 我们要证明的是$$ ||f||^2_{L^2} \leq \frac{1}{4\sin^2\left(\frac{\pi}{n}\right)}||f^{\prime}||^2_{L^2}$$

* 参考证明[[Ky Fan不等式]]，以及[[Wirtinger不等式]]的经验，我们只需要在上考虑对函数做傅里叶展开，问题就不难对付了。因为对于差分算子而言傅里叶基（或者叫做特征函数）是其特征值。也就是说令$\chi_m(k):=e^{2\pi i \frac{mk}{n}}$是离散的傅里叶基当中的一个元素，或者说一个特征值，于是$$\begin{aligned}\Delta \chi_m(k)&=\chi_m(k+1)-\chi_m(k)\\&= (e^{2\pi i\frac{m}{n}}-1)\chi_m(k)\\&= \lambda_m\chi_m(k)\end{aligned}$$所以在这种涉及差分的，特别是$L^2$范数的问题当中对函数按照傅里叶基进行分解，或者说对函数做傅里叶变换是有利于简化问题的。此外这种傅里叶基的差分与傅里叶基的关系会保持到函数的傅里叶变换的关系当中$$\begin{aligned}\Delta f(k)&=\Delta \left(\sum_{m=1}^n \widehat{f}(m)\chi_m(k)\right)\\&=\sum_{m=1}^n \widehat{f}(m)\Delta \chi_m(k)\\&=\sum_{m=1}^n \widehat{f}(m)\lambda_m \chi_m(k)\end{aligned}$$另一边如果我们直接对函数做傅里叶展开$$\Delta f(k)=\sum_{m=1}^n \widehat{\Delta f}(m)\chi_m(k)$$于是我们得到$$\widehat{\Delta f}(m)= \widehat{f}(m)\lambda_m$$


回顾[[Wirtinger不等式]]的思路，先找到$\widehat{f},\widehat{f'}$之间的关系，然后通过Parseval恒等式联系起来各自范数，然后对范数进行放缩得到最终不等式。

首先Parseval不等式告诉我们$$||f||^2_{L^2} =n\sum_{m=1}^n |\widehat{f}(m)|^2$$然后由于差分与$\chi_m$之间的关系，我们有$$\begin{aligned}||\Delta f||^2_{L^2} &=n\sum_{m=1}^n |\widehat{\Delta f}(m)|^2\\&= n\sum_{m=1}^n |\widehat{f}(m)|^2|\lambda_m|^2  \end{aligned}$$其中$|\lambda_m|^2$经过三角函数的化简以后得到$|\lambda_m|^2=4\sin^2(\frac{\pi m}{n})$。此处只要$m\neq n$我们都有$$|\lambda_m|^2\geq 4\sin^2(\frac{\pi }{n})$$此外由于$\int_{G} f(k)\,d\mu =0$于是$\widehat{f}(n)=0$，从而
$$\begin{aligned}||\Delta f||^2_{L^2} &= n\sum_{m=1}^n |\widehat{f}(m)|^2|\lambda_m|^2 \\&=n\sum_{m=1}^{n-1} |\widehat{f}(m)|^2|\lambda_m|^2 \\ &\geq  n4\sin^2(\frac{\pi }{n})\sum_{m=1}^{n-1} |\widehat{f}(m)|^2\\&= n4\sin^2(\frac{\pi }{n})\sum_{m=1}^{n} |\widehat{f}(m)|^2\\&= ||f||^2_{L^2}4\sin^2(\frac{\pi }{n}) \end{aligned}$$
而原本的式子当中，带入$x_k=f(k)$，以及$$||f||_{L^{2}(G)}^2=\frac{1}{n}\sum_{k=1}^n |x_k|^2,||\Delta f||^2_{L^2}=\frac{1}{n}\sum_{k=1}^n |\Delta x_k|^2$$于是得到最终的不等式$$\sum_{k=1}^n |x_k|^2\leq \frac{1}{4\sin^2\left(\frac{\pi}{n}\right)}\sum_{k=1}^{n}|x_{k+1}-x_k|^2 $$


