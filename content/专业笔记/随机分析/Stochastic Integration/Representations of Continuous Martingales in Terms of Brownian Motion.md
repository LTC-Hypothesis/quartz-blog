We have known the Brownian motion is the fundamental continuous martingale. In this section, our theme is that how to construct another continuous local martingale by Brownian motion, in other words, continuous local martingale can be represented by Brownian motion. The techniques conclude **representation by stochastic integral** and **representation by time change**. 
# Continuous Local Martingales as Stochastic Integrals w.r.t. Brownian Motion
> [!def] Extension of a probability space 
> Let $X_t$ be an adapted process on probability space $(\Omega,\mathcal{F},\mathbb{P})$. We need make a Brownian motion which is independent of $X_t$. It is not rich enough to construct Brownian motion in space $(\Omega,\mathcal{F},\mathbb{P})$. Hence, we must extend the probability space to construct this. 
> 
> Let $(\hat{\Omega},\hat{\mathcal{F}},\hat{\mathbb{P}})$ be another probability space, on which we construct d-dimensional Brownian motion $\hat{B}_t=\{B_t,\hat{\mathcal{F}}_t\}$ and 
> $$
> \tilde{\Omega}=\Omega\times\hat{\Omega},\mathcal{G}=\mathcal{F}\otimes\hat{\mathcal{F}},\tilde{\mathbb{P}}=\mathbb{P}\times\hat{\mathbb{P}},\tilde{\mathcal{G}}_t=\mathcal{F}_t\otimes\hat{\mathcal{F}}_t$$
> But $\tilde{\mathcal{G}}_t$ may not satisfy usual condition. We set 
> $$
> \tilde{\mathcal{F}}_t=\bigcap_{s>t}\sigma(\tilde{\mathcal{G}}_s\cup\mathcal{N})
> $$
> where $\mathcal{N}=\{\tilde{\mathbb{P}}-\mbox{null set in }\tilde{\mathcal{G}}\}$. We also complete $\mathcal{G}$ by $\tilde{\mathcal{F}}=\sigma(\tilde{\mathcal{G}}\cup\mathcal{N})$. 
> 
> We extend $X,B$ to $\tilde{\mathcal{F}}_t$-adapted on $(\tilde{\Omega},\tilde{\mathcal{F}},\tilde{\mathbb{P}})$ by defining for $(\omega,\hat{\omega})\in\tilde{\Omega}$
> $$
> \tilde{X}_t(\omega,\hat{\omega})=X_t(\omega),\tilde{B}_t(\omega,\hat{\omega})=B_t(\hat{\omega})
> $$
> Then $\tilde{B}_t$ is the Brownian motion we desired. 

> [!thm]
> Let $M_t=(M^{(1)}_t,\cdots,M^{(d)}_t)$ is defined on $(\Omega,\mathcal{F},\mathbb{P})$ and $M^{(i)}_t\in\mathcal{M}^{c,loc},i=1,\cdots,d$. For $1\le i,j\le d$, $\langle M^{(i)},M^{(j)}\rangle_t$ are absolutely continuous. Then $\exists$ extension $(\tilde{\Omega},\tilde{\mathcal{F}},\tilde{\mathbb{P}})$ s.t. d-dimensional Brownian motion $B_t=(B^{(1)},\cdots,B^{(d)}_t),\tilde{\mathcal{F}}_t$ and matrix process $\{X^{i,k}_t\}_{1\le i,k\le d}$ are measurable, adapted with 
> $$
> \tilde{\mathbb{P}}\left[\int_{0}^{t}(X^{i,k}_s)^2{d}s<\infty\right]=1
> $$
> It holds the representation
> $$
> \begin{align}
> M^{(i)}=\sum_{k=1}^{d}\int_{0}^{t}X^{i,k}_s{d}B^{(i)}_s\Longleftrightarrow M_t=\int_{0}^{t}X_s\cdot{d}B_s
> \end{align}
> $$
> and thus
> $$
> \langle M^{(i)},M^{(j)}\rangle_t=\sum_{k=1}^{d}\int_{0}^{t}X^{i,k}_sX^{j,k}_s{d}s
> $$

