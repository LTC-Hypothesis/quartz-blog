# Poisson Process and Stochastic Integration

> [!warning]
> Notes compiled from the lecture notes 《带跳过程的随机积分入门》 Ch.9, following Cont & Tankov [19], Protter [16], Ikeda & Watanabe [17]. All processes are defined on a filtered probability space $(\Omega,\mathcal{F},(\mathcal{F}_t)_{t\ge0},\mathbb{P})$ satisfying the usual conditions.

# Poisson Process

## Counting Process and the Definition of Poisson Process

> [!def] Counting process
> Let $\{T_n\}_{n\ge0}$ be a sequence of stopping times with $T_0=0,\ a.s.$. The process $N=(N_t)_{0\le t\le\infty}$ defined by
> $$
> N_t:=\sum_{n\ge1}\mathbf{1}_{t\ge T_n},\qquad 0\le t<\infty,
> $$
> taking values in $\mathbb{N}_0\cup\{\infty\}$, is called the **counting process** associated with $\{T_n\}_{n\ge0}$.

^def-counting

> [!warning]
> If $\{T_k\}$ are the waiting times (i.e. $T_n=\tau_1+\cdots+\tau_n$ with $\{\tau_k\}$ i.i.d.), then
> $$
> N_t:=\sup\Big\{n\ge1:\ \sum_{k=1}^n T_k\le t\Big\}:=\inf\Big\{n\ge1:\ \sum_{k=1}^n T_k>t\Big\}.
> $$
> Let $T=\sup_n T_n$. Then $[T_n,\infty)=\{N\ge n\}:=\{(t,\omega):\ N_t(\omega)\ge n\}$, $[T_n,T_{n+1})=\{N=n\}$, $[T,\infty)=\{N=\infty\}$. We say $N$ **does not explode** if $T=\infty,\ a.s.$. Note that for $0\le s<t<\infty$,
> $$
> N_t-N_s=\sum_{n\ge1}\mathbf{1}_{s<T_n\le t},
> $$
> i.e. $N_t-N_s$ counts the number of jumping times $T_n$ falling in $(s,t]$.

> [!proposition]
> The counting process $N$ is $\mathcal{F}_t$-adapted **if and only if** the sequence $\{T_n\}_{n\ge0}$ is a sequence of stopping times.
>
> *Proof.* See P. Protter [16]. $\square$

^prop-adapted

> [!def] Poisson process
> A non-exploding $\mathcal{F}_t$-adapted counting process $N$ is called an **$\mathcal{F}_t$-Poisson process** if it satisfies:
> 1. **Independent increments:** for all $s,t$ with $0\le s<t<\infty$, $N_t-N_s$ is independent of $\mathcal{F}_s$;
> 2. **Stationary increments:** for all $s,t,u,v$ with $0\le s<t<\infty$, $0\le u<v<\infty$ and $t-s=v-u$, $N_t-N_s$ and $N_v-N_u$ have the same distribution.

^def-poisson

