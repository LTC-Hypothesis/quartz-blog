# Elementary Properties and Examples
## Elementary Properties
we denote $\mathbb{F}$ either $\mathbb{R}$ or $\mathbb{C}$.

> [!def] Semi-inner product
> If $X$ is a vector space over $\mathbb{F}$, a semi-inner product on $X$ is a function $u: X\times X  \to \mathbb{F}$ such that for all $\alpha,\beta$ in $\mathbb{F}$, and $x, y, z \in X$, the following are satisfied:
> 1. $u(\alpha x + \beta y,z) = \alpha u(x,z) + \beta u(y,z)$
> 2. $u(x,\alpha y + \beta z) = \bar{\alpha}u(x,y) + \bar{\beta}u(x,z)$
> 3. $u(x,x)\ge 0$
> 4. $u(x,y) = \overline{u(y,x)}$

> [!warning]
> 1. If $\alpha = 0$ or $\beta = 0$, $u(x,0) = (0,y) = 0, \forall x,y\in X$

> [!def] Inner product
> An inner product on $X$ is a semi-inner product that also satisfies the following
> $$u(x,x) = 0 \Longrightarrow x=0$$
> 
> We denote inner product $\left\langle x,y\right\rangle = u(x,y)$

> [!thm] The Cauchy-Bunyakowsky-Schwarz Inequality(CBS)
> If $\left \langle \cdot,\cdot \right \rangle$ is a semi-inner product on $X$, then $$|\left \langle x,y \right \rangle|^2\le \left \langle x,x \right \rangle\left \langle y,y \right \rangle$$
> 
> for all $x$ and $y$ in$X$. Moreover, equality occurs if and only if there are scalars $\alpha$ and $\beta$, both not 0, such that $\left\langle \beta x + \alpha y, \beta x + \alpha y\right\rangle$ = 0. 
> 
> ^970a9c

> [!proposition] Norm
> If $\left \langle \cdot,\cdot \right \rangle$ is a semi-inner product on $X$ and $||x|| = \sqrt{\left \langle x,x \right \rangle}$, then
> 2. $||x+y||\le ||x|| + ||y||$
> 3. $||\alpha x|| = |\alpha| ||x||$
> If $\left \langle \cdot,\cdot \right \rangle$ is an inner product, then 
> 4. $||x|| = 0\Longrightarrow x = 0$

> [!proposition] Polar identity
> If $\left \langle \cdot,\cdot \right \rangle$ is a semi-inner product on $X$ and $x,y\in X$, then$$||x+y||^2 = ||x||^2 + 2Re\left\langle x,y\right\rangle + ||y||^2$$

> [!def] Hilbert Space
> Define metric:$d(x,y) = ||x-y||$. A Hilbert space is a vector space $H$ is a **complete metric space** with $d(\cdot,\cdot)$

## Examples
$L^2(\mu)$ is a typical Hilbert space in measure theory.

> [!example] $L^2(\mu)$
> The inner product is deined as $\left\langle f,g\right\rangle = \int_{X}f\bar{g}{d}\mu$, norm $||f|| = \left(\int_{X}|f|^2{d}\mu\right)^{\frac{1}{2}}$

Now we introduce an example of a Hilbert space from analytic function theory.

> [!example] Bergman space
> If $G$ is an open subset of the complex plane $\mathbb{C}$, $f$ is analytic function on $G$, then
> $$L^2_a(G) = \left\{f:G\to \mathbb{C}\ |\ \int_G |f(z)|^2{d}x{d}y<+\infty\right\}$$

> [!warning]
> Note that $L^2_a(G)\subseteq L^2(\mu)$, since let $\mu = Leb(G)$.So that $L^2_a(G)$ has a natural inner product and norm from $L^2(\mu)$.
> 
> ^4d4530

> [!lemma]
> If $f$ is analytic in a neighborhood of $\bar{B}(a,r)$ then $$f(a) = \frac{1}{\pi r^2}\int_{B(a,r)}f(z){d}z$$
> 
> ^53b497

**Proof** By mean value Theorem, if $0< t\le r$, then $$f(a) = \frac{1}{2\pi }\int_{-\pi}^{\pi}f(a+te^{i\theta}){d}\theta$$
Hence, for RHS 
$$\frac{1}{\pi r^2}\int_{B(a,r)}f(z){d}z = \frac{1}{\pi r^2}\int_{0}^{r}t\int_{-\pi}^{\pi}f(a+te^{\theta}){d}\theta{d}t = \frac{2}{r^2}f(a)\int_{0}^{r}t{d}t = f(a)$$
Indeed, $f(a) = \frac{1}{\pi r^2}\int_{B(a,r)}f(z){d}z$. **QED**

