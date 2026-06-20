We start this section from random time.

> [!def] random time
> A random time $T$ is an $\mathcal{F}$-measurable random variable, with values in $[0, \infty]$. With process $X$, we define the function $X_T$ on the event $\{T<\infty\}$ by 
> $$
> X_T(\omega)=X_{T(\omega)}(\omega)
> $$
> If $X_{\infty}(\omega)$ is defined for every $\omega\in \Omega$, then $X_T$ can also be defined on $\Omega$, by setting $X_{T}(\omega)=X_{\infty}(\omega)$ on $\{T=\infty\}$

> [!def] Stopping time and optional times
> Let us consider a measurable space $(\Omega,\mathcal{F})$ equipped with a filtration $\{\mathcal{F}_t\}$. A random time $T$ is a **stopping time** of the filtration, if the event $\{T\le t\}\in \mathcal{F}_t$. A random time $T$ is an **optional time** of the filtration, if $\{T<t\}\in \mathcal{F}_t$.

> [!proposition] Properties of stopping time
> 1. Every random time equal to a nonnegative constant is a stopping time
> 2. Every stopping time is optional
> 3. The two concepts coincide if the filtration is right-continuous.
> 4. T is an optional time of the filtration $\{\mathcal{F}_t\}$ if and only if it is a stopping time of the filtration $\{\mathcal{F}_{t+}\}$

**Proof**
1. Suppose $T=c>0$, with $t>0$, if $T=c\le t$, then $\{T=c\le t\}\in \mathcal{F}_t$. If $T=c>t$, then $\{T=c>t\}=\{T=c\le t\}^c\in \mathcal{F}_t$. Hence, $T=c$ is a stopping time.
2. Note that 
$$
\{T<t\}=\bigcup_{n=1}^{\infty}\{T\le t-\frac{1}{n}\}\in \mathcal{F}_t
$$
3. It suffices to show optional time is stopping. Since $\{\mathcal{F}_t\}$ is right-continuous i.e. $\mathcal{F}_t=\mathcal{F}_{t+}$. Note that $$\{T\le t\}=\bigcap_{n=1}^{\infty}\{T<t+\frac{1}{n}\}\in\mathcal{F}_{t+}=\mathcal{F}_t$$
4. By 2. and 3., it is trivial.

**QED**

> [!def] Hitting time
> Consider a stochastic process $X$ with right-continuous paths, which is adapted to a filtration $\{\mathcal{F}_t\}$. Consider a subset $\Gamma\in \mathcal{B}(\mathbb{R}^d)$ of the state space of the process, and define 
> $$
> H_{\Gamma}(\omega)=\inf\{t\ge 0:X_t(\omega)\in\Gamma\}
> $$

> [!proposition] Properties of hitting time
> 1. If the set $\Gamma$ is open, $H_\Gamma$ is an optional time.
> 2. If the set $\Gamma$ is closed and the sample paths of the process $X$ are continuous, then $H_\Gamma$ is a stopping time.

^5ea1fe

