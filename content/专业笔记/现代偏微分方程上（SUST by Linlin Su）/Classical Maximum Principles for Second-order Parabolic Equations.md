# Classical Maximum Principles for Second-order Parabolic Equations

## 2.1 Parabolic boundary and operators

Let $D\subset\mathbb{R}^{n+1}$ be a bounded domain, with coordinates $(x,t)$, such that $0<t<T$ in $D$ and $\overline D$ meets both $t=0$ and $t=T$. In this lecture, define

$$
\Gamma=\overline{\partial D\cap\{0\le t<T\}},\qquad D^*=\overline D\setminus\Gamma.
$$

$\Gamma$ is the **parabolic boundary** and $D^*$ the **parabolic interior** in the lecture's convention. For a cylinder,

$$
D=\Omega\times(0,T),\qquad \Gamma=(\overline\Omega\times\{0\})\cup(\partial\Omega\times[0,T]),\qquad D^*=\Omega\times(0,T].
$$

> [!remark] 整理注
> The Week 6 board includes the closure over the boundary expression. This includes the terminal lateral rim, makes $\Gamma$ compact, and is needed in the following distance argument. It completes the preliminary convention in [[Intro 二阶PDE#5. Parabolic boundary — opening page]]. For noncylindrical $D$, this is the specific boundary set used in these lectures; different formulations of parabolic boundary may use a more local time-directed definition.

**Fact.** If $P=(x_0,T)\in D^*$, then for some $\delta>0$,

$$
B_\delta(P)\cap D=B_\delta(P)\cap\{t<T\}=:B_\delta^-.
$$

**Proof.** Since $P\notin\Gamma$ and $\Gamma$ is compact, choose $\delta$ with $B_\delta(P)\cap\Gamma=\varnothing$. The connected half-ball $B_\delta^-$ meets $D$, since $P\in\partial D$. Its intersections with $D$ and $\mathbb{R}^{n+1}\setminus\overline D$ are disjoint open sets and exhaust it: there are no boundary points of $D$ in this half-ball. Connectedness implies the second set is empty. **QED**

Consider

$$
Lu=u_t-\left[a_{ij}(x,t)u_{x_i x_j}+b_i(x,t)u_{x_i}+c(x,t)u\right].
$$

> [!def] Parabolicity
> Assume $A=(a_{ij})$ is symmetric. The operator is **degenerately parabolic** if $A\ge0$, **parabolic** if $A>0$ pointwise, and **strictly parabolic** if there exists $\lambda_0>0$ with
> $$
> a_{ij}(x,t)\xi_i\xi_j\ge\lambda_0|\xi|^2\qquad\forall (x,t)\in D^*,\ \xi\in\mathbb{R}^n.
> $$

$C^{2,1}$ means two continuous spatial derivatives and one continuous time derivative, with one-sided time derivatives on the terminal face when it is included.

## 2.2 Weak Maximum Principle

For $u_t-\Delta u=f\le0$, the physical picture is a heat sink (“fridge”). The expected maximum is controlled by initial and lateral data.

> [!thm] WMP, $c\equiv0$
> Suppose $L$ is degenerately parabolic and $u\in C^{2,1}(D^*)\cap C(\overline D)$ satisfies $Lu\le0$ in $D^*$. Then
> $$
> \max_{\overline D}u=\max_\Gamma u.
> $$

**Proof.** First suppose $Lu<0$. If a maximum occurs at $P_0=(x_0,t_0)\in D^*$, then

$$
u_t(P_0)\ge0,\qquad D_xu(P_0)=0,\qquad D_x^2u(P_0)\le0.
$$

At an ordinary interior point $u_t=0$; at $t=T$, use the left derivative and the half-ball fact above. Since $A\ge0$,

$$
Lu(P_0)=u_t(P_0)-a_{ij}(P_0)u_{x_i x_j}(P_0)\ge0,
$$

a contradiction. Thus the maximum lies on $\Gamma$.

For $Lu\le0$, put $v_\varepsilon=u-\varepsilon t$. Since $c=0$,

$$
Lv_\varepsilon=Lu-\varepsilon<0,\qquad v_\varepsilon\longrightarrow u\text{ uniformly on }\overline D.
$$

Apply the strict case and pass to the limit. **QED**

> [!remark]
> Strict parabolicity and coefficient bounds are not used in this WMP proof. In particular, when $a_{ij}=0$, the transport operator $Lu=u_t-b_i u_{x_i}$ still satisfies this statement on the indicated boundary set.

> [!thm] WMP, $c\le0$
> Under the same assumptions, with $c\le0$,
> $$
> Lu\le0\quad\Longrightarrow\quad \max_{\overline D}u\le\max_\Gamma u^+.
> $$
> If $\max_{\overline D}u>0$, then $\max_{\overline D}u=\max_\Gamma u$.

**Proof.** If the maximum is nonpositive, the estimate is immediate. At a positive maximum, the term $-cu$ is nonnegative, so the strict-case contradiction is unchanged. Alternatively, work on $\{u>0\}$ with the zero-order-free operator, where $u_t-a_{ij}u_{x_i x_j}-b_i u_{x_i}=Lu+cu\le0$. A perturbation by $-\varepsilon t$ gives the nonstrict case. **QED**

> [!thm] Bounded-above zero-order coefficient
> Suppose $c(x,t)\le M$ for a constant $M$. Then
> $$
> Lu\le0\text{ in }D^*,\quad u|_\Gamma\le0\quad\Longrightarrow\quad u\le0\text{ on }\overline D.
> $$

**Proof.** Let $v=e^{-Mt}u$. Direct differentiation gives

$$
v_t-a_{ij}v_{x_i x_j}-b_i v_{x_i}-(c-M)v=e^{-Mt}Lu\le0.
$$

Now $c-M\le0$ and $v|_\Gamma\le0$. Apply the preceding WMP and multiply by $e^{Mt}>0$. **QED**

## 2.3 Hopf boundary point lemmas

Source: [[PDE Note Week6 LecWed.pdf#page=11|Week 6, p. 11]] and [[PDE Note Week7 LecMon.pdf#page=2|Week 7 Mon, pp. 2–7]].

### Baby Hopf B.P.L.

Let

$$
B_R^-:=\{(x,t):|x|^2+(t-R)^2<R^2,\ 0<t\le R\}.
$$

Assume $L$ is strictly parabolic there and $|a_{ij}|,|b_i|,|c|\le M$. Let $u\in C^{2,1}(B_R^-)\cap C(\overline{B_R^-})$, $Lu\le0$. Suppose $P_0=(x_0,t_0)$ lies on the spherical boundary, $x_0\ne0$, and

$$
u(P_0)>u(P)\qquad\forall P\in\overline{B_R^-}\setminus\{P_0\}.
$$

> [!lemma] Baby Hopf lemma
> For every outward direction $\eta$ at $P_0$ whose inward segment lies in $B_R^-$, the one-sided directional derivative satisfies
> $$
> \partial_\eta u(P_0)>0
> $$
> whenever it exists, provided one of the following holds: (i) $c\equiv0$; (ii) $c\le0$ and $u(P_0)\ge0$; (iii) $u(P_0)=0$, without a sign restriction on $c$.

Here $\eta$ is a space-time direction with $(x_0,t_0-R)\cdot\eta>0$; the derivative is taken along the inward segment ending at $P_0$.

**Proof.** In cases (i) and (ii), use the cap

$$
\Sigma=\{(x,t)\in B_R^-:|x|>|x_0|/2\}
$$

and the barrier

$$
v(x,t)=e^{-\alpha(|x|^2+(t-R)^2)}-e^{-\alpha R^2}=:E(x,t)-e^{-\alpha R^2}.
$$

Then $v=0$ on the spherical boundary and $\partial_\eta v(P_0)<0$. Its derivatives are

$$
v_{x_i}=-2\alpha x_iE,\qquad v_t=-2\alpha(t-R)E,\qquad v_{x_i x_j}=(4\alpha^2x_ix_j-2\alpha\delta_{ij})E.
$$

Consequently,

$$
Lv=E\left[-4\alpha^2a_{ij}x_ix_j+2\alpha\sum_i a_{ii}+2\alpha b_i x_i-2\alpha(t-R)-c\right]+ce^{-\alpha R^2}.
$$

On $\Sigma$, $|x|>|x_0|/2$, so the negative quadratic term dominates:

$$
Lv\le E\left[-\lambda_0|x_0|^2\alpha^2+(2nM+2\sqrt n MR+2R)\alpha+M\right]<0
$$

for sufficiently large $\alpha$. Set $w=u-u(P_0)+\varepsilon v$. Then

$$
Lw=Lu+c\,u(P_0)+\varepsilon Lv<0.
$$

On the spherical part of the parabolic boundary, $w\le0$. On the artificial boundary $|x|=|x_0|/2$, compactness gives a strict gap below $u(P_0)$; choose $\varepsilon>0$ small enough to keep $w\le0$ there. The WMP gives $w\le0$ in $\overline\Sigma$. Since $w(P_0)=0$,

$$
0\le\partial_\eta w(P_0)=\partial_\eta u(P_0)+\varepsilon\partial_\eta v(P_0),
$$

which yields the strict derivative inequality.

In case (iii), $u\le0$. With $c^+=\max(c,0)$ and $c^-=\min(c,0)$, replace $c$ by $c^-$:

$$
\widetilde Lu=u_t-a_{ij}u_{x_i x_j}-b_i u_{x_i}-c^-u=Lu+c^+u\le0.
$$

Case (ii) now applies. **QED**

### General Hopf B.P.L.

> [!lemma] Interior sphere version
> Suppose $P_0\in\Gamma$ is a strict local maximum relative to nearby interior points, $u$ is continuous at $P_0$, and a space-time ball inside $D$ is tangent at $P_0$. Assume $P_0$ is neither the north pole nor the south pole of that ball. Under local strict parabolicity, bounded coefficients, $Lu\le0$ and one of the three sign conditions above,
> $$
> \partial_\eta u(P_0)>0
> $$
> for each strictly outward direction for which the derivative exists.

The proof uses a small cap of the tangent ball and the same barrier. Spatial and temporal translations are allowed. Spatial rotations are harmless, but rotations mixing space with time do not preserve the parabolic operator. The exclusion of the two time-axis poles ensures a nonzero spatial component in the barrier's quadratic term.

### No strict first maximum at the top of a cylinder

Source: [[PDE Note Week7 LecMon.pdf#page=8|Week 7 Mon, pp. 8–13]].

Let $Q(R,h)=B_R(0)\times(0,h]$. Under the same strict parabolicity, boundedness and sign conditions, there is no $u$ satisfying

$$
Lu\le0\text{ in }Q(R,h),\qquad u(0,h)>u(x,t)\quad(|x|<R,\ 0<t<h).
$$

**Proof.** Write $m=u(0,h)$. Continuity implies $u(x,h)\le m$. We construct a barrier proving $u_t(0,h)>0$. Choose $\rho$ large and then $\delta>0$ small so the cap

$$
N=B_\rho(0,h-\rho)\cap\{h-\delta<t<h\}
$$

lies inside the cylinder, and use

$$
v(x,t)=\rho^2-|x|^2-(t-h+\rho)^2.
$$

On $N$, $0<v\le2\rho\delta$, while $v=0$ on the spherical boundary and $v_t(0,h)=-2\rho$. In cases (i),(ii),

$$
Lv=-2(t-h+\rho)+2\sum_i a_{ii}+2b_i x_i-cv\le2\rho(-1+M\delta)+2\delta+2M(n+\sqrt n R)<0.
$$

Choose $M\delta<1/2$ and $\rho$ large enough; shrink $\delta$ further to fit the cap inside $B_R\times(0,h]$. For $w=u-m+\varepsilon v$, the WMP as above gives $w\le0$ and $w(0,h)=0$. Hence $u_t(0,h)\ge2\varepsilon\rho>0$. But $D_xu(0,h)=0$, $D_x^2u(0,h)\le0$ and $cm\le0$, so $Lu(0,h)>0$, a contradiction. Case (iii) reduces to (ii) by replacing $c$ with $c^-$. **QED**

## 2.4 Strong Maximum Principle

Source: [[PDE Note Week7 LecWed.pdf#page=1|Week 7 Wed, pp. 1–6]].

For $P_0=(x_0,t_0)\in D^*$, let $S(P_0)$ consist of all $Q\in D^*$ which can be joined to $P_0$ by a continuous path in $D^*$ whose time coordinate is nondecreasing when travelling from $Q$ to $P_0$. Also set

$$
C(P_0)=S(P_0)\cap\{t=t_0\}.
$$

Both sets are path-connected. $S(P_0)$ is the part of the parabolic interior reachable backwards in time; it need not be all of $D^*$.

> [!thm] Parabolic SMP
> Let $L$ be strictly parabolic with bounded coefficients and $u\in C^{2,1}(D^*)\cap C(\overline D)$ satisfy $Lu\le0$. If
> $$
> u(P_0)=\max_{\overline D}u=:m,\qquad P_0\in D^*,
> $$
> then $u\equiv m$ on $S(P_0)$, provided (i) $c\equiv0$; (ii) $c\le0$ and $m\ge0$; or (iii) $m=0$.

**Proof.** Let $F=\{P\in\overline D:u(P)=m\}$.

**Step 1: local propagation on a time slice.** Fix $P_0\in F\cap D^*$ and let $d=\operatorname{dist}(P_0,\Gamma)>0$. Suppose there exists $\overline P=(\overline x,t_0)$ with $|\overline x-x_0|<d/3$ and $u(\overline P)<m$. Set $\delta=\frac12\operatorname{dist}(\overline P,F)>0$ and consider expanding lower half-ellipsoids

$$
E_\sigma=\left\{(x,t):\frac{|x-\overline x|^2}{(\sigma\delta)^2}+\frac{(t-t_0)^2}{\delta^2}<1,\ t\le t_0\right\}.
$$

For $\sigma<1$, $E_\sigma$ misses $F$; once its horizontal radius reaches $|\overline x-x_0|$, its closure meets $F$. The first contact occurs before reaching $\Gamma$, since

$$
\operatorname{dist}(\overline P,\Gamma)\ge d-|\overline P-P_0|>2d/3>|\overline P-P_0|.
$$

At a first contact $\widehat P$ on the curved boundary, use an interior tangent ball; if the contact is on the equator $t=t_0$, use a lower half-ball and the baby Hopf lemma. The contact is not at the bottom pole, whose distance from $\overline P$ is $\delta$, strictly less than the distance to $F$. A horizontal outward direction is available. Hopf gives a nonzero spatial derivative, contradicting the fact that $\widehat P$ is a maximum on its spatial slice. This proves local constancy along $t=t_0$.

**Step 2: propagation along the connected slice.** The set $F\cap C(P_0)$ is nonempty, relatively closed by continuity and relatively open by Step 1. Thus $C(P_0)\subset F$.

**Step 3: propagation backwards in time.** If $Q\in S(P_0)$ has $u(Q)<m$, take a time-nondecreasing path from $Q$ to $P_0$ and its first contact $P_1$ with $F$. By Step 2, a sufficiently small fixed spatial cylinder ending at $P_1$ has no point of $F$ at earlier times: otherwise constancy on that slice would reach the nearby path. At its top, $u(P_1)=m$. This contradicts the preceding no-strict-first-maximum lemma. Hence $S(P_0)\subset F$. **QED**

For a connected cylinder, $S(x_0,t_0)=\Omega\times(0,t_0]$. The conclusion propagates to earlier times; it makes no claim that $u$ must remain constant after $t_0$.

## Comparison principle for semilinear equations

Source: [[PDE Note Week7 LecWed.pdf#page=7|Week 7 Wed, pp. 7–11]].

Let $\Omega$ be a bounded connected domain with $C^2$ boundary, $D=\Omega\times(0,T)$ and $S=\partial\Omega\times(0,T]$. Consider

$$
\mathcal Lu=u_t-a_{ij}(x,t)u_{x_i x_j}+b_i(x,t)u_{x_i}+f(x,t,u),\qquad Bu=\partial_\eta u+\beta(x,t)u.
$$

Assume strict parabolicity, bounded $a_{ij},b_i$, $\beta\ge0$, and that $\eta$ is an outward spatial oblique vector field on $S$. Assume $f_s$ exists and is bounded uniformly in $(x,t)$ on each bounded interval of $s$.

> [!thm] Comparison
> For classical $u,v$, continuous on $\overline D$ with the indicated boundary derivatives, suppose
> $$
> \mathcal Lu\ge\mathcal Lv\text{ in }D^*,\qquad Bu\ge Bv\text{ on }S,\qquad u(x,0)\ge v(x,0)\text{ on }\overline\Omega.
> $$
> Then $u\ge v$ on $\overline D$. If the initial functions are not identical, then $u(x,t)>v(x,t)$ for every $x\in\overline\Omega$, $0<t\le T$.

**Proof.** Put $w=v-u$ and linearize:

$$
q(x,t)=\int_0^1 f_s(x,t,u+\theta(v-u))\,d\theta,\qquad w_t-a_{ij}w_{x_i x_j}+b_iw_{x_i}+qw\le0.
$$

Since $u,v$ are bounded, $|q|\le M$. For $\widetilde w=e^{-Mt}w$,

$$
\widetilde w_t-\left[a_{ij}\widetilde w_{x_i x_j}-b_i\widetilde w_{x_i}-(q+M)\widetilde w\right]\le0.
$$

The new bracket's zero-order coefficient is $-(q+M)\le0$. Also $B\widetilde w=e^{-Mt}Bw\le0$ and $\widetilde w(x,0)\le0$. A positive maximum in $D^*$ contradicts the SMP and the initial inequality. A positive maximum on $S$ gives, by Hopf, $\partial_\eta\widetilde w>0$, contradicting $B\widetilde w\le0$. Hence $w\le0$.

If $w=0$ at an interior point with $t>0$, SMP implies $w\equiv0$ at all earlier times, contradicting the nonidentical initial data. If $w=0$ at a lateral point with $t>0$, strict interior negativity and Hopf contradict $Bw\le0$. **QED**

> [!remark]
> Pure Neumann/oblique derivative data ($\beta\equiv0$) are allowed because the initial condition fixes the additive constant. For Dirichlet data, replace $Bu\ge Bv$ by $u\ge v$ on $S$; the strict conclusion holds for $x\in\Omega$, while equality may persist on the prescribed lateral boundary.
>
> 整理注：The board changes drift/reaction signs when introducing the semilinear operator. The operator and its linearization above use one consistent convention. The identity $B(e^{-Mt}w)=e^{-Mt}Bw$ requires the oblique derivative to be spatial; a time component would add an extra term.

## Connections

The next topic is [[Distributions (Schwartz)]]. For energy methods, see [[8. L2-theory for parabolic equations]].
