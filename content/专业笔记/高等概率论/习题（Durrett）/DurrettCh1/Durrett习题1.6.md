> [!question] 1.6.1.
> Suppose $\varphi$ is strictly convex, i.e., $>$ holds for $\lambda \in (0,1)$. Show that, under the assumptions of Theorem 1.6.2, $\varphi(\mathbb{E}X) = \mathbb{E}\varphi(X)$ implies $X = \mathbb{E}X$ a.s.

> [!done]
> Set $Y=X-\mathbb{E}X$, consider the variance of $Y$, 
> $$
> \text{Var}(Y)=\mathbb{E}Y^2=\mathbb{E}\left[X^2-2X\mathbb{E}(X)+(\mathbb{E}X)^2\right]=\mathbb{E}X^2-(\mathbb{E}X)^2
> $$
> Since $X$ satisfies $\mathbb{E}X^2=(\mathbb{E}X)^2$ with $f(x)=x^2$, $\text{Var}(Y)=0$. Therefore, $Y=\text{constant} \ a.s.-\mathbb{P}$ and $\mathbb{E}Y=0$, $Y=0$.

> [!question] 1.6.2.
> Suppose $\varphi : \mathbf{R}^n \to \mathbf{R}$ is convex. Imitate the proof of Theorem 1.5.1 to show
> $$
> \mathbb{E}\varphi(X_1, \dots, X_n) \geq \varphi(\mathbb{E}X_1, \dots, \mathbb{E}X_n)
> $$
> provided $\mathbb{E}|\varphi(X_1, \dots, X_n)| < \infty$ and $\mathbb{E}|X_i| < \infty$ for all $i$.

> [!done]

> [!question] 1.6.3.
> **Chebyshev's inequality is and is not sharp.** (i) Show that Theorem 1.6.4 is sharp by showing that if $0 < b \leq a$ are fixed there is an $X$ with $\mathbb{E}X^2 = b^2$ for which $\mathbb{P}(|X| \geq a) = b^2/a^2$. (ii) Show that Theorem 1.6.4 is not sharp by showing that if $X$ has $0 < \mathbb{E}X^2 < \infty$ then
> $$
> \lim_{a \to \infty} a^2 \mathbb{P}(|X| \geq a) / \mathbb{E}X^2 = 0
> $$

> [!done]

> [!question] 1.6.4.
> **One-sided Chebyshev bound.** (i) Let $a > b > 0$, $0 < p < 1$, and let $X$ have $\mathbb{P}(X = a) = p$ and $\mathbb{P}(X = -b) = 1 - p$. Apply Theorem 1.6.4 to $\varphi(x) = (x + b)^2$ and conclude that if $Y$ is any random variable with $\mathbb{E}Y = \mathbb{E}X$ and $\text{var}(Y) = \text{var}(X)$, then $\mathbb{P}(Y \geq a) \leq p$ and equality holds when $Y = X$.
> (ii) Suppose $\mathbb{E}Y = 0$, $\text{var}(Y) = \sigma^2$, and $a > 0$. Show that $\mathbb{P}(Y \geq a) \leq \sigma^2/(a^2 + \sigma^2)$, and there is a $Y$ for which equality holds.

> [!done]

> [!question] 1.6.5.
> **Two nonexistent lower bounds.**
> Show that: (i) if $\epsilon > 0$, $\inf\{\mathbb{P}(|X| > \epsilon) : \mathbb{E}X = 0, \text{var}(X) = 1\} = 0$.
> (ii) if $y \geq 1$, $\sigma^2 \in (0, \infty)$, $\inf\{\mathbb{P}(|X| > y) : \mathbb{E}X = 1, \text{var}(X) = \sigma^2\} = 0$.

> [!done]

> [!question] 1.6.6.
> **A useful lower bound.** Let $Y \geq 0$ with $\mathbb{E}Y^2 < \infty$. Apply the Cauchy-Schwarz inequality to $Y 1_{(Y > 0)}$ and conclude
> $$
> \mathbb{P}(Y > 0) \geq (\mathbb{E}Y)^2 / \mathbb{E}Y^2
> $$

> [!done]

> [!question] 1.6.7.
> Let $\Omega = (0, 1)$ equipped with the Borel sets and Lebesgue measure. Let $\alpha \in (1, 2)$ and $X_n = n^\alpha 1_{(1/(n+1), 1/n)} \to 0$ a.s. Show that Theorem 1.6.8 can be applied with $h(x) = x$ and $g(x) = |x|^{2/\alpha}$, but the $X_n$ are not dominated by an integrable function.

