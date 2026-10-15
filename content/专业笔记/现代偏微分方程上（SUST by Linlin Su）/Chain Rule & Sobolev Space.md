# Chain Rule & Sobolev Space

2025.12.1, 2025.12.3 · [[PDE Week13 Mon.pdf|Source, pp. 1–2]]; [[PDE Week13 Wed.pdf|continuation, pp. 1–3]]; [[剩下的几次课.pdf#page=1|density theorem, pp. 1–2]]

[[Weak Derivatives]] · [[Approximation of bad functions by good functions]] → [[Sobolev Inequalities & Compact Embeddings]]

## Chain rule

Recall the lecture's local notation $W^1(\Omega)=W^{1,1}_{\mathrm{loc}}(\Omega)$.

> [!thm] Thm 1 · Chain rule
> If $f\in C^1(\mathbb{R})$, $f'\in L^\infty(\mathbb{R})$ and $u\in W^1(\Omega)$, then $f(u)\in W^1(\Omega)$ and
> $$
> D_i(f(u))=f'(u)D_i u\quad\text{a.e.},\qquad \nabla(f(u))=f'(u)\nabla u.
> $$

**Proof.** By [[Approximation of bad functions by good functions#Characterization by smooth approximation|smooth approximation]], choose $u_k\in C^\infty(\Omega)$ such that $u_k\to u$ and $\nabla u_k\to\nabla u$ locally in $L^1$. For $\Omega'\Subset\Omega$,

$$
|f(u)|\le|f(0)|+\|f'\|_\infty|u|,\qquad \|f(u_k)-f(u)\|_{L^1(\Omega')}\le\|f'\|_\infty\|u_k-u\|_{L^1(\Omega')}\longrightarrow0.
$$

After passing to a subsequence, $u_k\to u$ a.e. Split the gradient error:

$$
f'(u_k)\nabla u_k-f'(u)\nabla u=f'(u_k)(\nabla u_k-\nabla u)+[f'(u_k)-f'(u)]\nabla u.
$$

The first term tends to $0$ in local $L^1$. The second tends to $0$ by dominated convergence, with majorant $2\|f'\|_\infty|\nabla u|$. Since the classical chain rule holds for each $f(u_k)\in C^1$, integration by parts and these limits prove the asserted weak derivative. **QED**

> [!remark] 整理注
> $f(u_k)$ need not have compact support when $f(0)\ne0$, even if $u_k$ does. Compact support of the test function is sufficient for the argument; only local integrability of $f(u_k)$ is needed.

## Positive and negative parts

Keep the sign convention of the manuscripts:

$$
u^+=\max(u,0),\qquad u^-=\min(u,0),\qquad u=u^++u^-,\qquad |u|=u^+-u^-.
$$

> [!thm] Thm 2
> If $u\in W^1(\Omega)$, then $u^+,u^-,|u|\in W^1(\Omega)$, and a.e.
> $$
> \nabla u^+=\mathbf1_{\{u>0\}}\nabla u,\qquad \nabla u^-=\mathbf1_{\{u<0\}}\nabla u,\qquad \nabla|u|=(\mathbf1_{\{u>0\}}-\mathbf1_{\{u<0\}})\nabla u.
> $$

**Proof.** Approximate the positive part by

$$
f_\varepsilon(s)=\begin{cases}\sqrt{s^2+\varepsilon^2}-\varepsilon,&s>0,\\0,&s\le0.\end{cases}
$$

Then $f_\varepsilon\in C^1(\mathbb{R})$, $0\le f_\varepsilon'\le1$, $f_\varepsilon(s)\to s^+$, and

$$
f_\varepsilon'(u)\nabla u=\mathbf1_{\{u>0\}}\frac{u\nabla u}{\sqrt{u^2+\varepsilon^2}}\longrightarrow\mathbf1_{\{u>0\}}\nabla u.
$$

On the support of a test function, $|f_\varepsilon(u)|\le|u|$ and $|f_\varepsilon'(u)\nabla u|\le|\nabla u|$. Apply dominated convergence in the weak chain-rule identity to obtain the formula for $u^+$. Use $u^-=-(-u)^+$ and $|u|=u^+-u^-$. **QED**

> [!thm] Cor 1 · Gradient on a level set
> For $u\in W^1(\Omega)$ and any fixed $c\in\mathbb{R}$,
> $$
> \nabla u=0\quad\text{a.e. on }\{x\in\Omega:u(x)=c\}.
> $$

**Proof.** Write $u-c=(u-c)^++(u-c)^-$. Both terms have zero weak gradient a.e. on $\{u=c\}$ by the preceding formulas. **QED**

## Sobolev spaces and norms

