>[!question] 1.2.1
 >Suppose $X$ and $Y$ are random variables on $(\Omega, \mathcal{F}, \mathbb{P})$ and let $A \in \mathcal{F}$. Show that if we let $Z(\omega) = X(\omega)$ for $\omega \in A$ and $Z(\omega) = Y(\omega)$ for $\omega \in A^c$, then $Z$ is a random variable.

>[!done] 
>For any Borel set $B\in\mathcal{B}$, we have 
>$$
>\begin{aligned}
>Z^{-1}(B)&=\left[Z^{-1}(B)\cap A\right]\cup\left[Z^{-1}(B)\cap A^c\right]\\
>&=\left[X^{-1}(B)\cap A\right]\cup\left[Y^{-1}(B)\cap A^c\right]\in\mathcal{F}
>\end{aligned}
>$$
>Hence, $Z$ is a r.v.

>[!question] 1.2.2. 
>Let $\chi$ have the standard normal distribution. Use Theorem 1.2.6 to get upper and lower bounds on $\mathbb{P}(\chi \geq 4)$.

>[!done]
>Thm1.2.6: 
>$$
>(x^{-1} - x^{-3}) \exp(-x^2/2) \leq \int_x^\infty \exp(-y^2/2) dy \leq x^{-1} \exp(-x^2/2)
>$$
>Then we have 
>$$
>\begin{aligned}
>&\mathbb{P}(\chi\ge4)=\frac{1}{\sqrt{2\pi}}\int_{4}^{\infty}e^{-\frac{x^2}{2}}{d}x\\
>\Longrightarrow&\frac{15}{64\sqrt{2\pi}}e^{-8}\le\mathbb{P}(\chi\ge4)\le\frac{1}{4\sqrt{2\pi}}e^{-8}
>\end{aligned}
>$$

>[!question] 1.2.3. 
>Show that a distribution function has at most countably many discontinuities.

>[!done] 
>It is a well-known conclusion in real analysis. 

>[!question] 1.2.4. 
>Show that if $F(x) = \mathbb{P}(X \leq x)$ is continuous then $Y = F(X)$ has a uniform distribution on $(0,1)$, that is, if $y \in [0,1]$, $\mathbb{P}(Y \leq y) = y$.

>[!done] 
>

>[!question] 1.2.5.
> Suppose $X$ has continuous density $f$, $\mathbb{P}(\alpha \leq X \leq \beta) = 1$ and $g$ is a function that is strictly increasing and differentiable on $(\alpha, \beta)$. Then $g(X)$ has density $f(g^{-1}(y))/g'(g^{-1}(y))$ for $y \in (g(\alpha), g(\beta))$ and $0$ otherwise. When $g(x) = ax + b$ with $a > 0$, $g^{-1}(y) = (y - b)/a$ so the answer is $(1/a)f((y - b)/a)$.

>[!question] 1.2.6. 
>Suppose $X$ has a normal distribution. Use the previous exercise to compute the density of $\exp(X)$. (The answer is called the **lognormal distribution**.)

>[!question] 1.2.7. (i) 
>Suppose $X$ has density function $f$. Compute the distribution function of $X^2$ and then differentiate to find its density function. 


>[!question] 1.2.7.(ii) 
>Work out the answer when $X$ has a standard normal distribution to find the density of the **chi-square distribution**.