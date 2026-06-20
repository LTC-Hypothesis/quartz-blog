# Introduction
```ad-def
title:$C[0,\infty)$ space 
Let 
$$
C[0,\infty)\triangleq\{\mbox{continuous real-value functions on }[0,\infty) \mbox{ with metric } \rho\}
$$
where 
$$
\rho(\mu_1,\mu_1)=\sum_{n=1}^{\infty}\frac{\max_{1\le t\le n}\left(|\mu_1(t)-\mu_2(t)|\wedge 1\right)}{2^n}
$$
```

```ad-proposition
$\rho$ is a metric on $C[0,\infty)$ and $C[0,\infty)$ is complete and separable under $\rho$. 
```
**Proof**
**Metric**. 
For triangle inequality, 
$$
\begin{align}
\rho(\mu_1,\mu_2)&=\sum_{n=1}^{\infty}\frac{\max_{1\le t\le n}\left(|\mu_1(t)-\mu_2(t)|\wedge 1\right)}{2^n}\\
&\le \sum_{n=1}^{\infty}\frac{\max_{1\le t\le n}\left((|\mu_1(t)-\mu_3(t)|+|\mu_3(t)-\mu_2(t)|)\wedge 1\right)}{2^n}\\
&\le \sum_{n=1}^{\infty}\frac{\max_{1\le t\le n}\left((|\mu_1(t)-\mu_3(t)|\wedge 1+|\mu_3(t)-\mu_2(t)|\wedge 1)\right)}{2^n}\\
&\le\sum_{n=1}^{\infty}\frac{\max_{1\le t\le n}\left(|\mu_1(t)-\mu_3(t)|\wedge 1\right)+\max_{1\le t\le n}\left(|\mu_3(t)-\mu_2(t)|\wedge 1\right)}{2^n}\\
&=\rho(\mu_1,\mu_3)+\rho(\mu_3,\mu_2)
\end{align}
$$
**Complement**
Suppose $\{\mu\}_{k=1}^{\infty}$ are Cauchy sequence
**QED**
```ad-def
title:Induced probability measure
Suppose a r.v. $X$ in probability space $(\Omega,\mathcal{F},\mathbb{P})$ with values in measurable space $(S,\mathcal{B}(S))$ i.e. $X:\Omega\to S$ is $\mathcal{F}/\mathcal{B}(S)$-measurable. Then we induce a probability measure $\mathbb{P}X^{-1}$ i.e. 
$$
\mathbb{P}X^{-1}(B)=\mathbb{P}(X(\omega)\in B),\forall B\in\mathcal{B}(S)
$$
```

```ad-def
title:Law of X
We apply the definition of induced probability measure to a continuous stochastic process $X_t$. Such $X$ is r.v. on $(\Omega,\mathcal{F},\mathbb{P})$ with values in $(C[0,\infty),\mathcal{B}(C[0,\infty)))$, then the induced probability measure $\mathbb{P}X^{-1}$ is called the law of $X$.
```
# Weak convergence 
```ad-def
title:Converge weakly
Let $(S, \rho)$ be a metric space with Borel $\sigma$-field $\mathcal{B}(S)$. Let $\{\mathbb{P}_n\}_{n=1}^{\infty}$ be a sequence of probability measures on $(S, \mathcal{B}(S))$, and let $\mathbb{P}$ be another measure on this space. We say that $\mathbb{P}_n$ converges weakly to $\mathbb{P}$ and write $\mathbb{P}_n\xrightarrow{w} \mathbb{P}$, if and only if
$$
\lim_{n\to\infty}\int_{S}f(s){d}\mathbb{P}_n=\int_{S}f(s){d}\mathbb{P},\forall f \mbox{ is on $S$ and }\mbox{ bounded}
$$
```

```ad-def
title:converge in distribution
Let $\{(\Omega_n, \mathcal{F}_n, \mathbb{P}_n)\}_{n=1}^{\infty}$ be a sequence of probability spaces, and on each of them consider a random variable $X$ with values in the metric space $(S, \rho)$ . Let $(\Omega,\mathcal{F},\mathbb{P})$ be another probability space, on which a random variable $X$ with values in $(S, \rho)$ is given. We say that $X_n\xrightarrow{d}X$ if and only if $\mathbb{P}_nX_n^{-1}\xrightarrow{w}\mathbb{P}X^{-1}\Longleftrightarrow\mathbb{E}_nf(X_n)\to\mathbb{E}f(X)$ for bounded, continuous real-valued function $f$ as $n\to\infty$.
```
# Tightness
```ad-def
title:Relatively compact
Let $(S, \rho)$ be a metric space and let $\mathscr{P}$ be a family of probability measures on $(S,\mathcal{B}(S))$. We say that $\mathscr{P}$ is **relatively compact** if every sequence of elements of $\mathscr{P}$ contains a weakly convergent subsequence.
```

```ad-def
title:Tightness
Let $(S, \rho)$ be a metric space and let $\mathscr{P}$ be a family of probability measures on $(S,\mathcal{B}(S))$. We say that $\mathscr{P}$ is **tightness**, if $\forall\varepsilon>0$, there exists a compact set $K\subseteq S$ s.t. $\mathbb{P}(K)\ge 1-\varepsilon\Longleftrightarrow\mathbb{P}(K^c)\le \varepsilon$.
```

```ad-def
title:Relatively compact/Tightness for stochastic process
If $\{X_\alpha\}_{\alpha\in\Lambda}$ is a family of random variables, each one defined on a probability space $(\Omega_\alpha,\mathcal{F}_\alpha,\mathbb{P}_\alpha)$ and taking values in $S$, we say that this family is relatively compact or tight if the family of induced measures $\{\mathbb{P}_\alpha X^{-1}_\alpha\}$ has the appropriate property.
```

```ad-thm
title:Prohorov
Let $\mathscr{P}$ be a family of probability measures on a complete, separable metric space $S$. This family is relatively compact if and only if it is tight.
```

^07a931

