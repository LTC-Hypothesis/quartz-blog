# Definitions
```ad-def
title:Stochastic differential equation(SDE)
Consider 
$$
dX_t=b(t,X_t){d}t+\sigma(t,X_t){d}W_t\tag{SDE2}
$$
where 
1. $W$ is r-dimensional Brownian motion
2. $b=\{b_i\}_{1\le i\le d}:[0,\infty)\times\mathbb{R}^d\to\mathbb{R},\sigma=\{\sigma_{ij}\}_{1\le i\le d,1\le j\le r}:[0,\infty)\times\mathbb{R}^d\to\mathbb{R}^{d\times r}$. $b$ is called drift and $\sigma$ is called dispersion.
3. $a(t,x)$ is called diffusion matrix and $a(t,x)=\sigma(t,x)\sigma(t,x)^{\top}$
   $$
   a_{ik}=\sum_{j=1}^{r}\sigma_{ij}\sigma_{kj}
   $$
```

^53e799

```ad-def
title:Preparation of space and filtration
We assume that the probability spcae $(\Omega,\mathcal{F},\mathbb{P})$ is rich enough s.t. $\xi$ taking value in $\mathbb{R}^d$, independent of $\mathcal{F}_{\infty}^W$ and with initial probability
$$
\mu(\Gamma)=\mathbb{P}[\xi\in \Gamma],\Gamma\in\mathcal{B}(\mathbb{R}^d)
$$
Left-continuous filtration
$$
\mathcal{G}_t=\sigma(\xi)\vee\mathcal{F}_t^W
$$
Null sets 
$$
\mathcal{N}=\left\{N\subseteq\Omega:\exists G\in\mathcal{G}_{\infty},N\subseteq G,\mathbb{P}(G)=0\right\}
$$
Augmented filtration
$$
\mathcal{F}_t=\sigma(\mathcal{G}_t\cup\mathcal{N}),\mathcal{F}_\infty=\sigma\left(\bigcup_{t\ge0}\mathcal{F}_t\right)
$$
```

^32ec87

```ad-def
title:Strong solutions
A strong solutions $X$ of (SDE2) on the given probability space $(\Omega,\mathcal{F},\mathbb{P})$  and w.r.t. Brownian motion $W$ and initial condition $X_0=\xi$, is a process with continuous sample paths and satisfies the following properties:
1. **(Most important)** $X$ is adapted to the augmented filtration $\{\mathcal{F}_t\}$
2. $\mathbb{P}[X_0=\xi]=1$
3. It holds that 
   $$
   \mathbb{P}\left[\int_{0}^{t}|b_i(s,X_s)|^2+\sigma_{ij}^2(s,X_s){d}s<\infty\right]=1,1\le i\le d,1\le j\le r,0\le t<\infty
   $$
4. It holds that 
   $$
   X_t=\xi+\int_{0}^{t}b(s,X_s){d}s+\int_{0}^{t}\sigma(s,X_s){d}W_s,a.s.-\mathbb{P}
   $$
```

```ad-def
title:Strong uniqueness
Suppose $X_t$ and $\tilde{X}_t$ be two strong solutions of (SDE2) relative to $W_t$ with initial condition $\xi$ and then $\mathbb{P}[X_t=\tilde{X}_t,0\le t<\infty]=1$. We say that strong solutions holds for the pair $(b,\sigma)$. 
```
# The Ito Theory
```ad-lemma
title:Gronwall's inequality
Suppose the continuous function $g(t)$ satisfies
$$
0\le g(t)\le \alpha(t)+\beta\int_{0}^{t}g(s){d}s
$$
where $\beta\ge0,\alpha:[0,T]\to\mathbb{R}$ integrable. Then 
$$
g(t)\le \alpha(t)+\beta \int_{0}^{t}\alpha(s)e^{\beta (t-s)}{d}s
$$
```

^5fc0f3

```ad-thm
title:Local result
Suppose $b,\sigma$ satisfy the locally Lipschitz condition i.e. for $n\ge1$, $\exists K_n>0$ s.t. $\|x\|\le n,\|y\|\le n$, we have 
$$
\|b(t,x)-b(t,y)\|+\|\sigma(t,x)-\sigma(t,y)\|\le K_n\|x-y\|
$$
where $\|\sigma\|^2=\sum_{i=1}^{d}\sum_{j=1}^{r}|\sigma_{ij}|^2$. Then (SDE2) have unique strong solutions. 
```

```ad-thm
title:Global result
Suppose $b,\sigma$ satisfy Lipschitz conditions and linear growth conditions i.e. for $x,y\in\mathbb{R}^d,\exists K>0$ s.t. 
$$
\|b(t,x)-b(t,y)\|+\|\sigma(t,x)-\sigma(t,y)\|\le K\|x-y\|
$$
$$
\|b(t,x)\|+\|\sigma(t,x)\|\le K(1+\|x\|)
$$
and initial condition $\xi$ have finite 2nd moment $\mathbb{E}\|\xi\|^2<\infty$. Then there exists a continuous adapted process $X_t$ be strong solution of (SDE2).
Moreover, $\forall T>0$, $\exists C=C(K,T)>0$ s.t. 
$$
\mathbb{E}\|X_t\|^2\le C(1+\mathbb{E}\|\xi\|^2)e^{Ct},0\le t\le T
$$
```

^d1379b

**Proof**
The method of proof is the Picard Iteration. We should construct the a sequence of Iterated formula, setting $X^{(0)}=\xi$ and 
$$
X^{(k+1)}_t=\xi+\int_{0}^{t}b(s,X^{(k)}_s){d}s+\int_{0}^{t}\sigma(s,X_s^{(k)}){d}W_s\tag{$**$}
$$
The process $\{X^{(k)}_t\}_{k=1}^{\infty}$ we construct is continuous and adapted to the filtration $\{\mathcal{F}_t\}$. We hope to show $X^{(k)}$ converges to some $X$ be the solution of (SDE2).
Now we need a lemma. 
```ad-lemma
$\forall T>0$, $\exists C=C(K,T)>0$ s.t.
$$
\mathbb{E}\|X^{(k)}_t\|^2\le C(1+\mathbb{E}\|\xi\|^2)e^{Ct},0\le t\le T
$$
```

