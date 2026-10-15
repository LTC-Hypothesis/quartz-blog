# Intro: Second-order PDEs
## 1. Second-order elliptic equations

Let $\Omega\subset\mathbb{R}^n$ be a **domain**, i.e. an open and connected set. Write

$$
x=(x_1,\ldots,x_n),\qquad u\in C^2(\Omega).
$$

A linear second-order differential operator has the form

$$
\begin{aligned}
Lu
&=\sum_{i,j=1}^n a_{ij}(x)u_{x_i x_j}
+\sum_{i=1}^n b_i(x)u_{x_i}+c(x)u\\
&=a_{ij}(x)u_{x_i x_j}+b_i(x)u_{x_i}+c(x)u.
\end{aligned}
$$

Repeated indices are summed from $1$ to $n$ (**Einstein summation convention**). The corresponding equation is

$$
Lu=f(x),
$$

where $f$ is given and $u$ is the unknown.

> [!def] Ellipticity
> $L$ is **elliptic** in $\Omega$ if $A(x)=(a_{ij}(x))$ is symmetric and positive definite for every $x\in\Omega$:
> $$
> a_{ij}(x)\xi_i\xi_j>0
> \qquad(\xi\in\mathbb{R}^n\setminus\{0\}).
> $$
> In these lectures, $L$ is called **strictly elliptic** if there exists $\lambda_0>0$ such that
> $$
> a_{ij}(x)\xi_i\xi_j\ge\lambda_0|\xi|^2
> \qquad\forall x\in\Omega,\ \xi\in\mathbb{R}^n.
> $$

> [!remark] Terminology
> We retain the lecture's use of “strictly elliptic.” The displayed condition is a uniform **lower** ellipticity bound; boundedness of the coefficients, when needed, is stated separately.

### Linear, semilinear and quasilinear equations

| Type | Form | Dependence of the principal coefficients |
| --- | --- | --- |
| Linear | $a_{ij}(x)u_{x_i x_j}+b_i(x)u_{x_i}+c(x)u=f(x)$ | $x$ only |
| Semilinear | $a_{ij}(x)u_{x_i x_j}+b(x,u,Du)=0$ | $x$ only |
| Quasilinear | $a_{ij}(x,u,Du)u_{x_i x_j}+b(x,u,Du)=0$ | May depend on $u,Du$ |

All three are linear in the highest-order derivatives $D^2u$; the lower-order terms in a semilinear or quasilinear equation need not be linear.

## 2. Harmonic, subharmonic and superharmonic functions