> [!thm] Properties of a Poisson process
> Let $N=(N_t)_{t\ge0}$ be an $\mathcal{F}_t$-Poisson process. Then the following hold:
> 1. $N_t<\infty,\ a.s.$ for every $t>0$;
> 2. For every $\omega\in\Omega$, the sample path $t\mapsto N_t(\omega)$ is a right-continuous pure jump (step) function;
> 3. $t\mapsto N_t$ is RCLL, and its jumps are exhausted by an at most countable sequence of stopping times;
> 4. $\mathbb{P}(N_{t-}=N_t)=1$ for every $t>0$, where $N_{t-}:=\lim_{s\uparrow t}N_s$;
> 5. $(N_t)_{t\ge0}$ is **stochastically continuous** (continuous in probability): for all $s,t>0,\ \varepsilon>0$,
>    $$
>    \lim_{s\to t}\mathbb{P}(|N_s-N_t|>\varepsilon)=0;
>    $$
> 6. $N_t$ has a Poisson distribution with parameter $\lambda t$ ($\lambda\ge0$):
>    $$
>    \mathbb{P}(N_t=n)=\frac{(\lambda t)^n}{n!}e^{-\lambda t},\qquad n=0,1,2,\cdots
>    $$
>    $\lambda$ is called the **intensity** of the Poisson process $N$;
> 7. $\mathbb{E}[N_t]=\lambda t$, $\operatorname{Var}[N_t]=\lambda t$, and the characteristic function is
>    $$
>    \mathbb{E}[e^{iuN_t}]=\exp\big[\lambda t(e^{iu}-1)\big],\qquad \forall u\in\mathbb{R};
>    $$
> 8. For $0\le s<t<\infty$, $\mathbb{E}[N_t]<\infty$ and
>    $$
>    \mathbb{E}[N_t-N_s|\mathcal{F}_s]=\lambda(t-s);
>    $$
> 9. **Markov property:** for $0\le s<t<\infty$, $\mathbb{E}[N_t]<\infty$, and for every bounded Borel function $f$,
>    $$
>    \mathbb{E}[f(N_t)|N_u,\ u\le s]=\mathbb{E}[f(N_t)|N_s];
>    $$
> 10. **Decomposition (closure under addition):** if $N'=(N'_t)_{t\ge0}$ is a Poisson process independent of $N$ with intensity $\lambda'$, then $N+N'=(N_t+N'_t)_{t\ge0}$ is a Poisson process with intensity $\lambda+\lambda'$.
>
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

^thm-poisson-props

> [!warning]
> In real applications many stochastic phenomena can be modelled by Poisson processes. Examples: the arrival of customers to a queue, claims arriving at an insurance company, radioactive particle counts, jumps in the price of a financial asset, etc.

## The Compensated Poisson Process

> [!thm]
> Let $N$ be an $\mathcal{F}_t$-Poisson process with intensity $\lambda$. Then
> 1. $\widetilde{N}:=(\widetilde{N}_t)_{t\ge0}:=(N_t-\lambda t)_{t\ge0}$ is an $\mathcal{F}_t$-martingale. $\widetilde{N}$ is called the **compensated Poisson process**, and $(\lambda t)_{t\ge0}$ is its **compensator**;
> 2. $(N_t-\lambda t)^2-\lambda t$ is an $\mathcal{F}_t$-martingale.
>
> *Proof.* Denote $M_t:=N_t-\lambda t$.
> 1. By the independent increments property, $N_t-N_s\perp\mathcal{F}_s$ and $N_s$ is $\mathcal{F}_s$-measurable, so
>    $$
>    \mathbb{E}[M_t|\mathcal{F}_s]=\mathbb{E}[N_t-N_s|\mathcal{F}_s]+N_s-\lambda t=\lambda(t-s)+N_s-\lambda t=M_s.
>    $$
> 2. Since $N_t-N_s\sim\operatorname{Poisson}(\lambda(t-s))$, $\operatorname{Var}(N_t-N_s|\mathcal{F}_s)=\lambda(t-s)$. Using $M_t^2-M_s^2=2M_s(M_t-M_s)+(M_t-M_s)^2$ and $\mathbb{E}[M_t-M_s|\mathcal{F}_s]=0$,
>    $$
>    \mathbb{E}[M_t^2-M_s^2|\mathcal{F}_s]=0+\operatorname{Var}(N_t-N_s|\mathcal{F}_s)=\lambda(t-s).
>    $$
>    Hence $\mathbb{E}[(N_t-\lambda t)^2-\lambda t|\mathcal{F}_s]=(N_s-\lambda s)^2-\lambda s$. $\square$

^thm-compensated

> [!thm]
> Let $N$ be an $\mathcal{F}_t$-Poisson process. Then its natural filtration $\mathcal{F}^N_t:=\sigma\{N_s;\ s\le t\}$ is right-continuous.
>
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

> [!thm]
> Let $N^1,N^2$ be two independent Poisson processes. Then
> $$
> \mathbb{E}\Big[\sum_{s>0}(\Delta N^1_s)(\Delta N^2_s)\Big]=0,
> $$
> where $\Delta N^i_s:=N^i_s-N^i_{s-}$, $i=1,2$. That is, two independent Poisson processes have no common jumps, $a.s.$.
>
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

^thm-no-common-jumps

## Multidimensional Poisson Process

> [!def] Multidimensional Poisson process
> An $\mathcal{F}_t$-adapted process $N=(N^1,N^2,\cdots,N^d)$ is called a **$d$-dimensional $\mathcal{F}_t$-Poisson process** if each $N^i$ is an independent Poisson process, $N^i_0=0$, and there exist constants $c_i$ (i.e. intensities $\lambda_i$) such that for all $0\le s<t<\infty$,
> $$
> \mathbb{P}\{N^i_t-N^i_s=k_i,\ i=1,\cdots,d\}=\prod_{i=1}^{d}\frac{[\lambda_i(t-s)]^{k_i}}{k_i!}e^{-\lambda_i(t-s)}.
> $$

^def-multidim

> [!thm]
> $N=(N^1,N^2,\cdots,N^d)$ is a $d$-dimensional $\mathcal{F}_t$-Poisson process **if and only if**
> 1. each $N^i$ is an $\mathcal{F}_t$-Poisson process;
> 2. for all $0\le s<t<\infty$, $N_t-N_s$ is independent of $\mathcal{F}_s$, and its distribution depends only on $t-s$;
> 3. any two components $N^i,N^j$ ($i\neq j$) have no common jumps, $a.s.$.
>
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

^thm-multidim-char

# Poisson Random Measure

## The Random Measure Associated with a Counting Process

> [!def]
> Given a Poisson process $N=(N_t)_{t\ge0}$ with jumping times $\{T_i\}_{i\ge1}$, define the random measure $M$ on $[0,\infty)$:
> $$
> M(\omega,A)=\#\{i\ge1:\ T_i(\omega)\in A\},\qquad A\subset[0,\infty).
> $$
> For each $\omega$, $M(\omega,\cdot)$ is a $\sigma$-finite measure, and $M(A)<\infty,\ a.s.$ for every bounded $A$. Moreover $N$ has intensity $\lambda$ **if and only if**
> $$
> \mathbb{E}[M(A)]=\lambda|A|,
> $$
> where $|\cdot|$ denotes Lebesgue measure.

^def-random-measure

> [!def] Compensated random measure
> Let $M$ be the random measure of a Poisson process $N$. Then $M$ and $N$ are related by
> $$
> N_t(\omega)=M(\omega,[0,t])=\int_{[0,t]}M(\omega,ds).
> $$
> The random measure $M$ has the following properties:
> 1. For intervals $[t_k,t'_k]$, $M([t_k,t'_k])$ has a Poisson distribution with parameter $\lambda(t'_k-t_k)$ — it is exactly the increment of $N$ over $[t_k,t'_k]$;
> 2. If $j\neq k$, $M([t_j,t'_j])$ and $M([t_k,t'_k])$ are independent;
> 3. For a bounded set $A$, $M(A)\sim\operatorname{Poisson}(\lambda|A|)$ with $|A|=\int_A dt$.
>
> The **compensated random measure** is
> $$
> \widetilde{M}(\omega,A):=M(\omega,A)-\lambda|A|,
> $$
> with $\mathbb{E}[\widetilde{M}(A)]=0$ and $\operatorname{Var}[\widetilde{M}(A)]=\lambda|A|$. $\widetilde{M}$ is a $\sigma$-finite signed measure.

^def-compensated-measure

> [!def] Poisson random measure
> Let $(X,\mathcal{B}_X)$ be a measurable space. A map $M:\Omega\times\mathcal{B}_X\to\mathbb{N}_0\cup\{\infty\}$ is a **random measure** if $M_\omega(B)\in\mathbb{N}_0\cup\{\infty\}$ for all $B\in\mathcal{B}_X$, and $\omega\mapsto M_\omega(B)$ is $\mathcal{F}/\mathcal{B}_{\mathbb{N}_0\cup\{\infty\}}$-measurable. $M$ is called a **Poisson random measure** if:
> 1. for every $B\in\mathcal{B}_X$, $M(B)$ has a Poisson distribution:
>    $$
>    \mathbb{P}(M(B)=k)=\frac{[\mu(B)]^k}{k!}e^{-\mu(B)},\qquad k=0,1,\cdots,
>    $$
>    where $\mu(B):=\mathbb{E}[M(B)]<\infty$ (in particular $P(M(B)=\infty)=1$ forces $\mu(B)=\infty$);
> 2. for disjoint sets $B_1,\cdots,B_n\in\mathcal{B}_X$, the random variables $M(B_1),\cdots,M(B_n)$ are independent.
>
> The deterministic measure $\mu$ is called the **intensity measure** (or compensator) of $M$.

