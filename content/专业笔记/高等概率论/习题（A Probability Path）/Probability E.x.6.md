> [!question] 1.(a)
> Let $\{X_n\}$ be a monotone sequence of random variables. If
> 
> $$
> X_n \xrightarrow{P} X
> $$
> 
> then
> 
> $$
> X_n \xrightarrow{\text{a.s.}} X.
> $$
> 
> ^8562ab

> [!done]
> Since $X_n\xrightarrow{\mathbb{P}}X$, there exists a subsequence $X_{n_k}$ s.t. $X_{n_k}\xrightarrow{a.s.}X$. Since $X_n$ is monotone, the sequence has the same limit with subsequence. Hence, $X_n\xrightarrow{a.s.}X$.

> [!question] 1.(b)
> (b) Let $\{X_n\}$ be any sequence of random variables. Show that
> 
> $$
> X_n \xrightarrow{\text{a.s.}} X
> $$
> 
> iff
> 
> $$
> \sup_{k \geq n} |X_k - X| \xrightarrow{P} 0.
> $$

> [!done]
> $\Longrightarrow$: Let $Y_n=\sup_{k\ge n}|X_k-X|$. Since $X_n\xrightarrow{a.s.}X\Longrightarrow X_n\xrightarrow{\mathbb{P}}X$. For any $\varepsilon>0$, note that $\{Y_n>\varepsilon\}\subseteq\{|X_n-X|>\varepsilon\}$, then 
> $$
> \mathbb{P}(Y_n>\varepsilon)\le\mathbb{P}(|X_n-X|>\varepsilon)\to0
> $$
> Hence, $Y_n\xrightarrow{\mathbb{P}}0$
> $\Longleftarrow$: Note that $Y_n$ is monotone, by [[#^8562ab|E.x.(a)]], $Y_n\xrightarrow{a.s.}0$. Hence, $|X_n-X|\xrightarrow{a.s.}0\Longrightarrow X_n\xrightarrow{a.s.}X$

> [!question] 1.(c)
> Points are chosen at random on the circumference of the unit circle. $Y_n$ is the arc length of the largest arc not containing any points when $n$ points are chosen. Show $Y_n \to 0, a.s.$

> [!done]
> (To be completed)

> [!question] 1.(d)
> Let $\{X_n\}$ be i.i.d. with common distribution $F(x)$ which satisfies $F(x_0) = 1$, $F(x) < 1$ for $x < x_0$ with $x_0 < \infty$. Prove
> $$
> \max\{X_1, \ldots, X_n\} \uparrow x_0
> $$
> almost surely.

> [!done]
> We consider the distribution of $Y_n=\max\{X_1,\cdots,X_n\}$ first. It is a elementary exercise. The result is $F_Y(x)=[F(x)]^n$.For $\forall\varepsilon>0$, let set $A_n=\{|Y_n-x_0|>\varepsilon\}$.
> $$
> \begin{align}
> \mathbb{P}(A_n)=\mathbb{P}(|Y_n-x_0|>\varepsilon)&=1-\mathbb{P}(|Y_n-x_0|\le\varepsilon)\\
> &=1-[[F(x_0+\varepsilon)]^n-[F(x_0-\varepsilon)]^n]\\
> &=[F(x_0-\varepsilon)]^n<1
> \end{align}
> $$
> Then $\sum_{n=1}^{\infty}\mathbb{P}(A_n)=\sum_{n=1}^{\infty}[F(x_0-\varepsilon)]^n<1$. By Borel-Cantelli lemma, we obtain$\mathbb{P}(A_n,i.o.)=0$. Hence, $Y_n\xrightarrow{a.s.}x_0$.

> [!question] 2
> Let $\{X_n\}$ be i.i.d, $\mathbb{E}X_n = \mu$, $\operatorname{Var}(X_n) = \sigma^2$. Set $\bar{X} = \sum_{i=1}^n X_i / n$. Show
> 
> $$
> \frac{1}{n} \sum_{i=1}^n (X_i - \bar{X})^2 \xrightarrow{P} \sigma^2.
> $$

> [!done]
> By convergence of statistic, $\bar{X}\xrightarrow{\mathbb{P}}\mu$, $\frac{1}{n}\sum_{i=1}^{n}X^{2}_i\xrightarrow{\mathbb{P}}\mathbb{E}(X^2)=\sigma^2+\mu^2$. Besides, we have 
> $$
> \begin{align}
> \frac{1}{n} \sum_{i=1}^n (X_i - \bar{X})^2=\frac{1}{n} \sum_{i=1}^n (X^2_i - 2X_i\bar{X}+\bar{X}^2)=\frac{1}{n}\sum_{i=1}^{n}X^2_i-\bar{X}^2
> \end{align}
> $$
> Hence, by properties of convergence in probability, we obtain
> $$
> \frac{1}{n} \sum_{i=1}^n (X_i - \bar{X})^2\xrightarrow{\mathbb{P}}\sigma^2+\mu^2-\mu^2=\sigma^2
> $$

> [!question] 3(a)
> Suppose $X \ge 0$ and $Y \ge 0$ are random variables and that $p \ge 0$.Prove 
> $$
> \mathbb{E}(X+Y)^p\le 2^{p}(\mathbb{E}(X^p)+\mathbb{E}(Y^p))
> $$

> [!done]
> Since $X,Y\ge0$, $$X+Y\le 2\max\{X,Y\}\Longrightarrow (X+Y)^p\le 2^p\max\{X,Y\}^p\le 2^p(X^p+Y^p)$$

> [!question] 3(b)
> If $p>1$, the factor $2^p$ can be replaced by $2^{p-1}$

> [!done]
> Let $\frac{1}{p}+\frac{1}{q}=1$. By Holder's inequality, 
> $$
> (X+Y)=(X\cdot1+Y\cdot1)\le(X^p+Y^p)^{\frac{1}{p}}(1^q+1^q)^{\frac{1}{q}}=2^{\frac{1}{q}}(X^p+Y^p)^{\frac{1}{p}}
> $$
> $$
> \Longrightarrow (X+Y)^p\le 2^{\frac{p}{q}}(X^p+Y^p)=2^{p-1}(X^p+Y^p)
> $$
> Take expectation and obtain the result.

> [!question] 3(c)
> If $0\le p\le 1$, the factor $2^p$ may be replaced by 1.

> [!done]
> Since $(X+Y)^p\le (X^p+Y^p)$ when $0\le p\le 1$.

> [!question] 4
> Let $\{X_n, n \geq 1\}$ be iid, $\mathbb{E} X_n = 0$, $\mathbb{E} X_n^2 = \sigma^2$. Let $a_n \in \mathbb{R}$ for $n \geq 1$. Set  
> $$
> S_n = \sum_{i=1}^n a_i X_i.
> $$
> Prove $\{S_n\}$ is $L_2$-convergent iff $\sum_{i=1}^\infty a_i^2 < \infty$.

> [!done]
> Since 
> $$
> \begin{align}
> \mathbb{E}S^2_n=\mathbb{E}\left(\sum_{i=1}^{n}a_iX_i\right)^2&=\mathbb{E}\left(\sum_{i=1}^{n}a_i^2X^2_i+2\sum_{i<j}a_ia_jX_iX_j\right)\\
> &=\sum_{i=1}^{n}a^2_i\mathbb{E}X_i^2=\sigma^2\sum_{i=1}^{n}a^2_i
> \end{align}
> $$

> [!question] 5
> Suppose $\{X_n\}$ is iid. Show $\{\frac{S_n}{n}, n \geq 1\}$ is uniformly integrable provided $X_i \in L^1$.

> [!done]
> Since $X_i\in L^1$ and $X_i$ are i.i.d, for $\forall\varepsilon>0$, $\exists K>0$ s.t. $\mathbb{E}|X_i|\mathbb{1}_{\{|X_i|\ge K\}}<\frac{\varepsilon}{2}$. Let $Y_n=\frac{S_n}{n}$. For any $M>0$, 
> $$
> \begin{align}
> \mathbb{E}[|Y_n|\mathbb{1}_{\{|Y_n|\ge M\}}]&\le \frac{1}{n}\mathbb{E}\left[\sum_{i=1}^{n}|X_i|\mathbb{1}_{\{|Y_n|\ge M\}}\right]\\
> &=\frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}(|X_i|\mathbb{1}_{\{|X_i|\ge K\}}\mathbb{1}_{\{|Y_n|\ge M\}})+\mathbb{E}(|X_i|\mathbb{1}_{\{|X_i|<K\}}\mathbb{1}_{\{|Y_n|\ge M\}})\right]
> \end{align}
> $$
> For item1, 
> $$
> \begin{align}
> \mathbb{E}[|X_i|\mathbb{1}_{\{|X_i|\ge K\}}\mathbb{1}_{\{|Y_n|\ge M\}}]\le\mathbb{E}[|X_i|\mathbb{1}_{\{|X_i|\ge K\}}]<\frac{\varepsilon}{2} 
> \end{align}
> $$
> For item2, 
> $$
> \begin{align}
> \mathbb{E}(|X_i|\mathbb{1}_{\{|X_i|<K\}}\mathbb{1}_{\{|Y_n|\ge M\}})\le K\mathbb{P}(|Y_n|\ge M)\le \frac{K}{M}\mathbb{E}(|Y_n|)\le \frac{K}{M}\mathbb{E}(|X_1|)
> \end{align}
> $$
> Therefore, we have 
> $$
> \mathbb{E}[|Y_n|\mathbb{1}_{\{|Y_n|\ge M\}}]\le \frac{\varepsilon}{2}+\frac{K}{M}\mathbb{E}|X_1|\Longrightarrow\varlimsup_{M\to\infty}\mathbb{E}[|Y_n|\mathbb{1}_{\{|Y_n|\ge M\}}]\le\varepsilon
> $$
> Hence, $Y_n$ is u.i.
> 
> ^4f8b77