**Proof**
Our method is random, time-dependent rotation of coordinates i.e. d-dimensional $\longrightarrow$ 1-dimensional. Suppose the matrix $Z=\{z^{i,j}_t\}_{1\le i,j\le d}$ where $z^{i,j}$ is defined as follows,
$$
z^{i,j}=z^{j,i}=\frac{{d}}{dt}\langle M^{(i)},M^{(j)}\rangle_t\tag{absolutely continuous}
$$
and for $\alpha\in\mathbb{R}^d,\alpha\ne 0$
$$
\alpha^\top Z\alpha=\sum_{i,j=1}^{d}\alpha_i z^{i,j}\alpha_j=\sum_{i=1}^{d}\frac{d}{dt}\langle \alpha_iM^{(i)}\rangle_t\ge 0\tag{quadratic variation}
$$
Then $Z$ is a symmetric and positive matrix. By classical theorem, there exists orthogonal matrix $Q$ s.t. $Q^\top Q=I$ and 
$$
Q^\top ZQ=\Lambda=\begin{bmatrix}
\lambda^{(1)}_t(\omega)&&&\\
&\lambda^{(2)}_t(\omega)&&\\
&&\ddots&\\
&&&\lambda^{(d)}_t(\omega)
\end{bmatrix}
$$
Suppose $Q=\{q^{k,l}_{1\le k,l\le d}\}$. Then we have the follow identities by matrix, 
$$
\begin{align}
\begin{cases}
\sum_{k=1}^{d}q^{k,i}q^{k,j}=\delta_{ij}\\
\sum_{k=1}^{d}\sum_{l=1}^{d}q^{k,i}z^{i,j}q^{j,l}=\delta_{ij}\lambda^{(i)}_t
\end{cases}
\end{align}
$$
With $i=j$, we have $(q^{k,i})^2\le 1$, then we have 
$$
\int_{0}^{t}(q^{i,k})^{2}{d}\langle M^{(k)}\rangle_s\le \langle M\rangle_t<\infty
$$
We define 
$$
N_t^{(i)}=\sum_{k=1}^{d}\int_{0}^{t}q^{i,k}_s{d}M^{(k)}_s
$$
then 
$$
\begin{align}
\langle N^{(i)},N^{(j)}\rangle_t&=\sum_{k=1}^{d}\sum_{l=1}^{d}\int_{0}^{t}q^{l,i}_sq^{k,j}_s{d}\langle M^{i},M^{(j)}\rangle_s\\
&=\sum_{k=1}^{d}\sum_{l=1}^{d}\int_{0}^{t}q^{l,i}z^{i,j}q^{j,k}{d}s\\
&=\delta_{ij}\int_{0}^{t}\lambda_s^{(i)}{d}s
\end{align}
$$
Hence, $\int_{0}^{t}\lambda_s^{(i)}{d}s=\langle N^{(i)}\rangle_t$. We obtain $N_t=(N^{(1)}_t,\cdots,N^{(d)}_t)$. Now we W.T.S. the representation of stochastic integral can use $N_t$ on extended probability space $(\tilde{\Omega},\tilde{\mathcal{F}},\tilde{\mathbb{P}})$. A d-dimensional Brownian motion $\tilde{B}_t=(\tilde{B}^{(1)}_t,\cdots,\tilde{B}^{(d)}_t)$ on $(\tilde{\Omega},\tilde{\mathcal{F}},\tilde{\mathbb{P}})$ is independent of $N_t$. We consider the continuous local martingale
$$
B^{(i)}_t=\int_{0}^{t}\mathbb{1}_{\{\lambda^{(i)}_s>0\}}\frac{1}{\sqrt{\lambda^{(i)}_s}}{d}N_s^{(i)}+\int_{0}^{t}\mathbb{1}_{\{\lambda^{(i)}_s=0\}}{d}\tilde{B}^{(i)}_s,1\le i\le d
$$
Since 
$$
\langle B^{(i)},B^{(j)}\rangle_t=\delta_{ij}t
$$
By [[The Change-of-Variable Formula#^b655c5|Martingale Characterization of Brownian Motion]], $B^{(i)}_t$ is one-dimensional Brownian motion. Moreover, 
$$
\int_{0}^{t}\sqrt{\lambda_s^{(i)}}{d}B^{(i)}_s=\int_{0}^{t}\mathbb{1}_{\{\lambda_s^{(i)}>0\}}{d}N^{(i)}_s=N^{(i)}_t,1\le i\le d
$$
We observe 
$$
\int_{0}^{t}(q^{i,k}_s)^2\lambda_s^{(k)}{d}s\le \int_{0}^{t}\lambda^{(k)}_s{d}s<\infty
$$
We take $X^{i,k}_t=q^{i,k}_t\sqrt{\lambda_t^{(k)}}$ and we represent $M_t$ by $X^{(i,k)}_t$
$$
\begin{align}
\sum_{k=1}^{d}\int_{0}^{t}X^{i,k}_s{d}B^{(k)}_s&=\sum_{k=1}^{d}\int_{0}^{t}q^{i,k}_s{d}N_s^{(k)}\\
&=\sum_{k=1}^{d}\sum_{j=1}^{d}\int_{0}^{t}q^{i,k}_sq^{k,j}_s{d}M^{(j)}_s\\
&=\sum_{j=1}^{d}\delta_{ij}\int_{0}^{t}{d}M^{(j)}_s=M^{(i)}_t
\end{align}
$$
**QED**
> [!warning]
> If $a.s.-\mathbb{P}$, the matrix $Z$ has rank $1\le rank(Z)=r\le d$. Then we can choose r-dimensional Brownian motion and it is nonnecessary to introduce the extended space $(\tilde{\Omega},\tilde{\mathcal{F}},\tilde{\mathbb{P}})$. Now we let 
> $$
> B^{(i)}_t=\int_{0}^{t}\frac{1}{\sqrt{\lambda^{(i)}_s}}{d}N^{(i)}_s,1\le i\le r;N^{(i)}_t=0,r+1\le i\le d
> $$

# Continuous Local Martingales as Time-Changed Brownian Motions
> [!thm] Time-change for martingales
> Let $M_t\in\mathcal{M}^{c,loc}$ and it satisfies $\lim_{t\to\infty}\langle M\rangle_t=\infty,a.s.-\mathbb{P}$. For each $0\le s<\infty$, the stopping time
> $$
> T(s)=\inf\{t\ge0:\langle M\rangle_t>s\}
> $$
> Then the time-chage process 
> $$
> B_s=M_{T(s)},\mathcal{G}_s=\mathcal{F}_{T(s)}
> $$
> is a standard one-dimensional Brownian motion. In particular, the filtration $\{\mathcal{G}_s\}$ satisfies the usual conditions and we have, $a.s.-\mathbb{P}$
> $$
> M_t=B_{\langle M\rangle_t}
> $$

^19597e

**Proof**
**Step1: Time-change**
Each $T(s)$ is optional, i.e. for $t\ge0$, 
$$
\{T(s)<t\}=\{\langle M\rangle_t>s\}\in\mathcal{F}_t
$$
Besides, $\langle M\rangle_t$ is stopping time of $\mathcal{G}_s$ for each $t$ i.e.  ^724075
$$
\{\langle M\rangle_t\le s\}=\{T(s)>t\}\in\mathcal{F}_{T(s)}=\mathcal{G}_s
$$
**Step2: Construct martingale**
Let $0\le s_1<s_2$, consider the martingale $\tilde{M}_t=M_{t\wedge T(s_2)}$. Note that 
$$
\langle \tilde{M}\rangle_{t}=\langle M\rangle_{t\wedge T(s_2)}\le \langle M\rangle_{T(s_2)}=s_2
$$
By [[Continuous, Square-Integrable Martingales#^e5c0a3|Exercise]] and [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], we obtain $\tilde{M}_t$ and $\tilde{M}^2-\langle \tilde{M}\rangle_t$ are u.i., For $B_s=M_{T(s)}$, we W.T.S. it is a Brownian motion. 
$$
\mathbb{E}[B_{s_2}-B_{s_1}|\mathcal{G}_{s_1}]=0
$$
$$
\mathbb{E}[(B_{s_2}-B_{s_1})^2|\mathcal{G}_{s_1}]=\mathbb{E}[\langle M\rangle_{T(s_2)}-\langle M\rangle_{T(s_1)}|\mathcal{G}_{s_1}]=0
$$
and $\langle B\rangle_s=s$. It remains to show the path of $B_s$ is continuous. 
**Step3: Continuity of path**
We W.T.S. $\forall\omega\in\Omega^{*}\subseteq\Omega$ with $\mathbb{P}(\Omega^*)=1$, it holds 
$$
\langle M\rangle_{t_1}(\omega)=\langle M\rangle_t(\omega),\mbox{ for some }0\le t_1<t\Longrightarrow M_{t_1}(\omega)=M_{t}(\omega)\tag{$*$}
$$
By [[#^05cfb3|Exercise 4.]], we can infer $B_s=M_{T(s)}$ is continuous. If $(*)$ holds for $t_1\in\mathbb{Q}_+$, then by the continuity of $M$ and $\langle M\rangle$, $(*)$ holds without any assumption. 
For $t_1\in\mathbb{Q}_+$, we define
$$
\sigma=\inf\{t\ge t_1:\langle M\rangle_t>\langle M\rangle_{t_1}\}
$$
$$
N_s=M_{(t_1+s)\wedge \sigma}-M_{t_1}\in\mathcal{M}^{c,loc}\mbox{ with }\mathcal{F}_{t_1+s}
$$
Then we have $\langle N\rangle_s=\langle M\rangle_{(t_1+s)\wedge \sigma}-\langle M\rangle_{t_1}=0$. By [[Continuous, Square-Integrable Martingales#^7ac13a|Exercise]], we have $N_s=0$ on $\Omega(t_1)\subseteq\Omega$ with $\mathbb{P}(\Omega(t_1))=1$ i.e. $\forall\omega\in\Omega(t_1)$, $(*)$ holds. Then 
$$
\Omega^*=\bigcup_{t_1\in\mathbb{Q}_+}\Omega(t_1)
$$
Hence, the proof have been done. 
**QED**
> [!proposition] Ramification of time-change for martingale
> If $X_t$ is progressively measurable and satisfies 
> $$
> \int_{0}^{\infty}X^{2}_t{d}\langle M\rangle_t<\infty
> $$
> then the process
> $$
> Y_s=X_{T(s)},\mathcal{G}_s
> $$
> is adapted and satisfies
> 1. $$
>    \int_{0}^{\infty}Y_s^2{d}s<\infty
>    $$
> 2. $$
>    \int_{0}^{t}X_s{d}M_s=\int_{0}^{\langle M\rangle_t}Y_s{d}B_s
>    $$
> 3. $$
>    \int_{0}^{T(s)}X_t{d}M_t=\int_{0}^{s}Y_t{d}B_s
>    $$


---
# Exercises
> [!question]
> Let $\{M = (M_t^{(1)},\dots,M_t^{(d)}), \mathscr{F}_t; 0 \le t < \infty\}$ be a vector of continuous local martingales on some $(\Omega, \mathscr{F}, \mathbb{P})$, and define $$ A^{(i,j)} \triangleq \langle M^{(i)}, M^{(j)} \rangle, \quad A_t(\omega) \triangleq \sum_{i=1}^d \sum_{j=1}^d \check{A}_t^{(i,j)}(\omega), $$ where $\check{A}_t^{(i,j)}$ denotes the total variation of $A^{(i,j)}$ on $[0,t]$. Let $T_s(\omega)$ be the inverse of the function $A_t(\omega) + t$, i.e., $A_{T_s(\omega)}(\omega) + T_s(\omega) = s$, $0 \le s < \infty$. 
> 1. Show that for each $s$, $T_s$ is a stopping time of $\{\mathscr{F}_t\}$. 
> 2. Define $\mathscr{G}_s \triangleq \mathscr{F}_{T_s}$; $0 \le s < \infty$. Show that if $\{\mathscr{F}_t\}$ satisfies the usual conditions, then $\{\mathscr{G}_s\}$ does also. 
> 3. Define $$ N_s^{(i)} \triangleq M_{T_s}^{(i)}, \quad 1 \le i \le d; \quad 0 \le s < \infty. $$ Show that for each $1 \le i \le d$: $N^{(i)} \in \mathscr{M}^{c,\text{loc}}$, and the cross-variation $\langle N^{(i)}, N^{(j)} \rangle_s$ is an absolutely continuous function of $s$, a.s. $\mathbb{P}$.

> [!question]
> Let $A = \{A(t); 0 \le t < \infty\}$ be a continuous, nondecreasing function with $A(0) = 0$, $S \triangleq A(\infty) \le \infty$, and define for $0 \le s < \infty$: $$ T(s) = \begin{cases} \inf\{t \ge 0; A(t) > s\}; & 0 \le s < S \\ \infty; & s \ge S. \end{cases} $$ The function $T = \{T(s); 0 \le s < \infty\}$ has the following properties:
> 4. $T$ is nondecreasing and right-continuous on $[0,S)$, with values in $[0, \infty)$. If $A(t) < S; \forall t \ge 0$, then $\lim_{s \uparrow S} T(s) = \infty$.
> 5. $A(T(s)) = s \wedge S; 0 \le s < \infty$. 
> 6. $T(A(t)) = \sup\{\tau \ge t: A(\tau) = A(t)\}; 0 \le t < \infty$. 
> 7. Suppose $\varphi: [0, \infty) \to \mathbb{R}$ is continuous and has the property $$ A(t_1) = A(t) \text{ for some } 0 \le t_1 < t \implies \varphi(t_1) = \varphi(t). $$ Then $\varphi(T(s))$ is continuous for $0 \le s < S$, and $$ \varphi(T(A(t))) = \varphi(t); \quad 0 \le t < \infty. $$
> 8. For $0 \le t, s < \infty$: $s < A(t) \Leftrightarrow T(s) < t$ and $T(s) \le t \Rightarrow s \le A(t)$.
> 9. If $G$ is a bounded, measurable, real-valued function or a nonnegative, measurable, extended real-valued function defined on $[a,b] \subset [0, \infty)$, then $$ \int_a^b G(t) dA(t) = \int_{A(a)}^{A(b)} G(T(s)) ds. $$

^05cfb3

> [!question]
> Show that if $\mathbb{P}[S \triangleq \langle M\rangle_\infty < \infty] > 0$, it is still possible to define a Brownian motion $B$ for which (4.17) holds. (Hint: The time-change $T(s)$ is now given as in Problem 4.5; assume, as you may, that the probability space has been suitably extended to support an independent Brownian motion (Remark 4.1).)

> [!question]
> We cannot expect to be able to define the stochastic integral $\int_0^1 X_s dW_s$ with respect to Brownian motion $W$ for measurable adapted processes $X$ which do not satisfy $\int_0^1 X_s^2 ds < \infty$ a.s. Indeed, show that if $$ \mathbb{P}\left[\int_0^t X_s^2 ds < \infty\right] = 1, \quad \text{for } 0 \le t < 1 \quad \text{and} \quad E \triangleq \left\{\int_0^1 X_s^2 ds = \infty\right\}, $$ then $$ \varlimsup_{t \uparrow 1} \int_0^t X_s dW_s = -\varliminf_{t \uparrow 1} \int_0^t X_s dW_s = +\infty, \quad \text{a.s. on } E. $$

> [!question] 
> Consider the semimartingale $X_t = x + M_t + C_t$ with $x \in \mathbb{R}$, $M \in \mathscr{M}^{c,\text{loc}}$, $C$ a continuous process of bounded variation, and assume that there exists a constant $\rho > 0$ such that $|C_t| + \langle M\rangle_t \le \rho t$, $\forall t \ge 0$ is valid almost surely. Show that for fixed $T > 0$ and sufficiently large $n \ge 1$, we have $$ \mathbb{P}\left[ \max_{0 \le t \le T} |X_t| \ge n \right] \le \exp\left\{ -\frac{n^2}{18\rho T} \right\}$$.