> [!lemma]
> If $f\in L^2_a(G)$, $a\in G$, and $0<r<dist(a,\partial G)$, then $$|f(a)|\le \frac{1}{r\sqrt{\pi}}||f||_{L^2(G)}$$
> 
> ^b919d4

**Proof** Since $0<r<dist(a,\partial G)$, the ball $\bar{B}(a,r)\subset G$ and $f$ is analytic on ${B}(a,r)$. By [[#^53b497|Lemma]] and [[#^970a9c | CBS]], 
$$|f(a)| = \frac{1}{\pi r^2}\left|\int_{B(a,r)}f(z)\cdot 1{d}z\right| \le \frac{1}{\sqrt{\pi}r}\left(\int_{B(a,r)}|f(z)|^2{d}z\right)^{\frac{1}{2}} = \frac{1}{\sqrt{\pi}r}||f||_{L^2(G)}$$**QED**

Now we check $L^2_a(G)$ is a Hilbert space.

> [!thm]
> $L^2_a(G)$ is a Hilbert space.

**Proof** Since [[Introduction of Hilbert Space#^4d4530| warning]], it suffices to show that $L^2_a(G)$ is a closed subspace of $L^2(\mu)$. Suppose $\{f_n\}\subset L^2_a(G)$ and $f\in L^2(\mu)$ s.t. $\int_{X}|f_n - f|^2{d}\mu\to 0$ as $n\to \infty$. W.T.S: $f\in L^2_a(G)$. Suppose $\bar{B}(a,r)\subset G$ and $0<\rho <dist({B}(a,r),\partial G)$. By [[Introduction of Hilbert Space#^b919d4| Lemma]], for any $n,m$ and $|z - a| \le \rho$ s.t.$$|f_n - f_m|\le \frac{1}{\sqrt{\pi (\rho - r)}}||f_n - f_m||_{L^2_a(G)}$$
Thus $\{f_n\}$ is a uniformly Cauchy sequence on any closed disk in G. By theorem of complex analysis, $\exists \ g$ is analytic on G s.t. $f_n\to g \ u.i$. Since $f_n\to f$ in $L^2\Longrightarrow f_n\to f$ in $\mu\Longrightarrow \exists \{f_{n_k}\}s.t. f_{n_k}\to f \ a.e.$ Hence, $f= g\in L^2_a(G) \ a.e.$ **QED**

---

## Exercises

> [!question]
> Let $I$ be any set and let $l^2 (I)$ denote the set of all functions $x: I\to \mathbb{F}$ such that $x(i) = 0$ for all but a countable number of $i$ and $\sum_{i\in I}|x(i)|^2<\infty$. For $x$ and $y$ in $l^2(I)$ define $$\left\langle x,y \right\rangle = \sum_{i\in I}x(i)\overline{y(i)}$$
> Show that $l^2(I)$ is a Hilbert space.

> [!done]
> W.T.S: $l^2(I)$ is complete with metric $d(x,y) = \left(\sum_{i\in I}|x(i) - y(i)|^2\right)^{\frac{1}{2}}$. Suppose $\{x_n\}$ is Cauchy sequence of $l^2(I)$ i.e. $\forall \varepsilon>0$, $\exists N\in \mathbb{N}$, s.t. $n,m > N$, $$d(x_n(i),x_m(i)) = \left(\sum_{i\in I}|x_n(i) - x_m(i)|^2\right)^{\frac{1}{2}}<\varepsilon$$ 
> Note that $|x_n(i) - x_m(i)|<\left(\sum_{i\in I}|x_n(i) - x_m(i)|^2\right)^{\frac{1}{2}}<\varepsilon$. It implies $\{x_n(i)\}$ is a Cauchy Sequence for fixed $i\in I$. Hence, there exists $x(i)$ satisfies $|x_n(i) - x(i)|\to 0$ as $n\to \infty$. Choose $\frac{\varepsilon}{2^i}>0$, as $n>N$ $$d(x_n(i),x(i)) = \left(\sum_{i\in I}|x_n(i) - x(i)|^2\right)^{\frac{1}{2}}<\sum_{i\in I}\frac{\varepsilon}{2^i}<\varepsilon$$
> Hence, $l^2(I)$ is complete and it is a Hilbert space.

> [!warning]
> - When $I = \mathbb{N}$, $l^2(I) = l^2$
> - $\Omega = 2^I$ and for $E\subset \Omega$, $$\mu = \begin{cases}|E|,E \mbox{ is finite} \\
>   \infty, E\mbox{ is infinite}\end{cases}$$
>   then $l^2(I) = L^2(\Omega,\mu)$

> [!question]
> Let $H = \left\{f: [0,1]\to \mathbb{F}, f\in C_{abs}(0,1) \ |\ f(0) = 0,f'(x)\in L^2(0,1)\right\}$ where $C_{abs}(0,1)$ is the set of all absolutly continuous function on $(0,1)$. Define inner product $\left\langle f,g\right\rangle = \int_{0}^{1}f'(t)\overline{g'(t)}{d}t, f,g\in H$. Show that $H$ is a Hilbert space.

> [!done]
> Suppose $\{f_n\}\subset H$ is a Cauchy sequence, that is $\forall \varepsilon>0$, $\exists N$, s.t. $n,m>N$, 
> $$
> d^2(f_n,f_m) = ||f_n-f_m||^2 = \int_{0}^{1}|f'_n(t)-f'_m(t)|^2{d}t<\varepsilon
> $$ 
> Since $f'_n\in L^2(0,1)$ and $L^2(0,1)$ is complete, there exists $g\in L^2(0,1)$ s.t. $f'_n(t)\to g$ in $L^2(0,1)$ as $n\to \infty$ i.e. 
> $$
> \int_{0}^{1}|f'_n(t)-g(t)|^2{d}t\to 0
> $$
> Define $f(x) = \int_{0}^{x}g(t){d}t\in C_{abs},f'(x) = g(x)$, then 
> $$
> ||f_n(x)-f(x)||^2=\int_{0}^{1}|f'_n(x)-g(x)|^2{d}t\to 0
> $$
> Hence, $H$ is a Hilbert space.

> [!question] A variation
> Let $n \ge 2$ and let $f\in H$ satisfy:
> 1. $f(0) = 0$ 
> 2. For $0\le k\le n-1$, $f^{(k)}$ exists for $t\in [0,1]$ and  is continuous on [0, 1]
> 3. $f^{(n-1)}$ is absolutely continuous and $f^{(n)}\in L^2(0, 1)$.
> 
> For $f$ and $g$ in $H$, define inner product$$\left\langle f,g\right\rangle = \sum_{k=1}^{n}\int_{0}^{1}f^{(k)}(t)\overline{g^{(k)}(t)}{d}t$$ 
> Show that $H$ is a Hilbert space.

> [!done]
> Suppose $\{f_j\}\subset H$ is a Cauchy sequence, that is $\forall \varepsilon>0$, $\exists N$, s.t. $j,m>N$
> $$
> |f^{(k)}_j-f^{(k)}_m|< ||f_j-f_m||^2 = \sum_{k=1}^{n}\int_{0}^{1}|f^{(k)}_j(t)-f^{(k)}_m(t)|^2{d}t<\varepsilon
> $$
> Since $f^{(k)}_j\in L^2(0,1)$ and $L^2(0,1)$ is complete, there exists $g_k\in L^2(0,1)$ s.t. $f^{(k)}_j\to g_k$ in $L^2(0,1)$ as $j\to\infty$. For case $k=n$, we define 
> $$
> h_j(t)=\int_0^tf^{(n)}_j(s){d}s, H(t)=\int_0^tg_n(s){d}s
> $$
> then 
> $$
> |h_j(t)-H(t)|\le\int_0^1|f^{(n)}_j(s)-g_n(s)|{d}s\le\|f^{(n)}_j-g_n\|^2\to0,as \ j\to\infty
> $$
> Hence, $h_j$ uniformly converge to $H(t)$ and converge in $L^2$. Since $f^{(n-1)}$ is absolutely continuous, then 
> $$
> f^{(n-1)}_j(t)=f^{(n-1)}_j(0)+\int_{0}^{t}f^{(n)}_j(s){d}s=f^{(n-1)}_j(0)+h_j(t)
> $$
> Note that $f^{(n-1)}_j(t)-h_j(t)$ is convergent and converges to $g_{n-1}(t)-H(t)$ in $L^2$, so is $f^{(n-1)}_j(0)$ and we note as $C_{n-1}$. By product, we have 
> $$
> g_{n-1}(t)=\int_{0}^{t}g_{n}(s){d}s+C_{n-1}, g'_{n-1}(t)=g_n(t),a.e.
> $$
> Hence, $g_{n-1}$ is absolutely continuous. Similarly, for $k=n-1,n-2,\cdots,1$, we repeat above process adn get 
> $$
> g_{k}=\int_{0}^{t}g_{k+1}(s){d}s+C_{k},k=1,2,\cdots,n-1
> $$
> and we define 
> $$
> f(t)=\int_{0}^{t}g_1(s){d}s\in H
> $$
> Finally, we should prove $f_j\to f$ in the norm in $H$. 
> $$
> \begin{align}
> \|f_j-f\|^2&=\sum_{k=1}^{n}\int_0^1|f^{(k)}_j(t)-f^{(k)}(t)|{d}t\\
> &=\sum_{k=1}^{n}\int_0^1|f^{(k)}_j(t)-g_k(t)|{d}t\\
> &\le \sum_{k=1}^{n}\|f^{(k)}_j(t)-g_k(t)\|^2\to0,as \ j\to\infty
> \end{align}
> $$
> Hence, $H$ is a Hilbert space.

> [!question]
> Let $u$ be a semi-inner product on $X$ and put $\mathcal{N} = \{x\in X\ |\ u(x,x)=0\}$. Show that 
> 4. $\mathcal{N}$ is a linear subspace of $X$
> 5. If $$\left\langle x+\mathcal{N},y+\mathcal{N}\right\rangle = u(x,y)$$
>    in the quotient space $X/\mathcal{N}$, then $\left\langle\cdot,\cdot\right\rangle$ is a well-defined inner product on $X/\mathcal{N}$.

> [!done]
> 6. Trially, $\mathcal{N}\subseteq X$. Suppose $a,b\in\mathbb{F}$ and $x,y\in \mathcal{N}$, then$$u(ax+by,ax+by)=a\bar{b}u(x,y)+\overline{a\bar{b}u(x,y)}$$Note [[#^970a9c|CBS inequality]] holds for semi-inner product, then $|u(x,y)|^2\le |u(x,x)||u(y,y)|=0$. Hence, $u(ax+by,ax+by)=0$. Hence, $\mathcal{N}$ is a linear subspace of $X$.
> 7. Firstly, we check $\langle\cdot,\cdot\rangle$ is well-defined. For $x+\mathcal{N}=x'+\mathcal{N}$ and $y+\mathcal{N}=y'+\mathcal{N}$, then $x-x',y-y'\in\mathcal{N}$. By CBS inequality, 
>    $$
>    |u(x-x',y)|^2\le|u(x-x',x-x')||u(y,y)|=0
>    $$
>    $$
>    |u(x',y-y')|^2\le|u(x',x')||u(y-y',y-y')=0|
>    $$
>    Then $u(x,y)-u(x',y')=u(x-x',y)-u(x',y-y')=0$. It implies the inner product is dependent with represented element.
>    Next, we check the properties of inner product. 
>    $$
>    \left\langle y+\mathcal{N},x+\mathcal{N}\right\rangle=u(y,x)=\overline{u(x,y)}=\overline{\left\langle x+\mathcal{N},y+\mathcal{N}\right\rangle}
>    $$
>    $$
>    \left\langle x+\mathcal{N},x+\mathcal{N}\right\rangle=u(x,x)\ge0
>    $$
>    $u(x,x)=0$ iff $x\in \mathcal{N}$ and $x+\mathcal{N}=0$. Hence, $\langle\cdot,\cdot\rangle$ is a inner product in $H$

> [!question]
> Let $\mathcal{H}$ be a Hilbert space over $\mathbb{R}$ and show that there is a Hilbert space $\mathcal{X}$ over $\mathbb{C}$ and a map $U: \mathcal{H} \to \mathcal{X}$ such that 
> (a) $U$ is linear; 
> (b) $\langle Uh_1, Uh_2 \rangle = \langle h_1, h_2 \rangle$ for all $h_1, h_2$ in $\mathcal{H}$; 
> (c) for any $k$ in $\mathcal{X}$ there are unique $h_1, h_2$ in $\mathcal{X}$ such that $k = Uh_1 + iUh_2$. 
> ($\mathcal{X}$ is called the **complexification** of $\mathcal{H}$.)

> [!done]
> (To be completed)

> [!question]
> If $G = \{z \in \mathbb{C}: 0 < |z| < 1\}$ show that every $f$ in $L_a^2(G)$ has a removable singularity at $z = 0$.

> [!done]
> (To be completed)

> [!question]
> Let $G$ be an open subset of $\mathbb{C}$ and show that if $a \in G$, then $\{f \in L_a^2(G): f(a) = 0\}$ is closed in $L_a^2(G)$.

> [!done]
> (To be completed)

> [!question]
> If $\{h_n\}$ is a sequence in a Hilbert space $H$ such that $\sum_{n=1}^{\infty}||h_n||<\infty$, then show that $\sum_{n=1}^{\infty}h_n$ converges in $H$

> [!done]
> Note that $S_n = \sum_{k=1}^{n}h_k$. Since $H$ is a Hilbert space, it suffices to show that $\{S_n\}$ is a Cauchy sequence.$\forall \varepsilon>0$, since $\sum_{n=1}^{\infty}||h_n||<\infty$, $\exists N$, s.t. $n>N$, $\sum_{k\ge n}||h_k||<\varepsilon$. Then for $n>m>N$,
> $$
> ||S_n - S_m|| = \left\|\sum_{k=m+1}^{n}h_k\right\|\le \sum_{k=m+1}^{n}||h_k||\le\sum_{k=m+1}^{\infty}||h_k||<\varepsilon
> $$
> Hence, $\{S_n\}$ is convergence in H.