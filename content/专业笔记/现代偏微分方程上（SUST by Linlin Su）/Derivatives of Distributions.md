# Derivatives of Distributions

2025.11.3–11.17 · [[PDE Note Week9Mon + Week10Wed+Week11Mon.pdf|Source, pp. 1–5]]

[[Distributions (Schwartz)]] → [[Weak Derivatives]]

## Distributional derivatives

For $f\in C^1(\Omega)$, integration by parts against a test function gives

$$
\int_\Omega f_{x_i}\varphi\,dx=-\int_\Omega f\varphi_{x_i}\,dx.
$$

This motivates the definition for arbitrary distributions.

> [!def]
> For $F\in\mathscr D'(\Omega)$ and a multi-index $\alpha$, define
> $$
> \langle D^\alpha F,\varphi\rangle=(-1)^{|\alpha|}\langle F,D^\alpha\varphi\rangle\qquad\forall\varphi\in\mathscr D(\Omega).
> $$

Since differentiation preserves convergence in $\mathscr D(\Omega)$, $D^\alpha F$ is again a distribution. For a smooth function this agrees with its classical derivative.

### A jump produces a Dirac mass

Let $f_1\in C^1([0,\infty))$, $f_2\in C^1(( -\infty,0])$ and

$$
f(x)=\begin{cases}f_1(x),&x\ge0,\\f_2(x),&x<0.\end{cases}
$$

Writing $f'_{\mathrm{cl}}=f'_1$ on $(0,\infty)$ and $f'_2$ on $(-\infty,0)$, we have

$$
Df=f'_{\mathrm{cl}}+[f_1(0)-f_2(0)]\delta_0.
$$

**Proof.** For $\varphi\in C_c^\infty(\mathbb{R})$, split at $0$ and integrate by parts:

$$
\langle Df,\varphi\rangle=-\int_{-\infty}^0f_2\varphi'\,dx-\int_0^\infty f_1\varphi'\,dx=\int_{\mathbb{R}}f'_{\mathrm{cl}}\varphi\,dx+[f_1(0)-f_2(0)]\varphi(0).
$$

The endpoint terms at infinity vanish because $\varphi$ has compact support. **QED**

## Distributional solutions and the formal adjoint

Let

$$
Lu=\sum_{|\alpha|\le m}A_\alpha(x)D^\alpha u,\qquad A_\alpha\in C^\infty(\Omega).
$$

Smooth multiplication makes $Lu$ meaningful for $u\in\mathscr D'(\Omega)$. Define

$$
L^*\varphi=\sum_{|\alpha|\le m}(-1)^{|\alpha|}D^\alpha(A_\alpha\varphi).
$$

Then

$$
\langle Lu,\varphi\rangle=\sum_{|\alpha|\le m}\langle D^\alpha u,A_\alpha\varphi\rangle=\langle u,L^*\varphi\rangle.
$$

Here $L:\mathscr D'\to\mathscr D'$ and $L^*:\mathscr D\to\mathscr D$. In particular $\Delta^*=\Delta$.

> [!def] Distributional solution
> For $f\in\mathscr D'(\Omega)$, a distribution $u$ solves $Lu=f$ if
> $$
> \langle u,L^*\varphi\rangle=\langle f,\varphi\rangle\qquad\forall\varphi\in\mathscr D(\Omega).
> $$

A classical solution is a distributional solution. The converse needs regularity information.

## Fundamental solution of the Laplacian

> [!def]
> A distributional solution of $-\Delta u=\delta_y$ on $\mathbb{R}^n$ is a fundamental solution with pole at $y$.

It is not unique: adding a harmonic function, in particular a constant, leaves $-\Delta u$ unchanged.

Let $\omega_n=|S^{n-1}|$ denote the surface area of the unit sphere, as in the manuscript. For $n\ge2$,

$$
\Gamma(x-y)=\begin{cases}-\dfrac{1}{2\pi}\log|x-y|,&n=2,\\\dfrac{1}{(n-2)\omega_n}|x-y|^{2-n},&n\ge3.\end{cases}
$$

> [!thm]
> $\Gamma(\cdot-y)\in L^1_{\mathrm{loc}}(\mathbb{R}^n)$ and
> $$
> -\Delta\Gamma(\cdot-y)=\delta_y,\qquad \int_{\mathbb{R}^n}\Gamma(x-y)(-\Delta\varphi(x))\,dx=\varphi(y).
> $$

**Proof. Step 1: local integrability.** Put $r=|x-y|$. Near $0$, the radial integrals are

$$
\int_0^1r|\log r|\,dr<\infty\quad(n=2),\qquad \int_0^1r^{2-n}r^{n-1}\,dr=\int_0^1r\,dr<\infty\quad(n\ge3).
$$