^def-poisson-random-measure

> [!warning]
> If $X\subset\mathbb{R}^d$ and $M$ is a *Radon* random measure (i.e. $M(B)<\infty$ for all bounded $B\in\mathcal{B}_X$), then the definition above is automatically satisfied.

> [!thm] Existence of Poisson random measures
> Let $(X,\mathcal{B}_X)$ be a $\sigma$-finite measurable space and $\mu$ a $\sigma$-finite measure on it. Then there exists a Poisson random measure $M$ with intensity measure $\mu$, i.e. such that $M(B)\sim\operatorname{Poisson}(\mu(B))$ for $\mu(B)<\infty$, and $M(B_1),\cdots,M(B_n)$ are independent for disjoint sets.
>
> *Proof.* See N. Ikeda, S. Watanabe [17]. $\square$

^thm-existence-prm

> [!def] Representation
> Every Poisson random measure admits the representation
> $$
> M(\omega,A)=\sum_{n\ge1}\mathbf{1}_A(X_n(\omega)),\qquad A\in\mathcal{B}_X,
> $$
> for a sequence of random variables $\{X_n\}_{n\ge1}$. The **compensated** Poisson random measure is $\widetilde{M}(B):=M(B)-\mu(B)$.
>
> In particular, if $M$ is a Poisson random measure on $E=[0,T]\times\mathbb{R}^d\setminus\{0\}$ with intensity measure $\mu$ and compensator
> $$
> \widetilde{M}([0,t]\times A)=M([0,t]\times A)-\mu([0,t]\times A),\qquad t\in[0,T],\ A\subset\mathbb{R}^d,
> $$
> then, as before, $M$ admits the representation
> $$
> M(\omega,[0,t],A):=\sum_{\{n:\ T_n(\omega)\in[0,t]\}}\mathbf{1}_A(Y_n(\omega)),
> $$
> where $(T_n(\omega),Y_n(\omega))\in[0,T]\times\mathbb{R}^d$ is a sequence of random points.

^def-repr-prm

> [!def] Adaptedness
> A Poisson random measure $M$ on $E=[0,T]\times\mathbb{R}^d\setminus\{0\}$ is called $\mathcal{F}_t$-**adapted** if
> 1. $(T_n)_{n\ge1}$ are stopping times;
> 2. $Y_n$ is $\mathcal{F}_{T_n}$-measurable, $n\ge1$.

^def-adapted-prm

> [!thm] Integration against the compensated measure
> Let $M$ be an $\mathcal{F}_t$-adapted Poisson random measure on $E=[0,T]\times\mathbb{R}^d\setminus\{0\}$ with intensity measure $\mu$, and let $\widetilde{M}=M-\mu$ be its compensator. Let $f:E\to\mathbb{R}$ be measurable with
> $$
> \mu(|f|):=\int_0^T\int_{\mathbb{R}^d\setminus\{0\}}|f(s,y)|\,\mu(ds\,dy)<\infty.
> $$
> Then
> $$
> X_t:=\int_0^t\int_{\mathbb{R}^d\setminus\{0\}}f(s,y)\,\widetilde{M}(ds\,dy)
> $$
> is an $\mathcal{F}_t$-martingale. Moreover,
> $$
> \int_0^t\int_{\mathbb{R}^d\setminus\{0\}}f(s,y)\,\widetilde{M}(ds\,dy)
> =\sum_{\{n:\ T_n(\omega)\in[0,t]\}}f(T_n(\omega),Y_n(\omega))
> -\int_0^t\int_{\mathbb{R}^d\setminus\{0\}}f(s,y)\,\mu(ds\,dy).
> $$
>
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

^thm-martingale-integral

> [!warning]
> The theorem above is the key observation of the whole theory: an integral against the compensated Poisson random measure equals "sum of the jump sizes at the jumps, minus the compensator". This is what turns the (uncompensated) sum into a martingale.

# Poisson Point Process

> [!def] Point process
> Let $(X,\mathcal{B}_X)$ be a measurable space. An $X$-valued **point process** $p$ is a map $p:D_p\subset(0,\infty)\to X$, where $D_p$ is an at most countable subset of $(0,\infty)$. $p$ is represented as the sequence
> $$
> p:\begin{pmatrix}t_1,&t_2,&\cdots,&t_n,&\cdots\\ u_1,&u_2,&\cdots,&u_n,&\cdots\end{pmatrix},\qquad 0<t_i<\infty,\ u_i\in X,
> $$
> i.e. $p(t)=u_i$ for $t=t_i\in D_p$. The counting measure of $p$ is
> $$
> N_p(t,U):=N_p((0,t]\times U):=\#\{s\in D_p:\ s\le t,\ p(s)\in U\}=\sum_{s\in D_p,\ s\le t}\mathbf{1}_U(p(s)),
> $$
> for $0<t<\infty$, $U\in\mathcal{B}_X$. $\Pi_X$ denotes the set of point processes, and $\mathcal{B}(\Pi_X)$ the smallest $\sigma$-algebra making $p\mapsto N_p(t,U)$ measurable for all $t>0,\ U\in\mathcal{B}_X$.

^def-point-process

> [!def]
> On a filtered probability space $(\Omega,\mathcal{F},(\mathcal{F}_t)_{t\ge0},\mathbb{P})$, an $(X,\mathcal{B}_X)$-valued point process $p_t(\omega)$ is called
> 1. **$\mathcal{F}_t$-adapted** if the counting measure $N_p(t,U)$ is $\mathcal{F}_t$-adapted for all $t>0,\ U\in\mathcal{B}_X$;
> 2. **$\sigma$-finite** if there exist $U_n(\in\mathcal{B}_X)\uparrow X$ with $\mathbb{E}[N_p(t,U_n)]<\infty$ for all $t>0,\ n=1,2,\cdots$.

^def-adapted-point-process

