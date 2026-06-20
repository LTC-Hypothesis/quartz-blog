# The Reflection Principle
```ad-def
title:Passage time
For $b\in\mathbb{R}$, we define
$$
T_b(\omega)=\inf\{t\ge0:B_t=b\}
$$
For continuous process, we obtain $T_b$ is a [[Stopping Times#^5ea1fe|stopping time]]. 
```

^cdb697

Our goal is to calculate the distribution of $T_b$ i.e. $\mathbb{P}(T_b<t)$. But in this section we only show the heuristic proof. 
```ad-note
title:Heuristic proof
Suppose $B_t$ is a standard, one-dimensional Brownian motion on $(\Omega,\mathcal{F},\mathbb{P}^0)$. For $b\in\mathbb{R}$, we have 
$$
\begin{align}
\mathbb{P}^0(T_b<t)=\mathbb{P}^0(B_t\ne b)=\mathbb{P}^0(T_b<t,B_t>b)+\mathbb{P}^0(T_b<t,B_t<b)
\end{align}
$$
The technique is that we calculate **the distribution of process**, which is usual by **the dual relationship** between stopping time and process. 
For the first item, since $B_t$ is continuous, by the **intermediate value theorem**, we have $\{B_t>b\}\subseteq\{T_b<t\}$, then $\mathbb{P}^0(T_b<t,B_t>b)=\mathbb{P}(B>b)$. 
For the second item, it seem to be stuck. Therefore, we should introduce the idea of the **Reflection Principle**. Any Brownian path that hits level $b$ before time $t$ and ends below $b$ has a symmetric "shadow path" that ends above $b$ with equal likelihood, leading to
$$
\mathbb{P}^0(T_b<t,B_t<b)=\mathbb{P}^0(T_b<t,B_t>b)=\mathbb{P}^0(B_t>b)
$$
![[Pasted image 20260413104805.png]]
Then we obtain
$$
\begin{align}
\mathbb{P}^0(T_b<t)=2\mathbb{P}^0(B_t>b)=\sqrt{\frac{2}{\pi}}\int_{\frac{b}{\sqrt{t}}}^{\infty}e^{-\frac{x^2}{2}}{d}s
\end{align}
$$
And we claim $B_{t+T_b}-B_{T_b}$ is also a Brownian motion. If $T_b=constant$, the claim holds. But if $T_b$ is any random time, the claim is not true.
```

^9087d3

We have the example
```ad-example

```
# Strong Markov Processes and Families
```ad-def
title:Strong Markov process
Let $d\in\mathbb{N}_+$ and $\mu$ is a probability measure on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$. ). A progressively measurable, d-dimensional process $\symbf{X}_t$ on $(\Omega,\mathcal{F},\mathbb{P}^\mu)$ is said to be a **strong Markov process** with initial distribution $\mu$ if
1. $\mathbb{P}^{\mu}(\symbf{X}_0\in \Gamma)=\mu(\Gamma),\forall\Gamma\in\mathcal{B}(\mathbb{R}^d)$
2. For any optional time $S$ of $\mathcal{F}$, $t\ge0,\Gamma\in\mathcal{B}(\mathbb{R}^d)$
   $$
   \mathbb{P}^\mu(\symbf{X}_{S+t}\in\Gamma|\mathcal{F}_{S+})=\mathbb{P}^\mu(\symbf{X}_{S+t}\in\Gamma|\symbf{X}_{S})
   $$
```

```ad-def
title:Strong Markov family
Let $d\in\mathbb{N}_+$ and $\mu$ is a probability measure on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$. ). A progressively measurable, d-dimensional process $\symbf{X}_t$ on $(\Omega,\mathcal{F},\mathbb{P}^\mu)$ together with $\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ on $(\Omega,\mathcal{F})$ s.t. 
1. For $F\in\mathcal{F}$, the mapping $x\mapsto\mathbb{P}^x(F)$ is universally measurable
2. $\mathbb{P}^x[\symbf{X}_0=x]=1.\forall x\in\mathbb{R}^d$
3. For $x\in\mathbb{R}^d,t\ge0,\Gamma\in\mathcal{B}(\mathbb{R}^d)$ and any optional time $S$,
   $$
   \mathbb{P}^x(\symbf{X}_{S+t}\in\Gamma|\mathcal{F}_{S+})=\mathbb{P}^x(\symbf{X}_{S+t}\in\Gamma|\symbf{X}_{S})
   $$
4. For $x\in\mathbb{R}^d,t\ge0,\Gamma\in\mathcal{B}(\mathbb{R}^d)$ and any optional time $S$,
   $$
   \mathbb{P}^x(\symbf{X}_{S+t}\in\Gamma|\symbf{X}_S=y)=\mathbb{P}^y(\symbf{X}_{t}\in\Gamma)
   $$
```

