>[!note] 强大数定律
>令 $S_n=\sum_{k=1}^nX_k$。强大数定律（Strong Law of Large Numbers，SLLN）的典型结论为
>$$
>\frac{S_n}{n}\xrightarrow{a.s.}\mu,
>\qquad\text{i.e.}\qquad
>\mathbb{P}\left(\lim_{n\to\infty}\frac{S_n}{n}=\mu\right)=1.
>$$
>与[[弱大数定律（WLLN）]]相比，这里要求在同一个概率为 $1$ 的集合上，样本平均沿整条序列收敛。

>[!note] 如何证明 $a.s.$ 收敛
>以 $S_n/n\to0$ 为例，我们需要将[[测度论基础#^a5f606|收敛语言转换成集合交并]]
>$$
>\left\{\lim_{n\to\infty}\frac{S_n}{n}=0\right\}
>=\bigcap_{k=1}^\infty\bigcup_{N=1}^\infty
>\bigcap_{n=N}^\infty
>\left\{\left|\frac{S_n}{n}\right|\le\frac1k\right\}.
>$$
>因此，只要对每个 $k\ge1$ 有
>$$
>\mathbb{P}\left(\left|\frac{S_n}{n}\right|>\frac1k,\text{ i.o.}\right)=0,
>$$
>对这些零测集取可数并，就得到 $S_n/n\xrightarrow{a.s.}0$。
>
>常用的充分条件是：对任意 $\varepsilon>0$，
>$$
>\sum_{n=1}^\infty
>\mathbb{P}\left(\left|\frac{S_n}{n}\right|>\varepsilon\right)<\infty.
>$$
>此时直接应用[[积分与期望#^5c2707|Borel-Cantelli 第一引理]]。只需对 $\varepsilon=1/k$ 使用引理，再取可数个概率为 $1$ 的集合的交；不需要处理不可数个 $\varepsilon$ 对应的集合之交。

^as-summability

>[!thm] 四阶矩条件下的 SLLN
>设 $X_1,X_2,\cdots$ 为 i.i.d. 随机变量，满足
>$$
>\mathbb{E}X_1=0,\qquad \mathbb{E}X_1^4<\infty.
>$$
>令 $S_n=\sum_{k=1}^nX_k$，则
>$$
>\frac{S_n}{n}\xrightarrow{a.s.}0.
>$$

^slln-fourth-moment

**Proof**

由 Markov 不等式，对任意 $\varepsilon>0$，
$$
\mathbb{P}\left(\left|\frac{S_n}{n}\right|>\varepsilon\right)
=\mathbb{P}(|S_n|^4>n^4\varepsilon^4)
\le\frac{\mathbb{E}S_n^4}{n^4\varepsilon^4}.
$$
因此关键是估计 $\mathbb{E}S_n^4$。

展开四次方，
$$
\mathbb{E}S_n^4
=\sum_{1\le i,j,k,l\le n}\mathbb{E}(X_iX_jX_kX_l).
$$
若某个指标恰好出现一次，则由独立性，可把对应的 $\mathbb{E}X_i=0$ 提出来，所以该项为 $0$。例如当 $i,j,k$ 不同时，
$$
\mathbb{E}(X_i^3X_j)=\mathbb{E}X_i^3\mathbb{E}X_j=0,\qquad
\mathbb{E}(X_i^2X_jX_k)
=\mathbb{E}X_i^2\mathbb{E}X_j\mathbb{E}X_k=0.
$$
因此仅剩两类项：

- 四个指标相同，共 $n$ 项，每项为 $\mathbb{E}X_1^4$；
- 两个不同指标各出现两次。先选指标对 $i<j$，再排列两个 $i$ 和两个 $j$，共有 $6\binom n2=3n(n-1)$ 项，每项为 $(\mathbb{E}X_1^2)^2$。

所以
$$
\begin{aligned}
\mathbb{E}S_n^4
&=n\mathbb{E}X_1^4+6\sum_{1\le i<j\le n}\mathbb{E}(X_i^2X_j^2)\\
&=n\mathbb{E}X_1^4+3n(n-1)(\mathbb{E}X_1^2)^2\\
&\le Cn^2,
\end{aligned}
$$
其中可取 $C=\mathbb{E}X_1^4+3(\mathbb{E}X_1^2)^2<\infty$。于是
$$
\sum_{n=1}^\infty
\mathbb{P}\left(\left|\frac{S_n}{n}\right|>\varepsilon\right)
\le\frac C{\varepsilon^4}\sum_{n=1}^\infty\frac1{n^2}<\infty.
$$
由[[积分与期望#^5c2707|Borel-Cantelli 第一引理]]及[[#^as-summability|上面的可数化论证]]，
$$
\frac{S_n}{n}\xrightarrow{a.s.}0.
$$

**QED**

>[!warning]
>这里消去四次展开中的混合项，需要用到独立性，不能只由“两两不相关”推出。
>
>若 $\mathbb{E}X_1=\mu$，则对 $X_i-\mu$ 应用定理，得到 $S_n/n\xrightarrow{a.s.}\mu$。同分布也可以放宽为：$X_i$ 独立、$\mathbb{E}X_i=0$，且 $\sup_i\mathbb{E}X_i^4<\infty$。
>
>只用二阶矩作逐项 Chebyshev 估计，通常得到 $O(1/n)$ 的上界，其和发散。这表示该估计不能直接用于第一引理，并不表示 SLLN 不成立。

回故[[积分与期望#^5c2707|Borel-Cantelli第一引理（1st Borel-Cantelli）]]。

>[!lemma] 2nd Borel-Cantelli
>设 $A_1,A_2,\cdots$ 相互独立，且
>$$
>\sum_{n=1}^\infty\mathbb{P}(A_n)=\infty,
>$$
>则
>$$
>\mathbb{P}(A_n,\text{ i.o.})
>=\mathbb{P}\left(\bigcap_{M=1}^\infty\bigcup_{n=M}^\infty A_n\right)=1.
>$$

^bc-second

**Proof**

固定 $M$，对任意 $N\ge M$，由独立性以及 $1-x\le e^{-x}$，
$$
\begin{aligned}
\mathbb{P}\left(\bigcap_{n=M}^NA_n^c\right)
&=\prod_{n=M}^N\mathbb{P}(A_n^c)\\
&=\prod_{n=M}^N(1-\mathbb{P}(A_n))\\
&\le\exp\left(-\sum_{n=M}^N\mathbb{P}(A_n)\right)\to0
\quad\text{as }N\to\infty.
\end{aligned}
$$
这里删去前 $M-1$ 项后，概率级数仍然发散。由概率测度的从上连续性，
$$
\mathbb{P}\left(\bigcap_{n=M}^\infty A_n^c\right)=0,
$$
即对每个 $M$，
$$
\mathbb{P}\left(\bigcup_{n=M}^\infty A_n\right)=1.
$$
再令 $M\to\infty$。由于 $\bigcup_{n=M}^\infty A_n\downarrow\limsup_nA_n$，得到
$$
\mathbb{P}(\limsup_nA_n)=1.
$$

**QED**

>[!warning] 
>仅有 $\sum_n\mathbb{P}(A_n)=\infty$ 不足以推出结论。例如所有 $A_n=A$，其中 $0<\mathbb{P}(A)<1$，则 $\limsup_nA_n=A$，概率并不为 $1$。

>[!thm] 0-1律
>对于相互独立的事件 $\{A_n\}$，则成立
>$$
>\sum_{n=1}^{\infty}\mathbb{P}(A_n)\begin{cases}
><\infty\\
>=\infty
>\end{cases}\Longrightarrow\mathbb{P}(A_n,\text{i.o.})\begin{cases}
>=0\\
>=1
>\end{cases}
>$$

>[!thm] 一阶绝对矩无限时，样本平均不存在有限极限
>设 $X_1,X_2,\cdots$ 为 i.i.d. 随机变量，$\mathbb{E}|X_1|=\infty$，令 $S_n=\sum_{k=1}^nX_k$。则
>$$
>\mathbb{P}(|X_n|>n,\text{ i.o.})=1,
>$$
>并且
>$$
>\mathbb{P}\left(\lim_{n\to\infty}\frac{S_n}{n}
>\text{ exists in }\mathbb{R}\right)=0.
>$$

^slln-infinite-moment

**Proof**

由[[Fubini定理及其应用#^f5a22d|尾积分公式]]，以及尾概率关于 $t$ 的单调性，
$$
\begin{aligned}
\mathbb{E}|X_1|
&=\int_0^\infty\mathbb{P}(|X_1|>t)\,dt\\
&=\sum_{n=0}^\infty\int_n^{n+1}\mathbb{P}(|X_1|>t)\,dt\\
&\le\sum_{n=0}^\infty\mathbb{P}(|X_1|>n).
\end{aligned}
$$
左端为 $\infty$，而 $n=0$ 的一项至多为 $1$，故
$$
\sum_{n=1}^\infty\mathbb{P}(|X_n|>n)
=\sum_{n=1}^\infty\mathbb{P}(|X_1|>n)=\infty.
$$
事件 $\{|X_n|>n\}$ 相互独立，由[[#^bc-second|第二引理]]，
$$
\mathbb{P}(A)=1,\qquad
A=\{|X_n|>n,\text{ i.o.}\}.
$$

再令
$$
C=\left\{\lim_{n\to\infty}\frac{S_n}{n}\text{ exists in }\mathbb{R}\right\}.
$$
注意恒等式
$$
\frac{S_n}{n}-\frac{S_{n+1}}{n+1}
=\frac{S_n}{n(n+1)}-\frac{X_{n+1}}{n+1}.
$$
在 $C$ 上，$S_n/n$ 收敛到某个有限值，因而
$$
\frac{S_n}{n(n+1)}=\frac1{n+1}\frac{S_n}{n}\to0,
\qquad
\frac{S_n}{n}-\frac{S_{n+1}}{n+1}\to0.
$$
但是，在 $A$ 上有无穷多个 $n$ 满足 $|X_{n+1}|/(n+1)>1$。若 $\omega\in C\cap A$，则对其中充分大的 $n$，
$$
\left|\frac{S_n(\omega)}{n}-\frac{S_{n+1}(\omega)}{n+1}\right|
\ge\frac{|X_{n+1}(\omega)|}{n+1}-\left|\frac{S_n(\omega)}{n(n+1)}\right|
>\frac23,
$$
与相邻两项之差趋于 $0$ 矛盾。故 $C\cap A=\varnothing$，于是
$$
\mathbb{P}(C)\le\mathbb{P}(A^c)=0.
$$

**QED**

>[!example] Rényi 破纪录问题的 SLLN
>回忆[[独立性#^renyi-record|Rényi 破纪录问题]]设 $X_1,X_2,\cdots$ 为 i.i.d. 随机变量，共同分布函数连续，令
>$$
>A_k=\{X_k>\max_{1\le j<k}X_j\},\quad k\ge2,\qquad A_1=\Omega.
>$$
>沿用手稿，记前 $n$ 次观测的纪录总数为
>$$
>R_n=\sum_{k=1}^n\mathbb{1}_{A_k}.
>$$
>则
>$$
>\frac{R_n}{\log n}\xrightarrow{a.s.}1.
>$$

^slln-record

**Proof**

本次手稿中的 $W_n$ 就是上文的 $R_n$。由[[独立性#^renyi-record|已经证明的 Rényi 结论]]，只需使用 $A_m$ 相互独立及 $\mathbb{P}(A_m)=1/m$，下面直接证明所需的大数律估计。

>[!thm] 计数型 SLLN
>设 $A_1,A_2,\cdots$ 两两独立，且
>$$
>\sum_{m=1}^{\infty}\mathbb{P}(A_m)=\infty.
>$$
>则
>$$
>\frac{\sum_{m=1}^{n}\mathbb{1}_{A_m}}
>{\sum_{m=1}^{n}\mathbb{P}(A_m)}
>\xrightarrow{a.s.}1.
>$$

^counting-slln

令 $X_i=\mathbb{1}_{A_i},S_n=\sum_{i=1}^{n}X_i$。由两两独立，
$$
\operatorname{Var}(S_n)=\sum_{i=1}^{n}\operatorname{Var}(X_i)
\le\sum_{i=1}^{n}\mathbb{E}X_i^2
=\sum_{i=1}^{n}\mathbb{P}(A_i)=\mathbb{E}S_n.
$$
于是对 $\delta>0$，由Chebyshev不等式，
$$
\mathbb{P}\bigl(|S_n-\mathbb{E}S_n|>\delta\mathbb{E}S_n\bigr)\le\frac{\operatorname{Var}(S_n)}
{\delta^2(\mathbb{E}S_n)^2}\le\frac1{\delta^2\mathbb{E}S_n}\to0.\tag{1}
$$
这里 $\mathbb{E}S_n\to\infty$，故分母从某一项起为正。这首先给出 $S_n/\mathbb{E}S_n\xrightarrow{\mathbb{P}}1$。

现在证明几乎必然收敛。取
$$
n_k=\inf\{n:\mathbb{E}S_n\ge k^2\},\qquad T_k=S_{n_k}.
$$
由于 $\mathbb{E}S_n-\mathbb{E}S_{n-1}=\mathbb{P}(A_n)\le1$，
$$
k^2\le\mathbb{E}T_k\le k^2+1.
$$
在 $(1)$ 中取 $n=n_k$，则
$$
\sum_{k=1}^{\infty}\mathbb{P}\bigl(|T_k-\mathbb{E}T_k|>\delta\mathbb{E}T_k\bigr)\le\frac1{\delta^2}\sum_{k=1}^{\infty}\frac1{k^2}<\infty.
$$
由[[积分与期望#^5c2707|Borel-Cantelli 第一引理]]，对 $\delta=1/r,r\ge1$ 取可数交，得到
$$
\frac{T_k}{\mathbb{E}T_k}\xrightarrow{a.s.}1.
$$

再由单调性控制中间项。固定一条满足上述收敛的样本路径，若 $n_k\le n<n_{k+1}$，则
$$
\begin{aligned}
\frac{T_k}{\mathbb{E}T_k}
\frac{\mathbb{E}T_k}{\mathbb{E}T_{k+1}}=\frac{T_k}{\mathbb{E}T_{k+1}}\le\frac{S_n}{\mathbb{E}S_n}\le\frac{T_{k+1}}{\mathbb{E}T_k}=\frac{T_{k+1}}{\mathbb{E}T_{k+1}}\frac{\mathbb{E}T_{k+1}}{\mathbb{E}T_k}.
\end{aligned}
$$
又
$$
1\le\frac{\mathbb{E}T_{k+1}}{\mathbb{E}T_k}
\le\frac{(k+1)^2+1}{k^2}\to1.
$$
两端都趋于 $1$，所以 $S_n/\mathbb{E}S_n\xrightarrow{a.s.}1$。

回到破纪录计数 $R_n$，由 $\sum_{m=1}^{n}1/m\sim\log n$，
$$
\frac{R_n}{\log n}=\frac{R_n}{\sum_{m=1}^{n}1/m}
\cdot\frac{\sum_{m=1}^{n}1/m}{\log n}
\xrightarrow{a.s.}1.
$$

**QED**

>[!warning] 子列加单调夹逼(经典方法，严肃学习)
>这里 $S_n$ 与 $\mathbb{E}S_n$ 分别单调递增，但 $S_n/\mathbb{E}S_n$ 一般不单调，不能直接由其依概率收敛推出 a.s. 收敛。
>
>先选出使误差概率可求和的子列，再利用分子、分母的单调性及相邻归一化常数之比趋于 $1$，就能把子列收敛推广到整列。这也是后面几何子列证明的出发点。
>
>计数型强律只要求两两独立；它还给出 $\sum_n\mathbb{1}_{A_n}=\infty$ a.s.，从而把[[#^bc-second|第二 Borel-Cantelli 引理]]推广到了两两独立情形。

下面证明强大数定律，分别为Etemadi和Kolmogorov的证明。

>[!thm] Kolmogorov 强大数定律
>设 $X_1,X_2,\cdots$ 为 i.i.d. 随机变量，$S_n=\sum_{k=1}^{n}X_k$。则 $S_n/n$ 几乎必然收敛到有限极限的充要条件是
>$$
>\mathbb{E}|X_1|<\infty.
>$$
>条件成立时，记 $\mu=\mathbb{E}X_1$，有
>$$
>\frac{S_n}{n}\xrightarrow{a.s.}\mu.
>$$

^slln-integrable

**Proof**

必要性已由[[#^slln-infinite-moment|一阶绝对矩无限时的结论]]给出。先证明充分性，取手稿中的截断
$$
Y_k=X_k\mathbb{1}_{\{|X_k|\le k\}},\qquad
T_n=\sum_{k=1}^{n}Y_k.
$$
注意每个 $Y_k$ 按自己的指标 $k$ 截断，与[[弱大数定律（WLLN）#^wlln-truncation|弱大数律中一整行使用同一个阈值]]不同。我们断言

>[!lemma] 截断不改变样本平均的极限
>在 $\mathbb{E}|X_1|<\infty$ 下，
>$$
>\frac{S_n-T_n}{n}\xrightarrow{a.s.}0.
>$$
>因此只需证明 $T_n/n\xrightarrow{a.s.}\mu$。

^slln-truncation

由[[Fubini定理及其应用#^f5a22d|尾积分公式]]及尾概率的单调性，
$$
\begin{aligned}
\sum_{k=1}^{\infty}\mathbb{P}(X_k\ne Y_k)
&=\sum_{k=1}^{\infty}\mathbb{P}(|X_1|>k)\\
&\le\sum_{k=1}^{\infty}
\int_{k-1}^{k}\mathbb{P}(|X_1|>t)\,dt\\
&=\mathbb{E}|X_1|<\infty.
\end{aligned}
$$
By [[积分与期望#^5c2707|1st Borel-Cantelli]]，
$$
\mathbb{P}(X_k\ne Y_k,\text{ i.o.})=0.
$$
即在一个概率为 $1$ 的集合上，对每个 $\omega$ 存在 $N=N(\omega)$，使得 $k\ge N$ 时 $X_k(\omega)=Y_k(\omega)$。于是对所有 $n$，
$$
|S_n(\omega)-T_n(\omega)|\le\sum_{k=1}^{N(\omega)-1}|X_k(\omega)-Y_k(\omega)|<\infty.
$$
除以 $n$ 即得结论。这里最终相等的是 $X_k$ 与 $Y_k$；$S_n-T_n$ 最终为一个有限的随机常数，不必为 $0$。

下面的方差估计是两种证明都会用到的。

>[!lemma] 截断后的方差估计
>$$
>\sum_{k=1}^{\infty}\frac{\operatorname{Var}(Y_k)}{k^2}
>\le\sum_{k=1}^{\infty}\frac{\mathbb{E}Y_k^2}{k^2}
>\le4\mathbb{E}|X_1|<\infty.
>$$

^slln-truncated-variance

由尾积分公式，
$$
\operatorname{Var}(Y_k)\le\mathbb{E}Y_k^2
=\int_0^{\infty}2y\mathbb{P}(|Y_k|>y)\,dy
\le\int_0^k2y\mathbb{P}(|X_1|>y)\,dy.
$$
被积函数非负，by [[Fubini定理及其应用|Fubini 定理]] 可交换求和与积分，
$$
\begin{aligned}
\sum_{k=1}^{\infty}\frac{\mathbb{E}Y_k^2}{k^2}
&\le\sum_{k=1}^{\infty}\frac1{k^2}
\int_0^{\infty}2y\mathbb{1}_{\{y<k\}}
\mathbb{P}(|X_1|>y)\,dy\\
&=\int_0^{\infty}
\left(2y\sum_{k>y}\frac1{k^2}\right)
\mathbb{P}(|X_1|>y)\,dy.
\end{aligned}
$$
只需要证明
$$
2y\sum_{k>y}\frac1{k^2}\le4,\qquad y\ge0.
$$
当 $0\le y<1$ 时，
$$
2y\sum_{k>y}\frac1{k^2}
\le2\left(1+\int_1^{\infty}\frac{dx}{x^2}\right)=4.
$$
当 $y\ge1$ 时，令 $m=\lfloor y\rfloor\ge1$，则
$$
\sum_{k>y}\frac1{k^2}
=\sum_{k=m+1}^{\infty}\frac1{k^2}
\le\int_m^{\infty}\frac{dx}{x^2}=\frac1m,
\qquad \frac ym<2.
$$
所以该上界仍成立，进而
$$
\sum_{k=1}^{\infty}\frac{\mathbb{E}Y_k^2}{k^2}
\le4\int_0^{\infty}\mathbb{P}(|X_1|>y)\,dy
=4\mathbb{E}|X_1|.
$$

现在回到证明 $T_n/n\xrightarrow{a.s.}\mu$。

**第一种证明：几何子列与单调性（Etemadi's argument）**

先设 $X_n\ge0$，从而 $Y_n\ge0,T_n$ 单调递增。取 $\alpha>1$，沿用手稿记号
$$
k(n)=\lfloor\alpha^n\rfloor,\qquad W_n=T_{k(n)}.
$$
这里 $W_n$ 仅表示这条子列，与前面破纪录计数中的同名记号无关。序列 $k(n)$ 最终严格递增，有限个重复指标不影响极限。

对 $\delta>0$，由 Chebyshev 不等式及 $Y_m$ 之间的独立性，
$$
\begin{aligned}
&\sum_{n=1}^{\infty}
\mathbb{P}\bigl(|W_n-\mathbb{E}W_n|>\delta k(n)\bigr)\\
&\quad\le\frac1{\delta^2}
\sum_{n=1}^{\infty}\frac{\operatorname{Var}(T_{k(n)})}{k(n)^2}\\
&\quad=\frac1{\delta^2}\sum_{n=1}^{\infty}
\frac1{k(n)^2}\sum_{m=1}^{k(n)}\operatorname{Var}(Y_m)\\
&\quad=\frac1{\delta^2}\sum_{m=1}^{\infty}
\operatorname{Var}(Y_m)\sum_{\{n:k(n)\ge m\}}\frac1{k(n)^2}.
\end{aligned}
$$
最后一步仍是对非负项换序。

由于 $\lfloor\alpha^n\rfloor\ge\alpha^n/2$，并且 $k(n)\ge m$ 蕴含 $\alpha^n\ge m$，
$$
\sum_{\{n:k(n)\ge m\}}\frac1{k(n)^2}
\le4\sum_{\{n:\alpha^n\ge m\}}\alpha^{-2n}
\le\frac4{1-\alpha^{-2}}\frac1{m^2}.
$$
因此由[[#^slln-truncated-variance|截断方差估计]]，
$$
\begin{aligned}
&\sum_{n=1}^{\infty}
\mathbb{P}\bigl(|W_n-\mathbb{E}W_n|>\delta k(n)\bigr)\\
&\quad\le
\frac4{\delta^2(1-\alpha^{-2})}
\sum_{m=1}^{\infty}\frac{\operatorname{Var}(Y_m)}{m^2}
<\infty.
\end{aligned}
$$
由Borel-Cantelli引理，
$$
\frac{T_{k(n)}-\mathbb{E}T_{k(n)}}{k(n)}
\xrightarrow{a.s.}0.
$$
另一方面，由同分布及[[积分与期望#^9122df|DCT]]，
$$
\mathbb{E}Y_k
=\mathbb{E}\bigl[X_1\mathbb{1}_{\{X_1\le k\}}\bigr]
\to\mathbb{E}X_1=\mu.
$$
由Stolz公式，
$$
\frac{\mathbb{E}T_n}{n}
=\frac1n\sum_{k=1}^{n}\mathbb{E}Y_k\to\mu.
$$
故 $T_{k(n)}/k(n)\xrightarrow{a.s.}\mu$。

对于 $k(n)\le m<k(n+1)$，由 $T_m$ 单调递增，
$$
\frac{T_{k(n)}}{k(n)}
\frac{k(n)}{k(n+1)}
\le\frac{T_m}{m}
\le
\frac{T_{k(n+1)}}{k(n+1)}
\frac{k(n+1)}{k(n)}.
$$
又 $k(n+1)/k(n)\to\alpha$，所以 a.s.
$$
\frac{\mu}{\alpha}
\le\liminf_{m\to\infty}\frac{T_m}{m}
\le\limsup_{m\to\infty}\frac{T_m}{m}
\le\alpha\mu.
$$
为使这些估计在同一个概率为 $1$ 的集合上成立，取 $\alpha_j=1+1/j,j\ge1$，对相应集合取可数交，再令 $j\to\infty$。于是
$$
\frac{T_n}{n}\xrightarrow{a.s.}\mu.
$$
由[[#^slln-truncation|截断引理]]，$S_n/n\xrightarrow{a.s.}\mu$。

对一般 $X_n$，写成 $X_n=X_n^+-X_n^-$。两族分别满足上述非负情形，且
$$
\mathbb{E}X_1^++\mathbb{E}X_1^-=\mathbb{E}|X_1|<\infty.
$$
所以
$$
\frac{S_n}{n}
=\frac1n\sum_{k=1}^{n}X_k^+
-\frac1n\sum_{k=1}^{n}X_k^-
\xrightarrow{a.s.}
\mathbb{E}X_1^+-\mathbb{E}X_1^-=\mu.
$$
充分性得证。

必要性也可按手稿最后的恒等式来理解。若 $S_n/n$ 收敛到有限值，则
$$
\frac{X_n}{n}
=\frac{S_n}{n}
-\frac{n-1}{n}\frac{S_{n-1}}{n-1}\to0.
$$
如果 $\mathbb{E}|X_1|=\infty$，则由
$$
\sum_{n=1}^{\infty}\mathbb{P}(|X_1|>n)
\le\mathbb{E}|X_1|
\le1+\sum_{n=1}^{\infty}\mathbb{P}(|X_1|>n)
$$
可知尾概率级数发散。[[#^bc-second|第二 Borel-Cantelli 引理]]给出 $|X_n|>n$ i.o. a.s.，与上式矛盾。

**QED**

>[!warning] 
>几何子列的作用是保证
>$$
>\sum_{\{n:k(n)\ge m\}}\frac1{k(n)^2}\le\frac{C_\alpha}{m^2},
>$$
>从而能使用截断方差估计；随后令 $\alpha\downarrow1$ 消除夹逼两端的误差。不能只取 $\alpha=2$，就直接把两端都写成 $\mu$。

>[!def] 尾 $\sigma$ 代数
>设 $X_1,X_2,\cdots$ 为实值随机变量，记
>$$
>\mathscr{F}_n=\sigma(X_1,\cdots,X_n),\qquad
>\mathscr{F}'_n=\sigma(X_n,X_{n+1},\cdots).
>$$
>称
>$$
>\mathscr{T}=\bigcap_{n=1}^{\infty}\mathscr{F}'_n
>$$
>为这列随机变量的尾 $\sigma$-代数，$A\in\mathscr{T}$ 称为尾事件。
>
>尾事件可以仅由任意远以后的变量判断。对于坐标序列，改变有限多个坐标不影响其是否发生；严格验证时，仍需说明事件属于每个 $\mathscr{F}'_n$。这个定义本身不要求独立性。

^tail-sigma

>[!example] 尾事件的例子
>令 $S_n=\sum_{k=1}^{n}X_k$。
>
>1. $\{\lim_{n\to\infty}S_n\text{ exists in }\mathbb{R}\}\in\mathscr{T}$。对任意固定的 $r$，有
>   $$
>   \left\{\sum_{k=1}^{\infty}X_k\text{ 收敛}\right\}
>   =
>   \left\{\sum_{k=r}^{\infty}X_k\text{ 收敛}\right\}.
>   $$
>   由 [[度量空间|Cauchy 判别准则]]，该事件可写成
>   $$
>   \bigcap_{j=1}^{\infty}\bigcup_{N=r}^{\infty}
>   \bigcap_{q>p\ge N}
>   \left\{\left|\sum_{k=p+1}^{q}X_k\right|\le\frac1j\right\}.
>   $$
>   这里交并均可数，且只涉及 $X_r,X_{r+1},\cdots$，所以它属于 $\mathscr{F}'_r$。
>
>2. 若 $c_n>0,c_n\to\infty$，则对任意 $x\in\mathbb{R}$，
>   $$
>   \left\{\limsup_{n\to\infty}\frac{S_n}{c_n}>x\right\}
>   \in\mathscr{T}.
>   $$
>   因为对固定 $r$，$S_{r-1}/c_n\to0$，故
>   $$
>   \limsup_{n\to\infty}\frac{S_n}{c_n}
>   =\limsup_{n\to\infty}
>   \frac{\sum_{k=r}^{n}X_k}{c_n}.
>   $$
>
>3. $\{\limsup_nS_n>0\}$ 一般不是尾事件。取 $X_1=\pm1$，概率各为 $1/2$，而 $X_n=0,n\ge2$。此时该事件为 $\{X_1=1\}$，但 $\mathscr{F}'_2=\{\varnothing,\Omega\}$，所以它不属于 $\mathscr{T}$。删去有限项不改变级数是否收敛，却可能改变其极限值的正负。

>[!thm] Kolmogorov's 0-1 law
>若 $X_1,X_2,\cdots$ 相互独立，$A\in\mathscr{T}$，则
>$$
>\mathbb{P}(A)=0\quad\text{or}\quad\mathbb{P}(A)=1.
>$$

^kolmogorov-zero-one

**Proof**

只需要证明 $\mathscr{T}$ 与自身独立，并令
$$
\mathscr{F}_\infty
=\sigma(X_1,X_2,\cdots)
=\sigma\left(\bigcup_{k=1}^{\infty}\mathscr{F}_k\right).
$$

**Step1: 证明$\mathscr{F}_k\perp\!\!\!\!\perp\mathscr{F}'_{k+1}$**

首先，由[[独立性#^sigma-independent|独立随机变量分组后生成的 $\sigma$-代数仍独立]]，对任意 $k,r\ge1$，
$$
\mathscr{F}_k\ \perp\!\!\!\!\perp\sigma(X_{k+1},\cdots,X_{k+r}).
$$
固定 $B\in\mathscr{F}_k$。令
$$
\mathscr{D}_B
=\{C\in\mathscr{F}'_{k+1}:
\mathbb{P}(B\cap C)=\mathbb{P}(B)\mathbb{P}(C)\}.
$$
这是一个 $\lambda$-类，并包含
$$
\bigcup_{r=1}^{\infty}\sigma\left(X_{k+1},\cdots,X_{k+r}\right).
$$
后者是递增的 $\sigma$-代数之并，因而是 $\pi$-系，且生成 $\mathscr{F}'_{k+1}$, i.e. 
$$
\mathscr{F}'_{k+1}=\sigma\left(\bigcup_{r=1}^{\infty}\sigma(X_{k+1},\cdots,X_{k+r})\right)
$$
由[[测度论基础#^2245d8|$\pi$-$\lambda$ 定理]]，$\mathscr{D}_B=\mathscr{F}'_{k+1}$，故
$$
\mathscr{F}_k\perp\!\!\!\!\perp\mathscr{F}'_{k+1}.
$$
**Step2: 证明 $\mathscr{T}\perp\!\!\!\!\perp\mathscr{F}_\infty$**

由于 $\mathscr{T}\subseteq\mathscr{F}'_{k+1}$，得到 $\mathscr{F}_k\perp\!\!\!\!\perp\mathscr{T}$，对每个 $k$ 都成立。

再固定 $A\in\mathscr{T}$，令
$$
\mathscr{D}_A
=\{B\in\mathscr{F}_\infty:
\mathbb{P}(A\cap B)=\mathbb{P}(A)\mathbb{P}(B)\}.
$$
同理，$\mathscr{D}_A$ 是 $\lambda$-系，并包含 $\pi$-系 $\bigcup_k\mathscr{F}_k$。再次应用 $\pi$-$\lambda$ 定理，
$$
\mathscr{D}_A=\mathscr{F}_\infty,
\qquad\text{即}\qquad
\mathscr{T}\perp\!\!\!\!\perp\mathscr{F}_\infty.
$$
又 $\mathscr{T}\subseteq\mathscr{F}_\infty$，所以 $A$ 与自身独立，
$$
\mathbb{P}(A)
=\mathbb{P}(A\cap A)
=\mathbb{P}(A)^2.
$$
故 $\mathbb{P}(A)\in\{0,1\}$。

**QED**

>[!thm] Kolmogorov 极大不等式
>设 $X_1,\cdots,X_n$ 相互独立，$\mathbb{E}X_k=0,\operatorname{Var}(X_k)<\infty$，$S_k=\sum_{j=1}^{k}X_j$。对任意 $x>0$，
>$$
>\mathbb{P}\left(\max_{1\le k\le n}|S_k|\ge x\right)
>\le\frac{\operatorname{Var}(S_n)}{x^2}
>=\frac1{x^2}\sum_{k=1}^{n}\operatorname{Var}(X_k).
>$$

^kolmogorov-maximal

**Proof**

按第一次越界的位置分解，这是非常标准的方法，需要严肃学习，令
$$
A_k=\{|S_k|\ge x,\ |S_j|<x,\ 1\le j<k\}.
$$
$A_k$ 两两不交，且
$$
\bigcup_{k=1}^{n}A_k
=\left\{\max_{1\le k\le n}|S_k|\ge x\right\}.
$$
因此
$$
\begin{aligned}
\mathbb{E}S_n^2
&\ge\sum_{k=1}^{n}\int_{A_k}S_n^2\,d\mathbb{P}\\
&=\sum_{k=1}^{n}\int_{A_k}
\bigl[S_k^2+2S_k(S_n-S_k)+(S_n-S_k)^2\bigr]\,d\mathbb{P}\\
&\ge\sum_{k=1}^{n}\int_{A_k}S_k^2\,d\mathbb{P}
+2\sum_{k=1}^{n}\mathbb{E}
\bigl[S_k\mathbb{1}_{A_k}(S_n-S_k)\bigr].
\end{aligned}
$$
其中 $S_k\mathbb{1}_{A_k}$ 是 $\mathscr{F}_k$-可测的，而 $S_n-S_k$ 只依赖 $X_{k+1},\cdots,X_n$。由独立性及 $\mathbb{E}(S_n-S_k)=0$，
$$
\mathbb{E}\bigl[S_k\mathbb{1}_{A_k}(S_n-S_k)\bigr]
=\mathbb{E}[S_k\mathbb{1}_{A_k}]
\mathbb{E}(S_n-S_k)=0.
$$
又在 $A_k$ 上 $S_k^2\ge x^2$，故
$$
\mathbb{E}S_n^2
\ge x^2\sum_{k=1}^{n}\mathbb{P}(A_k)
=x^2\mathbb{P}\left(\max_{1\le k\le n}|S_k|\ge x\right).
$$
由 $\mathbb{E}S_n=0$，即得结论。

**QED**

>[!note] 与停时、鞅最大不等式的联系
>$A_k=\{\tau=k\}$，其中 $\tau=\inf\{k:|S_k|\ge x\}$，这正是[[Stopping Times|首次到达时间与停时]]的想法。
>
>在自然信息流 $\mathscr{F}_k$ 下，$S_k$ 是平方可积鞅，$S_k^2$ 是非负次鞅。对 $S_k^2$ 使用[[Continuous-Time Martingales#^bd276e|次鞅第一最大不等式]]的离散时间版本，同样得到上述估计。
>
>Chebyshev 只控制最后一项 $|S_n|$；这里用相同的上界控制整个有限序列的最大值。若方差为无穷，上界变成无穷便没有估计作用，不能直接删去条件并保留原来的有限上界。

>[!def] 中位数
>实数 $m(X)$ 是随机变量 $X$ 的一个中位数，若
>$$
>\mathbb{P}(X\le m(X))\ge\frac12,\qquad
>\mathbb{P}(X\ge m(X))\ge\frac12.
>$$
>中位数可以不唯一，这里任选一个。定义不要求矩存在；若分布有原子，两边不必都等于 $1/2$。
>
>当 $\mathbb{E}|X|<\infty$ 时，中位数也可由
>$$
>\operatorname*{arg\,min}_{a\in\mathbb{R}}\mathbb{E}|X-a|
>$$
>刻画：此集合恰好是所有中位数组成的集合。

^median

>[!thm] Lévy 极大不等式（中位数形式）
>设 $X_1,\cdots,X_n$ 相互独立，$S_k=\sum_{j=1}^{k}X_j$。记
>$$
>b_k=m(S_k-S_n),\qquad 1\le k\le n.
>$$
>则对任意 $x>0$，
>$$
>\mathbb{P}\left(\max_{1\le k\le n}|S_k-b_k|\ge x\right)
>\le2\mathbb{P}(|S_n|\ge x).
>$$
>这里不要求均值为 $0$，也不要求一阶矩或二阶矩存在。

^levy-median

**Proof**

令
$$
H_k=\{|S_k-b_k|\ge x,\ |S_j-b_j|<x,\ 1\le j<k\}.
$$
这些事件两两不交，且 $H_k\in\mathscr{F}_k$。注意 $b_j$ 是由分布决定的常数，因此即使 $j<k$，$H_k$ 也不涉及 $k$ 之后随机变量的取值。

将越界方向分为两种：
$$
H_k^+=H_k\cap\{S_k-b_k\ge x\},\qquad
H_k^-=H_k\cap\{S_k-b_k\le-x\}.
$$
由于 $x>0$，$H_k=H_k^+\cup H_k^-$。又 $S_k-S_n$ 与 $\mathscr{F}_k$ 独立，且 $b_k$ 是其中位数，
$$
\begin{aligned}
\mathbb{P}\bigl(H_k^+\cap\{S_k-S_n\le b_k\}\bigr)
&\ge\frac12\mathbb{P}(H_k^+),\\
\mathbb{P}\bigl(H_k^-\cap\{S_k-S_n\ge b_k\}\bigr)
&\ge\frac12\mathbb{P}(H_k^-).
\end{aligned}
$$
在 $H_k^+\cap\{S_k-S_n\le b_k\}$ 上，
$$
S_n=S_k-(S_k-S_n)\ge S_k-b_k\ge x;
$$
在 $H_k^-\cap\{S_k-S_n\ge b_k\}$上，
$$
S_n\le S_k-b_k\le-x.
$$
这些交事件仍两两不交，并且都包含于 $\{|S_n|\ge x\}$。求和得
$$
\begin{aligned}
\mathbb{P}(|S_n|\ge x)
&\ge\frac12\sum_{k=1}^{n}
\bigl[\mathbb{P}(H_k^+)+\mathbb{P}(H_k^-)\bigr]\\
&=\frac12\mathbb{P}\left(\max_{1\le k\le n}|S_k-b_k|\ge x\right).
\end{aligned}
$$
即得结论。

**QED**

>[!note] 对称化
>若各 $X_k$ 关于 $0$ 对称，则 $S_k-S_n$ 也关于 $0$ 对称，可取 $b_k=0$，得到常用形式
>$$
>\mathbb{P}\left(\max_{1\le k\le n}|S_k|\ge x\right)
>\le2\mathbb{P}(|S_n|\ge x).
>$$
>对于非对称变量，可以构造独立同分布副本 $X'_k$，使两列联合独立，则 $X_k-X'_k$ 相互独立且关于 $0$ 对称。这个构造与[[概率耦合方法|独立副本的构造]]相关。
>
>对称化是使用无中位数形式的常见方法；上面的中位数形式本身不要求对称性。

>[!thm] Lévy 型最大不等式（尾和形式）
>在相互独立的假设下，固定 $x>0$，令
>$$
>c=\max_{1\le k\le n}\mathbb{P}(|S_n-S_k|>x).
>$$
>若 $c<1$，则
>$$
>\mathbb{P}\left(\max_{1\le k\le n}|S_k|>2x\right)
>\le\frac{\mathbb{P}(|S_n|>x)}{1-c}.
>$$

^levy-tail

**Proof**

令 $H_k=\{|S_k|>2x,\ |S_j|\le2x,\ j<k\}$。在
$$
H_k\cap\{|S_n-S_k|\le x\}
$$
上，$|S_n|\ge|S_k|-|S_n-S_k|>x$。由各 $H_k$ 不交，且 $H_k$ 与尾和 $S_n-S_k$ 独立，
$$
\begin{aligned}
\mathbb{P}(|S_n|>x)
&\ge\sum_{k=1}^{n}\mathbb{P}(H_k)
\mathbb{P}(|S_n-S_k|\le x)\\
&\ge(1-c)\sum_{k=1}^{n}\mathbb{P}(H_k)\\
&=(1-c)\mathbb{P}\left(\max_{1\le k\le n}|S_k|>2x\right).
\end{aligned}
$$
除以 $1-c$ 即可。

**QED**

>[!thm] 独立中心化随机级数的收敛
>设 $X_1,X_2,\cdots$ 相互独立，$\mathbb{E}X_n=0$。若
>$$
>\sum_{n=1}^{\infty}\mathbb{E}X_n^2<\infty,
>$$
>则 $\sum_{n=1}^{\infty}X_n$ 几乎必然收敛到有限值。

^random-series

**Proof**

令 $S_n=\sum_{j=1}^{n}X_j$。W.T.S. $S_n$ 是 a.s. Cauchy 列。考虑证明 $S_n$ 几乎必然是一个Cauchy列，
$$
W_k=\sup_{m,n\ge k}|S_m-S_n|,
\qquad
U_k=\sup_{m\ge k}|S_m-S_k|.
$$
$W_k$ 是非负的扩展实值随机变量，且 $W_k\downarrow$。由三角不等式，$W_k\le2U_k$。

先对有限区间使用[[#^kolmogorov-maximal|Kolmogorov 极大不等式]]0。对 $N>k$，
$$
\mathbb{P}\left(\max_{k\le m\le N}|S_m-S_k|>\varepsilon\right)
\le\frac1{\varepsilon^2}
\sum_{j=k+1}^{N}\operatorname{Var}(X_j).
$$
令 $N\to\infty$，左边事件递增，故
$$
\mathbb{P}(U_k>\varepsilon)
\le\frac1{\varepsilon^2}
\sum_{j=k+1}^{\infty}\operatorname{Var}(X_j).
$$
于是
$$
\mathbb{P}(W_k>2\varepsilon)
\le\mathbb{P}(U_k>\varepsilon)
\le\frac1{\varepsilon^2}
\sum_{j=k+1}^{\infty}\operatorname{Var}(X_j)
\to0.
$$
这里直接由 $W_k\le2U_k$ 即可，不需要额外的系数 $2$。指标 $k$ 固定后先令 $N\to\infty$，再令 $k\to\infty$。

还需把依概率趋于 $0$ 变成 a.s. 趋于 $0$。由于 $W_k$ 单调不增，对每个 $r\ge1$，
$$
\{W_k>1/r\}\downarrow,
\qquad
\mathbb{P}\left(\bigcap_{k=1}^{\infty}\{W_k>1/r\}\right)
=\lim_{k\to\infty}\mathbb{P}(W_k>1/r)=0.
$$
对 $r$ 取可数并的补集，得到 a.s. 对每个 $r$ 存在 $k_r$，使 $k\ge k_r$ 时 $W_k\le1/r$。因此 $W_k\downarrow0$ a.s.，即 $S_n$ 为 Cauchy 列。

**QED**

>[!example] 随机调和级数
>设 $\xi_n$ 独立，$\mathbb{P}(\xi_n=1)=\mathbb{P}(\xi_n=-1)=1/2$。由于
>$$
>\mathbb{E}\frac{\xi_n}{n}=0,\qquad
>\sum_{n=1}^{\infty}\mathbb{E}\left(\frac{\xi_n}{n}\right)^2
>=\sum_{n=1}^{\infty}\frac1{n^2}<\infty,
>$$
>所以 $\sum_n\xi_n/n$ a.s. 收敛，但
>$$
>\sum_{n=1}^{\infty}\left|\frac{\xi_n}{n}\right|
>=\sum_{n=1}^{\infty}\frac1n=\infty.
>$$
>上述定理给出的是级数收敛，不是绝对收敛。

>[!lemma] Kronecker 引理
>设 $a_n>0,a_n\uparrow\infty$，$x_n$ 为实数。若级数
>$$
>\sum_{n=1}^\infty\frac{x_n}{a_n}
>$$
>收敛到有限值，则
>$$
>\frac1{a_n}\sum_{k=1}^nx_k\to0.
>$$
>特别地，$\sum_{n=1}^\infty x_n/n$ 收敛蕴含 $\frac1n\sum_{k=1}^nx_k\to0$。

^kronecker

**Proof**

令 $a_0=0,b_0=0$，并记
$$
b_n=\sum_{k=1}^{n}\frac{x_k}{a_k}\to b.
$$
则 $x_k=a_k(b_k-b_{k-1})$。由Abel变换（分部求和），
$$
\begin{aligned}
\frac1{a_n}\sum_{k=1}^{n}x_k
&=\frac1{a_n}\sum_{k=1}^{n}a_k(b_k-b_{k-1})\\
&=b_n-\frac1{a_n}\sum_{k=1}^{n}(a_k-a_{k-1})b_{k-1}.
\end{aligned}
$$
注意权重非负，且
$$
\sum_{k=1}^{n}\frac{a_k-a_{k-1}}{a_n}=1.
$$
只需证明这个加权平均也趋于 $b$。

给定 $\varepsilon>0$，取 $K$ 使 $k\ge K$ 时 $|b_k-b|<\varepsilon$。则
$$
\begin{aligned}
&\left|\frac1{a_n}
\sum_{k=1}^{n}(a_k-a_{k-1})b_{k-1}-b\right|\\
&\quad\le
\frac1{a_n}\sum_{k=1}^{K}(a_k-a_{k-1})|b_{k-1}-b|
+\varepsilon\frac{a_n-a_K}{a_n}.
\end{aligned}
$$
固定 $K$，第一项随 $n\to\infty$ 趋于 $0$，第二项至多为 $\varepsilon$。再令 $\varepsilon\downarrow0$，得到加权平均趋于 $b$，从而
$$
\frac1{a_n}\sum_{k=1}^{n}x_k\to b-b=0.
$$

**QED**

>[!note] 第二种证明：随机级数方法
>回到[[#^slln-integrable|Kolmogorov 强律]]。仍取
>$$
>Y_k=X_k\mathbb{1}_{\{|X_k|\le k\}},\quad
>T_n=\sum_{k=1}^{n}Y_k,\quad
>Z_k=Y_k-\mathbb{E}Y_k.
>$$
>需要证明的是中心化后的平均趋于 $0$，而不是直接证明 $\sum_kY_k/k$ 收敛。

**Proof**

由[[#^slln-truncated-variance|前面的截断估计]]，
$$
\sum_{k=1}^{\infty}
\operatorname{Var}\left(\frac{Z_k}{k}\right)
=\sum_{k=1}^{\infty}\frac{\operatorname{Var}(Y_k)}{k^2}
\le4\mathbb{E}|X_1|<\infty.
$$
$Z_k/k$ 相互独立且均值为 $0$，所以由[[#^random-series|独立中心化级数收敛定理]]，
$$
\sum_{k=1}^{\infty}\frac{Z_k}{k}
\quad\text{a.s. 收敛}.
$$
在每一条级数收敛的样本路径上，对 $x_k=Z_k(\omega),a_k=k$ 使用 [[#^kronecker|Kronecker 引理]]，得到
$$
\frac1n\sum_{k=1}^{n}Z_k
=\frac{T_n}{n}-\frac1n\sum_{k=1}^{n}\mathbb{E}Y_k
\xrightarrow{a.s.}0.
$$
再由 DCT 与 Cesàro 平均，
$$
\mathbb{E}Y_k\to\mu,\qquad
\frac1n\sum_{k=1}^{n}\mathbb{E}Y_k\to\mu.
$$
于是 $T_n/n\xrightarrow{a.s.}\mu$，最后用[[#^slln-truncation|截断引理]]回到 $S_n/n\xrightarrow{a.s.}\mu$。

**QED**

>[!note] 证明中的连接
>$$
>\begin{gathered}
>\sum_{k=1}^{\infty}
>\frac{\operatorname{Var}(Y_k)}{k^2}<\infty\\
>\Downarrow\quad\text{独立中心化级数收敛定理}\\
>\sum_{k=1}^{\infty}\frac{Y_k-\mathbb{E}Y_k}{k}
>\text{ a.s. 收敛}\\
>\Downarrow\quad\text{Kronecker}\\
>\frac1n\sum_{k=1}^{n}(Y_k-\mathbb{E}Y_k)
>\xrightarrow{a.s.}0.
>\end{gathered}
>$$

^slln-variance-criterion