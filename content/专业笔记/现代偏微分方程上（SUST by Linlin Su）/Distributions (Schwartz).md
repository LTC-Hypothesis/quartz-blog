# Distributions (Schwartz) · 广义函数

2025.10.29 · [[PDE Note Week8 LectureWed.pdf|Source, pp. 1–3]]

[[Classical Maximum Principles for Second-order Parabolic Equations]] → [[Derivatives of Distributions]]

## Test functions

Let $\Omega\subset\mathbb{R}^n$ be a domain. Define

$$
\mathscr D(\Omega)=C_c^\infty(\Omega),\qquad \operatorname{supp}u=\overline{\{x\in\Omega:u(x)\ne0\}}.
$$

For a test function, the support is a compact subset of $\Omega$.

### Standard mollifier

$$
j(x)=\begin{cases}C\exp\left(\dfrac{1}{|x|^2-1}\right),&|x|<1,\\0,&|x|\ge1,\end{cases}\qquad \int_{\mathbb{R}^n}j(x)\,dx=1.
$$

Here $C>0$ normalizes the integral. The function is nonnegative and belongs to $C_c^\infty(\mathbb{R}^n)$.

**Proof of smoothness.** Write $j(x)=h(|x|^2)$, where $h(s)=Ce^{1/(s-1)}$ for $s<1$, and $h(s)=0$ for $s\ge1$. Each one-sided derivative at $1$ is a finite sum of powers of $(s-1)^{-1}$ times $e^{1/(s-1)}$. With $z=(s-1)^{-1}\to-\infty$, every such term tends to $0$ because $|z|^m e^z\to0$. Thus all derivatives match the zero function at $s=1$. The composition with $|x|^2$ is smooth also at $x=0$. **QED**

For $a\in\Omega$ and $\overline{B_\varepsilon(a)}\subset\Omega$, set

$$
j_{\varepsilon,a}(x)=\varepsilon^{-n}j\left(\frac{x-a}{\varepsilon}\right).
$$

Then $\operatorname{supp}j_{\varepsilon,a}=\overline{B_\varepsilon(a)}$ and, by $x=a+\varepsilon z$,

$$
\int_{\mathbb{R}^n}j_{\varepsilon,a}(x)\,dx=\int_{B_1(0)}j(z)\,dz=1.
$$

Hence every nonempty open set has nonzero test functions.

## Definition of a distribution

> [!def] Distribution
> A distribution is a linear functional $F:\mathscr D(\Omega)\to\mathbb{R}$, written $\langle F,\varphi\rangle$, continuous in the following sense. Whenever $\varphi_k\in\mathscr D(\Omega)$ have supports in one fixed compact $K\Subset\Omega$ and
> $$
> \|D^\alpha\varphi_k\|_{L^\infty(\Omega)}\longrightarrow0\qquad\text{for every multi-index }\alpha,
> $$
> then $\langle F,\varphi_k\rangle\to0$.

Write $\mathscr D'(\Omega)$ for the space of distributions. By linearity, continuity at $0$ suffices. A multi-index is $\alpha=(\alpha_1,\ldots,\alpha_n)\in\mathbb{N}_0^n$, with $|\alpha|=\sum_i\alpha_i$.

### Examples

**Locally integrable functions.** For $f\in L^1_{\mathrm{loc}}(\Omega)$, define

$$
\langle F_f,\varphi\rangle=\int_\Omega f\varphi\,dx.
$$

If $\operatorname{supp}\varphi_k\subset K\Subset\Omega$, then

$$
|\langle F_f,\varphi_k\rangle|\le\|\varphi_k\|_\infty\int_K|f|\,dx\longrightarrow0.
$$

Thus $F_f\in\mathscr D'(\Omega)$; we often identify $f$ with $F_f$.

**Multiplication by a smooth function.** For $F\in\mathscr D'(\Omega)$ and $g\in C^\infty(\Omega)$,

$$
\langle gF,\varphi\rangle=\langle F,g\varphi\rangle.
$$

This is a distribution because multiplication by $g$ preserves test-function convergence, by the product rule on the fixed compact support.

**Dirac mass.** For $a\in\Omega$,

$$
\langle\delta_a,\varphi\rangle=\varphi(a),\qquad |\langle\delta_a,\varphi_k\rangle|\le\|\varphi_k\|_\infty\longrightarrow0.
$$

$\delta_a$ is the Dirac measure of unit mass at $a$.

## Convergence and the Spiky Theorem

> [!def] Distributional convergence
> $$
> F_k\longrightarrow F\text{ in }\mathscr D'(\Omega)\quad\Longleftrightarrow\quad \langle F_k,\varphi\rangle\longrightarrow\langle F,\varphi\rangle\quad\forall\varphi\in\mathscr D(\Omega).
> $$

> [!thm] Spiky Theorem
> Suppose $f_k\in L^1(\Omega)$, $a\in\Omega$, and
> $$
> \int_{\Omega\setminus B_\delta(a)}|f_k|\,dx\longrightarrow0\quad\forall\delta>0,\qquad \sup_k\|f_k\|_{L^1(\Omega)}\le M,\qquad \int_\Omega f_k\,dx\longrightarrow A.
> $$
> Then $f_k\to A\delta_a$ in $\mathscr D'(\Omega)$.

**Proof.** For $\varphi\in\mathscr D(\Omega)$,

$$
\int_\Omega f_k\varphi\,dx=\int_\Omega f_k[\varphi(x)-\varphi(a)]\,dx+\varphi(a)\int_\Omega f_k\,dx.
$$

Given $\epsilon>0$, choose $\delta>0$ so that $|\varphi(x)-\varphi(a)|<\epsilon$ when $|x-a|<\delta$. Splitting into the ball and its complement gives

$$
\left|\int_\Omega f_k[\varphi(x)-\varphi(a)]\,dx\right|\le M\epsilon+2\|\varphi\|_\infty\int_{\Omega\setminus B_\delta(a)}|f_k|\,dx.
$$

Take $k\to\infty$ and then $\epsilon\to0$. The remaining term tends to $A\varphi(a)$. **QED**

In particular, $j_{\varepsilon,a}\to\delta_a$ as $\varepsilon\downarrow0$: the total mass is $1$, the $L^1$ norm is $1$, and the mass outside $B_\delta(a)$ is zero once $\varepsilon<\delta$.

The same concentration argument will establish the [[Derivatives of Distributions#Fundamental solution of the Laplacian|fundamental solution]] of $-\Delta$.