> [!def] Shift and stationarity
> For $s>0$, the $s$-**shift** of the point process $p$ is
> $$
> \theta_s p:=\begin{pmatrix}t_{k_1}-s,&\cdots,&t_{k_l}-s,&\cdots\\ u_{k_1},&\cdots,&u_{k_l},&\cdots\end{pmatrix},
> $$
> where $\{t_{k_1},\cdots,t_{k_l},\cdots\}=\{t_i>s:\ t_i\in D_p\}$. The point process $p_t(\cdot)$ is called **stationary** if for every $s>0$ the shifted process $(\theta_s p)_t(\omega)$ has the same distribution as $p_t(\omega)$, i.e. for all $s,n$, $t_1,\cdots,t_n$, $U_1,\cdots,U_n$, $k_1,\cdots,k_n$,
> $$
> \mathbb{P}(N_p(t_1,U_1)=k_1,\cdots,N_p(t_n,U_n)=k_n)
> =\mathbb{P}(N_{\theta_s p}(t_1,U_1)=k_1,\cdots,N_{\theta_s p}(t_n,U_n)=k_n).
> $$

^def-stationary

> [!def] Poisson point process
> A point process $p_t(\cdot)$ is a **Poisson point process** if its counting measure $N_p$ is a Poisson random measure on $((0,\infty)\times X,\mathcal{B}((0,\infty)\times X))$. It is an ($\mathcal{F}_t$-adapted) Poisson point process if for every $t>s$,
> $$
> \{N_p((s,t]\times U):\ U\in\mathcal{B}_X\}\ \text{is independent of}\ \mathcal{F}_s.
> $$

^def-poisson-point-process

> [!thm] Characterization of stationarity
> A Poisson point process $p_t(\cdot)$ is stationary **if and only if** its intensity measure $\mu$ has the product form
> $$
> \mu((s,t]\times U)=(t-s)\nu(U),\qquad \forall U\in\mathcal{B}_X,
> $$
> where $\nu(\cdot)$ is a $\sigma$-finite measure on $(X,\mathcal{B}_X)$, called the **characteristic (intensity) measure** of $p_t(\cdot)$.
>
> *Proof.* See N. Ikeda, S. Watanabe [17]. $\square$

^thm-stationarity

> [!warning]
> If $\nu(X)<\infty$, then the counting process $N_p((0,t]\times X)$ of a stationary Poisson point process is an ordinary Poisson process with intensity $\nu(X)$.