> [!def]
> For an integer $k\ge0$ and $1\le p\le\infty$,
> $$
> W^{k,p}(\Omega)=\{u\in W^k(\Omega):D^\alpha u\in L^p(\Omega)\text{ for all }|\alpha|\le k\}.
> $$
> The order-zero condition includes $u\in L^p(\Omega)$, so $W^{0,p}(\Omega)=L^p(\Omega)$.

For $1\le p<\infty$, use

$$
\|u\|_{W^{k,p}(\Omega)}=\left(\sum_{|\alpha|\le k}\int_\Omega|D^\alpha u|^p\,dx\right)^{1/p}.
$$

An equivalent norm is $\sum_{|\alpha|\le k}\|D^\alpha u\|_p$. For $p=\infty$, the lecture uses

$$
\|u\|_{W^{k,\infty}(\Omega)}=\sum_{|\alpha|\le k}\|D^\alpha u\|_\infty.
$$

The equivalence for finite $p$ follows from finite-dimensional $\ell^p$–$\ell^1$ norm equivalence. If there are $N$ multi-indices, then

$$
\left(\sum_{j=1}^Na_j^p\right)^{1/p}\le\sum_{j=1}^Na_j\le N^{1-1/p}\left(\sum_{j=1}^Na_j^p\right)^{1/p}\qquad(a_j\ge0).
$$

## Completeness, separability and reflexivity

