> [!question] 3.1.1.
> Generalize the proof of Lemma 3.1.1 to conclude that if $\max_{1 \leq j \leq n} |c_{j,n}| \to 0$, $\sum_{j=1}^n c_{j,n} \to \lambda$, and $\sup_n \sum_{j=1}^n |c_{j,n}| < \infty$ then $\prod_{j=1}^n (1 + c_{j,n}) \to e^\lambda$.

> [!done] 
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
> Recall Stirling's fomula, 
> $$
> n!\sim\sqrt{2\pi n}\left(\frac{n}{e}\right)^n,\text{ a.s. }n\to\infty
> $$
> We calculate 
> $$
> \begin{aligned}
>\sqrt{2\pi n}\mathbb{P}(S_n = k)=\sqrt{2\pi n}\frac{n^k}{k!}e^{-n}
>\end{aligned}
> $$

> [!question] 3.1.3.
> In the next two examples you should begin by considering $\mathbb{P}(S_n = k)$ when $k/n \to a$ and then relate $\mathbb{P}(S_n = j+1)$ to $\mathbb{P}(S_n = j)$ to show $\mathbb{P}(S_n \geq k) \leq C \mathbb{P}(S_n = k)$.
> 
> Suppose $\mathbb{P}(X_i = 1) = \mathbb{P}(X_i = -1) = 1/2$. Show that if \(a \in (0, 1)\)
> $$
> \frac{1}{2n} \log \mathbb{P}(S_{2n} \geq 2na) \to -\gamma(a)
> $$
> where $\gamma(a) = \frac{1}{2}\{(1+a)\log(1+a) + (1-a)\log(1-a)\}$.

> [!done]

> [!question] 3.1.4.
> Suppose $\mathbb{P}(X_i = k) = e^{-1}/k!$ for $k = 0, 1, \dots$. Show that if $a > 1$
> $$
> \frac{1}{n} \log \mathbb{P}(S_n \geq na) \to a - 1 - a\log a
> $$

> [!done]