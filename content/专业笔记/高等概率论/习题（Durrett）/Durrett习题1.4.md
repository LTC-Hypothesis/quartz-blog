> [!question] 1.4.1.
> Show that if $f \geq 0$ and $\int f d\mu = 0$ then $f = 0$ a.e.

> [!done]
> Consider the set 
> $$
> E_n=\left\{x:f(x)\ge\frac{1}{n}\right\}
> $$
> Then 
> $$
> E=\left\{x:f(x)>0\right\}=\bigcap_{n=1}^{\infty}E_n
> $$
> Then 
> $$
> \begin{aligned}
>\mu(E)&=\mu\left(\bigcap_{n=1}^{\infty}E_n\right)=\lim_{n\to\infty}\mu(E_n)\\
>&=\lim_{n\to\infty}\int_{E_n}{d}\mu\le \lim_{n\to\infty}n\int_{E_n}\frac{1}{n}{d}\mu\\
>&\le \lim_{n\to\infty}n\int_{X}f(x){d}\mu=0
>\end{aligned}
> $$
> Hence, $f(x)=0,a.e.$

> [!question] 1.4.2.
> Let $f \geq 0$ and $E_{n,m} = \{x : m/2^n \leq f(x) < (m+1)/2^n\}$. As $n \uparrow \infty$,
> $$
> \sum_{m=1}^\infty \frac{m}{2^n} \mu(E_{n,m}) \uparrow \int f d\mu
> $$

> [!done]
> Note that 
> $$
> \frac{m}{2^n}\mu(E_{n,m})=\frac{m}{2^n}\int_{E_{n,m}}{d}\mu\le \int_{E_{n,m}}f(x){d}\mu
> $$
> then 
> $$
> \sum_{m=1}^{\infty}\frac{m}{2^n}\mu(E_{n,m})\le \sum_{m=1}^{\infty}\int_{E_{n,m}}f(x){d}\mu\le\int_{X}f(x){d}\mu|\longrightarrow
> $$

> [!question] 1.4.3. (i)
> Let $g$ be an integrable function on $\mathbf{R}$ and $\epsilon > 0$. Use the definition of the integral to conclude there is a simple function $\varphi = \sum_k b_k 1_{A_k}$ with $\int |g - \varphi| dx < \epsilon$.

> [!done]
> 

> [!question] 1.4.3. (ii)
> Use Exercise A.2.1 to approximate the $A_k$ by finite unions of intervals to get a **step function**
> $$
> q = \sum_{j=1}^k c_j 1_{(a_{j-1}, a_j)}
> $$
> with $a_0 < a_1 < \ldots < a_k$, so that $\int |\varphi - q| < \epsilon$.

> [!done]
> 

> [!question] 1.4.3. (iii)
> Round the corners of $q$ to get a continuous function $r$ so that $\int |q - r| dx < \epsilon$.

> [!done]

> [!question] 1.4.3. (iii) 补充说明
> To make a continuous function replace each $c_j 1_{(a_{j-1}, a_j)}$ by a function that is $0$ $(a_{j-1}, a_j)^c$, $c_j$ on $[a_{j-1} + \delta_j, a_j - \delta_j]$, and linear otherwise. If the $\delta_j$ are small enough and we let $r(x) = \sum_{j=1}^k r_j(x)$ then
> $$
> \int |q(x) - r(x)| d\mu = \sum_{j=1}^k \delta_j c_j < \epsilon
> $$


> [!done]

> [!question] 1.4.4.
> Prove the **Riemann-Lebesgue lemma**. If $g$ is integrable then
> $$
> \lim_{n \to \infty} \int g(x) \cos nx \, dx = 0
> $$
> Hint: If $g$ is a step function, this is easy. Now use the previous exercise.

> [!done]