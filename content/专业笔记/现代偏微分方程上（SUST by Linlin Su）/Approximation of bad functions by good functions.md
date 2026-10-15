# Approximation of bad functions by good functions

2025.11.19, 2025.11.26 · [[PDE Note Week11LectureWed.pdf|Source, pp. 1–3]]; [[PDE Week12 Wed.pdf|continuation, pp. 1–3]]

[[Distributions (Schwartz)]] · [[Weak Derivatives]] · [[Chain Rule & Sobolev Space]]

## Regularization

Let $j$ be the [[Distributions (Schwartz)#Standard mollifier|standard mollifier]]. Write

$$
j_\varepsilon(x)=\varepsilon^{-n}j(x/\varepsilon),\qquad \Omega_\varepsilon=\{x\in\Omega:\operatorname{dist}(x,\partial\Omega)>\varepsilon\}.
$$

For $u\in L^1_{\mathrm{loc}}(\Omega)$, define

$$
u_\varepsilon(x)=\int_\Omega j_\varepsilon(x-y)u(y)\,dy\qquad(x\in\Omega_\varepsilon).
$$

For each $x\in\Omega$, this is well-defined when $0<\varepsilon<\operatorname{dist}(x,\partial\Omega)$. If $u\in L^p(\Omega)$, $1\le p\le\infty$, extend it by zero outside $\Omega$; then $u_\varepsilon=j_\varepsilon*u$ is defined on all of $\mathbb{R}^n$, because the convolution only integrates over a compact ball.

> [!lemma] Lemma 1 · Smoothness
> For $u\in L^1_{\mathrm{loc}}(\Omega)$, $u_\varepsilon\in C^\infty(\Omega_\varepsilon)$, and
> $$
> D^\alpha u_\varepsilon(x)=\int_\Omega D_x^\alpha j_\varepsilon(x-y)u(y)\,dy.
> $$
> If $u\in L^p(\Omega)$ and is extended by zero, then $u_\varepsilon\in C^\infty(\mathbb{R}^n)$. If $\Omega$ is also bounded, $u_\varepsilon$ has compact support in $\mathbb{R}^n$.

**Proof.** Fix $x\in\Omega_\varepsilon$ and a ball $B_\delta(x)\Subset\Omega$ with $\delta>\varepsilon$. For nearby $z$, the support of $j_\varepsilon(z-\cdot)$ stays in this ball. The difference quotient in direction $e_i$ is dominated by

$$
\|\partial_i j_\varepsilon\|_\infty|u(y)|\mathbf1_{B_\delta(x)}(y),
$$

which is integrable. Dominated convergence permits differentiation under the integral. To prove continuity of the derivative, use the domination $2\|\partial_i j_\varepsilon\|_\infty|u|\mathbf1_{B_\delta(x)}$ and continuity of the kernel. Repeat for every order. The zero-extended case is local on $\mathbb{R}^n$; if $\Omega$ is bounded, the support lies within distance $\varepsilon$ of $\overline\Omega$. **QED**

## Convergence of regularizations

> [!lemma] Lemma 2 · Locally uniform convergence
> If $u\in C(\Omega)$ and $\Omega'\Subset\Omega$, then $u_\varepsilon\to u$ uniformly on $\overline{\Omega'}$.

**Proof.** Choose $\Omega'\Subset\Omega''\Subset\Omega$. For small $\varepsilon$, use the change of variables $y=x-\varepsilon z$:

$$
u_\varepsilon(x)-u(x)=\int_{B_1}j(z)[u(x-\varepsilon z)-u(x)]\,dz.
$$

Uniform continuity on $\overline{\Omega''}$ makes the bracket uniformly small for $x\in\overline{\Omega'}$, $|z|\le1$, and $\int j=1$. **QED**

> [!lemma] Lemma 3 · Almost-everywhere convergence
> If $u\in L^1_{\mathrm{loc}}(\Omega)$, then $u_\varepsilon(x)\to u(x)$ at every Lebesgue point of $u$, hence a.e.

**Proof.** At a Lebesgue point $x$,

$$
|u_\varepsilon(x)-u(x)|\le\|j\|_\infty\varepsilon^{-n}\int_{B_\varepsilon(x)}|u(y)-u(x)|\,dy\longrightarrow0.
$$

The final limit is the Lebesgue differentiation theorem, in its mean-absolute-oscillation form. **QED**

> [!lemma] Lemma 4 · $L^p$ convergence
> If $1\le p<\infty$ and $u\in L^p_{\mathrm{loc}}(\Omega)$, then $u_\varepsilon\to u$ in $L^p_{\mathrm{loc}}(\Omega)$. If $u\in L^p(\Omega)$ is zero-extended, convergence holds in $L^p(\mathbb{R}^n)$.

**Proof.** For $\Omega'\Subset\Omega''\Subset\Omega$, let $\widehat u=u\mathbf1_{\Omega''}$, extended by zero. Minkowski's inequality gives

$$
\|u_\varepsilon-u\|_{L^p(\Omega')}\le\int_{B_1}j(z)\|\widehat u(\cdot-\varepsilon z)-\widehat u\|_{L^p(\mathbb{R}^n)}\,dz.
$$

Translations are continuous in $L^p$ for $p<\infty$. The integrand tends to $0$ and is dominated by $2j(z)\|\widehat u\|_p$. Apply dominated convergence. For the global result, use the zero extension directly. **QED**

> [!remark] 整理注
> After $y=x-\varepsilon z$, the kernel is $j(z)$, not $j_\varepsilon(z)$. Also, the general $L^p$ convergence result requires $p<\infty$; an arbitrary $L^\infty$ function need not be approximated in the essential-supremum norm by mollification.

## Density in Lebesgue spaces

For $1\le p<\infty$, the preceding lemmas imply that smooth functions in $L^p(\Omega)$ are dense in $L^p(\Omega)$. More precisely,

> [!thm]
> $C_c^\infty(\Omega)$ is dense in $L^p(\Omega)$ for every open $\Omega\subset\mathbb{R}^n$ and $1\le p<\infty$.

**Proof.** Use the compact exhaustion

$$
\Omega_k=\{x\in\Omega:|x|<k,\ \operatorname{dist}(x,\partial\Omega)>1/k\},\qquad u_k=u\mathbf1_{\Omega_k}.
$$

Then $u_k\to u$ in $L^p(\Omega)$ by dominated convergence. For fixed $k$, $(u_k)_\varepsilon\to u_k$ in $L^p$, and for sufficiently small $\varepsilon$ its support is compactly contained in $\Omega$. Given $\delta>0$, first make $\|u_k-u\|_p<\delta/2$, then choose $\varepsilon$ with $\|(u_k)_\varepsilon-u_k\|_p<\delta/2$. The triangle inequality finishes the proof. **QED**

> [!remark]
> If a bounded-domain function is zero-extended, its mollification has compact support in $\mathbb{R}^n$, but generally not in $\Omega$. Truncation away from the boundary is why the proof above produces elements of $C_c^\infty(\Omega)$.

## Regularization and weak derivatives

> [!lemma] Lemma 5 · Commutation in the interior
> If $u\in L^1_{\mathrm{loc}}(\Omega)$ has a weak derivative $D^\alpha u\in L^1_{\mathrm{loc}}(\Omega)$, then
> $$
> D^\alpha u_\varepsilon(x)=(D^\alpha u)_\varepsilon(x)\qquad(x\in\Omega_\varepsilon).
> $$

**Proof.** For $x\in\Omega_\varepsilon$, $j_\varepsilon(x-\cdot)\in C_c^\infty(\Omega)$. Hence

$$
D^\alpha u_\varepsilon(x)=\int_\Omega D_x^\alpha j_\varepsilon(x-y)u(y)\,dy=(-1)^{|\alpha|}\int_\Omega D_y^\alpha j_\varepsilon(x-y)u(y)\,dy=\int_\Omega j_\varepsilon(x-y)D^\alpha u(y)\,dy.
$$

The two signs cancel. **QED**

Near $\partial\Omega$, the kernel may fail to be a test function in $\Omega$. Thus zero-extending $u$ and its interior weak derivative does not generally preserve this identity on all of $\Omega$. If $u$ has compact support in $\Omega$, the zero-extension identity holds globally, since there is no boundary contribution.

Applications include [[Weak Derivatives#Uniqueness and the fundamental lemma|uniqueness of weak derivatives]] and [[Weak Derivatives#Zero weak gradient|constancy for zero weak gradient]].

## Characterization by smooth approximation

> [!thm]
> For $u,v\in L^1_{\mathrm{loc}}(\Omega)$, $v=D^\alpha u$ weakly if and only if there are $u_k\in C^\infty(\Omega)$ such that
> $$
> u_k\longrightarrow u\text{ in }L^1_{\mathrm{loc}}(\Omega),\qquad D^\alpha u_k\longrightarrow v\text{ in }L^1_{\mathrm{loc}}(\Omega).
> $$

**Proof, reverse direction.** For a fixed test function, integrate by parts for $u_k$ and pass to the local $L^1$ limits:

$$
\int_\Omega v\varphi\,dx=\lim_k\int_\Omega D^\alpha u_k\varphi\,dx=(-1)^{|\alpha|}\lim_k\int_\Omega u_kD^\alpha\varphi\,dx=(-1)^{|\alpha|}\int_\Omega uD^\alpha\varphi\,dx.
$$

**Forward direction.** Use the bounded exhaustion $\Omega_k$ above and choose $\varepsilon_k\downarrow0$ with $\varepsilon_k<1/(2k)$. Define the globally smooth function

$$
u_k=j_{\varepsilon_k}*(u\mathbf1_{\Omega_k}).
$$

For each fixed $K\Subset\Omega$, the convolution ball around every $x\in K$ lies inside $\Omega_k$ for sufficiently large $k$. On that compact set, $u_k$ is the ordinary local regularization of $u$, so Lemmas 4 and 5 imply both required limits. The same construction works simultaneously for any finite collection of weak derivatives. **QED**

> [!remark] 整理注
> On an unbounded domain, the condition $\operatorname{dist}(x,\partial\Omega)>1/k$ alone does not make the inner set relatively compact. The extra cutoff $|x|<k$ ensures that $u\mathbf1_{\Omega_k}\in L^1$ and makes the global convolution construction legitimate.