**Proof**
1. It suffices to show $\{H_\Gamma<t\}\in \mathcal{F}_t$. By definition of hitting time, $\exists s<t$ s.t. $X_s\in \Gamma$. Since $\Gamma$ is open and $X$ has right-continuous paths, for fixed $t>0$, $\forall\varepsilon>0$, for $s < u < s+\varepsilon<t$, $X_u\in \Gamma$. We choose rational number $q\in (s,s+\varepsilon)\subset(s,t)$, $\{X_q\in\Gamma\}\in \mathcal{F}_q\subset\mathcal{F}_t$. Note that $$\{H_\Gamma<t\}=\bigcup_{q\in \mathbb{Q}\cap [0,t)}\{X_q\in \Gamma\}\in \mathcal{F}_t$$Hence, $H_\Gamma$ is an optional time.
2. For $x\in \mathbb{R}^d$, define $d(x,\Gamma)=\inf_{y\in\Gamma}d(x,y)$. We want to use the result of 1., so we construct a nondecreasing sequence of open neighborhood $\Gamma_n=\{x\in \mathbb{R}^d:d(x,\Gamma)<\frac{1}{n}\}$ and hitting time $T_n=H_{\Gamma_n}$. By 1., $T_n$ is optional and $T=\lim_{n\to\infty}T_n\le H_\Gamma$. It becomes two cases:first, $\{H_\Gamma=0\}$, then $T_n=0,\forall n\ge1$. Second, $\{H_\Gamma>0\}$, then $\exists k=k(\omega)\ge1$ s.t. $T_n=0,1\le n<k$ and $0<T_n<T_{n+1}<H_\Gamma,n\ge k$. It suffices to show $T\ge H_\Gamma$ on the event $\{H>0,T<\infty\}$.
   If $\{H_\Gamma=0\}$, then $\{H_\Gamma=0\}=\{X_0\in \Gamma\}\in\mathcal{F}_t$. For $\{H_\Gamma>0\}$, since the continuity sample of $X$, $X_T=\lim_{n\to\infty}X_{T_n}$ and $X_m\in \partial\Gamma_m\subseteq\Gamma_n,m>n\ge k$. Let $m\to \infty$, $X_T\in\Gamma_n,n\ge k$ and thus $X_T\in \bigcap_{n=1}^{\infty}\Gamma=\Gamma$. Hence, $T\ge H$ and $\{H_\Gamma\le t\}=\bigcap_{n=1}^{\infty}\{T_n<t\}\in \mathcal{F}_t$ is a stopping time.

**QED**

> [!proposition] Arithmetic of stopping time
> 1. If $T$ is optional and $\theta$ is a positive constant, then $T+\theta$ is a stopping time.
> 2. If $T, S$ are stopping times, then so are $T \vee S=\max\{T,S\}$, $T \wedge S=\min\{T,S\}$, $T + S$.
> 3. Let $T, S$ be optional times, then $T + S$ is optional. It is a stopping time, if one of the following conditions holds:
>    - $T > 0, S > 0$;
>    - $T > 0$, $T$ is a stopping time.

^e32b22

**Proof**
1. If $t\ge\theta$, then $\{T+\theta\le t\}=\{T\le t-\theta\}\in \mathcal{F_{t-\theta}}\subseteq\mathcal{F}_t$. If $0\le t<\theta$, $\{T+\theta\le t\}=\emptyset\in\mathcal{F}_t$.
2. Note that $$\{T\vee S\le t\}=\{T\le t\}\cup\{S\le t\}\in\mathcal{F}_t$$ $$\{T\wedge S\le t\}=\{T\le t\}\cap\{S\le t\}\in\mathcal{F}_t$$For the third, we consider the decomposition $$\{T+S>t\}=\{T=0,S>t\}\cup\{T>t,S=0\}\cup\{0<T<t,T+S>t\}\cup\{T\ge t,S>0\}$$
3. Note that $$\{T+S<t\}=\bigcup_{q\in \mathbb{Q}\cap[0,t)}\{T<q\}\cap \{S<t-q\}\in \mathcal{F}_t$$ then $T+S$ is optional. SInce $\{T+s<t\}\in \mathcal{F}_t$, if we W.T.S $T+S$ is a stopping time, we suffices to prove $\{T+S=t\}\in\mathcal{F}_t$.
    **For item 2**,  for $k,n\in\mathbb{N}$, we define the event $$A_{n,k}=\{\frac{k}{2^n}\le T<\frac{k+1}{2^n}\}\cap\{t-\frac{k+1}{2^n}\le S<t-\frac{k}{2^n}\}$$Since $S$ is optional time and $T$ is stopping time, then $\{t-\frac{k+1}{2^n}\le S<t-\frac{k}{2^n}\}\in\mathcal{F}_t$, $\{\frac{k}{2^n}\le T<\frac{k+1}{2^n}\}\in\mathcal{F}_{\frac{k+1}{2^n}}$. We write $$\{T+S=t\}=\bigcup_{n=1}^{\infty}\bigcap_{k=0}^{\infty}A_{n,k}$$If $\frac{k+1}{2^n}\le t$, then $\mathcal{F}_\frac{k+1}{2^n}\subseteq\mathcal{F}_{t}$, $\{\frac{k}{2^n}\le T<\frac{k+1}{2^n}\}\in\mathcal{F}_t$ and $\{T+S=t\}\in \mathcal{F}_t$. If $\frac{k+1}{2^n}>t$, then necessarily $\frac{k}{2^n}\le t$, otherwise $\{t-\frac{k+1}{2^n}\le S<t-\frac{k}{2^n}\}=\emptyset$. On $A_{n,k}$, since $\{T+S=t\}$, we have $T\le t$ and $\{\frac{k+1}{2^n}\le T\le t\}\in \mathcal{F}_t$. Hence, $A_{n,k}\in \mathcal{F}_t$.
    **For item 1**,  