^fe3d0d

We prove by induction. For $k=0$, $\mathbb{E}\|X^{(0)}\|^2=\mathbb{E}\|\xi\|^2\le C(1+\mathbb{E}\|\xi\|^2)e^{Ct}$ obviously. Suppose it holds for $k$ i.e. 
$$
\mathbb{E}\|X^{(k)}_t\|^2\le C(1+\mathbb{E}\|\xi\|^2)e^{Ct}
$$
We W.T.S. it also holds for $X^{(k+1)}$.
$$
\begin{align}
\mathbb{E}\|X^{(k+1)}\|^2&=\mathbb{E}\left\|\xi+\int_{0}^{t}b(s,X_s^{(k)}){d}s+\int_{0}^{t}\sigma(s,X^{(k)}_s){d}W_s\right\|^2\\
&\le \mathbb{E}\|\xi\|^2+\mathbb{E}\left\|\int_{0}^{t}b(s,X_s^{(k)}){d}s\right\|^2+\mathbb{E}\sup_{0\le t\le T}\left\|\int_{0}^{t}\sigma(s,X^{(k)}_s){d}W_s\right\|^2
\end{align}
$$
For drift item, by Cauchy-Schwarz's inequality, 
$$
\begin{align}
\mathbb{E}\left\|\int_{0}^{t}b(s,X_s^{(k)}){d}s\right\|^2&\le T\mathbb{E}\int_{0}^{t}\left\|b(s,X_s^{(k)})\right\|^2{d}s\\
&\le K^2T\mathbb{E}\int_{0}^{t}(1+\|X_s^{(k)}\|)^2{d}s\\
&\le 2K^2T\left(T+\int_{0}^{t}\mathbb{E}\|X^{(k)}_s\|^2{d}s\right)\\
&\le 2K^2T\left(T+e^{Ct}(1+\mathbb{E}\|\xi\|^2)\right)
\end{align}
$$
For dispersion item, by [[The Change-of-Variable Formula#^6cf33d|BDG's inequality]], 
$$
\begin{align}
\mathbb{E}\sup_{0\le t\le T}\left\|\int_{0}^{t}\sigma(s,X^{(k)}_s){d}W_s\right\|^2&\le\mathbb{E}\int_{0}^{t}\|\sigma(s,X^{(k)}_s)\|^2{d}s\\
&\le 2K^2\left(T+e^{Ct}(1+\mathbb{E}\|\xi\|^2)\right)
\end{align}
$$
Above all, we have 
$$\mathbb{E}\|X^{(k+1)}\|^2\le C(K,T)(1+\mathbb{E}\|\xi\|^2)e^{Ct}
$$
Now we return the main proof. We have $X^{(k+1)}-X^{(k)}\triangleq A_t+M_t$ where 
$$
A_t\triangleq\int_{0}^{t}b(s,X_s^{(k)})-b(s,X^{(k-1)}_s){d}s,M_t\triangleq\int_{0}^{t}\sigma(s,X_s^{(k)})-\sigma(s,X^{(k-1)}_s){d}W_s
$$
Thanks to linear growth conditions and [[#^fe3d0d|lemma]], $M_t\in\mathcal{M}^c_2$. We use [[The Change-of-Variable Formula#^400644|the moment inequality]],
$$
\begin{align}
\mathbb{E}\left[\max_{0\le s\le t}\|M_s\|^2\right]&\le C_1\mathbb{E}\int_{0}^{t}\left\|\sigma(s,X^{(k)}_s)-\sigma(s,X^{(k-1)}_s)\right\|^2{d}s\\
&\le C_1K^2\mathbb{E}\int_{0}^{t}\left\|X^{(k)}_s-X^{(k-1)}\right\|^2{d}s
\end{align}
$$
and
$$
\begin{align}
\mathbb{E}\|A_t\|^2\le K^2t\int_{0}^{t}\left\|X^{(k)}_s-X^{(k-1)}\right\|^2{d}s
\end{align}
$$
By [[Continuous-Time Martingales#^bd276e|Doob's Maximal inequality]], we denote $4K^2(C_1+T)$ by $L$
$$
\begin{align}
\mathbb{E}\left[\max_{0\le s\le t}\left\|X^{(k+1)}_s-X^{(k)}\right\|^2\right]\le L\mathbb{E}\int_{0}^{t}\left\|X^{(k)}_s-X^{(k-1)}\right\|^2{d}s,k\ge1
\end{align}
$$
Picard iteration: 
$$
\mathbb{E}\left[\max_{0\le s\le t}\left\|X^{(2)}_s-X^{(1)}_s\right\|^2\right]\le L\mathbb{E}\int_{0}^{t}\left\|X^{(1)}_s-\xi\right\|^2{d}s\le Lt\mathbb{E}\left[\max_{0\le t\le T}\|X_t^{(1)}-\xi\|^2\right]
$$
Let $C^*\triangleq\mathbb{E}\left[\max_{0\le t\le T}\|X_t^{(1)}-\xi\|^2\right]$,
$$
\mathbb{E}\left[\max_{0\le s\le t}\left\|X^{(3)}_s-X^{(2)}_s\right\|^2\right]\le L\mathbb{E}\int_{0}^{t}\left\|X^{(2)}_s-X^{(1)}_s\right\|^2{d}s\le C^*L^2\int_{0}^{t}s{d}s=C^{*}\frac{(Lt)^2}{2}
$$
Hence 
$$
\begin{align}
\mathbb{E}\left[\max_{0\le s\le t}\left\|X^{(k+1)}_s-X^{(k)}_s\right\|^2\right]\le C^*\frac{(Lt)^k}{k!}
\end{align}
$$
We consider 
$$
\begin{align}
&\mathbb{P}\left[\max_{0\le s\le t}\left\|X^{(k+1)}_s-X^{(k)}_s\right\|^2\ge\frac{1}{2^{k+1}}\right]\le C^*\frac{(2Lt)^k}{k!}\\
\Longrightarrow&\sum_{k=1}^{\infty}\mathbb{P}\left[\max_{0\le s\le t}\left\|X^{(k+1)}_s-X^{(k)}_s\right\|^2\ge\frac{1}{2^{k+1}}\right]\le \sum_{k=1}^{\infty}C^*\frac{(2Lt)^k}{k!}<\infty
\end{align}
$$
By Borel-Cantelli lemma, we have 
$$
\mathbb{P}\left[\max_{0\le s\le t}\left\|X^{(k+1)}_s-X^{(k)}_s\right\|^2\ge\frac{1}{2^{k+1}},i.o.\right]=0
$$
i.e. $\exists\Omega^*\subseteq\Omega$ with $\mathbb{P}(\Omega^*)=1$ and $N(\omega)\in\mathbb{N}$ s.t. for $\omega\in\Omega^*$, $k\ge N(\omega)$ and $m\ge1$, we have 
$$
\max_{0\le s\le t}\left\|X^{(k+m)}_s-X^{(k)}_s\right\|^2<\frac{1}{2^{k+1}}
$$
Then we obtain $X^{(k)}_t$ converges in compact subset on $[0,\infty)$ with continuous sample path i.e. $X_t^{(k)}\to X_t$ in $C[0,T]$. Besides, by Fatou's lemma,
$$
\mathbb{E}\|X_t\|^2\le \varliminf_{k\to\infty}\mathbb{E}\|X_t^{(k)}\|^2\le C(1+\mathbb{E}\|\xi\|^2)e^{Ct}
$$
**Claim: The just constructed process $X_t\triangleq\lim_{k\to\infty}X^{(k)}_t$ satisfies (SDE2).**
For LHS of $(**)$, $X^{(k+1)}_t\xrightarrow{a.s.}X_t$. It suffices to show the convergence of RHS. For drift integral, by Lipschitz's condition, 
$$
\begin{align}
\left\|\int_{0}^{t}b(s,X_s^{(k)})-b(s,X_s){d}s\right\|&\le \int_{0}^{t}\left\|b(s,X_s^{(k)})-b(s,X_s)\right\|{d}s\\
&\le K\int_{0}^{t}\left\|X^{(k)}_s-X_s\right\|{d}s\\
&\le Kt\sup_{0\le t\le T}\left\|X^{(k)}_t-X_t\right\|\to0\text{ as }k\to\infty
\end{align}
$$
For stochastic integral, 
$$
\begin{align}
\mathbb{E}\left\|\int_{0}^{t}\sigma(s,X_s^{(k)})-\sigma(s,X_s){d}W_s\right\|^2&=\mathbb{E}\int_{0}^{t}\left\|\sigma(s,X_s^{(k)})-\sigma(s,X_s)\right\|^2{d}s\\
&\le K^2\mathbb{E}\int_{0}^{t}\left\|X^{(k)}_s-X_s\right\|^2{d}s\\
&\le K^2T\mathbb{E}\left[\sup_{0\le t\le T}\left\|X_t^{(k)}-X_t\right\|^2\right]\to0\mbox{ as }k\to0
\end{align}
$$
Note that we have 
$$
\int_{0}^{t}b(s,X_s^{(k)}){d}s\xrightarrow{L^2}\int_{0}^{t}b(s,X_s){d}s,\int_{0}^{t}\sigma(s,X_s^{(k)}){d}W_s\xrightarrow{L^2}\int_{0}^{t}\sigma(s,X_s){d}W_s
$$
and 
$$
\begin{align}
0=&X^{(k+1)}-\xi-\int_{0}^{t}b(s,X_s^{(k)}){d}s-\int_{0}^{t}\sigma(s,X_s^{(k)}){d}W_s\\
&\xrightarrow{L^2}X_t-\xi-\int_{0}^{t}b(s,X_s){d}s-\int_{0}^{t}\sigma(s,X_s){d}W_s
\end{align}
$$
Then 
$$
X_t-\xi-\int_{0}^{t}b(s,X_s){d}s-\int_{0}^{t}\sigma(s,X_s){d}W_s=0
$$
**QED**
```ad-warning
If we only remove the condition of $\mathbb{E}\left\|\xi\right\|^2<\infty$, the assertion still remain valid. 
```

# Comparison Results
In this section, we consider one-dimensional case i.e. $d=r=1$. 
```ad-proposition
title:Yamada & Watanabe 
Consider one-dimensional case
$$
dX_t=b(t,X_t){d}t+\sigma(t,X_t){d}W_t
$$
satisfies
$$
|b(t,x)-b(t,y)|\le K|x-y|,|\sigma(t,x)-\sigma(t,y)|\le h(|x-y|)
$$
for $\forall x,y\in\mathbb{R},K>0$ and $h:[0,\infty)\to[0,\infty)$ is strictly increasing with $h(0)=0$ and satisfies
$$
\int_{0}^{\varepsilon}\frac{1}{h^2(u)}{d}u=\infty,\varepsilon>0
$$
Then the strong uniqueness holds for (SDE2). 
```
**Proof**
Suppose two continuous, adapted process $X^{(1)}_t,X^{(2)}_t$, let $\Delta_t=X^{(1)}_t-X^{(2)}_t$. We W.T.S. $|\Delta_t|=0$. But we note that $f(x)=|x|\notin C^2(\mathbb{R})$ so that we cann't use the Ito's rule. The idea is that we should find a function $\psi_n(x)$ s.t. 

1. $\psi_n(x)\in C^2(\mathbb{R}), \psi_n(x)\uparrow|x|$
2. $|\psi_n'(x)|\le 1$
3. $|\psi_n''(x)h(|x|)|\le O\left(\frac{1}{n}\right)$

so that we can use the Ito's rule for $\psi_n(\Delta_t)$. The $\Delta_t$ satisfies 
$$
\Delta_t=\int_{0}^{t}b(s,X_s^{(1)})-b(s,X_s^{(2)}){d}s+\int_{0}^{t}\sigma(s,X_s^{(1)})-\sigma(s,X_s^{(2)}){d}W_s
$$
Then 
$$
\begin{align}
\psi_n(\Delta_t)=&\int_{0}^{t}\psi'_n(\Delta_s)[b_1(s,X_s^{(1)})-b(s,X_s^{(2)})]{d}s+\frac{1}{2}\int_{0}^{t}\psi''_n(\Delta_s)[\sigma(s,X_s^{(1)})-\sigma(s,X_s^{(2)})]^2{d}s\\
&+\int_{0}^{t}\psi'_n(\Delta_s)[\sigma(s,X_s^{(1)})-\sigma(s,X^{(2)}_s)]{d}W_s
\end{align}
$$
Take expectation,
$$
\begin{align}
\mathbb{E}\psi_n(\Delta_t)=&\mathbb{E}\int_{0}^{t}\psi'_n(\Delta_s)[b_1(s,X_s^{(1)})-b(s,X_s^{(2)})]{d}s\\
&+\frac{1}{2}\mathbb{E}\int_{0}^{t}\psi''_n(\Delta_s)[\sigma(s,X_s^{(1)})-\sigma(s,X_s^{(2)})]^2{d}s\\
\le &K\mathbb{E}\int_{0}^{t}|\Delta_s|{d}s+O\left(\frac{1}{n}\right)
\end{align}
$$
Let $n\to\infty$, we obtain 
$$
\mathbb{E}|\Delta_t|\le K\mathbb{E}\int_{0}^{t}|\Delta_s|{d}s
$$
By [[#^5fc0f3|Gronwall's inequality]], we obtain
$$
\mathbb{E}|\Delta_t|\le 0\Longrightarrow|\Delta_t|=0
$$
Now we turn to construct such $\psi_n(x)$. We take a sequence $a_n$ s.t. $a_n\downarrow0$ with $a_0=1$ and s.t. $\int_{a_{n}}^{a_{n-1}}\frac{1}{h^2(u)}{d}u=n$. For $n\ge1$, $\exists\rho_n(x)\in C(\mathbb{R})$ with $\text{supp}\rho_n\subset(a_n,a_{n-1})$ and $0\le \rho_n(x)\le \frac{2}{nh^2(u)}$ hold for $x>0$, $\int_{a_n}^{a_{n-1}}\rho_n(x){d}x=1$. We construct 
$$
\psi_n(x)=\int_{0}^{|x|}\int_{0}^{y}\rho_n(u){d}u{d}y\in C^2(\mathbb{R})
$$
Then we have 
$$
|\psi'_n(x)|\le \int_{0}^{|x|}|\rho_n(u)|{d}u\le \int_{0}^{\infty}\rho_n(u){d}u=1
$$
and 
$$
\begin{align}
\psi_n(x)-|x|&=\int_{0}^{|x|}\int_{0}^{y}\rho_n(u){d}u{d}y-\int_{0}^{|x|}1{d}y\\
&=\int_{0}^{|x|}\int_{0}^{y}\rho_n(u){d}u{d}y-\int_{0}^{|x|}\int_{a_n}^{a_{n-1}}\rho_n(u){d}u{d}y\\
&=\int_{0}^{|x|}\int_{(0,y)\setminus(a_n,a_{n-1})}\rho_n(u){d}u{d}y
\end{align}
$$
For sufficiently large $n$, $(a_n,a_{n-1})\subseteq(0,y)$ and thus $\text{supp}\rho_n(x)\subset(0,y)^c$, i.e. for large $n$ $\psi_n(x)-|x|=0$
$$
\lim_{n\to\infty}\left(\psi_n(x)-|x|\right)=0
$$
The $\psi_n(x)$ is desired. 
**QED**
```ad-warning
title:Yamada & Watanabe 
Weaker condition: For $b(t,X_t)$,
$$
|b(t,x)-b(t,y)|\le \kappa(|x-y|)
$$
where $\kappa:[0,\infty)\to[0,\infty)$ strictly increasing and concave with $\kappa(0)=0$ and 
$$
\int_{0}^{\varepsilon}\frac{1}{\kappa(u)}{d}u=\infty,\forall\varepsilon>0
$$
```

```ad-thm
title:Comparison Theorem
Suppose two continuous, adapted process $X^{(j)}_t,j=1,2$ s.t. 
$$
X^{(j)}_t=X_0^{(j)}+\int_{0}^{t}b_j(s,X^{(j)}_s){d}s+\int_{0}^{t}\sigma(s,X^{(j)}_s){d}W_s
$$
holds a.s. We assume that
1. $\sigma,b_j$ are continuous, real-valued functions on $[0,\infty)\times\mathbb{R}$
2. $|\sigma(t,x)-\sigma(t,y)|\le h(|x-y|)$
3. $X_0^{(1)}\le X_0^{(2)},a.s.-\mathbb{P}$
4. $b_1(t,x)\le b_2(t,x),\forall0\le t<\infty,x\in\mathbb{R}$
5. Either $b_1$ or $b_2$ satisfies $|b(t,x)-b(t,y)|\le K|x-y|$. 
   
Then $\mathbb{P}\left[X^{(1)}_t\le X^{(2)}_t;0\le t<\infty\right]=1$
```
**Proof**
We should consider the auxiliary function $\varphi_n(x)=\psi_n(x)\mathbb{1}_{[0,\infty)}$ amd thus $\varphi_n(x)\to x^+$. We use the Ito's rule for $\varphi_n(\Delta_t)$, 
$$
\begin{align}
\varphi_n(\Delta_t)=&\int_{0}^{t}\varphi'_n(\Delta_s)[b_1(s,X_s^{(1)})-b_2(s,X_s^{(2)})]{d}s+\frac{1}{2}\int_{0}^{t}\varphi_n''(\Delta_s)[\sigma(s,X^{(1)}_s)-\sigma(s,X^{(2)}_s)]^2{d}s\\
&+\int_{0}^{t}\varphi_n'(\Delta_s)[\sigma(s,X^{(1)}_s)-\sigma(s,X^{(2)}_s)]{d}W_s
\end{align}
$$
Take expectation,
$$
\begin{align}
\mathbb{E}\varphi_n(\Delta_t)=&\mathbb{E}\int_{0}^{t}\varphi'_n(\Delta_s)[b_1(s,X_s^{(1)})-b_2(s,X_s^{(2)})]{d}s\\
&+\frac{1}{2}\mathbb{E}\int_{0}^{t}\varphi_n''(\Delta_s)[\sigma(s,X^{(1)}_s)-\sigma(s,X^{(2)}_s)]^2{d}s\\
\le&\mathbb{E}\int_{0}^{t}\varphi'_n(\Delta_s)[b_1(s,X_s^{(1)})-b_1(s,X_s^{(2)})]{d}s\\
&+\mathbb{E}\int_{0}^{t}\varphi'_n(\Delta_s)[b_1(s,X_s^{(2)})-b_2(s,X_s^{(2)})]{d}s+O\left(\frac{1}{n}\right)\\
\le &K\mathbb{E}\int_{0}^{t}\Delta_s^+{d}s+O\left(\frac{1}{n}\right)
\end{align}
$$
Let $n\to\infty$, we have 
$$
\mathbb{E}\Delta_t^+\le K\mathbb{E}\int_{0}^{t}\Delta_s^+{d}s\Longrightarrow\mathbb{E}\Delta_t^+\le0\Longrightarrow X^{(1)}_t\le X^{(2)}_t
$$
**QED**
# Approximations of Stochastic Differential Equations
As is well- known, Brownian motion is an excellent noise model, but in many actual noise processes is **of bounded variation(BV)** and **non-Markov**. Now we have the problem. 
```ad-question
Suppose such process $\{V^{(n)}\}_{n=1}^{\infty}$ i.e. is of BV and non-Markov, $V^{(n)}\to W_t$ in appropriate strong sense. Let process $\{X^{(n)}\}$ be the solutions of the follow SDE
$$
X^{(n)}_t=\xi+\int_{0}^{t}b(X^{(n)}_s){d}s+\int_{0}^{t}\sigma(X^{(n)}_s){d}V^{(n)}_s\tag{SDE3}
$$
We regard the second integral as Lebesgue-Stielthes sense. As $n\to\infty$, what equation will (SDE3) converges to? and what process will $X^{(n)}$ converges to? The answer is F-S integral for the second integral. 
```

```ad-proposition
title:Doss
Suppose $\sigma\in C^2(\mathbb{R})$ with bounded 1st,2nd order derivatives and $b$ is Lipschitz continuous. The the one-dimensional SDE
$$
X_t=\xi+\int_{0}^{t}b(X_s)+\frac{1}{2}\sigma(X_s)\sigma'(X_s){d}s+\int_{0}^{t}\sigma(X_s){d}W_s
$$
holds strong uniqueness. Moreover, it has the form
$$
X_t=u\left(W_t,Y_t\right)
$$
where $u\in C(\mathbb{R}^2)$ and $Y$ solving an ODE. 
```

^38d532

**Proof**
Suppose $A>0$ s.t. $|\sigma',\sigma''|\le A$ and $|b(x)-b(y)|\le L|x-y|$. 
We consider a ODE for function $u:\mathbb{R}^2\to\mathbb{R}$, 
$$
\begin{cases}
\frac{\partial u}{\partial x}=\sigma(u)\\
\frac{\partial }{\partial x}u(0,y)=y
\end{cases}
$$
Derive for $y$, we have 
$$
\begin{align}
\frac{\partial }{\partial x}\left(\frac{\partial u}{\partial y}\right)=\frac{\partial^2 u}{\partial x\partial y}=\sigma'(u)\frac{\partial u}{\partial y},\frac{\partial}{\partial y}u(0,y)=1
\end{align}
$$
Let $v=\frac{\partial u}{\partial y}(x,y)$ and we obtain
$$
\begin{cases}
\frac{\partial v}{\partial x}=\sigma'(u)v\\
v(0,y)=1
\end{cases}\Longrightarrow v=\frac{\partial u}{\partial y}=\exp\left(\int_{0}^{x}\sigma'(u(z,y)){d}z\right)\triangleq\frac{1}{\rho(x,y)}
$$
By $|\sigma'|\le A$, we have $e^{-A|x|}\le \rho(x,y)\le e^{A|x|}$. Now we explore the Lipschitz continuity of $u$ and $\rho$. For $\forall y_1,y_2\in\mathbb{R}$
$$
\begin{align}
|u(x,y_1)-u(x,y_2)|=\left|\int_{y_1}^{y_2}\frac{\partial u(x,y)}{\partial y}{d}y\right|\le e^{A|x|}|y_1-y_2|
\end{align}
$$
For Lipschitz continuity of $\rho$, we should use the inequality 
$$
|e^{z_1}-e^{z_2}|\le (e^{z_1}\vee e^{z_{2}})|z_1-z_2|
$$
Then 
$$
\begin{align}
\left|\rho(x,y_1)-\rho(x,y_2)\right|&\le (\rho(x,y_1)\vee\rho(x,y_2))\int_{0}^{|x|}(\sigma'(u(z,y_1))-\sigma'(z,y_2)){d}z\\
&\le e^{A|x|}\int_{0}^{|x|}|\sigma''(z,\xi)||u(z,y_1)-u(z,y_2)|{d}z\\
&\le e^{2A|x|}|y_1-y_2|
\end{align}
$$
Another one is 
$$
|b(u(x,y_1))-b(u(x,y_1))|\le Le^{A|x|}|y_1-y_2|
$$
Now we define $f(x,y)\triangleq \rho(x,y)b(u(x,y))$. Now we consider the ODE of the process $Y_t$,
$$
\frac{d Y_t}{dt}=f(W_t,Y_t)\tag{ODEY}
$$
We need local Lipschitz conditions. On $[-k,k]$, we have 

- $|f(x,y_1)-f(x,y_1)|\le L_k|y_1-y_2|,\forall |x,y_1,y_2|\le k$
- $|f(x,y)|\le K_1+M_k|y|,|x|\le k,y\in\mathbb{R}$

By the theorem of ODE, there exists the unique solution of (ODEY) $Y_t$. We define $X_t\triangleq u(W_t,Y_t)$. By the Ito's rule, we have 
$$
\begin{align}
dX_t&=\frac{\partial u}{\partial x}{d}W_t+\frac{\partial u}{\partial y}{d}Y_t+\frac{1}{2}\frac{\partial^2u}{\partial x^2}{d}t\\
&=\sigma(X_t){d}W_t+b(X_t){d}t+\frac{1}{2}\sigma(u)\sigma'(u){d}t
\end{align}
$$
**QED**
```ad-warning
Note that (SDE3) is equivalent to F-S integral SDE, 
$$
X_t=\xi+\int_{0}^{t}b(X_s){d}s+\int_{0}^{t}\sigma(X_s)\circ{d}W_s
$$
```

```ad-lemma
Let $V_\cdot(\omega)$ be a continuous process and have finite total variation $\check{V}_t$ on the compact interval $[0,t]$. If $b,\sigma:\mathbb{R}\to\mathbb{R}$ are Lipschitz continuous, then the (SDE3) with $V^{(n)}\equiv V_\cdot$ has a unique solution. 
```
**Proof**
Set $X^{(n)}_0=\xi$, we define the recursively for $k\ge1$, 
$$
X^{(k+1)}=\xi+\int_{0}^{t}b(X^{(k)}_s){d}s+\int_{0}^{t}\sigma(X^{(k)}_s){d}V_s
$$
and $M^{(k+1)}=\max_{0\le s\le t}|X^{(k+1)}_s-X^{(k)}_s|$. We have 
$$
M^{(k+1)}\le L\int_{0}^{t}M^{(k)}({ds+d\check{V}_s})
$$
By Picard's iteration, 
$$
M^{(k+1)}\le M^{(1)}\frac{L^k(t+\check{V})^k}{k!}
$$
For fixed $t\ge0$, we have 
$$
\sum_{k=1}^{\infty}M^{(1)}\frac{L^k(t+\check{V})^k}{k!}<\infty
$$
For $N(\omega)\in\mathbb{N}$, if $m>n>N(\omega)$, 
$$
\max_{0\le s\le t}|X^{(m)}_s-X^{(n)}_s|\le \sum_{j=n+1}^{m}M^{(j)}\le\sum_{j=n+1}^{m} M^{(1)}\frac{L^j(t+\check{V})^j}{j!}\to0
$$
$\{X^{(n)}\}$ is Cauchy in the supremum norm and thus $X^{(n)}\xrightarrow{a.s.}X$ as $n\to\infty$. 
If there exists $Y_t$ also solving (SDE3), let $M_t=\max_{0\le s\le t}|X_s-Y_s|$, then 
$$
M_t\le M_t\frac{L^k(t+\check{V}_t)^k}{k!}\Longrightarrow M_t=0
$$
**QED**
```ad-thm
Suppose $\sigma\in C^2(\mathbb{R})$ with bounded 1st, 2nd derivatives and $b$ is Lipschitz continuous. Let $V^{(n)}$ be the same process in lemma. Let $W_t$ be the Brownian motion with 
$$
\lim_{n\to\infty}\sup_{0\le s\le t}\left|V^{(n)}_s-W_s\right|=0
$$
for $0\le t<\infty$. Then the sequence of solutions $\{X^{(n)}_t\}$ to the (SDE3), $X^{(n)}_t\xrightarrow{a.s.}X$ which satisfies
$$
X_t=\xi+\int_{0}^{t}b(X_s){d}s+\int_{0}^{t}\sigma(X_s)\circ{W_s}
$$
```
**Proof**
Consider the functions $u$ and $f$ in [[#^38d532|the result of Doss]]. Suppose the process $Y^{(n)}_t$ be the solution of the ODE, 
$$
\frac{dY^{(n)}_t}{dt}=f(V^{(n)}_t,Y^{(n)}_t)
$$
and we can define $X^{(n)}_t\triangleq u(V^{(n)}_t,Y^{(n)}_t)$. It suffices to show that the convergence of $Y^{(n)}_t\to Y$ which solves $\frac{dY_t}{dt}=f(W_t,Y_t)$ i.e. 
$$
\lim_{n\to\infty}\sup_{0\le s\le t}|Y^{(n)}_s-Y_s|=0
$$
If the convergence holds, we have 
$$
\begin{align}
|X^{(n)}_t-X_{t}|&=\left|u(V^{(n)}_t,Y_t^{(n)})-u(W_t,Y_t)\right|\\
&\le |u(V^{(n)}_t,Y_t^{(n)})-u(V^{(n)}_t,Y_t)|+|u(V^{(n)}_t,Y_t)-u(W_t,Y_t)|\\
&\le L|Y^{(n)}_s-Y_s|+\varepsilon
\end{align}
$$
Now we prove the claim. 
For fixed $\omega\in\Omega,t\ge0,k\in\mathbb{N}_+$, we choose $\varepsilon<e^{-L_kt}$. We define the stopping time 
$$
\tau_{k}(\omega)=t\wedge\inf\left\{0\le s\le t:|Y_s|\ge k-1\mbox{ or }W_s\ge k-1\right\}
$$
and 
$$
\tau_{k}^{(n)}=t\wedge \inf\left\{0\le s\le t:|Y^{(n)}_s|\ge k\right\}
$$
We choose $n$ sufficiently large s.t. 
$$
\left|f(V^{(n)}_s(\omega),Y_s(\omega))-f(W_s(\omega),Y_s(\omega))\right|\le \varepsilon^2
$$
and $|V^{(n)}_s|\le k$ holds for $s\in[0,\tau_k\wedge \tau_k^{(n)}]$. We have 
$$
\begin{align}
\left|\frac{d}{dt}(Y^{(n)}_t-Y_t)\right|&=\left|f(V^{(n)}_t,Y^{(n)}_t)-f(W_t,Y_t)\right|\\
&\le \left|f(V^{(n)}_t,Y^{(n)}_t)-f(W_t,Y^{(n)}_t)\right|+|f(W_t,Y^{(n)}_t)-f(W_t,Y_t)|\\
&\le L_k\left|Y^{(n)}_t-Y_t\right|+\varepsilon^2
\end{align}
$$
By [[#^5fc0f3|Gronwall's inequality]], we obtain 
$$
\left|Y^{(n)}_s-Y_s\right|\le \varepsilon^2e^{L_kt}<\varepsilon,\forall s\in[0,\tau_k\wedge \tau^{(n)}_k]
$$
The last inequality implies $\tau_k\le \tau^{(n)}_k$, let $n\to\infty$ and $\varepsilon\downarrow0$, we obtain 
$$
\lim_{n\to\infty}\sup_{0\le s\le \tau_{k}}|Y^{(n)}_s-Y_s|=0
$$
Let $k\to\infty$, $\tau_k=t$. 
**QED**

---
# Exercises
```ad-question
The stochastic equation $$ X_t = 3 \int_0^t X_s^{1/3} ds + 3 \int_0^t X_s^{2/3} dW_s $$ has uncountably many strong solutions of the form $$ X_t^{(\Theta)} = \begin{cases} 0; & 0 \le t < \beta_\Theta, \\ W_t^3; & \beta_\Theta \le t < \infty, \end{cases} $$ where $0 \le \Theta \le \infty$ and $\beta_\Theta \triangleq \inf\{s \ge \Theta; W_s = 0\}$. Note that the function $\sigma(x) = 3x^{2/3}$ satisfies condition (2.24), but the function $b(x) = 3x^{1/3}$ fails to satisfy the condition of Remark 2.16.
```

```ad-done
We check $X^{(\Theta)}_t$ is the solution of this SDE. 
$$
\begin{align}
&3\int_0^t (X_s^{(\Theta)})^{1/3} ds + 3 \int_0^t (X_s^{(\Theta)})^{2/3} dW_s\\
=&3\int_{\beta_{\Theta}}^t W_s ds + 3 \int_{\beta_\Theta}^t W_s^2 dW_s\\
=&W_t^3,t\ge\beta_{\Theta}\tag{Ito's rule}
\end{align}
$$
Note that 
$$
\begin{align}
|\sigma(x)-\sigma(y)|\le C|x-y|^{\frac{2}{3}}
\end{align}
$$
Take $h(u)=u^{\frac{2}{3}}$, we have 
$$
\int_{0}^{\varepsilon}u^{-\frac{4}{3}}d{u}=\infty,\forall\varepsilon>0
$$
$\sigma$ satisfies the Yamada & Watanabe condition. But for $b$,
$$
|b(x)-b(y)|\le C|x-y|^{\frac{1}{3}}
$$
Take $\kappa(u)=u^{\frac{1}{3}}$, we have 
$$
\int_{0}^{\varepsilon}u^{-\frac{2}{3}}<\infty,\forall\varepsilon>0
$$
The drift item $b$ doesn't have a good condition.
```

```ad-question
Suppose that the coefficients $\sigma: \mathbb{R} \to (0, \infty)$ and $b: \mathbb{R} \to \mathbb{R}$ are of class $C^2$ and $C^1$, respectively; that $b' - \frac{1}{2}\sigma\sigma'' - \frac{b\sigma'}{\sigma}$ is bounded; and that $1/\sigma$ is not integrable at either $\pm\infty$. Then (2.4)'' has a unique, strong solution $X$. (Hint: Consider the function $f(x) = \int_0^x \frac{du}{\sigma(u)}$ and apply Itô’s rule to $f(X_t)$.)
```

```ad-done

```

```ad-question
Suppose that in Proposition 2.18 we drop condition (v) but strengthen condition (iv) to $$ b_1(t, x) < b_2(t, x); \quad 0 \le t < \infty, x \in \mathbb{R}. $$ Then the conclusion (2.32) still holds. 
```

```ad-done

```

```ad-question
title:The Kramers-Smoluchowski Approximation; Nelson (1967)) 
Let $b(t, x): [0, \infty) \times \mathbb{R} \to \mathbb{R}$ be a continuous, bounded function which satisfies the Lipschitz condition (2.23), and for every finite $\alpha > 0$ consider the stochastic differential system $$ \begin{aligned} dX_t^{(\alpha)} &= Y_t^{(\alpha)} dt; & X_0^{(\alpha)} &= \xi \\ dY_t^{(\alpha)} &= \alpha b(t, X_t^{(\alpha)}) dt - \alpha Y_t^{(\alpha)} dt + \alpha dW_t; & Y_0^{(\alpha)} &= \eta, \end{aligned} $$ where $\xi, \eta$ are a.s. finite random variables, jointly independent of the Brownian motion $W$. 
1. This system admits a unique, strong solution for every value of $\alpha \in (0, \infty)$.
2. For every fixed, finite $T > 0$, we have $$ \lim_{\alpha \to \infty} \sup_{0 \le t \le T} |X_t^{(\alpha)} - X_t| = 0, \quad \text{a.s.}, $$ where $X$ is the unique, strong solution to (2.34).
```

```ad-done
title:Done for 1
Suppose $Z_t^{(\alpha)}=\left(X^{(\alpha)}_t,Y^{(\alpha)}_t\right)$, and 
$$
A^{(\alpha)}_t=\begin{bmatrix}
Y^{(\alpha)}_t\\
\alpha b(t,X^{(\alpha)}_t)-\alpha Y^{(\alpha)}_t
\end{bmatrix}, B^{(\alpha)}_t=\begin{bmatrix}
0\\
\alpha
\end{bmatrix}
$$
Then we obtain the 2-dimensional SDE
$$
dZ_t^{(\alpha)}=A^{(\alpha)}_t{d}t+B^{(\alpha)}_t{d}W_t
$$
We check the Lipschitz condition of $A^{(\alpha)}_t$, 
$$
\begin{align}
\left|A^{(\alpha)}(t,Z_1)-A^{(\alpha)}(t,Z_2)\right|&=\left|\begin{bmatrix}
Y^{(\alpha,1)}_t-Y^{(\alpha,2)}_t\\
\alpha(b(t,X^{(\alpha,1)}_t)-b(t,X^{(\alpha,2)}))-\alpha(Y^{(\alpha,1)}_t-Y^{(\alpha,2)}_t)
\end{bmatrix}\right|\\
&\le L\alpha|X^{(\alpha,1)}-X^{(\alpha,2)}|+(\alpha+1)|Y^{(\alpha,1)}-Y^{(\alpha,2)}|
\end{align}
$$
Since $B^{(\alpha)}_t$ is constant, the all conditions are satisfied. By [[#^d1379b|E&U theorem of SDE]], this SDE exists unique solution for $\alpha\in(0,\infty)$. 
```

```ad-done
title:Done for 2
We can solve $Y^{(\alpha)}_t$, 
$$
\begin{align}
Y^{(\alpha)}_t=e^{-\alpha t}\eta +\alpha\int_{0}^{t}e^{-\alpha(t-s)}b(s,X^{\alpha}_s){d}s+\alpha\int_{0}^{t}e^{-\alpha(t-s)}{d}W_s
\end{align}
$$
and 
$$
\begin{align}
X_t^{(\alpha)}&=\xi+\int_{0}^{t}Y^{(\alpha)}_s{d}s\\
&=\xi+\frac{\eta}{\alpha}(1-e^{-\alpha t})+\alpha\int_{0}^{t}\int_{0}^{r}e^{-\alpha(r-s)}b(s,X^{(\alpha)}_s){d}s{d}r+\alpha\int_{0}^{t}\int_{0}^{r}e^{-\alpha(r-s)}{d}W_s{d}r\\
&=\xi+\frac{\eta}{\alpha}(1-e^{-\alpha t})+\int_{0}^{t}(1-e^{-\alpha(t-s)})b(s,X^{(\alpha)}_s){d}s+\int_{0}^{t}(1-e^{-\alpha(t-s)}){d}W_s
\end{align}
$$
Since $X_t$ solve 
$$
X_t=\xi+\int_{0}^{t}b(s,X_s){s}+W_t
$$
We have 
$$
\begin{align}
\left|X^{(\alpha)}_t-X_t\right|\le L\int_{0}^{t}|X^{(\alpha)}_s-X_s|{d}s+o(1)\xRightarrow{Gronwall}\sup_{0\le t\le T}|X^{(\alpha)}_t-X_t|\to0
\end{align}
$$
```

```ad-question
Solve explicitly the one-dimensional equation $$ dX_t = \left( \sqrt{1 + X_t^2} + \frac{1}{2} X_t \right) dt + \sqrt{1 + X_t^2} dW_t. $$ 
```

```ad-done

```

```ad-question
1. Suppose that there exists an $\mathbb{R}^d$-valued function $u(t, y) = (u_1(t, y), \dots, u_d(t, y))$ of class $C^{1,2}([0, \infty) \times \mathbb{R}^d)$, such that $$ \frac{\partial u_i}{\partial t}(t, y) = b_i(t, u(t, y)), \quad \frac{\partial u_i}{\partial y_j}(t, y) = \sigma_{ij}(t, u(t, y)); \quad 1 \le i, j \le d $$ hold on $[0, \infty) \times \mathbb{R}^d$, where each $b_i(t, x)$ is continuous and each $\sigma_{ij}(t, x)$ is of class $C^{1,2}$ on $[0, \infty) \times \mathbb{R}^d$. 
   Show then that the process $$ X_t \triangleq u(t, W_t); \quad 0 \le t < \infty, $$ where $W$ is a $d$-dimensional Brownian motion, solves the Fisk-Stratonovich equation $$ dX_t = b(t, X_t) dt + \sigma(t, X_t) \circ dW_t. $$
2. Use the above result to find the unique, strong solution of the one-dimensional Itô equation 
$$ dX_t = \left[ \frac{2}{1 + t} X_t - a(1 + t)^2 \right] dt + a(1 + t)^2 dW_t; \quad 0 \le t < \infty.$$
```

```ad-done
title:Done for 1
By the Ito's rule,
$$
\begin{align}
X_t&=u(t,W_t)=\int_{0}^{t}\frac{\partial u(s,W_s)}{\partial s}\cdot{d}s+\int_{0}^{t}\nabla_xu\cdot{d}W_s+\frac{1}{2}\int_{0}^{t}\left(\frac{\partial^2u_i}{\partial x_j^2}\right){d}s\\
&=\sum_{i=1}^{d}\int_{0}^{t}b_i(s,X_s){d}s+\frac{1}{2}\sum_{i=1}^{d}\sum_{j=1}^{d}\int_{0}^{t}\sigma_{ij}(s,X_s)\sigma'_{ij}(s,X_s){d}s+\int_{0}^{t}\sigma(s,X_{s}){d}W_s\\
&=\int_{0}^{t}b(s,X_s){d}s+\int_{0}^{t}\sigma(s,X_s)\circ{d}W_s
\end{align}
$$
```

```ad-done
title:Done for 2
We write $b(t,x)=\frac{2}{1+t}x-a(1+t)^2$ and $\sigma(t,x)=a(1+t)^2$. we have 
$$
\begin{cases}
\frac{\partial u}{\partial t}=\frac{2}{1+t}u-a(1+t)^2\\
\frac{\partial u}{\partial x}=a(1+t)^2
\end{cases}
$$
By solving the second equation, we obtain $u(t,x)=a(1+t)^2x+C(t)$ and thus 
$$
\begin{align}
&\frac{\partial u}{\partial t}=2a(1+t)x+C'(t)=2a(1+t)x+\frac{2C(t)}{1+t}-a(1+t)^2\\
\Longrightarrow&C'(t)=\frac{2}{1+t}C(t)-a(1+t)^2
\end{align}
$$
$u(0,x)=ax=ax+C(0)\Longrightarrow C(0)=0$, we obtain an ODE, 
$$
\begin{cases}
C'(t)=\frac{2}{1+t}C(t)-a(1+t)^2\\
C(0)=0
\end{cases}\Longrightarrow C(t)=-at(1+t)^2
$$
Then we have 
$$
u(t,x)=a(1+t)^2(x-t)
$$
and thus $X_t=u(t,W_t)=a(1+t)^2(W_t-t)$. 
```
