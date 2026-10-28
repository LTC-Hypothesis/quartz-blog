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
>对于独立的 r.v. $\{A_n\}$ ，则成立
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

>[!thm] Kolmogorov 强大数定律
>设 $X_1,X_2,\cdots$ 为 i.i.d. 随机变量，$\mathbb{E}|X_1|<\infty$，记
>$$
>\mu=\mathbb{E}X_1,\qquad S_n=\sum_{k=1}^nX_k.
>$$
>当且仅当
>$$
>\frac{S_n}{n}\xrightarrow{a.s.}\mu.
>$$

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


