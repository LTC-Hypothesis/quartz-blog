> [!def] stochastic process
> A stochastic process is a collection of random variables $X=\{X_t\ :\ 0\le t<\infty\}$ on **probability space** $(\Omega,\mathcal{F})$, which take values in a second measurable space $(S,\mathscr{S})$, called the **state space**. 

> [!warning]
> - In our note, we let $S=\mathbb{R}^d,\mathscr{S}=\mathcal{B}(\mathbb{R}^d)$
> - The index $t\in [0,\infty)$ admits a convenient interpretation as **time**.

> [!def] Sample path
> For a fixed sample point $\omega\in \Omega$, the function $t\mapsto X_t(\omega)$ is the **sample path** of the process $X$ associated with $\omega$

> [!def] Two stochastic process are the same
> Let us consider two stochastic processes $X$ and $Y$ defined on the same probability space $(\Omega,\mathcal{F},\mathbb{P})$. we would say $X$ and $Y$ were the same if and only if $X_t(\omega)=Y_t(\omega)$ for all $\omega\in \Omega$ and $t\ge 0$. 

The three weaker concept of "sameness" between two stochastic process are following: 

> [!def] modification
> $Y$ is a modification of $X$ if, for every $t\ge 0$, we have $\mathbb{P}[X_t = Y_t] = 1$.

> [!def] indistinguishable(the strongest)
> $X$ and $Y$ are called indistinguishable if almost all their sample paths agree: $\mathbb{P}(X_t=Y_t;0\le t<\infty)=1$

> [!warning] How to comprehend the differece between modification and indistinguishable
> **Modification:**
> - **Focus:** A single, fixed point in time $t$.     
> - **Logic:** If you pick a specific time $t$ in advance (like $t=3.5$), the probability that $X$ and $Y$ differ at that exact moment is zero.    
> - **The Catch:** The set of "bad" sample paths ωω where they differ can be **different for every $t$**. Since time is continuous (uncountably infinite), the union of all these "bad" sets might not have probability zero.   
> 
> **Indistinguishable:**
> - **Focus:** The entire sample path (the function $t↦X_t$​).    
> - **Logic:** There is a single set of "bad" sample paths with probability zero. If you remove that set, then for the remaining $\omega$, $X_t(ω)$ equals $Y_t(ω)$ for **every single moment** $t$ in the time interval $[0,∞)$.
> - **Key Point:** It requires the two trajectories to be identical everywhere, almost surely.
> 
> If $Y$ is a **modification** of $X$, they are equal at any given time with probability 1, but which exact paths are "bad" can depend on the time you look at. If they are **indistinguishable**, there is a single set of probability 1 where the two functions are identical over the whole timeline.

> [!def] finite-dimensional distributions
> $X$ and $Y$ have the same finite-dimensional distributions if, for any integer $n\ge 1$, real number $0\le t_1<t_2<\cdots<t_n<\infty$, and $A\in \mathcal{B}(\mathbb{R}^{nd})$, we have 
> $$
> \mathbb{P}[(X_{t_1},X_{t_2},\cdots,X_{t_n})\in A] = \mathbb{P}[(Y_{t_1},Y_{t_2},\cdots,Y_{t_n})\in A]
> $$

> [!warning]
> indistinguishable $\Longrightarrow$ modification $\Longrightarrow$ finite-dimensional distributions. But A modification is **not necessarily** indistinguishable.

> [!example]
> Consider a positive random variable $T$ with continuous distribution, let 
> $$
> X_t=0,Y_t=\begin{cases}
> 0,T\ne t\\
> 1,T=t
> \end{cases}
> $$
> It is tivial that $Y_t$ is a modification of $X_t$. Hence, for every $t\ge 0$, $\mathbb{P}(X_t=Y_t)=\mathbb{P}(T\ne t)=1$. However, $\mathbb{P}(Y_t=X_t;0\le t<\infty)=0$.

> [!question] How can **modification $\Longrightarrow$ indistinguishable**? A positive result: Let $Y$ be a modification of $X$, and suppose that both processes have **a.s. right-continuous sample paths**. Then $X$ and $Y$ are indistinguishable.

^a7c078

