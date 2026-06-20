# Brownian Motion in Several Dimensions
```ad-def
title:d-dimensional Brownian motion
Let $d\in\mathbb{N}_+$ and $\mu$ a probability measure on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$. Let $\symbf{B}_t$ be a continuous, adapted process with value in $\mathbb{R}^d$, defined on some probability space $(\Omega,\mathcal{F},\mathbb{P})$. The process is called **d-dimensional Brownian motion with initial distribution $\mu$** if
1. $\mathbb{P} [\symbf{B}_0\in \Gamma]=\mu(\Gamma),\forall\Gamma\in \mathcal{B}(\mathbb{R}^d)$
2. For $0\le s<t$, $\symbf{B}_t-\symbf{B}_s\sim N_d(\symbf{0},(t-s)I_{d})$ and independent of $\mathcal{F}_s$ where $I_d$ is $d\times d$ identity matrix.
```

```ad-note
title:No.1 way to construct $d$-dimensional Brownian motion(Product Space)
Let $X(\omega_0)=\omega_0$ be the identity random variable on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d),\mu)$. For $i=1,\cdots,d$, $B^{(i)}_t$ is a standard, one-dimensional Brownian motion on some $(\Omega_i,\mathcal{F}_i,\mathbb{P}_i)$. On the product space
$$
(\mathbb{R}^d\times\Omega_1\times\cdots\times\Omega_d,\mathcal{B}(\mathbb{R}^d)\otimes\mathcal{F}_1\otimes\cdots\otimes\mathcal{F}_d,\mu\times\mathbb{P}_1\times\cdots\times\mathbb{P}_d)
$$
We define
$$
\symbf{B}_t(\omega)=X(\omega_0)+(B^{(1)}_t(\omega_1),\cdots,B^{(d)}_t(\omega_d))
$$
```

```ad-note
title:No.2 way to construct $d$-dimensional Brownian motion(Markov family)
For $i=1,\cdots,d$, let $\mathbb{P}_i$ be Wiener measure on $(C[0,\infty),\mathcal{B}(C[0,\infty)))$. Then d-dimensional Wiener measure is $\mathbb{P}_0=\mathbb{P}_1\times\cdots\times\mathbb{P}_d$ on $(C[0,\infty)^d,\mathcal{B}(C[0,\infty)^d))$. Under $\mathbb{P}_0$, the coordinate mapping process $B_t(\omega) \triangleq \omega(t)$ together with the filtration $\mathcal{F}^B_t$ is a d-dimensional Brownian motion starting at the origin. For $x\in\mathbb{R}^d$, we define the probability measure $\mathbb{P}^x$ on $(C[0,\infty)^d,\mathcal{B}(C[0,\infty)^d))$:
$$
\mathbb{P}^x=\mathbb{P}(F-x),F\in\mathcal{B}(C[0,\infty)^d)
$$
where $F-x=\{\omega\in C[0,\infty)^d: \omega+x\in F\}$. 
We claim **the mapping $x\mapsto\mathbb{P}^x(F)$ is $\mathcal{B}(\mathbb{R}^d)/\mathcal{B}([0,1])$-measurable**.
**Proof**
Finally, , for a probability measure $\mu$ on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$, we define $\mathbb{P}^{\mu}$ on $\mathcal{B}(C[0,\infty)^d)$ by 
$$
\mathbb{P}^{\mu}(F)=\int_{\mathbb{R}^d}\mathbb{P}^x(F)d\mu
$$
```

^de6b55

```ad-proposition
Under $\mathbb{P}^x$, the coordinate mapping process $\symbf{B}_t=\omega(t)$ on $(C[0,\infty)^d,\mathcal{B}(C[0,\infty)^d),\mathbb{P}^\mu)$) is a d-dimensional Brownian motion with initial distribution $\mu$.
```
**Proof**

**QED**
```ad-def
title:Universally measurable
Given a metric space $(S, \rho)$, we denote $\overline{\mathcal{B}(S)}_\mu$ be the completion of $\mathcal{B}(S)$ under the finite measure $\mu$ on $(S,\mathcal{B}(S))$.
The **universal $\sigma$-algebra** is $\mathscr{U}(S)\triangleq\bigcap_{\mu}\overline{\mathcal{B}(S)}_\mu$. A $\mathscr{U}(S)/\mathcal{B}(\mathbb{R})$-measurable, real-valued function is said to be **universally measurable**.
```