^a2b026

```ad-warning
1. $\{X_{S+t}\in\Gamma\}\triangleq\{S<\infty,X_{S+t}\in\Gamma\}$ and $\mathbb{P}^x\symbf{X}^{-1}_S(\mathbb{R}^d)=\mathbb{P}^x(S<\infty)$.
2. $\mathbb{P}^\mu[X_{S+t}\in\Gamma|\mathcal{F}_{S+}]=\mathbb{P}^\mu[X_{S+t}\in \Gamma|X_S]=0$ on $\{S=\infty\}$
3. If $S$ is a stopping time, then $X_S$ is $\mathcal{F}_S$-measurable and we can take conditional expectation with respect to $\mathcal{F}_S$. 
4. Every strong Markov family is a Markov family. Likewise, every strong Markov process is a Markov process. However, not every Markov family enjoys the strong Markov property
```

```ad-proposition
For a strong Markov family $X_t,(\Omega,\mathcal{F}),\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$, we have 
1. For $x\in\mathbb{R}^d$, $F\in\mathcal{B}(\mathbb{R}^d)^{[0,\infty)}$ and any optional time $S$ of $\mathcal{F}_t$,
   $$
   \mathbb{P}^x[X_{S+\cdot}\in F|\mathcal{F}_{S+}]=\mathbb{P}^x[X_{S+\cdot}\in F|X_{S}]
   $$
2. For $x\in\mathbb{R}^d$, $F\in\mathcal{B}(\mathbb{R}^d)^{[0,\infty)}$ and any optional time $S$ of $\mathcal{F}_t$,
   $$
   \mathbb{P}^x[X_{S+\cdot}\in F|X_S=y]=\mathbb{P}^y[X_{\cdot}\in F]
   $$
```

```ad-proposition
title:Use the transfer semigroup operator
Let $X_t$ be a progressively measurable process on $(\Omega,\mathcal{F})$ and let $\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ be a family of probability measure satisfying [[#^a2b026|condition 3 and 4]]. Then $X_t,(\Omega,\mathcal{F}),\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ is a strong Markov family iff for any $\mathcal{F}_t$-optional time $S,t\ge0$ and $x\in\mathbb{R}^d$, one of the following equivalent conditions holds:
1. For any $\Gamma\in\mathcal{B}(\mathbb{R}^d)$, 
   $$
   \mathbb{P}^x[X_{S+t}\in\Gamma|\mathcal{F}_{S+}]=(U_t\mathbb{1}_\Gamma)(X_S)
   $$
2. For any bounded, continuous function $f:\mathbb{R}^d\to\mathbb{R}$,
   $$
   \mathbb{E}^x[f(X_{S+t})|\mathcal{F}_{S+}]=(U_tf)(X_S)
   $$
```

^793d8e