**QED**

> [!proposition] Limit arithmetic of stopping time
> Let $\{T\}_{n=1}^{\infty}$ be a sequence of optional times; then the random times
> $$
> \sup_{n\ge 1}T_n, \inf_{n\ge 1}T_n, \varlimsup_{n\to\infty}T_n, \varliminf_{n\to\infty}T_n
> $$
> are all optional. Furthermore, if the $T_n$'s are stopping times, then so is above all.

**Proof**
Note that $$\{\sup_{n\ge 1}T_n<t\} = \bigcap_{n\ge 1}\{T_n<t\}$$ $$\{\inf_{n\ge1}T_n<t\}=\bigcup_{n\ge 1}\{T_n<t\}$$ $$\varlimsup_{n\to\infty}T_n = \inf_{n\ge 1}\sup_{k\ge n}T_k$$ $$\varliminf_{n\to\infty}T_n = \sup_{n\ge 1}\inf_{k\ge n}T_k$$
**QED**

> [!def] Events determined prior to the stopping time
> Let $T$ be a stopping time of the filtration $\{\mathcal{F}_t\}$. The $\sigma$-field
> $$
> \mathcal{F}_T = \{A\in \mathcal{F}:A\cap \{T\le t\}\in \mathcal{F}_t\}
> $$
> of events determined prior to the stopping time $T$

> [!def] Events determined immediately after the optional time 
> Let $T$ be a optional time of the filtration $\{\mathcal{F}_t\}$. The $\sigma$-field
> $$
> \mathcal{F}_{T+} = \{A\in \mathcal{F}:A\cap \{T\le t\}\in \mathcal{F}_{t+}\}
> $$
> of events determined prior to the stopping time $T$

> [!def] Usual conditions
> A filtration $\mathcal{F}_t$ is said to satisfy the **usual conditions** if it is **right-continuous** and contains all the $\mathbb{P}$-negligible events in $\mathcal{F}$.

^47dba3

> [!warning]
> The set of jumps for a stochastic process whose sample paths do not admit discontinuities of the second kind.

> [!proposition]
> 1. $\mathcal{F}_T$ is actually a $\sigma$-field and $T$ is $\mathcal{F}_T$-measurable
> 2. If $T(\omega) = t$ for some constant $t > 0$ and every $\omega\in\Omega$, then $\mathcal{F}_T=\mathcal{F}_t$
> 3. the class $\{\mathcal{F}_{T+}\}$ is indeed a $\sigma$-field with respect to which $T$ is measurable, that it coincides with $\{A\in\mathcal{F};A\cap\{T < t\}\in \mathcal{F}_t\}$, and that if $T$ is a stopping time (so that both $\mathcal{F}_T,\mathcal{F}_{T+}$ are defined), then $\mathcal{F}_{T}\subseteq\mathcal{F}_{T+}$

^8059e9

