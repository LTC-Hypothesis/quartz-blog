# Introduction
```ad-def
title:Martingales
The process $\{X_t, \mathcal{F}_t; 0 \le t < \infty\}$ is said to be a **submartingale** (respectively, a **supermartingale**) if, for every $0 \le s < t < \infty$, we have, a.s. $\mathbb{P}: \mathbb{E}(X_t|\mathcal{F}_s)\ge  X_s$, (respectively, $\mathbb{E}(X_t|\mathcal{F}_s)\le X_s$).
We shall say that $X_t$ is a martingale if it is both a submartingale and a supermartingale ($\mathbb{E}(X_t|\mathcal{F}_s) = X_s$).
```

```ad-def
title:Poisson process
A Poisson process with intensity $\lambda > 0$ is an adapted, integer valued RCLL process [[#^cae1eb|N]] such that $N_0 = 0$ and for $0\le s<t$, $N_t-N_s\sim P(\lambda(t-s))$ is independent of $\mathcal{F}_s$.
```

```ad-def
title:Compensated Poisson process
Given a Poisson process $N$ with intensity $\lambda$, we define the compensated Poisson process:
$$
M_t=N_t-\lambda t
$$
Note that the filtrations $\{\mathcal{F}^M_s\}$ and $\{\mathcal{F}^N_s\}$ are degree.
```

```ad-proposition
A compensated Poisson process $M_t$ is a martingale.
```
**Proof**
We consider 
$$
\mathbb{E}[M_t|\mathcal{F}^M_s]=\mathbb{E}[N_t-\lambda t|\mathcal{F}^M_s]=\mathbb{E}[N_t-N_s|\mathcal{F}^M_s]+\mathbb{E}[N_s|\mathcal{F}^M_s]-\lambda t
$$
Since $N_t-N_s$ is independent of $\mathcal{F}^M_s$, $\mathbb{E}[N_t-N_s|\mathcal{F}^M_s]=\mathbb{E}[N_t-N_s]=\lambda(t-s)$. Since $N_s$ is $\mathcal{F}^M_s$-measurable, $\mathbb{E}[N_s|\mathcal{F}^M_s]=N_s$. Hence, 
$$
\mathbb{E}[M_t|\mathcal{F}^M_s]=\lambda(t-s)+N_s-\lambda t=M_s
$$
Hence, $M_t$ is a martingale.
**QED**
```ad-warning
We note that $M_t=N_t-\lambda t\Longrightarrow N_t=M_t+\lambda t$ is a kind of decomposition. In fact, we will introduce the general result in next section Doob-Meyer decomposition.
```

^1dd541

# Fundamental Inequalities
```ad-def
title:Sub(Super)martingale with last element
Consider a submartingale $X_t$ and an integrable, $\mathcal{F}_{\infty}=\sigma(\bigcup_{t\ge 0}\mathcal{F}_t)$measurable random variable $X_\infty$. If we also have,$$\mathbb{E}[X_\infty|\mathcal{F}_t]\ge X_t$$then we say that $X_t$ is a submartingale with last element $X_\infty$.
```

```ad-proposition
title:Convex and martingale
Let $\{X_t,, \mathcal{F}_t; 0 \le t < \infty\}$ be a martingale (respectively, submartingale), and $\varphi: \mathbb{R}\to\mathbb{R}$ a convex (respectively, convex nondecreasing) function, such that $\mathbb{E}|\varphi(X_t)|<\infty$ holds for every $t\ge 0$. Then $\{\varphi(X_t),\mathcal{F}_t,0\le t<\infty\}$ is a submartingale.
```
**Proof**
The method is to use Jensen's inequality. For $0\le s<t<\infty$, by Jensen's Inequality, 
$$
\mathbb{E}[\varphi(X_t)|\mathcal{F}_s]\ge \varphi(\mathbb{E}[X_t|\mathcal{F_s}])=\varphi(X_s)
$$
Hence, $\varphi(X_t)$ is a submartingale.
**QED**
```ad-def
title:number of up-crossing 
Let $X = \{X; 0 \le t < \infty\}$ be a real-valued stochastic process. Consider two numbers $\alpha<\beta$ and a finite subset $F$ of $[0, \infty)$. We define on the interval $[\alpha,\beta]$] by the restricted sample path$\{X_t:t\in F\}$ as follows. 
$$
\tau_{1}(\omega)=\min\{t\in F:X_t(\omega)\le \alpha\}
$$
$$
\sigma_j(\omega)=\min\{t\in F:t\ge \tau_j(\omega),X_t(\omega)>\beta\}
$$
$$
\tau_{j+1}=\min\{t\in F:t\ge \sigma_j(\omega),X_t(\omega)<\alpha\}
$$
The number of upcrossings: 
$$
U_F(\alpha,\beta;X_t(\omega))=\max\{j:\sigma_j(\omega)<\infty\}
$$
If $I\subset[0,\infty)$ is infinite, we define:
$$
U_I(\alpha,\beta;X_t(\omega))=\sup\{U_F(\alpha,\beta;X_t(\omega)):F\subset I,F \mbox{ is finite}\}
$$
The number of downcrossings $D_F(\alpha,\beta;X_t(\omega))$ is defined similarly.
```

```ad-warning
A vivid illustration: 
![[a018096d9c4bbe9dee56053390bc934d.jpg]]
```

```ad-thm
title:Upcrossing inequality and relate inequalities
Let $X_t$ be a submartingale whose every path is right-continuous, let $[a,b]\subset[0,\infty)$ be a subinterval, and let $\alpha<\beta,\lambda>0$ be real numbers. We have the following results:
1. First submartingale inequality
   $$
   \lambda\mathbb{P}[\sup_{a\le t\le b}X_t\ge\lambda]\le \mathbb{E}(X^+_{b})
   $$
2. Second submartingale inequality
   $$
   \lambda\mathbb{P}[\inf_{a\le t\le b}X_t\le -\lambda]\le \mathbb{E}(X^+_b)-\mathbb{E}(X_a)
   $$
3. Upcrossings and downcrossings inequalities
   $$
   \mathbb{E}[U_{[a,b]}(\alpha,\beta,X_t(\omega))]\le\frac{\mathbb{E}(X^+_b)+|\alpha|}{\beta-\alpha},\mathbb{E}[D_{[a,b]}(\alpha,\beta,X_t(\omega))]\le\frac{\mathbb{E}(X_b-\alpha)^+}{\beta-\alpha}
   $$
4. Doob's maximal inequality
   $$
   \mathbb{E}\left(\sup_{a\le t\le b}X_t\right)^p\le\left(\frac{p}{p-1}\right)^p\mathbb{E}(X^p_b),p> 1
   $$
5. **Regularity of the paths**: Almost every sample path $X_t(w)$ is **bounded on compact intervals**; is free of **discontinuities of the second kind** i.e. admits **left-hand limits** everywhere on $(0, \infty)$; and its jumps are exhausted by a sequence of stopping times
```

^bd276e

