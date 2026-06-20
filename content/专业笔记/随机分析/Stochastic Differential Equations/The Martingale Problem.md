# Fundamental Martingales
> [!def] Second-order differential operator
> We introduce the second-order differential operator,
> $$
> (\mathscr{A}_tf)(x)=\frac{1}{2}\sum_{i=1}^{d}\sum_{k=1}^{d}a_{ik}(t,x)\frac{\partial^2 f(x)}{\partial x_i\partial x_k}+\sum_{i=1}^{d}b_i(t,x)\frac{\partial f(x)}{\partial x_i}
> $$
> where $a_{ik}(t,x)$ are [[Diffusion Process & Introduction of SDE#^cefffc|the diffusion matrix]]. If $f(t,x)$ is the function of $[0,\infty)\times\mathbb{R}^d$, then $\mathscr{A}_tf$ is obtained by applying $\mathscr{A}_t$ on $f(t,\cdot)$. 

> [!proposition]
> For function $f(t,x):[0,\infty)\times\mathbb{R}^d\to\mathbb{R}$ belongs to $C^{1,2}((0,\infty)\times\mathbb{R}^d)$, then the process
> $$
> M^f\triangleq f(t,X_t)-f(x,X_0)-\int_{0}^{t}\left(\frac{\partial f}{\partial t}+\mathscr{A}_tf\right)(s,X_s){d}s
> $$
> is a continuous, local martingale.
> Moreover, if there exists $g\in C([0,\infty)\times\mathbb{R}^d)\cap C((0,\infty)\times\mathbb{R}^d)$, then $M^g\in\mathcal{M}^{c,loc}$ and satisfies
> $$
> \langle M^f,M^g\rangle=\sum_{i=1}^{d}\sum_{k=1}^{d}\int_{0}^{t}a_{ik}(s,X_s)\frac{\partial f(s,X_s)}{\partial x_i}\frac{\partial g(s,X_s)}{\partial x_k}{d}s
> $$
> Furthermore, if $f\in C_0([0,\infty)\times\mathbb{R}^d)$ and $\sigma_{ij}$ is bounded on $\text{supp} \ f$, then $M^f\in\mathcal{M}^c_2$.

^4b0475

**Proof**
By [[The Change-of-Variable Formula#^57e183|the Ito's rule]], 
$$
M^f=\sum_{i=1}^{d}\sum_{j=1}^{r}\int_{0}^{t}\sigma_{ij}(s,X_s)\frac{\partial f(s,X_s)}{\partial s}{d}W^{(j)}_s
$$
We define the stopping time, 
$$
\tau_n=\left\{t\ge0:\|X_s\|\ge n\text{ or }\int_{0}^{t}\sigma_{ij}^2(s,X_s)\ge n\text{ for some }i,j\right\}
$$
Obviously, $\tau_n\to\infty$ as $n\to\infty$. We consider 
$$
M^f_{t}(n)=M^f_{t\wedge \tau_n}=\sum_{i=1}^{d}\sum_{j=1}^{r}\int_{0}^{t\wedge \tau_n}\sigma_{ij}(s,X_s)\frac{\partial f(s,X_s)}{\partial s}{d}W^{(j)}_s
$$
is a continuous martingale. 
**QED**
> [!proposition] Functional case
> Let $b_i(t,y)$ and $\sigma_{ij}(t,y)$; $1\le i\le d$, $1\le j\le r$, be progressively measurable functionals from $[0,\infty)\times C[0,\infty)^d$ into $\mathbb R$. By analogy with (2.2), we define the diffusion matrix $a(t,y)$ with components 
> $$
> a_{ik}(t,y)\triangleq\sum_{j=1}^r\sigma_{ij}(t,y)\sigma_{kj}(t,y);\quad 0\le t<\infty,\ y\in C[0,\infty)^d. 
> $$ 
> Suppose that $(X,W),(\Omega,\mathscr F,P),\{\mathscr F_t\}$, is a weak solution to the functional stochastic differential equation (3.15), and set 
> $$
> (\mathscr A_t' u)(y) = \frac12\sum_{i=1}^d\sum_{k=1}^d a_{ik}(t,y)\frac{\partial^2 u(y(t))}{\partial x_i\partial x_k}+\sum_{i=1}^d b_i(t,y)\frac{\partial u(y(t))}{\partial x_i}; 
> $$ 
> $$ 0\le t<\infty,\ u\in C^2(\mathbb R^d),\ y\in C[0,\infty)^d. $$ Then, for any functions $f,g\in C([0,\infty)\times\mathbb R^d)\cap C^{1,2}((0,\infty)\times\mathbb R^d)$, the process 
> $$
> M_t^f\triangleq f(t,X_t)-f(0,X_0)-\int_0^t\left[\frac{\partial f}{\partial s}+\mathscr A_s' f\right](s,X)ds,\ \mathscr F_t;\quad 0\le t<\infty 
> $$ 
> is in $\mathscr M^{c,\mathrm{loc}}$, and $$\langle M^f,M^g\rangle_t=\sum_{i=1}^d\sum_{k=1}^d\int_0^t a_{ik}(s,X)\frac{\partial}{\partial x_i}f(s,X_s)\frac{\partial}{\partial x_k}g(s,X_s)ds. $$ Furthermore, if $f\in C_0([0,\infty)\times\mathbb R^d)$ and for each $0<T<\infty$ we have $$\|\sigma(t,y)\|\le K_T;\quad 0\le t\le T,\ y\in C[0,\infty)^d, $$ where $K_T$ is a constant depending on $T$, then $f\in\mathscr M_2^c$.

^4eb5a2

**Proof**

**QED**
> [!warning]
> The simplest case is that of a d-dimensional Brownian motion, which corresponding to $b_i(t,x)=0,\sigma_{ij}=\delta_{ij}$. Then 
> $$
> \mathscr{A}f=\frac{1}{2}\Delta f
> $$

> [!proposition] Martingale characterization of Brownian motion
> A continuous, adapted process $W=\{W_t,\mathscr F_t;\ 0\le t<\infty\}$ is a $d$-dimensional Brownian motion if and only if $$ f(W_t)-f(W_0)-\frac12\int_0^t\Delta f(W_s)ds,\ \mathscr F_t;\quad 0\le t<\infty, $$ is in $\mathscr M^{c,\mathrm{loc}}$ for every $f\in C^2(\mathbb R^d)$.

**Proof**
$\Longrightarrow$: It is done by the Ito's rule or [[#^4b0475|the proposition]]. 
$\Longleftarrow$: Take function $f(x)=x_ix_j,1\le i,j\le d$. Then 
$$
\Delta(x_ix_j)=2\delta_{ij},1\le i,j\le d
$$
We denote $M^f_t=f(W_t)-f(W_0)-\frac12\int_0^t\Delta f(W_s)ds$ and we have 
$$
M^{x_ix_j}_t=W_t^{(i)}W_t^{(j)}-W_0^{(i)}W_0^{(j)}-\delta_{ij}t\in\mathcal{M}^{c,loc}
$$
Then by [[The Change-of-Variable Formula#^b655c5|characterization of Brownian motion]], we have 
$$
\left\langle W^{(i)},W^{(j)}\right\rangle_t=\delta_{ij}t\xRightarrow{levy} W_t\text{ is a Brownian motion}
$$
**QED**
# Weak Solutions and Martingale Problems
> [!def]
> Let $b_i(t,y)$ and $\sigma_{ij}(t,y)$; $1\le i\le d$, $1\le j\le r$, be progressively measurable functionals from $[0,\infty)\times C[0,\infty)^d$ into $\mathbb R$. We define the diffusion matrix $a(t,y)$ with components 
> $$
> a_{ik}(t,y)\triangleq\sum_{j=1}^r\sigma_{ij}(t,y)\sigma_{kj}(t,y);\quad 0\le t<\infty,\ y\in C[0,\infty)^d. 
> $$ 
> Set 
> $$
> (\mathscr A_t' u)(y) = \frac12\sum_{i=1}^d\sum_{k=1}^d a_{ik}(t,y)\frac{\partial^2 u(y(t))}{\partial x_i\partial x_k}+\sum_{i=1}^d b_i(t,y)\frac{\partial u(y(t))}{\partial x_i}; 
> $$ 
> $$ 0\le t<\infty,\ u\in C^2(\mathbb R^d),\ y\in C[0,\infty)^d. $$

> [!def] Local martingale problem (LMP)
> The local martingale problem associated with $\{\mathscr{A}'_t\}$ is that find a probability measure $\mathbb{P}$ on $\left(C[0,\infty)^d,\mathcal{B}(C[0,\infty)^d)\right)$ s.t. the process 
> $$
> M^f\triangleq f(y(t))-f(y(0))-\int_{0}^{t}(\mathscr{A}'_sf)(y){d}s,\mathcal{F}_t
> $$
> is a continuous, local martingale for every $f\in C^2(\mathbb{R}^d)$.

> [!proposition]
> Let $\mathbb{P}$ be a probability measure on $(C[0,\infty)^d,\mathscr{B}(C[0,\infty)^d))$ under which the process $M^f$ is a continuous, local martingale for the choices $f(x)=x_i$ and $f(x)=x_i x_k, 1\le i,k\le d$. Then there is an $r$-dimensional Brownian motion $W=\{W_t,\tilde{\mathscr{F}}_t;0\le t<\infty\}$ defined on an extension $(\tilde{\Omega},\tilde{\mathscr{F}},\tilde{P})$ of $(C[0,\infty)^d,\mathscr{B}(C[0,\infty)^d),P)$, such that $(X_t\triangleq y(t),W_t),(\tilde{\Omega},\tilde{\mathscr{F}},\tilde{P}),\{\tilde{\mathscr{F}}_t\}$, is a weak solution to [[Weak Solutions#^3842a1|functional SDE]].

> [!proposition] Existence of LMP
> The existence of solution to the LMP associated with $\{\mathscr{A}'_t\}$ under $\mathbb{P}$ $\Longleftrightarrow$ The existence of the weak solution to the [[Weak Solutions#^3842a1|functional SDE]].

^555702

> [!proposition] Uniqueness of LMP
> The uniqueness of solution to the LMP associated with $\{\mathscr{A}'_t\}$ under $\mathbb{P}$ with fixed but arbitrary initial distribution 
> $$
> \mathbb{P}\left[y\in C[0,\infty)^d;y(0)\in\Gamma\right]=\mu(\Gamma)
> $$
> $\Longleftrightarrow$ The uniqueness in the sense of probability law to the [[Weak Solutions#^3842a1|functional SDE]].

^2de37e

> [!def] Martingale problem (MP)
> The martingale problem associated with $\{\mathscr{A}'_t\}$ is that find a probability measure $\mathbb{P}$ on $\left(C[0,\infty)^d,\mathcal{B}(C[0,\infty)^d)\right)$ s.t. the process 
> $$
> M^f\triangleq f(y(t))-f(y(0))-\int_{0}^{t}(\mathscr{A}'_sf)(y){d}s,\mathcal{F}_t
> $$
> is a continuous martingale for every $f\in C^2_0(\mathbb{R}^d)$.

> [!def] Assumptions
> Given progressively measurable functionals $b_i,\sigma_{ij}:[0,\infty)\times C[0,\infty)^d\to\mathbb{R}$ for $1\le i\le d,1\le j\le r$, operator $\{\mathscr{A}'_t\}$ and probability measure $\mu$ on $\mathcal{B}(\mathbb{R}^d)$. 
> 1. (A) There exists a weak solution of [[Weak Solutions#^3842a1|functional SDE]] with the initial distribution $\mu$.
> 2. (B)  There exists a solution $\mathbb{P}$ to the local martingale problem associated $\{\mathscr{A}'_t\}$ with $\mathbb{P}[y(0)\in\Gamma]=\mu(\Gamma),\forall\Gamma\in\mathcal{B}(\mathbb{R}^d)$. 
> 3. (C) There exists a solution $\mathbb{P}$ to the martingale problem associated $\{\mathscr{A}'_t\}$ with $\mathbb{P}[y(0)\in\Gamma]=\mu(\Gamma),\forall\Gamma\in\mathcal{B}(\mathbb{R}^d)$. 

^8211bc

> [!proposition]
> About [[#^8211bc|assumptions]] (A) (B) (C).
> 1. (A) $\Longleftrightarrow$ (B)
> 2. (C) $\Longrightarrow$ (A),(B)
> 3. (A) $\Longrightarrow$ (C) under either of the additional assumptions:
>    - (A1) For each $0<T<\infty$, it holds 
>      $$
>      \|\sigma(t,y)\|\le K_T,0\le t\le T, y\in C[0,\infty)^d
>      $$
>    - (A2) Each $\sigma_{ij}(t,y)$ is of the form $\sigma_{ij}(t,y)=\tilde{\sigma}_{ij}(t,y(t))$, where $\tilde{\sigma}_{ij}:[0,\infty)\times C[0,\infty)^d\to\mathbb{R}$ are Borel measurable and bounded on the compact sets.

**Proof**
1. We have proved by [[#^555702|the existence of LMP]] and [[#^2de37e|the uniqueness of LMP]].
2. It suffices to prove (C) $\Longrightarrow$ (B). Suppose $\mathbb{P}$ is the solution of (MP) and $f\in C^2(\mathbb{R}^d)$. We define the stopping time $$S_k=\inf\left\{t\ge0:\|y(t)\|\ge k\right\},S_k\uparrow\infty$$ Let $g_k(x)$ as follow, $$g_k(x)=\begin{cases}
f(x),&\|x\|\le k\\
0,&\|x\|>k
\end{cases}$$ Then $g_k\in C^2_0(\mathbb{R}^d)$ and thus $M^{g_k}_t=M^f_t$ is a martingale for $t\le S_k$. Hence, $M^f\in\mathcal{M}^{c,loc}$. 
3. Under condition (A1), [[#^4eb5a2|functional case]] 

**QED**
# Well-Posedness and the Strong Markov Property

# Existence
> [!thm] Skorohod, Stroock, Varadhan. (Existence)
> Consider the SDE 
> $$
> dX_t=b(X_t){d}t+\sigma(X_t){d}W_t\tag{$*$}
> $$
> where $b_i,\sigma_{ij}:\mathbb{R}^d\to\mathbb{R}$ are bounded and continuous and every initial distribution $\mu$ on $\mathcal{B}(\mathbb{R}^d)$ satisfies the condition
> $$
> \int_{\mathbb{R}^d}\|x\|^{2m}\mu(dx)<\infty
> $$
> Then there exists a weak solution of the SDE $(*)$.

# Uniqueness
> [!thm] Stroock & Varadhan. (Uniqueness)
> 

---
# Exercises