Source: [[PDE Note Week1LectureMon.pdf#page=3|pp. 3–4]].

Let $f(z)=u(x,y)+iv(x,y)$ be analytic in $\Omega\subset\mathbb{R}^2$, where $z=x+iy$. The Cauchy–Riemann equations give

$$
u_x=v_y,\qquad v_x=-u_y.
$$

Hence

$$
\Delta u=v_{yx}-v_{xy}=0,\qquad\Delta v=-u_{yx}+u_{xy}=0.
$$

Thus the real and imaginary parts of an analytic function are **harmonic**.

The product rule

$$
\Delta(fg)=(\Delta f)g+2\nabla f\cdot\nabla g+f\Delta g
$$

implies

$$
\Delta|f|^2=\Delta(u^2+v^2)=2|\nabla u|^2+2|\nabla v|^2\ge0.
$$

Therefore $|f|^2$ is subharmonic.

> [!def] Sign convention
> For $w\in C^2(\Omega)$:
> - $\Delta w=0$: **harmonic**;
> - $\Delta w\ge0$: **subharmonic**;
> - $\Delta w\le0$: **superharmonic**.
>
> For the operator $L$ with positive principal part used here:
> $$
> Lu\ge f\quad\Longleftrightarrow\quad
> u\text{ is a subsolution (lower solution) of }Lu=f,
> $$
> $$
> Lu\le f\quad\Longleftrightarrow\quad
> u\text{ is a supersolution (upper solution) of }Lu=f.
> $$

In one dimension, $u''=0$ gives affine functions, $u''\ge0$ gives convex functions, and $u''\le0$ gives concave functions. For fixed endpoint values, a convex function lies below its chord, while a concave function lies above it.

> [!remark]
> In dimension $n\ge2$, subharmonicity does **not** imply convexity. For example,
> $$
> u(x,y)=2x^2-y^2,\qquad \Delta u=2>0,
> $$
> but $D^2u=\operatorname{diag}(4,-2)$ is not positive semidefinite. See [[弱极值原理#1. WMP with c identically zero|WMP]].

## 3. Examples of elliptic equations

### Electrostatics

Source: [[PDE Note Week1LectureMon.pdf#page=5|p. 5]].

$$
-\Delta u=f(x),\qquad x\in\Omega\subset\mathbb{R}^3,
$$

where $u$ is the electric potential and $f$ is the charge density, with physical constants absorbed into $f$.

### Minimal surface equation

Source: [[PDE Note Week1LectureMon.pdf#page=5|pp. 5–6]].

For a graph $z=u(x,y)$, the lecture uses the mean-curvature convention

$$
H=\frac12\operatorname{div}
\left(\frac{\nabla u}{\sqrt{1+|\nabla u|^2}}\right),\qquad\operatorname{div}F=\sum_i\frac{\partial F_i}{\partial x_i}.
$$

A minimal surface satisfies $H=0$, i.e.

$$
\operatorname{div}
\left(\frac{\nabla u}{\sqrt{1+|\nabla u|^2}}\right)=0.
$$

Multiplying by $(1+|\nabla u|^2)^{3/2}$ gives

$$
(1+u_y^2)u_{xx}-2u_xu_yu_{xy}+(1+u_x^2)u_{yy}=0.
$$

This is a quasilinear second-order equation, with

$$
A=
\begin{pmatrix}
1+u_y^2&-u_xu_y\\
-u_xu_y&1+u_x^2
\end{pmatrix}.
$$

For $\xi=(\xi_1,\xi_2)$,

$$
\begin{aligned}
a_{ij}\xi_i\xi_j
&=(1+u_y^2)\xi_1^2-2u_xu_y\xi_1\xi_2+(1+u_x^2)\xi_2^2\\
&=|\xi|^2+(u_y\xi_1-u_x\xi_2)^2\ge|\xi|^2.
\end{aligned}
$$

Thus this multiplied operator has the lecture's lower ellipticity bound $\lambda_0=1$.

> [!remark] 整理注
> This calculation concerns the multiplied equation above. Its upper coefficient bound depends on $|\nabla u|$. Before multiplication, the principal coefficient matrix is $A/(1+|\nabla u|^2)^{3/2}$, whose smallest eigenvalue is $(1+|\nabla u|^2)^{-3/2}$. A uniform bound on $|\nabla u|$ matters when applying results requiring bounded coefficients or a two-sided uniform ellipticity bound.

### Irrotational incompressible flow

Let $V=(V_1,V_2,V_3)$ be the velocity field in $\Omega\subset\mathbb{R}^3$. Irrotationality means

$$
\operatorname{curl}V=\nabla\times V=0.
$$

If $\Omega$ is simply connected, a sufficiently smooth irrotational field has a velocity potential:

$$
V=\nabla\varphi.
$$

Incompressibility gives $\operatorname{div}V=0$, and therefore

$$
\Delta\varphi=\operatorname{div}(\nabla\varphi)=0.
$$

## 4. Heat equation and steady states

Let $u(x,t)$ denote temperature, $c$ specific heat, and $\rho$ the density of the medium. With $c,\rho$ constant, the thermal energy density is

$$
E=c\rho u.
$$

For an arbitrary control volume $N\Subset\Omega$, conservation of energy gives

$$
\frac{d}{dt}\int_N E\,dx
=-\int_{\partial N}J\cdot n\,dS+\int_N F\,dx,
$$

where $J$ is the heat flux, $n$ the outward unit normal and $F$ the net rate of heat production per unit volume.

**Fourier's law** takes the form

$$
J=-A(x)\nabla u,
$$

where $A(x)$ is symmetric and positive definite. Thus

$$
J\cdot(-\nabla u)=\nabla u\cdot A\nabla u>0
\quad\text{if }\nabla u\ne0.
$$

Using the divergence theorem,

$$
\begin{aligned}
\frac{d}{dt}\int_N c\rho u\,dx
&=\int_{\partial N}A\nabla u\cdot n\,dS+\int_N F\,dx\\
&=\int_N\bigl[\operatorname{div}(A\nabla u)+F\bigr]\,dx.
\end{aligned}
$$

Since $N$ is arbitrary,

$$
\boxed{c\rho u_t-\operatorname{div}(A\nabla u)=F(x,t).}
$$

For a homogeneous isotropic medium, $A=kI$ with constant thermal conductivity $k>0$. Set

$$
a^2=\frac{k}{c\rho},\qquad f=\frac{F}{c\rho}.
$$

Then

$$
u_t-a^2\Delta u=f(x,t).
$$

Here $a^2$ is the heat diffusion coefficient. If the forcing and the solution are independent of time, the steady state satisfies the elliptic equation

$$
-a^2\Delta u=f(x).
$$

### Wave equation and steady states

Source: [[PDE Note Week1LectureMon.pdf#page=10|p. 10]].

The wave equation is

$$
u_{tt}-k^2\Delta u=f(x,t).
$$

For time-independent forcing, a steady state satisfies

$$
-k^2\Delta u=f(x).
$$

Thus elliptic equations also arise as stationary equations of evolution problems.

## 5. Parabolic boundary — opening page

The opening page considers $u_t-a^2\Delta u=f(x,t)$ on a bounded space-time domain. The subsequent lecture includes the closure in its boundary convention:

$$
\Gamma=\overline{\partial D\cap\{0\le t<T\}},\qquad D^*=\overline D\setminus\Gamma.
$$

For a cylinder,

$$
D=\Omega\times(0,T),\qquad\Gamma=(\overline\Omega\times\{0\})\cup(\partial\Omega\times[0,T]),\qquad D^*=\Omega\times(0,T].
$$

The terminal face over $\Omega$ belongs to the parabolic interior. The terminal lateral rim belongs to $\Gamma$ under this closed-boundary convention.

See [[Classical Maximum Principles for Second-order Parabolic Equations#2.1 Parabolic boundary and operators]] for the continuation, the half-ball property at terminal points, and the precise convention for noncylindrical domains.

Source: [[PDE Note Week5 LectureSat.pdf#page=4|Week 5 Sat, p. 4]]; [[PDE Note Week6 LecWed.pdf#page=1|Week 6 Wed, continuation]].

## Connections

- [[弱极值原理]]: boundary control, comparison, uniqueness and a priori estimates.
- [[强极值原理]]: interior sphere condition, Hopf lemma and strict comparison.
- [[1. Existence and Uniqueness of weak solutions of elliptic equations]]: the weak-solution theory in the second part of the course.
- [[8. L2-theory for parabolic equations]]: the $L^2$ theory in the second part of the course.
