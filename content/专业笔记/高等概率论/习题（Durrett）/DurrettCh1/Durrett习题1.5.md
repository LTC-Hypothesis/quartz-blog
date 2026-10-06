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
> Note that 
> $$
> \begin{aligned}
>\sum_{m=0}^{\infty}\int_{E_m}f{d}\mu=\sum_{m=0}^{\infty}\int_{\Omega}f\mathbb{1}_{E_m}{d}\mu=\lim_{n\to\infty}\sum_{m=0}^{n}\int_{\Omega}f\mathbb{1}_{E_m}{d}\mu=\lim_{n\to\infty}\int_{\Omega}\sum_{m=0}^{n}f\mathbb{1}_{E_m}{d}\mu
>\end{aligned}
> $$
> By MCT, $\lim_{n\to\infty}\sum_{m=0}^{n}\mathbb{1}_{E_m}=\sum_{m=0}^{\infty}\mathbb{1}_{E_m}=\mathbb{1}_E$, then we obtain
> $$
> \sum_{m=0}^{\infty}\int_{E_m}f{d}\mu=\int_{\Omega}f\mathbb{1}_{E}{d}\mu=\int_{E}f{d}\mu
> $$
> If we define $\nu(E)=\int_Ef{d}\mu$, then 
> $$
> \nu\left(\bigcup_{m=0}^{\infty}E_m\right)=\int_{\bigcup_{m=0}^{\infty}E_m}f{d}\mu=\sum_{m=0}^{\infty}\int_{E_m}f{d}\mu=\sum_{m=0}^{\infty}\nu(E_m)
> $$

> [!question] 1.5.5.
> If $g_n \uparrow g$ and $\int g_1^- d\mu < \infty$ then $\int g_n d\mu \uparrow \int g d\mu$.

> [!done]
> We note that $g_n$ is a general measurable function. If we want to use limit theorem, we have to construct a nonnegative function. We consider 
> $$
> g_n+g_1^-\ge g_1+g_1^-=g^+\ge0
> $$
> Since $g_n\uparrow g$, $g_n+g_1^-\uparrow g+g_1^-$, by MCT, we obtain
> $$
> \int_\Omega g_n+g_1^-{d}\mu\uparrow\int_\Omega g+g_1^-{d}\mu
> $$
> By $\int_\Omega g_1^-{d}\mu<\infty$, we obtain $\int_\Omega g_n{d}\mu\uparrow\int_\Omega g{d}\mu$.

> [!question] 1.5.6.
> If $g_m \geq 0$ then $\int \sum_{m=0}^\infty g_m d\mu = \sum_{m=0}^\infty \int g_m d\mu$.

> [!done]
> By MCT, it is obtained directly.

> [!question] 1.5.7.(i)
> Let $f \geq 0$. Show that $f \wedge n \uparrow f$ and $\int f \wedge n d\mu \uparrow \int f d\mu$ as $n \to \infty$. 

>[!done] 
>By MCT, it is obtained directly.

>[!question] 1.5.7(ii) 
>Use (i) to conclude that if $g$ is integrable and $\epsilon > 0$ then we can pick $\delta > 0$ so that $\mu(A) < \delta$ implies $\int_A |g| d\mu < \epsilon$.

^6212d2

> [!done]
> Note that 
> $$
> \int g-g\wedge n{d}\mu\uparrow0
> $$
> then for any $\varepsilon>0$, we can choose $N$ s.t. 
> $$
> \int g-g\wedge N{d}\mu<\frac{\varepsilon}{2}
> $$
> we choose $\delta=\frac{\varepsilon}{2N}$ and 
> $$
> \begin{aligned}
>\int_A|g|{d}\mu&\le \int_A|g-g\wedge N|{d}\mu+\int_{A}g\wedge N{d}\mu\\
>&\le \frac{\varepsilon}{2}+N\mu(A)<\varepsilon
>\end{aligned}
> $$

> [!question] 1.5.8.
> Show that if $f$ is integrable on $[a, b]$, $g(x) = \int_{[a,x]} f(y) dy$ is continuous on $(a, b)$.

> [!done]
> By [[#^6212d2|1.5.7.(ii)]], $\forall \varepsilon>0$, we pick $\delta>0$ s.t. $|x-y|<\delta$, implies 
> $$
> \int_{\{|x-y|<\delta\}}|f|{d}\mu<\varepsilon
> $$
> then we have 
> $$
> |g(x)-g(y)|=\int_{y}^{x}|f|{d}\mu<\varepsilon
> $$

> [!question] 1.5.9.
> Show that if $f$ has $\|f\|_p = (\int |f|^p d\mu)^{1/p} < \infty$, then there are simple functions $\varphi_n$ so that $\|\varphi_n - f\|_p \to 0$.

> [!done]
> There exists simple function $s_n$ s.t. $s_n\uparrow |f|$, consider 
> $$
> \varphi_n=s_n\mathbb{1}_{\{f\ge0\}}-s_n\mathbb{1}_{\{f<0\}}
> $$
> then 
> $$
> |f-\varphi_n|=|f|-s_n\downarrow0
> $$
> so we obtain
> $$
> 0\le |f|^p-|f-\varphi_n|^p\downarrow|f|^p
> $$
> Hence, 
> $$
> \|\varphi_n-f\|_p^p=\|\varphi_n-f\|_p^p-\|f\|_p^p+\|f\|_p^p\uparrow0
> $$

>[!warning] 
>The class of simple functions is dense in $L^p(\Omega)$.

> [!question] 1.5.10.
> Show that if $\sum_n \int |f_n| d\mu < \infty$ then $\sum_n \int f_n d\mu = \int \sum_n f_n d\mu$.

> [!done]
> Note that 
> $$
> \begin{aligned}
>\sum_{n=1}^{\infty}\int_{\Omega}|f_n|{d}\mu&=\lim_{m\to\infty}\sum_{n=1}^{m}\int_{\Omega}|f_n|{d}\mu=\lim_{m\to\infty}\int_{\Omega}\sum_{n=1}^{m}|f_n|{d}\mu\\
>&\overset{\text{MCT}}{=}\int_{\Omega}\sum_{n=1}^{\infty}|f_n|{d}\mu<\infty
>\end{aligned}
> $$
> and 
> $$
> \begin{aligned}
>\sum_{n=1}^{\infty}\int_{\Omega}f_n{d}\mu=\lim_{m\to\infty}\sum_{n=1}^{m}\int_{\Omega}f_n{d}\mu=\lim_{m\to\infty}\int_{\Omega}\sum_{n=1}^{m}f_n{d}\mu
>\end{aligned}
> $$
> We W.T.S. 
> $$
> \lim_{m\to\infty}\int_\Omega \sum_{n=1}^{m}f_n{d}\mu=\int_{\Omega}\sum_{n=1}^{\infty}f_n{d}\mu
> $$
> Then 
> $$
> \begin{aligned}
>\left|\int_\Omega \sum_{n=1}^{m}f_n{d}\mu-\int_{\Omega}\sum_{n=1}^{\infty}f_n{d}\mu\right|&=\left|\int_\Omega\sum_{n=m+1}^{\infty}f_n{d}\mu\right|\\
>&\le \int_\Omega\sum_{n=m+1}^{\infty}|f_n|{d}\mu\to0\text{ as }m\to\infty
>\end{aligned}
> $$