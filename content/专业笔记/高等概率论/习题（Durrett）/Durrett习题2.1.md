> [!question] 2.1.1.
> Suppose $(X_1, \dots, X_n)$ has density $f(x_1, x_2, \dots, x_n)$, that is
> $$
> \mathbb{P}((X_1, X_2, \dots, X_n) \in A) = \int_A f(x) dx \text{ for } A \in \mathcal{R}^n
> $$
> If $f(x)$ can be written as $g_1(x_1)\cdots g_n(x_n)$ where the $g_m \geq 0$ are measurable, then $X_1, X_2, \dots, X_n$ are independent. Note that the $g_m$ are not assumed to be probability densities.

> [!done]
> Suppose that 
> $$
> c_i=\int_{\mathbb{R}}g_i(x_i){d}x_i\Longrightarrow 1=\int_{\mathbb{R}}\frac{1}{c_i}g_i(x_i){d}x_i
> $$
> Therefore, $\frac{1}{c_i}g_i(x_i)$ is density. Suppose $A=A_1\times\cdots A_n,A_i\in\mathbb{R}$, then 
> $$
> \mathbb{P}((X_1,\cdots,X_n)\in A)=\mathbb{P}(X_1\in A_1,\cdots, X_n\in A_n)
> $$
> and 
> $$
> \int_{A}f(x){d}x=\int_{A}g_1(x_1)\cdots g_n(x_n){d}x_n=(c_1\cdots c_n)\prod_{i=1}^{n}\int_{A_i}\frac{1}{c_i}g_i(x_i){d}x_i
> $$
> We only need to check 
> $$
> c_1\cdots c_n=\prod_{i=1}^{n}\int_{\mathbb{R}}g_i(x_i){d}x_i=\int_{\mathbb{R}^n}f(x){d}x=1
> $$
> Hence，
> $$
> \mathbb{P}(X_1\in A_1,\cdots,X_n\in A_n)=\prod_{i=1}^{n}\int_{A_i}\frac{1}{c_i}g_i(x_i){d}x_i=\prod_{i=1}^{n}\mathbb{P}(X_i\in A_i)
> $$

> [!question] 2.1.2.
> Suppose $X_1, \dots, X_n$ are random variables that take values in countable sets $S_1, \dots, S_n$. Then in order for $X_1, \dots, X_n$ to be independent, it is sufficient that whenever $x_i \in S_i$
> $$
> \mathbb{P}(X_1 = x_1, \dots, X_n = x_n) = \prod_{i=1}^n \mathbb{P}(X_i = x_i)
> $$

> [!done]
> FOr any Borel set $B_i$, 
> $$
> \begin{aligned}
>\mathbb{P}(X_1\in B_1,\cdots, X_n\in B_n)&=\sum_{x_1\in B_1\cap S_1}\cdots\sum_{x_n\in B_n\cap S_n}\mathbb{P}(X_1= x_1,\cdots, X_n= x_n)\\
>&=\sum_{x_1\in B_1\cap S_1}\cdots\sum_{x_n\in B_n\cap S_n}\prod_{i=1}^{n}\mathbb{P}(X_i= x_i)\\
>&=\prod_{i=1}^{n}\sum_{x_i\in B_i\cap S_i}\mathbb{P}(X_i=x_i)=\prod_{i=1}^{n}\mathbb{P}(X_i\in B_i)
>\end{aligned}
> $$

> [!question] 2.1.3. (i)
> Let $\rho(x,y)$ be a metric. (i) Suppose $h$ is differentiable with $h(0) = 0$, $h'(x) > 0$ for $x > 0$ and $h'(x)$ decreasing on $[0, \infty)$. Then $h(\rho(x,y))$ is a metric.

> [!done]
> We only check triangle inequality. By $\rho$ is a metric, $\rho(x,z)\le \rho(x,y)+\rho(y,z)$, then 
> $$
> h(\rho(x,z))\le h(\rho(x,y)+\rho(y,z))
> $$
> we W.T.S. $h(s+t)\le h(s)+h(t)$, let $g(x)=h(x+t)-h(x)-h(t)$ for $x,t\ge 0$. Consider
> $$
> g'(x)=h'(x+t)-h'(x)\le 0
> $$
> Then $g(x)$ is decreasing and $g(0)=0$ and thus we have $h(x+t)-h(x)-h(t)\le0$.

> [!question] 2.1.3. (ii)
> (ii) $h(x) = x/(x+1)$ satisfies the hypotheses in (i).

> [!done]

> [!question] 2.1.4.
> Let $\Omega = (0,1)$, $\mathcal{F} =$ Borel sets, $\mathbb{P} =$ Lebesgue measure. $X_n(\omega) = \sin(2\pi n \omega)$, $n = 1, 2, \dots$ are uncorrelated but not independent.

> [!done]
> We compute 
> $$
> \begin{aligned}
>\mathbb{E}X_nX_m&=\int_{0}^{1}\sin{(2\pi n\omega)}\sin{(2\pi m\omega)}{d}\omega\\
>&=\int_{0}^{1}\frac{1}{2}\left(\cos(2\pi\omega(n-m))-\cos(2\pi\omega(n+m))\right){d}\omega\\
>&=0
>\end{aligned}
> $$
> Hence, $X_n(\omega)$ are uncorrelated. 

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
> We compute directly, for any Borel set $A,B$
> $$
> \begin{aligned}
>\mathbb{P}(f(X)\in A,g(Y)\in B)&=\mathbb{P}(X\in f^{-1}(A),Y\in g^{-1}(B))\\
>&=\mathbb{P}(X\in f^{-1}(A))\mathbb{P}(Y\in g^{-1}(B))\\
>&=\mathbb{P}(f(X)\in A)\mathbb{P}(g(Y)\in B)
>\end{aligned}
> $$

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
> We compute directly
> $$
> \begin{aligned}
>\mathbb{P}(X+Y=n)&=\sum_{m=1}^{n}\mathbb{P}(X=m)\mathbb{P}(Y=n-m)\\
>&=e^{-(\lambda+\mu)}\sum_{m=1}^{n}\frac{\lambda^m}{m!}\frac{\mu^{n-m}}{(n-m)!}\\
>&=\frac{1}{n!}e^{-(\lambda+\mu)}\sum_{m=1}^{n}\begin{pmatrix}
>n\\
>m
>\end{pmatrix}\lambda^m\mu^{n-m}=\frac{(\lambda+\mu)^n}{n!}e^{-(\lambda+\mu)}
>\end{aligned}
> $$

> [!question] 2.1.12. (i)
> $X$ is said to have a Binomial$(n,p)$ distribution if
> $$
> \mathbb{P}(X = m) = \binom{n}{m} p^m (1-p)^{n-m}
> $$
> (i) Show that if $X = \text{Binomial}(n,p)$ and $Y = \text{Binomial}(m,p)$ are independent then $X + Y = \text{Binomial}(n+m, p)$.

> [!done]
> We compute directly
> $$
> \begin{aligned}
>\mathbb{P}(X+Y=N)&=\sum_{k=1}^{N}\mathbb{P}(X=k)\mathbb{P}(Y=N-k)\\
>&=p^N(1-p)^{(n+m)}\\
>&=
>\end{aligned}
> $$

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