> [!question] 6
> Let $\{X_n\}$ be uniformly integrable and let $X \in L^1$. Show $\{X_n - X\}$ is uniformly integrable.

> [!done]
> Since $|X_n-X|\le |X_n|+|X|$, $|X_n|$ is u.i. and $|X|\in L^1$, then $|X_n|+|X|$ is u.i. refer to [[#^4f8b77|E.x.5]]. Hence, $X_n-X$ is u.i. 

> [!question] 7
> Let $X_n \sim N(0, \sigma_n^2)$. When is $\{X_n\}$ uniformly integrable?

> [!done]
> We calculate $\mathbb{E}[|X_n|\mathbb{1}_{\{|X_n|\ge M\}}]$.
> $$
> \begin{align}
> \mathbb{E}[|X_n|\mathbb{1}_{\{|X_n|\ge M\}}]&=\mathbb{E}|X_n|-\mathbb{E}[|X_n|\mathbb{1}_{\{|X_n|< M\}}]\\
> &=\sqrt{\frac{2}{\pi}}\sigma_n-2\int_{0}^{M}\frac{x}{\sqrt{2\pi}\sigma_n}e^{-\frac{x^2}{2\sigma_n^2}}{d}x\\
> &=\sqrt{\frac{2}{\pi}}\sigma_n-\sqrt{\frac{2}{\pi}}\sigma_n(1-e^{-\frac{M^2}{2\sigma_n^2}})=\sqrt{\frac{2}{\pi}}\sigma_ne^{-\frac{M^2}{2\sigma_n^2}}
> \end{align}
> $$
> If $\sigma_n$ exists a subsequence $n_k$ s.t $\sigma_{n_k}\to\infty$, for fixed $M>0$, $\sup_{n\ge1}\mathbb{E}[|X_n|\mathbb{1}_{\{|X_n|\ge M\}}]=\infty$. Hence, we need $\sup_{n\ge1}\sigma_n<\infty$, then we obtain$\lim_{M\to\infty}\mathbb{E}[|X_n|\mathbb{1}_{\{|X_n|\ge M\}}]=0$.

> [!question] 8
> Suppose $\{X_n\}$ and $\{Y_n\}$ are two families of uniformly integrable random variables defined on the same probability space. Is $\{X_n + Y_n\}$ uniformly integrable?

> [!done]
> $X_n+Y_n$ is u.i. 

> [!question] 9
> When is there equality in the Schwarz Inequality? (Examine the derivation of the Schwarz Inequality.)

> [!question] 10
> Suppose $\{X_n\}$ is a sequence for which there exists an increasing function $f:[0,\infty)\mapsto [0,\infty)$ such that $f(x)/x \to \infty$ as $x\to \infty$ and
> 
> $$
> \sup_{n\geq 1} \mathbb{E}(f(|X_n|)) < \infty.
> $$
> 
> Show $\{X_n\}$ is uniformly integrable.
> 
> Specialize to the case where $f(x) = x^p$ for $p > 1$ or $f(x) = x(\log x)^+$.

> [!done]
> Let $C\triangleq\sup_{n\geq 1} \mathbb{E}(f(|X_n|))$. Since $\frac{f(x)}{x}\to\infty$ as $x\to\infty$ i.e. $\forall\varepsilon>0,\exists M_0>0$ s.t. $x>M_0$, we have $\frac{f(x)}{x}>\frac{C}{\varepsilon}\Longrightarrow x<\frac{\varepsilon}{C} f(x)$. Take $M\ge M_0$, 
> $$
> \begin{align}
> \mathbb{E}[|X_n|\mathbb{1}_{\{|X_n|\ge M\}}]\le \frac{\varepsilon}{C}\mathbb{E}[f(|X_n|)\mathbb{1}_{\{|X_n|\ge M\}}]\le\frac{\varepsilon}{C}\cdot C=\varepsilon
> \end{align}
> $$
> Hence, $X_n$ is u.i.

> [!question] 11(a)
> Suppose $\{X_n, n \geq 1\}$ are iid and non-negative and define $M_n = \max_{1\le i\le n} X_i$.
> 
> Check that
> 
> $$
> P[M_n > x] \leq n P[X_1 > x].
> $$
> 
> ^9c2892

> [!done]
> We have 
> $$
> \begin{align}
> \mathbb{P}[M_n>x]=1-\mathbb{P}[M_n\le x]&=1-(\mathbb{P}[X_1\le x])^n
> \end{align}
> $$
> Let $t=\mathbb{P}[X_1>x]\le 1$, we W.T.S. $1-(1-t)^n\le nt$. Let $f(t)=(1-t)^n+nt-1$, $f'(t)=-n(1-t)^{n-1}+n=n(1-(1-t)^{n-1})\ge 0$. Therefore, $f(t)$ is increasing, then $f(t)\ge f(0)=0$. Hence, 
> $$
> \mathbb{P}[M_n>x]\le 1-(\mathbb{P}[X_1\le x])^n\le n\mathbb{P}(X_1>x)
> $$

> [!question] 11(b)
> If $\mathbb{E}(X_1^p) < \infty$, then $M_n / n^{1/p} \xrightarrow{P} 0$.

> [!done]
> By [[#^9c2892|E.x.11(a)]], $\forall\varepsilon>0$, 
> $$
> \mathbb{P}\left(\frac{M_n}{n^{\frac{1}{p}}}\ge\varepsilon\right)=\mathbb{P}\left(M_n\ge\varepsilon n^{\frac{1}{p}}\right)\le n\mathbb{P}(X^p_1\ge\varepsilon^pn)
> $$
> Now we prove the tail probability property. In fact, 
> $$
> n\mathbb{P}(X_1^p\ge\varepsilon^pn)=\int_{\{X_1^p\ge\varepsilon^pn\}}n{d}\mathbb{P}\le \frac{1}{\varepsilon^p}\int_{\{X_1^p\ge\varepsilon^pn\}}X_1^p{d}\mathbb{P}=\frac{1}{\varepsilon^p}\mathbb{E}(X_1^p\mathbb{1}_{\{X_1^p\ge \varepsilon^pn\}})
> $$
> Since $\mathbb{E}[X_1^p]<\infty$, then $\mathbb{E}(X_1^p\mathbb{1}_{\{X_1^p\ge \varepsilon^pn\}})\to0$ as $n\to\infty$. Hence, $\frac{M_n}{n^{\frac{1}{p}}}\to0$

> [!question] 11(c)
> If in addition to being iid, the sequence $\{X_n\}$ is non-negative, show
> 
> $$
> M_n / n \xrightarrow{P} 0 \quad \text{iff} \quad n P[X_1 > n] \to 0, \text{ as } n \to \infty.
> $$

> [!done]
> $\Longleftarrow$: It is trivial by [[#^9c2892|E.x.11(a)]].
> $\Longrightarrow$: We have 
> $$
> \begin{align}
> n\mathbb{P}(X_1>n)&=n\int_{\{X_1>n\}}{d}\mathbb{P}\le\int_{\{X_1>n\}}X_1{d}\mathbb{P}\\
> &=\mathbb{E}X_1\mathbb{1}_{\{X_1>n\}}
> \end{align}
> $$
> Since $X_1>n\Longrightarrow M_n>n$, $\{X_1>n\}\subseteq\{M_n>n\}$. Therefore, $\mathbb{E}X_1\mathbb{1}_{\{X_1>n\}}\le\mathbb{E}X_1\mathbb{1}_{\{M_n>n\}}$. Since $\frac{M_n}{n}\xrightarrow{\mathbb{P}}0$, $\mathbb{P}(\frac{M_n}{n}>1)\to0$ as $n\to\infty$. Then $\mathbb{E}X_1\mathbb{1}_{\{M_n>n\}}\to0$ as $n\to\infty$. Hence, $n\mathbb{P}(X_1>n)\to0$ as $n\to\infty$.

> [!question] 11(d)
> Review the definition of rapid variation in Exercise 27 of Chapter 5. Prove there exists a sequence $b(n) \to \infty$ such that
> 
> $$
> M_n / b(n) \xrightarrow{P} 1, \quad n \to \infty,
> $$
> 
> iff $1 - F(x) := P[X_1 > x]$ is rapidly varying at $\infty$. In this case, we may take
> 
> $$
> b(n) = \left(\frac{1}{1-F}\right)^{\leftarrow}(n)
> $$
> 
> to be the $1 - \frac{1}{n}$ quantile of $F$.
> ![[Pasted image 20260327192301.png]]

> [!done]
> $\Longrightarrow$: (To be completed)
> $\Longleftarrow$: (To be completed)

> [!question] 11(e)
> Now suppose $\{X_n\}$ is an arbitrary sequence of non-negative random variables. Show that
> 
> $$
> \mathbb{E}(M_n 1_{[M_n \geq \delta]}) \leq \sum_{k=1}^n \mathbb{E}(X_k 1_{[X_k \geq \delta]}).
> $$
> 
> If in addition, $\{X_n\}$ is uniformly integrable, show $\mathbb{E}(M_n)/n \to 0$.

> [!done]
> There exists $1\le j\le n$ s.t. $X_j\mathbb{1}_{\{|X_j|\ge\delta\}}=M_n\mathbb{1}_{\{|M_n|\ge\delta\}}$. Then 
> $$
> M_n\mathbb{1}_{\{|M_n|\ge\delta\}}\le \sum_{k=1}^{n}X_k\mathbb{1}_{\{|X_k|\ge\delta\}}
> $$
> Take expectation, we obtain the inequality. If $X_n$ is u.i. we choose sufficiently large $\delta$ s.t. $\sup_{k\ge1}\mathbb{E}[X_k\mathbb{1}_{\{|X_k|\ge\delta\}}]<\varepsilon$. Then 
> $$
> \begin{align}
> \frac{\mathbb{E}[M_n]}{n}=\frac{\mathbb{E}[M_n]\mathbb{1}_{\{|M_n|\ge\delta\}}+\mathbb{E}[M_n]\mathbb{1}_{\{|M_n|\ge\delta\}}}{n}\le\frac{\delta}{n}+\frac{1}{n}\sum_{k=1}^{n}\mathbb{E}[X_k\mathbb{1}_{\{|X_k|\ge\delta\}}]
> \end{align}
> $$
> For large $n$, $\frac{\delta}{n}<\varepsilon$. Hence, we have 
> $$
> \frac{\mathbb{E}[M_n]}{n}<2\varepsilon\Longrightarrow\lim_{n\to\infty}\frac{\mathbb{E}[M_n]}{n}=0
> $$

> [!question] 12(a)
> Let $\{X_n\}$ be a sequence of random variables. If $X_n\xrightarrow{\mathbb{P}}0$, then for any $p>0$
> $$
> \frac{|X_n|^p}{1+|X_n|^p}\xrightarrow{\mathbb{P}}0
> $$
> and 
> $$
> \mathbb{E}\left[\frac{|X_n|^p}{1+|X_n|^p}\right]\to0
> $$

> [!done]
> We only prove the second claim because the first claim can be obtain by Chebyshev's inequality. 
> For any $\varepsilon>0$, we have 
> $$
> \mathbb{E}\left[\frac{|X_n|^p}{1+|X_n|^p}\right]=\int_{\{|X_n|\ge\varepsilon\}}\frac{|X_n|^p}{1+|X_n|^p}{d}\mathbb{P}+\int_{\{|X_n|<\varepsilon]\}}\frac{|X_n|^p}{1+|X_n|^p}{d}\mathbb{P}
> $$
> Let function $\varphi(x)=\frac{x^p}{1+x^p}$ for $x>0$. $\varphi'(x)=\frac{px^{p-1}}{(1+x^p)^2}>0$ and thus $\varphi(x)$ is increasing. Since $X_n\xrightarrow{\mathbb{P}}0$, $\mathbb{P}(|X_n|\ge\varepsilon)\to0$ and $\mathbb{P}(|X_n|<\varepsilon)\to1$. For the second item, we have $\frac{|X_n|^p}{1+|X_n|^p}\le\frac{\varepsilon^p}{1+\varepsilon^p}$. Then 
> $$
> \mbox{item2}\le\frac{\varepsilon^p}{1+\varepsilon^p}\mathbb{P}(|X_n|<\varepsilon)\to\frac{\varepsilon^p}{1+\varepsilon^p}
> $$
> For the first item, 
> $$
> \mbox{item1}\to0\mbox{ since }\mathbb{P}(|X_n|\ge\varepsilon)\to0
> $$
> Above all, we obtain
> $$
> \varlimsup_{n\to\infty}\mathbb{E}\left[\frac{|X_n|^p}{1+|X_n|^p}\right]\le\frac{\varepsilon^p}{1+\varepsilon^p}
> $$
> Let $\varepsilon\to0$, we obtain the second claim.

> [!question] 12(b)
> If for some $p > 0$ (6.21) holds, then $X_n \xrightarrow{\mathbb{P}} 0$.

> [!done]
> For any $\varepsilon>0$, we have $\frac{|X_n|^p}{1+|X_n|^p}\ge\frac{\varepsilon^p}{1+\varepsilon^p}$ on the event $\{|X_n|\ge\varepsilon\}$. Then 
> $$
> \begin{align}
> \mathbb{P}(|X_n|\ge\varepsilon)&=\int_{\{|X_n|\ge\varepsilon\}}{d}\mathbb{P}=\frac{1+\varepsilon^p}{\varepsilon^p}\int_{\{|X_n|\ge\varepsilon\}}\frac{\varepsilon^p}{1+\varepsilon^p}{d}\mathbb{P}\\
> &\le\frac{1+\varepsilon^p}{\varepsilon^p}\int_{\{|X_n|\ge\varepsilon\}}\frac{|X_n|^p}{1+|X_n|^p}{d}\mathbb{P}\\
> &\le\frac{1+\varepsilon^p}{\varepsilon^p}\int_{\{\frac{|X_n|^p}{1+|X_n|^p}\ge\frac{\varepsilon^p}{1+\varepsilon^p}\}}\frac{|X_n|^p}{1+|X_n|^p}{d}\mathbb{P}\to0\mbox{ as }n\to\infty
> \end{align}
> $$

> [!question] 12(c)
> Suppose $p > 0$. Show $X_n \xrightarrow{\mathbb{P}} 0$ iff (6.22).

> [!done]
> $\Longrightarrow$: It is done by 12(a)
> $\Longleftarrow$: (6.22)$\Longrightarrow$(6.21)$\Longrightarrow X_n\xrightarrow{\mathbb{P}}0$

> [!question] 13
> Suppose ${X_n,n≥1}$ are identically distributed with finite variance. Show that
> $$
> n\mathbb{P}\big(|X_1| \ge \varepsilon \sqrt{n}\big) \to 0
> $$
> and
> $$
> \frac{\bigvee_{i=1}^n |X_i|}{\sqrt{n}} \xrightarrow{P} 0
> $$

> [!done]
> For $\varepsilon>0$, we have
> $$
> \begin{align}
> \mathbb{P}\left(\frac{\bigvee_{i=1}^n |X_i|}{\sqrt{n}}>\varepsilon\right)&=\mathbb{P}\left(\bigvee_{i=1}^n |X_i|>\sqrt{n}\varepsilon\right)\\
> &=1-\mathbb{P}\left(\bigvee_{i=1}^n |X_i|\le\sqrt{n}\varepsilon\right)\\
> &=1-\left[1-\mathbb{P}\left(|X_i|>\sqrt{n}\varepsilon\right)\right]^n\\
> &\le n\mathbb{P}(|X_1|>\sqrt{n}\varepsilon)\to0
> \end{align}
> $$

> [!question] 14
> Suppose $\{X_k\}$ are independent with $$ \mathbb{P}(X_k = k^2) = \frac{1}{k^2}, \quad \mathbb{P}(X_k = -1) = 1 - \frac{1}{k^2}. $$ Show that $\sum_{i=1}^n X_i \to -\infty$ almost surely as $n \to \infty$.

> [!done]
> Since $\mathbb{P}(X_k=K^2)=\frac{1}{k^2}$ and thus $\sum_{k=1}^{\infty}\frac{1}{k^2}<\infty$, $\mathbb{P}\{X_k=k^2,i.o.\}=0$. Therefore, there exists $N$ s.t. $k>N$, $X_k=-1$. Then 
> $$
> S_n=\sum_{k=1}^{N}\frac{1}{k^2}+\sum_{k=N+1}^{n}(-1)=\sum_{k=1}^{N}\frac{1}{k^2}-(n-N)\to-\infty\mbox{ as }n\to\infty
> $$

> [!question] 15
> Suppose $X_n \ge 0$ for $n \ge 0$ and $X_n \xrightarrow{P} X_0$, and also $\mathbb{E}(X_n) \to \mathbb{E}(X_0)$. Show that $X_n \to X_0$ in $L^1$.

> [!done]
> Note that 
> $$
> \begin{align}
> \mathbb{E}|X_n-X_0|&=\mathbb{E}(X_n-X_0)^++\mathbb{E}(X_0-X_n)^+\\
> &=2\mathbb{E}(X_n-X_0)^++\mathbb{E}(X_0-X_n)
> \end{align}
> $$
> Since $\mathbb{E}(X_n)\to\mathbb{E}(X_0)$, $\mathbb{E}(X_0-X_n)\to0$. Since $X_n\xrightarrow{\mathbb{P}}X_0$, $\mathbb{E}(X_n-X_0)^+=\mathbb{P}(X_n-X_0>0)\to0$. Above all, we obtain
> $$
> \mathbb{E}|X_n-X_0|\to0
> $$

> [!question] 16(a)
> For any sequence of random variables ${X_n}$ set $S_n = \sum_{i=1}^{n}X_i$. Show $X_n\xrightarrow{a.s.}0\Longrightarrow\frac{S_n}{n}\xrightarrow{a.s.}0$

> [!done]
> Since $X_n(\omega)\to0\Longrightarrow\frac{S_n(\omega)}{n}\to0$, then $\{\omega:X_n(\omega)\to0\}\subseteq\{\omega:\frac{S_n(\omega)}{n}\to0\}$. we have 
> $$
> 1\le\mathbb{P}\{\omega:\frac{S_n(\omega)}{n}\to0\}\Longrightarrow\frac{S_n(\omega)}{n}\xrightarrow{a.s.}0
> $$

> [!question] 16(b)
> $X_n\xrightarrow{L^p}0\Longrightarrow \frac{S_n}{n}\xrightarrow{L^p}0$ for $p\ge1$

> [!done]
> Since $X_n\xrightarrow{L^p}0$, for $\varepsilon>0$, $\exists N\in\mathbb{N}$ s.t. $n\ge N$, we have $(\mathbb{E}|X_n|^p)^{\frac{1}{p}}<\varepsilon$. For $n\ge N$, 
> $$
> \begin{align}
> \left(\mathbb{E}\left|\frac{S_n}{n}\right|^p\right)^{\frac{1}{p}}&=\frac{1}{n}\left(\mathbb{E}\left|\sum_{k=1}^{n}X_k\right|^p\right)^{\frac{1}{p}}\\
> &\le\frac{1}{n}\sum_{k=1}^{N}(\mathbb{E}|X_k|^p)^{\frac{1}{p}}+\frac{1}{n}\sum_{k=N+1}^{n}(\mathbb{E}|X_k|^p)^{\frac{1}{p}}\\
> &<\frac{1}{n}\sum_{k=1}^{N}(\mathbb{E}|X_k|^p)^{\frac{1}{p}}+\frac{\varepsilon(n-N)}{n}
> \end{align}
> $$
> Then 
> $$
> \varlimsup_{n\to\infty}\left(\mathbb{E}\left|\frac{S_n}{n}\right|^p\right)^{\frac{1}{p}}\le\varepsilon\Longrightarrow\frac{S_n}{n}\xrightarrow{L^p}0
> $$

> [!question] 16(c)
> $X_n\xrightarrow{\mathbb{P}}0$ does not imply $\frac{S_n}{n}\xrightarrow{\mathbb{P}}0$ 

> [!done]
> We construct 
> $$
> \mathbb{P}(X_n=2^n)=\frac{1}{n},\mathbb{P}(X_n=0)=1-\frac{1}{n}
> $$
> For sufficiently large $n$, $2^n>\varepsilon$, 
> $$
> \mathbb{P}(|X_n|>\varepsilon)=\frac{1}{n}\to0\Longrightarrow X_n\xrightarrow{\mathbb{P}}0
> $$
> Fix $M>0$, let set
> $$
> A_n=\{\exists i\in\{1,\cdots,n\} \ s.t.\ X_i=2^i,2^i>nM \}
> $$ 
> Then $A_n\Longrightarrow\frac{S_n}{n}>M$ and $\mathbb{P}(A_n)\le\mathbb{P}(\frac{S_n}{n}>M)$. 
> $$
> \mathbb{P}(A_n)=1-\prod_{i=k}^{n}(1-\frac{1}{i})=1-\frac{k-1}{n}
> $$
> where $k=[\log_2(nM)]+1$. Note that 
> $$
> \mathbb{P}(A_n)\ge1-\frac{[\log_2(nM)]+1]}{n}\to1
> $$
> Then for any $M>0$, 
> $$
> \lim_{n\to\infty}\mathbb{P}(\frac{S_n}{n}>M)=1\Longrightarrow\frac{S_n}{n}\xrightarrow{\mathbb{P}}\infty
> $$

> [!question] 16(d)
> $\frac{S_n}{n}\xrightarrow{\mathbb{P}}0\Longrightarrow\frac{X_n}{n}\xrightarrow{\mathbb{P}}0$

> [!done]
> Note that
> $$
> \frac{X_n}{n}=\frac{S_n}{n}-\frac{S_{n-1}}{n-1}\frac{n-1}{n}\xrightarrow{\mathbb{P}}0
> $$

> [!question] 17
> In a discrete probability space, convergence in probability is equivalent to almost sure convergence.

> [!done]
> It is trivially that almost sure convergence implies convergence in probability. We prove the another direction. Suppose $\omega\in\Omega$ and $\mathbb{P}(\{\omega\})>0$ and r.v. $X_n\xrightarrow{\mathbb{P}}X$. Note that $\{\omega\}\subseteq\{\omega:|X_n(\omega)-X(\omega)|>\varepsilon\}$ for fixed $\varepsilon>0$, we have 
> $$
> \mathbb{P}(|X_n-X|>\varepsilon)\ge\mathbb{P}(\{\omega\})
> $$
> But $\mathbb{P}(|X_n-X|>\varepsilon)\to0$ as $n\to\infty$, it is a contradiction! Hence, $\omega\in\{\omega:|X_n-X|<\varepsilon\}$ which imply $X_n\xrightarrow{a.s.}X$. 

> [!question] 18
> Suppose $\{X_n\}$ is an uncorrelated sequence, meaning $$ \operatorname{Cov}(X_i, X_j) = 0, \quad i \ne j. $$ If there exists a constant $c > 0$ such that $\operatorname{Var}(X_n) \le c$ for all $n \ge 1$, then for any $\alpha > 1/2$ we have $$ \frac{\sum_{i=1}^n X_i}{n^\alpha} \xrightarrow{L^2} 0. $$

> [!done]
> We have 
> $$
> \begin{align}
> \mathbb{E}\left[\frac{\sum_{i=1}^{n}X_i}{n^\alpha}\right]^2&=\mathbb{E}\left[\frac{\sum_{i=1}^{n}X^2_i+\sum_{i\ne j}X_iX_j}{n^{2\alpha}}\right]\\
> &=\frac{\sum_{i=1}^{n}\mathbb{E}X_i^2+\sum_{i\ne j}\mathbb{E}(X_iX_j)}{n^{2\alpha}}\\
> &\le\frac{nc+(\sum_{i=1}^{n}\mathbb{E}(X_i))^2}{n^{2\alpha}}\to0\tag{$2\alpha>1$}
> \end{align}
> $$

> [!question] 19
> If $0\le X_n\le Y_n$ and $Y_n\xrightarrow{\mathbb{P}}0$, then $X_n\xrightarrow{\mathbb{P}}0$

> [!done]
> Note that for $\varepsilon>0$,
> $$
> \{X_n\ge\varepsilon\}\subseteq\{Y_n\ge\varepsilon\}
> $$

> [!question] 20
> Suppose $E(X^2) = 1$ and $E(|X|) \geq a > 0$. Prove for $0 \leq \lambda \leq 1$ that $$ P[|X| \geq \lambda a] \geq (1 - \lambda)^2 a^2. $$

> [!done]
> By $\mathbb{E}|X|\ge a$, $\mathbb{P}[|X|\ge\lambda a]\ge\mathbb{P}[|X|\ge\lambda$