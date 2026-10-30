> [!question] 2.5.1.
> Suppose $X_1, X_2, \dots$ are i.i.d. with $\mathbb{E}X_i = 0$, $\text{var}(X_i) = C < \infty$. Use Theorem 2.5.5 with $n = m^\alpha$ where $\alpha(2p - 1) > 1$ to conclude that if $S_n = X_1 + \dots + X_n$ and $p > 1/2$ then $S_n/n^p \to 0$ almost surely.

> [!done]
> Firstly, we consider 
> $$
> \mathbb{P}\left(\max_{1\le k\le n}|S_k|\ge\varepsilon n^p\right)\le\frac{\text{Var}(S_n)}{\varepsilon^2 n^{2p}}\le\frac{C}{\varepsilon^2n^{(2p-1)}}
> $$
> We take $n=m^\alpha$ and obtain by $\alpha(2p-1)>1$ 
> $$
> \sum_{m=1}^{\infty}\frac{C}{\varepsilon^2m^{\alpha(2p-1)}}<\infty
> $$
> After passing subsequence $n_m=\left \lceil  m^\alpha\right \rceil$, we have 
> $$
> \mathbb{P}\left(\max_{1\le k\le n_m}|S_k|\ge\varepsilon n_m^p\right)\le\frac{C}{\varepsilon^2n_m^{(2p-1)}}\le\frac{C}{\varepsilon^2m^{\alpha(2p-1)}}
> $$
> By Borel-Cantelli's lemma,
> $$
> \sum_{m=1}^{\infty}\mathbb{P}\left(\max_{1\le k\le n_m}|S_k|\ge\varepsilon n_m^p\right)<\infty\Longrightarrow\mathbb{P}\left(\max_{1\le k\le n_m}|S_k|\ge\varepsilon n_m^p,\text{i.o.}\right)=0
> $$
> Then for any $k\in\mathbb{N}$, there exists $N\in\mathbb{N}$ and $\Omega_k$ with probability $1$, for $m\ge N$ and $\omega\in\Omega_k$, it holds 
> $$
> \max_{1\le j\le n_m}|S_j(\omega)|<\frac{1}{k}\cdot n_m^p
> $$
> Let $\Omega_*=\bigcap_{k=1}^{\infty}\Omega_k$, for $\omega\in\Omega_*$, 
> $$
> \mathbb{P}\left(\bigcap_{k=1}^{\infty}\bigcup_{N=1}^{\infty}\bigcap_{m=N}^{\infty}\left\{\frac{\max_{1\le j\le n_m}|S_j|}{n_m^p}\le\frac{1}{k}\right\}\right)=1
> $$
> It implies $\frac{\max_{1\le j\le n_m}|S_j|}{n_m^p}\xrightarrow{a.s.}0$. Now for any $n\in\mathbb{N}$, there exists $n_{m}\le n<n_{m+1}$
> $$
> \frac{|S_n|}{n^p}\le\frac{\max_{1\le k\le n_{m+1}}|S_k|}{n_m^p}=\frac{\max_{1\le k\le n_{m+1}}|S_k|}{n_{m+1}^p}\frac{n_{m+1}^p}{n_{m}^p}\to0\text{ a.s. }m\to\infty
> $$
> Hence, $\frac{S_n}{n^p}\xrightarrow{a.s.}0$.

> [!question] 2.5.2.
> The converse of Theorem 2.5.12 is much easier. Let $p > 0$. If $S_n/n^{1/p} \to 0$ a.s. then $\mathbb{E}|X_1|^p < \infty$.

> [!done]
> Let $Y=|X_1|^p$, note that 
> $$
> \mathbb{E}Y<\infty\Longleftrightarrow\sum_{n=1}^{\infty}\mathbb{P}(Y>n)<\infty
> $$
> Since $\frac{S_n}{\sqrt[p]{n}}\xrightarrow{a.s.}0$, we have 
> $$
> \frac{X_n}{\sqrt[p]{n}}=\frac{S_n}{\sqrt[p]{n}}-\frac{S_{n-1}}{\sqrt[p]{n-1}}\sqrt[p]{\frac{n-1}{n}}\xrightarrow{a.s}0
> $$
> Therefore, denote the event by 
> $$
> A_n:=\{|X_n|>\sqrt[p]{n}\}\Longrightarrow\mathbb{P}(A_n,\text{i.o.})=0
> $$
> If $\sum_{n=1}^{\infty}\mathbb{P}(Y>n)=\infty$, since $A_n$ are independent, by 2nd Borel-Cantelli''s lemma, $\mathbb{P}(Y>n,\text{i.o.})=1\Longrightarrow\Longleftarrow$ with $\mathbb{P}(A_n,\text{i.o.})=0$. Hence, we prove it. 

> [!question] 2.5.3.
> Let $X_1, X_2, \dots$ be i.i.d. standard normals. Show that for any $t$
> $$
> \sum_{n=1}^\infty X_n \cdot \frac{\sin(n\pi t)}{n} \quad \text{converges a.s.}
> $$
> We will see this series again at the end of Section 8.1 [REF].