**Proof**
1. For $\emptyset\cap \{T\le t\}=\emptyset,\Omega\cap\{T\le t\}=\{T\le t\}\in\mathcal{F}_t$. With $A\in \mathcal{F}_T$, then $A\cap \{T\le t\}\in \mathcal{F}_t$ $A^c\cap\{T\le t\}=(\Omega\cap\{T\le t\})\setminus(A\cap\{T\le t\})\in\mathcal{F}_t$. Suppose $\{A_n\}\subseteq\mathcal{F}_T$, then $(\bigcup_{n=1}^{\infty}A_n)\cap\{T\le t\}=\bigcup_{n=1}^{\infty}(A_n\cap\{T\le t\})\in \mathcal{F}_T$. For any $u\ge 0$, $\{T\le u\}\cap\{T\le t\}=\{T\le u\wedge t\}\in \mathcal{F}_{u\wedge t}\subseteq\mathcal{F}_t$, then $T$ is $\mathcal{F}_T$-measurable.
2. Assume $T(ω)=t$ for all $ω∈Ω$ with $t≥0$. Then $$\{T\le s\}=\begin{cases}
\emptyset,s<t\\
\Omega,s\ge t
\end{cases}$$For $A\in \mathcal{F}$, the set $A\cap \{T\le s\}\in\mathcal{F}_s$ for all $s$: If $s<t$, $A\cap\emptyset=\emptyset\in\mathcal{F}_s$; If $s\ge t$, $A\cap\Omega=A\in\mathcal{F}_s$. Then $A\in\mathcal{F}_T$ if an only if $A\in\mathcal{F}_s$ for $s\ge t$. Let $s=t$, then $\mathcal{F}_T=\mathcal{F}_t$
3. For $\emptyset\cap \{T\le t\}=\emptyset,\Omega\cap\{T\le t\}=\{T\le t\}\in\mathcal{F}_{t+}$. With $A\in \mathcal{F}_{T+}$, then $A\cap \{T\le t\}\in \mathcal{F}_{t+}$ $A^c\cap\{T\le t\}=(\Omega\cap\{T\le t\})\setminus(A\cap\{T\le t\})\in\mathcal{F}_{t+}$. Suppose $\{A_n\}\subseteq\mathcal{F}_{T+}$, then $(\bigcup_{n=1}^{\infty}A_n)\cap\{T\le t\}=\bigcup_{n=1}^{\infty}(A_n\cap\{T\le t\})\in \mathcal{F}_{T+}$. Next we W.T.S $$\{A\in\mathcal{F};A\cap\{T < t\}\in \mathcal{F}_t\}=\{A\in\mathcal{F};A\cap\{T \le t\}\in \mathcal{F}_{t+}\}$$
$\Longleftarrow$: Suppose $A\in RHS$, we consider $$A\cap\{T<t\}=\bigcup_{n=1}^{\infty}(A\cap\{T\le t-\frac{1}{n}\})\in\mathcal{F}_{(t-\frac{1}{n})+}=\bigcap_{n=1}^{\infty}\mathcal{F}_{t-\frac{1}{n}+\frac{1}{n}}=\mathcal{F}_t$$
$\Longrightarrow$: Suppose $A\in LHS$, we consider $$A\cap\{T\le t\} = \bigcap_{n=1}^{\infty}(A\cap\{T< t+\frac{1}{n}\})\in\bigcap_{n=1}^{\infty}\mathcal{F}_{(t+\frac{1}{n})}=\mathcal{F}_{t+}$$
The last claim can be got by $\{T<t\}\subset\{T\le t\}$.
**QED**

> [!proposition]
> For any two stopping times $T$ and $S$, and for any $A \in \mathcal{F}_S$, we have $A \cap \{S \le T\} \in \mathcal{F}_T$. In particular, if $S \le T$ on $\Omega$, we have $\mathcal{F}_S\subseteq \mathcal{F}_T$.

^4558a9

**Proof**
For $A\in \mathcal{F}_S$, we W.T.S $A\cap\{S\le T\}\in \mathcal{F}_T$ i.e. $A\cap\{S\le T\}\cap\{T\le t\}\in \mathcal{F}_t$. Note that $T\wedge t$ is also an $\mathcal{F}_t$-measurable random variable. We claim the follows from the decomposition:
$$
A\cap\{S\le T\}\cap\{T\le t\}=(A\cap \{S\le t\})\cap \{T\le t\}\cap \{S\wedge t\le T\wedge t\}\in\mathcal{F}_t
$$
**QED**

> [!proposition]
> Let $T$ and $S$ be stopping times. Then $\mathcal{F}_{T\wedge S}=\mathcal{F}_T\cap \mathcal{F}_S$, and each of the events
> $$
> \{T<S\},\{T\le S\},\{T>S\},\{T\ge S\},\{T=S\}\in \mathcal{F}_{T}\cap\mathcal{F}_{S}
> $$

^4a9887

