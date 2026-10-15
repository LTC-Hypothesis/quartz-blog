# L2-theory for Second-order Elliptic Equations

[[剩下的几次课.pdf#page=9|Source, pp. 9–11]] · End of the first part of the course

[[Sobolev Inequalities & Compact Embeddings]] → [[1. Existence and Uniqueness of weak solutions of elliptic equations|Continuation in the second part]]

## Divergence-form operator

Let $\Omega\subset\mathbb{R}^n$ be a bounded domain. Consider

$$
Lu=-\sum_{i,j=1}^n(a_{ij}(x)u_{x_i})_{x_j}+\sum_{i=1}^nb_i(x)u_{x_i}+c(x)u.
$$

Assume $a_{ij},b_i,c\in L^\infty(\Omega)$, $A=(a_{ij})$ is symmetric and for some $\lambda_0>0$,

$$
a_{ij}(x)\xi_i\xi_j\ge\lambda_0|\xi|^2\qquad\text{for a.e. }x\in\Omega,\ \xi\in\mathbb{R}^n.
$$

The principal part is $-\operatorname{div}(A^T\nabla u)$, which equals $-\operatorname{div}(A\nabla u)$ under symmetry. This is a **divergence-form** operator, unlike the classical nondivergence form in [[Intro 二阶PDE]].

The Dirichlet problem is

$$
\begin{cases}Lu=f&\text{in }\Omega,\\u=0&\text{on }\partial\Omega.\end{cases}
$$

## Hilbert and dual spaces

Write

$$
H_0^k(\Omega)=W_0^{k,2}(\Omega),\qquad (u,v)_{H^k}=\sum_{|\alpha|\le k}\int_\Omega D^\alpha uD^\alpha v\,dx.
$$

These are Hilbert spaces. In $H_0^1$, the boundary condition is encoded by closure of $C_c^\infty(\Omega)$, rather than by pointwise values of an arbitrary representative. Define

$$
H^{-1}(\Omega)=(H_0^1(\Omega))^*.
$$

For $u\in H_0^1$, $a_{ij}u_{x_i}\in L^2$, so its distributional derivative is defined even though the coefficient need not have a classical derivative. For a test function,

$$
\langle Lu,\varphi\rangle=\int_\Omega\left(a_{ij}u_{x_i}\varphi_{x_j}+b_i u_{x_i}\varphi+cu\varphi\right)\,dx.
$$

## The operator maps into H minus one

The same expression extends to every $v\in H_0^1$:

$$
\langle Lu,v\rangle=\int_\Omega\left(a_{ij}u_{x_i}v_{x_j}+b_i u_{x_i}v+cuv\right)\,dx.
$$

By Hölder,

$$
|\langle Lu,v\rangle|\le C\left(\|\nabla u\|_2\|\nabla v\|_2+\|\nabla u\|_2\|v\|_2+\|u\|_2\|v\|_2\right)\le C\|u\|_{H_0^1}\|v\|_{H_0^1}.
$$

Therefore $Lu\in H^{-1}$ and

$$
L:H_0^1(\Omega)\longrightarrow H^{-1}(\Omega)\text{ is bounded and linear},\qquad \|Lu\|_{H^{-1}}\le C\|u\|_{H_0^1}.
$$

Conversely, a functional $f\in H^{-1}$ restricts to a distribution on $C_c^\infty(\Omega)$. Indeed, test-function convergence on a fixed compact support implies convergence in $H_0^1$. The inclusion $H^{-1}\subset\mathscr D'$ is injective because $C_c^\infty$ is dense in $H_0^1$.

> [!def] Weak solution
> For $f\in H^{-1}(\Omega)$, a **weak solution** of the Dirichlet problem is $u\in H_0^1(\Omega)$ such that
> $$
> \int_\Omega\left(a_{ij}u_{x_i}v_{x_j}+b_i u_{x_i}v+cuv\right)\,dx=\langle f,v\rangle_{H^{-1},H_0^1}\qquad\forall v\in H_0^1(\Omega).
> $$

Every such weak solution is a distributional solution. For a given $u\in H_0^1$ and $f\in H^{-1}$, equality on $C_c^\infty$ extends to all of $H_0^1$ by density and boundedness.

### Examples of right-hand sides

If $f\in L^2(\Omega)$, view it as an element of $H^{-1}$ via $\langle f,v\rangle=\int fv$. More generally, if

$$
f=g+\sum_{i=1}^nD_i g_i,\qquad g,g_i\in L^2(\Omega),
$$

then

$$
\langle f,v\rangle=\int_\Omega gv\,dx-\sum_{i=1}^n\int_\Omega g_i v_{x_i}\,dx
$$

defines a bounded functional on $H_0^1$. The derivative of $g_i$ is understood distributionally.

## Poisson problem and Riesz representation

> [!thm]
> For every $f\in H^{-1}(\Omega)$, the problem $-\Delta u=f$, $u\in H_0^1(\Omega)$, has a unique weak solution.

**Proof.** By [[Sobolev Inequalities & Compact Embeddings#Poincaré inequality and equivalent norms|Poincaré's inequality]], the bilinear form

$$
(u,v)_\nabla=\int_\Omega\nabla u\cdot\nabla v\,dx
$$

is an inner product inducing an equivalent Hilbert norm on $H_0^1$. The [[The Riesz Representation Theorem]] gives a unique $u\in H_0^1$ such that

$$
\int_\Omega\nabla u\cdot\nabla v\,dx=\langle f,v\rangle\qquad\forall v\in H_0^1.
$$

This is precisely the weak equation. **QED**

## Lax–Milgram theorem

Source: [[剩下的几次课.pdf#page=11|p. 11]].

> [!thm] Lax–Milgram
> Let $H$ be a real Hilbert space and $a:H\times H\to\mathbb{R}$ bilinear. Assume there are $M,\gamma>0$ such that
> $$
> |a(u,v)|\le M\|u\|_H\|v\|_H,\qquad a(u,u)\ge\gamma\|u\|_H^2\qquad\forall u,v\in H.
> $$
> Then for every $f\in H^*$ there is a unique $u\in H$ satisfying
> $$
> a(u,v)=\langle f,v\rangle\qquad\forall v\in H,\qquad \|u\|_H\le\gamma^{-1}\|f\|_{H^*}.
> $$

This generalizes Riesz representation to bounded coercive bilinear forms which need not be symmetric. The source ends with the statement; the existence theory for general elliptic operators continues in [[1. Existence and Uniqueness of weak solutions of elliptic equations]]. Strict ellipticity alone does not automatically make the full form coercive when lower-order terms are present; that continuation addresses the appropriate estimates and shifts.