The function is smooth away from the pole. Local integrability does not assert global $L^1$ integrability on $\mathbb{R}^n$.

**Step 2: regularize the singularity.** Define

$$
\Gamma_\varepsilon(r)=\begin{cases}-\dfrac{1}{4\pi}\log(r^2+\varepsilon^2),&n=2,\\\dfrac{1}{(n-2)\omega_n}(r^2+\varepsilon^2)^{-(n-2)/2},&n\ge3.\end{cases}
$$

For fixed $\varepsilon>0$, this is smooth on all of $\mathbb{R}^n$. On the compact support of $\Delta\varphi$, dominated convergence gives

$$
\int\Gamma_\varepsilon\Delta\varphi\,dx\longrightarrow\int\Gamma\Delta\varphi\,dx.
$$

For $n\ge3$, $0\le\Gamma_\varepsilon\le\Gamma$. For $n=2$, use $|\log r|$ near the pole and a uniform bound on the remaining compact annulus.

**Step 3: concentration of $-\Delta\Gamma_\varepsilon$.** The radial formula $\Delta g=g''+(n-1)g'/r$ yields

$$
-\Delta\Gamma_\varepsilon=\frac{\varepsilon^2}{\pi(r^2+\varepsilon^2)^2}\quad(n=2),\qquad -\Delta\Gamma_\varepsilon=\frac{n\varepsilon^2}{\omega_n(r^2+\varepsilon^2)^{(n+2)/2}}\quad(n\ge3).
$$

These are nonnegative and have total mass $1$. For $n\ge3$, the mass calculation uses

$$
\frac{d}{dr}\left[\frac{r^n}{(r^2+\varepsilon^2)^{n/2}}\right]=\frac{n\varepsilon^2r^{n-1}}{(r^2+\varepsilon^2)^{(n+2)/2}}.
$$

The mass outside radius $\delta>0$ tends to zero. For $n=2$ it equals $\varepsilon^2/(\delta^2+\varepsilon^2)$; for $n\ge3$ it is bounded by

$$
n\varepsilon^2\int_\delta^\infty r^{-3}\,dr=\frac{n\varepsilon^2}{2\delta^2}\longrightarrow0.
$$

By the [[Distributions (Schwartz)#Convergence and the Spiky Theorem|Spiky Theorem]], $-\Delta\Gamma_\varepsilon\to\delta_y$. Integration by parts gives

$$
\int\Gamma_\varepsilon(-\Delta\varphi)\,dx=\int(-\Delta\Gamma_\varepsilon)\varphi\,dx\longrightarrow\varphi(y).
$$

Combine this with Step 2. **QED**

> [!remark] 整理注
> The manuscript's higher-dimensional tail estimate loses a radial power in one line. Including the Jacobian $r^{n-1}$ gives $r^{n-1}/r^{n+2}=r^{-3}$, as above. The normalization uses sphere area $\omega_n$, not unit-ball volume.

## Poisson equation by convolution

Source: pp. 4–5, with the detailed proof dated 2025.11.17.

> [!thm]
> If $f\in C_c^2(\mathbb{R}^n)$, $n\ge2$, then
> $$
> u(x)=(\Gamma*f)(x)=\int_{\mathbb{R}^n}\Gamma(x-y)f(y)\,dy
> $$
> belongs to $C^2(\mathbb{R}^n)$ and solves $-\Delta u=f$ classically.

**Proof.** Local integrability of $\Gamma$ and compact support of $f$ make the integral finite. Rewrite it as $u(x)=\int\Gamma(y)f(x-y)\,dy$. Near a fixed $x$, all the translated supports lie in a common compact set, and difference quotients are bounded by an integrable multiple of $|\Gamma|$. Dominated convergence gives

$$
u_{x_i}(x)=\int\Gamma(y)f_{x_i}(x-y)\,dy,\qquad u_{x_i x_j}(x)=\int\Gamma(y)f_{x_i x_j}(x-y)\,dy.
$$

The same domination proves continuity of these derivatives. Consequently,

$$
-\Delta u(x)=\int\Gamma(y)(-\Delta f(x-y))\,dy=f(x).
$$

The fundamental-solution identity, initially proved for smooth test functions, extends to $C_c^2$ by uniform approximation of the derivatives through order $2$ on a common compact support. **QED**

> [!remark] 整理注
> An earlier line on p. 4 states the result for merely continuous compactly supported $f$, but the repeated theorem and proof on the same page assume $C_c^2$. The classical $C^2$ conclusion here uses that latter hypothesis. Continuity of $f$ alone does not justify the two differentiations used in this proof.
