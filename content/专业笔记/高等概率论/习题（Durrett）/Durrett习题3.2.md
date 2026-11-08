> [!question] 3.2.1.
> Give an example of random variables $X_n$ with densities $f_n$ so that $X_n \Rightarrow$ a uniform distribution on $(0,1)$ but $f_n(x)$ does not converge to 1 for any $x \in [0,1]$.

> [!done]
> 

> [!question] 3.2.2.**Convergence of maxima.**
>  Let $X_1, X_2, \dots$ be independent with distribution $F$, and let $M_n = \max_{m \leq n} X_m$. Then $\mathbb{P}(M_n \leq x) = F(x)^n$. Prove the following limit laws for $M_n$:

> [!question] 3.2.2. (i)
> (i) If $F(x) = 1 - x^{-\alpha}$ for $x \geq 1$ where $\alpha > 0$ then for $y > 0$
> $$
> \mathbb{P}(M_n/n^{1/\alpha} \leq y) \to \exp(-y^{-\alpha})
> $$

> [!done]
> We compute 
> $$
> \begin{aligned}
>\mathbb{P}(M_n\le n^\frac{1}{\alpha}y)=&\left(F(n^\frac{1}{\alpha}y)\right)^n\\
>=&\left(1-\frac{y^{-\alpha}}{n}\right)^n\to e^{-y^{-\alpha}}\text{ as }n\to\infty
>\end{aligned}
> $$

> [!question] 3.2.2. (ii)
> (ii) If $F(x) = 1 - |x|^\beta$ for $-1 \leq x \leq 0$ where $\beta > 0$ then for $y < 0$
> $$
> \mathbb{P}(n^{1/\beta} M_n \leq y) \to \exp(-|y|^\beta)
> $$

> [!done]
> We compute 
> $$
> \mathbb{P}\left(M_n\le\frac{y}{n^\frac{1}{\beta}}\right)=\left(1-\frac{|y|^\beta}{n}\right)^n\to e^{-|y|^\beta}
> $$

> [!question] 3.2.2. (iii)
> (iii) If $F(x) = 1 - e^{-x}$ for $x \geq 0$ then for all $y \in (-\infty, \infty)$
> $$
> \mathbb{P}(M_n - \log n \leq y) \to \exp(-e^{-y})
> $$
> The limits that appear above are called the **extreme value distributions**. The last one is called the **double exponential** or **Gumbel distribution**. Necessary and sufficient conditions for $(M_n - b_n)/a_n$ to converge to these limits were obtained by Gnedenko (1943). For a recent treatment, see Resnick (1987).

> [!done]
> We compute 
> $$
> \mathbb{P}(M_n\le y+\log{n})=\left(1-\frac{e^{-y}}{n}\right)^n\to\exp(-e^{-y})
> $$

> [!question] 3.2.3. (i)
> Let $X_1, X_2, \dots$ be i.i.d. and have the standard normal distribution. (i) From Theorem 1.2.6, we know
> $$
> \mathbb{P}(X_i > x) \sim \frac{1}{\sqrt{2\pi}x} e^{-x^2/2} \quad \text{as } x \to \infty
> $$
> Use this to conclude that for any real number $\theta$
> $$
> \mathbb{P}(X_i > x + (\theta/x))/\mathbb{P}(X_i > x) \to e^{-\theta}
> $$

> [!done]
> We compute 
> $$
> \frac{\mathbb{P}(X_i>x+\frac{\theta}{x})}{\mathbb{P}(X_i>x)}\sim\frac{x^2}{x^2+\theta}e^{-\left(\frac{\theta(2x^2+1)}{2x^2}\right)}\to e^{-\theta}\text{ as }x\to\infty
> $$

> [!question] 3.2.3. (ii)
> (ii) Show that if we define $b_n$ by $\mathbb{P}(X_i > b_n) = 1/n$
> $$
> \mathbb{P}(b_n(M_n - b_n) \leq x) \to \exp(-e^{-x})
> $$

> [!done]
> Note that 
> $$
> \frac{\mathbb{P}(X_i>x+\frac{\theta}{x})}{\mathbb{P}(X_i>x)}\sim e^{-\theta}\text{ as }x\to\infty
> $$
> then 
> $$
> \mathbb{P}\left(X_i>b_n+\frac{x}{b_n}\right)=\frac{e^{-x}}{n}+o\left(\frac{1}{n}\right)
> $$
> and thus the maxima distribution is 
> $$
> \mathbb{P}\left(M_n\le b_n+\frac{x}{b_n}\right)=\left(1-\frac{e^{-x}}{n}+o\left(\frac{1}{n}\right)\right)^n\to\exp\left(-e^{-x}\right)
> $$

