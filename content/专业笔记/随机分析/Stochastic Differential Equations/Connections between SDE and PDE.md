We consider such SDE, 
$$
X^{(t,x)}_s=x+\int_t^sb(\theta,X^{(t,x)}_\theta){d}\theta+\int_{t}^{s}\sigma(\theta,X^{(t,x)}_\theta){d}W_\theta,s\ge t\tag{$*1$}
$$
with the follow assumptions.

> [!def] Assumptions
> 1. $b_i,\sigma_{ij}:[0,\infty)\times\mathbb{R}^d\to\mathbb{R}$ are continuous and satisfy linear growth condition. 
> 2. For every pair of $(t,x)$, SDE $(*1)$ has a weak solution $(X^{(t,x)},W),(\Omega,\mathcal{F},\mathbb{P}),\{\mathcal{F}_s\}$.
> 3. The solution is unique of probability law.

^546e6e
# The Dirichlet Problem

> [!def] Dirichlet problem
> Suppose $\Omega\subseteq\mathbb{R}^d$ is open and bounded domain, $\mathscr{A}$ is [[Diffusion Process & Introduction of SDE#^3fb7e2|the differential operator]] which is elliptic. Consider the PDE, 
> $$
> \begin{cases}
> \mathscr{A}u-k(x)u=-g(x),&x\in\Omega\\
> u=f,&x\in\partial\Omega
> \end{cases}\tag{D}
> $$
> where $k:\overline{\Omega}\to[0,\infty),g:\overline{\Omega}\to\mathbb{R},f:\partial\Omega\to\mathbb{R}$ are continuous. The Dirichlet problem is to find a solution $u:\overline{\Omega}\to\mathbb{R}$ of PDE (D) and $u\in C^2(\Omega)$

> [!thm] The form of solution for PDE (D)
> Let $u$ be the solution od PDE (D) in the open, bounded domain $\Omega$, let 
> $$
> \tau_{\Omega}\triangleq\inf\left\{t\ge0:X_t\notin\Omega\right\}
> $$
> If $\mathbb{E}^x\tau_{\Omega}<\infty,\forall x\in\Omega$, under [[#^546e6e|the assumptions]], then the solution $u$ have the form
> $$
> u(x)=\mathbb{E}^x\left[f(X_{\tau_\Omega})\exp\left(-\int_{0}^{\tau_\Omega}k(X_s){d}s\right)+\int_{0}^{\tau_\Omega}g(X_t)\exp\left(-\int_{0}^{t}k(X_s){d}s\right){d}t\right]
> $$

**Proof**

**QED**
Now how can we guarantee the condition $\mathbb{E}^x[\tau_\Omega]<\infty$?

> [!lemma]
> Suppose for open and bounded domain $\Omega$ and some $1\le k\le d$, $\min_{x\in\overline{\Omega}}a_{kk}(x)>0$, then $\mathbb{E}^x[\tau_\Omega]<\infty$ holds.

**Proof**
The idea is to find a function $h(x)$ which satisfies **$(\mathscr{A}h)(x)$ is bounded** and **continuous** so that we can use the Ito's rule, 
$$
h(X_{t\wedge \tau_\Omega})=h(x)+\int_{0}^{t\wedge \tau_\Omega}(\mathscr{A}h)(X_{s}){d}s\Longrightarrow \mathbb{E}^x
[t\wedge \tau_\Omega]\le 2\max_{x\in\overline{\Omega}}|h(x)|<\infty
$$
Now we denote by 
$$
b=\min_{x\overline{\Omega}}|b(x)|,a=\min_{x\in\overline{\Omega}}|a_{kk}(x)|,q=\min_{x\in\overline{\Omega}}x_k
$$
and $\nu>\frac{2b}{a}$. Consider the function $h(x)=-\mu e^{\nu x_k}$ where $\mu>0$. Obviously, $h(x)\in C^\infty(\Omega)$ and then  
$$
-(\mathscr{A}h)(x)=\mu e^{\nu x_k}\left(\frac{1}{2}\nu^2a_{kk}(x)+b_k(x)\nu\right)\ge\frac{1}{2}\mu e^{\nu q}a\nu(\nu-\frac{2b}{a})>0
$$
We can  take $\mu\to\infty$ s.t. $(\mathscr{A}h)(x)\le -1$. 
**QED**

> [!warning]
> - $\min_{x\in\overline{\Omega}}a_{kk}(x)>0$ is strong than elliptic condition but weaker than uniformly elliptic condition. 
> - Now under the assumptions, 
> 
>   1. $\mathscr{A}$ is uniformly elliptic.
>   2. $a_{ij},b_i,k,g$ are Holder-continuous. 
>     3. Exterior sphere condition i.e $\forall x\in\partial\Omega$, there exists    ball $B(x)$ s.t. $\overline{B(x)}\cap\Omega=\emptyset, \overline{B(x)}\cap\partial\Omega=x$.
>     4. $f$ is still continuous on $\partial\Omega$.
> 
> Then there exists solution $u(x)\in C(\overline{\Omega})\cap C^2(\Omega)$.

# The Cauchy Problem and a Feynman-Kac Representation

> [!def] Assumptions
> Fix $T>0$, and appropriate constants $L>0,\lambda\ge1$, we consider the functions $f:\mathbb{R}^d\to\mathbb{R},g:[0,T]\times\mathbb{R}^d\to\mathbb{R}$ and continuous function $k:[0,T]\times\mathbb{R}^d\to[0,\infty)$. $f,g$ satisfy
> $$
> |f(x)|\le L\left(1+\|x\|^{2\lambda}\right)\text{ or }f(x)\ge0,\forall x\in\mathbb{R}^d
> $$
> $$
> |g(t,x)|\le L\left(1+\|x\|^{2\lambda}\right)\text{ or }g(t,x)\ge0,\forall (t,x)\in[0,T]\times\mathbb{R}^d
> $$
> and operator $\mathscr{A}_t$, 
> $$
> (\mathscr{A}_tf)(x)=\frac{1}{2}\sum_{i=1}^{d}\sum_{k=1}^{d}a_{ik}(t,x)\frac{\partial^2f(x)}{\partial x_i\partial x_k}+\sum_{i=1}^{d}b_i(t,x)\frac{\partial f(x)}{\partial x_i}
> $$

> [!def] Cauchy problem
> Under [[#^546e6e|the assumptions]], suppose that $v(t,x):[0,T]\times\mathbb{R}^d\to\mathbb{R}^d$ which is $v\in C^{1,2}\left([0,T)\times\mathbb{R}^d\right)$ satisfies such PDE
> $$
> \begin{cases}
> -\frac{\partial v}{\partial t}-\mathscr{A}_tv+k(t,x)v=g(t,x),&x\in[0,T)\times\mathbb{R}^d\\
> v(T,x)=f(x),&x\in\mathbb{R}^d
> \end{cases}\tag{C}
> $$

> [!thm]
> If $v$ satisfies the Cauchy problem and $v$ satisfies the polynomial growth condition for some $M>0,\mu\ge1$, 
> $$
> \max_{0\le t\le T}\left\|v(t,x)\right\|\le M\left(1+\|x\|^{2\mu}\right)
> $$
> Then $v(t,x)$ admits the stochastic representation
> $$ 
> \begin{aligned} v(t, x) = \mathbb{E}^{t,x}\Bigg[ & f(X_T)\exp\left\{-\int_{t}^{T} k(\theta, X_{\theta})d\theta\right\} \\ + & \int_{t}^{T} g(s, X_s)\exp\left\{-\int_{t}^{s} k(\theta, X_{\theta})d\theta\right\}ds \Bigg] \end{aligned} 
> $$
> for $(t,x)\in [0,T]\times\mathbb{R}^d$. In particular, such solution is unique. 

> [!warning]
> A set of conditions sufficient for the existence of solution $v$ satisfying the polynomial growth is 
> 1. $\mathscr{A}_t$ is uniformly ellipitic. 
> 2. $a_{ij},b_i,k$ are bounded.
> 3. $a_{ij},b_i,k,g$ are Holder-continuous. 
> 4. $f,g$ satisfy polynomial growth condition. 

> [!def] Fundamental solution
> fundamental solution of the second-order partial differential equation
> $$
> -\frac{\partial u}{\partial t}+k(x)u=\mathscr{A}_tu
> $$
> is nonnegetive function $G(t,x;\tau,\xi)$ which satisfies
> 1. For every $f(x)\in C_0(\mathbb{R}^d),\tau\in(0,T]$, the function 
>    $$
>    u(t,x)=\int_{\mathbb{R}^n}G(t,x;\tau,\xi)f(\xi){d}\xi,0\le t<\tau,x\in\mathbb{R}^d
>    $$
>    is bounded and belongs to $C^{1,2}([0,\tau)\times\mathbb{R}^d)$. 
> 2. $u(t,x)$ satisfies the PDE.
> 3. It holds 
>    $$
>    \lim_{t\uparrow\tau}u(t,x)=f(x)
>    $$

---
# Exercises

> [!question]
> In the case of bounded coefficients, i.e., $$ \tag{7.19} |b_i(t,x)|+\sum_{j=1}^r \sigma_{ij}^2(t,x)\le \rho;\quad 0\le t<\infty,\ x\in\mathbb R^d,\ 1\le i\le d, $$ the polynomial growth condition (7.14) in Theorem 7.6 may be replaced by $$ \tag{7.20} \max_{0\le t\le T}|v(t,x)|\le M e^{\mu\|x\|^2};\quad x\in\mathbb R^d $$ for some $M>0$ and $0<\mu<\big(1/(18\rho T d)\big)$.