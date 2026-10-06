> [!question] 2.1.1.
> Suppose $(X_1, \dots, X_n)$ has density $f(x_1, x_2, \dots, x_n)$, that is
> $$
> \mathbb{P}((X_1, X_2, \dots, X_n) \in A) = \int_A f(x) dx \text{ for } A \in \mathcal{R}^n
> $$
> If $f(x)$ can be written as $g_1(x_1)\cdots g_n(x_n)$ where the $g_m \geq 0$ are measurable, then $X_1, X_2, \dots, X_n$ are independent. Note that the $g_m$ are not assumed to be probability densities.

> [!done]

> [!question] 2.1.2.
> Suppose $X_1, \dots, X_n$ are random variables that take values in countable sets $S_1, \dots, S_n$. Then in order for $X_1, \dots, X_n$ to be independent, it is sufficient that whenever $x_i \in S_i$
> $$
> \mathbb{P}(X_1 = x_1, \dots, X_n = x_n) = \prod_{i=1}^n \mathbb{P}(X_i = x_i)
> $$

> [!done]

> [!question] 2.1.3. (i)
> Let $\rho(x,y)$ be a metric. (i) Suppose $h$ is differentiable with $h(0) = 0$, $h'(x) > 0$ for $x > 0$ and $h'(x)$ decreasing on $[0, \infty)$. Then $h(\rho(x,y))$ is a metric.

> [!done]

> [!question] 2.1.3. (ii)
> (ii) $h(x) = x/(x+1)$ satisfies the hypotheses in (i).

> [!done]

> [!question] 2.1.4.
> Let $\Omega = (0,1)$, $\mathcal{F} =$ Borel sets, $\mathbb{P} =$ Lebesgue measure. $X_n(\omega) = \sin(2\pi n \omega)$, $n = 1, 2, \dots$ are uncorrelated but not independent.

> [!done]

> [!question] 2.1.5. (i)
> Show that if $X$ and $Y$ are independent with distributions $\mu$ and $\nu$ then
> $$
> \mathbb{P}(X + Y = 0) = \sum_y \mu(\{-y\})\nu(\{y\})
> $$

> [!done]

> [!question] 2.1.5. (ii)
> (ii) Conclude that if $X$ has continuous distribution $\mathbb{P}(X = Y) = 0$.

> [!done]

> [!question] 2.1.6.
> Prove directly from the definition that if $X$ and $Y$ are independent and $f$ and $g$ are measurable functions then $f(X)$ and $g(Y)$ are independent.

> [!done]

> [!question] 2.1.7.
> Let $K \geq 3$ be a prime and let $X$ and $Y$ be independent random variables that are uniformly distributed on $\{0, 1, \dots, K-1\}$. For $0 \leq n < K$, let $Z_n = X + nY \bmod K$. Show that $Z_0, Z_1, \dots, Z_{K-1}$ are **pairwise independent**, i.e., each pair is independent. They are not independent because if we know the values of two of the variables then we know the values of all the variables.

> [!done]

> [!question] 2.1.8.
> Find four random variables taking values in $\{-1, 1\}$ so that any three are independent but all four are not. Hint: Consider products of independent random variables.

> [!done]

> [!question] 2.1.9.
> Let $\Omega = \{1, 2, 3, 4\}$, $\mathcal{F} =$ all subsets of $\Omega$, and $\mathbb{P}(\{i\}) = 1/4$. Give an example of two collections of sets $\mathcal{A}_1$ and $\mathcal{A}_2$ that are independent but whose generated $\sigma$-fields are not.

> [!done]

> [!question] 2.1.10.
> Show that if $X$ and $Y$ are independent, integer-valued random variables, then
> $$
> \mathbb{P}(X + Y = n) = \sum_m \mathbb{P}(X = m)\mathbb{P}(Y = n - m)
> $$

> [!done]

> [!question] 2.1.11.
> In Example 1.6.13, we introduced the Poisson distribution with parameter $\lambda$, which is given by $\mathbb{P}(Z = k) = e^{-\lambda}\lambda^k/k!$ for $k = 0, 1, 2, \dots$. Use the previous exercise to show that if $X = \text{Poisson}(\lambda)$ and $Y = \text{Poisson}(\mu)$ are independent then $X + Y = \text{Poisson}(\lambda + \mu)$.

> [!done]

> [!question] 2.1.12. (i)
> $X$ is said to have a Binomial$(n,p)$ distribution if
> $$
> \mathbb{P}(X = m) = \binom{n}{m} p^m (1-p)^{n-m}
> $$
> (i) Show that if $X = \text{Binomial}(n,p)$ and $Y = \text{Binomial}(m,p)$ are independent then $X + Y = \text{Binomial}(n+m, p)$.

> [!done]

> [!question] 2.1.12. (ii)
> (ii) Look at Example 1.6.12 and use induction to conclude that the sum of $n$ independent Bernoulli$(p)$ random variables is Binomial$(n,p)$.

> [!done]

> [!question] 2.1.13. (a)
> It should not be surprising that the distribution of $X + Y$ can be $F * G$ without the random variables being independent. Suppose $X, Y \in \{0, 1, 2\}$ and take each value with probability $1/3$. (a) Find the distribution of $X + Y$ assuming $X$ and $Y$ are independent.

> [!done]

> [!question] 2.1.13. (b)
> (b) Find all the joint distributions $(X, Y)$ so that the distribution of $X + Y$ is the same as the answer to (a).

> [!done]

> [!question] 2.1.14.
> Let $X, Y \geq 0$ be independent with distribution functions $F$ and $G$. Find the distribution function of $XY$.

> [!done]

> [!question] 2.1.15.
> If we want an infinite sequence of coin tossings, we do not have to use Kolmogorov's theorem. Let $\Omega$ be the unit interval $(0,1)$ equipped with the Borel sets $\mathcal{F}$ and Lebesgue measure $\mathbb{P}$. Let $Y_n(\omega) = 1$ if $[2^n \omega]$ is odd and $0$ if $[2^n \omega]$ is even. Show that $Y_1, Y_2, \dots$ are independent with $\mathbb{P}(Y_k = 0) = \mathbb{P}(Y_k = 1) = 1/2$.

> [!done]