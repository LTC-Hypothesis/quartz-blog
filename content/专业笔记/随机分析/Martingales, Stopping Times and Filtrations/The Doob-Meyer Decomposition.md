```ad-def
title:Increasing process
Consider a probability space $(\Omega,\mathcal{F},\mathbb{P})$ and a random sequence $\{A_n\}_{n=1}^{\infty}$ adapted to the discrete filtration $\{\mathcal{F_n}\}_{n=1}^{\infty}$. The sequence is called increasing, if for $\mathbb{P}-a.e. \omega\in\Omega$ we have $0=A_0(\omega)\le A_1(\omega)\le\cdots$, and $\mathbb{E}(A_n) < \infty$ holds for every $n \ge 1$.
```

```ad-def
title:Integrable of increasing sequence
An increasing sequence is called integrable if $\mathbb{E}(A_{\infty})<\infty$, where $A_{\infty}\triangleq\lim_{n\to\infty}A_n$
```

```ad-def
title:Predictable
An arbitrary random sequence $\{\xi_n\}_{n=1}^{\infty}$ is called predictable for the filtration $\{\mathcal{F}_n\}_{n=1}^{\infty}$, if for every $n\ge 1$ the random variable $\xi_n$ is $\mathcal{F}_{n-1}$-measurable.
```

```ad-def
title:Martingale transform / discrete version of stochastic integral
If $A$ is predictable with $\mathbb{E}|A_n|<\infty$ for every $n$, and $M_n$ is a bounded martingale, then the martingale transform of $A$ by $M$ defined by 
$$Y_0=0,Y_n=\sum_{k=1}^{n}A_k(M_k-M_{k-1})$$
This martingale transform is the discrete-time version of the stochastic integral with respect to a martingale.
```

^6ea757

We recall the discrete version of Doob decomposition. 
```ad-proposition
title:Doob decomposition (discrete)
For any submartingale $X_n$, there admits the decomposition
$$X_n=M_n+A_n$$
where $M_n$ is a martingale and $A_n$ is an increasing process. Moreover, $A_0=0$, the decomposition is unique, and 
$$
A_{n+1}=\sum_{k=0}^{n}\left(\mathbb{E}[X_{k+1}|\mathcal{F}_k]-X_k\right)
$$
```

```ad-def
title:Natural
An increasing sequence $A_n$ is called natural if for every bounded martingale $M_n$ we have 
$$\mathbb{E}(M_nA_n)=\mathbb{E}\left[\sum_{k=1}^{n}M_{k-1}(A_k-A_{k-1})\right]$$
```

```ad-warning
An increasing sequence $A$ is natural if and only if the martingale transform $Y$ of $A$ by every bounded martingale $M$ satisfies $EY_n = 0, n \ge 0$. 
```

^329422

