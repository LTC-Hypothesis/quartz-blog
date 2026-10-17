> [!question] 2.2.1.
> Let $X_1, X_2, \dots$ be uncorrelated with $\mathbb{E}X_i = \mu_i$ and $\text{var}(X_i)/i \to 0$ as $i \to \infty$. Let $S_n = X_1 + \dots + X_n$ and $\nu_n = \mathbb{E}S_n/n$ then as $n \to \infty$, $S_n/n - \nu_n \to 0$ in $L^2$ and in probability.

>[!done] 
>Since $\frac{1}{i}\text{Var}(X_i)\to\varepsilon$, for any $\varepsilon>0$, for sufficiently large $i$, there exists $N\in\mathbb{N}$ s.t. $i\ge N$, we have 
>$$
>\text{Var}(X_i)\le\varepsilon i
>$$
>We compute for $n\ge N$
>$$
>\begin{aligned}
>\mathbb{E}\left|\frac{S_n}{n}-\nu_n\right|^2&=\frac{\sum_{i=1}^{n}\text{Var}(X_i)}{n^2}\\
>&=\frac{\sum_{i=1}^{N}\text{Var}(X_i)}{n^2}+\frac{1}{n^2}\sum_{i=N+1}^{n}\text{Var}(X_i)\\
>&\le \frac{\sum_{i=1}^{N}\text{Var}(X_i)}{n^2}+\varepsilon\frac{n(n-N)}{n^2}
>\end{aligned}
>$$
>Thus, 
>$$
>\limsup_{n\to\infty}\mathbb{E}\left|\frac{S_n}{n}-\nu_n\right|^2\le \varepsilon
>$$
>Hence, $\frac{S_n}{n}-\nu_n\xrightarrow{L^2}0$ and thus in probability.

> [!question] 2.2.2.
> The $L^2$ weak law generalizes immediately to certain dependent sequences. Suppose $\mathbb{E}X_n = 0$ and $\mathbb{E}X_n X_m \leq r(n-m)$ for $m \leq n$ (no absolute value on the left-hand side!) with $r(k) \to 0$ as $k \to \infty$. Show that $(X_1 + \dots + X_n)/n \to 0$ in probability.

> [!done]
> 

> [!question] 2.2.3. (i)
> **Monte Carlo integration.** (i) Let $f$ be a measurable function on $[0,1]$ with $\int_0^1 |f(x)|dx < \infty$. Let $U_1, U_2, \dots$ be independent and uniformly distributed on $[0,1]$, and let
> $$
> I_n = n^{-1}(f(U_1) + \dots + f(U_n))
> $$
> Show that $I_n \to I \equiv \int_0^1 f dx$ in probability.

> [!done]

> [!question] 2.2.3. (ii)
> (ii) Suppose $\int_0^1 |f(x)|^2 dx < \infty$. Use Chebyshev's inequality to estimate $\mathbb{P}(|I_n - I| > a/n^{1/2})$.

> [!done]

> [!question] 2.2.4.
> Let $X_1, X_2, \dots$ be i.i.d. with $\mathbb{P}(X_i = (-1)^k k) = C/k^2 \log k$ for $k \geq 2$ where $C$ is chosen to make the sum of the probabilities = 1. Show that $\mathbb{E}|X_i| = \infty$, but there is a finite constant $\mu$ so that $S_n/n \to \mu$ in probability.

> [!done]

> [!question] 2.2.5.
> Let $X_1, X_2, \dots$ be i.i.d. with $\mathbb{P}(X_i > x) = e/x \log x$ for $x \geq e$. Show that $\mathbb{E}|X_i| = \infty$, but there is a sequence of constants $\mu_n \to \infty$ so that $S_n/n - \mu_n \to 0$ in probability.

> [!done]

> [!question] 2.2.6. (i)
> (i) Show that if $X \geq 0$ is integer valued $\mathbb{E}X = \sum_{n \geq 1} \mathbb{P}(X \geq n)$.

> [!done]

> [!question] 2.2.6. (ii)
> (ii) Find a similar expression for $\mathbb{E}X^2$.

> [!done]

> [!question] 2.2.7.
> Generalize Lemma 2.2.13 to conclude that if $H(x) = \int_{(-\infty, x]} h(y) dy$ with $h(y) \geq 0$, then
> $$
> \mathbb{E} H(X) = \int_{-\infty}^\infty h(y)\mathbb{P}(X \geq y) dy
> $$
> An important special case is $H(x) = \exp(\theta x)$ with $\theta > 0$.

> [!done]

> [!question] 2.2.8.
> **An unfair "fair game."** Let $p_k = 1/2^k k(k+1)$, $k = 1, 2, \dots$ and $p_0 = 1 - \sum_{k \geq 1} p_k$.
> $$
> \sum_{k=1}^\infty 2^k p_k = (1 - \frac{1}{2}) + (\frac{1}{2} - \frac{1}{3}) + \dots = 1
> $$
> so if we let $X_1, X_2, \dots$ be i.i.d. with $\mathbb{P}(X_n = -1) = p_0$ and
> $$
> \mathbb{P}(X_n = 2^k - 1) = p_k \quad \text{for } k \geq 1
> $$
> then $\mathbb{E}X_n = 0$. Let $S_n = X_1 + \dots + X_n$. Use Theorem 2.2.11 with $b_n = 2^{m(n)}$ where $m(n) = \min\{m : 2^{-m} m^{-3/2} \leq n^{-1}\}$ to conclude that
> $$
> S_n/(n/\log_2 n) \to -1 \text{ in probability}
> $$

> [!done]

> [!question] 2.2.9.
> **Weak law for positive variables.** Suppose $X_1, X_2, \dots$ are i.i.d., $\mathbb{P}(0 \leq X_i < \infty) = 1$ and $\mathbb{P}(X_i > x) > 0$ for all $x$. Let $\mu(s) = \int_0^s x dF(x)$ and $\nu(s) = \mu(s)/s(1-F(s))$. It is known that there exist constants $a_n$ so that $S_n/a_n \to 1$ in probability, if and only if $\nu(s) \to \infty$ as $s \to \infty$. Pick $b_n \geq 1$ so that $n\mu(b_n) = b_n$ (this works for large $n$), and use Theorem 2.2.11 to prove that the condition is sufficient.

> [!done]