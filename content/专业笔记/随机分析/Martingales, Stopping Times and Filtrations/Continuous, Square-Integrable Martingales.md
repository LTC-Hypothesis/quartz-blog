Fix probability space $(\Omega,\mathcal{F},\mathbb{P})$ and a filtration $\{\mathcal{F}_t\}$ with [[Stopping Times#^47dba3|usual condition]].

> [!def] Square-integrable martingale
> Let $X_t$ be a right-continuous martingale. We say that $X$ is square-integrable if $\mathbb{E}(X^2_t)<\infty$ for every $t > 0$.
> If $X_0=0,a.s.$ we write $X_t\in\mathcal{M}_2$. If $X_t$ is also continuous, we write $X_t\in \mathcal{M}^c_2$.

> [!warning]
> Although we have defined $\mathcal{M}^c_2$ so that its members have every sample path continuous, the results which follow are also true if we assume only that $\mathbb{P}$-almost every sample path is continuous.

> [!def] Quadratic variation
> For $X_t\in\mathcal{M}_2$, the quadratic variation $\langle X\rangle_t\triangleq A_t$, where $A_t$ is s the natural increasing process in the **Doob-Meyer decomposition** of $X^2_t$
> $\langle X\rangle_t$ is that unique (up to indistinguishability) adapted, natural increasing process, for which $\langle X\rangle_0=0,a.s.$ and $X^2_t -\langle X\rangle_t$ is a martingale.

^d32204

> [!warning]
> The definition is well-defined. For $X_t\in\mathcal{M}_2$, $X^2_t$ is a submartingale since $\varphi(x)=x^2$ is convex and thus in class $DL$. By [[The Doob-Meyer Decomposition#^5cc05f|Doob-Meyer decomposition]], we have $X^2_t=M_t+A_t$. We normalize $M_0=A_0=0$. If $X\in\mathcal{M}^c_2$, then $A$ and $M$ are continuous.

> [!example]
> For example, we call [[Continuous-Time Martingales#^1dd541|Poisson process]]. Then the quadratic variation $\langle M\rangle_t=\lambda t$.

> [!def] Cross variation
> For any two martingales $X,Y\in\mathcal{M}_2$, we define the **cross variation** $\langle X,Y\rangle$, 
> $$
> \langle X,Y\rangle_t=\frac{1}{4}\left(\langle X+Y\rangle_t-\langle X-Y\rangle_t\right)
> $$
> Then $XY-\langle X,Y\rangle_t$ is a martingale. If $\langle X,Y\rangle_t=0,a.s.$, we call $X,Y$ are **orthogonal**.

^1be06d

> [!warning]
> 1. $\langle X,X\rangle=\langle X\rangle$
> 2. We calculate
>    $$
>    \begin{align}
> \mathbb{E}\left[(X_t-X_s)(Y_t-Y_s)|\mathcal{F}_s\right]&=\mathbb{E}[X_tY_t-X_sY_s|\mathcal{F}_s]\\
> &=\mathbb{E}[\langle X,Y\rangle_t-\langle X,Y\rangle_s|\mathcal{F}_s]
> \end{align}
>    $$
>    The orthogonality of $X_t,Y_t\in\mathcal{M}_2$ is equivalent of "$X,Y$ are martingale" or "the cross variation of $X,Y$ are codnitional uncorrelated".
> 3. The uniqueness argument also shows that is, up to indistinguishability.

> [!proposition]
> $\langle \cdot,\cdot\rangle_t$ is a bilinear form on $\mathcal{M}_2$ i.e. it satisfies 
> 4. $\langle \alpha X+\beta Y,Z\rangle_t=\alpha\langle X,Z\rangle_t+\beta\langle Y,Z\rangle_t,\forall\alpha,\beta\in\mathbb{R}$
> 5. $\langle X,Y\rangle_t=\langle Y,X\rangle_t$
> 6. $|\langle X,Y\rangle_t|^2\le \langle X\rangle_t\langle Y\rangle_t$
> 7. For $\mathbb{P}-a.s.\omega\in\Omega$, $0\le s<t<\infty$
>    $$
>    \langle X,Y\rangle_t-\langle X,Y\rangle_s\le \frac{1}{2}[\langle X\rangle_t-\langle X\rangle_s+\langle Y\rangle_t-\langle Y\rangle_s]
>    $$

**Proof**
We check each item. 
1. We use the property of uniqueness. Since $(\alpha X+\beta Y)Z-\langle \alpha X+\beta YZ\rangle_t$ is a martingale, and $(\alpha X+\beta Y)Z=\alpha XZ+\beta YZ$. For $XZ$ and $YZ$, $\alpha XZ-\alpha\langle X,Z\rangle$ and $\beta YZ-\beta\langle Y,Z\rangle$ are martingales, then $(\alpha XZ+\beta YZ)-(\alpha\langle X,Z\rangle+\beta\langle Y,Z\rangle)$ is a martingale. By uniqueness, we obtain $\langle \alpha X+\beta Y,Z\rangle_t=\alpha\langle X,Z\rangle_t+\beta\langle Y,Z\rangle_t$.
2. Since $XY-\langle X,Y\rangle_t$ is a martingale, $YX-\langle Y,X\rangle_t=XY-\langle Y,X\rangle_t$. By uniqueness, $\langle X,Y\rangle_t=\langle Y,X\rangle_t$.
3. We can use the [[Introduction of Hilbert Space#^970a9c|CBS]]. In fact, cross variation satisfies item1 and item2, it becomes a semi-inner product and it holds CBS. Hence, we obtain $$|\langle X,Y\rangle_t|^2\le |\langle X,X\rangle_t||\langle Y,Y\rangle_t|^2=\langle X\rangle_t\langle Y\rangle_t$$
4. Consider $0\le s<t$ and $\lambda\in\mathbb{R}$, we have $$\begin{align}
0&\le \langle X+\lambda Y\rangle_t-\langle X+\lambda Y\rangle_s\\
&=(\langle X\rangle_t-\langle X\rangle_s)+(\langle X,Y\rangle_t-\langle X,Y\rangle_s)\lambda+(\langle Y\rangle_t-\langle Y\rangle_s)\lambda^2
\end{align}$$Therefore, $\langle X,Y\rangle_t-\langle X,Y\rangle_s\le \sqrt{(\langle X\rangle_t-\langle X\rangle_s)(\langle Y\rangle_t-\langle Y\rangle_s)}\le\frac{1}{2}[\langle X\rangle_t-\langle X\rangle_s+\langle Y\rangle_t-\langle Y\rangle_s]$

**QED**

> [!def] More conventional use of variation/p-variation
> Let $X_t$ be a process, fix $t>0$ and let partition $\Pi=\{t_0,t_1,\cdots,t_m\}$ with $0=t_0\le t_1\le\cdots\le t_m=t$. Define the $p-$variation of $X_t$ over the $\Pi$ to be 
> $$
> V^{(p)}_t(\Pi)=\sum_{k=1}^{m}|X_{t_k}-X_{k-1}|^p
> $$ 
> Define $\|\Pi\|=\max_{1\le k\le m}|t_{k}-t_{k-1}|$. If $V^{(2)}_t$ converge as $\|\Pi\|\to0$, , the limit is entitled to be called the **quadratic variation** of $X$ on $[0, t]$.

For two definition, We have follow result. 

> [!thm]
> Let $X\in\mathcal{M}^c_2$. For partition $\Pi$ on $[0,t]$, we have 
> $$
> \lim_{\|\Pi\|\to0}V^{(2)}_t(\Pi)=\langle X\rangle_t,in \ probability
> $$
> i.e. for every $\varepsilon>0$, $\eta>0$, there exists $\delta>0$, s.t. $\|\Pi\|<\delta$ implies
> $$
> \mathbb{P}(|V^{(2)}_t-\langle X\rangle_t|>\varepsilon)<\eta
> $$

^783219

The proof of the Theorem proceeds through two lemmas.

> [!lemma]
> Let $X\in\mathcal{M}_2$ satisfy $|X_s|\le K<\infty$ for all $s\in[0,t],a.s.\mathbb{P}$. Let partition $\Pi=\{t_0,\cdots,t_m\}$ with $0=t_0\le t_1\le \cdots\le t_m=t$ on $[0,t]$. Then $\mathbb{E}[V^{(2)}_t(\Pi)]^2\le 6K^4$.

^c2158c

**Proof**
Before the proof, we should note that a key fact of calculation. For $X\in\mathcal{M}_2$ and $0\le s<t\le u<v$, then 
$$
\mathbb{E}(X_v-X_u)(X_t-X_s)=\mathbb{E}[\mathbb{E}(X_v-X_u|\mathcal{F}_u)(X_t-X_s)]=0
$$
This fact to both $X\in\mathcal{M}_2$ and $X^2-\langle X\rangle_t$ is true. 
$$
\begin{align}
\mathbb{E}[(X_v-X_u)^2|\mathcal{F}_t]&=\mathbb{E}[X^2_v-2X_vX_u+X^2_u|\mathcal{F}_t]\\
&=\mathbb{E}[X^2_v-2\mathbb{E}[X_v|\mathcal{F}_u]X_u+X^2_u|\mathcal{F}_t]\tag{Tower principle}\\
&=\mathbb{E}[X^2_v-X^2_u|\mathcal{F}_t]\\
&=\mathbb{E}[\langle X\rangle_v-\langle X\rangle_u|\mathcal{F}_t]\tag{Martingale}
\end{align}
$$
We prove the lemma. We calculate
$$
\begin{align}
\mathbb{E}\left[V^{(2)}_t(\Pi)\right]^2&=\mathbb{E}\left[\sum_{j=1}^{m}|X_{t_j}-X_{t_{j-1}}|^2\right]^2\\
&=\mathbb{E}\left[\sum_{k=1}^{m}(X_{t_k}-X_{t_{k-1}})^4\right]+2\mathbb{E}\left[\sum_{k=1}^{m-1}\sum_{j=k+1}^{m}(X_{t_j}-X_{t_{j-1}})^2(X_{t_k}-X_{t_{k-1}})^2\right]
\end{align}
$$
For the second item, for $0\le k\le m-1$, by the key fact, 
$$
\begin{align}
\mathbb{E}\left[\sum_{j=k+1}^{m}(X_{t_j}-X_{t_{j-1}})^2|\mathcal{F}_{t_k}\right]&=\mathbb{E}\left[\sum_{j=k+1}^{m}(X_{t_j}^2-X_{t_{j-1}}^2)|\mathcal{F}_{t_k}\right]\\
&=\mathbb{E}[X^{2}_{t_m}-X^2_{t_{k}}|\mathcal{F}_{t_k}]\le\mathbb{E}[X^{2}_{t_m}|\mathcal{F}_{t_k}]\le K^2 
\end{align}
$$
By product, 
$$
\mathbb{E}\left[\sum_{k=1}^{m}(X_{t_j}-X_{t_{j-1}})^2\right]\le K^2
$$
Hence, 
$$
\begin{align}
&\mathbb{E}\left[\sum_{k=1}^{m-1}\sum_{j=k+1}^{m}(X_{t_j}-X_{t_{j-1}})^2(X_{t_k}-X_{t_{k-1}})^2\right]\\
=&\mathbb{E}\left[\sum_{k=1}^{m-1}(X_{t_k}-X_{t_{k-1}})^2\mathbb{E}\left[\sum_{j=k+1}^{m}(X_{t_j}-X_{t_{j-1}})^2|\mathcal{F}_{t_k}\right]\right]\\
\le &K^2\mathbb{E}\left[\sum_{k=1}^{m-1}(X_{t_k}-X_{t_{k-1}})^2\right]\le K^4
\end{align}
$$
For the first item, 
$$
\begin{align}
\mathbb{E}\left[\sum_{k=1}^{m}(X_{t_k}-X_{t_{k-1}})^4\right]&=\mathbb{E}\left[\sum_{k=1}^{m}(X_{t_k}-X_{t_{k-1}})^2(X_{t_k}-X_{t_{k-1}})^2\right]\\
&\le4K^2\mathbb{E}\left[\sum_{k=1}^{m}(X_{t_j}-X_{t_{j-1}})^2\right]\le4K^4
\end{align}
$$
Hence, 
$$
\mathbb{E}\left[V^{(2)}_t(\Pi)\right]^2\le 4K^4+2K^4=6K^4
$$
**QED**

> [!lemma]
> Let $X\in\mathcal{M}^c_2$ satisfy $|X_s|\le K<\infty$ for all $s\in[0,t],a.s.\mathbb{P}$. Let partition $\Pi=\{t_0,\cdots,t_m\}$ with $0=t_0\le t_1\le \cdots\le t_m=t$ on $[0,t]$.we have 
> $$
> \lim_{\|\Pi\|\to0}\mathbb{E}(V^{(4)}_t(\Pi))=0
> $$

^ec029d

**Proof**
Let $m^2_t(X,\delta)\triangleq\{|X_r-X_s|:r,s\in\mathbb{Q},0\le r<s\le t,s-r<\delta\}$, note that 
$$
V^{(4)}_t(\Pi)\le V^{(2)}_t(\Pi)m^2_t(X,\|\Pi\|)
$$
Take expectation and by Holder's inequality,
$$
\mathbb{E}(V^{(4)}_t(\Pi))\le (\mathbb{E}(V^{(2)}_t(\Pi))^2)^{\frac{1}{2}}(\mathbb{E}(m^4_t(X,\|\Pi\|)))^{\frac{1}{2}}
$$
By [[#^c2158c|last lemma]] and let $\|\Pi\|\to0$, since $X$ is continuous, $m_t(X,\|\Pi\|)\to0$. Hence, by BCT, $\mathbb{E}(V^{(4)}_t(\Pi))\to0$ as $\|\Pi\|\to0$.
**QED**

**Proof of [[#^783219|Thm]]**: **Case1**: $X_t$ and $\langle X\rangle_t$ are bounded i.e. $|X_s|\le K<\infty$ and $\langle X\rangle_t\le K$ hold for all $s\in[0,t],a.s.\mathbb{P}$. 
$$
\begin{align}
\mathbb{E}[V^{(2)}_t(\Pi)-\langle X\rangle_t]^2&=\mathbb{E}\left[\sum_{k=1}^{m}((X_{t_k}-X_{t_{k-1}})^2-(\langle X\rangle_{t_k}-\langle X\rangle_{t_{k-1}}))\right]^2\\
&=\sum_{k=1}^{m}\mathbb{E}\left[(X_{t_k}-X_{t_{k-1}})^2-(\langle X\rangle_{t_k}-\langle X\rangle_{t_{k-1}})\right]^2\\
&\le2\sum_{k=1}^{m}\mathbb{E}[(X_{t_k}-X_{t_{k-1}})^4+(\langle X\rangle_{t_k}-\langle X\rangle_{t_{k-1}})^2]\\
&\le2\mathbb{E}(V^{(n)}_t(\Pi))^4+2\mathbb{E}[\langle X\rangle_t m_t(X,\|\Pi\|)]
\end{align}
$$
By [[Continuous, Square-Integrable Martingales#^ec029d|lemma]] and $m_t(X,\|\Pi\|)$, $\mathbb{E}[V^{(2)}_t(\Pi)-\langle X\rangle_t]^2\to0$ as $\|\Pi\|\to0$. Hence, $L^2$ convergence implies converge in probability.
**Case2**: Now we suppose $X$ is not necessarily bounded. To transform to the case1, we consider the technique of localization. We define the stopping time 
$$
T_n=\inf\{t\ge0:|X_t|\ge n \mbox{ or } \langle X\rangle_t\ge n\}
$$
Let $X^{(n)}_t=X_{t\wedge T_n}$ is a bounded martingale refer to [[Continuous-Time Martingales#^c29c8c|Exercise of Martingale]] and so is $X^{2}_{t\wedge T_n}-\langle X\rangle_{t\wedge T_n}$. By uniqueness of [[The Doob-Meyer Decomposition#^5cc05f|Doob-Meyer decomposition]], $\langle X^{(n)}\rangle_t=\langle X\rangle_{t\wedge T_n}$. By case1, 
$$
\mathbb{E}\left[(V^{(2)}_{X^{(n)}_t}(\Pi))^2-\langle X\rangle_{t\wedge T_n}\right]^2\to0,\mbox{as }\|\Pi\|\to0 
$$
Since $T_n\uparrow\infty$, for fixed $t\ge0$, $\mathbb{P}[T_n<t]\to0$ as $n\to\infty$. Hence, we obtain
$$
\mathbb{E}\left[(V^{(2)}_{t}(\Pi))^2-\langle X\rangle_{t}\right]^2\to0,\mbox{as }\|\Pi\|\to0,n\to\infty
$$
**QED**

The follow theorem tell us why $\mathcal{M}^c_2(\mathcal{M}_2)$ is worth to study.

> [!thm]
> Let $\{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be a continuous process with the property that for each fixed $t > 0$ and for some $p > 0$,
> $$
> \lim_{\|\Pi\| \to 0} V_t^{(p)}(\Pi) = L_t \quad \text{(in probability)},
> $$
> where $L_t$ is a random variable taking values in $[0, \infty)$ a.s. Show that for $q > p$,
> $$
> \lim_{\|\Pi\| \to 0} V_t^{(q)}(\Pi) = 0 \quad \text{(in probability)},
> $$
> and for $0 < q < p$,
> $$
> \lim_{\|\Pi\| \to 0} V_t^{(q)}(\Pi) = \infty \quad \text{(in probability)} \text{ on the event } \{L_t > 0\}.
> $$

^56ddbe

**Proof**
Case1: $q>p$. we have 
$$
\begin{align}
V^{(q)}_t&=\sum_{k=1}^{m}|X_{t_k}-X_{t_{k-1}}|^q=\sum_{k=1}^{m}|X_{t_k}-X_{t_{k-1}}|^{q-p}|X_{t_k}-X_{t_{k-1}}|^{p}\\
&\le\sup_{1\le k\le m}|X_{t_k}-X_{t_{k-1}}|^{q-p}V^{(p)}_t
\end{align}
$$
Since $V^{(p)}_t\xrightarrow{\mathbb{P}}L_t$ as $\|\Pi\|\to0$, it suffices to show that $\sup_{1\le k\le m}|X_{t_k}-X_{t_{k-1}}|^{q-p}\xrightarrow{\mathbb{P}}0$. Since process $X_t$ is continuous i.e. for every $\varepsilon>0$, $\exists\delta>0$ s.t. $|t_{k}-t_{k-1}|<\delta$, $|X_{t_k}-X_{t_{k-1}}|^{q-p}<\varepsilon^2$. By [[Continuous-Time Martingales#^bd276e|maximal inequality]], 
$$
\begin{align}
\mathbb{P}\left(\sup_{1\le k\le m}|X_{t_k}-X_{t_{k-1}}|^{p-q}>\varepsilon\right)\le \frac{\mathbb{E}\left(|X_{t}-X_{t_{m-1}}|^{p-q}\right)}{\varepsilon}<\varepsilon
\end{align}
$$
Hence, $V^{q}_t\xrightarrow{\mathbb{P}}0$ as $\|\Pi\|\to0$.
Case2: $0<q<p$. We have 
$$
\begin{align}
V^{(q)}_t&=\sum_{k=1}^{m}|X_{t_k}-X_{t_{k-1}}|^q=\sum_{k=1}^{m}|X_{t_k}-X_{t_{k-1}}|^{q-p}|X_{t_k}-X_{t_{k-1}}|^{p}\\
&=\sum_{k=1}^{m}\frac{|X_{t_k}-X_{t_{k-1}}|^{p}}{|X_{t_k}-X_{t_{k-1}}|^{p-q}}\ge\frac{V^{(p)}_t}{\sup_{1\le k\le m}|X_{t_k}-X_{t_{k-1}}|^{p-q}}\\
\end{align}
$$
Since $V^{(p)}_t\xrightarrow{\mathbb{P}}L_t$ and $L_t>0$, $V^{(p)}_t$ has lower bounded in probability. For $\sup_{1\le k\le m}|X_{t_k}-X_{t_{k-1}}|^{p-q}\to0$ as $\|\Pi\|\to0$, it is proved by case1. Hence, 
$$
V^{(q)}_t\ge \frac{V^{(p)}_t}{\sup_{1\le k\le m}|X_{t_k}-X_{t_{k-1}}|^{p-q}}\to\infty \mbox{ as $\|\Pi\|\to0$ in probability}
$$
**QED**

> [!warning]
> This theorem implies that quadratic variation is the **"right" variation to study**. All variations of **higher order are zero**, and, except in trivial cases where the martingale is a.s. constant on an initial interval, all variations of **lower order are infinite with positive probability**. Thus, the sample paths of continuous, square-integrable martingales are **quite different from "ordinary" continuous functions**. Being of unbounded first variation, they cannot be differentiable, nor is it possible to define integrals of the form Ito $\int_0^tY_s(\omega){d}X_s(\omega)$ with respect to $X\in \mathcal{M}^c_2$, in a pathwise (i.e., for every or $\mathbb{P}$-almost every $\omega\in\Omega$), Lebesgue-Stieltjes sense. 

We discuss now the cross-variation between two continuous, square-integrable martingales.

> [!thm]
> Let $X,Y\in\mathcal{M}^c_2$. There is a unique (up to indistinguishability) $\{\mathcal{F}_t\}$-adapted, continuous process of bounded variation $A_t$ satisfying $A_0=0$ a.s. $\mathbb{P}$, such that $X_tY_t-A_t$ is a martingale. This process is given by the cross-variation $\langle X,Y\rangle$.

**Proof**
In fact, $A=\langle X,Y\rangle$ is clearly the process from [[Continuous, Square-Integrable Martingales#^1be06d|cross variation]]. This show the existence. Now we prove the uniqueness. Suppose there exists another process $B$ satisfies $X_tY_t-B_t$ is a martingale. Then $M\triangleq (XY-A)-(XY-B)=B-A$ is a continuous martingale with finite first variation. We define the stopping time 
$$
T_n=\inf\{t\ge0:|M_t|=n\}
$$
then $M^{(n)}_t\triangleq M_{t\wedge T_n}$ is a continuous, bounded martingale by [[Continuous-Time Martingales#^c29c8c|Exercise of Martingale]], , with finite first variation on every interval $[0,t]$. By [[Continuous, Square-Integrable Martingales#^56ddbe|variation theorem]], we obtain $\langle M\rangle_{t\wedge T_n}=\langle M^{(n)}\rangle_t=0,a.s.\mathbb{P}$ for $t\ge0$. Then $M^{(n)}\equiv0,a.s.$ as $T_n\uparrow\infty$. $M\equiv0,a.s.\mathbb{P}$.
**QED**

Cross variation can also be describe by limit of partition. 

> [!proposition]
> For $X,Y\in\mathcal{M}^c_2$ and partition $\Pi=\{t_0,t_1,\cdots,t_m\}$ of $[0,t]$. We have 
> $$
> \lim_{\|\Pi\|\to0}\sum_{k=1}^{m}(X_{t_k}-X_{t_{k-1}})(Y_{t_k}-Y_{t_{k-1}})=\langle X,Y\rangle,\mbox{in probability}
> $$

**Proof**
By polarization identity, 
$$
\begin{align}
&\sum_{k=1}^{m}(X_{t_k}-X_{t_{k-1}})(Y_{t_k}-Y_{t_{k-1}})\\
=&\frac{1}{4}\sum_{k=1}^{n}\left[(X_{t_k}-X_{t_{k-1}}+Y_{t_k}-Y_{t_{k-1}})^2-(X_{t_k}-X_{t_{k-1}}-Y_{t_k}+Y_{t_{k-1}})^2\right]\\
=&\frac{1}{4}\sum_{k=1}^{n}\left[(X_{t_k}+Y_{t_k}-(X_{t_{k-1}}+Y_{t_{k-1}}))^2-(X_{t_k}-Y_{t_k}-(X_{t_{k-1}}-Y_{t_{k-1}}))^2\right]\\
&\to\frac{1}{4}[\langle X+Y\rangle-\langle X-Y\rangle]=\langle X,Y\rangle\mbox{ as $\|\Pi\|\to0$ in probability}
\end{align}
$$
**QED**

We note that the technique of "localization" is excellent in above proof. In fact, the technique make square-integrable martingale to continuous in some stopping time. The process with this property is called local martingale.

> [!def] Local martingale
> Let $X_t$ be a continuous process with $X_0=0,a.s.$ If there exists a nondecreasing sequence $\{T_n\}$ s.t. $X_{t\wedge T_n}$ be a martingalefor each $n\ge 1$ and $\mathbb{P}[\lim_{n\to\infty}T_n=\infty]=1$, then we say that $X$ is a **(continuous) local martingale** and write $X\in\mathcal{M}^{loc}$ (respectively, $X\in\mathcal{M}^{c,loc}$ if $X$ is continuous).

> [!warning]
> 1. Every martingale is a local martingale.[[Continuous-Time Martingales#^c29c8c|Exercise of Martingale]]but the converse is false.
> 2. We shall encounter continuous, local martingales which are integrable, or even uniformly integrable, but fail to be martingales.

Now we discuss the metric on $\mathcal{M}_2$ and its subspace $\mathcal{M}^c_2$. 

> [!def] Metric on $\mathcal{M}_2$
> For $X\in\mathcal{M}_2$ and $t\ge0$, we define 
> $$
> \|X\|_t=\sqrt{\mathbb{E}(X^2_t)}, \|X\|\triangleq\sum_{n=1}^{\infty}\frac{\|X\|_n\wedge1}{2^n}
> $$

> [!warning]
> 1. $t\mapsto\|X\|_t$ is nondecreasing since $X^2_t$ is submartingale.
> 2. $\|X-Y\|$ is a pseudo-metric(伪度量) i.e. it admits the distence of different point is 0. It becomes a metric if we identify indistinguishable process. 
>    Suppose $X,Y\in\mathcal{M}_2$ we have $\|X-Y\|=0\Longrightarrow X_n=Y_na.s.\mathbb{P}$ for $n\ge1$ and thus $X_t=\mathbb{E}(X_n|\mathcal{F}_t)=\mathbb{E}(Y_n|\mathcal{F}_t)=Y_t$ for $0\le t\le n$. Since $X,Y$ are right-continuous, then they are [[Stochastic Processes and σ-Fields#^a7c078|indistinguishable]].

> [!thm]
> Under the preceding metric, $\mathcal{M}_2$ is a **complete metric space**, and $\mathcal{M}^c_2$ a **closed subspace** of $\mathcal{M}_2$

^8acb93

**Proof**
Suppose a Cauchy sequence $\{X^{(n)}\}_{n=1}^{\infty}\subseteq\mathcal{M}_2$ under the metric $\|\cdot\|$, that is $\lim_{n,m\to\infty}\|X^{(n)}-X^{(m)}\|=0$. For fixed $t$, $\{X^{(n)}_t\}$ is Cauchy sequence in $L^2(\Omega,\mathcal{F},\mathbb{P})$ and $L^2(\Omega,\mathcal{F},\mathbb{P})$ is complete. There exists $X_t\in L^2(\Omega,\mathcal{F},\mathbb{P})$ s.t. $X^{(n)}_t\xrightarrow{L^2}X_t$. Now we check $X_t$ is a martingale. For $0\le s<t<\infty$ and $A\in\mathcal{F}_s$, then 
$$
\mathbb{E}(\mathbb{1}_A(X^{(n)}_t-X_t))\le \sqrt{\mathbb{E}(X^{(n)}_t-X_t)^2\mathbb{P}(A)}\to0
$$
So is $\mathbb{E}(\mathbb{1}_A(X^{(n)}_s-X_s))\to0$. Since $X^{(n)}$ is martingale, then $\mathbb{E}(\mathbb{1}_AX^{(n)}_t)=\mathbb{E}(\mathbb{1}_AX^{(n)}_s)$. Hence, $\mathbb{E}(\mathbb{1}_AX_t)=\mathbb{E}(\mathbb{1}_AX_s)$. we can choose a right-continuous modification s.t. $X\in\mathcal{M}_2$ and hold $\|X_t-X\|\to0$.
Now we prove $\mathcal{M}^c_2$ is closed. Suppose $\{X^{(n)}\}\subseteq\mathcal{M}^c_2$ and $X^{(n)}\to X\in\mathcal{M}_2$. We W.T.S $X$ is continuous. The method is to show $X^{(n)}\rightrightarrows X$. By [[Continuous-Time Martingales#^bd276e|maximal inequality]], 
$$
\mathbb{P}\left[\sup_{0\le t\le T}|X^{(n)}_t-X_t|\ge \varepsilon\right]\le\frac{1}{\varepsilon^2}\mathbb{E}|X^{(n)}_T-X_T|^2\to0
$$
For $\forall k\ge1$, we choose the subsequence $n_k$ and have 
$$
\mathbb{P}\left[\sup_{0\le t\le T}|X^{(n_k)}_t-X_t|\ge \frac{1}{k}\right]\le \frac{1}{2^k}
$$
By Borel-Cantelli lemma, $X^{(n_k)}_t\xrightarrow{a.s.}X_t\Longrightarrow X^{(n_k)}_t\rightrightarrows X_t$. Since $X^{(n_k)}_t$ is continuous, $X_t$ is also continuous.
**QED**

---
# Exercises

> [!question]
> Let $X$ be in $\mathcal{M}_2^c$, and $T$ be a stopping time of $\{ \mathcal{F}_t \}$. If $\langle X \rangle_T = 0$,a.s. $\mathbb{P}$, then we have $\mathbb{P}[X_{T \wedge t} = 0; \forall 0 \leq t < \infty] = 1$.

^7ac13a

> [!done]
> Since $X_t\in\mathcal{M}^c_2$, $X_0=0$ and $X^2-\langle X\rangle$ is martingale. By $\langle X\rangle_T=0$ and variation is increasing, $\langle X\rangle_{T\wedge t}\le \langle X\rangle_T=0$. Then we obtain $X^2_{T\wedge t}$ is a martingale and satisfies
> $$
> \mathbb{E}[X^2_{T\wedge t}]=\mathbb{E}[\langle X\rangle_{T\wedge t}]=0\Longrightarrow X_{T\wedge t}=0,a.s.-\mathbb{P}
> $$
> In other word, $X_{T\wedge t}$ is a modification of $0$. By continuity of $X$, $t\mapsto X_{T\wedge t}$ is also continuous, then $X_{T\wedge t}$ is [[Stochastic Processes and σ-Fields#^a7c078|indistinguishable]] with $0$ i.e. $\mathbb{P}[X_{T \wedge t} = 0; \forall 0 \leq t < \infty] = 1$

> [!question]
> Let $X, Y$ be in $\mathcal{M}^{c,\text{loc}}$. Then there is a unique (up to indistinguishable) adapted, continuous process of bounded variation $\langle X, Y \rangle$ satisfying $\langle X, Y \rangle_0 = 0$ a.s. $\mathbb{P}$, such that $XY - \langle X, Y \rangle \in \mathcal{M}^{c,\text{loc}}$. If $X = Y$, we write $\langle X \rangle = \langle X, X \rangle$, and this process is nondecreasing.

> [!done]
> 

> [!question]
> Suppose $X \in \mathcal{M}_2$ has stationary, independent increments. Then
> $$
> \langle X \rangle_t = t (\mathbb{E} X_1^2), \quad t \geq 0.
> $$

> [!done]
> 

> [!question]
> 1. A local martingale of class $DL$ is a martingale.  
> 2. A nonnegative local martingale is a supermartingale.  
> 3. If $M \in \mathcal{M}^{c,\text{loc}}$ and $S$ is a stopping time of $\{\mathcal{F}_t\}$, then $\mathbb{E}(M_S^2) \leq \mathbb{E}\langle M\rangle_S$, where $M_\infty^2 \triangleq \varliminf_{t \to \infty} M_t^2$.

> [!done] Done for 1
> Suppose $X_t$ is a local martingale of class $DL$, $T_n\uparrow\infty ,a.s.$ is a sequence of stopping time. We have $X_{T_n\wedge t}$ is a martingale for $0\le t<\infty$. Note that $T_n\wedge t\le t$, then $T_n\wedge t$ is bounded in probability, such as take $a=t+1$ for any $0\le t<\infty$. Therefore $T_n\wedge t\in\mathscr{S}_a$. Since $X_t$ is class $DL$, $X_{T_n\wedge t}$ is u.i. By [[Continuous-Time Martingales#^3e0f1e|convergence of martingale]] and $X_{T_n\wedge t}$ is a martingale, for $0\le s<t<\infty$, we obtain
> $$
> \begin{align}
> \mathbb{E}[X_{T_n\wedge t}|\mathcal{F}_s]=X_{T_n\wedge s}\Longrightarrow\mathbb{E}[X_t|\mathcal{F}_s]=X_s\mbox{ as $T_n\uparrow\infty$ }
> \end{align}
> $$

> [!done] Done for 2
> Suppose $X_t$ is a local martingale, $T_n\uparrow\infty$ is a sequence of stopping time s.t. $X_{T_n\wedge t}$ is a martingale. We have $X_t=\lim_{n\to\infty}X_{T_n\wedge t}$. Then by Fatou's lemma, 
> $$
> \mathbb{E}[X_t|\mathcal{F}_s]=\mathbb{E}[\lim_{n\to\infty}X_{T_n\wedge t}|\mathcal{F}_s]\le \varliminf_{n\to\infty}\mathbb{E}[X_{T_n\wedge t}|\mathcal{F}_s]=\varliminf_{n\to\infty}X_{T_n\wedge s}=X_s
> $$
> Hence, $X_t$ is a supermartingale.

> [!done] Done for 3
> Define a sequence of stopping time $\tau_n$,
> $$
> \tau_n=\inf\{t\ge0:\langle M\rangle_t\ge n\}\wedge n
> $$
> Since $M$ is local martingale and thus its variation is bounded, $\tau_n\uparrow\infty$. Let $S_n=S\wedge \tau_n$, $S_n\le n$ and thus is a bounded stopping time. Since $M^2_t-\langle M\rangle_t\in\mathcal{M}^{c,loc}$, by [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], 
> $$
> \mathbb{E}(M^2_{S\wedge\tau_n}-\langle M\rangle_{S\wedge\tau_n})\le 0\Longrightarrow\mathbb{E}(M^2_{S\wedge\tau_n})\le\mathbb{E}(\langle M\rangle_{S\wedge \tau_n})
> $$
> Let $n\to\infty$, $\tau_n\uparrow\infty$, we obtain $\mathbb{E}(M^2_{S})\le\mathbb{E}(\langle M\rangle_{S})$. If $S=\infty$, the definition is given by $M^2_\infty=\varliminf_{t\to\infty}M^2_t$.

> [!question]
> Employ the localization technique used in the solution of Problem 5.17 to establish the following extension of Problem 5.12: If $X \in \mathcal{M}^{c, \text{loc}}$, and for some stopping time $T$ of $\{ \mathcal{F}_t \}$ we have $\langle X \rangle_T = 0$ a.s. $\mathbb{P}$, then
> $$
> P[X_{T \wedge t} = 0; \, \forall 0 \leq t < \infty] = 1.
> $$
> In particular, every $X \in \mathcal{M}^{c, \text{loc}}$ of bounded first variation is identically equal to zero.

> [!done]
> 

> [!question]
> Let $M = \{M_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be a process in $\mathcal{M}_2 \cup \mathcal{M}^{c,\text{loc}}$ and assume that its quadratic variation process $\langle M \rangle$ is integrable: $\mathbb{E}\langle M \rangle_{\infty} < \infty$. Then:
> 4. $M$ is a martingale, and $M$ and the submartingale $M^2$ are both uniformly integrable; in particular, $M_{\infty} = \lim_{t \to \infty} M_t$ exists a.s. $\mathbb{P}$, and $\mathbb{E} M_{\infty}^2 = \mathbb{E}\langle M \rangle_{\infty}$;
> 5. we may take a right-continuous modification of $Z_t = \mathbb{E}(M_{\infty}^2 | \mathcal{F}_t) - M_t^2$; $t \geq 0$, which is a potential.

^e5c0a3

> [!done] Done for 1
> If $M\in\mathcal{M}_2$, it is trivial. If $M\in\mathcal{M}^{c,loc}$, there exists $T_n\uparrow\infty$ s.t $M_{t\wedge T_n}$ be a martingale and thus $M^2_{t\wedge T_n}-\langle M\rangle_{t\wedge T_n}$ is a martingale. Then we have 
> $$
> \mathbb{E}[M^2_{t\wedge T_n}]=\mathbb{E}[\langle M\rangle_{t\wedge T_n}]\le\mathbb{E}\langle M\rangle_{\infty}<\infty
> $$
> Since $\langle M\rangle_{t\wedge T_n}\uparrow\langle M\rangle_t$, by MCT, $\mathbb{E}\langle M\rangle_{t\wedge T_n}\to\mathbb{E}\langle M\rangle_{t}$. Then by Fatou's lemma, 
> $$
> \mathbb{E}[M^2_t]\le\varliminf_{n\to\infty}\mathbb{E}[\langle M\rangle_{t\wedge T_n}]=\mathbb{E}\langle M\rangle_{t}\le\mathbb{E}\langle M\rangle_{\infty}<\infty
> $$
> Hence, $M_t\in L^2$ and thus $M_{t\wedge T_n}\xrightarrow{L^2}M_t$. Then 
> $$
> \mathbb{E}[M_{t\wedge T_n}|\mathcal{F}_{s}]=M_{s\wedge T_n}\Longrightarrow\mathbb{E}[M_{t}|\mathcal{F}_{s}]=M_{s}
> $$
> Hence, $M$ is a martingale.
> By [[Continuous-Time Martingales#^f35afc|Doob's maximal inequality]], 
> $$
> \mathbb{E}[\sup_{0\le t\le T}M^2_t]\le4\mathbb{E}[M^2_T]\le4\sup_{0\le t\le T}\mathbb{E}M^2_t\le 4\mathbb{E}\langle M\rangle_{\infty}
> $$
> Then $M^2$ is u.i.

> [!note]
> A method to prove u.i.: to prove $\mathbb{E}[\sup_{0\le t\le T}M_t]<\infty$. THe reason is that there exists $K>0$ s.t. $\mathbb{E}[\sup_{0\le t\le T}M_t\mathbb{1}_{\{|M_t|\ge K\}}]<\varepsilon$. We have 
> $$
> \sup_{0\le t\le T}\mathbb{E}[|M_t|\mathbb{1}_{\{|M_t|\ge K\}}]\le\mathbb{E}[\sup_{0\le t\le T}M_t\mathbb{1}_{\{|M_t|\ge K\}}]<\varepsilon
> $$

> [!done] Done for 2
> Since $M_t\xrightarrow{a.s.}M_\infty\Longrightarrow M_t\xrightarrow{L^2}M_\infty$, then $\mathbb{E}(Z_t)=\mathbb{E}(M_\infty)-\mathbb{E}(M^2_t)\to0$ as $t\to\infty$. Hence, $Z_t$ is a potential.

> [!question]
> Let $M \in \mathcal{M}^{c,\text{loc}}$ and show that for any stopping time $T$ of $\{ \mathcal{F}_t \}$,
> 
> $$
> \mathbb{P}\left[ \max_{0 \leq t \leq T} |M_t| \geq \epsilon \right] \leq \frac{\mathbb{E}(\delta \wedge \langle M \rangle_T)}{\epsilon^2} + \mathbb{P}[\langle M \rangle_T \geq \delta],
> $$
> 
> $\forall \epsilon > 0, \delta > 0$. In particular, for a sequence $\{ M^{(n)} \}_{n=1}^\infty \subseteq \mathcal{M}^{c,\text{loc}}$ we have
> 
> $$
> \langle M^{(n)} \rangle_T \xrightarrow{n \to \infty} 0 \implies \max_{0 \leq t \leq T} |M_t^{(n)}| \xrightarrow{n \to \infty} 0.
> $$

^58ac04

> [!done]
> Let $M^*_T\triangleq\max_{0\le t\le T}|M_t|$, note that 
> $$
> \mathbb{P}\left[M^*_T\ge \varepsilon\right]\le\mathbb{P}\left[M^*_T\ge \varepsilon,\langle M\rangle_T<\delta\right]+\mathbb{P}[\langle M\rangle_T\ge\delta]
> $$
> It suffices to show $\mathbb{P}\left[M^*_T\ge \varepsilon,\langle M\rangle_T<\delta\right]\le\frac{\mathbb{E}(\delta \wedge \langle M \rangle_T)}{\epsilon^2}$. We recall the [[The Doob-Meyer Decomposition#^f31d9e|Exercise]] and let $X_t=M^2_t,A_t=\langle M\rangle_t$. Since $M\in\mathcal{M}^{c,loc}$, there exists $T_n\uparrow\infty$ s.t. $M^2_{t\wedge T_n}-\langle M\rangle_{t\wedge T_n}$ be a martingale. Then for any bounded stopping time $T$, we have 
> $$
> \mathbb{E}[M^2_{t\wedge T_n}]=\mathbb{E}[\langle M\rangle_{t\wedge T_n}]\Longrightarrow\mathbb{E}[M^2_{T\wedge T_n}]=\mathbb{E}[\langle M\rangle_{T\wedge T_n}]
> $$
> Note that $M^2_{T\wedge T_n}\to M^2_{T}$ as $T_n\to\infty$, by Fatou's lemma, we obtain,
> $$
> \begin{align}
> \mathbb{E}[M^2_T]=\mathbb{E}[\varliminf_{n\to\infty}M^2_{T\wedge T_n}]\le\varliminf_{n\to\infty}\mathbb{E}[M^2_{T\wedge T_n}]=\varliminf_{n\to\infty}\mathbb{E}[\langle M\rangle_{T\wedge T_n}]=\mathbb{E}[\langle M\rangle_{T}]
> \end{align}
> $$
> By the [[The Doob-Meyer Decomposition#^f31d9e|Exercise]], we obtain
> $$
> \mathbb{P}\left[M^*_T\ge\varepsilon,\langle M\rangle_T<\delta\right]=\mathbb{P}\left[\max_{0\le t\le T}M^2_t\ge\varepsilon^2,\langle M\rangle_T<\delta\right]\le\frac{\mathbb{E}[\delta\wedge \langle M\rangle_T]}{\varepsilon^2}
> $$
> Above all, 
> $$
> \mathbb{P}\left[M^*_T\ge \varepsilon\right]\le\frac{\mathbb{E}[\delta\wedge \langle M\rangle_T]}{\varepsilon^2}+\mathbb{P}[\langle M\rangle_T\ge\delta]
> $$

> [!question]
> Let $\{M_t, \mathcal{F}_t; 0 \leq t < \infty\}$ and $\{N_t, \mathcal{G}_t; 0 \leq t < \infty\}$ on $(\Omega, \mathcal{F}, \mathbb{P})$ be continuous local martingales relative to their respective filtrations, and assume that $\mathcal{F}_\infty$ and $\mathcal{G}_\infty$ are independent. With $\mathcal{H}_t \triangleq \sigma(\mathcal{F}_t \cup \mathcal{G}_t)$, show that $\{M_t, \mathcal{H}_t; 0 \leq t < \infty\}$, $\{N_t, \mathcal{H}_t; 0 \leq t < \infty\}$ and $\{M_t N_t, \mathcal{H}_t; 0 \leq t < \infty\}$ are local martingales. If we define $\tilde{\mathcal{H}_t} = \bigcap_{s > t} \sigma(\mathcal{H}_s \cup \mathcal{N})$, where $\mathcal{N}$ is the collection of $\mathbb{P}$-negligible events in $\mathcal{F}$, then the filtration $\{\mathcal{H}_t\}$ satisfies the usual conditions, and relative to it the processes $M$, $N$ and $MN$ are still local martingales. In particular, $\langle M, N \rangle \equiv 0$.

> [!done]
> Since $M,N$ are local martingale, there exists $T_n$ is $\mathcal{F}_t$-stopping time and $S_n$ is $\mathcal{G}_t$-stopping time s.t. $M_{t\wedge T_n},N_{t\wedge S_n}$ are martingale. Since $\mathcal{F}_t,\mathcal{G}_t\subseteq\mathcal{H}_t$ for $t\ge0$ and $\mathcal{F}_{\infty}\bot\mathcal{G}_\infty$, we have $M^{t\wedge T_n}$ is independent with $\mathcal{G}_s$ for $s<t$. Then by independence, we obtain
> $$
> \mathbb{E}[M_{t\wedge T_n}|\mathcal{H}_s]=\mathbb{E}[M_{t\wedge T_n}|\mathcal{F}_s]=M_{s\wedge T_n}
> $$
> Similarly, we also obtain $N_{t\wedge S_n}$ is a $\mathcal{H}_t$-martingale. Take $H_n=T_n\wedge S_n\uparrow\infty$ as $n\to\infty$, $M_{t\wedge H_n}$ is $\mathcal{F}_t$-martingale and $N_{t\wedge H_n}$ is $\mathcal{G}_t$-martingale. Then we obtain
> $$
> \mathbb{E}[M_{t\wedge H_n}N_{t\wedge H_n}|\mathcal{H}_s]=\mathbb{E}[M_{t\wedge H_n}|\mathcal{F}_s]\mathbb{E}[N_{t\wedge H_n}|\mathcal{G}_s]=M_{s\wedge H_n}N_{s\wedge H_n}
> $$