> [!question] 3.2.3. (iii)
> (iii) Show that $b_n \sim (2\log n)^{1/2}$ and conclude $M_n/(2\log n)^{1/2} \to 1$ in probability.

> [!done]
> By tail estimation, 
> $$
> \frac{1}{n}\sim\frac{1}{\sqrt{2\pi}b_n}e^{-\frac{b_n^2}{2}}\Longrightarrow n\sim \sqrt{2\pi}b_ne^{\frac{b_n^2}{2}}
> $$
> Then $b_n\to\infty$ and take log, we obtain the lof form estimation,
> $$
> \log{n}=\frac{b_n^2}{2}+\log{b_n}+o(1)\Longrightarrow b_n^2\sim2\log{n}
> $$
> Now it suffices to show that $\frac{M_n}{b_n^2}\xrightarrow{\mathbb{P}}1$. Let $Y_n=b_n(M_n-b_n)$, then it suffices to show that $\frac{Y_n}{b_n^2}\xrightarrow{\mathbb{P}}0$. For any $\varepsilon>0$, 
> $$
> \mathbb{P}(|Y_n|>\varepsilon b_n^2)=\mathbb{P}(Y_n>\varepsilon\cdot b_n^2)+\mathbb{P}(Y_n<-\varepsilon b_n^2)
> $$
> Denote $\mathbb{P}(Y_n\le x)$ by $F_n(x)$. By $F_n(x)\to\exp(-e^{-x})$, there exists $N_1$ and $K_1$, by the way, without loss of generality, we assume for $n\ge N_1$, $b_n^2>K_1$, which s.t. for $n\ge N_1,x<-K_1$, 
> $$
> \left|F_n(-\varepsilon b_n^2)-\exp(-e^{\varepsilon b_n^2})\right|<\frac{\varepsilon}{4}, \ \left|\exp{(-e^{-x})}\right|<\frac{\varepsilon}{4}
> $$
> then 
> $$
> |F_n(-\varepsilon b_n^2)|\le\left|F_n(-\varepsilon b_n^2)-\exp(-e^{\varepsilon b_n^2})\right|+\left|\exp{(-e^{\varepsilon b_n^2})}\right|<\frac{\varepsilon}{2}
> $$
> Similarly, there exists such $N_2,K_2$, for $n\ge N_2,b_n^2>K_2$, we also obtain
> $$
> \left|1-F_n(\varepsilon b_n^2)\right|\le|1-\exp(-e^{-\varepsilon b_n^2})|+|\exp(-e^{-\varepsilon b_n^2})-F_n(\varepsilon b_n^2)|<\frac{\varepsilon}{2}
> $$
> Now take $N=\max\{N_1,N_2\},K=\{K_1,K_2\}$, for $n\ge N,b_n^2>K$, 
> $$
> \mathbb{P}(|Y_n|\ge \varepsilon b_n^2)<\varepsilon
> $$
> Hence, $\frac{Y_n}{b_n^2}\xrightarrow{\mathbb{P}}0$ and thus $\frac{M_n}{\sqrt{2\log{n}}}\xrightarrow{\mathbb{P}}1$. 

> [!question] 3.2.4.**Fatou's lemma.**
> Let $g \geq 0$ be continuous. If $X_n \Rightarrow X_\infty$ then
> $$
> \liminf_{n \to \infty} \mathbb{E}g(X_n) \geq \mathbb{E}g(X_\infty)
> $$

> [!done]
> For fixed $M>0$, let $g_M(x)\triangleq g(x)\wedge M$ and thus $g_M(x)$ is a bounded continuous function and $g_M(x)\le g(x)$. Then we have $\mathbb{E}[g_M(X_n)]\to\mathbb{E}[g_M(X_\infty)]$ as $n\to\infty$. By $\mathbb{E}[g_M(X_n)]\le\mathbb{E}[g(X_n)]$, take $\liminf_{n\to\infty}$, 
> $$
> \mathbb{E}[g_M(X_\infty)]\le \liminf_{n\to\infty}\mathbb{E}[g(X_n)]
> $$
> Let $M\to+\infty$, we obtain $\mathbb{E}[g(X_\infty)]\le\liminf_{n\to\infty}\mathbb{E}[g(X_n)]$. 