```ad-proposition
An increasing random sequence $A$ is **predictable** if and only if it is **natural**.
```
**Proof**
$\Longleftarrow$: Suppose $A$ is natural and $M$ is a bounded martingale. By [[#^329422|warning]], $Y_n=\sum_{k=1}^{n}A_k(M_k-M_{k-1}),\mathbb{E}Y_n=0$ for $n\ge 0$. Then 
$$
\mathbb{E}(A_n(M_n-M_{n-1}))=\mathbb{E}Y_n-\mathbb{E}Y_{n-1}=0
$$
We calculate
$$
\begin{align}
\mathbb{E}\left[M_n(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))\right]=&\mathbb{E}[(M_n-M_{n-1})A_n]+\mathbb{E}[M_n(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))]\\
&-\mathbb{E}[(M_n-M_{n-1})\mathbb{E}(A_n|\mathcal{F}_{n-1}))]=0\\
\end{align}
$$
where $\mathbb{E}[M_n(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))]=\mathbb{E}[\mathbb{E}(M_n(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))|\mathcal{F}_{n-1})]$, since $A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1})$ is $\mathcal{F}_{n-1}$-measurable and $\mathbb{E}(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))=0$. Then $\mathbb{E}[M_n(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))]=\mathbb{E}[M_n|\mathcal{F}_{n-1}]\mathbb{E}(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))=0$. Similarly, $\mathbb{E}[(M_n-M_{n-1})\mathbb{E}(A_n|\mathcal{F}_{n-1}))]=0$. Fixed $n\ge 0$, we construct 
$$
M_k=\begin{cases}
sgn(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1})),&k=n\\
M_n,&k>n\\
\mathbb{E}(M_n|\mathcal{F}_{n-1}),&k=1,\cdots,n
\end{cases}
$$
We obtain $\mathbb{E}(sgn(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))=\mathbb{E}|(A_n-\mathbb{E}(A_n|\mathcal{F}_{n-1}))|=0$. Hence, $A_n$ is predictable.
$\Longrightarrow$: Suppose $A_n$ is predictable, $A_n$ is $\mathcal{F}_{n-1}$-measurable for $n\ge 1$. Without loss of generality, we assume $A_0=0$. Note that $A_n=A_1-A_0+A_2-A_1+\cdots+A_n-A_{n-1}$, then 
$$
\begin{align}
\mathbb{E}[M_nA_n]&=\mathbb{E}[M_n\sum_{k=1}^{n}(A_k-A_{k-1})]=\sum_{k=1}^{n}\mathbb{E}\left[M_n(A_k-A_{k-1})\right]\\
&=\mathbb{E}\left[\sum_{k=1}^{n}\mathbb{E}\left(M_n(A_k-A_{k-1})|\mathcal{F}_{k-1}\right)\right]\\
&=\mathbb{E}\left[\sum_{k=1}^{n}(A_k-A_{k-1})\mathbb{E}\left(M_n|\mathcal{F}_{k-1}\right)\right]=\mathbb{E}\left[\sum_{k=1}^{n}M_{k-1}(A_k-A_{k-1})\right]
\end{align}
$$
Hence, $A_n$ is natural. 
**QED**
```ad-def
title:Continuous increasing process
An adapted process $A$ is called increasing if for $\mathbb{P}-a.e. \omega\in\Omega$ we have
1. $A_0(\omega)=0$
2. $t\mapsto A_t(\omega)$ is a nondecreasing, right-continuous function. 

and $\mathbb{E}(A_t) < \infty$ holds for every $t\in [0, \infty)$. An increasing process is called integrable if $\mathbb{E}(A_\infty)$, where $A_{\infty}=\lim_{t\to\infty}A_t$.
```

```ad-def
title:Natural of continuous version
An increasing process $A$ is called natural if for every bounded, right-continuous martingal $M_t$ we have 
$$
\mathbb{E}\int_{0}^{t}M_s{d}A_s=\mathbb{E}\int_0^tM_{s-}{d}A_s
$$
```

```ad-warning
1. Recall Lebesgue-Stieltjes integrals: if $A$ is a increasing process and $X_t$ is a measurable process, the sample path $X_t(\omega):[0,\infty)\to\mathbb{R}$ is a measurable function. We can define the integral
$$
I^{\pm}_t(\omega)=\int_{0}^{t}X^{\pm}_t(\omega){d}A_s(\omega)
$$
If X is progressively measurable (e.g., right-continuous and adapted), and if $I_t = I^+_t-I^-_t$ is well defined and finite for all $t \le 0$, then $I$ is right-continuous and progressively measurable.
2. Every continuous, increasing process is natural. Indeed, for $a.s.-\mathbb{P},\omega\in\Omega$, we have 
   $$
   \int_{0}^{t}(M_s(\omega)-M_{s-}(\omega)){d}A_s(\omega)=0,t>0
   $$
   By [[Continuous-Time Martingales#^bd276e|countably discontuities of martingale]] $M_s(\omega)$.
3. Every natural increasing process is adapted to the filtration $\{\mathcal{F}_{t-}\}$, provided that $\{\mathcal{F}_t\}$ satisfies the usual condition.
```

```ad-proposition
$A$ is natural iff $$\mathbb{E}(M_tA_t)=\mathbb{E}\int_{0}^{t}M_{s-}{d}A_s$$
```

^9aa485

