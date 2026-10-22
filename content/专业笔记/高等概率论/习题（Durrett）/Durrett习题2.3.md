> [!question] 2.3.4.
> **Fatou's lemma.** Suppose $X_n \geq 0$ and $X_n \to X$ in probability. Show that $\liminf_{n \to \infty} \mathbb{E}X_n \geq \mathbb{E}X$.

> [!done]
> There exists further subsequence $X_{n(m_k)}\xrightarrow{a.s.}X$. Then 
> $$
> \mathbb{E}X\le \liminf_{k\to\infty}\mathbb{E}X_{n(m_k)}=\liminf_{n\to\infty}\mathbb{E}X_n
> $$

> [!question] 2.3.5.
> **Dominated convergence.** Suppose $X_n \to X$ in probability and (a) $|X_n| \leq Y$ with $\mathbb{E}Y < \infty$ or (b) there is a continuous function $g$ with $g(x) > 0$ for large $x$ with $|x|/g(x) \to 0$ as $|x| \to \infty$ so that $\mathbb{E}g(X_n) \leq C < \infty$ for all $n$. Show that $\mathbb{E}X_n \to \mathbb{E}X$.

> [!done]
> For case (a), we have obtained [[Fubini定理及其应用#^fd31fb|the result]]. We only consider the case (b). 

> [!question] 2.3.6.Metric for convergence in probability.(a) 
>  Show that $d(X,Y) = \mathbb{E}(|X-Y|/(1+|X-Y|))$ defines a metric on the set of random variables, i.e., (i) $d(X,Y) = 0$ if and only if $X = Y$ a.s., (ii) $d(X,Y) = d(Y,X)$, (iii) $d(X,Z) \leq d(X,Y) + d(Y,Z)$. 

> [!done]
> For (iii), note that de function $\frac{x}{1+x}$ is [[Durrett习题2.1#^9fde07|increasing]]. Since $|\cdot|$ is a metric, we have 
> $$
> |X-Z|\le|X-Y|+|Y-Z|\Longrightarrow\frac{|X-Z|}{1+|X-Z|}\le\frac{|X-Y|}{1+|X-Y|}+\frac{|Y-Z|}{1+|Y-Z|}
> $$

>[!question] 2.3.6.Metric for convergence in probability.(b)
>Show that $d(X_n,X) \to 0$ as $n \to \infty$ if and only if $X_n \to X$ in probability. 

>[!done] 
>$\Longrightarrow:$ Since $d(X_n,X)\to0$ i.e. 
>$$
>\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}\to0\text{ as }n\to\infty
>$$
>Then for any $\varepsilon>0$, we have 
>$$
>\begin{aligned}
>\mathbb{P}(|X_n-X|\ge\varepsilon)&=\int_{\{|X_n-X|\ge\varepsilon\}}1d\mathbb{P}\\
>&=\int_{\{|X_n-X|\ge\varepsilon\}}\frac{|X_n-X|}{1+|X_n-X|}\cdot\frac{1+|X_n-X|}{|X_n-X|}{d}\mathbb{P}\\
>&\le \frac{1+\varepsilon}{\varepsilon}\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}\to0
>\end{aligned}
>$$
>Hence, $X_n\xrightarrow{\mathbb{P}}X$. 
>$\Longleftarrow:$ Suppose $X_n\xrightarrow{\mathbb{P}} X$, then for any $\varepsilon>0$
>$$
>\begin{aligned}
>\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}&=\left(\int_{\{|X_n-X|\ge\varepsilon\}}+\int_{\{|X_n-X|<\varepsilon\}}\right)\frac{|X_n-X|}{1+|X_n-X|}{d}\mathbb{P}\\
>&\le\frac{\varepsilon}{1+\varepsilon}+\mathbb{P}(|X_n-X|\ge\varepsilon)
>\end{aligned}
>$$
>We obtain
>$$
>\limsup_{n\to\infty}\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}\le\frac{\varepsilon}{1+\varepsilon}\text{ and }\varepsilon\to0^+
>$$

> [!question] 2.3.7.
> Show that random variables are a complete space under the metric defined in the previous exercise, i.e., if $d(X_m, X_n) \to 0$ whenever $m, n \to \infty$ then there is a r.v. $X_\infty$ so that $X_n \to X_\infty$ in probability.

> [!done]
> 

> [!question] 2.3.8.
> Let $A_n$ be a sequence of independent events with $\mathbb{P}(A_n) < 1$ for all $n$. Show that $\mathbb{P}(\cup A_n) = 1$ implies $\sum_n \mathbb{P}(A_n) = \infty$ and hence $\mathbb{P}(A_n \text{ i.o.}) = 1$.

> [!done]

> [!question] 2.3.9. (i)
> (i) If $\mathbb{P}(A_n) \to 0$ and $\sum_{n=1}^\infty \mathbb{P}(A_n^c \cap A_{n+1}) < \infty$ then $\mathbb{P}(A_n \text{ i.o.}) = 0$.