> [!done]
> Since $Y$ is a modification of $X$, then for every $t\ge 0$, $\mathbb{P}[X_t\ne Y_t]=0$. Suppose 
> $$
> N_t=\{\omega:X_t(\omega)\ne Y_t(\omega)\},\mathbb{P}(N_t)=0
> $$
> We choose rational number $\mathbb{Q}_+$, let 
> $$
> N=\bigcup_{q\in\mathbb{Q}_+}N_q,\mathbb{P}(N)=0
> $$
> Since $X,Y$ has a.s. right-continuous sample paths, there exists $M_X,M_Y$, for $\omega\notin M_X\cup M_Y$, $t\mapsto X_t,Y_t$ is right-continuous i.e. for any $t$, choose a sequence of rational number $\{q_n\}$ s.t. $q_n\to t$. Let $M=M_X\cup M_Y\cup N$, $\mathbb{P}(M)=0$.For $\omega\notin M$, we have $X_q(\omega)=Y_q(\omega)$ for any $q\in\mathbb{Q}_+$ and 
> $$
> X_t(\omega)=\lim_{n\to \infty}X_{q_n}(\omega)=\lim_{n\to\infty}Y_{q_n}(\omega)=Y_t(\omega),\forall t\ge 0
> $$
> Hence, $X$ and $Y$ are the same on $\Omega\setminus M$ and $\mathbb{P}[X_t=Y_t,t\ge 0]=1$.

If $X$ and $Y$ have the same state space but are defined on different probability spaces, we can ask whether they have the same finite-dimensional distributions.

> [!def] finite-dimensional distributions of different probability space
> Let $X$ and $Y$ be stochastic processes defined on probability spaces $(\Omega,\mathcal{F},\mathbb{P})$ and $(\tilde{\Omega},\tilde{\mathcal{F}},\tilde{\mathbb{P}})$ and having the same state space $(S,\mathscr{S})$. $X$ and $Y$ have the same finite-dimensional distributions if, for any integer $n \ge 1$, real numbers $0\le t_1<t_2<\cdots<t_n<\infty$, and $A\in \mathcal{B}(\mathbb{R}^{nd})$, we have 
> $$
> \mathbb{P}[(X_{t_1},X_{t_2},\cdots,X_{t_n})\in A] = \tilde{\mathbb{P}}[(Y_{t_1},Y_{t_2},\cdots,Y_{t_n})\in A]
> $$

> [!def] Measurable
> The stochastic process $X$ is called measurable if, for every $A\in \mathcal{B}(\mathbb{R}^d)$, the set $\{(t,\omega)\ :\ X_t(\omega)\in A\}\in \mathcal{B}[0,\infty)\otimes \mathcal{F}$ i.e. the mapping $$
> (t,\omega)\mapsto X_t(\omega):([0,\infty)\times\Omega,\mathcal{B}[0,\infty)\otimes \mathcal{F})\to (\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))
> $$is measurable.

> [!warning]
> By Fubini theorem, the sample path $t\mapsto X_t(\omega)$ is Borel measurable, then the same is true for $m(t)=\mathbb{E}(X_t)$. Moreover, if $X$ takes values in $\mathbb{R}$ and $I$ is a subinterval of $[0, \infty)$ such that $\int_{I}\mathbb{E}|X_t|{d}t<\infty$, then expectation and integral of path can exchange
> $$
> \int_{I}|X_t|{d}t<\infty, \int_I\mathbb{E}X_t{d}t=\mathbb{E}\int_IX_t{d}t
> $$

> [!def] filtration
> We equip our sample space $(\Omega,\mathcal{F})$ with a filtration i.e. a **nondecreasing sub $\sigma$-fields** $\{\mathcal{F}_t ; t\ge 0\}$ of $\mathcal{F}$. We set $\mathcal{F}_{\infty}=\sigma(\bigcup_{t\ge 0}\mathcal{F}_t)$

> [!def] Natural filtration
> Given a stochastic process, the simplest choice of a filtration is that generated by the process itself, $\mathcal{F}^X_t=\sigma(X_s;0\le s\le t)$. The smallest $\sigma$-field with respect to which $X$, is measurable for every $s \in [0, t]$

> [!warning]
> Filtration is to keep track of **information**, which is a very important reason we study in stochastic process. we can talk about a **past, present, and future** and can ask how much an observer of the process knows about it at present, as compared to how much he knew at some point in the past or will know at some point in the future. 
> 
> We interpret $A\in \mathcal{F}^X_t$ to mean that by time $t$, an observer of $X$ knows whether or not $A$ has occurred.

