# Sobolev Inequalities & Compact Embeddings

2025.12.10–12.24 · [[剩下的几次课.pdf#page=2|Source, pp. 2–9]]

[[Chain Rule & Sobolev Space]] → [[L2-theory for Second-order Elliptic Equations]]

## Zero-boundary Sobolev spaces

Let $\Omega\subset\mathbb{R}^n$ be open, with $n\ge2$ throughout the displayed Sobolev-exponent arguments. Define

$$
W_0^{k,p}(\Omega)=\overline{C_c^\infty(\Omega)}^{\,W^{k,p}(\Omega)}.
$$

For $u\in W_0^{k,p}(\Omega)$, the zero extension to $\mathbb{R}^n$ belongs to $W^{k,p}(\mathbb{R}^n)$ and its weak derivatives are the zero extensions of those in $\Omega$. This follows by zero-extending a $C_c^\infty$ approximating sequence and passing to its Sobolev limit.

> [!remark]
> Most approximation and embedding arguments below are stated for finite $p$. If $W_0^{k,\infty}$ is used, it means exactly the norm closure in the displayed definition; it should not be silently identified with all $W^{k,\infty}$ functions having zero trace.

## SI-1: subcritical Sobolev inequality

> [!thm]
> If $1\le p<n$ and $p^*=np/(n-p)$, then
> $$
> \|u\|_{L^{p^*}(\Omega)}\le C_1(n,p)\|\nabla u\|_{L^p(\Omega)}\qquad\forall u\in W_0^{1,p}(\Omega).
> $$
> The lecture's proof gives $C_1(n,p)=p(n-1)/(\sqrt n(n-p))$.

**Proof. Step 1: $p=1$.** First let $u\in C_c^1(\Omega)$ and extend by zero. By the fundamental theorem of calculus in each coordinate,

$$
|u(x)|\le\int_{\mathbb{R}}|\partial_i u(x_1,\ldots,x_{i-1},s,x_{i+1},\ldots,x_n)|\,ds=:g_i(\widehat x_i).
$$

Multiplying the $n$ inequalities gives $|u|^{n/(n-1)}\le\prod_i g_i^{1/(n-1)}$. Integrate successively in the coordinates and apply Hölder at each stage, with exponent $n-1$ to the factors depending on the coordinate being integrated. This yields

$$
\int_{\mathbb{R}^n}|u|^{n/(n-1)}\,dx\le\prod_{i=1}^n\left(\int_{\mathbb{R}^n}|\partial_i u|\,dx\right)^{1/(n-1)}.
$$

Raising to $(n-1)/n$, then using the arithmetic–geometric mean inequality and $\sum_i|\partial_i u|\le\sqrt n|\nabla u|$, gives

$$
\|u\|_{n/(n-1)}\le\prod_i\|\partial_i u\|_1^{1/n}\le\frac1n\sum_i\|\partial_i u\|_1\le\frac1{\sqrt n}\|\nabla u\|_1.
$$

**Step 2: $1<p<n$.** Apply Step 1 to $|u|^\alpha$, where $\alpha>1$ is chosen below. For $p'=p/(p-1)$,

$$
\bigl\||u|^\alpha\bigr\|_{n/(n-1)}\le\frac\alpha{\sqrt n}\int|u|^{\alpha-1}|\nabla u|\,dx\le\frac\alpha{\sqrt n}\|\nabla u\|_p\bigl\||u|^{\alpha-1}\bigr\|_{p'}.
$$

Choose $\alpha=p(n-1)/(n-p)$ so that

$$
\frac{\alpha n}{n-1}=p^*,\qquad (\alpha-1)p'=p^*.
$$

Thus $\|u\|_{p^*}^\alpha\le(\alpha/\sqrt n)\|\nabla u\|_p\|u\|_{p^*}^{\alpha-1}$. Divide if $u\ne0$ to get SI-1.

**Step 3: pass to $W_0^{1,p}$.** Choose $u_k\in C_c^\infty(\Omega)$ converging to $u$ in $W^{1,p}$ and, along a subsequence, a.e. Apply the smooth estimate and Fatou's lemma:

$$
\|u\|_{p^*}\le\liminf_k\|u_k\|_{p^*}\le C_1(n,p)\|\nabla u\|_p.
$$

**QED**

## SI-2: supercritical supremum estimate

> [!thm]
> If $\Omega$ is bounded and $n<p<\infty$, then every $u\in W_0^{1,p}(\Omega)$ has a continuous representative on $\overline\Omega$, vanishing on $\partial\Omega$, and
> $$
> \|u\|_{L^\infty(\Omega)}\le C_2(n,p,|\Omega|)\|\nabla u\|_{L^p(\Omega)}.
> $$

**Proof. Step 1: $|\Omega|=1$.** For $u\in C_c^1(\Omega)$ with nonzero gradient norm, put

$$
v=\frac{\sqrt n\,u}{\|\nabla u\|_p},\qquad p'=\frac p{p-1},\qquad r=\frac n{n-1},\qquad \delta=\frac r{p'}>1.
$$

The power argument used above gives, for every $\alpha>1$,

$$
\|v\|_{\alpha r}\le\alpha^{1/\alpha}\|v\|_{(\alpha-1)p'}^{1-1/\alpha}.
$$

Choose $\alpha=\delta^m$. Since $(\delta^m-1)p'<\delta^{m-1}r$ and $|\Omega|=1$, monotonicity of $L^q$ norms gives

$$
\|v\|_{\delta^m r}\le\delta^{m\delta^{-m}}\|v\|_{\delta^{m-1}r}^{1-\delta^{-m}}.
$$

The initial bound is $\|v\|_r\le\|\nabla u\|_1/\|\nabla u\|_p\le1$. Iteration therefore yields

$$
\|v\|_{\delta^m r}\le\delta^{\sum_{j=1}^m j\delta^{-j}}\le\delta^{\delta/(\delta-1)^2}=:\gamma<\infty.
$$

As $m\to\infty$, $\|u\|_\infty\le(\gamma/\sqrt n)\|\nabla u\|_p$.

**Step 2: scaling.** Write $a=|\Omega|^{1/n}$, $x=ay$ and $w(y)=u(ay)$, so that the rescaled domain has measure $1$. Then

$$
\|w\|_\infty=\|u\|_\infty,\qquad \|\nabla_yw\|_p=a^{1-n/p}\|\nabla_xu\|_p.
$$

Hence one may take

$$
C_2(n,p,|\Omega|)=\frac\gamma{\sqrt n}|\Omega|^{1/n-1/p}.
$$

**Step 3: general $u$.** A sequence $u_k\in C_c^\infty(\Omega)$ converging in $W^{1,p}$ is Cauchy in the supremum norm by the estimate applied to differences. Its uniform limit on $\overline\Omega$ is continuous, is zero on the boundary, and agrees a.e. with the $L^p$ limit $u$. **QED**

> [!remark]
> As $p\downarrow n$, $\delta\downarrow1$ and this constant blows up. The source records the stronger Morrey conclusion $u\in C^{0,\alpha}(\overline\Omega)$ for $\alpha=1-n/p$, without a proof of that Hölder estimate here. The iteration above establishes the supremum estimate and continuity; the Hölder claim is an additional result.

For the lecture-defined $W_0^{1,\infty}$, a finite exponent $r>n$ gives the corresponding supremum estimate by Hölder and SI-2. Zero extensions are Lipschitz, which is the endpoint regularity.

## SI-3: critical exponent

> [!thm]
> If $\Omega$ is bounded and $u\in W_0^{1,n}(\Omega)$, then for each $1\le q<\infty$,
> $$
> \|u\|_{L^q(\Omega)}\le C_3(n,q,|\Omega|)\|\nabla u\|_{L^n(\Omega)}.
> $$

The manuscript states this result without a separate proof. It follows from SI-1: choose $1\le r<n$ with $r^*=nr/(n-r)\ge q$. On a bounded set, Hölder gives $\|u\|_q\le C\|u\|_{r^*}$ and $\|\nabla u\|_r\le C\|\nabla u\|_n$, and $W_0^{1,n}\subset W_0^{1,r}$. This argument does not give $q=\infty$.

## Poincaré inequality and equivalent norms

> [!thm] Cor 1 · Poincaré
> On a bounded domain, for $1\le p\le\infty$,
> $$
> \|u\|_{L^p(\Omega)}\le C(n,p,|\Omega|)\|\nabla u\|_{L^p(\Omega)}\qquad(u\in W_0^{1,p}(\Omega)).
> $$

**Proof.** If $p<n$, combine SI-1 with Hölder since $p^*>p$. If $p=n$, take $q=n$ in SI-3. If $p>n$, combine SI-2 with $\|u\|_p\le|\Omega|^{1/p}\|u\|_\infty$. The $p=\infty$ version follows from the finite-exponent reduction noted above. **QED**

Thus $\|\nabla u\|_p$ is an equivalent norm on $W_0^{1,p}$. In particular, for $H_0^1=W_0^{1,2}$ the gradient inner product is complete and equivalent to the full Sobolev inner product; this is used in [[L2-theory for Second-order Elliptic Equations]].

## Continuous embeddings

> [!def]
> For Banach spaces $X\subset Y$, write $X\hookrightarrow Y$ if the inclusion map is bounded, i.e. $\|x\|_Y\le C\|x\|_X$.

For example, on a bounded set, $L^{p_2}\hookrightarrow L^{p_1}$ when $1\le p_1<p_2\le\infty$.

The first-order conclusions are

$$
W_0^{1,p}(\Omega)\hookrightarrow L^{np/(n-p)}(\Omega)\quad(1\le p<n),
$$

$$
W_0^{1,n}(\Omega)\hookrightarrow L^q(\Omega)\quad(1\le q<\infty,\ \Omega\text{ bounded}),
$$

$$
W_0^{1,p}(\Omega)\hookrightarrow C^{0,1-n/p}(\overline\Omega)\quad(n<p<\infty,\ \Omega\text{ bounded}),
$$

where the last Hölder strengthening is recorded in the source without proof.

### Higher-order embeddings

For finite $p$ and integer $k\ge1$, iteration of first-order embeddings gives

$$
W_0^{k,p}(\Omega)\hookrightarrow L^{np/(n-kp)}(\Omega)\quad(kp<n),
$$

and, on bounded domains,

$$
W_0^{k,p}(\Omega)\hookrightarrow L^q(\Omega)\quad(kp=n,\ 1\le q<\infty).
$$

For instance, applying SI-1 to the derivatives through order $k-1$ gives $W_0^{k,p}\hookrightarrow W_0^{k-1,p^*}$; repeating replaces $p$ by $np/(n-jp)$ at the $j$-th stage.

If $kp>n$, put $s=k-n/p>0$. The lecture writes the target as $C^\alpha$; in explicit Hölder notation its usual finite-$p$ formulation is

$$
W_0^{k,p}(\Omega)\hookrightarrow C^{m,\theta}(\overline\Omega)\quad\text{if }s=m+\theta,\ m\in\mathbb{N}_0,\ 0<\theta<1,
$$

while if $s=m\in\mathbb{N}$, one can take $C^{m-1,\theta}$ for every $0<\theta<1$. This avoids asserting an integer Hölder endpoint not proved in the notes. Here $C^{m,\theta}$ means $m$ continuous derivatives whose order-$m$ derivatives are $\theta$-Hölder.

> [!remark] Boundary regularity
> The source also records the corresponding embeddings for the full $W^{k,p}(\Omega)$ on bounded $C^1$, or more generally Lipschitz ($C^{0,1}$), domains. Those versions require an extension theorem; the zero-boundary proofs above do not by themselves establish the full-space versions.

## Rellich–Kondrachov compactness theorem

> [!def] Compact embedding
> Write $X\hookrightarrow\hookrightarrow Y$ if the inclusion is bounded and every bounded subset of $X$ is relatively compact in $Y$. Equivalently, every bounded sequence has a subsequence converging in the $Y$ norm.

> [!thm] RKCT
> Let $\Omega\subset\mathbb{R}^n$ be bounded and $1\le p<n$. Then
> $$
> W_0^{1,p}(\Omega)\hookrightarrow\hookrightarrow L^q(\Omega)\qquad\text{for }1\le q<p^*:=\frac{np}{n-p}.
> $$

**Proof. Step 1: compactness in $L^1$.** Let $A\subset W_0^{1,p}(\Omega)$ satisfy $\|u\|_{W^{1,p}}\le M$. Extend every $u\in A$ by zero and put $A_\varepsilon=\{j_\varepsilon*u:u\in A\}$.

For each fixed $\varepsilon>0$,

$$
\|u_\varepsilon\|_\infty\le\|j_\varepsilon\|_\infty\|u\|_1\le C(\varepsilon,\Omega,p)M,\qquad \|\nabla u_\varepsilon\|_\infty\le\|\nabla j_\varepsilon\|_\infty\|u\|_1\le C(\varepsilon,\Omega,p)M.
$$

Thus $A_\varepsilon$ is uniformly bounded and equicontinuous on $\overline\Omega$. Arzelà–Ascoli makes it precompact in $C(\overline\Omega)$ and therefore in $L^1(\Omega)$.

We next need approximation **uniform over $A$**. For smooth compactly supported $u$, the fundamental theorem of calculus gives

$$
u_\varepsilon(x)-u(x)=\int j(z)[u(x-\varepsilon z)-u(x)]\,dz=-\int j(z)\int_0^\varepsilon\nabla u(x-sz)\cdot z\,ds\,dz.
$$

Since $|z|\le1$ on the kernel support, Fubini and translation invariance yield

$$
\|u_\varepsilon-u\|_{L^1(\mathbb{R}^n)}\le\varepsilon\|\nabla u\|_{L^1(\mathbb{R}^n)}.
$$

Pass to a $C_c^\infty$ approximating sequence to obtain this estimate for every $u\in W_0^{1,p}(\Omega)$; the convergence in $W^{1,1}$ follows from boundedness of $\Omega$. Hence

$$
\sup_{u\in A}\|u_\varepsilon-u\|_{L^1(\Omega)}\le C(\Omega,p)M\varepsilon.
$$

Given $\delta>0$, choose $\varepsilon$ so this error is less than $\delta/2$. Cover $A_\varepsilon$ by finitely many $L^1$ balls of radius $\delta/2$. The corresponding balls of radius $\delta$ cover $A$. Thus $A$ is totally bounded in the complete space $L^1$, and is precompact.

**Step 2: interpolation to $1<q<p^*$.** Choose $0<\lambda<1$ with

$$
\frac1q=\lambda+\frac{1-\lambda}{p^*}.
$$

Hölder interpolation gives $\|f\|_q\le\|f\|_1^\lambda\|f\|_{p^*}^{1-\lambda}$. By SI-1, $\sup_{u\in A}\|u\|_{p^*}\le CM$. Thus for $u,v\in A$,

$$
\|u-v\|_q\le\|u-v\|_1^\lambda(2CM)^{1-\lambda}.
$$

Every sequence in $A$ has an $L^1$-Cauchy subsequence by Step 1. This inequality makes it Cauchy in $L^q$, hence convergent there. **QED**

### Further compact embeddings

If $p=n$, choose $r<n$ sufficiently close to $n$ so that $q<r^*$. Then

$$
W_0^{1,n}(\Omega)\hookrightarrow W_0^{1,r}(\Omega)\hookrightarrow\hookrightarrow L^q(\Omega)\qquad(1\le q<\infty).
$$

If $p>n$, Morrey's estimate and compactness of the Hölder inclusion give

$$
W_0^{1,p}(\Omega)\hookrightarrow\hookrightarrow C^{0,\beta}(\overline\Omega)\qquad(0\le\beta<1-n/p).
$$

The source records the higher-order versions by induction. For finite $p$,

$$
W_0^{k,p}(\Omega)\hookrightarrow\hookrightarrow L^q(\Omega)\quad\text{if }kp<n\text{ and }1\le q<\frac{np}{n-kp},
$$

with every finite $q$ allowed when $kp=n$. If $kp>n$, compact embedding holds into $C^{m,\beta}$ whenever $m\in\mathbb{N}_0$, $0\le\beta<1$ and $m+\beta<k-n/p$. As above, versions for the full $W^{k,p}$ use a regular boundary and extension.

### Regularity indices

The source summarizes the strict inequalities through the indices

$$
C^{m,\beta}:\ m+\beta,\qquad W^{k,p}:\ k-\frac np,\qquad L^q:\ -\frac nq.
$$

For the bounded-domain embeddings under discussion, a strict gap between the Sobolev index and the target index gives the compact range. Equality is the critical endpoint of continuous embedding and does not give compactness from this argument. This is a mnemonic for these theorems, with their boundary assumptions retained.

> [!remark] 整理注
> In the compactness proof, differentiating $j_\varepsilon(x)=\varepsilon^{-n}j(x/\varepsilon)$ introduces an additional factor $\varepsilon^{-1}$: $\|\nabla j_\varepsilon\|_\infty=\varepsilon^{-n-1}\|\nabla j\|_\infty$. The fixed-$\varepsilon$ equicontinuity conclusion is unchanged. At $kp=n$, the target exponent is stated as arbitrary finite $q$, rather than using a fraction with zero denominator.