> [!thm] Construction
> Let $\nu$ be a $\sigma$-finite measure on $(X,\mathcal{B}_X)$. Then $p$ is a stationary Poisson point process with characteristic measure $\nu$ **if and only if** for all $0\le s\le t$ and pairwise disjoint $U_1,\cdots,U_m\in\mathcal{B}_X$, $\lambda_i>0$,
> $$
> \mathbb{E}\Big[\exp\Big(\sum_{i=1}^m\lambda_i N_p((s,t]\times U_i)\Big)\ \Big|\ \sigma[N_p((0,s']\times U);\ s'\le s,\ U\in\mathcal{B}_X]\Big]
> =\exp\Big[-(t-s)\sum_{i=1}^m(e^{-\lambda_i}-1)\nu(U_i)\Big],\quad a.s.
> $$

^thm-construction

> [!thm] Existence
> For every $\sigma$-finite measure $\nu$ on $(X,\mathcal{B}_X)$, there exists a stationary Poisson point process $p$ with characteristic measure $\nu$.
>
> *Proof.* See N. Ikeda, S. Watanabe [17]. $\square$

^thm-existence-ppp

# Stochastic Integration w.r.t. Poisson Processes

## Integrals w.r.t. Semimartingales: the UCP framework

> [!def] Simple processes
> A process $\varphi=(\varphi_t)_{t\in[0,T]}$ is called a **simple (step) process** if
> $$
> \varphi_t=\varphi_0\mathbf{1}_{\{0\}}(t)+\sum_{i=0}^{n}\varphi_i\mathbf{1}_{(T_i,T_{i+1}]}(t),
> $$
> where $0=T_0<T_1<\cdots<T_n<T_{n+1}=T<\infty$ are stopping times, and the random variables $\varphi_i\in\mathcal{F}_{T_i}$ are bounded, $i=1,\cdots,n$. The space of simple processes on $[0,T]$ is denoted by $S([0,T])$.

^def-simple

> [!def] Stochastic integral of a simple process
> Let $S=(S_t)_{s\in[0,T]}$ be an RCLL adapted process. The stochastic integral of $\varphi\in S([0,T])$ w.r.t. $S$ is defined pathwise as
> $$
> \int_0^t\varphi_u\,dS_u:=\varphi_0S_0+\sum_{i=0}^{j-1}\varphi_i(S_{T_{i+1}}-S_{T_i})+\varphi_j(S_t-S_{T_j})
> =\varphi_0S_0+\sum_{i=0}^{n}\varphi_i(S_{T_{i+1}\wedge t}-S_{T_i\wedge t}),
> $$
> for $T_j<t<T_{j+1}$, $j=1,\cdots,n$. We call $\int_0^t\varphi\,dS$ the integral of $\varphi$ w.r.t. $S$.

^def-integral

> [!thm] UCP property
> An RCLL adapted process $S$ is called integrable (a semimartingale) if the following stability property holds: for every sequence $\varphi^n,\varphi\in S([0,T])$ with
> $$
> \sup_{(t,\omega)\in[0,T]\times\Omega}|\varphi^n_t(\omega)-\varphi_t(\omega)|\to0,
> $$
> we have, as $n\to\infty$,
> $$
> \sup_{t\in[0,T]}\Big|\int_0^t\varphi^n\,dS-\int_0^t\varphi\,dS\Big|\to0
> $$
> (uniform convergence in probability, abbreviated UCP).

^thm-ucp

> [!thm]
> 1. Every process of locally bounded variation is integrable;
> 2. every semimartingale is integrable;
> 3. every martingale is integrable;
> 4. every process is integrable w.r.t. a process of locally bounded variation.

^thm-integrable-classes

> [!warning]
> By virtue of the UCP property ([[#^thm-ucp|Theorem]]), the Poisson process, the Poisson point process (and the Poisson random measure) are integrable processes.

> [!thm]
> Let $S$ be a semimartingale and $\varphi\in L([0,T])$ (the space of LCRL adapted processes). Let $\pi^n:=(0=T^n_0<T^n_1<\cdots<T^n_n<T^n_{n+1}=T)$ be partitions of $[0,T]$ with mesh $|\pi^n|:=\sup_k|T^n_k-T^n_{k-1}|\to0$, and set $\varphi^n:=\varphi_0\mathbf{1}_{\{0\}}+\sum_k\varphi_{T^n_k}\mathbf{1}_{(T^n_k,T^n_{k+1}]}$. Then
> $$
> \int_0^t\varphi_{u-}\,dS_u:=\lim_{n\to\infty}\int_0^t\varphi^n\,dS_u
> $$
> exists in the UCP sense, uniformly in $t\in[0,T]$.

^thm-lcrl-integral

> [!thm]
> 1. If $X$ is a semimartingale and $\sigma=(\sigma_t)_{t\in[0,T]}$ is an LCRL process, then $S_t=\int_0^t\sigma\,dX$ is a semimartingale;
> 2. if $\varphi$ is an LCRL process, then $\int_0^t\varphi\,dS=\int_0^t\varphi\sigma\,dX$;
> 3. if $X$ is a continuous semimartingale and $\varphi$ is bounded, then $M_t:=\int_0^t\varphi\,dX$ is a continuous martingale.

^thm-integral-props

## Integrals w.r.t. a Poisson Random Measure

> [!def] Integrals of simple integrands
> Let $M$ be a Poisson random measure on $[0,T]\times\mathbb{R}^d\setminus\{0\}$ with intensity measure $\mu$ and compensator $\widetilde{M}([0,t]\times A)=M([0,t]\times A)-\mu([0,t]\times A)$. For $A\subseteq\mathbb{R}^d$, $M_t(A):=M([0,t]\times A)$ is a counting process, $\widetilde{M}_t(A)=M_t(A)-\mu([0,t]\times A)$ is a martingale whenever $\mu([0,t]\times A)<\infty$, and $M_t(A),M_t(B)$ are independent for $A\cap B=\emptyset$.
>
> Let $\varphi:\Omega\times[0,T]\times\mathbb{R}^d\to\mathbb{R}$ be a simple integrand of the form
> $$
> \varphi(t,y)=\sum_{i=1}^n\sum_{j=1}^m\varphi_{ij}\mathbf{1}_{(T_i,T_{i+1}]}(t)\mathbf{1}_{A_j}(y),
> $$
> with $0=T_1\le T_2\le\cdots\le T_n\le T_{n+1}=T$ stopping times, $\{\varphi_{ij}\}_{j=1,\cdots,m}$ bounded $\mathcal{F}_{T_i}$-measurable, and $(A_j)$ disjoint bounded sets with $\mu([0,T]\times A_j)<\infty$. We define
> $$
> \int_0^T\int_{\mathbb{R}^d\setminus\{0\}}\varphi(t,y)\,M(dt\,dy)
> :=\sum_{i=1}^n\sum_{j=1}^m\varphi_{ij}M((T_i,T_{i+1}]\times A_j)
> =\sum_{i=1}^n\sum_{j=1}^m\varphi_{ij}\big[M_{T_{i+1}}(A_j)-M_{T_i}(A_j)\big].
> $$
> For $t\in[0,T]$, $t\mapsto\int_0^t\int\varphi(s,y)\,M(ds\,dy)$ is an RCLL adapted process, denoted $I^\varphi_t(M)$. Similarly, against the compensator,
> $$
> \int_0^T\int_{\mathbb{R}^d\setminus\{0\}}\varphi(t,y)\,\widetilde{M}(dt\,dy)
> :=\sum_{i=1}^n\sum_{j=1}^m\varphi_{ij}\widetilde{M}((T_i,T_{i+1}]\times A_j).
> $$

^def-integral-prm

> [!thm] Itô isometry
> The integral $I^\varphi_t(\widetilde{M})$ against the compensated Poisson random measure is a square-integrable martingale, and the **Itô isometry** holds:
> $$
> \mathbb{E}\big[|I^\varphi_t(\widetilde{M})|^2\big]
> =\mathbb{E}\Big[\int_0^t\int_{\mathbb{R}^d\setminus\{0\}}|\varphi(s,y)|^2\,\mu(ds\,dy)\Big].
> $$
>
> *Proof.* We compute, using the martingale property of $\widetilde{M}$ and the independence of the increments,
> $$
> \begin{aligned}
> \mathbb{E}\big[|I^\varphi_t(\widetilde{M})|^2\big]
> &=\mathbb{E}\Big[\Big|\sum_{i=1}^n\sum_{j=1}^m\varphi_{ij}\big[\widetilde{M}_{T_{i+1}\wedge t}(A_j)-\widetilde{M}_{T_i\wedge t}(A_j)\big]\Big|^2\Big]\\
> &=\mathbb{E}\Big[\sum_{i=1}^n\sum_{j=1}^m|\varphi_{ij}|^2\mathbb{E}\big[\big[\widetilde{M}_{T_{i+1}\wedge t}(A_j)-\widetilde{M}_{T_i\wedge t}(A_j)\big]^2\ \big|\ \mathcal{F}_{T_i}\big]\Big]\\
> &=\mathbb{E}\Big[\sum_{i=1}^n\sum_{j=1}^m|\varphi_{ij}|^2\,\mu\big((T_i,T_{i+1}]\times A_j\big)\Big]
> =\mathbb{E}\Big[\int_0^t\int_{\mathbb{R}^d\setminus\{0\}}|\varphi(s,y)|^2\,\mu(ds\,dy)\Big],
> \end{aligned}
> $$
> where we used $\operatorname{Var}(\widetilde{M}((T_i,T_{i+1}]\times A_j)|\mathcal{F}_{T_i})=\mu((T_i,T_{i+1}]\times A_j)$ (cf. [[#^thm-compensated|Theorem]]). $\square$

^thm-ito-isometry

> [!thm] Extension by completion
> Let $\varphi=(\varphi_t)_{t\in[0,T]}$ be an $\mathcal{F}_t$-predictable process with
> $$
> \mathbb{E}\Big[\int_0^T\int_{\mathbb{R}^d\setminus\{0\}}|\varphi(t,y)|^2\,\mu(dt\,dy)\Big]<\infty.
> $$
> Then there exists a square-integrable martingale
> $$
> I^\varphi_t(\widetilde{M}):=\int_0^t\int_{\mathbb{R}^d\setminus\{0\}}\varphi(s,y)\,\widetilde{M}(ds\,dy),
> $$
> and the Itô isometry [[#^thm-ito-isometry|above]] remains valid. The extension is obtained by approximating $\varphi$ by simple integrands in $L^2(\mu)$.
>
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

^thm-extension

# Quadratic Variation and the Generalized Itô Formula

## Quadratic Variation and Covariation

> [!def] Quadratic variation
> For a semimartingale $X$ and a partition $\pi=\{0=t_0<t_1<\cdots<t_{n+1}=T\}$ of $[0,T]$, write
> $$
> V_X(\pi):=\sum_{t_i\in\pi}(X_{t_{i+1}}-X_{t_i})^2.
> $$
> Using $(X_{t_{i+1}}-X_{t_i})^2=X_{t_{i+1}}^2-X_{t_i}^2-2X_{t_i}(X_{t_{i+1}}-X_{t_i})$, we obtain
> $$
> V_X(\pi)=X_T^2-2\sum_{t_i\in\pi}X_{t_i}(X_{t_{i+1}}-X_{t_i}).
> $$
> By the UCP property [[#^thm-lcrl-integral|Theorem]], $V_X(\pi)$ converges in probability to the **quadratic variation**
> $$
> [X,X]_T:=|X_T|^2-2\int_0^TX_{u-}\,dX_u.
> $$
> The process $([X,X]_t)_{t\in[0,T]}$ is an increasing RCLL adapted process.

^def-quadratic-variation

> [!thm] Properties of the quadratic variation
> Let $X$ be a semimartingale. Then
> 1. $([X,X]_t)_{t\in[0,T]}$ is an increasing process;
> 2. $\Delta[X,X]_t=|\Delta X_t|^2$; in particular $[X,X]$ is continuous **iff** $X$ is continuous, and
>    $$
>    [X,X]_T=[X,X]^c_T+\sum_{0<s\le t}(\Delta X_s)^2;
>    $$
> 3. if $X$ is continuous and of locally bounded variation, then $[X,X]\equiv0$;
> 4. if $X$ is a semimartingale and $[X,X]\equiv0$, then $X$ is of bounded variation.
>
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

^thm-qv-props

> [!warning]
> Items 3. and 4. of [[#^thm-qv-props|Theorem]] say: a continuous process has zero quadratic variation iff it is of bounded variation — the analogue of the fact that Brownian motion has infinite variation but finite quadratic variation.

> [!thm] Quadratic covariation
> For semimartingales $X,Y$ and a partition $\pi$ of $[0,T]$,
> $$
> V_{X,Y}(\pi):=\sum_{t_i\in\pi}(X_{t_{i+1}}-X_{t_i})(Y_{t_{i+1}}-Y_{t_i}).
> $$
> Using $(X_{t_{i+1}}-X_{t_i})(Y_{t_{i+1}}-Y_{t_i})=X_{t_{i+1}}Y_{t_{i+1}}-X_{t_i}Y_{t_i}-Y_{t_i}(X_{t_{i+1}}-X_{t_i})-X_{t_i}(Y_{t_{i+1}}-Y_{t_i})$, and passing to the UCP limit,
> $$
> [X,Y]_T:=X_TY_T-X_0Y_0-\int_0^TX_{u-}\,dY_u-\int_0^TY_{u-}\,dX_u.
> $$
> $[X,Y]_t$ is an RCLL process of bounded variation, and the polarization identity holds:
> $$
> [X,Y]=\frac{1}{2}\big([X+Y,X+Y]-[X-Y,X-Y]\big)=\frac{1}{2}\big([X+Y,X+Y]-[X,X]-[Y,Y]\big).
> $$
> If $\varphi,\psi$ are integrable processes, then
> $$
> \Big[\int\varphi\,dX,\int\psi\,dY\Big]_t=\int_0^t\varphi\psi\,d[X,Y].
> $$

^thm-covariation

> [!thm] Integration by parts
> For semimartingales $X,Y$,
> $$
> X_tY_t=X_0Y_0+\int_0^tX_{s-}\,dY_s+\int_0^tY_{s-}\,dX_s+[X,Y]_t.
> $$

^thm-by-parts

> [!example] Quadratic variations of common processes
> 1. If $W$ is a Brownian motion, then $[W,W]_t=t$;
> 2. if $N$ is a Poisson process, then $[N,N]_t=N_t$;
> 3. for a pure jump process $X$, $[X,X]_t=\sum_{0\le s\le t}|\Delta X_s|^2$;
> 4. if $X_t=\int_0^t\sigma_s\,dW_s$ with $\sigma$ LCRL, then $[X,X]_t=\int_0^t\sigma_s^2\,ds$;
> 5. if $M$ is a Poisson random measure with intensity $\mu$ and $I^\varphi_t(M)=\int_0^t\int\varphi(s,y)\,M(ds\,dy)$, then
>    $$
>    \big[I^\varphi(M),I^\varphi(M)\big]_t=\int_0^t\int_{\mathbb{R}^d\setminus\{0\}}\varphi(s,y)^2\,M(ds\,dy).
>    $$

^example-qv

## The Generalized Itô Formula

> [!thm] Generalized Itô formula for semimartingales
> Let $X_t=(X^1_t,\cdots,X^d_t)$ be a $d$-dimensional semimartingale and $f\in C^{1,2}([0,T]\times\mathbb{R}^d\to\mathbb{R})$ with $f(\cdot,X)$ a semimartingale. Then
> $$
> \begin{aligned}
> f(t,X_t)-f(0,X_0)
> &=\int_0^t\frac{\partial f}{\partial s}(s,X_s)\,ds
> +\sum_{i=1}^{d}\int_0^t\frac{\partial f}{\partial x_i}(s,X_{s-})\,dX^i_s\\
> &\quad+\frac{1}{2}\sum_{i,j=1}^{d}\int_0^t\frac{\partial^2f}{\partial x_i\partial x_j}(s,X_{s-})\,d[X^i,X^j]_s\\
> &\quad+\sum_{\substack{0<s\le t\\ \Delta X_s\neq0}}\Big[f(s,X_s)-f(s,X_{s-})-\sum_{i=1}^{d}\frac{\partial f}{\partial x_i}(s,X_{s-})\Delta X^i_s
> -\frac{1}{2}\sum_{i,j=1}^{d}\frac{\partial^2f}{\partial x_i\partial x_j}(s,X_{s-})\Delta X^i_s\Delta X^j_s\Big].
> \end{aligned}
> $$
> *Proof.* See R. Cont, P. Tankov [19]. $\square$

^thm-generalized-ito

> [!warning]
> Splitting $[X^i,X^j]=[X^i,X^j]^c+\sum_{u\le t}\Delta X^i_u\Delta X^j_u$ into its continuous part and jump part, the formula can be rewritten in the equivalent form
> $$
> \begin{aligned}
> f(t,X_t)-f(0,X_0)
> &=\int_0^t\frac{\partial f}{\partial s}\,ds
> +\sum_{i=1}^{d}\int_0^t\frac{\partial f}{\partial x_i}\,dX^i_s
> +\frac{1}{2}\sum_{i,j=1}^{d}\int_0^t\frac{\partial^2f}{\partial x_i\partial x_j}\,d[X^i,X^j]^c_s\\
> &\quad+\sum_{\substack{0<s\le t\\ \Delta X_s\neq0}}\Big[f(s,X_s)-f(s,X_{s-})-\sum_{i=1}^{d}\frac{\partial f}{\partial x_i}(s,X_{s-})\Delta X^i_s\Big].
> \end{aligned}
> $$
> Note that the continuous part is governed by $[X^i,X^j]^c$, while the jumps enter through the (finite) jump sum — the "Itô correction" $\frac12\sum\partial_{ij}^2f\,\Delta X^i\Delta X^j$ is exactly absorbed when $f$ is applied to the jump sizes.

## Compensators of Point Processes (QL processes)

> [!def] QL processes and their compensator
> A point process $p$ is called **QL** (quasi-left-continuous, "quasi-lacunaire") if $p$ is $\mathcal{F}_t$-adapted and $\sigma$-finite, and there exists a random measure $\widehat{N}_p=(\widehat{N}_p(t,U))$ such that:
> 1. for every $U\in\Gamma_p$, $t\mapsto\widehat{N}_p(t,U)$ is an $\mathcal{F}_t$-adapted process of bounded variation;
> 2. for every $t>0$, $a.a.\ \omega$, $U\mapsto\widehat{N}_p(t,U)$ is a $\sigma$-finite measure on $(X,\mathcal{B}_X)$;
> 3. for every $U\in\Gamma_p$,
>    $$
>    \widetilde{N}_p(t,U):=N_p(t,U)-\widehat{N}_p(t,U)
>    $$
>    is an $\mathcal{F}_t$-martingale,
> where $\Gamma_p:=\{U\in\mathcal{B}_X:\ \mathbb{E}[N_p(t,U)]<\infty,\ \forall t>0\}$. $\{\widehat{N}_p(t,U)\}$ is called the **compensator** of the point process $p$.

^def-ql

> [!thm]
> An $\mathcal{F}_t$-Poisson point process $p$ is QL **if and only if** $t\mapsto\mathbb{E}[N_p(t,U)]$ is continuous for every $U\in\Gamma_p$, in which case the compensator is
> $$
> \widehat{N}_p(t,U)=\mathbb{E}[N_p(t,U)].
> $$
> In particular, if $p$ is stationary, then $\widehat{N}_p(t,U)=t\,\nu(U)$, where $\nu$ is the characteristic measure of $p$.
>
> *Proof.* See N. Ikeda, S. Watanabe [17]. $\square$

^thm-compensator

> [!thm] Characterization of Brownian motion and Poisson point processes
> Let $X(t)=(X^1(t),\cdots,X^d(t))$ be a $d$-dimensional $\mathcal{F}_t$-semimartingale, and let $p_1,\cdots,p_n$ be QL Poisson point processes taking values in $X_1,\cdots,X_n$. Suppose:
> 1. $M^i(t):=X^i(t)-X^i(0)$ is a continuous martingale;
> 2. $[M^i,M^j]_t=\delta_{ij}t$ for $i,j=1,\cdots,d$;
> 3. the compensator $\widehat{N}_{p_i}$ of $p_i$ is a deterministic $\sigma$-finite measure on $[0,\infty)\times X_i$;
> 4. the jump sets $D_{p_i}\subset[0,\infty)$ are pairwise disjoint, $a.s.$.
>
> Then $X(t)$ is a $d$-dimensional Brownian motion, the $p_i$'s are $\mathcal{F}_t$-Poisson point processes, and they are mutually independent.
>
> *Proof.* See N. Ikeda, S. Watanabe [17]. $\square$

^thm-bm-pp-char

## The Itô Formula for Jump-Diffusions

> [!def] Jump-diffusion (Itô process with jumps)
> Let $W_t=(W^1_t,\cdots,W^d_t)$ be a $d$-dimensional Brownian motion and $p$ an $(X,\mathcal{B}_X)$-valued stationary $\mathcal{F}_t$-Poisson point process with characteristic measure $\nu$. Write $\widetilde{N}_p(ds\,dz)=N_p(ds\,dz)-\nu(dz)ds$. The process
> $$
> X_t=X_0+\int_0^t b(s)\,ds+\int_0^t\sigma(s)\,dW(s)+\int_0^t\int_X c(s,z)\,\widetilde{N}_p(ds\,dz)
> $$
> is an **Itô process with jumps**, where $X_0$ is $\mathcal{F}_0$-measurable, $b(\cdot):[0,\infty)\times\Omega\to\mathbb{R}^d$ is $\mathcal{F}_t$-adapted, $\sigma(\cdot)=(\sigma^1(\cdot),\cdots,\sigma^d(\cdot))^\top\in L^2_F(\mathbb{R}^{d\times d})$, and $c(\cdot,\cdot)\in\mathcal{F}^2_p(\mathbb{R}^d)$.

^def-jump-diffusion

> [!thm] Itô formula for jump-diffusions
> Let $X$ be an Itô process with jumps as above and $f\in C^{1,2}([0,\infty)\times\mathbb{R}^d\to\mathbb{R})$. Then
> $$
> \begin{aligned}
> f(t,X_t)-f(0,X_0)
> &=\int_0^t\Big[\frac{\partial f}{\partial s}(s,X_s)+\sum_{i=1}^{d}\frac{\partial f}{\partial x_i}(s,X_s)b^i(s)+\frac{1}{2}\sum_{i,j=1}^{d}\frac{\partial^2f}{\partial x_i\partial x_j}(s,X_s)\sigma^i(s)(\sigma^j(s))^\top\Big]ds\\
> &\quad+\sum_{i=1}^{d}\int_0^t\frac{\partial f}{\partial x_i}(s,X_s)\sigma^i(s)\,dW^i_s\\
> &\quad+\int_0^t\int_X\big[f(s,X_{s-}+c(s,z))-f(s,X_{s-})\big]\widetilde{N}_p(ds\,dz)\\
> &\quad+\int_0^t\int_X\Big[f(s,X_s+c(s,z))-f(s,X_s)-\sum_{i=1}^{d}c^i(s,z)\frac{\partial f}{\partial x_i}(s,X_s)\Big]\nu(dz)\,ds.
> \end{aligned}
> $$
> In differential form,
> $$
> \begin{aligned}
> df(t,X_t)
> &=\Big[\frac{\partial f}{\partial t}+\sum_{i=1}^{d}\frac{\partial f}{\partial x_i}b^i+\frac{1}{2}\sum_{i,j=1}^{d}\frac{\partial^2f}{\partial x_i\partial x_j}\sigma^i(\sigma^j)^\top\Big]dt
> +\sum_{i=1}^{d}\frac{\partial f}{\partial x_i}\sigma^i\,dW^i_t\\
> &\quad+\int_X\big[f(t,X_{t-}+c(t,z))-f(t,X_{t-})\big]\widetilde{N}_p(dt\,dz)\\
> &\quad+\int_X\Big[f(t,X_t+c(t,z))-f(t,X_t)-\sum_{i=1}^{d}c^i(t,z)\frac{\partial f}{\partial x_i}(t,X_t)\Big]\nu(dz)\,dt.
> \end{aligned}
> $$
>
> *Proof.* Let $\Gamma_p$ be the jump set of $p$; it is a sequence $0<\sigma_1<\sigma_2<\cdots<\sigma_m<\cdots$ of $\mathcal{F}_t$-stopping times. Decompose
> $$
> f(t,X_t)-f(0,X_0)=\sum_{m}\big[f(\sigma_m\wedge t,X_{\sigma_m\wedge t})-f(\sigma_m\wedge t-,X_{\sigma_m\wedge t-})\big]
> +\sum_{m}\big[f(\sigma_m\wedge t-,X_{\sigma_m\wedge t-})-f(\sigma_{m-1}\wedge t,X_{\sigma_{m-1}\wedge t})\big],
> $$
> with $\sigma_0=0$. On the (random) interval $[\sigma_{m-1}\wedge t,\sigma_m\wedge t)$ the process $X$ has no jumps, so the second sum is computed by the (continuous) Itô formula, while the first sum collects the jumps via the generalized Itô formula [[#^thm-generalized-ito|above]]. Summing and passing to the limit gives the result. $\square$

^thm-ito-jump

> [!example]
> Let $f(t,X_t)=e^{\beta t}|X_t|^2$ with $\beta$ constant. Applying the Itô formula [[#^thm-ito-jump|above]],
> $$
> \begin{aligned}
> e^{\beta t}|X_t|^2
> &=|X_0|^2+\int_0^t e^{\beta s}\big(\beta|X_s|^2+2X_sb_s+\sigma_s^2\big)ds
> +2\int_0^t e^{\beta s}X_s\sigma_s\,dw_s\\
> &\quad+\int_0^t\int_X e^{\beta s}\big(|X_{s-}+c(s,z)|^2-|X_{s-}|^2\big)\widetilde{N}_p(ds\,dz)\\
> &\quad+\int_0^t\int_X\big[e^{\beta s}\big(|X_s+c(s,z)|^2-|X_s|^2\big)-2e^{\beta s}c(s,z)X_s\big]\nu(dz)\,ds\\
> &=|X_0|^2+\int_0^t e^{\beta s}\big(\beta|X_s|^2+2X_sb_s+\sigma_s^2\big)ds
> +2\int_0^t e^{\beta s}X_s\sigma_s\,dw_s\\
> &\quad+\int_0^t\int_X e^{\beta s}\big(2X_{s-}c(s,z)+|c(s,z)|^2\big)\widetilde{N}_p(ds\,dz)\\
> &\quad+\int_0^t\int_X e^{\beta s}|c(s,z)|^2\,\nu(dz)\,ds.
> \end{aligned}
> $$
> This is the natural analogue of the classical Itô formula, with the Brownian part supplemented by the compensated jump part.

## Martingale Representation Theorem

> [!thm] Martingale representation
> Let $m(t)$ be a continuous $\mathcal{F}^{W,p}_t$-martingale, where $\mathcal{F}^{W,p}_t:=\sigma\{W_s,p_s;\ 0\le s\le t\}$. Then there exist $q_i(t)\in L^2_F(\mathbb{R}^d)$, $i=1,\cdots,d$, and $r(t,z)\in\mathcal{F}^2_p(\mathbb{R}^d)$ such that
> $$
> m(t)=m(0)+\sum_{i=1}^{d}\int_0^tq_i(s)\,dW^i_s+\int_0^t\int_X r(s,z)\,\widetilde{N}_p(ds\,dz).
> $$
>
> *Proof.* See N. Ikeda, S. Watanabe [17]; S. Tang, X. Li [21]. $\square$

^thm-martingale-representation

> [!warning]
> The martingale representation theorem shows that the filtration generated by a Brownian motion and a Poisson point process is generated by the Brownian part and the (compensated) jump part: any martingale is a sum of a Brownian stochastic integral and an integral against the compensated Poisson random measure. This is the cornerstone for Malliavin calculus, jump-type BSDEs, and hedging in incomplete markets with jumps.

---
## References

- [16] P. Protter, *Stochastic Integration and Differential Equations*, Springer.
- [17] N. Ikeda, S. Watanabe, *Stochastic Differential Equations and Diffusion Processes*, North-Holland.
- [19] R. Cont, P. Tankov, *Financial Modelling with Jump Processes*, Chapman & Hall.
- [21] S. Tang, X. Li, *Necessary conditions for optimal control of stochastic systems with random jumps*.