```ad-def
title:Modulus of continuity
For $\mu\in C[0,\infty),T,\delta>0$, the **modulus of continuity** on $[0,T]$:
$$
m^T(\mu,\delta)\triangleq\max_{|s-t|\le\delta,s,t\in [0,T]}|\mu(s)-\mu(t)|
$$
```

```ad-proposition
title:Property of modulus of continuity
$m^T(\mu, \delta)$ is continuous in $\mu \in C[0, \infty)$ under the metric $\rho$, is nondecreasing in $\delta$, and $\lim_{\delta \downarrow 0} m^T(\mu, \delta) = 0$ for each $\mu \in C[0, \infty)$.
```

^afa975

**Proof**
Suppose $\rho(\mu_k,\mu)\to0$ as $k\to\infty$, we consider $|m^T(\mu_k,\delta)-m^T(\mu,\delta)|$. For sufficiently large $k$, $\max_{0\le t\le T}|\mu_k(t)-\mu(t)|\to0$ as $k\to\infty$. For fixed $\delta>0$, 
$$
\begin{align}
|m^T(\mu_k,\delta)-m^T(\mu,\delta)|&\le\max_{|s-t|\le\delta,s,t\in[0,T]}||\mu_k(s)-\mu_k(t)|-|\mu(s)-\mu(t)||\\
&\le 2\max_{t\in[0,T]}|\mu_k(t)-\mu(t)|\to0
\end{align}
$$
Hence, $m^T(\mu,\delta)$ is continuous. 
Suppose $0\le \delta_1<\delta_2$, then $\{|s-t|\le\delta_1\}\subseteq\{|s-t|\le\delta_2\}$, we have 
$$
m^T(\mu,\delta_1)\le m^T(\mu,\delta_2)
$$
Since $\mu$ is continuous on $[0,T]$ and thus is uniformly continuous on $[0,T]$, for $\varepsilon>0$, there exists $\delta_0>0$ s.t. $\delta<\delta_0$, $|s-t|<\delta$, $|\mu(s)-\mu(t)|<\varepsilon$, 
$$
m^T(\mu,\delta)=\max_{|s-t|\le\delta,s,t\in[0,T]}|\mu(s)-\mu(t)|<\varepsilon
$$
**QED**
```ad-thm
title:Arzelà-Ascoli
A set $A \subseteq C[0, \infty)$ has **compact closure** if and only if the following two conditions hold:
1. $$\sup_{\mu\in A}|\mu(0)|<\infty$$
2. $$\lim_{\delta\downarrow0}\sup_{\mu\in A}m^T(\mu,\delta)=0,\forall T>0$$
```

^4d7ac0

