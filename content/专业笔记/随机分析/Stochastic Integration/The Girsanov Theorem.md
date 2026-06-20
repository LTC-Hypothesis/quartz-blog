# The Main Theorem and Proof
> [!def] Exponent martingale
> Let probability space $(\Omega,\mathcal{F},\mathbb{P})$ and d-dimensional Brownian motion $B_t=(B^{(1)}_t,\cdots,B^{(d)}_t)$ with $\mathbb{P}[B_0=0]=1$. $\mathcal{F}_t$ satisfies the usual condition. Let $X_t=(X^{(1)}_t,\cdots,X^{(d)}_t)$ be a adapted, measurable process satisfies
> $$
> \mathbb{P}\left[\int_{0}^{t}(X^{(i)}_s)^2{d}s<\infty\right]=1
> $$
> Recall [[The Change-of-Variable Formula#^01ab9e|the example]], we set 
> $$
> Z_t(X)\triangleq\exp\left(\sum_{i=1}^{d}\int_{0}^{t}X^{(i)}_s{d}B^{(i)}_s-\frac{1}{2}\int_{0}^{t}\|X_s\|^2{d}s\right)
> $$
> By the Ito rule, we have 
> $$
> Z_t(X)=1+\sum_{i=1}^{d}\int_{0}^{t}Z_s(X)X^{(i)}_s{d}B_s^{(i)}
> $$

> [!def] change of probability measure
> $Z_t(X)$ will be a martingale with $\mathbb{E}(Z_t(X))=1$. We define a probability measure $\tilde{\mathbb{P}}$ for $0\le T<\infty$ on $\mathcal{F}_T$ as 
> $$
> \tilde{\mathbb{P}}_T(A)\triangleq\mathbb{E}[\mathbb{1}_AZ_T(X)],A\in\mathcal{F}_T
> $$
> The property of martingale admits $\tilde{\mathbb{P}}$ satisfies the consistency condition, for $A\in\mathcal{F}_t$
> $$
> \tilde{\mathbb{P}}_T(A)=\mathbb{E}[\mathbb{1}_AZ_T(X)]=\mathbb{E}\left[\mathbb{E}(\mathbb{1}_AZ_T(X))|\mathcal{F}_t\right]=\mathbb{E}[\mathbb{1}_AZ_t(X)]=\tilde{\mathbb{P}}_t(A)
> $$

> [!thm] Girsanov
> Assume that $Z_t(X)$ is a martingale. We define $\tilde{B}_t=(\tilde{B}^{(1)}_t,\cdots,\tilde{B}^{(d)}_t)$ by 
> $$
> \tilde{B}^{(i)}_t=B^{(i)}_t-\int_{0}^{t}X^{(i)}_s{d}s,1\le i\le d
> $$
> For $0\le T<\infty$, $\{\tilde{B}_t,\mathcal{F}_t,0\le t\le T\}$ is d-dimensions Brownian motion on $(\Omega,\mathcal{F}_T,\tilde{\mathbb{P}}_T)$. 

^db25d3

Before we proceed the proof, we denote the expectation $\tilde{\mathbb{E}}_T$ w.r.t. $\tilde{\mathbb{P}}_T$. 
> [!lemma] Bayes's rule
> Fix $0\le T<\infty$ and assume $Z(X)$ is a martingale. If $0\le s\le t\le T$, $Y$ is an $\mathcal{F}_t$-measurable r.v. with $\tilde{\mathbb{E}}_T|Y|<\infty$, then it holds 
> $$
> \tilde{\mathbb{E}}_T[Y|\mathcal{F}_s]=\frac{1}{Z_s(X)}\mathbb{E}[YZ_t(X)|\mathcal{F}_s]
> $$

^4b101d

**Proof**
For $A\in\mathcal{F}_s$, we have 
$$
\begin{align}
\tilde{\mathbb{E}}_T[Y\mathbb{1}_A]&=\mathbb{E}[\mathbb{1}_AYZ_t(X)]=\mathbb{E}\left[\mathbb{E}(\mathbb{1}_AYZ_t(X)|\mathcal{F}_s)\right]\\
&=\mathbb{E}\left[\mathbb{1}_AZ_s(X)\mathbb{E}(Y\frac{Z_t(X)}{Z_s(X)}|\mathcal{F}_s)\right]\\
&=\tilde{\mathbb{E}}\left[\mathbb{1}_A\frac{1}{Z_s(X)}\mathbb{E}[YZ_t(X)]\right]
\end{align}
$$
**QED**
> [!def] Local martingale on $[0,T]$
> We denote by 
> $$
> \mathcal{M}^{c,loc}[0,T]=\{M_t\in\mathcal{M}^{c,loc}:0\le t\le T\}\mbox{ on }(\Omega,\mathcal{F}_T,\mathbb{P})
> $$
> with $\mathbb{P}[M_0=0]=1$. And we define the $\tilde{M}^{c,loc}[0,T]$ similarly with probability measure $\tilde{P}_T$. 

> [!proposition]
> Fix $0\le T<\infty$ and assume $Z(X)$ is a martingale. If $M\in\mathcal{M}^{c,loc}[0,T]$, then the process 
> $$
> \tilde{M}_t=M_t-\sum_{i=1}^{d}\int_{0}^{t}X^{(i)}_s{d}\langle M,B^{(i)}\rangle_s\in\tilde{\mathcal{M}}^{c,loc}_T
> $$
> If $N\in\mathcal{M}^{c,loc}[0,T]$ and 
> $$
> \tilde{N}_t=N_t-\sum_{i=1}^{d}\int_{0}^{t}X^{(i)}_s{d}\langle N,B^{(i)}\rangle_s
> $$
> then $\langle\tilde{M},\tilde{N}\rangle_t=\langle M,N\rangle_t$ where the cross-variations are computed under the appropriate measures.

**Proof**
We assume that all is bounded such as $M,N$, quadratic variable and $Z(X)$ e.t.c. The general case can be localized. We W.T.S. $\tilde{\mathbb{E}}_T[\tilde{M}_t|\mathcal{F}_s]=\tilde{M}_s$. By [[#^4b101d|Bayes's rule]], 
$$
\tilde{\mathbb{E}}_T[\tilde{M}_t|\mathcal{F}_s]=\frac{1}{Z_s(X)}\mathbb{E}[\tilde{M}_tZ_t(X)|\mathcal{F}_s]
$$
It suffices to show that $Z_t(X)\tilde{M}_t$ is a martingale. By [[The Change-of-Variable Formula#^0403d8|I.B.P]], we have 
$$
\begin{align}
Z_t(X)\tilde{M}_t&=\int_{0}^{t}Z_s{d}\tilde{M}_s+\int_{0}^{t}\tilde{M}_s{d}Z_s(X)+\langle Z(X),\tilde{M}\rangle_t\\
&=\int_{0}^{t}Z_s(X){d}\tilde{M}_s+\sum_{i=1}^{d}\int_{0}^{t}\tilde{M}_sZ_s(X)X^{(i)}_s{d}B^{(i)}_s
\end{align}
$$
Then $Z_t(X)\tilde{M}_t$ is a martingale. Hence, $\tilde{M}_t\in\mathcal{M}^{c,loc}[0,T]$.
Now we consider $Y_t\triangleq\tilde{M}_t\tilde{N}_t-\langle M,N\rangle_t$. We W.T.S. $Y_t$ is a martingale. By [[The Change-of-Variable Formula#^0403d8|I.B.P]], we have 
$$
\begin{align}
Y_t&=\int_{0}^{t}\tilde{M}_s{d}\tilde{N}_s+\int_{0}^{t}\tilde{N}_s{d}\tilde{M}_s+\langle \tilde{M},\tilde{N}\rangle_t-\langle M,N\rangle_t\\
&=\int_{0}^{t}\tilde{M}_s{d}\tilde{N}_s+\int_{0}^{t}\tilde{N}_s{d}\tilde{M}_s\\
&-\sum_{i=1}^{d}\left[\int_{0}^{t}\tilde{M}X^{(i)}{d}\langle N,B^{(i)}\rangle_s+\int_{0}^{t}\tilde{N}X^{(i)}{d}\langle M,B^{(i)}\rangle_s\right]
\end{align}
$$
Then 
$$
\begin{align}
Z_t(X)Y_t&=\int_{0}^{t}Z_s(X){d}Y_s+\int_0^tY_s{d}Z_s(X)+\langle Z(X),Y\rangle_t\\
&=\int_0^tZ_s(X)\tilde{M}_s{d}\tilde{N}_s+\int_0^tZ_s(X)\tilde{N}_s{d}\tilde{M}_s\\
&+\sum_{i=1}^{d}\int_{0}^{t}[\tilde{M}_s\tilde{N}_s-\langle M,N\rangle_s]Z_sX^{(i)}_s{d}B^{(i)}_s
\end{align}
$$
Then $Z_t(X)Y_t$ is a martingale. By the same technique, $Y_t$ is a martingale with $\tilde{\mathbb{P}}_T$ and thus $\langle\tilde{M},\tilde{N}\rangle_t=\langle M,N\rangle_t$. 
**QED**
**Proof of Girsanov Theorem:** 
We take $M_t=B^{(i)}_t$ and $N_t=B^{(j)}_t$, then we have 
$$
\langle\tilde{M},\tilde{N}\rangle_t=\langle M,N\rangle_t\Longrightarrow\langle \tilde{B}^{(i)},\tilde{B}^{(j)}\rangle_t=\langle B^{(i)},B^{(j)}\rangle_t=\delta_{ij}t
$$
By [[The Change-of-Variable Formula#^b655c5|martingale charateristic of Brownian motion]], $\tilde{B}_t$ is a Brownian motion. 
> [!warning]
> For another point, $M_t$ is a continuous semimartingale. 
> $$
> M_t=\tilde{M}_t+\int_0^tX^{(i)}_s{d}\langle M,B^{(i)}\rangle_s
> $$

> [!proposition] Converse
> Under the assumption of Girsanov theorem, every $\tilde{M}_t\in\tilde{\mathcal{M}}^{c,loc}[0,T]$ has the representation 
> $$
> \tilde{M}_t=M_t-\sum_{i=1}^{d}\int_{0}^{t}X^{(i)}_s{d}\langle M,B^{(i)}\rangle_s
> $$
> for some $M_t\in\mathcal{M}^{c,loc}[0,T]$.

**Proof**
By [[#^4b101d|Bates's rule]], we have 
$$
\mathbb{E}[Z_t(X)\tilde{M}_t|\mathcal{F}_s]=Z_s(X)\tilde{M}_s
$$
$Z_t\tilde{M}_t$ is a martingale under $\mathbb{P}$. For $\tilde{M}_t\in\tilde{\mathcal{M}}^{c,loc}[0,T]$, $Z_t\tilde{M}_t\in\tilde{\mathcal{M}}^{c,loc}[0,T]$. By Ito's rule, $\tilde{M}_t=\frac{Z_t(X)\tilde{M}_t}{Z_t(X)}$ is a semimartingale. Then $\tilde{M}_t$ has the decomposition
$$
\tilde{M}_t=M_t+A_t
$$
Then 
$$
\tilde{M}_t-\left(M_t-\sum_{i=1}^{d}\int_{0}^{t}X^{(i)}_s{d}\langle M,B^{(i)}\rangle_s\right)=A_t+\sum_{i=1}^{d}\int_{0}^{t}X^{(i)}_s{d}\langle M,B^{(i)}\rangle_s
$$
Note that LHS is in $\tilde{\mathcal{M}}^{c,loc}[0,T]$ and RHS is of bounded variation, by [[The Change-of-Variable Formula#^8cb28c|uniqueness of decomposition for semimartingale]], the process must be 0. 
**QED**
# The Novikov Condition
In order to use the Girsanov theorem effectively, we should find condition to infer $Z(X)$ is a martingale. 
> [!def] The stopped process 
> Since $Z_t(X)$ is a local martingale, we define the stopping time
> $$
> T_n=\inf\left\{t\ge0:\max_{1\le i\le d}\int_{0}^{t}(Z_s(X)X^{(i)}_s)^2{d}s=n\right\}
> $$
> and process $Z^{(n)}(X)\triangleq Z_{t\wedge T_n}(X)$ are martingale. 

> [!warning]
> Since $Z^{(n)}$ is a martingale, then 
> $$
> \mathbb{E}[Z_{t\wedge T_n}|\mathcal{F}_s]=Z_{s\wedge T_n}
> $$
> By Fatou's lemma, 
> $$
> \mathbb{E}[Z_t|\mathcal{F}_s]\le \varliminf_{n\to\infty}\mathbb{E}[Z_{t\wedge T_n}|\mathcal{F}_s]=Z_s
> $$
> Hence, $Z_t$ is a supermartingale. $Z_t$ [[Continuous-Time Martingales#^77be8e|becomes a martingale]] if $\mathbb{E}[Z_t]=1$. 

> [!proposition]
> Let $M_t\in\mathcal{M}^{c,loc}$ and define
> $$
> Z_t=\exp\left(M_t-\frac{1}{2}\langle M\rangle_t\right)
> $$
> If $\mathbb{E}[\exp\left(\frac{1}{2}\langle M\rangle_t\right)]<\infty$, then $\mathbb{E}Z_t=1$

**Proof**
Let $T(s)=\inf\{t\ge0:\langle M\rangle_t>s\}$, by [[Representations of Continuous Martingales in Terms of Brownian Motion#^19597e|Time-change of martingale]], $B_s$ is a Brownian motion with filtration $\mathcal{G}_s$. For $b<0$, we define the stopping time 
$$
S_b=\inf\{s\ge0:B_s-s=b\}
$$
Then we have $\mathbb{E}\exp(B_{S_b}-\frac{1}{2}S_b)=1\Longrightarrow\mathbb{E}\exp(\frac{1}{2}S_b)=e^{-b}$. Consider the exponential martingale $Y_s\triangleq\exp\left(B_s-\frac{s}{2}\right),\mathcal{G}_s$ and $N_s=Y_{s\wedge S_b},\mathcal{G}_s$. Then $N_s$ is martingale and since $\mathbb{P}[S_b<\infty]=1$, 
$$
N_\infty\triangleq\lim_{s\to\infty}N_s=Y_{S_b}=\exp(B_{S_b}-\frac{1}{2}S_b)
$$
By Fatou's lemma, for $0\le t<s$
$$
\mathbb{E}[N_{\infty}|\mathcal{G}_s]\le\varliminf_{s\to\infty}\mathbb{E}[N_s|\mathcal{G}_t]=N_t
$$
Then $N=\{N_s,\mathcal{G}_s,0\le s\le \infty\}$ is a supermartingale with last element. Note $\mathbb{E}[N_\infty]=1=\mathbb{E}[N_0]$, then $N_s$ [[Continuous-Time Martingales#^77be8e|is a martingale]]. We can use [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], for any stopping time $R$ of $\mathcal{G}_s$, 
$$
\mathbb{E}\left[\exp\left(B_{R\wedge S_b}-\frac{1}{2}(R\wedge S_b)\right)\right]=1
$$
Since $\langle M\rangle_t$ is a [[Representations of Continuous Martingales in Terms of Brownian Motion#^724075|stopping time]], for any $b<0$, 
$$
\mathbb{E}\left[\mathbb{1}_{\{S_b\le \langle M\rangle_t\}}\exp\left(b+\frac{1}{2}S_b\right)\right]+\mathbb{E}\left[\mathbb{1}_{\{\langle M\rangle_t<S_b\}}\exp\left(M_t-\frac{1}{2}\langle M\rangle_t\right)\right]=1
$$
For the first item, since $\mathbb{E}\left[\mathbb{1}_{\{S_b\le \langle M\rangle_t\}}\exp\left(b+\frac{1}{2}S_b\right)\right]\le e^{b}\mathbb{E}\left[\exp\left(\frac{1}{2}\langle M\rangle_t\right)\right]$, as $b\downarrow-\infty$, the first item $\to0$. For the second item, as $b\downarrow-\infty$, $\mathbb{E}\left[\mathbb{1}_{\{\langle M\rangle_t<S_b\}}\exp\left(M_t-\frac{1}{2}\langle M\rangle_t\right)\right]\to\mathbb{E}Z_t$. Then let $b\downarrow-\infty$, $\mathbb{E}Z_t=1$. 
**QED**
> [!proposition] Novikov condition
> Let $B_t=(B^{(1)},\cdots,B^{(d)})$ be a d-dimensional Brownian motion, and $X_=(X^{(1)},\cdots,X^{(d)}_t)$ be a measurable, adapted process satisfying
> $$
> \mathbb{P}\left[\int_{0}^{t}(X^{(i)}_s)^2{d}s<\infty\right]=1
> $$
> If 
> $$
> \mathbb{E}\left[\exp\left(\frac{1}{2}\int_{0}^{T}\|X_s\|^2\right){d}s\right]<\infty
> $$
> Then $\mathbb{E}Z_t=1$ and thus $Z_t$ is a martingale. 

^01516a

> [!proposition]
> We can replace the condition 
> $$
> \mathbb{E}\left[\exp\left(\frac{1}{2}\int_{0}^{T}\|X_s\|^2\right){d}s\right]<\infty
> $$
> with $\exists\{t_n\}\uparrow\infty$ s.t. 
> $$
> \mathbb{E}\left[\exp\left(\frac{1}{2}\int_{t_{n-1}}^{t_n}\|X_s\|^2{d}s\right)\right]<\infty,\forall n\ge1
> $$
> the conclusion still holds. 

^51fd92

**Proof**
Let $X_t(n)=(X^{(1)}_t\mathbb{1}_{[t_{n-1},t_n)},\cdots,X^{(d)}_t\mathbb{1}_{[t_{n-1},t_n)})$, then $Z(X(n))$ is a martingale and 
$$
\mathbb{E}[Z_{t_n}(X(n))|\mathcal{F}_{t_{n-1}}]=Z_{t_{n-1}}(X(n))=1
$$
and $Z_{t_n}(X)=Z_{t_{n-1}}(X)Z_{t_n}(X(n))$, then
$$
\mathbb{E}[Z_{t_n}(X)|\mathcal{F}_{t_{n-1}}]=Z_{t_{n-1}}(X)\Longrightarrow\mathbb{E}[Z_{t_n}(X)]=\mathbb{E}[Z_{t_{n-1}}(X)]=\cdots=1
$$
Since $\mathbb{E}[Z_{t}(X)]$ is nonincreasing in $t$ and $t_n\uparrow\infty$, let $n\to\infty$, we obtain the conclusion. 
**QED**
> [!def]
> Let 
> $$
> C[0,\infty)^d=\{x:[0,\infty)\to\mathbb{R}|x\mbox{ is continuous}\}
> $$
> For $0\le t<\infty$, $\mathcal{G}_t=\sigma(x(s),0\le s\le t)$ and $\mathcal{G}\triangleq\mathcal{G}_\infty$. 
> $\mu:[0,\infty)\times C[0,\infty)^d\to\mathbb{R}$ is called progressively measurable functional on $C[0,\infty)^d$ if for fixed $t\in[0,\infty)$, $\mu\mid_{[0,t]\times C[0,\infty)^d}$ is $\mathcal{B}([0,t])\otimes\mathcal{G}_t/\mathcal{B}(\mathbb{R})$-measurable. 

> [!def]
> Let $\mu=(\mu^{(1)},\cdots,\mu^{(d)})$ be a progressively measurable functionals vector on $C[0,\infty)^d$ and $W=(W^{(1)},\cdots,W^{(d)})$ is a d-dimensional Brownian motion on $(\Omega,\mathcal{F},\mathbb{P})$, we define the progressively measurable process 
> $$
> X_t^{(i)}(\omega)=\mu(t,W_t(\omega)),1\le i\le d
> $$
> w.r.t. $\{\mathcal{F}_t\}$. 

> [!proposition]
> Let $\mu=(\mu^{(1)},\cdots,\mu^{(d)})$ be a progressively measurable functionals vector on $C[0,\infty)^d$ satisfy, for $0\le T<\infty$ and some $K_T>0$ depending on $T$. There holds 
> $$
> \|\mu(t,x)\|\le K_T(1+x^*(t)),0\le t\le T\tag{$*1$}
> $$
> where $x^*(t)=\max_{0\le s\le t}\|x(s)\|$. Then with $X_t(\omega)$ defined by, $Z(X)$ is a martingale. 

^884ad1

**Proof**
For fixed $T>0$, we can find a sequence $\{t_n\}_{n=0}^{\infty}$ s.t. $0=t_0<t_1<\cdots<t_{n(T)}=T$ and $t_n\uparrow\infty$. We hope to check the [[#^51fd92|condition]]. By $(*1)$, we have 
$$
\int_{t_{n-1}}^{t_n}\|X_t(\omega)\|^2{d}t=\int_{t_{n-1}}^{t_n}\|\mu(t,W_t(\omega))\|^2{d}t\le (t_n-t_{n-1})K_T^2(1+W^*_t(\omega))
$$
where $W_t^*=\max_{0\le s\le t}\|W_s\|$. We define $Y_t\triangleq\exp\left(\frac{1}{4}(t_n-t_{n-1})K^2_T(1+\|W_t\|)^2\right)$ is a [[Continuous-Time Martingales#^26a60a|supermartingale]].  By [[Continuous-Time Martingales#^bd276e|Doob's maximal inequality]], we have 
$$
\mathbb{E}\left(\exp\left(\frac{1}{4}(t_n-t_{n-1})K^2_T(1+\|W^*_T\|)^2\right)\right)\le 4\mathbb{E}Y_T^2
$$
We take $t_n-t_{n-1}\le\frac{1}{TK^2_T}$ for $n\ge1$. Then we obtain the [[#^51fd92|condition]].  
**QED**
# Application: Brownian Motion with Drift
As the application of the Girsanov theorem, we explore an interesting example: the distribution of [[Computations Based on Passage Times#^405d7c|passage time]] for Brownian motion with drift. 
> [!def] Brownian motion with drift
> The process $\tilde{W}_t=W_t-\mu t$ where $\mu\ne 0$ is a real number is a Brownian motion under the probability measure $\mathbb{P}^{(\mu)}$ 
> $$
> \mathbb{P}^{(\mu)}(A)=\mathbb{E}(\mathbb{1}_AZ_t),A\in\mathcal{F}^W_t
> $$
> where $Z_t=\exp\left(\mu W_t-\frac{1}{2}\mu^2t\right)$. The process $W_t\triangleq\mu t+\tilde{W}_t$ is a Brownian motion with drift $\mu$ under the measure $\mathbb{P}^{(\mu)}$. 

> [!note] Distributions of the passage time under $\mathbb{P}^{(\mu)}$
> Recall [[Stopping Times#^4a9887|cap of two filtration is the min of stopping time]], $\{T_b\le t\}\in\mathcal{F}_{T_b}\cap\mathcal{F}_t=\mathcal{F}_{T_b\wedge t}$. On $\{T_b\le t\}$, $Z_{t\wedge T_b}=Z_{T_b}$. By [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], 
> $$
> \begin{align}
> \mathbb{P}^{(\mu)}(T_b\le t)&=\mathbb{E}\left[\mathbb{1}_{\{T_b\le t\}}Z_t\right]=\mathbb{E}\left[\mathbb{1}_{\{T_b\le t\}}\mathbb{E}(Z_t|\mathcal{F}^W_{t\wedge T_b})\right]\\
> &=\mathbb{E}[Z_{t\wedge T_b}\mathbb{1}_{\{T_b\le t\}}]=\mathbb{E}[Z_{T_b}\mathbb{1}_{\{T_b\le t\}}]\\
> &=\mathbb{E}\left[\mathbb{1}_{\{T_b\le t\}}\exp\left(\mu b-\frac{1}{2}\mu^2T_b\right)\right]\\
> &=\int_{0}^{t}\exp\left(\mu b-\frac{1}{2}\mu^2s\right)\mathbb{P}[T_b\in ds]\\
> &=\int_{0}^{t}\frac{|b|}{\sqrt{2\pi s^3}}\exp\left(\mu b-\frac{1}{2}\mu^2s\right)\exp\left(-\frac{b^2}{2s}\right)ds
> \end{align}
> $$
> Then we obtain $\mathbb{P}^{(\mu)}(T_b\in dt)=\frac{|b|}{\sqrt{2\pi t^3}}\exp\left(-\frac{(b-\mu t)^2}{2t}\right)$. We compute
> $$
> \begin{align}
> \mathbb{P}^{(\mu)}(T_b<\infty)&=\int_{0}^{\infty}\exp\left(\mu b-\frac{1}{2}\mu^2t\right)\mathbb{P}[T_b\in dt]\\
> &=e^{\mu b}\int_{0}^{\infty}e^{-\frac{1}{2}\mu^2t}\mathbb{P}[T_b\in dt]=e^{\mu b}\mathbb{E}e^{-\frac{1}{2}\mu^2T_b}\tag{MGF}\\
> &=e^{\mu b-|\mu b|}
> \end{align}
> $$
> $\mathbb{P}(T_b<\infty)=1\Longleftrightarrow\mu$ and $b$ have the same sign. 

> [!proposition] Wald identity
> Let $T$ be a stopping time of the filtration $\{\mathscr{F}_t^W\}$ with $\mathbb{P}[T < \infty] = 1$. A necessary and sufficient condition for the validity of the Wald identity $$ \mathbb{E}\left[\exp\left(\mu W_T - \frac{1}{2}\mu^2 T\right)\right] = 1, $$ where $\mu$ is a given real number, is that $$ \mathbb{P}^{(\mu)}[T < \infty] = 1. $$ In particular, if $b \in \mathbb{R}$ and $\mu b < 0$, then this condition holds for the stopping time $$ S_b \triangleq \inf\{t \ge 0; W_t - \mu t = b\}. $$

**Proof**
We have 
$$
\mathbb{P}^{(\mu)}[T<\infty]=1\Longrightarrow\mathbb{E}[\mathbb{1}_{\{T<\infty\}}Z_T]=1,\{T<\infty\}\in\mathcal{F}_T^W
$$
Since $\mathbb{P}[T<\infty]=1$, $\mathbb{1}_{\{T<\infty\}}=1,a.s.-\mathbb{P}$ and thus 
$$
\mathbb{E}[\mathbb{1}_{\{T<\infty\}}Z_T]=\mathbb{E}[Z_T]=\mathbb{E}\left[\exp\left(\mu W_T-\frac{1}{2}\mu^2T\right)\right]
$$
**QED**
> [!proposition] Convolution
> Denote by $$ h(t; b, \mu) \triangleq \frac{|b|}{\sqrt{2\pi t^3}} \exp\left[-\frac{(b - \mu t)^2}{2t}\right]; \quad t > 0,\ b \neq 0,\ \mu \in \mathbb{R}, $$ the (possibly defective) density on the right-hand side of (5.12). Use Theorem 2.6.16 to show that $$ h(\ \cdot\ ; b_1 + b_2, \mu) = h(\ \cdot\ ; b_1, \mu) * h(\ \cdot\ ; b_2, \mu); \quad b_1 b_2 > 0,\ \mu \in \mathbb{R}, $$ where $*$ denotes convolution.

**Proof**
We write $h(t;b,\mu)=e^{\mu b-\frac{1}{2}\mu^2t}f_{T_b}(t)$ where $f_{T_b}$ is the density of $T_b$. For case of $\mu=0$, $h(t;b,0)=f_{T_b}(t)$, **we claim: $h(\cdot;b_1,0)*h(\cdot;b_2,0)=f_{T_{b_1}}*f_{T_{b_2}}(t)=f_{T_{b_1+b_2}}(t)$.** If the claim holds, then we have 
$$
\begin{align}
h(\cdot;b_1,\mu)*h(\cdot;b_2,\mu)&=\int_{0}^{t}e^{\mu s-\frac{1}{2}\mu^2s}e^{\mu(t-s)-\frac{1}{2}\mu(t-s)}f_{T_{b_1}}(s)f_{T_{b_2}}(t-s){d}s\\
&=e^{\mu t-\frac{1}{2}\mu^2t}\int_{0}^{t}f_{T_{b_1}}(s)f_{T_{b_2}}(t-s){d}s\\
&=e^{\mu t-\frac{1}{2}\mu^2t}f_{T_{b_1}}*f_{T_{b_2}}(t)=e^{\mu t-\frac{1}{2}\mu^2t}f_{T_{b_1+b_2}}(t)=h(\cdot;b_1+b_2,\mu)
\end{align}
$$
Now we use [[The Strong Markov Property and the  Reflection Principle#^322053|the strong Markov property of Brownian motion]], take $S=T_{b_1}$, and thus
$$
W_t=B_{T_{b_1}+t}-B_{T_{b_1}}
$$
is a Brownian motion. We define $T'=\inf\{t\ge0:W_t=b_2\}$. Since $T'$ is independent of $T_{b_{1}}$ and $W_t$ is a standard Brownian motion, we obtain $T'\xlongequal{d}T_{b_2}$. Then $T_{b_1+b_2}=T_{b_1}+T'\xlongequal{d}T_{b_1}+T_{b_2}$. Since the density of summation for r.v.s is the convolution of density for these r.v.s, i.e. 
$$
f_{T_{b_1}+T_{b_2}}(t)=f_{T_{b_1}}*f_{t_{b_2}}(t)
$$
Hence, it proves the proposition. 
**QED**
> [!proposition]
> With $\mu > 0$ and $W_* \triangleq \inf_{t>0} W_t$, under $\mathbb{P}^{(\mu)}$ the random variable $-W_*$ is exponentially distributed with parameter $2\mu$, i.e., $$ \mathbb{P}^{(\mu)}[-W_* \in db] = 2\mu e^{-2\mu b} db, \quad b > 0. $$

**Proof**
Note that $W_t=\mu t+\tilde{W}_t\xrightarrow{a.s.}0$ as $t\to\infty$, then $\{-W_*\ge b\}=\{W_*\le -b\}=\{T_{-b}<\infty\}$. Then we have 
$$
\mathbb{P}^{(\mu)}[-W_*\ge b]=\mathbb{P}^{(\mu)}[T_{-b}<\infty]=\exp\left(-\mu b-|\mu(-b)|\right)=e^{-2\mu b}
$$
Hence, $\mathbb{P}^{(\mu)}[-W_*\in b]=2\mu e^{-2\mu b}{d}b$. 
**QED**
> [!proposition] MGF under $\mathbb{P}^{(\mu)}$
> Show that $$ \mathbb{E}^{(\mu)} e^{-\alpha T_b} = \exp\left(\mu b - |b|\sqrt{\mu^2 + 2\alpha}\right), \quad \alpha > 0. $$

**Proof**
We have 
$$
\begin{align}
\mathbb{E}^{(\mu)}e^{-\alpha T_b}&=\int_{0}^{\infty}e^{-\alpha t}\mathbb{P}^{(\mu)}[T_b\in dt]\\
&=\int_{0}^{\infty}e^{-\alpha t}e^{\mu b-\frac{1}{2}\mu^2t}\mathbb{P}[T_b\in dt]\\
&=e^{\mu b}\mathbb{E}e^{-(\frac{1}{2}\mu^2+\alpha)T_b}=\exp\left(\mu b-|b|\sqrt{\mu^2+2\alpha}\right)\tag{MGF}
\end{align}
$$
**QED**
> [!proposition]
> Consider, for $\nu > 0$ and $c > 1$, the stopping time of $\{\mathscr{F}_t^W\}$: 
> $$ R_c = \inf\left\{t \ge 0: \exp\left(\nu W_t - \frac{1}{2}\nu^2 t\right) = c\right\}. 
> $$ 
> Show that 
> $$ \mathbb{P}[R_c < \infty] = \frac{1}{c}, \quad \mathbb{E}^{(\nu)} R_c = \frac{2\log c}{\nu^2}.
> $$

**Proof**
Consider the exponential martingale $Z_t=\exp\left(\nu W_t - \frac{1}{2}\nu^2 t\right)$, by [[Continuous-Time Martingales#^1b13f7|optional sampling thoerem]], we have 
$$
\mathbb{E}[Z_{t\wedge R_c}]=\mathbb{E}[Z_0]=1
$$
and thus 
$$
\mathbb{E}[Z_{R_c}\mathbb{1}_{\{R_c\le t\}}]+\mathbb{E}[Z_{t}\mathbb{1}_{\{R_c>t\}}]=1
$$
Let $t\to\infty$, the second item$\to0$, then 
$$
\mathbb{E}[Z_{R_c}\mathbb{1}_{\{R_c<\infty\}}]=1\Longrightarrow\mathbb{P}[R_c<\infty]=\frac{1}{c}
$$
Note that 
$$
\begin{align}
R_c &= \inf\left\{t \ge 0: \exp\left(\nu W_t - \frac{1}{2}\nu^2 t\right) = c\right\}\\
&=\inf\left\{t\ge0:\nu W_t-\frac{1}{2}\nu^2t=\log{c}\right\}\\
&=\inf\left\{t\ge0:W_t-\frac{1}{2}\nu t=\frac{\log{c}}{\nu}\right\}=T_{\frac{\log{c}}{\nu}}
\end{align}
$$
Then 
$$
\mathbb{E}^{(\nu)}R_c=\mathbb{E}^{(\nu)}T_{\frac{\log{c}}{\nu}}
$$
Note that we have 
$$
\begin{align}
\mathbb{E}^{(\mu)}T_b&=-\frac{d}{d\alpha}\mathbb{E}^{(\mu)}e^{-\alpha T_b}\mid_{\alpha=0}\\
&=\exp\left(\mu b-|\mu b|\right)\frac{|b|}{|\mu|}
\end{align}
$$
where $\mu=\frac{1}{2}\nu,b=\frac{\log{c}}{\nu}$, hence 
$$
\mathbb{E}^{(\nu)}[R_c]=\frac{2\log{c}}{\nu^2}
$$
**QED**

---
# Exercises
> [!question]
> Assume the hypotheses of Theorem 5.1 and suppose $Y = \{Y_t, \mathscr{F}_t; 0 \le t < \infty\}$ is a measurable adapted process satisfying $\mathbb{P}\left[\int_0^T Y_t^2 dt < \infty\right] = 1$; $0 \le T < \infty$. Under $\mathbb{P}$ we may define the Itô integral $\int_0^t Y_s dW_s^{(i)}$, whereas under $\widetilde{\mathbb{P}}_T$ we may define the Itô integral $\int_0^t Y_s d\widetilde{W}_s^{(i)}$, $0 \le t \le T$. Show that for $1 \le i \le d$, we have 
> $$\int_0^t Y_s d\widetilde{W}_s^{(i)} = \int_0^t Y_s dW_s^{(i)} - \int_0^t Y_s X_s^{(i)} ds; \quad 0 \le t \le T, \quad \text{a.s. } \mathbb{P} \text{ and } \widetilde{\mathbb{P}}_T$$

^6b9f7f

> [!question]
> With $W = \{W_t, \mathscr{F}_t; 0 \le t \le 1\}$ a Brownian motion, we define $$ T = \inf\{0 \le t \le 1; t + W_t^2 = 1\}, $$ $$ X_t = \begin{cases} -\dfrac{2}{(1-t)^2} W_t \mathbf{1}_{\{t \le T\}}; & 0 \le t < 1, \\[6pt] 0; & t = 1. \end{cases} $$
> 1. Prove that $\mathbb{P}[T < 1] = 1$, and therefore $\int_0^1 X_t^2 dt < \infty$ a.s. 
> 2. Apply Itô’s rule to the process $\{(W_t/(1-t))^2; 0 \le t < 1\}$ to conclude that $$ \int_0^1 X_t dW_t - \frac{1}{2} \int_0^1 X_t^2 dt = -1 - 2 \int_0^T \left[ \frac{1}{(1-t)^4} - \frac{1}{(1-t)^3} \right] W_t^2 dt \le -1. $$
> 3. The exponential supermartingale $\{Z_t(X), \mathscr{F}_t; 0 \le t \le 1\}$ is not a martingale; however, for each $n \ge 1$ and $\sigma_n = 1 - (1/\sqrt{n})$, $\{Z_{t \wedge \sigma_n}(X), \mathscr{F}_t; 0 \le t \le 1\}$ is a martingale.

> [!question]
> Let $W = \{W_t, \mathscr{F}_t; 0 \le t < \infty\}$ be a Brownian motion on $(\Omega, \mathscr{F}, \mathbb{P})$ with $\mathbb{P}[W_0 = 0] = 1$, and assume that $\{\mathscr{F}_t\}$ is the augmentation under $\mathbb{P}$ of the Brownian filtration $\{\mathscr{F}_t^W\}$. Suppose that, for each $0 \le T < \infty$, there is a probability measure $\widetilde{\mathbb{P}}_T$ on $\mathscr{F}_T$ which is mutually absolutely continuous with respect to $\mathbb{P}$, and that the family of probability measures $\{\widetilde{\mathbb{P}}_T; 0 \le T < \infty\}$ satisfies the consistency condition (5.5). Show that there exists a measurable, adapted process $X = \{X_t, \mathscr{F}_t; 0 \le t < \infty\}$ satisfying (5.1), such that $Z(X)$ defined by (5.2) is a martingale and (5.4) holds for $0 \le T < \infty$. (Hint: Apply Problem 4.16 to the Radon-Nikodým derivative process $d\widetilde{\mathbb{P}}_t/d\mathbb{P}$.)

> [!question]
> Suppose that $\{L_t, \mathscr{F}_t; 0 \le t < \infty\} \in \mathscr{M}^{c,\text{loc}}$ is such that $Z_t \triangleq \exp\left[L_t - \frac{1}{2}\langle L\rangle_t\right]$ is a martingale under $\mathbb{P}$, and define the new probability measure $\widetilde{\mathbb{P}}_T(A) \triangleq \mathbb{E}(\mathbf{1}_A Z_T); A \in \mathscr{F}_T$. Establish the following generalization of Proposition 5.4 and of the Girsanov theorem: if $M \in \mathscr{M}^{c,\text{loc}}$, then $$ \widetilde{M}_t \triangleq M_t - \langle L, M\rangle_t = M_t - \int_0^t \frac{1}{Z_s} d\langle Z, M\rangle_s, \quad \mathscr{F}_t; \ 0 \le t \le T $$ is in $\widetilde{\mathscr{M}}^{c,\text{loc}}$. (Hint: Imitate the proof of Proposition 5.4.)