> [!question] 3.2.5.**Integration to the limit.**
>  Suppose $g, h$ are continuous with $g(x) > 0$, and $|h(x)|/g(x) \to 0$ as $|x| \to \infty$. If $F_n \Rightarrow F$ and $\int g(x) dF_n(x) \leq C < \infty$ then
> $$
> \int h(x) dF_n(x) \to \int h(x) dF(x)
> $$

> [!done]
> 

> [!question] 3.2.6.**The Lévy Metric.**
>  Show that
> $$
> \rho(F, G) = \inf\{\epsilon : F(x-\epsilon) - \epsilon \leq G(x) \leq F(x+\epsilon) + \epsilon \text{ for all } x\}
> $$
> defines a metric on the space of distributions and $\rho(F_n, F) \to 0$ if and only if $F_n \Rightarrow F$.

> [!done]

> [!question] 3.2.7.**The Ky Fan metric**
>  on random variables is defined by
> $$
> \alpha(X, Y) = \inf\{\epsilon \geq 0 : \mathbb{P}(|X - Y| > \epsilon) \leq \epsilon\}
> $$
> Show that if $\alpha(X, Y) = \alpha$ then the corresponding distributions have Lévy distance $\rho(F, G) \leq \alpha$.

> [!done]

> [!question] 3.2.8.
> Let $\alpha(X, Y)$ be the metric in the previous exercise and let $\beta(X, Y) = \mathbb{E}(|X - Y|/(1 + |X - Y|))$ be the metric of Exercise 2.3.6. If $\alpha(X, Y) = a$ then
> $$
> a^2/(1 + a) \leq \beta(X, Y) \leq a + (1 - a)a/(1 + a)
> $$

> [!done]

> [!question] 3.2.9.
> If $F_n \Rightarrow F$ and $F$ is continuous then $\sup_x |F_n(x) - F(x)| \to 0$.

> [!done]

> [!question] 3.2.10.
> If $F$ is any distribution function there is a sequence of distribution functions of the form $\sum_{m=1}^n a_{n,m} 1_{(x_{n,m} \leq x)}$ with $F_n \Rightarrow F$.

> [!done]

> [!question] 3.2.11.
> Let $X_n, 1 \leq n \leq \infty$, be integer valued. Show that $X_n \Rightarrow X_\infty$ if and only if $\mathbb{P}(X_n = m) \to \mathbb{P}(X_\infty = m)$ for all $m$.

> [!done]

> [!question] 3.2.12.
> Show that if $X_n \to X$ in probability then $X_n \Rightarrow X$ and that, conversely, if $X_n \Rightarrow c$, where $c$ is a constant then $X_n \to c$ in probability.

> [!done]
> 

> [!question] 3.2.13.**Converging together lemma.**
>  If $X_n \Rightarrow X$ and $Y_n \Rightarrow c$, where $c$ is a constant then $X_n + Y_n \Rightarrow X + c$. A useful consequence of this result is that if $X_n \Rightarrow X$ and $Z_n - X_n \Rightarrow 0$ then $Z_n \Rightarrow X$.

> [!done]

> [!question] 3.2.14.
> Suppose $X_n \Rightarrow X$, $Y_n \geq 0$, and $Y_n \Rightarrow c$, where $c > 0$ is a constant then $X_n Y_n \Rightarrow cX$. This result is true without the assumptions $Y_n \geq 0$ and $c > 0$. We have imposed these only to make the proof less tedious.

> [!done]

> [!question] 3.2.15.
> Show that if $X_n = (X_n^1, \dots, X_n^n)$ is uniformly distributed over the surface of the sphere of radius $\sqrt{n}$ in $\mathbf{R}^n$ then $X_n^1 \Rightarrow$ a standard normal. Hint: Let $Y_1, Y_2, \dots$ be i.i.d. standard normals and let $X_n^i = Y_i(n/\sum_{m=1}^n Y_m^2)^{1/2}$.

> [!done]

> [!question] 3.2.16.
> Suppose $Y_n \geq 0$, $\mathbb{E}Y_n^\alpha \to 1$ and $\mathbb{E}Y_n^\beta \to 1$ for some $0 < \alpha < \beta$. Show that $Y_n \to 1$ in probability.

> [!done]

> [!question] 3.2.17.
> For each $K < \infty$ and $y < 1$ there is a $c_{y,K} > 0$ so that $\mathbb{E}X^2 = 1$ and $\mathbb{E}X^4 \leq K$ implies $\mathbb{P}(|X| > y) \geq c_{y,K}$.

> [!done]