> [!done]
> Let $Y_n:=X_n\cdot\frac{\sin{(n\pi t)}}{n}$, then 
> $$
> \mathbb{E}Y_n=0,\mathbb{E}Y_n^2=\frac{\sin^2(n\pi t)}{n^2}
> $$
> Since 
> $$
> \left|\frac{\sin^2(n\pi t)}{n^2}\right|\le\frac{1}{n^2}\Longrightarrow\sum_{n=1}^{\infty}\frac{\sin^2(n\pi t)}{n^2}<\infty
> $$
> Then 
> $$
> \sum_{n=1}^{\infty}Y_n<\infty\text{ with probability one}
> $$

> [!question] 2.5.4. (i)
> Let $X_1, X_2, \dots$ be independent with $\mathbb{E}X_n = 0$, $\text{var}(X_n) = \sigma_n^2$. (i) Show that if $\sum_n \sigma_n^2/n^2 < \infty$ then $\sum_n X_n/n$ converges a.s. and hence $n^{-1} \sum_{m=1}^n X_m \to 0$ a.s.

> [!done]

> [!question] 2.5.4. (ii)
> (ii) Suppose $\sum \sigma_n^2/n^2 = \infty$ and without loss of generality that $\sigma_n^2 \leq n^2$ for all $n$. Show that there are independent random variables $X_n$ with $\mathbb{E}X_n = 0$ and $\text{var}(X_n) \leq \sigma_n^2$ so that $X_n/n$ and hence $n^{-1} \sum_{m \leq n} X_m$ does not converge to 0 a.s.

> [!done]

> [!question] 2.5.5.
> Let $X_n \geq 0$ be independent for $n \geq 1$. The following are equivalent:
> (i) $\sum_{n=1}^\infty X_n < \infty$ a.s.
> 
> (ii) $\sum_{n=1}^\infty [\mathbb{P}(X_n > 1) + \mathbb{E}(X_n 1_{(X_n \leq 1)})] < \infty$
> 
> (iii) $\sum_{n=1}^\infty \mathbb{E}(X_n/(1 + X_n)) < \infty$.

> [!done]

> [!question] 2.5.6.
> Let $\psi(x) = x^2$ when $|x| \leq 1$ and $= |x|$ when $|x| \geq 1$. Show that if $X_1, X_2, \dots$ are independent with $\mathbb{E}X_n = 0$ and $\sum_{n=1}^\infty \mathbb{E}\psi(X_n) < \infty$ then $\sum_{n=1}^\infty X_n$ converges a.s.

> [!done]

> [!question] 2.5.7.
> Let $X_n$ be independent. Suppose $\sum_{n=1}^\infty \mathbb{E}|X_n|^{p(n)} < \infty$ where $0 < p(n) \leq 2$ for all $n$ and $\mathbb{E}X_n = 0$ when $p(n) > 1$. Show that $\sum_{n=1}^\infty X_n$ converges a.s.

> [!done]

> [!question] 2.5.8.
> Let $X_1, X_2, \dots$ be i.i.d. and not $\equiv 0$. Then the radius of convergence of the power series $\sum_{n \geq 1} X_n(\omega)z^n$ (i.e., $r(\omega) = \sup\{c : \sum |X_n(\omega)|c^n < \infty\}$) is 1 a.s. or 0 a.s., according as $\mathbb{E}\log^+|X_1| < \infty$ or $= \infty$ where $\log^+ x = \max(\log x, 0)$.

> [!done]

> [!question] 2.5.9.
> Let $X_1, X_2, \dots$ be independent and let $S_{m,n} = X_{m+1} + \dots + X_n$. Then
> $$
> (\star) \qquad \mathbb{P} \left( \max_{m < j \leq n} |S_{m,j}| > 2a \right) \min_{m < k \leq n} \mathbb{P}(|S_{k,n}| \leq a) \leq \mathbb{P}(|S_{m,n}| > a)
> $$

> [!done]

> [!question] 2.5.10.
> Use $(\star)$ to prove a theorem of P. Lévy: Let $X_1, X_2, \dots$ be independent and let $S_n = X_1 + \dots + X_n$. If $\lim_{n \to \infty} S_n$ exists in probability then it also exists a.s.

> [!done]

> [!question] 2.5.11.
> Let $X_1, X_2, \dots$ be i.i.d. and $S_n = X_1 + \dots + X_n$. Use $(\star)$ to conclude that if $S_n/n \to 0$ in probability then $(\max_{1 \leq m \leq n} S_m)/n \to 0$ in probability.

> [!done]

> [!question] 2.5.12. (i)
> Let $X_1, X_2, \dots$ be i.i.d. and $S_n = X_1 + \dots + X_n$. Suppose $a_n \uparrow \infty$ and $a(2^n)/a(2^{n-1})$ is bounded. (i) Use $(\star)$ to show that if $S_n/a(n) \to 0$ in probability and $S_{2^n}/a(2^n) \to 0$ a.s. then $S_n/a(n) \to 0$ a.s.

> [!done]

> [!question] 2.5.12. (ii)
> (ii) Suppose in addition that $\mathbb{E}X_1 = 0$ and $\mathbb{E}X_1^2 < \infty$. Use the previous exercise and Chebyshev's inequality to conclude that $S_n/n^{1/2}(\log_2 n)^{1/2+\epsilon} \to 0$ a.s.

> [!done]