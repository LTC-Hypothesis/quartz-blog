# Weak Derivatives

[[PDE Note Week9Mon + Week10Wed+Week11Mon.pdf#page=5|Source, p. 5]] · [[PDE Week12 Wed.pdf#page=2|Further properties, pp. 2–3]]

[[Derivatives of Distributions]] → [[Approximation of bad functions by good functions]] → [[Chain Rule & Sobolev Space]]

## Definition

> [!def] Weak derivative
> Let $u\in L^1_{\mathrm{loc}}(\Omega)$. If its distributional derivative $D^\alpha u$ is represented by a function $v\in L^1_{\mathrm{loc}}(\Omega)$, then $v$ is the $\alpha$-th **weak derivative** of $u$. Equivalently,
> $$
> \int_\Omega v\varphi\,dx=(-1)^{|\alpha|}\int_\Omega uD^\alpha\varphi\,dx\qquad\forall\varphi\in C_c^\infty(\Omega).
> $$
> We write $D^\alpha u=v$.

If $u\in C^{|\alpha|}(\Omega)$, its classical derivative is its weak derivative. Every distribution has distributional derivatives, but such derivatives need not be locally integrable functions.

> [!remark] 整理注
> In the original weak-derivative definition, the last integral has an extra factor $(-1)^{|\alpha|}$. The correct identity is the one displayed above: $\langle D^\alpha u,\varphi\rangle=\int v\varphi=(-1)^{|\alpha|}\int uD^\alpha\varphi$.

The lecture uses the notation

$$
W^k(\Omega)=\{u\in L^1_{\mathrm{loc}}(\Omega):D^\alpha u\in L^1_{\mathrm{loc}}(\Omega)\text{ for every }|\alpha|\le k\}.
$$

This is a linear space, corresponding to the usual local Sobolev class $W^{k,1}_{\mathrm{loc}}(\Omega)$. Global $L^p$ conditions will define $W^{k,p}(\Omega)$ in [[Chain Rule & Sobolev Space]].

## Example: the absolute-value function

Let $u(x)=|x|$ on $\mathbb{R}$. Its weak first derivative is

$$
v(x)=\begin{cases}-1,&x<0,\\1,&x>0,\end{cases}
$$

with an arbitrary value at $0$.

**Proof.** For $\varphi\in C_c^\infty(\mathbb{R})$, integration by parts separately on the two half-lines gives

$$
-\int_{\mathbb{R}}|x|\varphi'(x)\,dx=-\int_{-\infty}^0\varphi(x)\,dx+\int_0^\infty\varphi(x)\,dx=\int_{\mathbb{R}}v\varphi\,dx.
$$

Thus $|x|\in W^1(\mathbb{R})$. **QED**

However, its second distributional derivative is $D^2|x|=2\delta_0$, by the jump formula in [[Derivatives of Distributions#A jump produces a Dirac mass]]. It has no weak second derivative in $L^1_{\mathrm{loc}}$.

**Proof that $2\delta_0$ is not a locally integrable function.** Suppose $2\delta_0=v\in L^1_{\mathrm{loc}}(\mathbb{R})$. Let $\varphi_\varepsilon(x)=j(x/\varepsilon)$, without the mass-normalizing prefactor. Then

$$
\int v(x)j(x/\varepsilon)\,dx=2j(0)>0.
$$

The left side tends to $0$ by dominated convergence, since $j(x/\varepsilon)\to0$ for $x\ne0$ and the integrand is bounded by $\|j\|_\infty|v|\mathbf1_{[-1,1]}$ for small $\varepsilon$. This is a contradiction. **QED**

## Uniqueness and the fundamental lemma

> [!lemma]
> If $v\in L^1_{\mathrm{loc}}(\Omega)$ and $\int v\varphi=0$ for every $\varphi\in C_c^\infty(\Omega)$, then $v=0$ a.e. Consequently, weak derivatives are unique up to equality a.e.

**Proof.** For $y\in\Omega$ and sufficiently small $\varepsilon$, $j_\varepsilon(y-\cdot)$ is a test function. Hence $v_\varepsilon(y)=0$. By [[Approximation of bad functions by good functions#Convergence of regularizations|local $L^1$ convergence of regularizations]], $v_\varepsilon\to v$ locally in $L^1$, giving $v=0$ a.e. Apply this to the difference of two proposed weak derivatives. **QED**

## Zero weak gradient

> [!thm]
> If $\Omega$ is connected, $u\in W^1(\Omega)$ and $\nabla u=0$ a.e., then $u$ is a.e. equal to a constant.

**Proof.** On a ball $B\Subset\Omega$, regularization commutes with weak differentiation, so $\nabla u_\varepsilon=(\nabla u)_\varepsilon=0$ for small $\varepsilon$. Thus $u_\varepsilon$ is constant on $B$. Local $L^1$ convergence implies $u$ is a.e. constant on $B$. Constants on overlapping balls agree; connectedness propagates the constant throughout $\Omega$. **QED**

> [!remark] 整理注
> The manuscript writes $u_\varepsilon=c_\varepsilon$ on $\Omega_\varepsilon$. This inner set may be disconnected. The overlapping-ball argument supplies the required connectedness step. The conclusion for a weakly differentiable function is equality a.e., rather than equality at arbitrarily chosen representatives.

The characterization by smooth approximation and the differentiation–regularization identity are proved in [[Approximation of bad functions by good functions]].
