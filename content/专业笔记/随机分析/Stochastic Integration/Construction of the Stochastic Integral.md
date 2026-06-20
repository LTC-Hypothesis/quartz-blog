# Introduction
> [!warning] $M_t$ has infinite variation
> Suppose $M_t\in\mathcal{M}_2^c$, note that $M_t$ has [[Continuous, Square-Integrable Martingales#^56ddbe|infinite variation]], then we cann't define the integral of the form 
> $$
> I_T(X)=\int_0^TX_t(\omega){d}M_t
> $$
> as ordinary Lebesgue-Stieltjes integral.

> [!warning] But $M_t$ has finite quadratic variation
> Note that $M_t\in\mathcal{M}_2^c$ has finite quadratic variation $\langle M\rangle_t$ s.t. $M_t^2-\langle M\rangle_t$ be a [[Continuous, Square-Integrable Martingales#^d32204|martingale]]. Moreover, $\langle M\rangle_t$ is increasing.

> [!def]
> We define the measure
> $$
> \mu_M(A)=\mathbb{E}\int_{0}^{\infty}\mathbb{1}_A(t,\omega){d}\langle M\rangle_t(\omega)
> $$
> We shall say that two measurable, adapted processe $X_t$ and $Y_t$ are equivalent if 
> $$
> X_t(\omega)=Y_t(\omega),\mu_M-a.s.
> $$

> [!def] $L^2$-norm
> For a measurable, $\mathcal{F}_t$-adapted process $X$, we define
> $$
> [X]_T^2=\mathbb{E}\int_{0}^{T}X^2_t{d}\langle M\rangle_t
> $$
> By above norm, we say $X_t$ and $Y_t$ are equivalent iff $[X-Y]_T=0$.

> [!def]
> We denote the equivalent class
> $$
> \mathscr{L}=\left\{X_t:X_t \mbox{ is measurable, $\mathcal{F}_t$-adapted process},[X]_T<\infty\right\}
> $$
> we define the metric 
> $$
> [X]=\sum_{n=1}^{\infty}\frac{1\wedge[X]_n}{2^n}
> $$
> and 
> $$
> \mathscr{L}^*=\left\{X_t:X_t\mbox{ is progressively measurable},[X]_T<\infty\right\}
> $$

> [!def]
> We denote
> $$
> \mathscr{L}_T^*=\left\{X_t:X_t\in\mathscr{L}^*,\mathbb{E}\int_{0}^{T}X_t^2{d}\langle M\rangle_t<\infty\right\}
> $$
> A Hilbert space 
> $$
> \mathscr{H}_T=L^2([0,T]\times\Omega,\mathscr{B}[0,T]\otimes\mathscr{F}_T,\mu_M)
> $$

> [!lemma]
> For $0<T\le \infty$, $\mathscr{L}^*_T$ is a subspace of $\mathscr{H}_T$. In particular, $\mathscr{L}^*_T$ is complete under the norm $[X]_T$

**Proof**
Let $\{X^{(n)}_t\}_{n=1}^{\infty}\subseteq\mathscr{L}^*_T$ and $X^{(n)}\to X_{t}\in\mathscr{H}_T$. By after extracting subsequence s.t. 
$$
\mu_M\left(\{(t,\omega)\in[0,T]\times\Omega:\lim_{n\to\infty}X^{(n)}_t\ne X_t\}\right)=0
$$
implies $X^{(n)}\to X_t,\mu_M-a.s.$ for $(t,\omega)$. Since $X_t\in\mathscr{H}_T$, $X_{t}$ is $\mathcal{B}[0,T]\otimes\mathcal{F}$-measurable, but may not be progressively measurable. We should take a representation element which is progressively measurable in equivalent class. 
$$
A\triangleq\left\{(t,\omega):\lim_{n\to\infty}X^{(n)}_t\mbox{ exists}\right\}
$$
We define the modification
$$
Y_t(\omega)=\begin{cases}
\lim_{n\to\infty}X^{(n)}_t(\omega),&(t,\omega)\in A\\
0,&(t,\omega)\notin A
\end{cases}
$$
$Y_t$ satisfies the progressively measurable and is equivalent to $X$. Since each $X^{(n)}_t$ are progressively measurable and $Y_t$ is the pointwise limit of $X^{(n)}$, $Y_t$ inherits the progressively measurable from $X^{(n)}$. Since $X^{(n)}_t\to X_t,\mu_M-a.s.$ for $(t,\omega)\in A$ and thus $Y_t=X_t,\mu_M-a.s.$ 
**QED**
# Simple Processes and Approximations
> [!def] Simple process
> A process $X$ is called simple, if there exists $\{t_n\}\subseteq\mathbb{R}$ with $t_n\uparrow\infty$ and $t_0=0$, as well as r.v. $\{\xi_n\}_{n=1}^{\infty}$ with $\sup_{n\ge1}|\xi_n(\omega)|\le C<\infty$, $\forall\omega\in\Omega$ s.t. $\xi_n\in\mathcal{F}_{t_n}$ for $n\ge0$ and 
> $$
> X_t(\omega)=\xi_{0}\mathbb{1}_{\{0\}}(t)+\sum_{n=0}^{\infty}\xi_{n}\mathbb{1}_{(t_n,t_{n+1}]}(t)
> $$
> and we denote
> $$
> \mathscr{L}_0=\{\mbox{All simple processe}\}
> $$
> Note that $\mathscr{L}_0\subseteq\mathscr{L}^*\subseteq\mathscr{H}_T$.

> [!note] Construction of stochastic integral by simple process
> The integral is defined in the obvious way for $X\in\mathscr{L}_0$ as a [[The Doob-Meyer Decomposition#^6ea757|martingale transform]]:
> $$
> \begin{align}
> I_t(X)&\triangleq\sum_{i=0}^{n-1}\xi_i(M_{t_{i+1}}-M_{t_{i}})+\xi_{n}(M_{t}-M_{t_n})\\
> &=\sum_{n=0}^{\infty}\xi_n(M_{t\wedge t_{n+1}}-M_{t\wedge t_{n}})
> \end{align}
> $$
> for which $t_n\le t<t_{n+1}$. 

> [!lemma]
> Let $X$ be a bounded, measurable, $\{\mathcal{F}_t\}$-adapted process. Then there exists a sequence $\{X^{(n)}_t\}$ of simple processes s.t.
> $$
> \sup_{T>0}\lim_{n\to\infty}\mathbb{E}\int_{0}^{T}|X^{(n)}_t-X_t|^2{d}t=0
> $$

**Proof**
We W.T.S. for fixed $T>0$, a sequence of simple process $\{X^{(n,T)}\}_{n=1}^{\infty}$ s.t. 
$$
\lim_{n\to\infty}\mathbb{E}\int_{0}^{T}|X^{(n,T)}_t-X_t|^2{d}t=0
$$
Thus, for each positive integer $m$, there exists $n_m\in\mathbb{N}$ s.t. 
$$
\mathbb{E}\int_{0}^{m}|X^{(n_m,m)}_t-X_t|^2{d}t\le \frac{1}{m}
$$
The sequence $X^{(m)}_t\triangleq X^{(n_m,m)}_t$ has the desired properties. 
In order to prove the claim, we should proceeds in three steps. 
**Step1: Suppose $X$ is continuous.** 
We construct the sequence of simple process as follows
$$
X^{(n)}_t(\omega)\triangleq X_0(\omega)\mathbb{1}_{\{0\}}(t)+\sum_{k=0}^{2^n-1}X_{\frac{kT}{2^n}}(\omega)\mathbb{1}_{(\frac{kT}{2^n},\frac{(k+1)T}{2^n}]}(t)
$$
Then we have 
$$
\mathbb{E}\int_{0}^{T}|X^{(n)}_t-X_t|^2{d}t=\sum_{k=0}^{2^n-1}\mathbb{E}\int_{\frac{kT}{2^n}}^{\frac{(k+1)T}{2^n}}|X_{\frac{kT}{2^n}}-X_t|^2{d}t
$$
Since $|\frac{kT}{2^n}-t|<\frac{1}{2^n}$, $|X_{\frac{kT}{2^n}}-X_t|<\sqrt{\frac{\varepsilon}{2^n}}$, then
$$
\mathbb{E}\int_{0}^{T}|X^{(n)}_t-X_t|^2{d}t\le \varepsilon
$$
**Step2: Suppose $X$ is progressively measurable.** 
We construct the continuous, progressively measurable process 
$$
F_t(\omega)=\int_{0}^{t\wedge T}X_s(\omega){d}s,\tilde{X}_m(\omega)\triangleq m[F_t(\omega)-F_{(t-\frac{1}{m})^+}(\omega)]
$$
Recall [[Stopping Times#^ee15ca|the Exercise]], the property of progressively measurable is obtained. By step1, there exists $\tilde{X}^{(m,n)}_t$ s.t. $\lim_{n\to\infty}\mathbb{E}\int_0^T|\tilde{X}^{(m,n)}_t-\tilde{X}^{(m)}_t|^2{d}t=0$. Consider 
$$
A=\{(t,\omega)\in[0,T]\times\Omega:\lim_{m\to\infty}\tilde{X}^{(m)}_t(\omega)=X_T(\omega)\}^c
$$
$A$ is $\mathcal{B}[0,T]\otimes\mathcal{F}_T$-measurable. For each $\omega\in\Omega$, let $A_\omega=\{t\in[0,T]:(t,\omega)\in A\}\in\mathcal{B}[0,T]$. By the fundamental theorem of calculus, $\tilde{X}^{(m)}_t=F'_{u_m\wedge T}(\omega),a.s.$ under Lebesgue measure. Then $\symrm{Leb}(A_\omega)=0$. By BCT, 
$$
\lim_{m\to\infty}\mathbb{E}\int_{0}^{T}|\tilde{X}^{(m)}_t-X_t|^2{d}t=0
$$
Hence, we choose the sequence of simple process $\tilde{X}^{(m,n_m)}_t$ s.t. 
$$
\lim_{m\to\infty}\mathbb{E}\int_{0}^{T}|\tilde{X}^{(m,n_m)}_t-X_t|^2{d}t=0
$$
**Step3: Suppose $X$ is measurable and adapted.** 
Recall [[Stochastic Processes and σ-Fields#^7002e8|every measurable and adapted process has a progressively measurable modification]], then $X$ has a modification $Y$ which is progressively measurable. It suffices to show that the progressively measurable process 
$$
G_t(\omega)=\int_{0}^{t\wedge T}Y_s(\omega){d}s
$$
is a modification of $F_t(\omega)$. Let the measurable process $\eta_t=\mathbb{1}_{\{X_t(\omega)\ne Y_t(\omega)\}}$ for $0\le t\le T,\omega\in\Omega$, by Fubini, 
$$
\mathbb{E}\int_0^T\eta_t(\omega){d}t=\int_{0}^{T}\mathbb{P}[X_t\ne Y_t]{d}t=0
$$
Then we obtain $\int_0^T\eta_t(\omega){d}t=0$. Note that $\{F_t\ne G_t\}\subseteq\{\omega:\int_0^T\eta_t(\omega){d}t>0\}$, $G_t$ is $\mathcal{F}_t$-measurable. Since $\mathcal{F}_t$ contains all subsets of $\mathbb{P}$-null events, $F_t$ is also $\mathcal{F}_t$-measurable. Repeat the argument in step2, we can obtain a sequence of simple process $\{X^{(m,n_m)}_t\}$ s.t. $X^{(m,n_m)}_t\xrightarrow{L^2}X_t$. 
**QED**
> [!proposition]
> If the function $t\mapsto\langle M\rangle_t(\omega)$ is absolutely continuous w.r.t. Lebesgue measure for $\mathbb{P}$-a.e. $\omega\in\Omega$, then $\mathscr{L}^*$ is dense in $\mathscr{L}$ w.r.t. the metric of $[X]$.

**Proof**
**$X\in\mathscr{L}$ is bounded**
By above lemma, there exists $X^{(n)}$ s.t. 
$$
\sup_{T>0}\lim_{n\to\infty}\mathbb{E}\int_{0}^{T}|X^{(n)}_t-X_t|^2{d}t=0
$$
By after extracting subsequence $X^{(m_k)}$ s..t the set 
$$
\{(t,\omega)\in[0,\infty)\times\Omega:\lim_{k\to\infty}X^{(m_k)}_t=X_t\}^c
$$
has measure zero. Since $t\mapsto\langle M\rangle_t$ is absolutely continuous and by BCT, $[X^{(m_k)}_t-X_t]\to0$ as $k\to\infty$. 
**$X\in\mathscr{L}$ is not bounded**
We can take a truncation
$$
X^{(n)}_t(\omega)=X_t\mathbb{1}_{\{|X_t(\omega)|\le n\}}
$$
Then we get a sequence bounded process in $\mathscr{L}$. By DCT, we have 
$$
[X^{(n)}-X]_T=\mathbb{E}\int_0^T|X_t(\omega)|\mathbb{1}_{\{|X_t|>n\}}{d}\langle M\rangle_t\to0\mbox{ as }n\to\infty
$$
for every $T>0$. Then $[X^{(n)}-X]\to0$. Since each $X^{(n)}$ can be approximated by bounded, simple process, so is $X$. (逼近的逼近还是逼近)
**QED**
> [!lemma]
> Let $A_t$ be a continuous, increasing process adapted to the $\mathcal{F}^M_t$ where $M_t$ is a martingale. If $X_t$ is a progressively measurable process satisfies 
> $$
> \mathbb{E}\int_{0}^{T}X_t^2{d}A_t<\infty
> $$
> for each $T>0$, then there exists a sequence $X^{(n)}_t$ of simple process s.t. 
> $$
> \sup_{T>0}\lim_{n\to\infty}\mathbb{E}\int_{0}^{T}|X^{(n)}_t-X_t|^2{d}A_t=0
> $$

^cb1db7

> [!proposition]
> The set $\mathscr{L}_0$ is dense in $\mathscr{L}^*$ w.r.t. the metric $[X]$

^c16127

**Proof**
Take $A_t=\langle M\rangle_t$ in above [[#^cb1db7|lemma]].
**QED**
# Construction and Elementary Properties of the Integral
By last section, we have construct the stochastic integral $I_t(X)$ of simple process
$$
I_t(X)=\sum_{n=0}^{\infty}\xi_n(M_{t\wedge t_{n+1}}-M_{t\wedge t_n})
$$
> [!proposition] Properties of $I_t(X)$
> For $X,Y\in\mathscr{L}_0$, $0\le s< t<\infty$,
> 1. $$I_0(X)=0\tag{SP1}$$
> 2. $$\mathbb{E}[I_t(X)|\mathcal{F}_s]=I_s(X)\tag{SP2}$$
> 3. $$\mathbb{E}[(I_t(X)-I_s(X))^2|\mathcal{F}_s]=\mathbb{E}\left[\int_{s}^{t}X^2_u{d}\langle M\rangle_u|\mathcal{F}_s\right]\tag{SP3}$$
> 4. $$\|I(X)\|=[X]\tag{SP4}$$
> 5. $$\mathbb{E}[I_t(X)]^2=\mathbb{E}\int_{0}^{t}X^2_s{d}\langle M\rangle_s\tag{SP5}$$
> 6. $$I_t(\alpha X+\beta Y)=\alpha I_t(X)+\beta I_t(Y)\tag{SP6}$$

^4e8395

**Proof**
1. Obviously.
2. It can be checked by definition. $$\mathbb{E}\left[\sum_{n=0}^{\infty}\xi_n(M_{t\wedge t_{n+1}}-M_{t\wedge t_{n}})|\mathcal{F}_s\right]=\sum_{n=0}^{\infty}\xi_n(M_{s\wedge t_n}-M_{s\wedge t_{n+1}})$$ this can be verified for each of the three cases $s\le t_n,t_n<s\le t_{n+1},s>t_{n+1}$. Thus, $I_t(X)$ is a continuous martingale.
3. For $0\le s<t<\infty$, $n,m$ are chosen so that $t_{m-1}\le s<t_m$ and $t_n<t<t_{n+1}$, we compute $$\begin{align}
&\mathbb{E}[(I_t(X)-I_s(X))^2|\mathcal{F}_s]\\
=&\mathbb{E}\left[\left(\xi_{m-1}(M_{t_m}-M_s)+\sum_{k=m}^{n-1}\xi_k(M_{t_{k+1}}-M_{k})+\xi_n(M_{t}-M_{t_n})\right)^2|\mathcal{F}_s\right]\\
=&\mathbb{E}\left[\xi_{m-1}^2(M_{t_m}-M_s)^2+\sum_{k=m}^{n-1}\xi_k^2(M_{t_{k+1}}-M_{k})^2+\xi_n^2(M_{t}-M_{t_n})^2|\mathcal{F}_s\right]\\
=&\mathbb{E}\left[\xi_{m-1}^2(\langle M\rangle_{t_m}-\langle M\rangle_s)+\sum_{k=m}^{n-1}\xi_k^2(\langle M\rangle_{t_{k+1}}-\langle M\rangle_{k})+\xi_n^2(\langle M\rangle_{t}-\langle M\rangle_{t_n})|\mathcal{F}_s\right]\\
=&\mathbb{E}\left[\int_{0}^{t}X^2_u{d}\langle M\rangle_u|\mathcal{F}_s\right]
\end{align}$$
4. 
5. By 3. we obtain $I_t(X)$ is square-integrable: $I_t(X)\in\mathcal{M}_2^c$ with quadratic variation $$\langle I(X)\rangle_t=\int_{0}^{t}X_u^2{d}\langle M\rangle_u$$
6. Obviously

**QED**
> [!note] Construction of stochastic integral for $X\in\mathscr{L}^*$
> For $X\in\mathscr{L}^*$, by [[Construction of the Stochastic Integral#^c16127|density theorem]], there exists $\{X^{(n)}\}\subseteq\mathscr{L}_0$ s.t $[X^{(n)}-X]\to0$ as $n\to\infty$. Then 
> $$
> \|I(X^{(n)})-I(X^{(m)})\|=\|I(X^{(n)}-X^{(m)})\|=[X^{(n)}-X^{(m)}]\to0,\mbox{ as }n,m\to\infty
> $$
> It implies $\{I(X^{(n)})\}$ is a Cauchy sequence in $\mathcal{M}^c_2$. Since $\mathcal{M}^c_2$ is [[Continuous, Square-Integrable Martingales#^8acb93|a closed subspace and comlete]], then there exists $I(X)$ in $\mathcal{M}^c_2$ s.t. $\|I(X^{(n)})-I(X)\|\to0$ as $n\to\infty$. 

> [!def] Stochastic integral of $X\in\mathscr{L}^*$
> For $X\in\mathscr{L}^*$, the stochastic integral of $X$ w.r.t. martingale $M_t\in\mathscr{M}^c_2$ is the unique, square-integrable martingale $I(X)$ which satisfies $\|I(X^{(n)})-I(X)\|\to0$ as $n\to\infty$ for every $X^{(n)}\subseteq\mathscr{L}_0$ with $[X^{(n)}-X]\to0$. We write 
> $$
> I(X)=\int_{0}^{t}X_s^2{d}M_s
> $$

> [!proposition] Properties of stochastic integral
> $I(X)$ satisfies [[#^4e8395|the properties]]. Furthermore, for any two stopping times $S\le T$ of the filtration $\mathcal{F}_t$ and any number $t > 0$, we have
> $$
> \mathbb{E}[I_{t\wedge T}(X)|\mathcal{F}_S]=I_{t\wedge S}(X)
> $$
> With $X,Y\in\mathscr{L}^*$ we have $a.s.-\mathbb{P}$,
> $$
> \mathbb{E}[(I_{t\wedge T}(X)-I_{t\wedge S}(X))(I_{t\wedge T}(Y)-I_{t\wedge S}(Y))|\mathcal{F}_S]=\mathbb{E}\left[\int_{t\wedge S}^{t\wedge T}X_uY_u{d}\langle M\rangle_u|\mathcal{F}_S\right]
> $$
> and in particular, for any number $s$ in $[0,t]$
> $$
> \mathbb{E}[(I_{t}(X)-I_{s}(X))(I_{t}(Y)-I_{s}(Y))|\mathcal{F}_s]=\mathbb{E}\left[\int_{s}^{t}X_uY_u{d}\langle M\rangle_u|\mathcal{F}_s\right]
> $$
> Finally, 
> $$
> I_{t\wedge T}(X)=I_t(\tilde{X}),a.s. \ \tilde{X}_t(\omega)=X_t(\omega)\mathbb{1}_{\{t\le T(\omega)\}}
> $$

**Proof**
By (SP2) and [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], we obtain
$$
\mathbb{E}\left[I_{t\wedge T}(X)|\mathcal{F}_S\right]=I_{t\wedge S}(X)
$$
The same result applied to the martingale $I_t^2(X)-\int_0^t X_u^2{d}\langle M\rangle_u$. 
$$
\begin{align}
\mathbb{E}\left[(I_{t\wedge T}(X)-I_{t\wedge S}(X))^2|\mathcal{F}_S\right]&=\mathbb{E}\left[(I_{t\wedge T}^2(X)-I_{t\wedge S}^2(X))|\mathcal{F}_S\right]\\
&=\mathbb{E}\left[\int_{t\wedge S}^{t\wedge T}X^2_u{d}\langle M\rangle_u|\mathcal{F}_S\right]
\end{align}
$$
Replacing $X$ by $X+Y$ and $X-Y$, 
$$
\begin{align}
&\begin{cases}
\mathbb{E}\left[(I_{t\wedge T}(X+Y)-I_{t\wedge S}(X+Y))^2|\mathcal{F}_S\right]=\mathbb{E}\left[\int_{t\wedge S}^{t\wedge T}(X+Y)^2_u{d}\langle M\rangle_u|\mathcal{F}_S\right]\\
\mathbb{E}\left[(I_{t\wedge T}(X-Y)-I_{t\wedge S}(X-Y))^2|\mathcal{F}_S\right]=\mathbb{E}\left[\int_{t\wedge S}^{t\wedge T}(X-Y)^2_u{d}\langle M\rangle_u|\mathcal{F}_S\right]
\end{cases}\\
\Longrightarrow&\mathbb{E}[(I_{t\wedge T}(X)-I_{t\wedge S}(X))(I_{t\wedge T}(Y)-I_{t\wedge S}(Y))|\mathcal{F}_S]=\mathbb{E}\left[\int_{t\wedge S}^{t\wedge T}X_uY_u{d}\langle M\rangle_u|\mathcal{F}_S\right]
\end{align}
$$
Finally, consider $I_{t\wedge T}(X)-I_t(\tilde{X})=I_{t\wedge T}(X-\tilde{X})-[I_t(\tilde{X})-I_{t\wedge T}(\tilde{X})]$. We W.T.S. both $I_{t\wedge T}(X-\tilde{X})$ and $I_t(\tilde{X})-I_{t\wedge T}(\tilde{X})$ belongs to $\mathcal{M}^c_2$ and have quadratic variation 0. Recall the [[Continuous, Square-Integrable Martingales#^7ac13a|Exercises]], 
$$
\mathbb{E}[(I_{t\wedge T}(X-\tilde{X})-I_{s\wedge T}(X-\tilde{X}))^2|\mathcal{F}_S]=\mathbb{E}\left[\int_{s\wedge T}^{t\wedge T}(X-\tilde{X})^2{d}\langle M\rangle_u|\mathcal{F}_S\right]=0
$$
$$
\mathbb{E}\left[(I_t(\tilde{X})-I_{t\wedge T}(\tilde{X}))^2\right]=\mathbb{E}\left[\int_{t\wedge T}^{t}\tilde{X}^2_u{d}\langle M\rangle_u\right]=0
$$
**QED**
> [!warning]
> - If the sample path $t\mapsto\langle M\rangle_t(\omega)$) of the quadratic variation process $\langle M\rangle_t$ are absolutely continuous functions of $t$ for $a.s.-\mathbb{P}$, then we can define $I(X)$ on $X\in\mathscr{L}$.
> - The most important case is $M$ is standard Brownian motion which $\langle M\rangle_t=t$. We can construct simple process to approximate directly. 

# A Characterization of the Integral
> [!todo] Cross variation of stochastic integral
> Suppose $M,N\in\mathcal{M}^c_2$ and take $X\in\mathscr{L}^*(M),Y\in\mathscr{L}^*(N)$. Then $I^M_t(X)=\int_{0}^{t}X_s{d}M_s$, $I^N_t(Y)=\int_{0}^{t}Y_s{d}N_s$ are also in $\mathcal{M}^c_2$. We have 
> $$
> \langle I^M(X)\rangle_t=\int_{0}^{t}X_s^2{d}\langle M\rangle_s,\langle I^N(X)\rangle_t=\int_{0}^{t}Y_s^2{d}\langle N\rangle_s
> $$
> We want to **construct the cross variation**,
> $$
> \langle I^M(X),I^N(Y)\rangle_t=\int_{0}^{t}X_sY_s{d}\langle M,N\rangle_s\tag{$*1$}
> $$
> If $X,Y$ are simple, for $0\le s<t<\infty$,
> $$
> \mathbb{E}[(I^M_t(X)-I^M_s(X))(I^N_t(Y)-I_s^N(Y))|\mathcal{F}_s]=\mathbb{E}\left[\int_{s}^{t}X_uY_u{d}\langle M,N\rangle_s|\mathcal{F}_s\right]\tag{$*2$}
> $$
> The above two equations are equivalent. 

> [!proposition] Kunita, Watanabe
> If $M,N\in\mathcal{M}^c_2$, $X\in\mathscr{L}^*(M),Y\in\mathscr{L}^*(N)$, then $a.s.$
> $$
> \left(\int_{0}^{t}|X_sY_s|{d}\check{\xi}_s\right)^2\le \left(\int_{0}^{t}X^2_s{d}\langle M\rangle_s\right)\left(\int_{0}^{t}Y^2_s{d}\langle N\rangle_s\right)
> $$
> where $\check{\xi}_s$ is the total variation of the process $\langle M,N\rangle$ on $[0,s]$

**Proof**
Recall: $\langle M,N\rangle_t-\langle M,N\rangle_s\le\frac{1}{2}\left[\langle M\rangle_t-\langle M\rangle_s+\langle N\rangle_t-\langle N\rangle_s\right]$. Then $\check{\xi}_t$ is absolutely continuous with $\varphi(\omega)=\frac{1}{2}[\langle M\rangle_t+\langle N\rangle_t]$ for $\omega\in\hat{\Omega}$ where $\mathbb{P}(\hat{\Omega})=1$. Then there exists $f_i(\cdot,\omega):[0,\infty)\to\mathbb{R},i=1,2,3$ s.t. 
$$
\langle M\rangle_t=\int_{0}^{t}f_1(s,\omega){d}\varphi_s(\omega),\langle N\rangle_t=\int_{0}^{t}f_2(s,\omega){d}\varphi_s(\omega),\langle M,N\rangle_t=\int_{0}^{t}f_3(s,\omega){d}\varphi_s(\omega)
$$
For $\alpha,\beta\in\mathbb{R}$ and $\omega\in\Omega_{\alpha\beta}\subseteq\hat{\Omega}$ satisfying $\mathbb{P}(\Omega_{\alpha\beta})=1$, we have 
$$
\begin{align}
0&\le \langle \alpha M+\beta N\rangle_t(\omega)-\langle \alpha M+\beta N\rangle_s(\omega)\\
&=\int_{s}^{t}\alpha^2 f_1(u,\omega)+2\alpha\beta f_3(u,\omega)+\beta^2f_2(u,\omega){d}u
\end{align}
$$
This happen only if $\omega\in\Omega_{\alpha\beta}$, there exists a set $T_{\alpha\beta}\in\mathcal{B}[0,\infty)$ with $\int_{T_{\alpha\beta}}{d}\varphi_t(\omega)=0$. For $t\notin T_{\alpha\beta}$ we have 
$$
\alpha^2 f_1(t,\omega)+2\alpha\beta f_3(t,\omega)+\beta^2f_2(t,\omega)\ge0
$$
Now let $\tilde{\Omega}=\bigcap_{\alpha,\beta\in\mathbb{Q}}\Omega_{\alpha\beta}$ and $T(\omega)=\bigcap_{\alpha,\beta\in\mathbb{Q}}T_{\alpha\beta}(\omega)$ s.t. $\mathbb{P}(\tilde{\Omega})=1$ and $\int_{T}{d}\varphi_t(\omega)=0$. Fix $\omega\in\tilde{\Omega},t\notin T$, then $\alpha^2 f_1(t,\omega)+2\alpha\beta f_3(t,\omega)+\beta^2f_2(t,\omega)\ge0$. We replace $\alpha\to\alpha|X_t(\omega)|,\beta\to|Y_t(\omega)|$ and thus we obtain
$$
\alpha^2|X_t(\omega)|^2|f_1(t,\omega)|+2\alpha|X_t(\omega)||Y_t(\omega)| |f_3(t,\omega)|+|Y_t(\omega)|^2|f_2(t,\omega)|\ge0
$$
Integrating w.r.t. $d\varphi_t(\omega)$, we have 
$$
\alpha^2\int_{0}^{t}|X_s(\omega)|^2{d}\langle M\rangle_s+2\alpha\int_{0}^{t}|X_s(\omega)Y_s(\omega)|{d}\check{\xi}_s+\int_{0}^{t}|Y_t(\omega)|^2{d}\langle N\rangle_S\ge0
$$
By classical method, we can obtain the inequality.
**QED**
> [!lemma]
> If $M,N\in\mathcal{M}^c_2$, $X\in\mathscr{L}^*(M)$ and $\{X^{(n)}\}_{n=1}^{\infty}\subseteq\mathscr{L}^*(M)$ is s.t. for $T>0$, 
> $$
> \lim_{n\to\infty}\int_{0}^{T}|X_u^{(n)}-X_u|^2{d}\langle M\rangle_u=0
> $$
> then 
> $$
> \lim_{n\to\infty}\langle I(X^{(n)},N)\rangle_t=\langle I(X),N\rangle_t,0\le t\le T,a.s.-\mathbb{P}
> $$

**Proof**
Note that 
$$
\begin{align}
|\langle I(X^{(n)},N\rangle_t-\langle I(X),N\rangle_t|^2\le \langle I(X^{(n)}-X)\rangle_t\langle N\rangle_t=\int_{0}^{T}|X_u^{(n)}-X_u|^2{d}u\langle N\rangle_T
\end{align}
$$
**QED**
> [!lemma]
> If $M,N\in\mathcal{M}^c_2$, $X\in\mathscr{L}^*(M)$, then 
> $$
> \langle I^M(X),N\rangle_t=\int_{0}^{t}X_u{d}\langle M,N\rangle_u
> $$

^3666cd

**Proof**
There exists a sequence of simple process $X^{(n)}$ s.t. 
$$
\sup_{T>0}\lim_{n\to\infty}\mathbb{E}\int_{0}^{T}|X^{(n)}_u-X_u|^2{d}u=0
$$
For each $T>0$, by after extracting subsequence $\{\tilde{X}_n\}$ s.t. 
$$
\lim_{n\to\infty}\mathbb{E}\int_{0}^{T}|\tilde{X}_u^{(n)}-X_u|^2{d}\langle M\rangle_u=0
$$
Since for simple process holds $(*1)$, then 
$$
\langle I^M(\tilde{X}^{(n)}),N\rangle_t=\int_{0}^{t}\tilde{X}^{(n)}_u{d}\langle M,N\rangle_u
$$
Take limit we obtain $\langle I^M(X),N\rangle_t=\int_{0}^{t}X_u{d}\langle M,N\rangle_u$. 
**QED**
> [!proposition]
> If $M,N\in\mathcal{M}^c_2$, $X\in\mathscr{L}^*(M),Y\in\mathscr{L}^*$, then $(*1)$ and $(*2)$ hold. 

**Proof**
Similarly, by [[#^3666cd|lemma]], wer also have $\langle M,I^N(Y)\rangle_t=\int_{0}^{t}Y_u{d}\langle M,N\rangle_u$ or the differential form $d\langle M,I^N(Y)\rangle_t=Y_u{d}\langle M,N\rangle_u$. Then 
$$
\langle I^M(X),I^N(Y)\rangle_t=\int_{0}^{t}X_ud\langle M,I^N(Y)\rangle_u=\int_{0}^{t}X_uY_ud\langle M,N\rangle_u
$$
**QED**
> [!proposition]
> $M\in\mathcal{M}^c_2,X\in\mathscr{L}^*(M)$, the $I^M(X)$ is the unique martingale $\Phi\in\mathcal{M}^c_2$ satisfying 
> $$
> \langle\Phi,N\rangle_t=\int_{0}^{t}X_u{d}\langle M,N\rangle_u
> $$
> for $\forall N\in\mathcal{M}^c_2$. 

^09e22b

**Proof**
Suppose $\Phi$ satisfies $\langle\Phi,N\rangle_t=\int_{0}^{t}X_u{d}\langle M,N\rangle_u$ and $\langle I^M(X),N\rangle_t=\int_{0}^{t}X_u{d}\langle M,N\rangle_u$, then 
$$
\langle \Phi-I^M(X),N\rangle_t=0,0\le t<\infty,a.s.-\mathbb{P}
$$
Set $N=\Phi-I^M(X)$, then $N=0$ i.e. $\Phi=I^M(X)$.
**QED**
> [!proposition]
> $M\in\mathcal{M}^c_2,X\in\mathscr{L}^*(M)$ and $N\triangleq I^M(X)$. Suppose further $Y\in\mathscr{L}^*(N)$. Then $MN\in\mathscr{L}^*(M)$ adn $I^N(Y)=I^M(XY)$.

**Proof**
$\langle N\rangle_t=\int_{0}^{t}X^2_s{d}\langle M\rangle_s$, we have 
$$
\mathbb{E}\int_{0}^{T}X_s^2Y_s^2{d}\langle M\rangle_s=\mathbb{E}\int_{0}^{T}Y^2_s{d}\langle N\rangle_s,T>0
$$
so $XY\in\mathscr{L}^*(M)$. For any $\tilde{N}\in\mathcal{M}^c_2$, $d\langle N,\tilde{N}\rangle_t=X_td\langle M,\tilde{N}\rangle_t$ and thus 
$$
\langle I^M(XY),\tilde{N}\rangle_t=\int_{0}^{t}X_sY_s{d}\langle M,\tilde{N}\rangle_s=\int_{0}^{t}Y_s{d}\langle N,\tilde{N}\rangle_s=\langle I^N(Y),\tilde{N}\rangle_t
$$
Hence, $I^M(XY)=I^N(Y)$. 
**QED**
> [!proposition]
> Suppose $M, \tilde{M} \in \mathcal{M}_2^c$, $X \in \mathcal{L}^*(M)$, and $\tilde{X} \in \mathcal{L}^*(\tilde{M})$, and there exists a stopping time $T$ of the common filtration for these processes, such that for $\mathbb{P}$-almost every $\omega$
> $$
> X_{t \wedge T(\omega)}(\omega) = \tilde{X}_{t \wedge T(\omega)}(\omega), \quad M_{t \wedge T(\omega)}(\omega) = \tilde{M}_{t \wedge T(\omega)}(\omega); \quad 0 \leq t < \infty.
> $$
> Then
> $$
> I_{t \wedge T(\omega)}^M(X)(\omega) = I_{t \wedge T(\omega)}^{\tilde{M}}(\tilde{X})(\omega); \quad 0 \leq t < \infty, \text{ for } \mathbb{P}\text{-a.e. } \omega.
> $$

^159d5e

**Proof**
For any $N\in\mathcal{M}^c_2$, we have $\langle M-\tilde{M},N\rangle_{t\wedge T}=0$ and thus $\langle I^M(X)-I^{\tilde{M}}(X),N\rangle_{t\wedge T}=0$. Set $N=I^M(X)-I^{\tilde{M}}(X)$. By [[Continuous, Square-Integrable Martingales#^7ac13a|Exercise]], we obtain $I^M_{t\wedge T}(X)=I_{t\wedge T}^{\tilde{M}}(X)$. 
**QED**
# Integration with Respect to Continuous, Local Martingales
> [!def]
> Let $M\in\mathcal{M}^{c,loc}$ with $M_0=0$ and $\mathcal{F}_t$ satisfies usual condition. We denote by 
> $$
> \mathscr{P}=\left\{X_t:X_t\mbox{ is measurable, adapted and }\mathbb{P}\left[\int_{0}^{T}X_t^2{d}\langle M\rangle_t<\infty\right]=1\right\}
> $$
> and
> $$
> \mathscr{P}^*=\left\{X_t:X_t\mbox{ is progressively measurable and }\mathbb{P}\left[\int_{0}^{T}X_t^2{d}\langle M\rangle_t<\infty\right]=1\right\}
> $$ 

> [!warning]
> Note that $\mathscr{P}^*\subseteq\mathscr{P}$, $\mathscr{L}\subseteq\mathscr{P}$ and $\mathscr{L}^*\subseteq\mathscr{P}^*$. 

> [!note] Construction of stochastic integral for local martingale
> We construct the integral in $\mathscr{P}^*$. If $t\mapsto\langle M\rangle_t(\omega)$ is absolutely continuous, we can construct in $\mathscr{P}$. 
> For $M\in\mathcal{M}^{c,loc}$, there exists a sequence of stopping time $S_n\uparrow\infty$ s.t. $M_{t\wedge S_n}\in\mathcal{M}^c_2$. For $X\in\mathscr{P}^*$, one can construct another bounded stopping times by setting 
> $$
> R_n(\omega)=n\wedge \inf\left\{0\le t<\infty:\int_{0}^{t}X^2_s{d}\langle M\rangle_s\ge n\right\}
> $$
> Note that $R_n(\omega)\uparrow\infty,a.s.-\mathbb{P}$. Set $T_n(\omega)=R_n(\omega)\wedge S_n(\omega)$ and 
> $$
> M^{(n)}_t=M_{t\wedge T_n}(\omega),X^{(n)}_t=X_t(\omega)\mathbb{1}_{\{T_n(\omega)\ge t\}}
> $$
> Then $M^{(n)}_t\in\mathcal{M}^c_2,X^{(n)}_t\in\mathscr{L}^*(M^{(n)})$ and thus $I^{M^{(n)}}_t(X^{(n)})$ is defined. By [[#^159d5e|proposition]], for $1\le n\le m$, $I^{M^{(n)}}_t(X^{(n)})=I^{M^{(m)}}_t(X^{(m)}),0\le t\le T_n$. Hence, we define the stochastic integral as 
> $$
> I_t(X)\triangleq I^{M^{(n)}}_t(X^{(n)}),\mbox{ on }\{0\le t\le T_n\}
> $$
> This definition is consistent, is independent of the choice of $\{S_n\}$, if and determines a continuous process, which is also a **local martingale**.

> [!def]
> For $M\in\mathcal{M}^{c,loc}$, $X\in\mathscr{P}^*$, the stochastic integral of $X$ w.r.t. $M$ is the process $I(X)$ in $\mathcal{M}^{c,loc}$ defined by $I_t(X)\triangleq I^{M^{(n)}}_t(X^{(n)})$. We also write as $I_t(X)=\int_{0}^{t}X_sdM_s$.

> [!proposition] Properties of stochastic integral
> 1. $$I_0(X)=0$$
> 2. $$I_t(\alpha X+\beta Y)=\alpha I_t(X)+\beta I_t(Y)$$
> 3. $$\langle I(X)\rangle_t=\int_{0}^{t}X_s^2{d}\langle M\rangle_s$$
> 4. For $\tilde{X}_t(\omega)=X_t\mathbb{1}_{\{T(\omega)\ge t\}}$, 
>    $$
>    I_{t\wedge T}(X)=I_t(\tilde{X})
>    $$
> 5. $$\langle I^M_t(X),I^N_t(Y)\rangle_t=\int_{0}^{t}X_sY_s{d}\langle M,N\rangle_s$$
> 6. $I^M(X)$ is the unique local martingale $\Phi\in\mathcal{M}^{c,loc}$ which satisfying $\langle\Phi,N\rangle_t=\int_{0}^{t}X_s{d}\langle M,N\rangle_s$ for every $N\in\mathcal{M}^c_2$ or $N\in\mathcal{M}^{c,loc}$. 

^cff966

> [!proposition]
> Let $M\in\mathcal{M}^{c,loc},\{X^{(n)}\}\subseteq\mathscr{P}^*(M),X\in\mathscr{P}^*(M)$ and for some stopping time $T$ of $\mathcal{F}_t$ we have $$\int_{0}^{T}|X^{(n)}_s-X_s|^2{d}\langle M\rangle_s\xrightarrow{\mathbb{P}}0,as \ n\to\infty$$
> Then 
> $$
> \sup_{0\le t\le T}\left|\int_{0}^{t}X^{(n)}_s{d}M_s-\int_{0}^{t}X_s{d}M_s\right|\xrightarrow{\mathbb{P}}0,as \ n\to\infty
> $$

**Proof**
Recall: [[Continuous, Square-Integrable Martingales#^58ac04|Exercise]] and [[#^cff966|property6.]]. Denote by $I^{(n)}_t=\int_{0}^{t}X^{(n)}_s-X_s{d}M_s$. Then 
$$
\langle I^{(n)}\rangle_T=\int_{0}^{T}|X^{(n)}_s-X_s|^2{d}\langle M\rangle_s\xrightarrow{\mathbb{P}}0\Longrightarrow\sup_{0\le t\le T}|I^{(n)}_t|\xrightarrow{\mathbb{P}}0
$$
**QED**

---
# Exercises
> [!question]
> This problem outlines a method by which the use of Proposition 1.1.12, a result not proved in this text, can be avoided in part (c) of the proof of Lemma 2.4. Let $X$ be a bounded, measurable, $\{\mathcal{F}_t\}$-adapted process. Let $0 < T < \infty$ be fixed. We wish to construct a sequence $\{ X^{(k)} \}_{k=1}^\infty$ of simple processes so that
>
> $$
> \lim_{k \to \infty} \mathbb{E} \int_0^T |X_t^{(k)} - X_t|^2 \, dt = 0.
> $$
>
> To simplify notation, we set $X_t = 0$ for $t \leq 0$. Let $\varphi_n : \mathbb{R} \to \{ j2^{-n}; j = 0, \pm 1, \pm 2, \dots \}$ be given by
>
> $$
> \varphi_n(t) = \frac{j-1}{2^n} \quad \text{for} \quad \frac{j-1}{2^n} < t \leq \frac{j}{2^n}.
> $$
>
> 1. Fix $s \geq 0$. Show that $t - (1/2^n) \leq \varphi_n(t-s) + s < t$, and that
>
> $$
> X_t^{(n,s)} \triangleq X_{\varphi_n(t-s)+s}, \quad \mathcal{F}_t; \quad t \geq 0
> $$ 
>
> is a simple, adapted process.
>
> 2. Show that
>
> $$
> \lim_{n \to \infty} \mathbb{E} \int_0^T |X_t - X_{t-n}|^2 \, dt = 0.
> $$
>
> 3. Use (1) and (2) to show that
>
> $$
> \lim_{n \to \infty} \mathbb{E} \int_0^T \int_0^1 |X_t^{(n,s)} - X_t|^2 \, ds \, dt = 0.
> $$
>
> 4. Show that for some choice of $s \geq 0$ and some increasing sequence $\{ n_k \}_{k=1}^\infty$ of integers, (2.8) holds with $X^{(k)} = X^{(n_k,s)}$.

> [!done]
> 

> [!question]
> Let $W = \{W_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be a standard, one-dimensional Brownian motion, and let $T$ be a stopping time of $\{\mathcal{F}_t\}$ with $\mathbb{E}T < \infty$. Prove the Wald identities
>
> $$
> \mathbb{E}(W_T) = 0, \quad \mathbb{E}(W_T^2) = \mathbb{E}T.
> $$
>
> (Warning: The optional sampling theorem cannot be applied directly because $W$ does not have a last element and $T$ may not be bounded. The stopping time $t \wedge T$ is bounded for fixed $0 \leq t < \infty$, so $\mathbb{E}(W_{t \wedge T}) = 0$, $\mathbb{E}(W_{t \wedge T}^2) = \mathbb{E}(t \wedge T)$, but it is not a priori evident that
>
> $$
> \lim_{t \to \infty} \mathbb{E}(W_{t \wedge T}) = \mathbb{E}W_T, \quad \lim_{t \to \infty} \mathbb{E}(W_{t \wedge T}^2) = \mathbb{E}(W_T^2).
> $$
>

> [!done]
> 

> [!question]
> Let $W$ be as in Problem 2.12, let $b$ be a real number, and let $T_b$ be the passage time to $b$ of (2.6.1). Use Problem 2.12 to show that for $b \neq 0$, we have $\mathbb{E}T_b = \infty$.

> [!done]
> 

> [!question]
> Let $M = \{M_t, \mathcal{F}_t; 0 \leq t < \infty\}$ and $N = \{N_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be in $\mathcal{M}_2$ and suppose $X \in \mathcal{L}_\infty^*(M)$, $Y \in \mathcal{L}_\infty^*(N)$. Then the martingales $I^M(X)$, $I^N(Y)$ are uniformly integrable and have last elements $I_\infty^M(X)$, $I_\infty^N(Y)$, the cross-variation $\langle I^M(X), I^N(Y) \rangle$ converges almost surely as $t \to \infty$, and
> $$
> \mathbb{E}[I_\infty^M(X)I_\infty^N(Y)] = \mathbb{E}\langle I^M(X), I^N(Y)\rangle_\infty = \mathbb{E}\int_0^\infty X_t Y_t \, d\langle M, N\rangle_t.
> $$
> In particular,
> $$
> \mathbb{E}\left( \int_0^\infty X_t \, dM_t \right)^2 = \mathbb{E}\int_0^\infty X_t^2 \, d\langle M \rangle_t.
> $$

> [!done]
> 

> [!question]
> Suppose $M, N \in \mathcal{M}^{c,\text{loc}}$ and $X \in \mathcal{P}^*(M) \cap \mathcal{P}^*(N)$. Show that for every pair $(\alpha, \beta)$ of real numbers we have
>
> $$
> I^{\alpha M + \beta N}(X) = \alpha I^M(X) + \beta I^N(X).
> $$

> [!question]
> Let $M \in \mathcal{M}^{c,\text{loc}}$ and choose $X \in \mathcal{P}^*$. Show that there exists a sequence of simple processes $\{X^{(n)}\}_{n=1}^\infty$ such that, for every $T > 0$,
>
> $$
> \lim_{n \to \infty} \int_0^T |X_t^{(n)} - X_t|^2 \, d\langle M \rangle_t = 0
> $$
>
> and
>
> $$
> \lim_{n \to \infty} \sup_{0 \leq t \leq T} |I_t(X^{(n)}) - I_t(X)| = 0
> $$
>
> hold a.s. $\mathbb{P}$. If $M$ is a standard, one-dimensional Brownian motion, then the preceding also hold with $X \in \mathcal{P}$.

> [!question]
> Let $M = W$ be standard Brownian motion and $X \in \mathcal{P}$. We define for $0 \leq s < t < \infty$
>
> $$
> \zeta_s^t(X) \triangleq \int_s^t X_u \, dW_u - \frac{1}{2} \int_s^t X_u^2 \, du; \quad \zeta_t(X) \triangleq \zeta_t^0(X).
> $$
>
> The process $\{\exp(\zeta_t(X)), \mathcal{F}_t; 0 \leq t < \infty\}$ is a supermartingale; it is a martingale if $X \in \mathcal{L}_0$.

> [!question]
> Let $W$ be a standard Brownian motion, $\varepsilon$ a number in $[0, 1]$, and $\Pi = \{t_0, t_1, \ldots, t_m\}$ a partition of $[0, t]$ with $0 = t_0 < t_1 < \cdots < t_m = t$. Consider the approximating sum
>
> $$
> S_\varepsilon(\Pi) \triangleq \sum_{i=0}^{m-1} [(1 - \varepsilon)W_{t_i} + \varepsilon W_{t_{i+1}}](W_{t_{i+1}} - W_{t_i})
> $$
>
> for the stochastic integral $\int_0^t W_s \, dW_s$. Show that
>
> $$
> \lim_{\|\Pi\| \to 0} S_\varepsilon(\Pi) = \frac{1}{2} W_t^2 + \left( \varepsilon - \frac{1}{2} \right) t,
> $$
>
> where the limit is in $L^2$. The right-hand side is a martingale if and only if $\varepsilon = 0$, so that $W$ is evaluated at the left-hand endpoint of each interval $[t_i, t_{i+1}]$ in the approximating sum; this corresponds to the Itô integral. With $\varepsilon = \frac{1}{2}$ we obtain the *Fisk-Stratonovich integral*, which obeys the usual rules of calculus such as $\int_0^t W_s \, dW_s = \frac{1}{2} W_t^2$; we shall have more to say about this in Problems 3.14, 3.15. Finally, $\varepsilon = 1$ leads to the *backward Itô integral* (McKean (1969), p. 35). The sensitivity of the limit to the value of $\varepsilon$ is a consequence of the unbounded variation of the Brownian path.

> [!question]
> For $M \in \mathcal{M}^{c,\text{loc}}$, $X \in \mathcal{P}^*$, and $Z$ an $\mathcal{F}_s$-measurable random variable, show that
>
> $$
> \int_s^t Z X_u \, dM_u = Z \int_s^t X_u \, dM_u, \quad s < t < \infty, \text{ a.s.}
> $$