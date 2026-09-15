> [!question] 1.5.1.
> Let $\|f\|_\infty = \inf\{M : \mu(\{x : |f(x)| > M\}) = 0\}$. Prove that
> $$
> \int |fg| d\mu \leq \|f\|_1 \|g\|_\infty
> $$

> [!done]
> 

> [!question] 1.5.2.
> Show that if $\mu$ is a probability measure then
> $$
> \|f\|_\infty = \lim_{p \to \infty} \|f\|_p
> $$

> [!done]

> [!question] **Minkowski's inequality.** 1.5.3.(i)
>  Suppose $p \in (1, \infty)$. The inequality $|f + g|^p \leq 2^p (|f|^p + |g|^p)$ shows that if $\|f\|_p$ and $\|g\|_p$ are $< \infty$ then $\|f + g\|_p < \infty$. Apply Hölder's inequality to $|f||f + g|^{p-1}$ and $|g||f + g|^{p-1}$ to show $\|f + g\|_p \leq \|f\|_p + \|g\|_p$. 

> [!done]

>[!question] 1.5.3.(ii) 
>Show that the last result remains true when $p = 1$ or $p = \infty$.

>[!done] 
>

> [!question] 1.5.4.
> If $f$ is integrable and $E_m$ are disjoint sets with union $E$ then
> $$
> \sum_{m=0}^\infty \int_{E_m} f d\mu = \int_E f d\mu
> $$
> So if $f \geq 0$, then $\nu(E) = \int_E f d\mu$ defines a measure.

> [!done]

> [!question] 1.5.5.
> If $g_n \uparrow g$ and $\int g_1^- d\mu < \infty$ then $\int g_n d\mu \uparrow \int g d\mu$.
> [!done]

> [!question] 1.5.6.
> If $g_m \geq 0$ then $\int \sum_{m=0}^\infty g_m d\mu = \sum_{m=0}^\infty \int g_m d\mu$.
> [!done]

> [!question] 1.5.7.
> Let $f \geq 0$. (i) Show that $f \wedge n \uparrow f$ and $f \wedge n d\mu \uparrow \int f d\mu$ as $n \to \infty$. (ii) Use (i) to conclude that if $g$ is integrable and $\epsilon > 0$ then we can pick $\delta > 0$ so that $\mu(A) < \delta$ implies $\int_A |g| d\mu < \epsilon$.
> [!done]

> [!question] 1.5.8.
> Show that if $f$ is integrable on $[a, b]$, $g(x) = \int_{[a,x]} f(y) dy$ is continuous on $(a, b)$.
> [!done]

> [!question] 1.5.9.
> Show that if $f$ has $\|f\|_p = (\int |f|^p d\mu)^{1/p} < \infty$, then there are simple functions $\varphi_n$ so that $\|\varphi_n - f\|_p \to 0$.
> [!done]

> [!question] 1.5.10.
> Show that if $\sum_n \int |f_n| d\mu < \infty$ then $\sum_n \int f_n d\mu = \int \sum_n f_n d\mu$.
> [!done]