**Proof**
For condition 1, the equivalent proof is the same as [[The Markov Property#^dd4132|the proposition]]. 
For condition 2
$\Longrightarrow$: Since $f$ can be approximated by simple function, by BCT and condition 1, the condition 2 holds.
$\Longleftarrow$: If condition 2 holds, we suppose $\Gamma\subseteq\mathbb{R}^d$ is a closed set, then $f_n(x)\to\mathbb{1}_\Gamma(x)$ pointwise where $f_n=(1-n\rho(x,\Gamma))\vee0$. Each $f_n$ is bounded and continuous, so condition 1 holds for closed set. Let $\mathscr{D}=\{\Gamma\in\mathcal{B}(\mathbb{R}^d):\Gamma\mbox{ holds condition 1}\}$ be a Dynkin system, by [[Kolmogorov's Construction of Brownian Motion#^273f1e|Dynkin system theorem]], we obtain condition 1 holds for $\Gamma\in\mathcal{B}(\mathbb{R}^d)$. 
**QED**
```ad-warning
We can define the [[The Markov Property#^de6b55|propbability measure]] $\mathbb{P}^\mu$ and condition 2 of strong Markov process can be writed 
$$
\int_F(U_t\mathbb{1}_\Gamma)(X_S){d}\mathbb{P}^x=\mathbb{P}^x(X_{S+t}\in\Gamma,F)
$$
```

```ad-def
title:Random shift operator
For any optional time $S$, we define $\theta_S:\{S<\infty\}\to\Omega$ by $\theta_S=\theta_s$ 0n $\{S=s\}$. Then we can write $X_{S(\omega)+t}(\omega)=X_t(\theta_S(\omega))$. 
```

```ad-thm
Let $X_t$ be an adapted process on a measurable space $(\Omega,\mathcal{F})$, $\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ be a family of probability measures on $(\Omega,\mathcal{F})$ and $\{\theta_s\}_{s\ge0}$ be shift operator. Then $X_t,(\Omega,\mathcal{F}),\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ is a strong Markov family if and only if the follow conditions hold.
1. For $F\in\mathcal{F}$, $x\mapsto\mathbb{P}^x(F)$ is universally measurable
2. For each $x_0\in \mathbb{R}^d$, $\mathbb{P}^x(\symbf{X}_0=x)=1$
3. For every $F\in\mathcal{F}^X_\infty$ and $s\ge0$, 
   $$
   \mathbb{P}^x[\theta^{-1}_S(F)|\mathcal{F}_{S+}]=\mathbb{P}^{X_S}(F),\mbox{ on }\{S<\infty\}
   $$
```
# The Strong Markov Property for Brownian motion
```ad-def
title:Regular conditional probability
Let $X:(\Omega,\mathcal{F},\mathbb{P})\to(S,\mathcal{B}(S))$. Let $\mathscr{C}$ be a sub-$\sigma$-algebra of $\mathcal{F}$. A regular conditional probability of $X$ given $\mathscr{C}$ is a function $Q:\Omega\times\mathcal{B}(S)\to[0,1]$ s.t. 
1. For $\omega\in\Omega$, $Q(\omega,\cdot)$ is a probability measure on $(S,\mathcal{B}(S))$
2. For $E\in\mathcal{B}(S)$, the mapping $\omega\mapsto Q(\omega,E)$ is $\mathscr{C}$-measurable. 
3. For $E\in\mathcal{B}(S)$, $\mathbb{P}(X\in E|\mathscr{C})(\omega)=Q(\omega,E)$
```

```ad-lemma
Let $X$ be a d-dimensional r.v. on $(\Omega,\mathcal{F},\mathbb{P})$ and $\mathscr{C}$ be a sub-$\sigma$-algebra of $\mathcal{F}$. Suppose for each $\omega\in\Omega$, there is a function $\varphi(\omega,\cdot):\mathbb{R}^d\to\mathbb{C}$ s.t. for $u\in\mathbb{R}^d$, 
$$
\varphi(\omega,u)=\mathbb{E}[e^{i(u,X)}|\mathscr{C}](\omega)
$$
If $\varphi(\omega,\cdot)$ is a charateristic function of some probability measure $\mathbb{P}^\omega$ on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$ i.e. 
$$
\varphi(\omega,u)=\int_{\mathbb{R}^d}e^{i(u,X)}{d}\mathbb{P}^\omega
$$
then for each $\Gamma\in\mathcal{B}(\mathbb{R}^d)$
$$
\mathbb{P}[X\in\Gamma|\mathscr{C}](\omega)=\mathbb{P}^\omega(\Gamma)
$$
```

^4401cd

```ad-def
title:Process $R_t$ and $I_t$
First we recall the d-dimensional normal r.v. $X\sim N_d(\mu_d,\Sigma_{d\times d})$ and its charateristic function 
$$
\mathbb{E}[e^{i(u,X)}]=e^{i(u,\mu)-\frac{u^\top\Sigma u}{2}}
$$
For d-dimensional Brownian motion $B_t$ and $u\in\mathbb{R}^d$, we define
$$
M_t=\exp(i(u,B_t)+\frac{t}{2}\|u\|^2),R_t=Re(M_t),I_t=Im(M_t)
$$
```

```ad-lemma
The process $R_t$ and $I_t$ are martingale on $(\Omega,\mathcal{F},\mathbb{P}^x)$
```
**Proof**
For $0\le s<t$, we have 
$$
\begin{align}
\mathbb{E}^x[M_t|\mathcal{F}_s]&=\mathbb{E}^x\left[M_s\exp(i(u,B_t-B_s)+\frac{t-s}{2}\|u\|^2)|\mathcal{F}_s\right]\\
&=M_s\exp(\frac{t-s}{2}\|u\|^2)\mathbb{E}^x[\exp(i(u,B_t-B_s))]\\
&=M_s\exp(\frac{t-s}{2}\|u\|^2)\exp(-\frac{t-s}{2}\|u\|^2)=M_s
\end{align}
$$
**QED**
```ad-thm
1. A d-dimensional Brownian family is a strong Markov family.
2. A d-dimensional Brownian motion is a strong Markov process.
```
**Proof**
We verify the Brownian family satisfies [[#^793d8e|the condition 1]]. Suppose $S$ is a bounded optional time. For fixed $x\in\mathbb{R}^d$, by [[Continuous-Time Martingales#^91b46a|optional sampling theorem]] and [[#^4401cd|lemma]], we W.T.S 
$$
\begin{align}
\mathbb{P}^x[B_{S+t}\in\Gamma|\mathcal{F}_{S+}]=(U_t\mathbb{1}_\Gamma)(B_{S+t})=\mathbb{P}^x(B_{t}\in\Gamma)
\end{align}
$$
We calculate $\mathbb{E}^x[\exp(i(u,B_{S+t}))|\mathcal{F}_{S+}]$ by [[Continuous-Time Martingales#^91b46a|optional sampling theorem]], since $M_t$ is martingale
$$
\begin{align}
&\mathbb{E}^x[M_{S+t}|\mathcal{F}_{S+}]=M_S\\
\Longleftrightarrow&\mathbb{E}^x\left[\exp(i(u,B_{S+t})+\frac{S+t}{2}\|u\|^2)\right]=\exp\left(i(u,B_S)+\frac{S}{2}\|u\|^2\right)\\
\Longleftrightarrow&\mathbb{E}^x[\exp(i(u,B_{S+t}))|\mathcal{F}_{S+}]=\exp\left(i(u,B_S)-\frac{t}{2}\|u\|^2\right)
\end{align}
$$
We conclude $B_{S+t}\sim N_d(B_{S(\omega)}(\omega),tI_d)$. By [[#^4401cd|lemma]], we obtain 
$$
\mathbb{P}^x[B_{S+t}\in\Gamma|\mathcal{F}_{S+}]=\mathbb{P}^\omega[\Gamma]
$$
where $\mathbb{P}^\omega$ is normal distribution $N_d(B_{S(\omega)}(\omega),tI_d)$. Note that $\mathbb{P}^x[B_t\in\Gamma]=\mathbb{P}^\omega(\Gamma)$, hence, we prove $\mathbb{P}^x[B_{S+t}\in\Gamma|\mathcal{F}_{S+}]=(U_t\mathbb{1}_\Gamma)(B_{S+t})=\mathbb{P}^x(B_{t}\in\Gamma)$.
**QED**
```ad-thm
Let $S$ be an a.s. finite optional time of the filtration $\{\mathcal{F}_t\}$ for the d-dimensional Brownian motion $B_t$. Then with $W_t=B_{S+t}-B_S$, the process $W_t$ is a d-dimensional Brownian motion, independent of $\mathcal{F}_{S+}$.
```

^322053

**Proof**
We W.T.S for $n\ge1$, $0\le t_0\le t_1\le\cdots\le t_n<\infty$ and $u_1,c\dots,u_n\in\mathbb{R}^d$, we have 
$$
\mathbb{E}\left[\exp\left(i\sum_{k=1}^{n}(u_k,W_{t_k}-W_{t_{k-1}})\right)\big|\mathcal{F}_{S+}\right]=\prod_{k=1}^{n}\exp\left(-\frac{1}{2}(t_k-t_{k-1})\|u_k\|^2\right)\tag{*}
$$
If $(*)$ holds, by [[#^4401cd|lemma]], $\{W_{t_k}-W_{t_{k-1}}\}_{k=1}^{n}\sim N_d(0,(t_k-t_{k-1})I_d)$ and are independent of $\sigma$-field $\mathbb{F}_{S+}$. Suppose $S$ is a bounded optional time, we prove by induction. We calculate 
$$
\begin{align}
&\mathbb{E}\left[\exp\left(i(u_{n+1},W_{t_{n+1}}-W_{t_n})\right)|\mathcal{F}_{(S+t_n)+}\right]\\
=&\mathbb{E}\left[\exp\left(i(u_{n+1},B_{S+t_{n+1}})\right)|\mathcal{F}_{(S+t_n)+}\right]\exp(-i(u_{n+1},B_{S+t_n}))\\
=&\exp\left(-\frac{1}{2}(t_{n+1}-t_n)\|u_{n+1}\|^2\right)
\end{align}
$$
Therefore,
$$
\begin{align}
&\mathbb{E}\left[\exp\left(i\sum_{k=1}^{n+1}(u_k,W_{t_k}-W_{t_{k-1}})\right)\big|\mathcal{F}_{S+}\right]\\
=&\mathbb{E}\left[\exp\left(i\sum_{k=1}^{n}(u_k,W_{t_k}-W_{t_{k-1}})\right)\mathbb{E}(\exp(i(u_{n+1},(W_{t_{n+1}}-W_{t_n}))|\mathcal{F}_{(S+t_n)+})|\mathcal{F}_{S+}\right]\\
=&\exp\left(-\frac{1}{2}(t_{n+1}-t_n)\|u_{n+1}\|^2\right)\mathbb{E}\left[\exp\left(i\sum_{k=1}^{n}(u_k,W_{t_k}-W_{t_{k-1}})\right)|\mathcal{F}_{S+}\right]\\
=&\prod_{k=1}^{n+1}\exp\left(-\frac{1}{2}(t_k-t_{k-1})\|u_k\|^2\right)
\end{align}
$$
By induction, we prove $(*)$.
**QED**
```ad-proposition
Let $X_t, (\Omega, \mathscr{F}), \{\mathbb{P}^x\}_{x \in \mathbb{R}^d}$ be a strong Markov family, and the process $X$ be right-continuous. Let $S$ be an optional time of $\{\mathcal{F}_t\}$ and $T$ an $\mathcal{F}_{S+}$-measurable random time satisfying $T(\omega) \geq S(\omega)$ for all $\omega \in \Omega$. Then, for any $x \in \mathbb{R}^d$ and any bounded, continuous $f: \mathbb{R}^d \to \mathbb{R}$, (6.8) $$ \mathbb{E}^x[f(X_T) \mid \mathcal{F}_{S+}](\omega) = (U_{T(\omega)-S(\omega)} f)(X_{S(\omega)}(\omega)), \quad \mathbb{P}^x\text{-a.e. } \omega \in \{T < \infty\}. $$
```

^0ecc3f

**Proof**
For $n\ge1$, 
$$
T_n=\begin{cases}
S+\frac{1}{2^n}\left([2^n(T-S)]+1\right),&T<\infty\\
\infty,&T=\infty
\end{cases}
$$
When $\frac{k-1}{2^n}<T-S<\frac{k}{2^n}$ s.t. $T_n=S+\frac{k}{2^n}$. We have $T_n\downarrow T$ on event $\{T<\infty\}$. By [[#^793d8e|condition of strong Markov process]], 
$$
\begin{align}
&\mathbb{E}^x[f(X_{S+\frac{k}{2^n}})|\mathcal{F}_{S+}]=(U_{\frac{k}{2^n}}f)(X_S)\\
\Longleftrightarrow&\mathbb{E}^x[f(X_{T_n})|\mathcal{F}_{S+}]=(U_{T_n-S}f)(X_S)
\end{align}
$$
By BCT and continuity,
$$
\mathbb{E}^x[f(X_{T})|\mathcal{F}_{S+}]=(U_{T-S}f)(X_S)
$$
**QED**
```ad-proposition
Under the conditions of [[#^0ecc3f|Proposition]] holds for every bounded, $\mathscr{B}(\mathbb{R}^d)/\mathscr{B}(\mathbb{R})$-measurable function $f$. In particular, for any $\Gamma \in \mathscr{B}(\mathbb{R}^d)$ we have for $P^x$-a.e. $\omega \in \{T < \infty\}$: $$ P^x[X_T \in \Gamma \mid \mathscr{F}_{S+}](\omega) = (U_{T(\omega)-S(\omega)} \mathbb{1}_\Gamma)(X_{S(\omega)}(\omega))$$
```

^1e90be

```ad-proposition
Let $B_t$ be a standard, one-dimensional Brownian motion, and for $b \neq 0$, let $T_b$ be [[#^cdb697|passage time]]. Then $T_b$ has the density given by [[#^9087d3|Heuristic proof]].
```

^48be42

**Proof**
Note that $-B_t$ is also o a standard, one-dimensional Brownian motion. Without loss of generality, we consider $b>0$ and let 
$$
T=\begin{cases}
t,&T_b<t\\
\infty,&T_b\ge t
\end{cases}
$$
We have $B_{T_b(\omega)}(\omega)=b$ and $\{T<\infty\}=\{T_b<t\}$, by [[#^1e90be|proposition]], 
$$
\begin{align}
\mathbb{P}^0[B_t<b,T_b<t]&=\mathbb{E}^0\left[\mathbb{1}_{\{T_b<t\}\cap\{B_T<b\}}\right]\\
&=\mathbb{E}^0\left[\mathbb{1}_{\{T_b<t\}}\mathbb{E}^0[\mathbb{1}_{\{B_T<b\}}|\mathcal{F}_{S+}]\right]\\
&=\int_{\{T_b<t\}}\mathbb{P}^0(B_T<b|\mathcal{F}_{T_b+})d\mathbb{P}^0\\
&=\int_{\{T_b<t\}}(U_{T-T_b}\mathbb{1}_{(-\infty,b)})(B_{T_b})d\mathbb{P}^0\\
&=\int_{\{T_b<t\}}\mathbb{P}^b(B_T<b)d\mathbb{P}^0=\frac{1}{2}\mathbb{P}^0[T_b<t]
\end{align}
$$
Then 
$$
\begin{align}
&\mathbb{P}^0[T_b<t]=\mathbb{P}^0[B_t<b,T_b<t]+\mathbb{P}^0[B_t>b]=\mathbb{P}^0[B_t>b]+\frac{1}{2}\mathbb{P}^0[T_b<t]\\
\Longrightarrow&\mathbb{P}^0(T_b<t)=2\mathbb{P}^0(B_t>b)
\end{align}
$$
By the way, let $t\to\infty$, we obtain $\mathbb{P}^0(T_b<\infty)=1$. It implies for each point, Brownian motion can hit it in finite time.
**QED**

---
# Exercises
```ad-question
Let $S$ be an optional time of the filtration $\{\mathscr{F}_t\}$ on some $(\Omega, \mathscr{F}, P)$. 
1. Show that if $Z_1$ and $Z_2$ are integrable random variables and $Z_1 = Z_2$ on some $\mathscr{F}_{S+}$-measurable set $A$, then $$ E[Z_1 \mid \mathscr{F}_{S+}] = E[Z_2 \mid \mathscr{F}_{S+}], \quad \text{a.s. on } A. $$ 
2. Show under the conditions of (i) that if $s$ is a positive constant, then $$ E[Z_1 \mid \mathscr{F}_{S+}] = E[Z_2 \mid \mathscr{F}_{(S \wedge s)+}], \quad \text{a.s. on } \{S \leq s\} \cap A. $$  
3. Show that if (e) (or (e')) in Proposition 6.7 holds for every bounded optional time $S$ of $\{\mathscr{F}_t\}$, then it holds for every optional time.
```

```ad-done

```

```ad-question
Show that (e") is equivalent to the following condition: (e""): For all $x \in \mathbb{R}^d$, any bounded, $\mathscr{F}_{\infty}^X$-measurable random variable $Y$, and any optional time $S$ of $\{\mathscr{F}_t\}$, we have $$ E^x[Y \circ \theta_S \mid \mathscr{F}_{S+}] = E^{X_S}(Y), \quad P^x\text{-a.s. on } \{S < \infty\}. $$ *(Note: If we write this equation with the arguments filled in, it becomes)* $$ E^x[Y \circ \theta_S \mid \mathscr{F}_{S+}](\omega) = \int_{\Omega} Y(\omega') P^{X_{S(\omega)}(\omega)}(d\omega'), \quad P^x\text{-a.e. } \omega \in \{S < \infty\}, $$ where $(Y \circ \theta_S)(\omega'') \triangleq Y(\theta_{S(\omega'')}(\omega'')).$
```

```ad-done
```

```ad-question
Show that [[The Markov Property#^65e528|Poisson family]] and [[Continuous-Time Martingales#^07fcac|Piosson process]] are strong Markov family and strong Markov process. 
```

```ad-done

```