```ad-def
title:d-dimensional Brownian family
$\symbf{B}_t$ on a measurable space $(\Omega,\mathcal{F})$ and family of probability measure $\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ s.t.
1. For $F\in\mathcal{F}$, $x\mapsto\mathbb{P}^x(F)$ is universally measurable
2. For each $x\in\mathbb{R}^d$, $\mathbb{P}^x(B_0=x)=1$
3. Under each $\mathbb{P}^x$, the process $\symbf{B}$ is d-dimensional Brownian motion starting at $x$
```
# Markov Processes and Markov Families
```ad-def
title:Markov process
Let $d\in\mathbb{N}_+$ and $\mu$ a probability measure on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$. An adapted, d-dimensional process $\symbf{X}_t$ on some probability space $(\Omega,\mathcal{F},\mathbb{P}^\mu)$ is said to be a **Markov process** with initial distribution $\mu$ if
1. $\mathbb{P}^\mu(\symbf{X}_0\in\Gamma)=\mu(\Gamma),\Gamma\in\mathcal{B}(\mathbb{R}^d)$
2. For $s,t\ge0$ and $\Gamma\in\mathcal{B}(\mathbb{R}^d)$,
   $$
   \mathbb{P}^\mu(\symbf{X}_{t+s}\in\Gamma|\mathcal{F}_s)=\mathbb{P}^\mu(\symbf{X}_{t+s}\in\Gamma|\symbf{X}_s)
   $$ 
```

```ad-def
title:Markov family
Let $d\in\mathbb{N}_+$ and $\mu$ a probability measure on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$. An adapted, d-dimensional process $\symbf{X}_t$ on some $(\Omega,\mathcal{F})$ together with a family of probability measures $\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ on $(\Omega,\mathcal{F})$ s.t.
1. For $F\in\mathcal{F}$, $x\mapsto\mathbb{P}^x(F)$ is universally measurable
2. For each $x_0\in \mathbb{R}^d$, $\mathbb{P}^x(\symbf{X}_0=x)=1$
3. For $x_0\in \mathbb{R}^d,s,t\ge0$ and $\Gamma\in\mathcal{B}(\mathbb{R}^d)$,
   $$
   \mathbb{P}^x[\symbf{X}_{t+s}\in \Gamma|\mathcal{F}_s]=\mathbb{P}^x[\symbf{X}_{t+s}\in \Gamma|\symbf{X}_s]
   $$
4. For $x_0\in \mathbb{R}^d,s,t\ge0$ and $\Gamma\in\mathcal{B}(\mathbb{R}^d)$,
   $$
   \mathbb{P}^x[\symbf{X}_{t+s}\in\Gamma|\symbf{X}_s=y]=\mathbb{P}^y[\symbf{X}_t\in\Gamma]
   $$
```

^7d7413

```ad-proposition
If $X$ and $Y$ are $d$-dimensional random vectors on $(\Omega, \mathscr{F}, P)$, $\mathscr{G}$ is a sub-$\sigma$-field of $\mathscr{F}$, $X$ is independent of $\mathscr{G}$ and $Y$ is $\mathscr{G}$-measurable, then for every $\Gamma \in \mathscr{B}(\mathbb{R}^d)$: $$ \quad P[X + Y \in \Gamma \mid \mathscr{G}] = P[X + Y \in \Gamma \mid Y], \quad \text{a.s. } P; $$ $$  \quad P[X + Y \in \Gamma \mid Y = y] = P[X + y \in \Gamma], \quad \text{for } P_Y\text{-a.e. } y \in \mathbb{R}^d$$
```
**Proof**

**QED**

```ad-thm
title:Markov property of Brownian motion
1. A d-dimensional Brownian motion is a Markov process. 
2. A d-dimensional Brownian family is a Markov family.
```
**Proof**