> [!def] Events strictly prior, events immediately after and right- (left-) continuous
> **Events strictly prior**: $\mathcal{F}_{t-}=\sigma(\bigcup_{s<t}\mathcal{F}_s)$. $\mathcal{F}_{0-}=\mathcal{F}_{0}$
> 
> **Events immediately after**: $\mathcal{F}_{t+}=\bigcap_{\varepsilon>0}\mathcal{F}_{t+\varepsilon}$
> 
> We say the filtration $\{\mathcal{F}_t\}$ is right- (left-) continuous if $\mathcal{F}_t=\mathcal{F}_{t+}(\mathcal{F}_t=\mathcal{F}_{t-})$ for every $t\ge 0$.

> [!def] Adapted to the filtration
> The stochastic process $X$ is **adapted to the filtration** $\{\mathcal{F}_t\}$ if for each $t > 0$, $X$ is an $\mathcal{F}_t$- measurable random variable. Obviously, every process $X$ is adapted to $\{\mathcal{F}^X_t\}$. Moreover, if $X$ is adapted to $\{\mathcal{F}^X_t\}$, and $Y$ is a modification of $X$, then $Y$ is also adapted to $\{\mathcal{F}^X_t\}$ provided that $\mathcal{F}_0$ contains all the $\mathbb{P}$-negligible sets in $\mathcal{F}$.

