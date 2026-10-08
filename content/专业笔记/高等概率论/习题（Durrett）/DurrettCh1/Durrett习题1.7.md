> [!question] 1.7.1.
> If $\int_X \int_Y |f(x,y)|\mu_2(dy)\mu_1(dx) < \infty$ then
> $$
> \int_X \int_Y f(x,y)\mu_2(dy)\mu_1(dx) = \int_{X \times Y} f d(\mu_1 \times \mu_2) = \int_Y \int_X f(x,y)\mu_1(dx)\mu_2(dy)
> $$
> **Corollary.** Let $X = \{1, 2, \ldots\}$, $\mathcal{A} =$ all subsets of $X$, and $\mu_1 =$ counting measure. If $\sum_n \int |f_n| d\mu < \infty$ then $\sum_n \int f_n d\mu = \int \sum_n f_n d\mu$.

> [!done]
> 

> [!question] 1.7.2.
> Let $g \geq 0$ be a measurable function on $(X, \mathcal{A}, \mu)$. Use Theorem 1.7.2 to conclude that
> $$
> \int_X g d\mu = (\mu \times \lambda)(\{(x,y) : 0 \leq y < g(x)\}) = \int_0^\infty \mu(\{x : g(x) > y\}) dy
> $$

> [!done]
> 

> [!question] 1.7.3.（i）
> Let $F, G$ be Stieltjes measure functions and let $\mu, \nu$ be the corresponding measures on $(\mathbf{R}, \mathcal{R})$. Show that
> $\int_{(a,b]} \{F(y) - F(a)\} dG(y) = (\mu \times \nu)(\{(x,y) : a < x \leq y \leq b\})$

>[!question] 1.7.3.(ii) 
> $\int_{(a,b]} F(y) dG(y) + \int_{(a,b]} G(y) dF(y) = F(b)G(b) - F(a)G(a) + \sum_{x \in (a,b]} \mu(\{x\})\nu(\{x\})$

>[!question] 1.7.3.(iii) 
> If $F = G$ is continuous then $\int_{(a,b]} 2F(y)dF(y) = F^2(b) - F^2(a)$.
> To see the second term in (ii) is needed, let $F(x) = G(x) = 1_{[0,\infty)}(x)$ and $a < 0 < b$.

> [!done]

> [!question] 1.7.4.
> Let $\mu$ be a finite measure on $\mathbf{R}$ and $F(x) = \mu((-\infty, x])$. Show that
> $$
> \int (F(x+c) - F(x)) dx = c\mu(\mathbf{R})
> $$

> [!done]
> We compute
> $$
> \begin{aligned}
>\int F(x+c)-F(x){d}x&=\int_{\mathbb{R}} \mu(-\infty,x+c]-\mu(-\infty,x]{d}x\\
>&=\int_{\mathbb{R}} \mu(x,x+c]{d}x\\
>&=\int_{\mathbb{R}} \int \mathbb{1}_{(x,x+c]}d\mu dx\\
>&=\int\int_{\mathbb{R}}\mathbb{1}_{(x,x+c]}dxd\mu=c\mu(\mathbb{R}) 
>\end{aligned}
> $$

> [!question] 1.7.5.
> Show that $e^{-xy} \sin x$ is integrable in the strip $0 < x < a, 0 < y$. Perform the double integral in the two orders to get:
> $$
> \int_0^a \frac{\sin x}{x} dx = \arctan(a) - (\cos a) \int_0^\infty \frac{e^{-ay}}{1+y^2} dy - (\sin a) \int_0^\infty \frac{y e^{-ay}}{1+y^2} dy
> $$
> and replace $1+y^2$ by $1$ to conclude $|\int_0^a (\sin x)/x dx - \arctan(a)| \leq 2/a$ for $a \geq 1$.

> [!done]