> [!done]

> [!question] 1.6.8.
> Suppose that the probability measure $\mu$ has $\mu(A) = \int_A f(x) dx$ for all $A \in \mathcal{R}$. Use the proof technique of Theorem 1.6.9 to show that for any $g$ with $g \geq 0$ or $\int |g(x)| \mu(dx) < \infty$ we have
> $$
> \int g(x) \mu(dx) = \int g(x) f(x) dx
> $$

> [!done]

> [!question] 1.6.9.
> **Inclusion-exclusion formula.** Let $A_1, A_2, \dots A_n$ be events and $A = \cup_{i=1}^n A_i$. Prove that $1_A = 1 - \prod_{i=1}^n (1 - 1_{A_i})$. Expand out the right hand side, then take expected value to conclude
> $$
> \begin{aligned}
> \mathbb{P}(\cup_{i=1}^n A_i) &= \sum_{i=1}^n \mathbb{P}(A_i) - \sum_{i<j} \mathbb{P}(A_i \cap A_j) \\
> &\quad + \sum_{i<j<k} \mathbb{P}(A_i \cap A_j \cap A_k) - \dots + (-1)^{n-1} \mathbb{P}(\cap_{i=1}^n A_i)
> \end{aligned}
> $$

> [!done]

> [!question] 1.6.10.
> **Bonferroni inequalities.** Let $A_1, A_2, \dots A_n$ be events and $A = \cup_{i=1}^n A_i$. Show that $1_A \leq \sum_{i=1}^n 1_{A_i}$, etc. and then take expected values to conclude
> $$
> \mathbb{P}(\cup_{i=1}^n A_i) \leq \sum_{i=1}^n \mathbb{P}(A_i)
> $$
> $$
> \mathbb{P}(\cup_{i=1}^n A_i) \geq \sum_{i=1}^n \mathbb{P}(A_i) - \sum_{i<j} \mathbb{P}(A_i \cap A_j)
> $$
> $$
> \mathbb{P}(\cup_{i=1}^n A_i) \leq \sum_{i=1}^n \mathbb{P}(A_i) - \sum_{i<j} \mathbb{P}(A_i \cap A_j) + \sum_{i<j<k} \mathbb{P}(A_i \cap A_j \cap A_k)
> $$
> In general, if we stop the inclusion exclusion formula after an even (odd) number of sums, we get a lower (upper) bound.

> [!done]

> [!question] 1.6.11.
> If $\mathbb{E}|X|^k < \infty$ then for $0 < j < k$, $\mathbb{E}|X|^j < \infty$, and furthermore
> $$
> \mathbb{E}|X|^j \leq (\mathbb{E}|X|^k)^{j/k}
> $$

> [!done]

> [!question] 1.6.12.
> Apply Jensen's inequality with $\varphi(x) = e^x$ and $\mathbb{P}(X = \log y_m) = p(m)$ to conclude that if $\sum_{m=1}^n p(m) = 1$ and $p(m), y_m > 0$ then
> $$
> \sum_{m=1}^n p(m) y_m \geq \prod_{m=1}^n y_m^{p(m)}
> $$
> When $p(m) = 1/n$, this says the arithmetic mean exceeds the geometric mean.

> [!done]

> [!question] 1.6.13.
> If $\mathbb{E}X_1^- < \infty$ and $X_n \uparrow X$ then $\mathbb{E}X_n \uparrow \mathbb{E}X$.

> [!done]

> [!question] 1.6.14.
> Let $X \geq 0$ but do NOT assume $\mathbb{E}(1/X) < \infty$. Show
> $$
> \lim_{y \to \infty} y \mathbb{E}(1/X ; X > y) = 0, \qquad \lim_{y \downarrow 0} y \mathbb{E}(1/X ; X > y) = 0.
> $$

> [!done]

> [!question] 1.6.15.
> If $X_n \geq 0$ then $\mathbb{E}(\sum_{n=0}^\infty X_n) = \sum_{n=0}^\infty \mathbb{E}X_n$.

> [!done]
> It is obtained by MCT directly.

> [!question] 1.6.16.
> If $X$ is integrable and $A_n$ are disjoint sets with union $A$ then
> $$
> \sum_{n=0}^\infty \mathbb{E}(X ; A_n) = \mathbb{E}(X ; A)
> $$
> i.e., the sum converges absolutely and has the value on the right.

> [!done]