**Proof**
1. We denote the event $A=\{\sup_{a\le t\le b}X_t\ge\lambda\}$. $A$ is measurable and the supremum over $[a,b]$ is the same as the supremum over $[a,b]\cap\mathbb{Q}$. Let $T=\inf\{t:X_t\ge \lambda\}$. Then $A=\{T\le t\}$. Since $X$ is a submartingale, $X^+$ is also a submartingale, then $$\mathbb{E}(X^+_t)\ge \mathbb{E}(X^+_{t\wedge T})\ge \mathbb{E}(X^+_{t\wedge T}\mathbb{1}_{\{T\le t\}})\ge \lambda\mathbb{P}(A)$$ This prove 1.
2. We denote the event $B=\{\inf_{a\le t\le b}X_t<-\lambda\}$. $B$ is measurable and the supremum over $[a,b]$ is the same as the supremum over $[a,b]\cap\mathbb{Q}$. Let $S=\inf\{t:X_t\le -\lambda\}$. Then $B=\{S\le t\}$. Since $X$ is a submartingale, $X^+$ is also a submartingale, then $$\begin{align}
\mathbb{E}(X_a)&\le\mathbb{E}(X_{b\wedge S})=\mathbb{E}(X_b\mathbb{1}_{\{S>b\}})+\mathbb{E}(X_S\mathbb{1}_{\{S\le b\}})\\
&\le \mathbb{E}(X_b\mathbb{1}_{\{S>b\}})-\lambda\mathbb{P}(B)\le\mathbb{E}(X^+_b)-\lambda\mathbb{P}(B)
\end{align}$$
Hence, $\lambda\mathbb{P}(B)\le \mathbb{E}(X^+_b)-\mathbb{E}(X_a)$
3. We prove the downcrossing case. 
4. Let $Y=\sup_{a\le t\le b}X_t$. Since $X_t$ is a continuous submartingale, we have $$\lambda\mathbb{P}(Y\ge \lambda)+\mathbb{E}|X_b|\mathbb{1}_{\{Y<\lambda\}}\le\mathbb{E}|X_b|$$ and hence, $$\mathbb{P}(Y\ge \lambda)\le \frac{1}{\lambda}\mathbb{E}|X_b|\mathbb{1}_{\{Y\ge \lambda\}}$$ Now we calculate $\mathbb{E}(Y^p)$, $$\begin{align}
\mathbb{E}(Y^p)&=p\int_{0}^{\infty}\lambda^{p-1}\mathbb{P}(Y\ge \lambda){d}\lambda\\
&\le p\int_{0}^{\infty}\lambda^{p-2}\mathbb{E}|X_b|\mathbb{1}_{\{Y\ge \lambda\}}{d}\lambda\\
&=\mathbb{E}\left(p|X_b|\int_{0}^{Y}\lambda^{p-2}{d}\lambda\right)(\mbox{By Fubini Thm})\\
&=\frac{p}{p-1}\mathbb{E}\left(|X_b|\cdot Y^{p-1}\right)\\
&\le\frac{p}{p-1}(\mathbb{E}|X_b|^p)^{\frac{1}{p}}(\mathbb{E}(Y^{p}))^{\frac{1}{p'}}(\mbox{By Holder,}p'=\frac{p}{p-1})
\end{align}$$Hence, $$\Longrightarrow(\mathbb{E}(Y^p))^{\frac{1}{p}}\le\frac{p}{p-1}(\mathbb{E}|X_b|^p)^{\frac{1}{p}}\Longrightarrow(\mathbb{E}(Y^p))\le\left(\frac{p}{p-1}\right)^{p}(\mathbb{E}|X_b|^p)$$
5. By 1. and 2., we get the boundedness on the compact interval trivially. We consider the event, $$A^{(n)}_{\alpha,\beta}=\{\omega:U_{[0,n]}(\alpha,\beta,X(\omega))=\infty\},n\ge1,\alpha<\beta$$   By 3., the probability of each event is 0. Take rational number $\alpha<\beta$ and take the union, $$A^{(n)}=\bigcup_{\alpha<\beta}A^{(n)}_{\alpha,\beta}$$ $A^{(n)}$ also has probability zero, which includes the set $$\left\{\omega:\varliminf_{s\uparrow t}X_s(\omega)<\varlimsup_{s\uparrow t}X_s,\mbox{for some }t\in[0,n]\right\}$$since if left-hand limit isn't exist, then there exists rational number $\alpha<\beta$ s.t. the path cross the interval $[\alpha,\beta]$ infinitely. Hence, for $n\ge 1$, take union and complement, $$\omega\in\left(\bigcup_{n=1}^{\infty}A^{(n)}\right)^c,\mathbb{P}\left(\bigcup_{n=1}^{\infty}A^{(n)}\right)^c=1$$
Indeed, it admits left-hand limits everywhere on $(0,\infty)$.
**QED**
```ad-proposition
Let $X_t$ be a submartingale. We have the following:
1. There is an event $\Omega^*\in\mathcal{F}$ with $\mathbb{P}(\Omega^*)=1$ s.t. $\forall \omega\in\Omega^*$, the limit:
   $$
   X_{t+}(\omega)=\lim_{s\downarrow t,s\in\mathbb{Q}}X_{s}(\omega),X_{t-}(\omega)=\lim_{s\uparrow t,s\in\mathbb{Q}}X_{s}(\omega)
   $$
   exists for every $t\ge 0$
2. The limit in 1. satisfy
   $$
   \mathbb{E}(X_{t+}|\mathcal{F}_t)\ge X_t,\mathbb{E}(X_{t}|\mathcal{F}_{t-})\ge X_{t-},a.s.-\mathbb{P}
   $$
3. $\{X_{t+},\mathcal{F}_{t+}\}$ is a submartingale with $\mathbb{P}$-a.s.every path RCLL.
```

^3e2539

**Proof**
1. We can imitate the proof of [[#^bd276e|5.]]. But we don't have assumption of right-continuity, so we can't use the up-crossing inequality. Thus we alter the definition of the set $A^{(n)}_{\alpha,\beta}$. $$A^{(n)}_{\alpha,\beta}=\left\{\omega:U_{[0,n]\cap\mathbb{Q}}(\alpha,\beta,X(\omega))=\infty\right\},n\ge1,\alpha<\beta$$ $$A^{(n)}=\bigcup_{\alpha<\beta,\alpha,\beta\in\mathbb{Q}}A^{(n)}_{\alpha,\beta}$$Then each $A^{(n)}_{\alpha,\beta}$ has probability zero, as does each $A^{(n)}$. The conclusions follow readily.
2. Let $\{t_n\}$ be a sequence of rational numbers s.t. $t_n\downarrow t$. Then $X_{t_n}$ is a back submartingale and the sequence $\mathbb{E}(X_{t_n})$ is decreasing and bounded below by $\mathbb{E}(X_t)$. By [[#^afeb3e|Exercises]], $\{X_{t_n}\}$ is uniformly integrable sequence. We W.T.S for every $A\in\mathcal{F}_{t}$, $\int_{A}X_t{d}\mathbb{P}\le \int_A X_{t+}{d}\mathbb{P}$. In fact, from the property of submartingale, we have $\int_{A}X_t{d}\mathbb{P}\le \int_A X_{t_n}{d}\mathbb{P}$. By uniformly integrable, we have $L^1$-convergence, letting $n\to\infty$, we prove the first inequality. For the second inequality, we take $\{t_n\}$ be a sequence of rational numbers s.t. $t_n\uparrow t$. According to the submartingale property $\mathbb{E}(X_t|\mathcal{F}_{t_n})\ge X_{t_n}$. Let $n\to\infty$, we get $\mathbb{E}(X_{t}|\mathcal{F}_{t-})\ge X_{t-}$.
3. Take a monotone decreasing sequence $\{s_n\}$ of rational number with $0\le s<s_n<t$ s.t. $s_n\downarrow s$. By the first inequality of 2., $\mathbb{E}(X_{t+}|\mathcal{F}_{s_n})\ge X_{s_n}$. Let $n\to \infty$, we obtain $$\mathbb{E}(X_t|\mathcal{F}_{s+})\ge X_{s+}$$By 1., , that $\mathbb{P}$-almost every path is RCLL.

**QED**
It was supposed in [[#^bd276e|Theorem]] that the submartingale $X$ has right-continuous sample paths. It is of interest to investigate conditions under which we may assume this to be the case.
```ad-thm
Let $X_t$ be a submartingale, and assume the filtration $\{\mathcal{F}_t\}$ satisfies the usual conditions. Then the process $X$ **has a right-continuous modification** if and only if the function $t\mapsto \mathbb{E}X_t$, from $[0, \infty)$ to $\mathbb{R}$ is **right-continuous**. 
```

^2cd6c5

**Proof**
$\Longleftarrow$: Suppose the mapping $t\mapsto\mathbb{E}(X_t)$ is right-continuous. **Claim: $X_{t+}$ is a modification of $X_t$.** Given $t > 0$, let $\{q_n\}$ be a sequence of rational numbers with $q_n\downarrow t$. Then $X_{q_n}\to X_{t+}a.s.$ and uniformly integrability implies that $\mathbb{E}(X_{t+})=\lim_{n\to \infty}\mathbb{E}(X_{q_n})$. By assumption, $\mathbb{E}(X_{q_n})\to \mathbb{E}(X_t)$ and thus $\mathbb{E}(X_{t+})=\mathbb{E}(X_t)$. By [[#^3e2539|proposition 2.]], $X_{t+}\ge X_t$. Hence, $X_{t+}=X_{t}$.
$\Longrightarrow$: Suppose the $\tilde{X}_t$ is a right-continuous modification of $X_t$. Given $t > 0$, let $\{q_n\}$ be a sequence of rational numbers with $q_n\downarrow t$. We have $\mathbb{P}(X_t=\tilde{X}_t,X_{q_n}=\tilde{X}_{q_n};n\ge 1)=1$ and $\tilde{X}_{q_n}\to \tilde{X}_{t}a.s.$, and the uniform integrability implies $\mathbb{E}(X_{q_n})\to\mathbb{E}(X_t)$. Then $t\mapsto\mathbb{E}(X_t)$ is right-continuous. 
**QED**
```ad-warning
If this right-continuous modification exists, it can be chosen so as to be RCLL and adapted to $\{\mathcal{F}_t\}$, hence a submartingale with respect to $\{\mathcal{F}_t\}$.
```

^c748c5

# Convergence Results
```ad-thm
title:Submartingale convergence
Let $X_t$ be a right-continuous submartingale and assume $C\triangleq\sup_{t\ge 0}\mathbb{E}(X^+_t)<\infty$. Then $X_{\infty}(\omega)\triangleq\lim_{t\to\infty}X_{t}(\omega)$) exists for a.e.$\omega\in\Omega$ and $\mathbb{E}|X_{\infty}|<\infty$.
```

^d32e0c

**Proof**
By [[#^bd276e|up-crossing inequality]], for $n\ge 1,-\infty<\alpha<\beta<\infty$: 
$$
\mathbb{E}[U_{[0,n]}(\alpha,\beta;X(\omega))]\le\frac{\mathbb{E}(X^+_n(\omega))+|\alpha|}{\beta-\alpha}
$$
By MCT, let $n\to\infty$, we have 
$$
\mathbb{E}[U_{[0,\infty)}(\alpha,\beta;X(\omega))]\le\frac{C+|\alpha|}{\beta-\alpha}
$$
Let $\alpha,\beta\in\mathbb{Q,\alpha<\beta}$, we define the set  
$$
\begin{align}
&A_{\alpha,\beta}=\left\{\omega:U_{[0,\infty)}(\alpha,\beta;X(\omega))=\infty\right\}\\
&A=\bigcup_{\alpha<\beta,\alpha,\beta\in\mathbb{Q}}A_{\alpha,\beta}
\end{align}
$$
Then $A_{\alpha,\beta}$ and $A$ have probability 0. Moreover, $A$ contains the set 
$$
\left\{\omega:\varliminf_{s\uparrow t}X_s(\omega)<\varlimsup_{s\uparrow t}X_s,\mbox{for some }t\ge 0\right\}
$$
Then for $\omega\in\Omega\setminus A$, we have $X_{\infty}(\omega)=\lim_{t\to\infty}X_{t}(\omega)$. Moreover, by Fatou Lemma, 
$$
\mathbb{E}|X_{\infty}|\le\varliminf_{t\to\infty}\mathbb{E}|X_t|\le\varliminf_{t\to\infty}\left(2\mathbb{E}X^+_t-\mathbb{E}X_t\right)\le C-\mathbb{E}(X_0)<\infty
$$
**QED**
```ad-def
title:Potential
A right-continuous, nonnegative supermartingale $Z_t$ with $\lim_{t\to\infty} E(Z_t) = 0$ is called a potential.
```
The follow proposition gerantees that a potential has a last element and element is 0 a.s. $\mathbb{P}$. Besides, it is also the supermartingale version of  convergence.
```ad-proposition
title:Supermartingale convergence
Let $X_t$ be a right-continuous **nonnegative supermartingale**, then $X_t(\omega) = \lim_{t\to\infty}=X_{\infty}(\omega)$ exists for $\mathbb{P}$-a.e. $\omega\in\Omega$, and $X_{t},0\le t\le \infty$ is a supermartingale.
```

^23db34

**Proof**
In fact, we only change the case to submartingale. Let $Y_t=-X_t$, then $Y_t$ is a submartingale and $Y_t\le 0$, $\sup_{t\ge 0}\mathbb{E}(Y^+_t)<\infty$. By submartingale convergence, $Y_t\to Y_{\infty}$ for $\mathbb{P}$-a.e and $\omega\in\Omega a.e.$ Correspondingly, $X_t(\omega) = \lim_{t\to\infty}=X_{\infty}(\omega)$ exists for $\mathbb{P}$-a.e. $\omega\in\Omega$. By Fatou Lemma, 
$$
\mathbb{E}(X_{\infty}|\mathcal{F}_{t})\le \varliminf_{s\to\infty}\mathbb{E}(X_s|\mathcal{F}_{t})\le X_{t}
$$
Hence, $X_{t},0\le t\le \infty$ is a supermartingale.
**QED**
```ad-warning
An intelligible method to comprehend sub(super)martingale convergence is to compare with bounded monotone theorem.
```

```ad-thm
title:Submartingale $L^1$ convergence
The following three conditions are equivalent for a nonnegative, right-continuous submartingale $X_t$:
1. It is a uniformly integrable family of random variables
2. It converges in $L^1$, as $t\to\infty$
3. it converges $\mathbb{P}-a.s.$ (as $t\to\infty)$ to an integrable random variable $X_{\infty}$, such that $X_t,0\le t\le\infty$ is a submartingale.
```

^1d7b18

**Proof**
$1\Longrightarrow2$: We recall the definition of uniformly integrable before proof. $X_t$ is called uniformly integrable if 
$$
\lim_{M\to\infty}\sup_{t}\mathbb{E}|X_{t}|\mathbb{1}_{\{|X_t|\ge M\}}=0
$$
The assumption of uniformly integrable and nonnegetive imply that $\sup_{t}\mathbb{E}X^+_t=\sup_{t}\mathbb{E}|X_t|<\infty$. By [[#^d32e0c|Submartingale convergence]], $X_{t}\to X_{\infty},a.s.$ and thus it implies $X_t\to X_{\infty}$ in $L^1$. 
$2\Longrightarrow3$: Trivial. We use the relationship of different convergence and can refer to the document [[收敛性互推总结 .pdf|收敛性互推]].
$3\Longrightarrow1$: By assumption, $X_{\infty}$ is integrable and for every $t\ge 0$ we have $\mathbb{E}(X_{\infty}|\mathcal{F}_t)\ge X_t$. Besides, $X_t$ is nonnegetive and the family of condition expectation $\{\mathbb{E}(X_{\infty}|\mathcal{F}_t)\}$ is uniformly integrable. Thus, $X_t$ is controlled by uniformly integrable random variables. Hence, $X_t$ is also uniformly integrable. 
**QED**
```ad-thm
title:Martingale $L^1$ convergence
The following four conditions are equivalent for a nonnegative, right-continuous martingale $X_t$:
1. It is a uniformly integrable family of random variables
2. It converges in $L^1$, as $t\to\infty$
3. It converges $\mathbb{P}- a.s.$ (as $t\to\infty)$ to an integrable random variable $X_{\infty}$, such that $X_t,0\le t\le\infty$ is a martingale.
4. There exists an integrable random variable $Y$, such that $X_t = \mathbb{E}(Y|\mathcal{F}_t) a.s. \mathbb{P}$, for every $t \ge 0$. Besides, , if 4. holds and $X_{\infty}$ is the random variable in 3., then $$\mathbb{E}(Y|\mathcal{F}_{\infty})=X_{\infty}$$
```

^3e0f1e

**Proof**
$1\Longrightarrow2$: By [[#^d32e0c|submartingale convergence]] and [[#^23db34|supermartingale convergence]], $X_t\to X_{\infty},a.s.$ and thus $X_t\to X_{\infty}$ in $L^1$
$2\Longrightarrow3$: Trivial.
$3\Longrightarrow4$: Trivial. We prove the second claim. Since $\mathcal{F}_t\uparrow\mathcal{F}_{\infty}$ and $\mathcal{F}_{\infty}=\sigma(\bigcup_{t\ge 0}\mathcal{F}_{t})$, we can refer to PTE theorem4.6.8 ![[Pasted image 20260313092715.png]]Take $t\to\infty$, then $X_t\to X_{\infty},a.s.$ and in $L^1$, $\mathbb{E}(Y|\mathcal{F}_t)\to\mathbb{E}(Y|\mathcal{F}_{\infty}),a.s.$ and in $L^1$. Hence, $X_{\infty}=\mathbb{E}(Y|\mathcal{F}_{\infty})$.
$4\Longrightarrow1$: Note that $Y$ is integrable, then the family of expectation $\{\mathbb{E}(Y|\mathcal{F}_t)\}$ is uniformly integrable. Hence, $X_t$ is uniformly integrable.
**QED**

# The Optional Sampling Theorem

^91b46a

```ad-thm
title:Optional Sampling
Let $X_t$ be a rightcontinuous submartingale with a last element $X_{\infty}$., and let $S \le T$ be two **optional times** of the filtration $\{\mathcal{F}_t\}$ We have
$$
\mathbb{E}(X_T|\mathcal{F}_{S+})\ge X_{S},a.s.\mathbb{P}
$$
If $S$ is a **stopping time**, then $\mathcal{F}_S$ can replace $\mathcal{F}_{S+}$ above. In particular, $\mathbb{E}(X_T)\ge \mathbb{E}(X_0)$ and for a martingale with a last element we have $\mathbb{E}X_T = \mathbb{E}X_0$.
```

^1b13f7

**Proof**
The idea to prove continuous version of optional sampling is to use discrete version. Therefore, we should construct a sequence of optional times. The motivation is derived from [[Stopping Times#^33bc9e|Exercise]]. Consider the $S_n$ and $T_n$ as follows,
$$
S_n=\begin{cases}
S(\omega),&S(\omega)=\infty\\
\frac{k}{2^n},&\frac{k-1}{2^n}\le S(\omega)<\frac{k}{2^n},k=1,\cdots,2^n
\end{cases}
$$
$$
T_n=\begin{cases}
T(\omega),&T(\omega)=\infty\\
\frac{k}{2^n},&\frac{k-1}{2^n}\le T(\omega)<\frac{k}{2^n},k=1,\cdots,2^n
\end{cases}
$$
By [[Stopping Times#^33bc9e|Exercise]], we know $S_n,T_n$ are stopping times and take coutable number of value, keep $S_n\le T_n$. We can use the discrete version of optional sampling. That is 
$$
\mathbb{E}(X_{T_n}|\mathcal{F}_{S_n})\ge X_{S_n}
$$
By [[Stopping Times#^256794|another Exercise]], since $S_n\downarrow S$, we have $\mathcal{F}_{S+}=\bigcap_{n=1}^{\infty}\mathcal{F}_{S_n}$. For convenience, we use the form of integral. That is for every $A\in\mathcal{F}_{S+}$, we have 
$$
\int_{A}X_{S_n}{d}\mathbb{P}\le \int_{A}X_{T_n}{d}\mathbb{P}
$$
Since $\{X_{S_n},\mathcal{F}_{S_n}\}$ is a back martingale, then $X_{S_n}$ is uniformly integrable by [[Continuous-Time Martingales#^afeb3e|Exercise of backmartingale]]. Therefore, by [[#^1d7b18|submartingale L^1 convergence]] and right-continuous, $X_{S_n}\to X_S,a.s.$, $X_{T_n}\to X_T,a.s.$, $X_T,X_S$ are integrable, then 
$$
\int_{A}X_S{d}\mathbb{P}\le\int_{A}X_T{d}\mathbb{P},\forall A\in\mathcal{F}_{S+}
$$
Hence, $\mathbb{E}(X_T|\mathcal{F}_{S+})\ge X_S$. If $S$ is a stopping time, then $S\le S_n\Longrightarrow\mathcal{F}_{S}\subset\mathcal{F}_{S_n}$, then the integral inequality holds for every $A\in\mathcal{F}_{S}$.
**QED**
Another optional sampling theorem. 
```ad-thm
Let $X_t$ be a rightcontinuous submartingale and optional times $S\le T$ under either of the following two conditions:
1. $T$ is bounded
2. there exists an integrable random variable $Y$, such that $X_t\le \mathbb{E}(Y|\mathcal{F}_t)a.s.-\mathbb{P}$, for every $t\ge 0$.
   
then $\mathbb{E}(X_T|\mathcal{F}_{S})\ge X_S$.
```

^675f51

---
## Exercises
```ad-question
Let $T_1, T_2, ...$ be a sequence of independent, exponentially distributed random variables with parameter $\lambda > 0$:
$$
\mathbb{P}[T_i\in dt]=\lambda e^{-\lambda t}dt,t\ge 0
$$
Let $S_0=0$ and $S_n=\sum_{i=1}^{n}T_i$. Define a continuous-time, integer valued RCLL process
$$
N_t=\max\{n\ge0:S_n\le t\},t\ge 0
$$
Show that:
1. For $0\le s<t$ we have $$\mathbb{P}[S_{N_s+1}>t|\mathcal{F}^N_s]=e^{-\lambda(t-s)},a.s.\mathbb{P}$$
2. For $0\le s<t$, $N_t-N_s\sim P(\lambda(t-s))$, independent of $\mathcal{F}^N_s$
```

^cae1eb

```ad-done
title:Done for 1
**Claim:** Fix $\tilde{A}\in\mathcal{F}^N_{s}$, there exists an event $A\in\sigma(T_1,T_2,\cdots,T_n)$ s.t. 
$$
A\cap\{N_s=n\}=\tilde{A}\cap\{N_s=n\}
$$
In fact, $\mathcal{F}^N_s=\sigma(N_t:0\le t<s)$. By $N_t=\sum_{k=1}^{\infty}\mathbb{1}_{\{S_k\le t\}}$, then $\mathcal{F}^N_s$ is also derived by set $\{S_k\le t\}(k\ge 1,0\le t<s)$. Let the set family
$$
\mathcal{C}=\{\{S_k\le t\}:k\ge 1,0\le t<s\}
$$
Note that $S_n=\sum_{k=1}^{n}T_k$, then $\sigma(S_1,S_2,\cdots,S_n)=\sigma(T_1,T_2,\cdots,T_n)$. We W.T.S. for any $C\in \mathcal{C}$, $\exists A\in\sigma(S_1,S_2,\cdots,S_n)$ s.t $C\cap\{N_s=n\}=A\cap\{N_s=n\}$. If $k>n$, $C\cap\{N_s=n\}=\emptyset$, take $A=\emptyset$. If $k\le n$, take $A=\{S_k\le t\}$, then $C\cap\{N_s=n\}=A\cap\{N_s=n\}$. By the method of appropriate set, let 
$$
\mathcal{D}=\{B\in\mathcal{F}^N_s:\exists A\in\sigma(T_1,T_2,\cdots,T_n) s.t. B\cap\{N_s=n\}=A\cap\{N_s=n\}\}
$$
We check $\mathcal{D}$ is a $\sigma$-algebra. For $\Omega\cap\{N_s=n\}=\{N_s=n\}$, take $A=\emptyset$. For $B\in\mathcal{D}$, then 
$$
\begin{align}
B^c\cap\{N_s=n\}&=\{N_s=n\}\setminus(B\cap\{N_s=n\})=\{N_s=n\}\setminus(A\cap\{N_s=n\})\\
&=A^c\cap\{N_s=n\}
\end{align}
$$
For $\{B_j\}\subset\mathcal{D}$, then 
$$
\begin{align}
(\bigcup_{j=1}^{\infty}B_j)\cap\{N_s=n\}&=\bigcup_{j=1}^{\infty}(B_j\cap\{N_s=n\})=\bigcup_{j=1}^{\infty}(A_j\cap\{N_s=n\})\\
&=(\bigcup_{j=1}^{\infty}A_j)\cap\{N_s=n\}
\end{align}
$$
Hence, $\mathcal{D}$ is a $\sigma$-algebra and $\mathcal{C}\subset\mathcal{D}$, $\mathcal{F}^N_s=\sigma(\mathcal{C})$. Hence, $\mathcal{D}=\mathcal{F}^N_s$ i.e. for $\tilde{A}\in\mathcal{F}^N_s$, there exists $A\in\sigma(T_1,T_2,\cdots,T_n)$ s.t. $A\cap\{N_s=n\}=\tilde{A}\cap\{N_s=n\}$. 
Next we calculate
$$
\begin{align}
\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}[S_{n+1}>t|\mathcal{F}^N_s]d\mathbb{P}&=\mathbb{P}\left(\{S_{n+1}>t\}\cap\tilde{A}\cap\{N_s=n\}\right)\\
&=\mathbb{P}\left(\{S_{n+1}>t\}\cap A\cap\{N_s=n\}\right)
\end{align}
$$
Note that $\{S_{n+1}>t\}\cap\{N_s=n\}=\{S_n\le s\}\cap\{T_{n+1}\ge t-S_n\}$ and $\{S_{n+1}>t\}\cap\{N_s=n\}=\{S_n\le s\}\cap\{T_{n+1}\ge s-S_n\}$. Since $T_{n+1}$ is independent with $\sigma(T_1,T_2,\cdots,T_n)=\sigma(S_1,S_2,\cdots,S_n)$, we have 
$$
\begin{align}
\mathbb{P}(\{S_{n+1}>t\}\cap A\cap\{N_s=n\})&=\mathbb{P}(\{S_n\le s\}\cap A\cap\{T_{n+1}\ge t-S_n\})\\
&=\mathbb{E}[\mathbb{1}_{A}\mathbb{1}_{\{S_n\le s\}}\mathbb{E}[\mathbb{1}_{\{T_{n+1}\ge t-S_n\}}|S_n]]\\
&=\mathbb{E}[\mathbb{1}_{A}\mathbb{1}_{\{S_n\le s\}}e^{-\lambda(t-S_n)}]
\end{align}
$$
$$
\begin{align}
\mathbb{P}(\{S_{n+1}>t\}\cap A\cap\{N_s=n\})&=\mathbb{P}(\{S_n\le s\}\cap A\cap\{T_{n+1}\ge s-S_n\})\\
&=\mathbb{E}[\mathbb{1}_{A}\mathbb{1}_{\{S_n\le s\}}\mathbb{E}[\mathbb{1}_{\{T_{n+1}\ge s-S_n\}}|S_n]]\\
&=\mathbb{E}[\mathbb{1}_{A}\mathbb{1}_{\{S_n\le s\}}e^{-\lambda(s-S_n)}]
\end{align}
$$
and 
$$
\begin{align}
e^{-\lambda(t-s)}\mathbb{P}[\tilde{A}\cap\{N_s=n\}]&=e^{-\lambda(t-s)}\mathbb{E}[\mathbb{1}_{A}\mathbb{1}_{\{S_n\le s\}}e^{-\lambda(s-S_n)}]\\
&=\mathbb{E}[\mathbb{1}_{A}\mathbb{1}_{\{S_n\le s\}}e^{-\lambda(t-S_n)}]\\
&=\mathbb{P}(\{S_{n+1}>t\}\cap A\cap\{N_s=n\})\\
&=\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}[S_{n+1}>t|\mathcal{F}^N_s]d\mathbb{P}
\end{align}
$$
Then 
$$
\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}[S_{n+1}>t|\mathcal{F}^N_s]d\mathbb{P}=\int_{\tilde{A}\cap\{N_s=n\}}e^{-\lambda(t-s)}d\mathbb{P}
$$
Hence, $\mathbb{P}[S_{N_s+1}>t|\mathcal{F}^N_s]=e^{-\lambda(t-s)},a.s.\mathbb{P}$.
```

```ad-done
title:Done for 2
Note that $\{N_t-N_s\le k\}=\{S_{n+k+1}>t\}$, then for $\tilde{A}\in\mathcal{F}^N_{s}$,
$$
\begin{align}
\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}(N_t-N_s\le k|\mathcal{F}^N_s)d\mathbb{P}&=\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}(S_{n+k+1}>t|\mathcal{F}^N_s)d\mathbb{P}\\
\end{align}
$$
By result of 1.
$$
\begin{align}
\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}(S_{n+k+1}>t|\mathcal{F}^N_s)d\mathbb{P}&=\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}(S_{n+1}+\sum_{i=2}^{k+1}T_{n+i}>t|\mathcal{F}^N_s)d\mathbb{P}\\
\end{align}
$$
Let $U=S_n$, $T_{n+i}$ are i.i.d. We calculate the condition distribution integrable of $U$, 
$$
\begin{align}
&\int_{s}^{\infty}\mathbb{P}(u+\sum_{i=2}^{n+1}T_{n+i}>t)\lambda e^{-\lambda(u-s)}{d}u\\
&=\int_{s}^{t}\sum_{i=0}^{k-1}e^{-\lambda(t-u)}\frac{(\lambda(t-u))^i}{i!}\lambda e^{-\lambda(u-s)}{d}u+\int_{t}^{\infty}\lambda e^{-\lambda(u-s)}{d}u\\
&=\lambda e^{-\lambda(t-s)}\sum_{m=0}^{k-1}\lambda^m\int_{s}^{t}\frac{(t-u)^m}{m!}{d}u+e^{-\lambda(t-s)}\\
&=e^{-\lambda(t-s)}\sum_{m=0}^{k}\frac{(\lambda(t-s))^m}{m!}
\end{align}
$$
Then we have 
$$
\int_{\tilde{A}\cap\{N_s=n\}}\mathbb{P}(N_t-N_s\le k|\mathcal{F}^N_s)d\mathbb{P}=\int_{\tilde{A}\cap\{N_s=n\}}e^{-\lambda(t-s)}\sum_{m=0}^{k}\frac{(\lambda(t-s))^m}{m!}d\mathbb{P}
$$
Hence, $\mathbb{P}(N_t-N_s\le k)=e^{-\lambda(t-s)}\sum_{m=0}^{k}\frac{(\lambda(t-s))^m}{m!}$. 
```

```ad-question
Let $\{X = (X^{(1)}_t,\cdots,X^{(d)}_t), \mathcal{F}_t; 0 \le t < \infty\}$ be a vector of martingales, and $\varphi: \mathbb{R}^d\to\mathbb{R}$ a convex function with $E|\varphi(X_t)| < \infty$ valid for every $t \le 0$. Then $\{\varphi(X_t), \mathcal{F}_t; 0\le t < \infty\}$ is a submartingale; in particular $\{||X_t||, \mathcal{F}_t,; 0 \le t < \infty\}$ is a submartingale.
```

^26a60a

```ad-done
Recall property of convex function, $\mathbb{E}(\varphi(X_t))\ge \varphi(\mathbb{E}(X_t))$. Then $\mathbb{E}[\varphi(X_t)|\mathcal{F}_s]\ge \varphi(\mathbb{E}(X_t|\mathcal{F}_s))=\varphi(X_s)$. Then $\varphi(X_t)$ is a submartingale. Take function $\varphi(\textbf{x}):\mathbb{R}^n\to\mathbb{R}$, $\varphi(\textbf{x})=\|\textbf{x}\|$. It is obviosly that $\varphi$ is convex by triangle inequality. Hence, $\|X_t\|$ is a submartingale.
```

^da874b

```ad-question
Let $N$ be a Poisson process with intensity $\lambda$.
1. For any $c > 0$,
   $$
   \varlimsup_{t\to\infty}\mathbb{P}\left[\sup_{0\le s\le t}(N_s-\lambda s)\ge c\sqrt{\lambda t}\right]\le \frac{1}{c\sqrt{2\pi}}
   $$
2. For any $c > 0$,
   $$
   \varlimsup_{t\to\infty}\mathbb{P}\left[\inf_{0\le s\le t}(N_s-\lambda s)\le -c\sqrt{\lambda t}\right]\le \frac{1}{c\sqrt{2\pi}}
   $$
3. For any $0<a<b$,
   $$
   \mathbb{E}\left[\sup_{a\le t\le b}(\frac{N_t}{t}-\lambda)^2\right]\le\frac{4b\lambda}{a^2}
   $$
```

^07fcac

```ad-done
title:Done for 1
By [[#^bd276e|Upcrossing Inequality 1]], we have
$$
\mathbb{P}\left[\sup_{0\le s\le t}(N_s-\lambda s)\ge c\sqrt{\lambda t}\right]\le \frac{\mathbb{E}[N_t-\lambda t]^+}{c\sqrt{\lambda t}}
$$
We calculate the $\mathbb{E}[N_t-\lambda t]^+$.
$$
\begin{align}
\mathbb{E}[N_t-\lambda t]^+&=\sum_{n=0}^{\infty}(n-\lambda t)^+e^{-\lambda t}\frac{(\lambda t)^n}{n!}\\
&=\sum_{n=[\lambda t]+1}^{\infty}(n-\lambda t)^+e^{-\lambda t}\frac{(\lambda t)^n}{n!}\\
&=\sum_{n=[\lambda t]+1}^{\infty}(n-\lambda t)e^{-\lambda t}\frac{(\lambda t)^n}{n!}\\
&=\lambda te^{-\lambda t}\left(\sum_{n=[\lambda t]}^{\infty}\frac{(\lambda t)^n}{n!}-\sum_{n=[\lambda t]+1}^{\infty}\frac{(\lambda t)^n}{n!}\right)=e^{-\lambda t}\frac{(\lambda t)^{[\lambda t]+1}}{[\lambda t]!}
\end{align}
$$
Let $k=[\lambda t]$, by estimation of string,i.e. $k!\sim\sqrt{2\pi k}(\frac{k}{e})^k$, then 
$$
\begin{align}
\frac{\mathbb{E}[N_t-\lambda t]^+}{c\sqrt{\lambda t}}=e^{-\lambda t}\frac{(\lambda t)^{k+\frac{1}{2}}}{ck!}\sim\frac{1}{c\sqrt{2\pi}}e^{-\lambda t}e^{(k+\frac{1}{2})\ln{}\frac{\lambda t}{k}}\to\frac{1}{c\sqrt{2\pi}},t\to\infty
\end{align}
$$
Hence, take $\varlimsup$ for LHS, the inequality holds.
```

```ad-done
title:Done for 2
It is similar with 1.
```

```ad-done
title:Done for 3
By [[#^bd276e|Doob maximal inequality]], 
$$
\begin{align}
\mathbb{E}\left[\sup_{a\le t\le b}(\frac{N_t}{t}-\lambda)^2\right]&=\mathbb{E}\left[\sup_{a\le t\le b}\frac{1}{t^2}(N_t-\lambda t )^2\right]\le\frac{1}{a^2}\mathbb{E}\left[\sup_{a\le t\le b}(N_t-\lambda t)^2\right]\\
&\le \frac{4\mathbb{E}(N_b-\lambda b)^2}{a^2}=\frac{4\lambda b}{a^2}
\end{align}
$$
```

^f35afc

```ad-warning
By Q1 and Q2, by product we have for every $c>0$, there exists $T_c>0$
$$
\mathbb{P}\left(\left|\frac{N_t}{t}-\lambda\right|\ge c\sqrt{\frac{\lambda}{t}}\right)\le \frac{3}{c\sqrt{2\pi}},t\ge T_c
$$
For fixed $\varepsilon>0$, choose $c$ s.t. $\frac{3}{c\sqrt{2\pi}}<\varepsilon$, for $t\ge \max{\{T_c,\frac{c^2\lambda}{\varepsilon^2}\}}$, we have
$$
\mathbb{P}\left(\left|\frac{N_t}{t}-\lambda\right|\ge \varepsilon\right)\le \mathbb{P}\left(\left|\frac{N_t}{t}-\lambda\right|\ge c\sqrt{\frac{\lambda}{t}}\right)\le \frac{3}{c\sqrt{2\pi}}<\varepsilon
$$
Hence, $\frac{N_t}{t}\to\lambda$ in probability. Choose $b=2^{n+1},a=2^n$, by Q3 and chebyshev's inequality, 
$$
\mathbb{P}\left(\sup_{2^n\le t\le 2^{n+1}}\left|\frac{N_t}{t}-\lambda\right|\ge \varepsilon\right)\le\frac{\mathbb{E}\left(\sup_{2^n\le t\le 2^{n+1}}\left|\frac{N_t}{t}-\lambda\right|\right)}{\varepsilon^2}\le \frac{8\lambda}{\varepsilon^2 2^n}
$$
We observe that $\sum_{n=1}^{\infty}\mathbb{P}\left(\sup_{2^n\le t\le 2^{n+1}}\left|\frac{N_t}{t}-\lambda\right|\ge \varepsilon\right)<\infty$, by Borel-Cantelli lemma and S.L.L.N, we obtain $\frac{N_t}{t}\to\lambda,a.s.$
```

^b55ecf

```ad-question
Let $\{\mathcal{F}\}_{n=1}^{\infty}$ be a decreasing sequence of sub-a-fields of $\mathcal{F}$ (i.e. $\mathcal{F}_{n+1} \subseteq\mathcal{F}_n\subseteq\mathcal{F}$), and let $X_n,n\ge 1$ be a **backward submartingale** i.e. $\mathbb{E}|X_n|<\infty$ $X_n$ is $\mathcal{F}$-measurable, and $\mathbb{E}(X_n|\mathcal{F}_{n+1})\ge X_{n+1}, a.s-\mathbb{P}$, for every $n \ge 1$. Then $l=\lim_{n\to\infty}\mathbb{E}X_n>-\infty$ implies that the sequence $\{X_n\}_{n=1}^{\infty}$ is uniformly integrable.
```

^afeb3e

```ad-done
Refer to Chung Thm 9.4.7
![[Pasted image 20260321164422.png]]
```

```ad-warning

```

```ad-question
Suppose that the filtration $\{\mathcal{F}_t\}$ satisfies the usual conditions. Then every right-continuous, uniformly integrable supermartingale $X_t$ admits **the Riesz decomposition $X_t = M_t + Z_t, a.s. \mathbb{P}$**, as the sum of a right-continuous, uniformly integrable martingale $M_t$ and a potential $Z_t$.
```

```ad-done
By convergence of supermartingale, there exists $X_{\infty}\in L^1$, s.t.
$$
X_t\to X_{\infty},a.s.\text{and in }L^1
$$
Let $M_t=\mathbb{E}[X_\infty|\mathcal{F}_t]$ and $Z_t=X_t-M_t$. Since $X_t$ is uniformly integrable, then $M_t$ is uniformly integrable. $\mathbb{E}[Z_t]=\mathbb{E}X_t-\mathbb{E}M_t=\mathbb{E}X_t-X_{\infty}\to0$ as $t\to\infty$. Hence, $X_t$ admits the Riesz decomposition.
```

```ad-question
Let $N_t$ be a Poisson process with parameter $\lambda > 0$. For $u\in\mathbb{C}$ and $i = \sqrt{-1}$, define the process
$$
X_t=\exp{[iuN_t-\lambda t(e^{iu}-1)]},0\le t<\infty
$$
1. Show that $Re(X_t),Im(X_t)$ are martingales.
2. Consider $X$ with $u = - i$. Does this martingale satisfy the equivalent conditions of [[#^3e0f1e|Martingale L^1 convergence]]?
```

```ad-done
title:Done for 1
Since $N_t-N_s$ is independent with $\mathcal{F}_s$ and by c.h. function of Poisson distribution, we have 
$$
\mathbb{E}(e^{iu(N_t-N_s)})=\exp{\lambda(t-s)(e^{iu}-1)}
$$
then 
$$
\begin{align}
\mathbb{E}[X_t|\mathcal{F}_s]&=\exp{(-\lambda t(e^{iu}-1))}\mathbb{E}(e^{iu N_t}|\mathcal{F}_s)\\
&=\exp{(-\lambda t(e^{iu}-1))}e^{iuN_s}\mathbb{E}(e^{iu (N_t-N_s)})\\
&=\exp{(-\lambda t(e^{iu}-1))}e^{iuN_s}\exp{\lambda(t-s)(e^{iu}-1)}\\
&=\exp{(-\lambda s(e^{iu}-1))}e^{iuN_s}=\exp{[iuN_s-\lambda s(e^{iu}-1)]}=X_s
\end{align}
$$
Hence, $X_t$ is a martingale and thus $Re(X_t)$ and $Im(X_t)$ are also martingale.
```

```ad-done
title:Done for 2
Let $u=-i$, then $X_t=\exp{[N_t-\lambda t(e-1)]}$. Note that $\mathbb{E}(X_t)=1$, but $X_t\to0,a.s.$ Hence, $X_t$ doesn't converge in $L^1$ and doesn't satisfy the equivalent conditions.
```

```ad-question
A submartingale of constant expectation, i.e., with $\mathbb{E}(X_t) = \mathbb{E}(X_0)$ for every $t \ge 0$ is a martingale.
```

^77be8e

```ad-done
Since $X_t$ is a submartingale, then $\mathbb{E}(X_t|\mathcal{F}_{s})\ge X_s$. Let $Y=\mathbb{E}(X_t|\mathcal{F}_{s})-X_s\ge 0$. Then 
$$
\mathbb{E}(Y)=\mathbb{E}(X_t)-\mathbb{E}(X_s)=\mathbb{E}(X_0)-\mathbb{E}(X_0)=0
$$
Hence, $Y=0,a.s.$ i.e. $\mathbb{E}(X_t|\mathcal{F}_s)=X_s$, $X_t$ is a martingale.
```

```ad-question
Suppose that $\{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ is a right-continuous submartingale and $S \leq T$ are stopping times of $\{\mathcal{F}_t\}$. Then

1. $\{X_{T \wedge t}, \mathcal{F}_t; 0 \leq t < \infty\}$ is a submartingale;

2. $\mathbb{E}[X_{T \wedge t} | \mathcal{F}_S] \geq X_{S \wedge t}, a.s. \mathbb{P}$, for every $t \geq 0$.
```

^c29c8c

```ad-done
title:Done for 1
Consider the decomposition, for $0\le s<t$, $X_{T\wedge t}=X_{T\wedge t}\mathbb{1}_{\{T\le s\}}+X_{T\wedge t}\mathbb{1}_{\{T>s\}}$. Note that $\{T\le s\}$ and $\{T> s\}$ are $\mathcal{F}_s$-measurable. On $\{T\le s\}$, $T\wedge t=T=T\wedge s$ and $X_{T\wedge s}$ is $\mathcal{F}_{s}$-measurable. On $\{T> s\}$, $s\le  T\wedge t\le t$ and thus $T\wedge t$ is bounded stopping time. By [[Continuous-Time Martingales#^675f51|optional sampling theorem of bounded stopping time]], we obtain $\mathbb{E}(X_{T\wedge t}|\mathcal{F}_s)\ge X_s=X_{T\wedge s}$. Above all, we have 
$$
\begin{align}
\mathbb{E}(X_{T\wedge t}|\mathcal{F}_{s})&=\mathbb{E}(X_{T\wedge t}\mathbb{1}_{\{T\le s\}}|\mathcal{F}_s)+\mathbb{E}(X_{T\wedge t}\mathbb{1}_{\{T>s\}}|\mathcal{F}_s)\\
&\ge X_{T\wedge s}\mathbb{1}_{\{T\le s\}}+X_{T\wedge s}\mathbb{1}_{\{T>s\}}=X_{T\wedge s}
\end{align}
$$
Hence, $X_{T\wedge t}$ is a submartingale.
```

```ad-done
title:Done for 2
Consider the decomposition, for $t\ge 0$, $X_{T\wedge t}=X_{T\wedge t}\mathbb{1}_{\{S\le t\}}+X_{T\wedge t}\mathbb{1}_{\{S> t\}}$. Note that $\{S\le t\}$ and $\{S>t\}$ are $\mathcal{F}_S$-measurable. 
On $\{S\le t\}$, $S\le T\wedge t\le t$ and thus $T\wedge t$ is a bounded stopping time. By [[Continuous-Time Martingales#^675f51|optional sampling theorem of bounded stopping time]], we obatain $\mathbb{E}(X_{T\wedge t}\mathbb{1}_{\{S\le t\}}|\mathcal{F}_S)\ge X_{S\wedge t}$
On $\{S>t\}$, $X_{T\wedge t}=X_t=X_{S\wedge t}$.
Above all, we have 
$$
\begin{align}
\mathbb{E}(X_{T\wedge t}|\mathcal{F}_S)&=\mathbb{E}(X_{T\wedge t}\mathbb{1}_{\{S\le t\}}|\mathcal{F}_S)+\mathbb{E}(X_{T\wedge t}\mathbb{1}_{\{S>t\}})\\
&\ge X_{S\wedge t}\mathbb{1}_{\{S\le t\}}+X_{S\wedge t}\mathbb{1}_{\{S>t\}}=X_{S\wedge t}
\end{align}
$$
```

```ad-question
A right-continuous process $X = \{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ with $\mathbb{E}|X_t| < \infty; 0 \leq t < \infty$ is a submartingale if and only if for every pair $S \leq T$ of bounded stopping times of the filtration $\{\mathcal{F}_t\}$ we have  
$$\quad \mathbb{E}(X_T) \geq \mathbb{E}(X_S)$$
```

```ad-done
$\Longrightarrow$: By [[Continuous-Time Martingales#^675f51|optional sampling theorem of bounded stopping time]], we have 
$$
\mathbb{E}(X_T|\mathcal{F}_S)\ge X_S\Longrightarrow\mathbb{E}(X_T)\ge \mathbb{E}(X_S)
$$
$\Longleftarrow$: For $0\le s<t<\infty$, consider the stopping time $S(\omega)=s\mathbb{1}_{A}(\omega)+t\mathbb{1}_{A^c}(\omega)$ for every $A\in\mathcal{F}_s$. By condition $\mathbb{E}(X_T)\ge \mathbb{E}(X_S)$, we have 
$$
\begin{align}
\mathbb{E}(X_t)\ge \mathbb{E}(X_S)&=\mathbb{E}(X_S\mathbb{1}_A)+\mathbb{E}(X_S\mathbb{1}_{A^c})\\
&=\mathbb{E}(X_s\mathbb{1}_A)+\mathbb{E}(X_t\mathbb{1}_{A^c})
\end{align}
$$
We obtain $\mathbb{E}(X_t\mathbb{1}_{A})\ge \mathbb{E}(X_s\mathbb{1}_A)$ for any $A\in\mathcal{F}_s$. Hence, $X_t$ is a submartingale.
```

```ad-question
Let  $T$  be a bounded stopping time of the filtration $\{\mathcal{F}_t\}$, which satisfies the usual conditions, and define $\tilde{\mathcal{F}}_t = \mathcal{F}_{T+t}$, $t \geq 0$. Then $\{\tilde{\mathcal{F}}_t\}$ also satisfies the usual conditions.

1. If $X = \{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ is a right-continuous submartingale, then so is $\tilde{X} = \{ \tilde{X}_t \triangleq X_{T+t} - X_T, \tilde{\mathcal{F}}_t; 0 \leq t < \infty \}$.

2. If $\tilde{X} = \{ \tilde{X}_t, \tilde{\mathcal{F}}_t; 0 \leq t < \infty\}$ is a right-continuous submartingale with $\tilde{X}_0 = 0$, $a.s.  \mathbb{P}$ , then $X = \{X_t \triangleq \tilde{X}_{(t-T) \vee 0}, \mathcal{F}_t; 0 \leq t < \infty\}$ is also a submartingale.
```

```ad-done
title:Done for 1
Note that for $0\le s<t$
$$
\begin{align}
\mathbb{E}(\tilde{X}_t|\tilde{\mathcal{F}}_s)=\mathbb{E}(X_{T+t}-X_T|\mathcal{F}_{T+s})=\mathbb{E}(X_{T+t}|\mathcal{F}_{T+s})-\mathbb{E}(X_T|\mathcal{F}_{T+s})
\end{align}
$$
Since $X_{T}$ is $\mathcal{F}_{T+s}$, $\mathbb{E}(X_T|\mathcal{F}_{T+s})=X_T$. Since $T+t$ is bounded stopping time, by [[Continuous-Time Martingales#^675f51|optional sampling theorem of bounded stopping time]], $\mathbb{E}(X_{T+t}|\mathcal{F}_{T+s})\ge X_{T+s}$. Hence, we obtain $\mathbb{E}(\tilde{X}_t|\tilde{\mathcal{F}}_s)\ge X_{T+s}-X_T=\tilde{X}_s$, $\tilde{X}_t$ is a submartingale.
```

```ad-done
title:Done for 2
Note that $\tilde{\mathcal{F}_t}=\mathcal{F}_{T+t}\Longrightarrow\tilde{\mathcal{F}}_{t-T}=\mathcal{F}_{t}$. Then for $0\le s<t$ we have 
$$
\begin{align}
\mathbb{E}(X_t|\mathcal{F}_s)&=\mathbb{E}(\tilde{X}_{(t-T)\vee0}|\mathcal{F}_{s-T})\\
&=\mathbb{E}(\tilde{X}_{(t-T)\vee0}\mathbb{1}_{\{T\le s\}}|\mathcal{F}_{s-T})+\mathbb{E}(\tilde{X}_{(t-T)\vee0}\mathbb{1}_{\{T>s\}}|\mathcal{F}_{s-T})
\end{align}
$$
On $\{T\le s\}$, $s-T\le t-T$ and $\tilde{X}_{(t-T)\vee0}=\tilde{X}_{t-T}$. Since $T$ is bounded, by [[Continuous-Time Martingales#^675f51|optional sampling theorem of bounded stopping time]], $\mathbb{E}(\tilde{X}_{t-T}|\mathcal{F}_{s-T})\ge \tilde{X}_{s-T}$. 
On $\{T>s\}$, since $\tilde{X}_0=0$, then 
$$
\mathbb{E}(\tilde{X}_{(t-T)\vee0}\mathbb{1}_{\{T>s\}}|\mathcal{F}_{s-T})\ge 0=\mathbb{E}(\tilde{X}_{(s-T)\vee0}\mathbb{1}_{\{T>s\}}|\mathcal{F}_{s-T})
$$
Above all, we obtain
$$
\mathbb{E}(X_t|\mathcal{F}_s)\ge \tilde{X}_{s-T}\mathbb{1}_{\{T\le s\}}+\tilde{X}_{(s-T)\vee0}\mathbb{1}_{\{T>s\}}=\tilde{X}_{(s-T)\vee0}=X_s
$$
```

```ad-question
Let $Z = \{Z_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be a continuous, nonnegative martingale with $Z_\infty \triangleq \lim_{t \to \infty} Z_t = 0$, a.s. $\mathbb{P}$. Then for every $s \geq 0$, $b > 0$:

1. $$\mathbb{P}\left[\sup_{t > s} Z_t \geq b \mid \mathcal{F}_s\right] = \frac{1}{b} Z_s, \quad \text{a.s. on } \{Z_s < b\}.$$

2. $$\mathbb{P}\left[\sup_{t \geq s} Z_t \geq b\right] = \mathbb{P}[Z_s \geq b] + \frac{1}{b} \mathbb{E}[Z_s \mathbb{1}_{\{Z_s < b\}}].$$
```

```ad-done
title:Done for 1
Fix $s\ge 0$, define the stopping time, 
$$
\tau=\inf\{t>s:Z_t\ge b\}
$$
and we define $\inf\emptyset=\infty$. Since $Z_t$ is continuous and $\tau$ is a bounded stopping time, $Z_\tau=b$ on $\{\tau<\infty\}$. By [[Continuous-Time Martingales#^675f51|optional sampling theorem of bounded stopping time]], we have 
$$
Z_s=\mathbb{E}(Z_{\tau\wedge t}|\mathcal{F}_s)
$$
By DCT, let $t\to\infty$, $Z_{\tau\wedge t}\to Z_\tau\mathbb{1}_{\{\tau<\infty\}}+Z_{\infty}\mathbb{1}_{\{\tau=\infty\}} = b\cdot\mathbb{1}_{\{\tau<\infty\}}$. Then 
$$
Z_s=b\cdot\mathbb{P}(\tau<\infty|\mathcal{F}_s)
$$
Note that $\{\tau<\infty\}=\{\sup_{t>s}Z_t\ge b\}$. Hence, we obtain 
$$\mathbb{P}\left[\sup_{t > s} Z_t \geq b \mid \mathcal{F}_s\right] = \frac{1}{b} Z_s$$
```

```ad-done
title:Done for 2
By Law of Total Probability, we have 
$$
\begin{align}
\mathbb{P}\left[\sup_{t \geq s} Z_t \geq b\right]=\mathbb{P}\left[Z_s\ge b\right]+\mathbb{P}\left[\sup_{t \geq s} Z_t \geq b,Z_s<b\right]
\end{align}
$$
For the second probability, by Q1 and conditional expectation, 
$$
\mathbb{P}\left[\sup_{t \geq s} Z_t \geq b,Z_s<b\right]=\mathbb{E}\left(\mathbb{1}_{\{Z_s<b\}}\mathbb{P}\left[\sup_{t \geq s} Z_t \geq b|\mathcal{F}_s\right]\right)=\mathbb{E}\left[\mathbb{1}_{\{Z_s<b\}}\frac{Z_s}{b}\right]
$$
Above all, we obtain
$$
\mathbb{P}\left[\sup_{t \geq s} Z_t \geq b\right] = \mathbb{P}[Z_s \geq b] + \frac{1}{b} \mathbb{E}[Z_s \mathbb{1}_{\{Z_s < b\}}]
$$
```

```ad-question
Let $\{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be a continuous, nonnegative supermartingale and $T = \inf\{t \geq 0; X_t = 0\}$. Show that
$$X_{T+t} = 0; \quad 0 \leq t < \infty \quad \text{holds a.s. on } \{T < \infty\}.$$
```

```ad-done
Obviously, $T$ is a stopping time. By [[Stopping Times#^e32b22|Proposition of stopping time]], $T+t$ is also a stopping time for every $t\ge 0$. By [[Continuous-Time Martingales#^1b13f7|optional sampling theorem of supermartingale]], we have 
$$
\mathbb{E}(X_{T+t}|\mathcal{F}_T)\le X_{T}=0\Longrightarrow\mathbb{E}(X_{T+t})\le0
$$
Since $X_t$ ia nonnegetive, then $X_{T+t}=0,a.s.-\mathbb{P}$.
```

```ad-question
Suppose that the filtration $\{\mathcal{F}_t\}$ satisfies the usual conditions and let $X^{(n)} = \{X_t^{(n)}, \mathcal{F}_t; 0 \leq t < \infty\}$, $n \geq 1$ be an increasing sequence of right-continuous supermartingales, such that the random variable $\xi_t \triangleq \lim_{n \to \infty} X_t^{(n)}$ is nonnegative and integrable for every $0 \leq t < \infty$. Then there exists an RCLL supermartingale $X = \{X_t, \mathcal{F}_t; 0 \leq t < \infty\}$ which is a modification of the process $\xi = \{\xi_t, \mathcal{F}_t; 0 \leq t < \infty\}$.
```

```ad-done
Firstlt, we check $\xi_t$ is a supermartingale. For $0\le s<t$ and $A\in \mathcal{F}_s$, since $X^{(n)}_t$ is a supermartingale, we have 
$$
\int_{A}X^{(n)}_t{d}\mathbb{P}\le \int_AX^{(n)}_s{d}\mathbb{P}
$$
Since $X^{(n)}_t\uparrow \xi_t$ as $n\to\infty$, by MCT,
$$\int_{A}\xi_t{d}\mathbb{P}\le \int_A\xi_s{d}\mathbb{P}$$
Hence, $\xi_t$ is a supermartingale. Next, by [[Continuous-Time Martingales#^2cd6c5|modification of right-continuous martingale]], it suffices to show that $\mathbb{E}(\xi_t)$ is right-continuous. Since $X^{(n)}_t$ is right-continuous, and $\xi_t=\lim_{n\to\infty}X^{(n)}_t$. Note that $\mathbb{E}(X^{(n)}_t)$ is right-continuous, by MCT, $\mathbb{E}(\xi_t)$ is right-continuous. Hence, $\xi_t$ exists a RCLL modification $X_t$.
```