**QED**
# Equivalent Formulations of the Markov Property
```ad-def
title:Transfer semigroup operator
An adapted process $\symbf{X}_t$ and a family of probability measures $\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ s.t. condition1 of Markov family is satisfied. We define operators $\{U_t\}_{t\ge0}$ s.t. 
$$
U_t:\mathcal{B}(\mathbb{R}^{[0,\infty)})\to\mathscr{U}(\mathbb{R}^{[0,\infty)}),(U_tf)(x)\triangleq\mathbb{E}^x(f(X_t))
$$
If $f=\mathbb{1}_{\Gamma},\Gamma\in\mathcal{B}(\mathbb{R}^d)$, $(U_tf)(x)=\mathbb{P}^x[X_t\in\Gamma]$. The universal measurability of $U_tf$ follows directly from Markov family for an arbitrary, Borel-measurable function $f$, the universal measurability of $U_tf$ is then a consequence of the BCT.
```

```ad-proposition
Condition 3 and 4 of [[#^7d7413|Markov family]] can be replace by:
1. For $x\in\mathbb{R}^d,s,t\ge0$ and $\Gamma\in\mathcal{B}(\mathbb{R}^d)$,
   $$
   \mathbb{P}^x[X_{s+t}\in\Gamma|\mathcal{F}_s]=(U_t\mathbb{1}_{\Gamma})(X_s)
   $$
```

^dd4132

