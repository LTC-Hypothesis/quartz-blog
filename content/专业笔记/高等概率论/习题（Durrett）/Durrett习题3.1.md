<span style="color:#ef5350;">批改总评：91/100。仅计本笔记已作答的四题；满分依次为 20、25、35、20 分，得分依次为 18、24、30、19 分。按宽松标准评分：常见跳步不扣分，明显笔误仅提示；主要证明思路均已掌握，以下仅标出必要修正。</span>

> [!question] 3.1.1.
> Generalize the proof of Lemma 3.1.1 to conclude that if $\max_{1 \leq j \leq n} |c_{j,n}| \to 0$, $\sum_{j=1}^n c_{j,n} \to \lambda$, and $\sup_n \sum_{j=1}^n |c_{j,n}| < \infty$ then $\prod_{j=1}^n (1 + c_{j,n}) \to e^\lambda$.

> [!done] 
>
> <span style="color:#ef5350;">评分：18/20。对数化及最大项控制平方和的思路正确；下述两处估计各扣 1 分。</span>
>
>We W.T.S. $\sum_{j=1}^{n}\log{(1+c_{j,n})}\to\lambda$ as $n\to\infty$. Consider for any $\varepsilon>0$, there exists $N$ s.t. $n\ge N$, it holds 
>$$
>\left|\sum_{j=1}^{n}c_{j,n}-\lambda\right|\le\frac{\varepsilon}{2},\sum_{n\ge N}|c_{j,n}|\le\frac{\varepsilon}{2}
>$$
>Now we have 
>$$
>\begin{aligned}
>\left|\sum_{j=1}^{n}\log{(1+c_{j,n})}-\lambda\right|\le&\sum_{j=1}^{n}\left|\log{(1+c_{j,n})}-c_{j,n}\right|+\left|\sum_{j=1}^{n}c_{j,n}-\lambda\right|\\
>\le&\frac{1}{2}\sum_{j=1}^{n}c_{j,n}^2+\frac{\varepsilon}{2}\\
>\le&\frac{1}{2}\max_{1\le j\le n}|c_{j,n}|\left(\sum_{j=1}^{N}|c_{j,n}|+\sum_{j=N+1}^{n}|c_{j,n}|\right)+\frac{\varepsilon}{2}
>\end{aligned}
>$$
>Without loss of generality, for sufficiently large $n$, we have 
>$$
>\frac{1}{2}\max_{1\le j\le n}|c_{j,n}|\left(\sum_{j=1}^{N}|c_{j,n}|+\sum_{j=N+1}^{n}|c_{j,n}|\right)\le\frac{\varepsilon}{2}
>$$
>then for $\varepsilon>0$, $\exists N\in\mathbb{N}$, for $n\ge N$, we have 
>$$
>\left|\sum_{j=1}^{n}\log{(1+c_{j,n})}-\lambda\right|\le\varepsilon\text{ i.e. }\sum_{j=1}^{n}\log{(1+c_{j,n})}\to\lambda
>$$
>
> <span style="color:#ef5350;">批注：题设不能推出前述跨行尾和趋零，也无需拆分尾和。对负数，原余项界的系数 1/2 不成立；直接用绝对值和一致有界及下列估计即可完成原证明。</span>
> $\color{#ef5350}{M:=\sup_n\sum_{j=1}^{n}|c_{j,n}|<\infty,\qquad \delta_n:=\max_{1\le j\le n}|c_{j,n}|\to0.}$
> $\color{#ef5350}{|\log(1+c)-c|\le |c|^2\quad (|c|\le\tfrac12),\qquad \sum_{j=1}^{n}|\log(1+c_{j,n})-c_{j,n}|\le M\delta_n\to0.}$
>

> [!question] 3.1.2.
> The next three exercises illustrate the use of Stirling's formula. In them, $X_1, X_2, \dots$ are i.i.d. and $S_n = X_1 + \dots + X_n$.
> 
> If the $X_i$ have a Poisson distribution with mean 1, then $S_n$ has a Poisson distribution with mean $n$, i.e., $\mathbb{P}(S_n = k) = e^{-n}n^k/k!$ Use Stirling's formula to show that if $(k-n)/\sqrt{n} \to x$ then
> $$
> \sqrt{2\pi n}\mathbb{P}(S_n = k) \to \exp(-x^2/2)
> $$
> As in the case of coin flips it follows that
> $$
> \mathbb{P}(a \leq (S_n - n)/\sqrt{n} \leq b) \to \int_a^b (2\pi)^{-1/2}e^{-x^2/2} dx
> $$
> but proving the last conclusion is not part of the exercise.

> [!done]
>
> <span style="color:#ef5350;">评分：24/25。计算主线和最终极限正确；将 Stirling 近似写成精确等式扣 1 分。</span>
>
> Recall Stirling's fomula, 
> $$
> n!\sim\sqrt{2\pi n}\left(\frac{n}{e}\right)^n,\text{ a.s. }n\to\infty
> $$
> Note that in fact $k:=k_n$. We calculate 
> $$
> \begin{aligned}
>\sqrt{2\pi n}\mathbb{P}(S_n = k)&=\sqrt{2\pi n}\frac{n^k}{k!}e^{-n}\\
>&=\sqrt{\frac{n}{k}}\frac{n^k}{k^k}e^{k-n}\\
>&=\sqrt{\frac{n}{k}}\exp\left(k-n-k\log{\frac{k}{n}}\right)\\
>&=\sqrt{\frac{n}{k}}\exp n\left(\frac{k-n}{n}-\left(1+\frac{k-n}{n}\right)\log{\left(1+\frac{k-n}{n}\right)}\right)
>\end{aligned}
> $$
> We denote $\frac{k-n}{n}$ by $x_n$, since $\frac{k-n}{\sqrt{n}}\to x$
> $$
> x_n=\frac{k-n}{\sqrt{n}}\frac{1}{\sqrt{n}}\to0\text{ as }n\to\infty
> $$
> By Taylor's expression, 
> $$
> x_n-(1+x_n)\log{(1+x_n)}\sim-\frac{x_n^2}{2}\text{ a.s. }n\to\infty
> $$
> then we have 
> $$
> \sqrt{2\pi n}\mathbb{P}(S_n = k)\sim\exp\left(-\frac{(k-n)^2}{2n}\right)\to e^{-\frac{x^2}{2}}
> $$
>
> <span style="color:#ef5350;">批注：代入 Stirling 的第二行应改用渐近等号，或在右侧乘上误差因子；之后的代数改写可保留。这里的 a.s. 均改为 as，属于确定性极限，不另扣分。Taylor 余项可简写如下，也涵盖扰动为零的情形：</span>
> $\color{#ef5350}{1+o(1)}$ <span style="color:#ef5350;">（Stirling 误差因子）；</span> $\color{#ef5350}{n[x_n-(1+x_n)\log(1+x_n)]=-\frac{nx_n^2}{2}+O(n|x_n|^3),\quad n|x_n|^3\to0.}$
>

> [!question] 3.1.3.
> In the next two examples you should begin by considering $\mathbb{P}(S_n = k)$ when $k/n \to a$ and then relate $\mathbb{P}(S_n = j+1)$ to $\mathbb{P}(S_n = j)$ to show $\mathbb{P}(S_n \geq k) \leq C \mathbb{P}(S_n = k)$.
> 
> Suppose $\mathbb{P}(X_i = 1) = \mathbb{P}(X_i = -1) = 1/2$. Show that if $a \in (0, 1)$
> $$
> \frac{1}{2n} \log \mathbb{P}(S_{2n} \geq 2na) \to -\gamma(a)
> $$
> where $\gamma(a) = \frac{1}{2}\{(1+a)\log(1+a) + (1-a)\log(1-a)\}$.

> [!done] 
>
> <span style="color:#ef5350;">评分：30/35。二项转换、取整和夹逼思路正确；极限漏系数扣 3 分，比值上界与几何级数起点各扣 1 分。</span>
>
> Let $B_{2n}\triangleq\#\left\{1\le i\le 2n:X_i=1\right\}$. Then if $B_{2n}=m$, $S_n=m\cdot1+(2n-m)\cdot(-1)=2m-2n=2B_{2n}-2n$ and thus 
> $$
> \left\{S_n\ge2na\right\}=\left\{B_{2n}\ge n(a+1)\right\}
> $$
> Set $k_n=\lceil n(a+1)\rceil$ and we have $\frac{k_n}{2n}\to\frac{a+1}{2}$ as $n\to\infty$. Note that $B_{2n}\sim B(2n,\frac{1}{2})$, 
> $$
> \begin{aligned}
>\frac{1}{2n}\log\mathbb{P}(B_{2n}=k_n)&=\frac{1}{2n}\log\left(\begin{pmatrix}
>2n\\
>k_n
>\end{pmatrix}\frac{1}{2^{2n}}\right)\\
>&=\frac{1}{2n}\left(\log((2n)!)-\log(k_n)!-\log(2n-k_n)!)\right)-\log2
>\end{aligned}
> $$
> Now we use the log form of stirling formula $\log (n!)\sim n\log{n}-n$ as $n\to\infty$, 
> $$
> \begin{aligned}
>\frac{1}{2n}\log\mathbb{P}(B_{2n}=k_n)\sim&\frac{1}{2n}\left(2n\log(2n)-k_n\log(k_n)-(2n-k_n)\log(2n-k_n)\right)-\log2\\
>=&-x_n\log x_n-(1-x_n)\log(1-x_n)-\log2\qquad (x_n:=\frac{k_n}{2n})\\
>\to&-(1+a)\log(1+a)-(1-a)\log(1-a):=-\gamma(a)
>\end{aligned}
> $$ 
>
> <span style="color:#ef5350;">批注：最后一行漏了整体的 1/2，正确极限为：</span>
> $\color{#ef5350}{-\frac{1+a}{2}\log(1+a)-\frac{1-a}{2}\log(1-a)=-\gamma(a).}$
> <span style="color:#ef5350;">补充：对数 Stirling 用下列加法余项形式，可直接保证相减再除以样本量后的误差趋零；此处不另扣分。</span> $\color{#ef5350}{\log(m!)=m\log m-m+O(\log m).}$
>
> Next we derivate the relation between $\mathbb{P}(B_{2n}=j+1)$ and $\mathbb{P}(B_{2n}=j)$. For convenience, we denote $\mathbb{P}(B_{2n}=j)$ by $p_{n,j}$. Consider 
> $$
> \frac{p_{n,j+1}}{p_{n,j}}=\frac{2n-j}{j+1}\to\frac{1-a}{1+a}\text{ as }j\ge k_n,n\to\infty
> $$
>
> <span style="color:#ef5350;">批注：不能说尾部所有位置的比值都趋于同一极限，应使用边界处的一致上界：</span>
> $\color{#ef5350}{\frac{p_{n,j+1}}{p_{n,j}}\le\frac{2n-k_n}{k_n+1}\to\frac{1-a}{1+a}<1\qquad(k_n\le j<2n).}$
> <span style="color:#ef5350;">因此可固定取</span> $\color{#ef5350}{\frac{1-a}{1+a}<\rho<1}$ <span style="color:#ef5350;">，则充分大的样本量下，整个尾部均有后文的不等式。</span>
>
> Note that $\frac{1-a}{1+a}<1$, there exists constant $\rho<1$ s.t. 
> $$
> p_{n,j+1}\le\rho p_{n,j}
> $$
> Then 
> $$
> \begin{aligned}
>\frac{1}{2n}\log\mathbb{P}(S_n\ge 2na)=&\frac{1}{2n}\log\sum_{\ell=0}^{2n-k_n}p_{2n,k_n+\ell}\\
>\le&\frac{1}{2n}\log\sum_{n=1}^{\infty}\rho^n\cdot p_{2n,k_n}\\
>\le&\frac{1}{2n}\log\frac{1}{1-\rho}+\frac{1}{2n}\log p_{2n,k_n}
>\end{aligned}
> $$
>
> <span style="color:#ef5350;">批注：几何级数须从 0 开始，包含边界项；求和指标也不要与样本量混用。按前文定义，本题解答中的记号统一为</span> $\color{#ef5350}{S_{2n}\ \text{及}\ p_{n,j}}$ <span style="color:#ef5350;">，下标笔误不另扣分。正确尾和估计是：</span>
> $\color{#ef5350}{\sum_{\ell=0}^{2n-k_n}p_{n,k_n+\ell}\le p_{n,k_n}\sum_{\ell=0}^{\infty}\rho^\ell=\frac{p_{n,k_n}}{1-\rho}.}$
>
> Now we obtain
> $$
> \frac{1}{2n}\log p_{2n,k_n}\le\frac{1}{2n}\log \mathbb{P}(S_n\ge 2na)\le\frac{1}{2n}\log\frac{1}{1-\rho}+\frac{1}{2n}\log p_{2n,k_n}
> $$
> Let $n\to\infty$, we obtain $\frac{1}{2n}\log\mathbb{P}(S_n\ge 2na)\to-\gamma(a)$. 

> [!question] 3.1.4.
> Suppose $\mathbb{P}(X_i = k) = e^{-1}/k!$ for $k = 0, 1, \dots$. Show that if $a > 1$
> $$
> \frac{1}{n} \log \mathbb{P}(S_n \geq na) \to a - 1 - a\log a
> $$

> [!done]
>
> <span style="color:#ef5350;">评分：19/20。单点指数和尾概率夹逼正确；比值上界的极限算错扣 1 分，阶乘号遗漏按笔误处理。</span>
>
> Note that $S_n\sim P(n)$. Consider 
> $$
> \frac{\mathbb{P}(S_n=j+1)}{\mathbb{P}(S_n=j)}=\frac{n}{j+1}\to\frac{1}{a+1}<1
> $$
>
> <span style="color:#ef5350;">批注：先取下文的整数阈值，再统一控制尾部。边界上界的极限是下式，而非原文所写：</span>
> $\color{#ef5350}{k_n=\lceil na\rceil,\qquad \frac{n}{j+1}\le\frac{n}{k_n+1}\to\frac1a<1\quad(j\ge k_n).}$
> <span style="color:#ef5350;">固定取</span> $\color{#ef5350}{1/a<\rho<1}$ <span style="color:#ef5350;">，则充分大的样本量下可使用后面的几何级数估计。</span>
>
> There exists constant $\rho<1$ s.t. $\mathbb{P}(S_n=j+1)\le\rho\mathbb{P}(S_n=j)$. Set $k_n:=\lceil na\rceil$ and thus $\frac{k_n}{n}\to a$ as $n\to\infty$. We compute firstly 
> $$
> \begin{aligned}
>\frac{1}{n}\log\mathbb{P}(S_n=k_n)=&\frac{1}{n}\log\frac{n^{k_n}}{k_n!}e^{-n}\\
>\sim&-1-\frac{k_n}{n}\log\frac{k_n}{n}+\frac{k_n}{n}\\
>\to&a-1-a\log a
>\end{aligned}
> $$
>
> <span style="color:#ef5350;">批注：首行概率分母漏了阶乘号，且对数应覆盖整个概率；后面的 Stirling 计算与正确公式一致，不另扣分。</span>
> $\color{#ef5350}{\frac1n\log\mathbb P(S_n=k_n)=\frac1n\log\left(e^{-n}\frac{n^{k_n}}{k_n!}\right).}$
>
> and next 
> $$
> \begin{aligned}
>\frac{1}{n}\log\mathbb{P}(S_n\ge na)=&\frac{1}{n}\log\sum_{j=k_n}^{\infty}\mathbb{P}(S_n=j)\\
>\le&\frac{1}{n}\log{\frac{1}{1-\rho}}+\frac{1}{n}\log\mathbb{P}(S_n=k_n)
>\end{aligned}
> $$
> Now we have 
> $$
> \frac{1}{n}\log\mathbb{P}(S_n=k_n)\le\frac{1}{n}\log\mathbb{P}(S_n\ge na)\le\frac{1}{n}\log{\frac{1}{1-\rho}}+\frac{1}{n}\log\mathbb{P}(S_n=k_n)
> $$
> Let $n\to\infty$, we obtain 
> $$
> \frac{1}{n}\log\mathbb{P}(S_n\ge na)\to a-1-a\log{a},n\to\infty
> $$