Source: [[PDE Week13 Wed.pdf#page=1|pp. 1–2]].

> [!thm] Banach property
> $W^{k,p}(\Omega)$ is a Banach space for $1\le p\le\infty$.

**Proof.** Homogeneity and definiteness follow from the corresponding $L^p$ properties. For finite $p$, the triangle inequality is Minkowski first in the finite derivative index and then in the spatial variable; equivalently it is the product-$L^p$ norm. The $p=\infty$ case follows from the sum norm.

Let $(u_m)$ be Cauchy in $W^{k,p}$. By completeness of $L^p$, there are $u$ and $v_\alpha$ such that

$$
u_m\longrightarrow u\text{ in }L^p,\qquad D^\alpha u_m\longrightarrow v_\alpha\text{ in }L^p\quad(|\alpha|\le k).
$$

For $\varphi\in C_c^\infty(\Omega)$, Hölder's inequality allows passage to the limit in

$$
\int D^\alpha u_m\varphi\,dx=(-1)^{|\alpha|}\int u_mD^\alpha\varphi\,dx.
$$

Thus $v_\alpha=D^\alpha u$ weakly. Therefore $u\in W^{k,p}$ and $u_m\to u$ in its norm. This also works for $p=1$ and $p=\infty$, using the appropriate conjugate exponents on the compact test support. **QED**

> [!thm]
> $W^{k,p}(\Omega)$ is separable for $1\le p<\infty$ and reflexive for $1<p<\infty$.

**Proof.** Define the isometry into a finite product,

$$
T:W^{k,p}(\Omega)\longrightarrow Y:=\prod_{|\alpha|\le k}L^p(\Omega),\qquad Tu=(D^\alpha u)_{|\alpha|\le k}.
$$

Its range is closed because $W^{k,p}$ is complete. The product $Y$ is separable in the first range and reflexive in the second. These properties pass to closed linear subspaces. **QED**

Recall the canonical map $J:X\to X^{**}$, defined by $J(x)(x^*)=x^*(x)$. A Banach space is reflexive if $J$ is onto. In a reflexive Banach space every bounded sequence has a weakly convergent subsequence:

$$
x_{m_j}\rightharpoonup x\quad\Longleftrightarrow\quad x^*(x_{m_j})\longrightarrow x^*(x)\quad\forall x^*\in X^*.
$$

## Partition of unity

Source: [[PDE Week13 Wed.pdf#page=2|pp. 2–3]].

> [!def]
> Let $(U_j)$ cover $\Omega$, with each $U_j\Subset\Omega$ open and every compact subset of $\Omega$ meeting only finitely many $U_j$. A subordinate smooth **partition of unity** is a family $\varphi_j\in C_c^\infty(\Omega)$ such that
> $$
> \varphi_j\ge0,\qquad \operatorname{supp}\varphi_j\subset U_j,\qquad \sum_j\varphi_j(x)=1\quad(x\in\Omega).
> $$

> [!thm]
> Every such locally finite covering admits a subordinate partition of unity.

**Proof. Step 1: shrink the covering.** Construct $V_j$ with $\overline V_j\subset U_j$ and $\bigcup_jV_j=\Omega$. At the first stage,

$$
F_1=\overline U_1\setminus\bigcup_{j\ge2}U_j
$$

is compact and contained in $U_1$. Choose an open neighborhood $V_1$ of $F_1$ with $\overline V_1\subset U_1$; for nonempty $F_1$ a sufficiently small distance-neighborhood works. Then $V_1,U_2,U_3,\ldots$ still cover $\Omega$. Continue with

$$
F_m=\overline U_m\setminus\left(\bigcup_{j<m}V_j\cup\bigcup_{j>m}U_j\right)
$$

and choose $V_m$ similarly. Every point belongs to only finitely many original $U_j$ locally, so after their last index is processed it belongs to one of the $V_j$. This proves the shrunken family covers.

**Step 2: smooth nonnegative functions.** For each nonempty $V_j$, choose $\varepsilon_j>0$ small and set $\psi_j=j_{\varepsilon_j}*\mathbf1_{V_j}$. Then $\psi_j\in C_c^\infty(U_j)$ and $\psi_j>0$ on $\overline V_j$: every ball around a point of $\overline V_j$ meets the open set $V_j$ in positive measure. For an empty $V_j$, set $\psi_j=0$.

**Step 3: normalize.** Local finiteness makes

$$
\psi(x)=\sum_j\psi_j(x)>0,\qquad \varphi_j(x)=\frac{\psi_j(x)}{\psi(x)}
$$

smooth and gives all required properties. **QED**

### Application: boundary integrals

Source: [[剩下的几次课.pdf#page=1|p. 1]].

On a compact smooth boundary, take finitely many graph charts $X_i(x')=(x',g_i(x'))$ and a partition of unity subordinate to them. Then

$$
\int_{\partial\Omega}f\,dS=\sum_i\int_{V_i'}f(X_i(x'))\varphi_i(X_i(x'))\sqrt{1+|\nabla g_i(x')|^2}\,dx'.
$$

This reduces the surface integral to ordinary integrals in $n-1$ variables. The graph area element is $dS=\sqrt{1+|\nabla g_i|^2}\,dx'$, not $dx$ on the boundary.

## Density theorem in Sobolev spaces

Source: [[剩下的几次课.pdf#page=1|pp. 1–2]].

> [!thm] Density theorem
> For any open $\Omega$, integer $k\ge0$ and $1\le p<\infty$,
> $$
> C^\infty(\Omega)\cap W^{k,p}(\Omega)\text{ is dense in }W^{k,p}(\Omega).
> $$

**Proof.** The case $k=0$ is [[Approximation of bad functions by good functions#Density in Lebesgue spaces|$L^p$ density]]. For general $k$, choose an increasing compact exhaustion $\Omega_j\Subset\Omega_{j+1}$ and a locally finite covering by overlapping shells, for example

$$
U_j=\Omega_{j+1}\setminus\overline{\Omega_{j-1}},\qquad \Omega_0=\Omega_{-1}=\varnothing.
$$

Take a subordinate partition $(\varphi_j)$. By the weak product rule,

$$
D^\alpha(\varphi_j u)=\sum_{\beta\le\alpha}\binom{\alpha}{\beta}(D^\beta\varphi_j)(D^{\alpha-\beta}u),
$$

so $\varphi_j u\in W^{k,p}$ and has compact support in $U_j$. Its zero extension can be mollified without boundary terms. For each $j$, choose $h_j>0$ small enough that

$$
\operatorname{supp}(\varphi_j u)_{h_j}\Subset U_j,\qquad \|(\varphi_j u)_{h_j}-\varphi_j u\|_{W^{k,p}}<\varepsilon\,2^{-j-1}.
$$

Define $v=\sum_j(\varphi_j u)_{h_j}$. This sum is locally finite, so $v\in C^\infty(\Omega)$. The differences form an absolutely convergent series in $W^{k,p}$, and locally their sum is $v-u$. Consequently,

$$
\|v-u\|_{W^{k,p}}\le\sum_j\|(\varphi_j u)_{h_j}-\varphi_j u\|_{W^{k,p}}<\varepsilon.
$$

In particular $v\in W^{k,p}$. **QED**

If $\Omega$ is bounded with $C^1$ boundary, the lecture also records density of $C^\infty(\overline\Omega)$ in $W^{k,p}(\Omega)$ for finite $p$, without proof. For $k=0$, no boundary regularity is needed for approximation by globally smooth restrictions.

> [!remark] 整理注 · endpoint and boundary conditions
> The source's opening density statement includes $p=\infty$, but the proof uses strong $L^p$ convergence of mollifiers, which holds in this generality only for $p<\infty$. For example $|x|\in W^{1,\infty}(-1,1)$ cannot be approximated in $W^{1,\infty}$ by smooth functions: their continuous derivatives cannot converge in essential supremum to the jump $\operatorname{sgn}x$.
>
> Also, $C_c^\infty(\Omega)$ is not generally dense in the full $W^{k,p}(\Omega)$ when $k\ge1$. Its closure is the separate space $W_0^{k,p}(\Omega)$, used in [[Sobolev Inequalities & Compact Embeddings]].