> [!done]

> [!question] 2.3.9. (ii)
> (ii) Find an example of a sequence $A_n$ to which the result in (i) can be applied but the Borel-Cantelli lemma cannot.

> [!done]

> [!question] 2.3.10.
> **Kochen-Stone lemma.** Suppose $\sum \mathbb{P}(A_k) = \infty$. Use Exercises 1.6.6 and 2.3.1 to show that if
> $$
> \limsup_{n \to \infty} \left( \sum_{k=1}^n \mathbb{P}(A_k) \right)^2 \Bigg/ \left( \sum_{1 \leq j,k \leq n} \mathbb{P}(A_j \cap A_k) \right) = \alpha > 0
> $$
> then $\mathbb{P}(A_n \text{ i.o.}) \geq \alpha$. The case $\alpha = 1$ contains Theorem 2.3.7.

> [!done]

> [!question] 2.3.11. (i)
> Let $X_1, X_2, \dots$ be independent with $\mathbb{P}(X_n = 1) = p_n$ and $\mathbb{P}(X_n = 0) = 1 - p_n$. Show that (i) $X_n \to 0$ in probability if and only if $p_n \to 0$.

> [!done]

> [!question] 2.3.11. (ii)
> (ii) $X_n \to 0$ a.s. if and only if $\sum p_n < \infty$.

> [!done]

> [!question] 2.3.12.
> Let $X_1, X_2, \dots$ be a sequence of r.v.'s on $(\Omega, \mathcal{F}, \mathbb{P})$ where $\Omega$ is a countable set and $\mathcal{F}$ consists of all subsets of $\Omega$. Show that $X_n \to X$ in probability implies $X_n \to X$ a.s.

> [!done]

> [!question] 2.3.13.
> If $X_n$ is any sequence of random variables, there are constants $c_n \to \infty$ so that $X_n/c_n \to 0$ a.s.

> [!done]

> [!question] 2.3.14.
> Let $X_1, X_2, \dots$ be independent. Show that $\sup X_n < \infty$ a.s. if and only if $\sum_n \mathbb{P}(X_n > A) < \infty$ for some $A$.

> [!done]

> [!question] 2.3.15. (i)
> Let $X_1, X_2, \dots$ be i.i.d. with $\mathbb{P}(X_i > x) = e^{-x}$, let $M_n = \max_{1 \leq m \leq n} X_m$. Show that (i) $\limsup_{n \to \infty} X_n / \log n = 1$ a.s.

> [!done]

> [!question] 2.3.15. (ii)
> (ii) $M_n / \log n \to 1$ a.s.

> [!done]

> [!question] 2.3.16.
> Let $X_1, X_2, \dots$ be i.i.d. with distribution $F$, let $\lambda_n \uparrow \infty$, and let $A_n = \{\max_{1 \leq m \leq n} X_m > \lambda_n\}$. Show that $\mathbb{P}(A_n \text{ i.o.}) = 0$ or $1$ according as $\sum_{n \geq 1} (1 - F(\lambda_n)) < \infty$ or $= \infty$.

> [!done]

> [!question] 2.3.17. (i)
> Let $Y_1, Y_2, \dots$ be i.i.d. Find necessary and sufficient conditions for (i) $Y_n/n \to 0$ almost surely.

> [!done]

> [!question] 2.3.17. (ii)
> (ii) $(\max_{m \leq n} Y_m)/n \to 0$ almost surely.

> [!done]

> [!question] 2.3.17. (iii)
> (iii) $(\max_{m \leq n} Y_m)/n \to 0$ in probability.

> [!done]

> [!question] 2.3.17. (iv)
> (iv) $Y_n/n \to 0$ in probability.

> [!done]

> [!question] 2.3.18.
> Let $0 \leq X_1 \leq X_2 \dots$ be random variables with $\mathbb{E}X_n \sim an^\alpha$ with $a, \alpha > 0$, and $\text{var}(X_n) \leq Bn^\beta$ with $\beta < 2\alpha$. Show that $X_n/n^\alpha \to a$ a.s.

> [!done]

> [!question] 2.3.19.
> Let $X_n$ be independent Poisson r.v.'s with $\mathbb{E}X_n = \lambda_n$, and let $S_n = X_1 + \dots + X_n$. Show that if $\sum \lambda_n = \infty$ then $S_n / \mathbb{E}S_n \to 1$ a.s.

> [!done]

> [!question] 2.3.20.
> Show that if $X_n$ is the outcome of the $n$th play of the St. Petersburg game (Example 2.2.16) then $\limsup_{n \to \infty} X_n/(n \log_2 n) = \infty$ a.s. and hence the same result holds for $S_n$. This shows that the convergence $S_n/(n \log_2 n) \to 1$ in probability proved in Section 2.2 does not occur a.s.

> [!done]