**Proof**
$\Longleftrightarrow$: Consider the partition of $[0,t]$: $\Pi=\{t_0,t_1,\cdots,t_n\}$, $0=t_0\le t_1\le \cdots\le t_n=t$. Define 
$$
M^{\Pi}_s=\sum_{k=0}^{n-1}M_{t_k}\mathbb{1}_{(t_k,t_{k+1}]}
$$
We have 
$$
\begin{align}
\mathbb{E}\int_{0}^{t}M^{\Pi}_s{d}A_s&=\mathbb{E}\left[\sum_{k=1}^{n}M_{t_k}(A_{t_k}-A_{t_{k-1}})\right]=\mathbb{E}\left[\sum_{k=1}^{n}M_{t_k}A_{t_k}-\sum_{k=0}^{n-1}M_{t_{k+1}}A_{t_{k}}\right]\\
&=\mathbb{E}M_tA_t-\mathbb{E}\sum_{k=1}^{n-1}(M_{t_{k}}-M_{t_{k-1}})A_{t_k}=\mathbb{E}M_tA_t
\end{align}
$$
where $\mathbb{E}\sum_{k=1}^{n-1}(M_{t_{k}}-M_{t_{k-1}})A_{t_k}=\mathbb{E}\left[\mathbb{E}\sum_{k=1}^{n-1}(M_{t_{k}}-M_{t_{k-1}})A_{t_k}|\mathcal{F}_{t_{k}}\right]=0$ by property of martingale. Let $\|\Pi\|=\max_{1\le k\le n}(t_k-t_{k-1})\to0$, so $M^{\Pi}_s\to M_s$. By MCT, $\mathbb{E}\int_{0}^{t}M^{\Pi}_s{d}A_s\to\mathbb{E}\int_{0}^{t}M_s{d}A_s$. Hence, $\mathbb{E}\int_{0}^{t}M_s{d}A_s=\mathbb{E}(M_tA_t)=\mathbb{E}\int_{0}^{t}M_{s-}{d}A_s$.
**QED**
```ad-def
title:Class $D$ and class $DL$
We define the class $\mathscr{S}$:
$$
\mathscr{S}=\{T\mbox{ is stopping time of }\mathcal{F}_t:\mathbb{P}(T<\infty)=1\}
$$
$$
\mathscr{S}_a=\{T\mbox{ is stopping time of }\mathcal{F}_t:\mathbb{P}(T\le a)=1,0<a<\infty\}
$$
Class $D$: if the family $\{X_T\}_{T\in\mathscr{S}}$ is uniformly integrable. 
Class $DL$: if the family $\{X_T\}_{T\in\mathscr{S}_a}$ is uniformly integrable.
```

```ad-thm
title:Doob-Meyer decomposition
Let $\{\mathcal{F}_t\}$ satisfies the usual condition. If the right-continuous submartingale $X_t$ is of the class $DL$, then it admits the decomposition as follow:
$$
X_t=M_t+A_t
$$
where $M_t$ is a **right-continuous martingale** and $A_t$ is a **increasing process**. $A_t$ can be token as natural, under this condition, the decomposition is unique. Futher, if $X$ is of the class $D$, then $M$ is uniformly integrable and $A$ is integrable. 
```

^5cc05f