**Proof**
By [[Stopping Times#^4558a9|last proposition]], $\mathcal{F}_{T\wedge S}\subseteq\mathcal{F}_T\cap\mathcal{F}_S$. Let $A\in \mathcal{F}_T\cap\mathcal{F}_S$ and 
$$
A\cap\{T\wedge S\le t\} = (A\cap\{T\le t\})\cup(A\cap\{S\le t\})\in\mathcal{F}_t
$$
Then $A\in \mathcal{F}_{T\wedge S}$. By [[Stopping Times#^4558a9|last proposition]] and note that the roles of $S$ and $T$ are the same, $\{S\le T\}\in\mathcal{F}_T$ and thus $\{S>T\}\in\mathcal{F}_T$. Let $R=S\wedge T$ is also a stopping time, then $\{S<T\}=\{R\le T\}\in \mathcal{F}_T$ and thus $\{S\ge T\}\in\mathcal{F}_T$. Interchanging $T,S$, we have $\{S\ge T\},\{S> T\}\in \mathcal{F}_S$. Hence, the above four sets belong to $\mathcal{F}_T\cap\mathcal{F}_S$. Besides, $\{T=S\}=\{T\le S\}\cap\{T\ge S\}$.
**QED**

> [!warning]
> The above two proposition is also true for events determined immediately after the optional time.

Now we can start to appreciate the usefulness of the concept of stopping time in the study of stochastic processes.

> [!proposition]
> Let $X$ be a progressively measurable process, and let $T$ be a stopping time of the filtration $\{\mathcal{F}_t\}$. Then the random variable $X_T$ , defined on the set $\{T<\infty\}\in\mathcal{F}_T$ is $\mathcal{F}_T$-measurable, and the **stopped process** $X_{T\wedge t}$ is progressively measurable.

**Proof**
In order to show $X_T$ is $\mathcal{F}_T$-measurable, we W.T.S for any Borel set $B\in\mathcal{B}(\mathbb{R}^d)$, $\{X_T\in B\}\cap\{T\le t\}\in\mathcal{F}_t$. This event is also writed as $\{X_{T\wedge t}\in B\}\cap \{T\le t\}$. It suffices to show that $X_{T\wedge t}$ is progressively measurable. We observe that mapping
$$
(s,\omega)\mapsto(T(\omega)\wedge s,\omega),[0,t]\times\Omega\to [0,t]\times\Omega
$$
is $\mathcal{B}([0,t])\otimes\mathcal{F}_t$-measurable. Since $X$ is progressively measurable, then the mapping 
$$
(s,\omega)\mapsto X_{s}(\omega),([0,t]\times\Omega,\mathcal{B}([0,t])\otimes\mathcal{F}_t)\to (\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))
$$
is measurable, so is $(s,\omega)\mapsto X_{T(\omega)\wedge s}(\omega)$.
**QED**

> [!question]
> Under the same assumptions and with $f(t, x): [0, \infty) \times \mathbb{R}^d\to \mathbb{R}$ a bounded, $\mathcal{B}([0,\infty))\otimes\mathcal{B}(\mathbb{R}^d)$-measurable function, show that the process $Y_t=\int_{0}^{t}f(s,X_s){d}s$ is progressively measurable with respect to $\{\mathcal{F}_t\}$, and $Y_T$ is $\mathcal{F}_T$-measurable.

^ee15ca

> [!done]
> We note that the technique of the above proposition is how to decompose the mappings. Similarly, it is crucial to decompose $Y_t$. Since $X$ is progressively measurable, then the mapping 
> $$
> (s,\omega)\mapsto(s,X_s(\omega)),(\mathbb{R}^+\times\Omega,\mathcal{B}(\mathbb{R}^+)\otimes\mathcal{F})\to(\mathbb{R}^+\times\mathbb{R}^d,\mathcal{B}(\mathbb{R}^+)\otimes\mathcal{B}(\mathbb{R}^d))
> $$
> is measurable. Since $f(t,x)$ is bounded and measurable, then 
> $$
> (s,X_s(\omega))\mapsto f(s,X_s(\omega)),(\mathbb{R}^+\times\mathbb{R}^d,\mathcal{B}(\mathbb{R}^+)\otimes\mathcal{B}(\mathbb{R}^d))\to(\mathbb{R},\mathcal{B}(\mathbb{R}))
> $$
> is also measurable. Let $g(s,\omega)=f\circ X(s,\omega)$, for $s\in[0,t]$, by Fubini Theorem, $Y_{t}=\int_{0}^{t}f(s,X_s){d}s = \int_{0}^{t}g(s,\omega){d}s$ is $\mathcal{F}_t$-measurable. Indeed, the mapping 
> $$
> (s,\omega)\mapsto Y_s(\omega),([0,t]\times\Omega,\mathcal{B}([0,t])\otimes\mathcal{F}_t)\to(\mathbb{R},\mathcal{B}(\mathbb{R}))
> $$
> is measurable. Hence, $Y_t$ is progressively measurable. By the above proposition, $Y_T$ is $\mathcal{F}_T$-measurable.

---
## Exercises

> [!question]
> If the process $X$ is measurable and the random time $T$ is finite, then the function $X_T$ is a random variable.

> [!done]
> We consider the mappings:
> $$
> (t,\omega)\mapsto X_t(\omega),[0,\infty)\times\Omega\to\mathbb{R}^d
> $$
> $$
> \omega\mapsto(T(\omega),\omega),\Omega\to [0,\infty)\times\Omega
> $$
> Since $X_t$ is measurable, then the first mapping is measurable. It suffices to show the second mapping is measurable. Let $\varphi(\omega)=(T(\omega),\omega)$, suppose $B\in\mathcal{B}([0,\infty))$ and $C\in\mathcal{F}$, then 
> $$
> \varphi^{-1}(B\times C)=T^{-1}(B)\cap C\in\mathcal{F}
> $$
> Hence, $X_{T(\omega)}(\omega)=X(T(\omega),\omega)=X\circ\varphi(\omega)$ is measurable and $X_T$ is a random variable.

> [!question]
> Let $X$ be a measurable process and $T$ a random time. Show that the collection of all sets of the form $\{X_T \in A\}$; $A \in \mathcal{B}(\mathbb{R})$, together with the set $\{T = \infty\}$, forms a sub-$\sigma$-field of $\mathcal{F}$. We call this the $\sigma$-field generated by $X_T$.

> [!done]
> By the above question, for $A\in\mathcal{B}(\mathbb{R})$, $X_T$ is measurable and $\{X_T\in A\}\in\mathcal{F}$. $T$ is random time and thus $\{T=\infty\}\in\mathcal{F}$. Consider the generating $\sigma$-field, 
> $$
> \mathscr{G}=\sigma\left(\{\{X_T\in A\}:A\in\mathcal{B}(\mathbb{R})\}\cup\{T=\infty\}\right)
> $$
> then $\mathscr{G}\subseteq\mathcal{F}$ is a sub-$\sigma$-field.

> [!question]
> Let $X$ be a stochastic process and $T$ a stopping time of $\{\mathcal{F}^X_t\}$. Suppose that for any $\omega,\omega'\in \Omega$, we have $X_t(\omega)=X_t(\omega')$ for all $t\in [0,T(\omega)]\cap [0,\infty)$. Show that $T(\omega)=T(\omega')$.

> [!done]
> Suppose $T(\omega)>T(\omega')$, let $t=T(\omega')$. Since $T$ is a stopping time of $\{\mathcal{F}^X_t\}$, $\{T\le t\}\in\mathcal{F}^X_t$. For any $s\in[0,T(\omega)]\cap[0,\infty)$, $X_s(\omega)=X_s(\omega')$, it implies that $\omega,\omega'$ have the same sample paths. Therefore, they either all belong to $\{T\le t\}$ or not all belong to. By $t=T(\omega')\le t$, then $\omega\in\{T\le t\}$. But $T(\omega)>t$, it is a contradiction. Hence, $T(\omega)\le T(\omega')$. Similarly, it holds $T(\omega)\ge T(\omega')$.

> [!question]
> Let $T$ be a stopping time and $S$ a random time such that $S \ge T$ on $\Omega$. If $S$ is $\mathcal{F}_T$-measurable, then it is also a stopping time.

> [!done]
> Since $S\ge T$, for $t\ge 0$, $\{S\le t\}\subseteq\{T\le t\}$ and $\{S\le t\}\cap\{T\le t\}=\{S\le t\}$. With $S$ is $\mathcal{F}_T$-measurable, then $\{S\le t\}\cap\{T\le t\}=\{S\le t\}\in \mathcal{F}_t$

> [!question]
> Let $T, S$ be stopping times and $Z$ an integrable random variable. We have
> 1. $\mathbb{E}(Z|\mathcal{F}_T)=\mathbb{E}(Z|\mathcal{F}_{S\wedge T})$,$\mathbb{P}-a.s.$ on $\{T\le S\}$
> 2. $\mathbb{E}[\mathbb{E}(Z|\mathcal{F}_T)|\mathcal{F}_S]=\mathbb{E}(Z|\mathcal{F}_{T\wedge S}),\mathbb{P}-a.s.$

> [!done]
> By [[Stopping Times#^4558a9|Proposition]] and [[#^4a9887|Proposition]], we have 
> $$
> \mathcal{F}_T\subseteq\mathcal{F}_S,\mathcal{F}_{T\wedge S}=\mathcal{F}_T\cap\mathcal{F}_S=\mathcal{F}_T
> $$
> Hence, $\mathbb{E}(Z|\mathcal{F}_T)=\mathbb{E}(Z|\mathcal{F}_{S\wedge T})$.
> We consider the decomposition on $\Omega$. 
> $$
> \Omega=\{S<T\}\cup\{T\le S\}
> $$
> On $\{S<T\}$, then $\mathcal{F}_S\subset\mathcal{F}_T$ and $\mathbb{E}[\mathbb{E}(Z|\mathcal{F}_T)|\mathcal{F}_S]=\mathbb{E}[Z|\mathcal{F}_S]=\mathbb{E}[Z|\mathcal{F}_{T\wedge S}]$. Similarly, on $\{T\le S\}$, $\mathbb{E}[\mathbb{E}(Z|\mathcal{F}_T)|\mathcal{F}_S]=\mathbb{E}[Z|\mathcal{F}_T]=\mathbb{E}[Z|\mathcal{F}_{T\wedge S}]$. Hence, on $\Omega$, we have $$\mathbb{E}[\mathbb{E}(Z|\mathcal{F}_T)|\mathcal{F}_S]=\mathbb{E}[Z|\mathcal{F}_{T\wedge S}]$$

> [!question]
> Show that if $\{T_n\}_{n=1}^{\infty}$, is a sequence of optional times and $T = \inf_{n\ge 1}T_n$, then $\mathcal{F}_{T+}=\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n+}$ Besides, if each $T_n$ is a positive stopping time and $T < T_n$ on $\{T < \infty\}$, then we have $\mathcal{F}_{T+}=\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n}$

^256794

> [!done]
> We use the definition of [[Stopping Times#^8059e9|Proposition 3.]]
> 1. **For the first claim**
>    - $\mathcal{F}_{T+}\subseteq\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n+}$. For $A\in\mathcal{F}_{T+}$ i.e. $A\cap\{T<t\}\in\mathcal{F}_{t}$. Since $T=\inf_{n\ge 1}T_n$, then $T\le T_n$ and $\{T_n<t\}\subseteq\{T<t\}$. Hence, for any $n\in\mathbb{N}$, $A\cap\{T_n<t\}\subseteq A\cap\{T<t\}\in\mathcal{F}_{t}$, $A\in\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n+}$
>    - $\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n+}\subseteq\mathcal{F}_{T+}$. For $A\in \bigcap_{n=1}^{\infty}\mathcal{F}_{T_n+}$, for any $n\in\mathbb{N}$, $A\in\mathcal{F}_{T_n+}$ i.e. $A\cap\{T_n<t\}\in\mathcal{F}_t$. Since $T=\inf_{n\ge 1}T_n$, then $\{T<t\}=\{\inf_{n\ge 1}T_n<t\}=\bigcup_{n=1}^{\infty}\{T_n<t\}$. Hence, $$A\cap\{T<t\}=A\cap\bigcup_{n=1}^{\infty}\{T_n<t\}=\bigcup_{n=1}^{\infty}(A\cap\{T_n<t\})\in\mathcal{F}_t$$Therefore, $A\in\mathcal{F}_{T+}$
> 2. **For the second claim**.
>    - $\mathcal{F}_{T+}\subseteq\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n}$. For $A\in \mathcal{F}_{T+}$ i.e. $A\cap\{T<t\}\in\mathcal{F}_t$. Since $T<T_n$, then $T_n\le t\Longrightarrow T<t$ and $\{T_n\le t\}\subseteq\{T<t\}$. Hence, $A\cap\{T_n\le t\}\subseteq A\cap\{T<t\}$ for any $n\in\mathbb{N}$. Therefore, $A\in\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n}$
>    - $\bigcap_{n=1}^{\infty}\mathcal{F}_{T_n}\subseteq\mathcal{F}_{T+}$. For $A\in \bigcap_{n=1}^{\infty}\mathcal{F}_{T_n}$, $\forall n\in\mathbb{N}$, $A\in\mathcal{F}_{T_n}$ i.e. $A\cap\{T_n\le t\}\in\mathcal{F}_t$. Since $T=\inf_{n\ge 1}T_n$, then $\{T<t\}=\{\inf_{n\ge 1}T_n<t\}=\bigcup_{n=1}^{\infty}\{T_n<t\}$ and $$A\cap\{T<t\}=\bigcup_{n=1}^{\infty}(A\cap\{T_n<t\})\subseteq\bigcup_{n=1}^{\infty}(A\cap\{T_n\le t\})\in\mathcal{F}_t$$ Therefore, $A\in\mathcal{F}_{T+}$.

> [!question]
> Given an optional time $T$ of the filtration $\{\mathcal{F}_t\}$, consider the sequence $\{T_n\}_{n=1}^{\infty}$ of random times given by
> $$
> T_n(\omega)=\begin{cases}
> T(\omega), &\{\omega:T(\omega)=+\infty\}\\
> \frac{k}{2^n},&\{\omega:\frac{k-1}{2^n}\le T<\frac{k}{2^n}\},k=1,2,\cdots,2^n
> \end{cases}
> $$
> for $n \le 1, k \le 1$. Obviously $T_n \ge T_{n+1} \ge T$, for every $n \le 1$. Show that each $T_n$ is a stopping time, that $\lim_{n\to\infty} T_n = T$, and that for every $A\in \mathcal{F}_{T+}$ we have $A\cap \{T_n=\frac{k}{2^n}\}\in\mathcal{F}_{\frac{k}{2^n}}$

^33bc9e

> [!done]
> - If $\omega\in\{T=+\infty\}$, the set $\{T_n\le t\}=\{T\le t\}=\emptyset\in\mathcal{F}_t$. If $\omega\in\{\frac{k-1}{2^n}\le T<\frac{k}{2^n}\},k=1,2,\cdots,2^n$, let $K=\{k:\frac{k}{2^n}\le t\}$, by $T$ is an optional time then
> $$
> \{T_n\le t\}=\bigcup_{k\in K}\{\frac{k-1}{2^n}\le T<\frac{k}{2^n}\}=\bigcup_{k\in K}(\{T<\frac{k}{2^n}\}\setminus\{T<\frac{k-1}{2^n}\})\in\mathcal{F}_t
> $$
> Hence, $T_n$ is a stopping time. 
> - If $T=\infty$, obviously $\lim_{n\to \infty}T_n=\infty$. If $\frac{k-1}{2^n}\le T<\frac{k}{2^n}$ for any $n\in\mathbb{N}$ and $k=1,2,\cdots,2^n$, then 
> $$
> |T_n-T|=|\frac{k}{2^n}-T|\le \frac{1}{2^n}\to 0,n\to\infty
> $$
> Hence, $\lim_{n\to\infty}T_n=T$.
> - Since $A\in\mathcal{F}_{T+}$, $A\cap\{T<t\}\in\mathcal{F}_{t}$. Note that $\{T_n=\frac{k}{2^n}\}=\{\frac{k-1}{2^n}\le T<\frac{k}{2^n}\}$ and $T$ is an optional time 
>   $$
>   A\cap\{T_n=\frac{k}{2^n}\}=A\cap\{\frac{k-1}{2^n}\le T<\frac{k}{2^n}\}=A\cap(\{T<\frac{k}{2^n}\}\setminus\{T<\frac{k-1}{2^n}\})
>   $$
>   Let $t=\frac{k}{2^n}$, then $A\cap\{T_n=\frac{k}{2^n}\}\in\mathcal{F}_{\frac{k}{2^n}}$