> [!def] Progressively measurable
> The stochastic process $X$ is called **progressively measurable** with respect to the filtration $\{\mathcal{F}_t\}$ if for each $t > 0$ and $A\in \mathcal{B}(\mathbb{R}^d)$, the set $$\{(s,\omega) : 0\le s\le t,\omega\in \Omega, X_s(\omega)\in A \}\in \mathcal{B}([0,t])\otimes \mathcal{F}_t$$
> In other words, the mapping $(s,\omega)\mapsto X_s(\omega):([0,t]\times\Omega,\mathcal{B}[0,t]\otimes \mathcal{F})\to (\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$ is measurable.

> [!warning]
> - Evidently, any progressively measurable process is measurable and adapted.
> - **(1965 Chung&Meyer)**If the stochastic process $X$ is **measurable and adapted to the filtration $\{\mathcal{F}_t\}$**, then it has a progressively measurable **modification**.

^7002e8

> [!proposition]
> If the stochastic process $X$ is adapted to the filtration $\{\mathcal{F}_t\}$ and every sample path is **right-continuous** or else every sample path is **left-continuous**, then $X$ is also progressively measurable with respect to $\{\mathcal{F}_t\}$

**Proof**
We treat the cases of right-continuous. With $t\ge 0$, $\forall n\in\mathbb{N}$,  $k=1,\cdots,2^n$, $0\le s\le t$ and $\omega\in \Omega$, we construct the process
$$
X^{(n)}_0(\omega)=X_0(\omega),X^{n}_s(\omega)=X^{(n)}_{\frac{(k+1)}{2^n}t}(\omega),\frac{kt}{2^n}<s\le \frac{(k+1)t}{2^n}
$$
Since $X$ is adapted to the filtration $\{\mathcal{F}_t\}$, each map $(s,\omega)\mapsto X^{(n)}_s(\omega)$ is $\mathcal{B}([0,t])\otimes \mathcal{F}_t$ measurable and $X^{(n)}_s$ can be represented as 
$$
X^{(n)}_s=X^{(n)}_0(\omega)\mathbb{1}_{0}(s)+\sum_{k=1}^{2^n-1}X^{(n)}_s(\omega)\mathbb{1}_{(\frac{kt}{2^n},\frac{(k+1)t}{2^n}]}(s)
$$
Hence, $X^{(n)}_s$ is also progressive measurable. By right-continuous and limit can hold, $\lim_{n\to\infty}X^{(n)}_s(\omega)=X_s(\omega)$, therefore, $X_s(\omega)$ is also progressive measurable.
**QED**

> [!warning]
> If $X$ is right- or left-continuous, but not necessarily adapted to $\{\mathcal{F}_t\}$, $X$ is measurable.

---
## Exercises

> [!question]
> Let $X$ be a process, every sample path of which is **RCLL** (right-continuous on $[0,\infty)$ with finite left-hand limits on $(0,\infty))$. Let $A$ be the event that $X$ is continuous on $[0, t_0)$. Show that $A\in \mathcal{F}^X_{t_0}$

> [!done]
> Suppose $\{t_k\}_{k=1}^{\infty}$ be a sequence of rational number s.t. $[0,t_k]\subset[0,t_0)$. By RCLL of $X_t$, $X_t$ is continuous on $[0,t_0)$ iff $X_t$ is continuous on every $[0,t_k]$. Since $[0,t_k]$ is closed interval, $X_t$ is uniformly continuous on $[0,t_k]$. Thus, $\forall m\in\mathbb{N}$, there exists $n\in\mathbb{N}$ s.t. for $s,r\in\mathbb{Q}\cap[0,t_k]$, $|s-r|<\frac{1}{n}\Longrightarrow |X_s-X_r|<\frac{1}{m}$. Then A can be writed as 
> $$
> A=\bigcap_{m=1}^{\infty}\bigcup_{n=1}^{\infty}\bigcap_{|s-r|<\frac{1}{n}}\{|X_s-X_r|<\frac{1}{m}\}
> $$
> Since $s,r\le t_k<t_0$, then the event $\{|X_s-X_r|<\frac{1}{m}\}\in\mathcal{F}^X_{t_0}$. By properties of $\sigma$-algebra, $A\in\mathcal{F}^X_{t_0}$.

> [!question]
> Let $X$ be a process whose sample paths are RCLL almost surely, and let $A$ be the event that $X$ is continuous on $[0, t_0)$. Show that $A\notin \mathcal{F}^X_{t_0}$, but if $\{\mathcal{F}_{t}\}$ is a filtration satisfying $\mathcal{F}^X_{t_0}\subseteq \mathcal{F}_t$ and $\mathcal{F}_{t_0}$ is complete under $\mathbb{P}$, then $A\in \mathcal{F}_{t_0}$

> [!done]
> We construct an example to illustrate $A\notin \mathcal{F}^X_{t_0}$. We construct such probability space and process. 
> 
> - Let $\Omega=[0,2]$, $\mathcal{F}=\mathcal{B}([0,2])$. Define the probability measure as $\mathbb{P}(F)=Leb(F\cap[0,1])$ for $F\in\mathcal{F}$.
> - Define the process
>   $$
>   X_t=\begin{cases}
> 0,&\omega\in[0,1]\\
> 0,&\omega\in(1,2),t\ne\omega\\
> 1,&\omega\in(1,2),t=\omega
> \end{cases}
>   $$
>   It implies a jump on $t=\omega$.
> 
> Let $t_0=2$, the event $A=[0,1]$. Now, natural filtration $\mathcal{F}^X_{2}$ is formed by the set of $\{(X_{t_1},X_{t_2},\cdots)\in B\}$. $\{t_k\}$ is a countable sequence in $[0,2]$, $B\in\mathcal{B}(\mathbb{R}^d)\otimes\mathcal{B}(\mathbb{R}^d)\otimes\cdots$ is product Borel set. Suppose $A\in\mathcal{F}^X_2$, then exists sequence $\{t_k\}$ and $B$ Borel set s.t. 
> $$
> A=\{(X_{t_k})\in B\}
> $$
> Since $(1,2)$ is uncountable, there exists $t\ne t_k,\forall k$. For $\omega= \bar{t}$, $X_{t_k}(\bar{t})=0$ and $\bar{t}\notin A$. Therefore, $(0,0,\cdots)\notin B$. But for any $\omega\in[0,1]$, $X_{t_k}(\omega)=0$, therefore, $\omega\in [0,1]$ but $\omega\notin A$. Hence, $[0,1]\cap A=\emptyset$, it is a contradiction! Hence, $A\notin \mathcal{F}^X_2$
> We next show the second claim. Let $N\subseteq\Omega$ which $X$ is not RCLL, and 
> $$
> A_n=\bigcap_{m=1}^{\infty}\bigcup_{q_1,q_2\in\mathbb{Q}\cap[0,t_0),|q_1-q_2|<\frac{1}{m}}\left\{|X_{q_1}-X_{q_2}|>\frac{1}{n}\right\}
> $$
> Then 
> $$
> A=\left(\bigcup_{n=1}^{\infty}A_n\right)^c\cap N^c\in\mathcal{F}_{t_0}
> $$

> [!question]
> Let $X$ be a process with every sample path LCRL (left-continuous on $(0, \infty)$ with finite right-hand limits on $[0, \infty)$), and let $A$ be the event that $X$ is continuous on $[0, t_0]$. Let $X$ be adapted to a right-continuous filtration $\{\mathcal{F}_t\}$. Show that $A\in \mathcal{F}_{t_0}$

> [!done]
> 