**Proof**
We only prove the uniqueness and give a sketch proof of existence. 
**For uniqueness.** Suppose $X_t$ admits the both decomposition:
$$
X_t=M'_t+A'_t=M''_t+A''_t
$$
$M'_t,M''_t$ are martingales and $A'_t,A''_t$ are natural increasing processes. Then 
$$
\{B_t=A'_t-A''_t=M''_t-M'_t:t\ge0\}
$$
is a martingale and for bounded and right-continuous martingale $\xi_t$, by [[#^9aa485|proposition]], we have 
$$
\mathbb{E}(\xi_tB_t)=\mathbb{E}\int_{0}^{t}\xi_{s-}{d}B_s=\lim_{n\to\infty}\mathbb{E}\sum_{j=1}^{m_n}\xi_{t^{(n)}_{j-1}}(B_{t^{(n)}_{j}}-B_{t^{(n)}_{j-1}})
$$
where partition $\Pi_n=\{t^{(n)}_{0},\cdots,t^{(n)}_{m_n}\},n\ge 1$ with $\|\Pi_n\|=\max_{1\le j\le m_n}|t^{(n)}_{j}-t^{(n)}_{j-1}|\to0$. But now, by property of martingale, we have 
$$
\mathbb{E}(\xi_{t^{(n)}_{j-1}}(B_{t^{(n)}_{j}}-B_{t^{(n)}_{j-1}}))=0,\mathbb{E}(\xi_tB_t)=\mathbb{E}(\xi_t(A'_t-A''_t))=0
$$
For an arbitrary bounded random variable $\xi$, we can select  a right-continuous modification of $\{\mathbb{E}(\xi|\mathcal{F}_t)\}$. We obtain $\mathbb{E}(\xi(A'_t-A''_t))=0$ and therefore we have $\mathbb{P}(A'_t=A''_t)=1$ for every $t\ge 0$.
**For existence.**
**QED**
```ad-def
title:Regular
A submartingale $X_t$ is called **regular** if for every $a>0$ and every nondecreasing sequence of stopping times $T_n\subseteq\mathscr{S}_a$ with $T_n\uparrow T$ we have $\lim_{n\to\infty}\mathbb{E}(X_{T_n})=\mathbb{E}(X_T)$
```

```ad-proposition
A continuous, nonnegative submartingale is regular.
```

^c8b329

**Proof**
Suppose $X_t$ is a continuous nonnegetive submartingale and $T_n\subseteq\mathscr{S}_a$ for every $a$ with $T_n\uparrow T$. For $T_n\le T\le a$, by [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], we have 
$$
\mathbb{E}(X_T|\mathcal{F}_{T_n})\ge X_{T_n}\Longrightarrow\mathbb{E}(X_T)\ge \mathbb{E}(X_{T_n})
$$
Then $\mathbb{E}(X_{T_n})$ is bounded and we have $\varlimsup_{n\to\infty}\mathbb{E}(X_{T_n})\le\mathbb{E}(X_{T})$. Another direction, since $T_n\uparrow T$ and $X_t$ is continuous, we have $X_{T_n}\to X_{T},a.s.$. Therefore, by Fatou's Lemma, 
$$
\mathbb{E}(X_T)=\mathbb{E}(\lim_{n\to\infty}X_{T_n})\le\varliminf_{n\to\infty}\mathbb{E}(X_{T_n})
$$
Above all, we have 
$$
\varlimsup_{n\to\infty}\mathbb{E}(X_{T_n})\le\mathbb{E}(X_{T})\le\varliminf_{n\to\infty}\mathbb{E}(X_{T_n})
$$
Hence, $\lim_{n\to\infty}\mathbb{E}(X_{T_n})=\mathbb{E}(X_T)$, $X_t$ is regular.
**QED**
```ad-thm
Suppose that $X_t$ is a right-continuous submartingale of class $DL$ with respect to the filtration $\{\mathcal{F}_t\}$, which satisfies the usual conditions, and let $A_t$ be the natural increasing process in the [[#^5cc05f|Doob-Meyer decomposition]]. The process **$A$ is continuous** if and only if **$X$ is regular**.
```
**Proof**
$\Longrightarrow:$ Suppose $A$ is continuous. We can imitate the proof of [[#^c8b329|last proposition]]. By appealing [[Continuous-Time Martingales#^675f51|optional sampling theorem]]. 
$\Longleftarrow$: Suppose $X$ is regular, for every $a>0$, $\{T_n\}\subseteq\mathscr{S}_a$ with $T_n\uparrow T$. By  [[Continuous-Time Martingales#^675f51|optional sampling theorem]], we have 
$$
\lim_{n\to\infty}\mathbb{E}(A_{T_n})=\lim_{n\to\infty}\mathbb{E}(X_{T_n})-\lim_{n\to\infty}\mathbb{E}(M_{T_n})=\mathbb{E}(A_T)
$$
Therefore, $A_{T_n(\omega)}(\omega)\uparrow A_{T(\omega)}(\omega),a.e.-\mathbb{P}$ which may depend on $T$. To remove the dependence of $T$, we consider the partition of $\Pi_n=\{t^{(n)}_1,\cdots,t^{(n)}_{2^n}\}$ of the interval $[0,a]$ and select $\lambda>0$. For each interval $[t^{(n)}_j,t^{(n)}_{j+1}],j=0,1,\cdots,2^n-1$, we construct a right-continuous modification of the martingale,
$$
\xi^{(n)}_t=\mathbb{E}[\lambda\wedge A_{t^{(n)}_{j+1}}|\mathcal{F}_t],t^{(n)}_j<t\le t^{(n)}_{j+1}
$$
In fact, [[Continuous-Time Martingales#^2cd6c5|modification of submartingale]] can guarantee the existence of $\xi^{(n)}_t$. The process $\xi^{(n)}_t$ is right-continuous on $(0,a)$ except the point of the partition and dominates the process $\lambda\wedge A_t$. In particular, the two process are equivalent a.s. on partition point. Since $A$ is a natural increasing process, we have 
$$
\mathbb{E}\int_{t^{(n)}_j}^{t^{(n)}_{j+1}}\xi^{(n)}_{s}{d}A_s=\mathbb{E}\int_{t^{(n)}_j}^{t^{(n)}_{j+1}}\xi^{(n)}_{s-}{d}A_s\Longrightarrow\mathbb{E}\int_{0}^{t}\xi^{(n)}_{s}{d}A_s=\mathbb{E}\int_{0}^{t}\xi^{(n)}_{s-}{d}A_s
$$

^aa9147

for any $t\le a$. Now the process 
$$
\eta^{(n)}_t=\begin{cases}
\xi^{(n)}_{t+}-\lambda\wedge A_t,&0\le t<a\\
0,&t=a
\end{cases}
$$
is right-continuous and adapted to $\mathcal{F}_t$. For any $\varepsilon>0$, the random time
$$
T_n(\varepsilon)=a\wedge\inf\{t:\eta^{(n)}_t>\varepsilon\}=a\wedge\inf\{t:\xi^{(n)}_t-\lambda\wedge A_t>\varepsilon\}
$$
By properties of [[Stopping Times#^5ea1fe|Hitting time]], $T_n(\varepsilon)$ can be regarded as hitting time of open interval $(\varepsilon,\infty)$. Hence, $T-n(\varepsilon)$ is a optional time and thus a stopping time. We define the function:
$$
\varphi_n:[0,a]\to\Pi_n,t\mapsto t^{(n)}_{j+1},t^{(n)}_{j}<t\le t^{(n)}_{j+1}
$$
Note that $\varphi_n(t)$ is a nondecreasing function and $\varphi_n(t)\ge t$. For stopping time $T_n$ and any $t\ge 0$, we have $\{\varphi_n(T_n(\varepsilon))\le t\}=\{T_n(\varepsilon)\le s_t\}$ where $s_t=\sup\{s\in[0,a]:\varphi_n(s)\le t\}$, then $\varphi_n(T_n(\varepsilon))\in\mathscr{S}_a$. Since $\xi^{(n)}$ is decreasing in $n$, $T_n(\varepsilon)\uparrow T_\varepsilon\in\mathscr{S}_a$, we also have $\lim_{n\to\infty}\varphi_n(T_n(\varepsilon))=T_{\varepsilon},a.s.-\mathbb{P}$. By  [[Continuous-Time Martingales#^675f51|optional sampling theorem]], we have 
$$
\mathbb{E}(\xi^{(n)}_{T_n(\varepsilon)})=\sum_{j=1}^{2^n-1}\mathbb{E}[\mathbb{E}(\lambda\wedge A_{t^{(n)}_{j+1}}|\mathcal{F}_{T_n(\varepsilon)})|\mathbb{1}_{\{t^{(n)}_{j}<t\le t^{(n)}_{j+1}\}}]=\mathbb{E}[\lambda\wedge A_{\varphi_n(T_n(\varepsilon))}]
$$
and therefore, 
$$
\begin{align}
\mathbb{E}[\lambda\wedge A_{\varphi_n(T_n(\varepsilon))}-\lambda\wedge A_{T_n(\varepsilon)}]&=\mathbb{E}[\xi^{(n)}_{T_n(\varepsilon)}-\lambda\wedge A_{T_n(\varepsilon)}]\\
&=\mathbb{E}[\mathbb{1}_{\{T_n(\varepsilon)<a\}}(\xi^{(n)}_{T_n(\varepsilon)}-\lambda\wedge A_{T_n(\varepsilon)})]\\
&\ge\varepsilon\mathbb{P}(T_n(\varepsilon)<a)
\end{align}
$$
Let $Q_n=\sup_{0\le t\le a}|\xi^{(n)}_{t}-\lambda\wedge A_{t}|$, by regularity of $X$, we have 
$$
\mathbb{P}(Q_n>\varepsilon)=\mathbb{P}(T_n<a)\le \frac{1}{\varepsilon}\mathbb{E}[\lambda\wedge A_{\varphi_n(T_n(\varepsilon))}-\lambda\wedge A_{T_n(\varepsilon)}]\to0
$$
Hence, $Q_n\to 0$ in probability and thus has a subsequence almost surely converge. By MCT with [[The Doob-Meyer Decomposition#^aa9147|Lebesgue-Stieltjes integral]], 
$$
\mathbb{E}\int_{0}^{t}(\lambda\wedge A_{s}){d}A_s=\mathbb{E}\int_{0}^{t}(\lambda\wedge A_{s-}){d}s
$$
It implies the continuity of $t\mapsto\lambda\wedge A_{s}$ for every $\lambda>0$. Let $\lambda\to\infty$, we have the continuity of $t\mapsto A_{s}$. 
**QED**

---
# Exercises
```ad-question
Suppose $X = \{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ is a right-continuous submartingale. Show that under any one of the following conditions, $X$ is of class $DL$.

(a) $X_t \geq 0$ a.s. for every $t \geq 0$.  
(b) $X$ has the special form  

$$ \quad X_t = M_t + A_t, \quad 0 \leq t < \infty$$

suggested by the Doob decomposition, where $\{M_t, \mathcal{F}_t; 0 \leq t < \infty\}$ is a martingale and $\{A_t, \mathcal{F}_t; 0 \leq t < \infty\}$ is an increasing process.

Show also that if $X$ is a uniformly integrable martingale, then it is of class $D$.
```

```ad-done
title:Done for condition (a)
For fixed $a>0$ and $T\le a$, by [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], we have 
$$
0\le X_{T}\le \mathbb{E}(X_a|\mathcal{F}_T)
$$
Note that if $\mathbb{E}(X_a|\mathcal{F}_T)$ is u.i., $X_T$ is also u.i. Now we check the r.v. family $\{\mathbb{E}(X_a|\mathcal{F}_T)\}_{T\in\mathscr{S}_a}$ are u.i. By definition, let $Z=\mathbb{E}(X_a|\mathcal{F}_T)$. Since $X_a$ is integrable, for $\forall \varepsilon>0$, $\exists K>0$ s.t. $\mathbb{E}(|X_a|\mathbb{1}_{\{|X_a|\ge K\}})<\frac{\varepsilon}{2}$. For $M>0$, we have 
$$
\begin{align}
|\mathbb{E}(Z\mathbb{1}_{\{|Z|\ge M\}})|\le&\mathbb{E}\left(\mathbb{E}(|X_a|\mathbb{1}_{\{|X_a|\le K\}}|\mathcal{F}_T)\mathbb{1}_{\{|Z|\ge M\}}\right)\\
&+\mathbb{E}\left(\mathbb{E}(|X_a|\mathbb{1}_{\{|X_a|> K\}}|\mathcal{F}_T)\mathbb{1}_{\{|Z|\ge M\}}\right)
\end{align}
$$
For the first item, 
$$
\mbox{item1}\le K\mathbb{P}(|Z|>M)\le K\frac{\mathbb{E}(|Z|)}{M}
$$
For the second item, since $\{|Z|\ge M\}$ is $\mathcal{F}_T$-measurable, 
$$
\mbox{item2}=\mathbb{E}\left(\mathbb{E}(|X_a|\mathbb{1}_{\{|X_a|> K\}}\mathbb{1}_{\{|Z|\ge M\}}|\mathcal{F}_T)\right)\le \mathbb{E}(|X_a|\mathbb{1}_{\{|X_a|> K\}})<\frac{\varepsilon}{2}
$$
Above all, we obtain $|\mathbb{E}(Z\mathbb{1}_{\{|Z|\ge M\}})|\le K\frac{\mathbb{E}(|Z|)}{M}+\frac{\varepsilon}{2}$, then $$\varlimsup_{M\to\infty}|\mathbb{E}(Z\mathbb{1}_{\{|Z|\ge M\}})|<\frac{\varepsilon}{2}$$
For arbitrary $\varepsilon>0$, we obtain $Z$ is u.i.
```

```ad-done
title:Done for condition (b)
Since $M_t$ is a continuous martingale, $M_T=\mathbb{E}(M_a|\mathcal{F}_T)$. Since $A_t$ is increasing process, $0\le A_T\le A_a$. Then we have $X_T\le \mathbb{E}(M_a|\mathcal{F}_T)+A_a$, $\{\mathbb{E}(M_a|\mathcal{F}_T)\}$ and $A_a$ are u.i. Hence, $X_T$ is u.i.
```

```ad-done
title:Done for final claim
we use this theorem ![[Pasted image 20260323181900.png]]
Then we have 
$$
X_t=\mathbb{E}(X_\infty|\mathcal{F}_t)
$$
For stopping time $T$ with $\mathbb{P}(T<\infty)=1$, we obtain $X_T=\mathbb{E}(X_\infty|\mathcal{F}_T)$ is u.i. Hence, $X_T\in D$.
```

```ad-question
Show that if $\{A^{(n)}\}_{n=1}^\infty$ is a sequence of integrable random variables on a probability space $(\Omega, \mathcal{F}, \mathbb{P})$ which converges weakly in $L^1$ to an integrable random variable $A$, then for each $\sigma$-field $\mathcal{G} \subset \mathcal{F}$, the sequence  
$$\mathbb{E}[A^{(n)} | \mathcal{G}]$$  
converges to $\mathbb{E}[A | \mathcal{G}]$ weakly in $L^1$.
```

```ad-done
We recall the definition of converge weakly in $L^1$. $A^{(n)}\xrightarrow{w}A$ i.e. for any $Z\in L^{\infty}$, $\mathbb{E}(A^{(n)}Z)\to\mathbb{E}(AZ)$ as $n\to\infty$. By Tower principle, for any bounded r.v. $Z$, we use the property of conditional expectation
![[Pasted image 20260324140504.png]]
$$
\mathbb{E}[Z\mathbb{E}(A^{(n)}|\mathcal{G})]=\mathbb{E}[A^{(n)}\mathbb{E}[Z|\mathcal{G}]]
$$
Take limit, we have $\mathbb{E}[Z\mathbb{E}(A|\mathcal{G})]=\mathbb{E}[A\mathbb{E}[Z|\mathcal{G}]]$. Hence, $\mathbb{E}[Z\mathbb{E}(A^{(n)}|\mathcal{G})]\to\mathbb{E}[Z\mathbb{E}(A|\mathcal{G})]$ weakly in $L^1$
```

```ad-question
Let $X = \{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be a continuous, nonnegative process with $X_0 = 0$ a.s., and $A = \{A_t, \mathcal{F}_t; 0 \leq t < \infty\}$ any continuous, increasing process for which

$$\mathbb{E}(X_T) \leq \mathbb{E}(A_T)$$

holds for every bounded stopping time $T$ of $\{ \mathcal{F}_t \}$. Introduce the process $V_t \triangleq \max_{0 \leq s \leq t} X_s$, consider a continuous, strictly increasing function $F$ on $[0, \infty)$ with $F(0) = 0$, and define $G(x) \triangleq 2F(x) + x \int_x^\infty u^{-1} dF(u); \, 0 < x < \infty$. Establish the inequalities
$$\mathbb{P}[V_T \geq \epsilon] \leq \frac{\mathbb{E}(A_T)}{\epsilon}; \quad \forall \epsilon > 0$$
$$\mathbb{P}[V_T \geq \varepsilon, A_T < \delta] \leq \frac{\mathbb{E}(\delta \land A_T)}{\varepsilon}; \quad \forall \varepsilon > 0, \delta > 0$$
$$\mathbb{E}F(V_T) \leq \mathbb{E}G(A_T)$$
for any stopping time $T$ of $\{ \mathcal{F}_t \}$.
```

^f31d9e

```ad-note
Technique: **construct appropiate stopping time**. In general, we should associate the hitting time.
```

```ad-done
title:Done for first inequality
Define the stopping time $H_\varepsilon=\inf\{t\ge0:X_t\ge\varepsilon\}$. Let $T_n=T\wedge n\wedge H_\varepsilon$, we have 
$$
\begin{align}
\varepsilon\mathbb{P}[V_{T_n}\ge \varepsilon]&=\mathbb{E}[\varepsilon\mathbb{1}_{\{V_{T_n}\ge \varepsilon\}}]\\
&\le \mathbb{E}[X_{T_n}\mathbb{1}_{\{V_{T_n}\ge\varepsilon\}}]\le\mathbb{E}[X_{T_n}]\le \mathbb{E}[A_{T_n}]\le \mathbb{E}[A_T]\\
&\Longrightarrow\mathbb{P}[V_{T_n}\ge\varepsilon]\le \frac{\mathbb{E}[A_T]}{\varepsilon}
\end{align}
$$
Since $T_n\uparrow T\wedge H_{\varepsilon}$ as $n\to\infty$, we obtain $\mathbb{P}[V_{T}]\le\frac{\mathbb{E}[A_T]}{\varepsilon}$.
```

```ad-done
title:Done for second inequality
Define the stopping time $S_\delta=\inf\{t\ge0:A_t\ge \delta\}$. If $A_T<\delta$, then $S_\delta>T$ and thus $T\wedge S_{\delta}=T$, $\{V_{S_{\delta}\wedge T}\ge \varepsilon\}=\{V_T\ge \varepsilon\}$. Then we have $\{V_T\ge \varepsilon,A_T<\delta\}\subseteq\{V_{T\wedge S_{\delta}}\ge \varepsilon\}$ and take probability,
$$
\mathbb{P}[V_T \geq \varepsilon, A_T < \delta]\le \mathbb{P}[V_{T\wedge S_{\delta}}\ge \varepsilon]\le \frac{\mathbb{E}[A_{T\wedge S_\delta}]}{\varepsilon}=\frac{\mathbb{E}[\delta\wedge A_T]}{\varepsilon}
$$
```

```ad-done
title:Done for third inequality
Since $F$ is strictly increasing, then $F(x)\le u\Longrightarrow x\le F^{-1}(u)$. By formula of expectation,
$$
\begin{align}
\mathbb{E}(F(V_T))&=\int_{0}^{\infty}\mathbb{P}(F(V_T)\ge u){d}u=\int_{0}^{\infty}\mathbb{P}(V_T\ge F^{-1}(u)){d}u\\
&\le \int_{0}^{\infty}\mathbb{P}(V_T\ge u,A_T\ge u)+\frac{\mathbb{E}[u\wedge A_T]}{u}{d}F(u)\\
&\le \int_{0}^{\infty}\mathbb{P}(A_T\ge u){d}F(u)+\int_{0}^{\infty}\mathbb{P}(A_T\ge u){d}F(u)+\int_{0}^{\infty}\frac{\mathbb{E}[A_T\mathbb{1}_{\{A_T< u\}}]}{u}\\
&=2\int_{0}^{\infty}\mathbb{P}(A_T\ge u){d}F(u)+\int_{0}^{\infty}\frac{1}{u}\int_{\{A_T<u\}}A_T{d}\mathbb{P}{d}F(u)\\
&=2\int_{0}^{\infty}\mathbb{P}(A_T\ge u){d}F(u)+\int_{\Omega}\int_{A_T}^{\infty}\frac{A_T}{u}{d}F(u){d}\mathbb{P}\\
&=2\int_{0}^{\infty}\mathbb{P}(A_T\ge u)+\mathbb{E}\left[A_T\int_{A_T}^{\infty}\frac{1}{u}{d}F(u)\right]\\
&=2\mathbb{E}(F(A_T))+\mathbb{E}\left[A_T\int_{A_T}^{\infty}\frac{1}{u}{d}F(u)\right]=\mathbb{E}(G(A_T))
\end{align}
$$
```