**Proof**
$\Longrightarrow$: Suppose condition 3 and 4 hold. We have 
$$
\mathbb{P}^x[X_{s+t}\in\Gamma|X_s=y]=\mathbb{P}^y[X_{t}\in\Gamma]=(U_t\mathbb{1}_{\Gamma})(y)
$$
Since $U_t\mathbb{1}_\Gamma$ is universally measurable, by [[#^80a218|Exercise]], there exists Borel-measurable function $g:\mathbb{R}^d\to[0,1]$ s.t. 
$$
U_t\mathbb{1}_\Gamma(y)=g(y),a.s.-\mathbb{P}^xX^{-1}_s,y\in\mathbb{R}^d
$$
and 
$$
U_t\mathbb{1}_\Gamma(X_s)=g(X_s),a.s.-\mathbb{P}^x\Longrightarrow\mathbb{P}^x[X_{s+t}\in\Gamma|X_s]=U_t\mathbb{1}_{\Gamma}(X_s)
$$
Br condition 3, $\mathbb{P}^x[X_{s+t}\in\Gamma|\mathcal{F}_s]=\mathbb{P}^x[X_{s+t}\in\Gamma|X_s]=U_t\mathbb{1}_{\Gamma}(X_s)$.
$\Longleftarrow$: Suppose $\mathbb{P}^x[X_{s+t}\in\Gamma|\mathcal{F}_s]=(U_t\mathbb{1}_{\Gamma})(X_s)$ holds. By above direction, we have 
$$
\mathbb{P}^x[X_{s+t}\in\Gamma|\mathcal{F}_s]=(U_t\mathbb{1}_{\Gamma})(X_s)=g(X_s)
$$
Since $\mathbb{P}^x[X_{s+t}\in\Gamma|\mathcal{F}_s]$ is a $\sigma(X_s)$-measurable version, then we have $\mathbb{P}^x[X_{s+t}\in\Gamma|\mathcal{F}_s]=\mathbb{P}^x[X_{s+t}\in\Gamma|X_s]$. Since $\mathbb{P}^x[X_{s+t}\in\Gamma|X_s=y]=g(y)$, then we have $\mathbb{P}^x[X_{s+t}\in\Gamma|X_s=y]=(U_t\mathbb{1}_\Gamma)(y)=\mathbb{P}^y[X_t\in \Gamma]$.
**QED**
```ad-note
We denote $X_{s+\cdot}(\omega)$ as the mapping $t\mapsto X_{s+t}(\omega)$ for $\omega\in\Omega$ and thus is measurable $(\Omega,\mathcal{F})\to((\mathbb{R}^d)^{[0,\infty)},\mathcal{B}((\mathbb{R}^d)^{[0,\infty)}))$
```

^9d4ff3

```ad-proposition
For a Markov family $X_t,(\Omega,\mathcal{F}),\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$, we have 
1. For $x\in\mathbb{R}^d,s\ge0$ and $F\in\mathcal{B}((\mathbb{R}^d)^{[0,\infty)})$,
   $$
   \mathbb{P}^x[X_{s+\cdot}\in F|\mathcal{F}_s]=\mathbb{P}^x[X_{s+\cdot}\in F|X_s]
   $$
2. For $x\in\mathbb{R}^d,s\ge0$ and $F\in\mathcal{B}((\mathbb{R}^d)^{[0,\infty)})$,
   $$
   \mathbb{P}^x[X_{s+\cdot}\in F|X_s=y]=\mathbb{P}^y[X_{\cdot}\in F]
   $$
```

^ee3a2f

**Proof**
Let $\mathscr{D}=\{F\in\mathcal{B}(\mathbb{R}^d)^{[0,\infty)}:F\mbox{ holds condition 1 and 2}\}$ be a Dynkin system. For $\Gamma\in \mathcal{B}(\mathbb{R}^d)$ and $F=\{\omega\in(\mathbb{R}^d)^{[0,\infty)}:\omega(t)\in\Gamma\}$, we W.T.S $F$ has the follow form by [[Kolmogorov's Construction of Brownian Motion#^273f1e|Dynkin system theorem]], 
$$
F=\{\omega:\omega(t_0)\in\Gamma_0,\cdots,\omega(t_n)\in\Gamma_n\},\Gamma_i\in\mathcal{B}(\mathbb{R}^d),\mathscr{C}=\{\mbox{such }F\}
$$
$\mathscr{C}$ is a $\pi$-system, then $\mathcal{B}(\mathbb{R}^d)^{[0,\infty)}=\sigma(\mathscr{C})\subseteq\mathscr{D}$. The condition 1 becomes 
$$
\mathbb{P}^x[X_s\in\Gamma_0,\cdots,X_{s+t_n}\in\Gamma_n|\mathcal{F}_s]=\mathbb{P}^x[X_s\in\Gamma_0,\cdots,X_{s+t_n}\in\Gamma_n|X_s]
$$
We prove the claim by induction of $n$. For $n=0$, it holds trivially. Assume it is true for $n-1$ i.e. 
$$
\mathbb{P}^x[X_s\in\Gamma_0,\cdots,X_{s+t_{n-1}}\in\Gamma_{n-1}|\mathcal{F}_s]=\mathbb{P}^x[X_s\in\Gamma_0,\cdots,X_{s+t_{n-1}}\in\Gamma_{n-1}|X_s]
$$
But we use another consequence of this assumption i.e. for any bounded Borel measurable function $\varphi:\mathbb{R}^{dn}\to\mathbb{R}$, we have 
$$
\mathbb{E}^x[\varphi(X_s,\cdots,X_{s+t_{n-1}})|\mathcal{F}_s]=\mathbb{E}^x[\varphi(X_s,\cdots,X_{s+t_{n-1}})|X_s]
$$
Note that
$$
\begin{align}
&\mathbb{P}^x[X_s\in\Gamma_0,\cdots,X_{s+t_n}\in\Gamma_n|\mathcal{F}_s]\\
=&\mathbb{E}^x[\mathbb{1}_{\{X_s\in\Gamma_0,\cdots,X_{s+t_{n-1}}\in\Gamma_{n-1}\}}\mathbb{P}^x(X_{s+t_n}\in\Gamma_n|\mathcal{F}_{s+t_{n-1}})|\mathcal{F}_s]\\
=&\mathbb{E}^x[\mathbb{1}_{\{X_s\in\Gamma_0,\cdots,X_{s+t_{n-1}}\in\Gamma_{n-1}\}}\mathbb{P}^x(X_{s+t_n}\in\Gamma_n|X_{s+t_{n-1}})|\mathcal{F}_s]
\end{align}
$$
There exists a Borel-measurable function $g:\mathbb{R}^d\to9[0,1]$ s.t. $\mathbb{P}^x(X_{s+t_n}\in\Gamma_n|X_{s+t_{n-1}})=g(X_{s+t_{n-1}})$. We take 
$$
\varphi(x_0,\cdots,x_{n-1})=\mathbb{1}_{\Gamma_0}(x_0)\cdots\mathbb{1}_{\Gamma_{n-1}}(x_{n-1})g(x_{n-1})
$$
By induction, 
$$
\begin{align}
&\mathbb{P}^x[X_s\in\Gamma_0,\cdots,X_{s+t_n}\in\Gamma_n|\mathcal{F}_s]\\
=&\mathbb{E}^x[\mathbb{1}_{\{X_s\in\Gamma_0,\cdots,X_{s+t_{n-1}}\in\Gamma_{n-1}\}}\mathbb{P}^x(X_{s+t_n}\in\Gamma_n|X_{s+t_{n-1}})|\mathcal{F}_s]\\
=&\mathbb{E}^x[\mathbb{1}_{\{X_s\in\Gamma_0,\cdots,X_{s+t_{n-1}}\in\Gamma_{n-1}\}}g(X_{s+t_{n-1}})|\mathcal{F}_s]\\
=&\mathbb{E}^x[\varphi(X_s,\cdots,X_{s+t_{n-1}})|\mathcal{F}_s]\\
=&\mathbb{E}^x[\varphi(X_s,\cdots,X_{s+t_{n-1}})|X_s]\\
=&\mathbb{E}^x[\mathbb{1}_{\{X_s\in\Gamma_0,\cdots,X_{s+t_{n-1}}\in\Gamma_{n-1}\}}\mathbb{P}^x(X_{s+t_n}\in\Gamma_n|X_{s+t_{n-1}})|X_s]\\
=&\mathbb{P}^x[X_s\in\Gamma_0,\cdots,X_{s+t_n}\in\Gamma_n|X_s]
\end{align}
$$ 
**QED**
```ad-def
title:Shift operator
A family operators $\theta_s:\Omega\to\Omega,s\ge0$ s.t. $\theta_s$ is $\mathcal{F}/\mathcal{F}$-measurable and 
$$
X_{s+t}(\omega)=X_t(\theta_s\omega),\forall\omega\in\Omega,s,t\ge0
$$
```

```ad-example
Let $\Omega=(\mathbb{R}^d)^{[0,\infty)}$, $\mathcal{F}$ is the smallest $\sigma$-algebra containing all finitedimensional cylinder sets, and $X$ is the coordinate mapping process $X_t(\omega)=\omega(t)$. We can define $\theta_s(\omega)(\cdot)=\omega(s+\cdot)$ i.e. $(\theta_s\omega)(t)=\omega(s+t)$. It is equivalent to move the axis.
![[Pasted image 20260411150051.png]]
```

```ad-example
By shift operator, we can rewrite the [[#^9d4ff3|notation]]. $X_{s+\cdot}(\omega)=X_{\cdot}(\theta_s(\omega))$. For $F\subseteq\mathcal{B}((\mathbb{R}^d))^{[0,\infty)}$, then $\{X_{s+\cdot}\in F\}=\theta^{-1}\{X_\cdot\in F\}$. Hence, we can replace the condition of [[#^ee3a2f|proposition]] by shift operator.
```

```ad-proposition
Let $X_t$ be an adapted process on a measurable space $(\Omega,\mathcal{F})$, $\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ be a family of probability measures on $(\Omega,\mathcal{F})$ and $\{\theta_s\}_{s\ge0}$ be shift operator. Then $X_t,(\Omega,\mathcal{F}),\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ is a Markov family if and only if the follow conditions hold.
1. For $F\in\mathcal{F}$, $x\mapsto\mathbb{P}^x(F)$ is universally measurable
2. For each $x_0\in \mathbb{R}^d$, $\mathbb{P}^x(\symbf{X}_0=x)=1$
3. For every $F\in\mathcal{F}^X_\infty$ and $s\ge0$, 
   $$
   \mathbb{P}^x[\theta^{-1}_s(F)|\mathcal{F}_s]=\mathbb{P}^{X_s}(F)
   $$
```

```ad-def
title:d-dimensional Brownian motion with drift
Let $\symbf{B}_t,(\Omega,\mathcal{F}),\mathbb{P}^x$ be a d-dimensional Brownian family. If $\mu\in\mathbb{R}^d$ and $\sigma\in \mathcal{L}(\mathbb{R}^d,\mathbb{R}^d)$ the space of linear transformation from $\mathbb{R}^d$ to $\mathbb{R}^d$ are constant and $\sigma$ is nonsingular, let $\symbf{Y}_t\triangleq\mu t+\sigma\symbf{B}_t$
```

```ad-def
title:Poisson family
A Poisson family with intensity $\lambda > 0$ is a process $N_t$ on a measurable space $(\Omega,\mathcal{F})$ and a family of probability measures $\{\mathbb{P}^x\}_{x\in\mathbb{R}}$, such that
1. For $E\in\mathcal{F}$, the mapping $x\mapsto \mathbb{P}^x(E)$ is universally measurable
2. For $x\in\mathbb{R}^d$, $\mathbb{P}^x[N_0=x]=1$
3. Under $\mathbb{P}^x$, $\tilde{N}=N_t-N_0$ is a Poisson process with intensity $\lambda$.
```

^65e528

---
# Exercises
```ad-question
Let $\{B_t = (B_t^{(1)}, \dots, B_t^{(d)}), \mathscr{F}_t; \, 0 \le t < \infty\}$ be a $d$-dimensional Brownian motion. Show that the processes $$ M_t^{(i)} \triangleq B_t^{(i)} - B_0^{(i)}, \quad \mathscr{F}_t; \quad 0 \le t < \infty,\; 1 \le i \le d $$ are continuous, square-integrable martingales, with $\langle M^{(i)}, M^{(j)} \rangle_t = t \delta_{ij}$ for $1 \le i, j \le d$. Furthermore, the vector of martingales $M = (M^{(1)}, \dots, M^{(d)})$ is independent of $\mathscr{F}_0$.
```

^6066df

```ad-question
Let $(S, \rho)$ be a metric space and let $f$ be a real-valued function defined on $S$. Show that $f$ is universally measurable if and only if for every finite measure $\mu$ on $(S, \mathscr{B}(S))$, there exists a Borel-measurable function $g_\mu \colon S \to \mathbb{R}$ such that $$ \mu\big(\{x \in S : f(x) \ne g_\mu(x)\}\big)=0$$
```

^80a218
```ad-question
Suppose that $X$, $(\Omega, \mathscr{F})$, $\{P^x\}_{x \in \mathbb{R}^d}$ is a Markov family with shift-operators $\{\theta_s\}_{s \ge 0}$. Use (c'') to show that for every $x \in \mathbb{R}^d$, $s \ge 0$, $G \in \mathscr{F}_s$ and $F \in \mathscr{F}_\infty^x$, 
$$ P^x\bigl[ G \cap \theta_s^{-1} F \mid X_s \bigr] = P^x\bigl[ G \mid X_s \bigr] \, P^x\bigl[ \theta_s^{-1} F \mid X_s \bigr], \quad P^x\text{-a.s.} 
$$ 
We may interpret this equation as saying that the 'past' $G$ and the 'future' $\theta_s^{-1}F$ are conditionally independent, given the 'present' $X_s$. Conversely, show that (c'') implies (c').
```

```ad-question
Suppose $X = \{X_t, \mathscr{F}_t;\, t \ge 0\}$ is a Markov process on $(\Omega, \mathscr{F}, P)$, and $\varphi \colon [0,\infty) \to \mathbb{R}^d$ and $\Psi \colon [0,\infty) \to L(\mathbb{R}^d, \mathbb{R}^d)$, the space of linear transformations from $\mathbb{R}^d$ to $\mathbb{R}^d$, are given (nonrandom) functions with $\varphi(0) = 0$ and $\Psi(t)$ nonsingular for every $t \ge 0$. Set $Y_t = \varphi(t) + \Psi(t) X_t$. Then $Y = \{Y_t, \mathscr{F}_t;\, t \ge 0\}$ is also a Markov process.
```

```ad-question
Construct a martingale which is not a Markov process.
```

```ad-question
Show that a Poisson family with intensity $\lambda > 0$ is a Markov family. Show furthermore that, in the notation of Definition~5.20 and under any $P^x$, the $\sigma$-fields $\mathscr{F}_\infty^{\tilde{N}}$ and $\mathscr{F}_0$ are independent.
```