**Proof**
$\Longrightarrow$: Suppose $A$ has closure $\bar{A}$ which is compact. Let the nondecreasing open ball, 
$$
G_n=\{\mu\in C[0,\infty):|\mu(0)|<n\}
$$
Since $\bar{A}$ is compact and $\{G_n\}$ become a open cover of $\bar{A}$, there exists open sub-cover that cover $\bar{A}$. Note that $G_n$ are nondecreasing, $\bar{A}$ is contained in some $G_{n_0}$. That is $\sup_{\mu\in A}|\mu(0)|<\infty$. 
For $\varepsilon>0$, let $K_\delta=\{\mu\in C[0,\infty):m^T(\mu,\delta)\ge\varepsilon\}$. By [[#^afa975|Property of modulus of continuity]], $K_\delta$ is closed and $\bigcap_{\delta>0}K_\delta=\emptyset$. Therefore, for $\varepsilon>0$, there exists $\delta(\varepsilon)>0$ s.t. $K_{\delta(\varepsilon)}=\emptyset$ i.e. $m^T(\mu,\delta(\varepsilon))<\varepsilon$. Hence, the two conditions hold. 
$\Longleftarrow$: Suppose the two conditions hold, we W.T.S. $\bar{A}$ is compact. Since $C[0,\infty)$ is metric space, it suffices to show that every sequence $\{\mu_n\}\subseteq A$ [[简明拓扑学#^f28684|has a convergent subsequence]]. The method to prove this claim is "diagonal sequence". Firstly, we prove for each $\mu$ is bounded. Fix $T>0$ and let $\varepsilon=1$, there exists $\delta_1>0$ s.t. $m^T(\mu,\delta_1)<1$. Fix $N\ge 1$ and $t\in(0,T]$ with $(N-1)\delta_1<t\le N\delta_1\wedge T$, then 
$$
|\mu(t)|\le|\mu(0)|+\sum_{k=1}^{N-1}\left|\mu(k\delta_1)-\mu((k-1)\delta_1)\right|+|\mu(t)-\mu((N-1)\delta_1)|\le |\mu(0)|+N
$$
For fixed $r\in\mathbb{Q}_+$, $\{\mu_n(r)\}$ is bounded. Let $\mathbb{Q}_+=\{r_0,r_1,\cdots\}$. For $\mu_n$, choose subsequence $\mu_n^{(0)}$ s.t. $\mu_n^{(0)}(r_0)\to\mu(r_0)$. For $\mu_n^{(0)}$, choose further subsequence $\mu_n^{(1)}$ s.t. $\mu_n^{(1)}(r_1)\to\mu(r_1)$. We have 
$$
\begin{matrix}
\mu_1^{(0)} &\mu_2^{(0)} &\cdots &\mu_n^{(0)}&\cdots&\to&\mu(r_0)\\
\mu_1^{(1)} &\mu_2^{(1)} &\cdots &\mu_n^{(1)}&\cdots&\to&\mu(r_1)\\
\vdots &\vdots & &\vdots& && \vdots\\
\mu_1^{(s)} &\mu_2^{(s)} &\cdots &\mu_n^{(s)}&\cdots&\to&\mu(r_s)\\
\vdots &\vdots & &\vdots& && \vdots
\end{matrix}
$$
Take $\tilde{\mu}_n\triangleq\mu^{(s)}_n$, for $r\in\mathbb{Q}_+$, then $\tilde{\mu}_n(r)\to\mu(r)$ as $n\to\infty$.
By the second condition, for $\varepsilon>0$, $\exists\delta(\varepsilon)>0$ s.t. $|\tilde{\mu}(s)-\tilde{\mu}(t)|<\varepsilon$ for $0\le s,t\le T$ and $|s-t|<\delta(\varepsilon)$. When $s,t\in\mathbb{Q}_+$, the same inequality holds for $\mu$. . It follows that $\mu$ is uniformly continuous on $[0,T]\cap\mathbb{Q}_+$ and so has an extension to a continuous function, also called $\mu$ i.e. $|\mu(s)-\mu(t)|<\varepsilon$ when $0\le s,t\le T$ and $|s-t|<\delta(\varepsilon)$. For $t\in[0,T]$, $\exists r\in\mathbb{Q}_+$ s.t. $|t-r|<\delta(\varepsilon)$. For sufficiently large $N$, when $n>N$, we have $|\tilde{\mu}_n(r)-\mu(r)|<\varepsilon$ and 
$$
|\tilde{\mu}_n(t)-\mu(t)|\le|\tilde{\mu}_n(t)-\tilde{\mu}_n(r)|+|\tilde{\mu}_n(r)-\mu(r)|+|\mu(r)-\mu(t)|<3\varepsilon
$$
Hence $\tilde{\mu}_n\rightrightarrows\mu$. It proves $\mu_n$ has convergent subsequence and thus $\bar{A}$ is compact.
**QED**
```ad-thm
A sequence $\{\mathbb{P}_n\}$ of probability measures on $(C[0,\infty),\mathcal{B}(C[0,\infty)))$ is **tight** iff 
1. $$
\lim_{\lambda\uparrow\infty}\sup_{n\ge 1}\mathbb{P}_n[|\mu(0)|>\lambda]=0
$$
2. $$
   \lim_{\delta\downarrow0}\sup_{n\ge1}\mathbb{P}_n[m^T(\mu,\delta)>\varepsilon]=0,\forall T,\varepsilon>0
   $$
```

^2783b9

**Proof**
$\Longrightarrow$: Suppose $\mathbb{P}_n$ is tight. For $\forall\eta>0$, there exists $K\subseteq C[0,\infty)$ is compact s.t. $\mathbb{P}_n(K)\ge 1-\eta$. By [[#^4d7ac0|Arzelà-Ascoli theorem]], there exists sufficiently large $\lambda>0$ s.t. $|\mu(0)|<\lambda$ for $\mu\in K$. Hence, $\forall\eta>0$, $\exists\lambda>0$ s.t. 
$$
\sup_{n\ge 1}\mathbb{P}_n[|\mu(0)|>\lambda]\le\sup_{n\ge1}\mathbb{P}[K^c]\le\eta
$$
For item2, bt the same theorem, fix $T$ and for $\varepsilon>0$, there exists $\delta_0>0$ s.t. $m^T(\mu,\delta)<\varepsilon$ for $0<\delta<\delta_0$.
$\Longleftarrow$: Suppose the two condition hold. Fix $T,\eta>0$, we choose $\lambda>0$ s.t. 
$$
\sup_{n\ge1}\mathbb{P}_n[|\mu(0)|>\lambda]\le\frac{\eta}{2^{T+1}}
$$
choose $\delta_k>0$ s.t. 
$$
\sup_{n\ge1}\mathbb{P}_n\left[m^T(\mu,\delta)>\frac{1}{k}\right]\le\frac{\eta}{2^{T+k+1}}
$$
Let 
$$
A_T=\left\{\mu:|\mu(0)|\le\lambda,m^{T}(\mu,\delta)\le\frac{1}{k}\right\},A=\bigcap_{T=1}^{\infty}A_T
$$
Then 
$$
\mathbb{P}_n(A_T)\ge1-\sum_{n=0}^{\infty}\frac{\eta}{2^{T+k+1}}=1-\frac{\eta}{2^{T}}
$$
$$
\mathbb{P}_n(A^c)\le\sum_{T=1}^{\infty}\mathbb{P}_n(A^c_T)\le\sum_{T=1}^{\infty}\frac{\eta}{2^T}=\eta
$$
By [[#^4d7ac0|Arzelà-Ascoli theorem]], $A$ is compact and $\mathbb{P}$ is tight.
**QED**
# Convergence of Finite-Dimensional distributions
```ad-def
title:Projection mapping
For finite set $\{t_1,\cdots,t_d\}\subseteq[0,\infty)$, define $\pi_{t_1,\cdots,t_d}:C[0,\infty)\to\mathbb{R}^d$ as 
$$
\pi_{t_1,\cdots,t_d}(\mu)=(\mu(t_1),\cdots,\mu(t_d))
$$
```

```ad-proposition
If the function $f:\mathbb{R}^d\to\mathbb{R}$ is continuous and bounded, then the composition mapping $f\circ\pi_{t_1,\cdots,t_d}:C[0,\infty)\to\mathbb{R}$ has the property, for $\textbf{X}^{(n)}\xrightarrow{d}\textbf{X}\Longrightarrow$
$$
\begin{align}
\lim_{n\to\infty}\mathbb{E}_n(f(X^{(n)}_{t_1}),\cdots,f(X^{(n)}_{t_d}))&=\lim_{n\to\infty}\mathbb{E}_n(f\circ\pi_{t_1,\cdots,t_d}(\textbf{X}^{(n)}))\\
&=\mathbb{E}(f\circ\pi_{t_1,\cdots,t_d}(\textbf{X}))\\
&=\mathbb{E}(f(X_{t_1}),\cdots,f(X_{t_d}))
\end{align}
$$
```

```ad-warning
the sequence of processes $\textbf{X}^{(n)}\xrightarrow{d}\textbf{X}$, then all finite-dimensional distributions converge as well. The converse holds in the presence of tightness, but not in general.
```

```ad-thm
Let $\textbf{X}^{(n)}$, be a **tight** sequence of continuous processes with the property that, whenever $0 < t_1 <\cdots < t_d < \infty$, then the sequence of random vectors $\{(X^{(n)}_{t_1},\cdots,X^{(n)}_{t_d})\}$ **converges in distribution**. Let $\mathbb{P}_n$ be the measure induced on $(C[0, \infty), \mathcal{B}(C[0, \infty)))$ by $\textbf{X}^{(n)}$. Then $\mathbb{P}_n\xrightarrow{w}\mathbb{P}$, under which the coordinate mapping process $W_t(\mu)\triangleq \mu(t)$ on $C[0, \infty)$ satisfies
$$
(X^{(n)}_{t_1},\cdots,X^{(n)}_{t_d})\xrightarrow{d}(W_{t_1},\cdots,W_{t_d})
$$
```

^039c08

```ad-proposition
Let $\textbf{X}^{(n)},\textbf{Y}^{(n)}$, and $\textbf{X}$ be random variables with values in a metric space $(S, \rho)$; we assume that for each $n \ge 1$, $\textbf{X}^{(n)}$ and $\textbf{Y}^{(n)}$ are defined on the same probability space. If $\textbf{X}^{(n)}\xrightarrow{d}\textbf{X}$ and $\rho(\textbf{X}^{(n)},\textbf{Y}^{(n)})\xrightarrow{\mathbb{P}}0$, as $n\to\infty$, then $\textbf{Y}^{(n)}\xrightarrow{d}\textbf{X}$ as $n\to\infty$.
```

^1a5130

**Proof**
We consider the equivalent description of weak convergence.
![[Pasted image 20260407143811.png]]
![[Pasted image 20260407143823.png]]
We W.T.S $\textbf{Y}^{(n)}\xrightarrow{d}X$, it suffices to prove item4 i.e. for every closed set $K\subseteq$, we have 
$$
\varlimsup_{n\to\infty}\mathbb{P}(\textbf{Y}^{(n)}\in K)\le\mathbb{P}(\textbf{X}\in K)
$$
Fix closed set $K$ and for $\delta>0$, we define $K_\delta=\{x\in S:\rho(x,K)\le\delta\}$, then $K_\delta$ is also closed. Note that 
$$
\{\textbf{Y}^{(n)}\in K\}\subseteq\{\textbf{X}^{(n)}\in K_\delta\}\cup\{\rho(\textbf{X}^{(n)},\textbf{Y}^{(n)})>\delta\}
$$
We have 
$$
\mathbb{P}(\textbf{Y}^{(n)}\in K)\le\mathbb{P}(\textbf{X}^{(n)}\in K_\delta)+\mathbb{P}(\rho(\textbf{X}^{(n)},\textbf{Y}^{(n)})>\delta)
$$
Since $\textbf{X}^{(n)}\xrightarrow{d}\textbf{X}$, $\varlimsup_{n\to\infty}\mathbb{P}(\textbf{X}^{(n)}\in K_\delta)\le\mathbb{P}(\textbf{X}\in K_\delta)$. Since $\rho(\textbf{X}^{(n)},\textbf{Y}^{(n)})\xrightarrow{\mathbb{P}}0$, $\mathbb{P}(\rho(\textbf{X}^{(n)},\textbf{Y}^{(n)})>\delta)\to0$ as $n\to\infty$. Hence, we obtain
$$
\varlimsup_{n\to\infty}\mathbb{P}(\textbf{Y}^{(n)}\in K)\le \mathbb{P}(X\in K_\delta)
$$
Let $\delta\downarrow0$, $K_\delta\downarrow K$, we prove this proposition.
**QED**
# The Invariance Principle and the Wiener Measure
```ad-def
title:Some definition
Consider $\xi_j\sim(0,\sigma^2),i.i.d$, and $S_0=0,S_k=\sum_{j=1}^{k}\xi_j,k\ge1$. A continuous-time process $Y_t$ can be obtain from $S_k$ by linear interpolation
$$
Y_t=S_{[t]}+(t-[t])\xi_{[t]+1}
$$
Scaling appropriately both time and space, we obtain a sequence of processes $X^{(n)}$
$$
X^{(n)}_t=\frac{1}{\sigma\sqrt{n}}Y_{nt}
$$
Note that with $s = k/n$ and $t = (k + 1)/n$, the increment $X^{(n)}_t-X^{(n)}_s=\frac{1}{\sigma\sqrt{n}}\xi_{k+1}$ is independent with $\sigma(\xi_1,\cdots,\xi_k)$ and $X^{(n)}_t-X^{(n)}_s\sim(0,t-s=\frac{1}{n})$.
```

```ad-thm
For $0\le t_1<\cdots<t_d<\infty$, we have
$$
(X^{(n)}_{t_1},\cdots,X^{(n)}_{t_d})\xrightarrow{d}(B_{t_1},\cdots,B_{t_d})
$$
$B_t$ is a standard, one-dimensional Brownian motion.
```

^37334b

**Proof**
The method is to calculate the **charateristic function**. For $k=1,\cdots,d$, 
$$
\left|X^{(n)}_{t_k}-\frac{1}{\sigma\sqrt{n}}S_{[nt_k]}\right|\le\frac{1}{\sigma\sqrt{n}}|\xi_{[nt_k]+1}|
$$
By Chebyshev's inequality, 
$$
\mathbb{P}\left(\left|X^{(n)}_{t_k}-\frac{1}{\sigma\sqrt{n}}S_{[nt_k]}\right|\ge\varepsilon\right)\le\frac{1}{\varepsilon^2n}\to0
$$
Then for each $k$, $\left|X^{(n)}_{t_k}-\frac{1}{\sigma\sqrt{n}}S^{(n)}\right|\xrightarrow{\mathbb{P}}0$ and thus 
$$
\left\|X^{(n)}-\frac{1}{\sigma\sqrt{n}}S^{(n)}\right\|\xrightarrow{\mathbb{P}}0
$$
where $S^{(n)}=\left(\sum_{j=1}^{[nt_1]}\xi_j,\cdots,\sum_{j=[nt_{d-1}]}^{[nt_d]}\xi_j\right)$. By [[#^1a5130|the proposition]], it suffices to show 
$$
\begin{align}
\frac{1}{\sigma\sqrt{n}}S^{(n)}\xrightarrow{d}(B_{t_1},\cdots,B_{t_d})\Longleftrightarrow
\end{align}
$$
$$
\begin{align}
\xi^{(n)}\triangleq\frac{1}{\sigma\sqrt{n}}\left(\sum_{j=1}^{[nt_1]}\xi_j,\sum_{j=[nt_1]+1}^{[nt_2]}\xi_j,\cdots,\sum_{j=[nt_{d-1}]+1}^{[nt_d]}\xi_j\right)\xrightarrow{d}(B_{t_1},B_{t_2}-B_{t_1}\cdots,B_{t_d}-B_{t_{d-1}})
\end{align}
$$
Now we calculate the charateristic function of $\xi^{(n)}$.
$$
\begin{align}
\mathbb{E}\left[e^{i\textbf{u}\cdot\xi^{(n)}}\right]&=\mathbb{E}\left[\exp\left(\frac{iu_1}{\sigma\sqrt{n}}\sum_{j=1}^{[nt_1]}\xi_j+\cdots+\frac{iu_d}{\sigma\sqrt{n}}\sum_{j=[nt_{d-1}]+1}^{[nt_d]}\xi_j\right)\right]\\
&=\mathbb{E}\left[\exp\left(\frac{i}{\sigma\sqrt{n}}\sum_{k=1}^{d}u_k\sum_{j=[nt_{k-1}]+1}^{[nt_k]}\xi_j\right)\right]\tag{$t_0=0$}\\
&=\prod_{k=1}^{d}\mathbb{E}\left[\exp\left(\frac{iu_k}{\sigma\sqrt{n}}\sum_{j=[nt_{k-1}]+1}^{[nt_k]}\xi_j\right)\right]
\end{align}
$$
By CLT, we have
$$
\mathbb{E}\left[\exp\left(\frac{iu_k}{\sigma\sqrt{n}}\sum_{j=[nt_{k-1}]+1}^{[nt_k]}\xi_j\right)\right]\to e^{-\frac{(t_k-t_{k-1})u_k}{2}}
$$
Therefore, we obtain
$$
\mathbb{E}[e^{i\textbf{u}\cdot\xi^{(n)}}]\to e^{-\frac{1}{2}\Delta\textbf{t}\cdot\textbf{u}}
$$
where $\Delta\textbf{t}=(t_1,t_2-t_1,\cdots,t_d-t_{d-1})$. Hence, we prove $\xi^{(n)}\xrightarrow{d}(B_{t_1},\cdots,B_{t_d}-B_{t_{d-1}})$.
**QED**
```ad-lemma
For $\varepsilon>0$, it holds 
$$
\lim_{\delta\downarrow0}\varlimsup_{n\to\infty}\frac{1}{\delta}\mathbb{P}\left[\max_{1\le j\le[n\delta]+1}|S_j|>\varepsilon\sigma\sqrt{n}\right]=0
$$
```
**Proof**
By CLT, note that $\frac{1}{\sigma\sqrt{[n\delta]+1}}S_{[n\delta]+1}\sim\frac{1}{\sigma\sqrt{[n\delta]}}S_{[n\delta]+1}\xrightarrow{d}Z\sim N(0,1)$. For fixed $\lambda>0$, there exists a sequence bounded, continuous function $\varphi_k$ s.t. $\varphi_k\downarrow\mathbb{1}_{(-\infty,-\lambda]\cup[\lambda,\infty)}$. We have 
$$
\begin{align}
\varlimsup_{n\to\infty}\mathbb{P}\left[|S_{[n\delta]+1}|\ge\lambda\sigma\sqrt{n\delta}\right]&=\varlimsup_{n\to\infty}\mathbb{E}\left[\mathbb{1}_{\{|S_{[n\delta]+1}|\ge\lambda\sigma\sqrt{n\delta}\}}\right]\\
&\le\varlimsup_{n\to\infty}\mathbb{E}\left[\varphi_k\left(\frac{1}{\sigma\sqrt{n\delta}}S_{[n\delta]+1}\right)\right]=\mathbb{E}(\varphi_k(Z))\to\mathbb{P}(|Z|>\lambda)
\end{align}
$$
By Chebyshev's inequality, 
$$
\varlimsup_{n\to\infty}\mathbb{P}\left[|S_{[n\delta]+1}|\ge\lambda\sigma\sqrt{n\delta}\right]\le\frac{1}{\lambda^3}\mathbb{E}|Z|^3
$$
Let $\tau=\min\{j:|S_j|\ge\varepsilon\sigma\sqrt{n}\}$ with $0<\delta<\frac{\varepsilon^2}{2}$. We have 
$$
\begin{align}
\mathbb{P}\left[\max_{1\le j\le[n\delta]+1}|S_j|>\varepsilon\sigma\sqrt{n}\right]&\le\mathbb{P}\left[\max_{1\le j\le[n\delta]+1}|S_j|>(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\right]\\
&\le\mathbb{P}\left[|S_{[n\delta]+1}|>(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\right]\\
&+\sum_{j=1}^{[n\delta]}\mathbb{P}\left[|S_{[n\delta]+1}|\le(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\mid \tau=j\right]\mathbb{P}(\tau=j)
\end{align}
$$
We estimate $\mathbb{P}\left[|S_{[n\delta]+1}|\le(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\mid \tau=j\right]$. On the event $\{\tau=j\}=\{|S_j|\ge\varepsilon\sigma\sqrt{n}\}$, that implies $|S_j-S_{[n\delta]+1}|\ge|S_j|-|S_{[n\delta]+1}|\ge\sigma\sqrt{2n\delta}$. By Chebyshev's inequality, 
$$
\begin{align}
\mathbb{P}\left[|S_{[n\delta]+1}|\le(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\mid \tau=j\right]&\le\mathbb{P}[|S_j-S_{[n\delta]+1}|\ge\sigma\sqrt{2n\delta}]\\
&\le\frac{1}{2n\delta\sigma^2}\mathbb{E}|S_j-S_{[n\delta]+1}|^2\\
&=\frac{1}{2n\delta\sigma^2}\mathbb{E}\sum^{i=j+1}_{[n\delta]+1}\xi^2_i=\frac{[n\delta]-j}{2n\delta}<\frac{1}{2}
\end{align}
$$
Then we obtain
$$
\begin{align}
\mathbb{P}\left[\max_{1\le j\le[n\delta]+1}|S_j|>\varepsilon\sigma\sqrt{n}\right]&\le\mathbb{P}\left[\max_{1\le j\le[n\delta]+1}|S_j|>(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\right]+\frac{1}{2}\mathbb{P}(\tau\le[n\delta]+1)\\
&\le\mathbb{P}\left[\max_{1\le j\le[n\delta]+1}|S_j|>(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\right]\\
&+\frac{1}{2}\mathbb{P}\left(\max_{1\le j\le[n\delta]+1}|S_j|>\varepsilon\sigma\sqrt{n}\right)\\
\Longrightarrow\mathbb{P}\left(\max_{1\le j\le[n\delta]+1}|S_j|>\varepsilon\sigma\sqrt{n}\right)&\le2\mathbb{P}\left[\max_{1\le j\le[n\delta]+1}|S_j|>(\varepsilon-\sqrt{2\delta})\sigma\sqrt{n}\right]
\end{align}
$$
Let $\lambda=\frac{(\varepsilon-\sqrt{2\delta}))}{\sqrt{2\delta}}$, then 
$$
\begin{align}
\varlimsup_{n\to\infty}\mathbb{P}\left(\max_{1\le j\le[n\delta]+1}|S_j|>\varepsilon\sigma\sqrt{n}\right)&\le\frac{\delta\sqrt{\delta}}{(\varepsilon-\sqrt{2\delta})^3}\mathbb{E}|Z|^3\\
\Longrightarrow\varlimsup_{n\to\infty}\frac{1}{\delta}\mathbb{P}\left(\max_{1\le j\le[n\delta]+1}|S_j|>\varepsilon\sigma\sqrt{n}\right)&\le\frac{\sqrt{\delta}}{(\varepsilon-\sqrt{2\delta})^3}\mathbb{E}|Z|^3\to0\mbox{ as $\delta\to0$}
\end{align}
$$
**QED**
```ad-lemma
Under the assumption of last lemma, for any $T>0$, 
$$
\lim_{\delta\downarrow0}\varlimsup_{n\to\infty}\mathbb{P}\left[\max_{1\le j\le[n\delta]+1,1\le k\le[nT]+1}|S_{j+k}-S_k|>\varepsilon\sigma\sqrt{n}\right]=0
$$
```

^e19cfb

**Proof**
For $0<\delta<T$, there exists $m\ge2$ s.t. $\frac{T}{m}<\delta<\frac{T}{m-1}$. Note that 
$$
\lim_{n\to\infty}\frac{[nT]+1}{[n\delta]+1}=\frac{T}{\delta}<m\Longrightarrow [nT]+1\le([n\delta]+1)m\mbox{ for large $n$}
$$
Suppose $|S_{j+k}-S_k|>\varepsilon\delta\sqrt{n}$ for some $k\in[0,[nT]+1]$ and some $j\in[0,[n\delta]+1]$. There exists unique integer $p\in [0,m-1]$ s.t. 
$$
([n\delta]+1)p\le k<([n\delta]+1)(p+1)
$$
There are two cases of $k+j$. One possibility is $([n\delta]+1)p\le k+j<([n\delta]+1)(p+1)$ in which cases either $|S_k-S_{([n\delta]+1)p}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}$ or $|S_{k+j}-S_{([n\delta]+1)p}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}$. The second possibility is $([n\delta]+1)(p+1)\le k+j<([n\delta]+1)(p+2)$ in which cases either $|S_k-S_{([n\delta]+1)p}|>\frac{1}{3}\varepsilon\sigma\sqrt{n},|S_{([n\delta]+1)p}-S_{([n\delta]+1)(p+1)}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}$ or $|S_{k+j}-S_{([n\delta]+1)(p+1)}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}$. In conclusions, 
$$
\left\{\max_{1\le j\le[n\delta]+1,1\le k\le[nT]+1}|S_{j+k}-S_k|>\varepsilon\sigma\sqrt{n}\right\}\subseteq\bigcup_{p=0}^{\infty}\left[\max_{1\le j\le[n\delta]+1}|S_{j+([n\delta]+1)p}-S_{([n\delta]+1)p}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}\right]
$$
and 
$$
\mathbb{P}\left\{\max_{1\le j\le[n\delta]+1}|S_{j+([n\delta]+1)p}-S_{([n\delta]+1)p}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}\right\}=\mathbb{P}\left\{\max_{1\le j\le[n\delta]+1}|S_{j}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}\right\}
$$
Hence, 
$$
\mathbb{P}\left\{\max_{1\le j\le[n\delta]+1,1\le k\le[nT]+1}|S_{j+k}-S_k|>\varepsilon\sigma\sqrt{n}\right\}\le(m+1)\mathbb{P}\left\{\max_{1\le j\le[n\delta]+1}|S_{j}|>\frac{1}{3}\varepsilon\sigma\sqrt{n}\right\}
$$
By last lemma, this lemma holds. 
**QED**
```ad-thm
title:The Invariance Principle
Let $(\Omega,\mathcal{F}, \mathbb{P})$ be a probability space on which is given a sequence $\{\xi_j\}\sim(0,\sigma^2),i.i.d$. Define $X^{(n)}=X^{(n)}_t$, and let $\mathbb{P}_n$ be the measure induced by $X^{(n)}$ on $(C[0, \infty), \mathcal{B}(C[0, \infty)))$. Then $\mathbb{P}_n\xrightarrow{w}\mathbb{P}_*$under which the coordinate mapping process $W_t(\omega)= \mu(t)$ on $C[0, \infty)$ is a standard, one-dimensional Brownian motion.
```
**Proof**
By [[#^039c08|tightness+converge in distribution theorem]] and [[#^37334b|converge to Brownian motion]], it suffices to show $X^{(n)}$ is tight. We need only establish  for $\forall\varepsilon>0,T>0$, the convergence 
$$
\lim_{\delta\downarrow0}\varlimsup_{n\to\infty}\mathbb{P}\left[\max_{|s-t|\le\delta,0\le s,t\le T}|X^{(n)}_s-X^{(n)}_t|>\varepsilon\right]=0
$$
Note that 
$$
\mathbb{P}\left[\max_{|s-t|\le\delta,0\le s,t\le T}|X^{(n)}_s-X^{(n)}_t|>\varepsilon\right]=\mathbb{P}\left[\max_{|s-t|\le n\delta,0\le s,t\le nT}|Y_s-Y_t|>\varepsilon\sigma\sqrt{n}\right]
$$
and 
$$
\max_{|s-t|\le n\delta,0\le s,t\le nT}|Y_s-Y_t|\le\max_{|s-t|\le [n\delta]+1,0\le s,t\le [nT]+1}|Y_s-Y_t|\le\max_{1\le j\le [n\delta]+1,0\le k\le [nT]+1}|S_{k+j}-S_k|
$$
By [[#^e19cfb|lemma]], the convergence holds. 
**QED**
```ad-def
title:Wiener measure
The probability measure on $(C[0, \infty), ,\mathcal{B}(C[0, \infty)))$, under which the coordinate mapping process $W_t(\omega)=\mu(t), 0 < t < \infty$, is a standard, one-dimensional Brownian motion, is called Wiener measure.
```

---
# Exercises
```ad-question
Let $\mathcal{C}(\mathcal{E}_i)$ be the collection of finite-dimensional cylinder sets of the form (2.1); i.e.,

$$
\quad C = \{ \omega \in C[0, \infty); (\omega(t_1), \ldots, \omega(t_n)) \in A \}; \quad n \geq 1, \, A \in \mathcal{B}(\mathbb{R}^n),
$$

where, for all $i = 1, \ldots, n$, $t_i \in [0, \infty)$ (respectively, $t_i \in [0, t]$). Denote by $\mathcal{C}(\mathcal{E}_i)$ the smallest $\sigma$-field containing $\mathcal{C}(\mathcal{E}_i)$.

Show that $\mathcal{G} = \mathcal{B}(C[0, \infty))$, the Borel $\sigma$-field generated by the open sets in $C[0, \infty)$, and that $\mathcal{G}_i = \varphi_i^{-1}(\mathcal{B}(C[0, \infty))) \triangleq \mathcal{B}_i(C[0, \infty))$, where $\varphi_i: C[0, \infty) \to C[0, \infty)$ is the mapping $(\varphi_i \omega)(s) = \omega(t \wedge s); \, 0 \leq s < \infty$.
```

```ad-done

```

```ad-question
Suppose $\{X_n\}_{n=1}^\infty$ is a sequence of random variables taking values in a metric space $(S_1, \rho_1)$ and converging in distribution to $X$. Suppose $(S_2, \rho_2)$ is another metric space, and $\varphi: S_1 \to S_2$ is continuous. Show that $Y_n \triangleq \varphi(X_n)$ converges in distribution to $Y \triangleq \varphi(X)$.
```

```ad-done
Since $X_n\xrightarrow{d}X$, $\mathbb{E}_nf(X_n)\to\mathbb{E}f(X)$ for any bounded, continuous function. We consider $g=f\circ \varphi$ is also continuous, then we have 
$$
\mathbb{E}_ng(X_n)\to\mathbb{E}g(X)\Longleftrightarrow\mathbb{E}_nf(\varphi(X_n))\to\mathbb{E}f(\varphi(X))
$$
Hence, $\varphi(X_n)\xrightarrow{d}\varphi(X)$. 
```

```ad-question
Let $\{X^{(m)}\}_{m=1}^\infty$ be a sequence of continuous stochastic processes  
$X^{(m)} = \{X_t^{(m)}; 0 \leq t < \infty\}$ on $(\Omega, \mathcal{F}, P)$, satisfying the following conditions:
(i) $\displaystyle \sup_{m \geq 1} \mathbb{E}|X_0^{(m)}|^\nu \triangleq M < \infty$,
(ii) $\displaystyle \sup_{m \geq 1} \mathbb{E}|X_t^{(m)} - X_s^{(m)}|^\alpha \leq C_T |t - s|^{1+\beta}; \quad \forall T > 0 \text{ and } 0 \leq s, t \leq T$
for some positive constants $\alpha, \beta, \nu$ (universal) and $C_T$ (depending on $T > 0$).
Show that the probability measures $P_m \triangleq P(X^{(m)})^{-1}$; $m \geq 1$ induced by these processes on $(C[0, \infty), \mathcal{B}(C[0, \infty)))$ form a tight sequence.
```

```ad-done
We check the [[#^2783b9|condition 1 and condition 2]]. 
For condition 1, by Chebyshev's inequality, 
$$
\begin{align}
\sup_{m\ge1}\mathbb{P}_m[\mu:|\mu(0)|>\lambda]=\sup_{m\ge1}\mathbb{P}_m[|X^{(m)}_0|>\lambda]\le \frac{\sup_{m\ge1}\mathbb{E}|X^{(m)}_0|^\nu}{\lambda^\nu}\to0\mbox{ as }\lambda\to\infty
\end{align}
$$
For condition 2. 
**Stpe1.** Take partition of $[0,T]$: $0=t^{(n)}_0<t^{(n)}_1<\cdots<t^{(n)}_k=\frac{kT}{2^n}<\cdots<t^{(n)}_{2^n}=T$. Let $M_n=\max_{1\le k\le 2^n}|X_{t^{(n)}_{k+1}}-X_{t^{(n)}_{k}}|$. We take some estimate. We will choose some $\eta_n$,
$$
\begin{align}
\mathbb{P}(|X_{t^{(n)}_{k+1}}-X_{t^{(n)}_{k}}|>\eta_n)\le\frac{\mathbb{E}|X_{t^{(n)}_{k+1}}-X_{t^{(n)}_{k}}|^\alpha}{\eta^\alpha}\le C_TT^{1+\beta}2^{-n(1+\beta)}\eta_n^{-\alpha}
\end{align}
$$
$$
\begin{align}
\mathbb{P}(M_n>\eta_n)\le\sum_{k=1}^{2^n}\mathbb{P}(|X_{t^{(n)}_{k+1}}-X_{t^{(n)}_{k}}|>\eta_n)\le C_T'2^{-n\beta}\eta_n^{-\alpha}
\end{align}
$$
**Step2.** The idea is from the [[Kolmogorov's Construction of Brownian Motion#^8ee428|proof of Kolmogorov-Centsov continuity theorem]]. We choose $N$ s.t. $\frac{T}{2^{N+1}}<\delta<\frac{T}{2^{N}}$ and $|s-t|<\delta$, we have 
$$
|X_t-X_s|\le2\sum_{n=N}^{\infty}M_n
$$
If $\sum_{n=N}^{\infty}M_n<\frac{\varepsilon}{2}\Longrightarrow m^T(\mu,\delta)<\varepsilon$ and thus $m^T(\mu,\delta)\ge\varepsilon\Longrightarrow\sum_{n=N}^{\infty}M_n\ge\frac{\varepsilon}{2}$. We have 
$$
\mathbb{P}_m(m^T(\mu,\delta)\ge\varepsilon)\le\mathbb{P}\left(\sum_{n=N}^{\infty}M_n\ge\frac{\varepsilon}{2}\right)
$$
If we choose some $\eta_n$ s.t. $\sum_{n=N}^{\infty}\eta_n<\frac{\varepsilon}{2}$, then we have 
$$
\mathbb{P}\left(\sum_{n=N}^{\infty}M_n\ge\frac{\varepsilon}{2}\right)\le \sum_{n=N}^{\infty}\mathbb{P}(M_n\ge\eta_n)
$$
Take $\eta_n=\frac{\varepsilon}{4}\frac{1}{2^{(n-N)\theta}}$ for some $\theta>0$. Then 
$$
\sum_{n=N}^{\infty}\eta_n=\frac{\varepsilon}{4}\frac{1}{1-2^{-\theta}}<\frac{\varepsilon}{2}\Longrightarrow\theta>1
$$
For this $\eta_n$,
$$
\begin{align}
\sum_{n=N}^{\infty}\mathbb{P}(M_n\ge\eta_n)\le C_T''2^{-N\beta}\to0\mbox{ as }N\to\infty\tag{$\theta=\frac{\beta}{2\alpha}$}
\end{align}
$$
When $N\to\infty$, $\delta\downarrow0$. Above all, we obtain
$$
\sup_{m\ge1}\mathbb{P}_m(m^T(\mu,\delta)>\varepsilon)\to0\mbox{ as }\delta\downarrow0
$$
By [[#^2783b9|the theorem]], we obtain $\mathbb{P}_m$ is a tight sequence.
```

```ad-question
Suppose $\{P_n\}_{n=1}^\infty$ is a sequence of probability measures on $(C[0, \infty), \mathcal{B}(C[0, \infty)))$ which converges weakly to a probability measure $P$.  
Suppose, in addition, that $\{f_n\}_{n=1}^\infty$ is a uniformly bounded sequence of real-valued, continuous functions on $C[0, \infty)$ converging to a continuous function $f$, the convergence being uniform on compact subsets of $C[0, \infty)$. Then  
$$
\lim_{n \to \infty} \int_{C[0, \infty)} f_n(\omega) \, dP_n(\omega) = \int_{C[0, \infty)} f(\omega) \, dP(\omega).
$$
```

```ad-done
Since $\mathbb{P}_n\xrightarrow{w}\mathbb{P}$, by [[#^07a931|Prohorov theorem]], $\mathbb{P}_n$ is tight. Then there exists a compact set $K\subseteq C[0,\infty)$ s.t. $\mathbb{P}_n(K^c)<\varepsilon$ and $K^c$ is open. we have 
$$
\varlimsup_{n\to\infty}\mathbb{P}_n(K^c)\le \mathbb{P}(K^c)<\varepsilon
$$
Since $f_n(\omega)\rightrightarrows f(\omega)$ on compact set $K$, suppose $N_1$ when $n\ge N_1$ s.t. 
$$
\sup_{\omega\in K}|f_n(\omega)-f(\omega)|<\varepsilon
$$
Besides, $\{f_n\}$ are uniformly bounded, we have for $\forall\omega$,
$$
\sup_{n\ge1}\sup_{\omega}|f_n(\omega)|\le M,\sup_{\omega}|f(\omega)|\le M
$$
Now We consider
$$
\begin{align}
&\left|\int_{C[0,\infty)}f_n(\omega){d}\mathbb{P}_n-\int_{C[0,\infty)}f(\omega){d}\mathbb{P}\right|\\
\le&\left|\int_{C[0,\infty)}f_n(\omega)-f(\omega){d}\mathbb{P}_n\right|+\left|\int_{C[0,\infty)}f(\omega){d}\mathbb{P}_n-\int_{C[0,\infty)}f(\omega){d}\mathbb{P}\right|
\end{align}
$$
For the first item, 
$$
\begin{align}
\mbox{item1}&\le\int_{K}|f_n(\omega)-f(\omega)|{d}\mathbb{P}_n+\int_{K^c}|f_n(\omega)-f(\omega)|{d}\mathbb{P}_n\\
&\le 2M+2M\mathbb{P}_n(K^c)\le (2M+1)\varepsilon
\end{align}
$$
For the second item, since $\mathbb{P}_n\xrightarrow{w}\mathbb{P}$ and $f$ is bounded, continuous, 
$$
\begin{align}
\mbox{item2}\to0\mbox{ as }n\to\infty
\end{align}
$$
Hence, 
$$
\int_{C[0,\infty)}f_n(\omega){d}\mathbb{P}_n\to\int_{C[0,\infty)}f(\omega){d}\mathbb{P}
$$
```