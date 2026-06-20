If $B_t$ is given but without filtration, it has stationary, independent increments and $B_t-B_s\sim N(0,t-s)$. By the [[Kolmogorov's Construction of Brownian Motion#^a01520|Exercise]], we konw $\{B_t,\mathcal{F}^B_t\}$ is a Brownian motion. In general, it is often interesting, and necessary, to work with a "large" filtration $\{\mathcal{F}_t\}$ which s.t. $\mathcal{F}^B_t\subseteq\mathcal{F}_t$. We know if $B_t-B_s\bot\mathcal{F}_s$, $\{B_t,\mathcal{F}_t\}$ is also Brownian motion.

> [!def]
> Let process $X_t$ with initial distribution $\mu$ on the space $(\Omega,\mathcal{F}^X_\infty,\mathbb{P}^\mu)$, where $\mathbb{P}^{\mu}(X_0\in\Gamma)=\mu(\Gamma),\Gamma\in\mathcal{B}(\mathbb{R}^d)$. We set for $0\le t<\infty$,
> $$
> \mathscr{N}^\mu_t=\{F\subseteq\Omega:\exists G\in\mathcal{F}^X_t,F\subseteq G,\mathbb{P}^{\mu}(G)=0
> $$
> $\mathscr{N}^\mu_\infty$ will be called "the collection of fm-null sets" and denoted simply by $\mathscr{N}^\mu$

> [!def]
> For $0\le t<\infty$,
> 1. **The completion**: $\mathcal{\bar{F}}_t^{\mu}=\sigma(\mathcal{F}^X_t\cup\mathscr{N}^\mu_t)$
> 2. **The augmentation**: $\mathcal{F}^\mu_t=\sigma(\mathcal{F}^X_t\cup\mathscr{N}^\mu_t)$
> 
> For $t=\infty$, $\mathcal{F}^\mu=\sigma(\mathcal{F}^X_\infty\cup\mathscr{N}^\mu)$. 

# Right-Continuity of the Augmented Filtration for a Strong Markov process

> [!proposition]
> For a d-dimensional strong Markov process $X_t$ with initial distribution $\mu$, the augmented filtration $\{\mathcal{F}^\mu_t\}$ is right-continuous.

> [!proposition]
> For a d-dimensional, left-continuous strong Markov process $X_t$ with initial distribution $\mu$, the augmented filtration $\{\mathcal{F}^\mu_t\}$ is continuous. 

> [!thm]
> Let $B_t$ be d-dimensional Brownian motion with initial distribution $\mu$ on $(\Omega,\mathcal{F}^B_\infty,\mathbb{P}^\mu)$. Relative to the filtration $\{\mathcal{F}^\mu_t\}$, $B_t$ is still a d-dimensional Brownian motion.

# A "Universal" filtration

> [!def]
> We define $\tilde{\mathcal{F}}_{t}\triangleq\bigcap_{\mu}\mathcal{F}^\mu_t$ where the intersection is over all probability measures $\mu$ on $(\mathbb{R}^d,\mathcal{B}(\mathbb{R}^d))$. Note that 
> $$
> \mathcal{F}^X_t\subseteq\tilde{\mathcal{F}}_t\subseteq\mathcal{F}^\mu_t
> $$

> [!proposition]
> If $\{X_t,\mathcal{F}^X_t\}$ and $\{X_t,\mathcal{F}^\mu_t\}$ are both strongly Markovian under $\mathbb{P}^\mu$, then so is $\{X_t,\tilde{\mathcal{F}}\}$. 

> [!proposition]
> $\{\tilde{\mathcal{F}}_t\}$ is also right-continuous.

**Proof**
Since $\{\mathcal{F}^\mu_t\}$ is right-continuous.
$$
\tilde{\mathcal{F}}_{t+}=\bigcap_{s>t}\bigcap_{\mu}\mathcal{F}^\mu_s=\bigcap_{\mu}\bigcap_{s>t}\mathcal{F}^\mu_s=\bigcap_{\mu}\mathcal{F}_{t}^\mu=\tilde{\mathcal{F}}_t
$$
**QED**

> [!thm]
> Let $\{B_t,\mathcal{F}^X_t\},(\Omega,\mathcal{F}_\infty^B),\{\mathbb{P}^x\}$ be a d-dimensional Brownian family. Then $\{B_t,\tilde{\mathcal{F}}_t\},(\Omega,\tilde{\mathcal{F}}_\infty),\{\mathbb{P}^x\}$ is also a Brownian family.

# The Blumenthal Zero-One Law

> [!thm] Blumenthal 0-1 Law
> Let $\{B_t,\tilde{\mathcal{F}}\},(\Omega,\mathcal{F}),\{\mathbb{P}^x\}$be a d-dimensional Brownian family. If $F\in\tilde{\mathcal{F}}_0$, then for each $x\in\mathbb{R}^d$ we have $\mathbb{P}^x(F)=0$ or $\mathbb{P}^x(F)=1$. 

> [!proposition] Changes sign infinitely
> With probability one, a standard, one-dimensional Brownian motion changes sign infinitely many times in any time-interval $[0, \varepsilon], \varepsilon > 0$.

^e7729a

---
# Exercises

> [!question]
> Let $\{X_t, \mathscr{F}_t^X; 0 \leq t < \infty\}$ be a $d$-dimensional process. 
> (i) Show that the filtration $\{\mathscr{F}_{t+}^X\}$ is right-continuous. 
> (ii) Show that if $X$ is left-continuous, then the filtration $\{\mathscr{F}_t^X\}$ is left-continuous. 
> (iii) Show by example that, even if $X$ is continuous, $\{\mathscr{F}_t^X\}$ can fail to be right-continuous and $\{\mathscr{F}_{t+}\}$ can fail to be left-continuous. 

> [!question]
> For any sub-$\sigma$-field $\mathscr{G}$ of $\mathscr{F}_\infty^X$, define $\mathscr{G}^\mu = \sigma(\mathscr{G} \cup \mathscr{N}^\mu)$ and $$ \mathscr{H} = \{F \subseteq \Omega; \exists G \in \mathscr{G} \text{ such that } F \triangle G \in \mathscr{N}^\mu\}. $$ Show that $\mathscr{G}^\mu = \mathscr{H}$. We now extend $P^\mu$ by defining $P^\mu(F) \triangleq P^\mu(G)$ whenever $F \in \mathscr{G}^\mu$, and $G \in \mathscr{G}$ is chosen to satisfy $F \triangle G \in \mathscr{N}^\mu$. Show that the probability space $(\Omega, \mathscr{G}^\mu, P^\mu)$ is complete: $$ F \in \mathscr{G}^\mu, \, P^\mu(F) = 0, \, D \subseteq F \quad \Rightarrow \quad D \in \mathscr{G}^\mu. $$ 

> [!question]
> From Definition 7.2 we have $\overline{\mathscr{F}}_t^\mu \subseteq \mathscr{F}_t^\mu$, for every $0 \leq t < \infty$. Show by example that the inclusion can be strict.

> [!question]
> Show that the $\sigma$-field $\mathscr{F}^\mu$ of Definition 7.2 agrees with $$ \mathscr{F}_\infty^\mu \triangleq \sigma \left( \bigcup_{t \geq 0} \mathscr{F}_t^\mu \right). $$

> [!question]
> If the process $X$ has left-continuous paths, then the filtration $\{\mathscr{F}_t^\mu\}$ is left-continuous.

> [!question]
> Show that any optional time $S$ of $\{\mathscr{F}_t^\mu\}$ is also a stopping time of this filtration, and for each such $S$ there exists an optional time $T$ of $\{\mathscr{F}_t^X\}$ with $\{S \neq T\} \in \mathscr{N}^\mu$. Conclude that $\mathscr{F}_{S+}^\mu = \mathscr{F}_S^\mu = \mathscr{F}_T^\mu$, where $\mathscr{F}_T^\mu$ is defined to be the collection of sets $A \in \mathscr{F}^\mu$ satisfying $A \cap \{T \leq t\} \in \mathscr{F}_t^\mu, \forall 0 \leq t < \infty$. 

> [!question]
> Exercise Suppose that $T$ is an optional time of $\{\mathscr{F}_t^X\}$. For fixed positive integer $n$, define $$ T_n = \begin{cases} T, & \text{on } \{T = \infty\} \\ \frac{k}{2^n}, & \text{on } \left\{\frac{k-1}{2^n} \leq T < \frac{k}{2^n}\right\}. \end{cases} $$ Show that $T_n$ is a stopping time of $\{\mathscr{F}_t^X\}$, and $\mathscr{F}_T^\mu \subseteq \sigma(\mathscr{F}_{T_n}^X \cup \mathscr{N}^\mu)$. Conclude that $\mathscr{F}_T^\mu \subseteq \sigma(\mathscr{F}_{T+}^X \cup \mathscr{N}^\mu)$. (Hint: Use Problems 1.2.23 and 1.2.24.)

> [!question]
> Establish the following proposition: if for each $t \geq 0$, $\Gamma \in \mathscr{B}(\mathbb{R}^d)$, and optional time $T$ of $\{\mathscr{F}_t^X\}$, we have the strong Markov property $$ P^\mu[X_{T+t} \in \Gamma \mid \mathscr{F}_{T+}^X] = P^\mu[X_{T+t} \in \Gamma \mid X_T], \quad P^\mu\text{-a.s. on } \{T < \infty\}, $$ then (7.1) holds for every optional time $S$ of $\{\mathscr{F}_t^\mu\}$.