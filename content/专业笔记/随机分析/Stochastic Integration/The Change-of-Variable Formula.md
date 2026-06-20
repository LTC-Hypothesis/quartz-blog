# Introduction
> [!def] Continuous semimartingale
> Let $X_t$ is a continuous semimartingale if $X_t$ is a adapted process, and satisfies the follow decomposition,
> $$
> X_t=X_0+M_t+A_t
> $$
> where $M_t\in\mathcal{M}^{c,loc}$ and $A_t$ is bounded variation. 
> $A_t=A^+_t-A^-_t$ where $A^+_t$ is the positive variation and $A^-_t$ is the negative variation i.e.
> $$
> A^+_t=\sup_{\Pi_n}\sum_{(+)}A_{t_j}-A_{j-1},\text{ the summation is for }A_{t_j}\ge A_{t_{j-1}}
> $$ 
> $$
> A^{-}_t=\sup_{\Pi_n}\sum_{(-)}A_{t_j}-A_{j-1},\text{ the summation is for }A_{t_j}\le A_{t_{j-1}}
> $$
> Besides, the total variation is $\check{A}_t=A^+_t+A^-_t$.

> [!proposition] Uniqueness of decomposition for semimartingale
> Suppose there are two decomposition for a continuous semimartingale i.e. 
> $$
> X_t=X_0+M_t+A_t=X_0+\tilde{M}_t+\tilde{A}_t
> $$
> Then $M_t=\tilde{M}_t$ and $A_t=\tilde{A}_t,a.s.-\mathbb{P}$ for $t\in[0,\infty)$.

^8cb28c

**Proof**
**QED**
# The Itô Rule
> [!thm] The Itô rule
> Let $f:\mathbb{R}\to\mathbb{R}$ and $f\in C^2(\mathbb{R})$. Suppose $X_t$ is a continuous semimartingale and satisfies the decomposition $X_t=X_0+M_t+A_t$. Then it holds
> $$
> f(X_t)=f(X_0)+\int_{0}^{t}f'(X_s){d}M_s+\int_{0}^{t}f'(X_s){d}A_s+\frac{1}{2}\int_{0}^{t}f''(X_s){d}\langle M\rangle_s
> $$ 
> or the differential form
> $$
> \begin{align}
> df(X_t)&=f'(X_t){d}M_t+f'(X_t){d}A_t+\frac{1}{2}f''(X_t){d}\langle M\rangle_t\\
> &=f'(X_t){d}X_t+\frac{1}{2}f''(X_t){d}\langle M\rangle_t
> \end{align}
> $$

^e6e674

> [!warning]
> If the process is Brownian motion $B_t$, note that $\langle B\rangle_t=t$, then 
> $$
> df(B_t)=f'(B_t){d}B_t+\frac{1}{2}f''(B_t){d}t
> $$

> [!thm] The high dimensional Itô rule
> Let $f:[0,\infty)\times \mathbb{R}^d\to\mathbb{R}$ and $f\in C^1[0,\infty)\cap C^2(\mathbb{R}^d)$. Suppose $\textbf{M}_t=(M_t^{(1)},\cdots,M_t^{(d)})$ and $\textbf{A}_t=(A_t^{(1)},\cdots,A_t^{(d)})$, $\textbf{X}_t$ is a continuous semimartingale vector and satisfies the decomposition $\textbf{X}_t=\textbf{X}_0+\textbf{M}_t+\textbf{A}_t$. Then it holds 
> $$
> \begin{align}
> f(\textbf{X}_t)=&f(\textbf{X}_0)+\int_{0}^{t}\frac{\partial f(s,\textbf{X}_s)}{\partial s}{d}s+\sum_{i=1}^{d}\int_{0}^{t}\frac{\partial f(s,\textbf{X}_s)}{\partial x_i}{d}M_s^{(i)}\\
> &+\sum_{i=1}^{d}\int_{0}^{t}\frac{\partial f(s,\textbf{X}_s)}{\partial x_i}{d}A_s^{(i)}+\frac{1}{2}\sum_{i=1}^{d}\sum_{j=1}^{d}\int_{0}^{t}\frac{\partial^2 f}{\partial x_ix_j}{d}\langle M^{(i)},M^{(j)}\rangle_s
> \end{align}
> $$
> For convenience, we write it as form of vector calculus,
> $$
> \begin{align}
> f(\textbf{X}_t)=&f(\textbf{X}_0)+\int_{0}^{t}\frac{\partial f(s,\textbf{X}_s)}{\partial s}{d}s+\int_{0}^{t}\nabla_xf(s,\textbf{X}_s)\cdot{d}\textbf{M}_s\\
> &+\int_{0}^{t}\nabla_xf(s,\textbf{X}_s)\cdot{d}\textbf{A}_s+\frac{1}{2}\int_{0}^{t}\nabla^2_xf(s,\textbf{X}_s):{d}\langle \symbf{M},\symbf{M}\rangle_s
> \end{align}
> $$
> where $A:B$ is Frobenius inner product for matrix i.e. $A:B=\sum_{i=1}^{d}\sum_{j=1}^{d}A_{ij}B_{ij}$ and $\langle M,M\rangle_t$ is a cross variation matrix i.e. 
> $$
> \langle \symbf{M},\symbf{M}\rangle_t=\begin{bmatrix}
> \langle M^{(1)}\rangle_t &\langle M^{(1)},M^{(2)}\rangle_t &\cdots &\langle M^{(1)},M^{(d)}\rangle_t\\
> \langle M^{(2)},M^{(1)}\rangle_t &\langle M^{(2)}\rangle_t &\cdots &\langle M^{(2)},M^{(d)}\rangle_t\\
> \vdots &\vdots & &\vdots\\
> \langle M^{(d)},M^{(1)}\rangle_t &\langle M^{(d)},M^{(2)}\rangle_t &\cdots &\langle M^{(d)}\rangle_t
> \end{bmatrix}_{d\times d}
> $$

^57e183

**Proof**
**QED**
> [!example]
> Use the Itô rule to compute the stochastic differential equation for $B_t^2$.

**Solution**
It is very convenient to compute by differential form of the Itô rule. Note that $f(x)=x^2$, and 
$$
\begin{align}
dB_t^2=df(B_t)&=f'(B_t){d}B_t+\frac{1}{2}f''(B_t){d}t\\
&=2B_t{d}B_t+dt
\end{align}
$$
Hence, we obtain $$B^2_t=\int_{0}^{t}2B_s{d}B_s+t$$
**QED**
> [!example]
> Suppose $\zeta_t=N_t+A_t$ where 
> $$
> N_t=\int_{0}^{t}X_s{d}B_s,A_t=-\frac{1}{2}\int_{0}^{t}X_s^2{d}s
> $$
> Consider $Z_t=\exp(\zeta_t)$. Show that $Z_t$ satisfies 
> $$
> Z_t=1+\int_{0}^{t}Z_sX_s{d}B_s
> $$

^01ab9e

**Solution**
Let $f(x)=e^x$, note that $d\zeta_t=X_t{d}B_t-\frac{1}{2}X_t^2{d}t$, by the Itô rule, 
$$
\begin{align}
dZ_t=df(\zeta_t)&=f'(\zeta_t){d}\zeta_t+\frac{1}{2}f''(\zeta_t){d}\langle N\rangle_t\\
&=Z_tX_t{d}B_t-\frac{1}{2}Z_tX_t^2{d}t+\frac{1}{2}Z_tX_t^2{d}t=Z_tX_t{d}B_t
\end{align}
$$
Hence, we have 
$$
Z_t=1+\int_{0}^{t}Z_sX_s{d}B_s
$$
**QED**
> [!def] Multiplication table 
> We introduce the follow multiplication table in order to formalise the computation. With two independent Brownian motion $W_t,\tilde{W}_t$, 

| |  $dt$  |  $dW_t$  | $d\tilde{W}_t$ |
|-|-|-|-|
|$dt$| 0 | 0 | 0 |
|$dW_t$| 0 |  $dt$ | 0 |
|$d\tilde{W}_t$ | 0 | 0 | $dt$ |
Then we can write the Itô rule as formalism.
$$
df(X_t)=f'(X_t){d}X_t+\frac{1}{2}f''(X_t)({d}X_t)^2
$$

> [!proposition] Integration by parts formula(I.B.P)
> Suppose two continuous semimartingales $X_t,Y_t$ and their decomposition 
> $$
> X_t=X_0+M_t+A_t,Y_t=Y_0+N_t+C_t
> $$
> where $M,N\in\mathcal{M}^{c,loc}$ and $A_t,C_t$ are adapted, continuous and have bounded variation with $A_0=C_0=0$. Then it holds 
> $$
> \int_{0}^{t}X_s{d}Y_s=X_tY_t-X_0Y_0-\int_{0}^{t}Y_s{d}X_s-\langle M,N\rangle_t
> $$

^0403d8

**Proof**
By [[#^57e183|the high dimensional Itô rule]], let $f(x,y)=xy$ and $\textbf{Z}_t=(X_t,Y_t),\symbf{G}_t=(M_t,N_t),\symbf{V}_t=(A_t,C_t)$, then we have 
$$
\begin{align}
d(X_tY_t)=df(X_t,Y_t)&=f_x{d}M_t+f_y{d}N_t+f_x{d}A_t+f_y{d}C_t+\langle M,N\rangle_t\\
&=X_t{d}Y_t+Y_t{d}X_t+\langle M,N\rangle_t
\end{align}
$$
Integrating from $0$ to $t$, we obtain
$$
\int_{0}^{t}X_s{d}Y_s=X_tY_t-X_0Y_0-\int_{0}^{t}Y_s{d}X_s-\langle M,N\rangle_t
$$
**QED**
> [!warning]
> Note that we can get **the product rule of stochastic integral** from (I.B.P)
> $$
> d(X_tY_t)=X_t{d}Y_t+Y_t{d}X_t+\langle M,N\rangle_t
> $$
> We can see the difference with classical product rule is the cross variation item $\langle M,N\rangle_t$. 

To avoid the appearance of $\langle M,N\rangle_t$, we will introduce the **Fisk-Stratonovich integral**, which has the follow advantages. First, we can comprehend the theory of diffusion on differential manifold. Second, it performs more **robust** under the perturbation of the integrating semimartingale. 
> [!def] Fisk-Stratonovich integral(F-S integral)
> Let $X_t,Y_t$ are continuous semimartingale with corresponding decomposition. The Fisk-Stratonovich integral of $Y_t$ w.r.t. $X_t$ is defined 
> $$
> \int_{0}^{t}Y_t\circ{d}X_t=\int_{0}^{t}Y_s{d}M_s+\int_{0}^{t}Y_s{d}A_s+\frac{1}{2}\langle M,N\rangle_t
> $$
> Note that the cross variation with finite value and finite variation process is 0 i.e. $\langle Y_0,M\rangle_t=\langle C_t,M\rangle_t=0$. Then the definition can be also write as 
> $$
> \int_{0}^{t}Y_t\circ{d}X_t=\int_{0}^{t}Y_s{d}M_s+\int_{0}^{t}Y_s{d}A_s+\frac{1}{2}\langle Y,M\rangle_t
> $$

One advantage of F-S integral is that its chain rule cater our expression of classical chain rule,but it is needed higher regularity. 
> [!proposition] The chain rule of F-S integral
> Let $\symbf{X}_t=(X_t^{(1)},\cdots,X_t^{(d)})$ be a vector of continuous semimartingale with the decomposition $X^{(i)}=X^{(i)}_0+M_t^{(i)}+A^{(i)}_t$. Let $f:\mathbb{R}^d\to\mathbb{R},f\in C^3(\mathbb{R}^d)$, then 
> $$
> f(\symbf{X}_t)=f(\symbf{X}_0)+\sum_{i=1}^{d}\int_{0}^{t}\frac{\partial f(\symbf{X}_s)}{\partial x_i}\circ{d}X^{(i)}_s
> $$

^4c7cfc

**Proof**
Since $f(x)\in C^3(\mathbb{R}^d)$, we can use the Itô rule. Then we have 
$$
f(\symbf{X}_t)=f(\symbf{X}_0)+\sum_{i=1}^{d}\int_{0}^{t}\frac{\partial f(\symbf{X}_s)}{\partial x_i}{d}X^{(i)}_s+\frac{1}{2}\sum_{i=1}^{d}\sum_{j=1}^{d}\int_{0}^{t}\frac{\partial^2f(\symbf{X}_s) }{\partial x_i\partial x_j}{d}\langle M^{(i)},M^{(j)}\rangle_t
$$
and for F-S integral
$$
\begin{align}
\sum_{i=1}^{d}\int_{0}^{t}\frac{\partial f(\symbf{X}_s)}{\partial x_i}\circ{d}X_s^{(i)}=\sum_{i=1}^{d}\left[\int_{0}^{t}\frac{\partial f(\symbf{X}_s)}{\partial x_i}{d}X_s^{(i)}+\frac{1}{2}\langle \frac{\partial f(\symbf{X}_s)}{\partial x_i},M\rangle_t\right]
\end{align}
$$
Since $f\in C^3(\mathbb{R}^d)$, $\frac{\partial f}{\partial x_i}\in C^2(\mathbb{R}^d)$ and thus we can use the Itô rule for $\frac{\partial f(\symbf{X}_t)}{\partial x_i}$ again
$$
\begin{align}
\frac{\partial f(\symbf{X}_t)}{\partial x_i}=&\frac{\partial f(\symbf{X}_0)}{\partial x_i}\tag{finite value}\\
&+\sum_{j=1}^{d}\int_{0}^{t}\frac{\partial^2 f(\symbf{X}_t)}{\partial x_i\partial x_j}{d}M_s^{(i)}\tag{local martingale}\\
&+\sum_{j=1}^{d}\int_{0}^{t}\frac{\partial^2 f(\symbf{X}_t)}{\partial x_i\partial x_j}{d}A_s^{(i)}\tag{finite variation}\\
&+\frac{1}{2}\sum_{k=1}^{d}\sum_{j=1}^{d}\int_{0}^{t}\frac{\partial^3 f(\symbf{X}_t)}{\partial x_i\partial x_j\partial x_k}{d}\langle M^{(j)},M^{(k)}\rangle_s\tag{finite variation}
\end{align}
$$
Then by [[Construction of the Stochastic Integral#^09e22b|proposition]], we have 
$$
\begin{align}
\left\langle\frac{\partial f(\symbf{X}_t)}{\partial x_i},M\right\rangle_t=\sum_{j=1}^{d}\int_{0}^{t}\frac{\partial^2 f(\symbf{X}_t)}{\partial x_i\partial x_j}{d}\langle M^{(i)},M^{(j)}\rangle_s
\end{align}
$$
Above all, we obtain
$$
\begin{align}
&f(\symbf{X}_0)+\sum_{i=1}^{d}\int_{0}^{t}\frac{\partial f(\symbf{X}_s)}{\partial x_i}\circ{d}X_s^{(i)}\\
=&f(\symbf{X}_0)+\sum_{i=1}^{d}\left[\int_{0}^{t}\frac{\partial f(\symbf{X}_s)}{\partial x_i}{d}X_s^{(i)}+\frac{1}{2}\langle \frac{\partial f(\symbf{X}_s)}{\partial x_i},M\rangle_t\right]\\
=&f(\symbf{X}_0)+\sum_{i=1}^{d}\int_{0}^{t}\frac{\partial f(\symbf{X}_s)}{\partial x_i}{d}X^{(i)}_s+\frac{1}{2}\sum_{i=1}^{d}\sum_{j=1}^{d}\int_{0}^{t}\frac{\partial^2f(\symbf{X}_s) }{\partial x_i\partial x_j}{d}\langle M^{(i)},M^{(j)}\rangle_t\\
=&f(\symbf{X}_t)
\end{align}
$$
**QED**
Another view to comprehend F-S integral is that the approximated summation take points of middle. 
> [!proposition]
> Let $X$ and $Y$ be continuous semimartingales and $\Pi = \{t_0, t_1, \dots, t_m\}$ a partition of $[0,t]$ with $0 = t_0 < t_1 < \cdots < t_m = t$. Then the sum $$ \sum_{i=0}^{m-1} \left( \frac{1}{2} Y_{t_{i+1}} + \frac{1}{2} Y_{t_i} \right) (X_{t_{i+1}} - X_{t_i}) $$ converges in probability to $\int_0^t Y_s \circ dX_s$ as $\|\Pi\| \to 0$.

**Proof**
Note that 
$$
\begin{align}
\sum_{i=0}^{m-1} \left( \frac{1}{2} Y_{t_{i+1}} + \frac{1}{2} Y_{t_i} \right) (X_{t_{i+1}} - X_{t_i})=\sum_{i=0}^{m-1}Y_{t_i}(X_{t_{i+1}}-X_{t_i})+\frac{1}{2}\sum_{i=0}^{m-1}(Y_{t_{i+1}}-Y_{t_i})(X_{t_{i+1}}-X_{t_i})
\end{align}
$$
and we have known as $\|\Pi\|\to0$
$$
\sum_{i=0}^{m-1}Y_{t_i}(X_{t_{i+1}}-X_{t_i})\to\int_{0}^{t}Y_t{d}X_t,\frac{1}{2}\sum_{i=0}^{m-1}(Y_{t_{i+1}}-Y_{t_i})(X_{t_{i+1}}-X_{t_i})\to\frac{1}{2}\langle Y,X\rangle_t
$$
Hence, as $\|\Pi\|\to0$
$$
\sum_{i=0}^{m-1} \left( \frac{1}{2} Y_{t_{i+1}} + \frac{1}{2} Y_{t_i} \right) (X_{t_{i+1}} - X_{t_i})\to\int_0^t Y_s \circ dX_s
$$
**QED**
# Martingale Characterization of Brownian Motion
We recall the martingale property of Brownian motion in [[The Markov Property#^6066df|the Markov property]]. We have known Brownian motion has the property. By claim of Paul levy, conversely, the process with such property must be Brownian motion. 
> [!thm] Levy
> Let $\symbf{X}_t=(X_t^{(1)},\cdots,X_t^{(d)})$ be a continuous, adapted process in $\mathbb{R}^d$. We define the process 
> $$
> M^{(k)}_t=X^{(k)}_t-X^{(k)}_0
> $$
> is a continuous local martingale and it satisfies $\langle M^{(k)},M^{(j)}\rangle_t=\delta_{kj}t$ for $1\le k,j\le d$. Then $\symbf{X}_t$ is d-dimensional Brownian motion. 

^b655c5

**Proof**
In order to show that one process is Brownian motion, it suffices to check the characterization of Brownian motion i.e. 
1. $\symbf{X}_t-\symbf{X}_s\bot\mathcal{F}_s$
2. $\symbf{X}_t-\symbf{X}_s\sim N_d(\symbf{0},(t-s)I_{d\times d})$

But recall the proof of strong Markov property, we can use the useful [[The Strong Markov Property and the  Reflection Principle#^4401cd|lemma]], it suffices to check the conditional charateristic function
$$
\mathbb{E}\left[e^{i(u,\symbf{X}_t-\symbf{X}_s)}|\mathcal{F}_s\right]=e^{{-\frac{1}{2}}\|u\|^2(t-s)},\forall u\in\mathbb{R}^d
$$
Let $f(x)=e^{i(u,x)}$, by the Itô rule, 
$$
\begin{align}
e^{i(u,\symbf{X}_t)}&=e^{i(u,\symbf{X}_s)}+\sum_{j=1}^{d}\int_{s}^{t}iu_je^{i(u,\symbf{X}_v)}{d}M^{(j)}_v-\frac{1}{2}\sum_{k=1}^{d}\sum_{j=1}^{d}\int_{s}^{t}u_ku_je^{i(u,\symbf{X}_v)}{d}\langle M^{(k)},M^{(j)}\rangle_v\\
&=e^{i(u,\symbf{X}_s)}+\sum_{j=1}^{d}\int_{s}^{t}iu_je^{i(u,\symbf{X}_v)}{d}M^{(j)}_v-\frac{1}{2}\sum_{j=1}^{d}\int_{s}^{t}u_j^2e^{i(u,\symbf{X}_v)}{d}v
\end{align}
$$
Note that the local martingale $\int_{s}^{t}iu_je^{i(u,\symbf{X}_v)}{d}M^{(j)}_v\in\mathcal{M}^{c,loc}\cap\mathcal{M}^c_2$. Then we have 
$$
\mathbb{E}\left[\int_{s}^{t}iu_je^{i(u,\symbf{X}_v)}{d}M^{(j)}_v|\mathcal{F}_s\right]=0
$$
For any $A\in\mathcal{F}_s$, we have
$$
\begin{align}
\mathbb{E}\left[e^{i(u,\symbf{X}_t-\symbf{X}_s)}\mathbb{1}_{A}\right]&=\mathbb{E}\left[e^{i(u,\symbf{X}_t)}e^{-i(u,\symbf{X}_s)}\mathbb{1}_{A}\right]\\
&=\mathbb{E}\left[\mathbb{1}_A+\sum_{j=1}^{d}\int_{s}^{t}iu_je^{i(u,\symbf{X}_v-\symbf{X}_s)}{d}M^{(j)}_v\mathbb{1}_A-\frac{1}{2}\sum_{j=1}^{d}\int_{s}^{t}u_j^2e^{i(u,\symbf{X}_v-\symbf{X}_s)}{d}v\mathbb{1}_A\right]\\
&=\mathbb{P}(A)-\frac{1}{2}\|u\|^2\mathbb{E}\left[\int_{s}^{t}e^{i(u,\symbf{X}_v-\symbf{X}_s)}{d}v\mathbb{1}_A\right]
\end{align}
$$
Let $g(t)=\mathbb{E}\left[e^{i(u,\symbf{X}_t-\symbf{X}_s)}\mathbb{1}_{A}\right]$, then we obtain a differential equation of $g$
$$
g(t)=\mathbb{P}(A)-\frac{1}{2}\|u\|^2\int_{s}^{t}g(v){d}v\Longrightarrow g(t)=\mathbb{P}(A)e^{-\frac{1}{2}\|u\|^2(t-s)}
$$
i.e. 
$$
\mathbb{E}\left[e^{i(u,\symbf{X}_t-\symbf{X}_s)}\mathbb{1}_{A}\right]=\mathbb{E}\left[e^{-\frac{1}{2}\|u\|^2(t-s)}\mathbb{1}_{A}\right]
$$

**QED**
# Bessel Processes, Questions of Recurrence
> [!def] Bessel process(family)
> For integer $d\ge 2$, let $\symbf{B}_t=(B_t^{(1)},\cdots,B_t^{(d)}),(\Omega,\mathcal{F}_t),\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ be d-dimensional Brownian family. We define the Bessel process 
> $$
> R_t=\|\symbf{B}_t\|=\left(\sum_{i=1}^{d}(B_t^{(i)})^2\right)^{\frac{1}{2}}
> $$
> $\mathbb{P}^0(R_0=\|x\|)=1$. The process $R_t$ with probability measure $\{\hat{\mathbb{P}}^r\}_{r\ge0}\triangleq\{\mathbb{P}^{(r,0,\cdots,0)}\}_{r\ge0}$ is called Bessel family.

The definition is well-defined i.e. for $x,y\in\mathbb{R}^d$ with $\|x\|=\|y\|$. Then there exists orthogonal matrix $Q$ s.t. $y=Qx$ and process $\tilde{\symbf{B}}_t=Q\symbf{B}_t$ is d-dimensional Brownian motion starting at $y$. For any $F\in\mathcal{B}(C[0,\infty))$, 
$$
\mathbb{P}^x[R_\cdot\in F]=\mathbb{P}^x[\|\tilde{\symbf{B}}_t\|\in F]=\mathbb{P}^y[R_\cdot\in F]
$$
Hence, the distribution of the process $R$ doesn't depend on the starting point.
> [!proposition] Stochastic differential equation of Bessel process
> The Bessel process satisfies the stochastic equation
> $$
> R_t=r+\int_{0}^{t}\frac{d-1}{2R_s}{d}s+S_t
> $$
> where $S_t$ is a one dimensional Brownian motion with 
> $$
> S_t=\sum_{i=1}^{d}S_t^{(i)}, \ S^{(i)}_t=\int_{0}^{t}\frac{B^{(i)}_s}{R_s}{d}B^{(i)}_s
> $$

**Proof**
For convenience, we write $\mathbb{P}$ replacing $\hat{\mathbb{P}}^r$. Firstly, we note that $R_t=0\Longrightarrow W^{(1)}_t=0$. Recall [[The Brownian Sample Paths#^47fc7b|the properties of zero set with Brownian motion]], then $\symrm{Leb}\{R_t=0\}=0$. It implies the integral $\int_{0}^{t}\frac{d-1}{2R_s}{d}s$ is well-defined. 
Now we check $S_t$ is one-dimensional Brownian motion. It is easy to check $S_t^{(i)}\in\mathcal{M}_{2}^c$ and 
$$
\langle S^{(i)}_,S^{(j)}\rangle_t=\int_{0}^{t}\frac{B_s^{(i)}B_s^{(j)}}{R_s^2}{d}\langle B^{(i)},B^{(j)}\rangle_s=\delta_{ij}t
$$
thus
$$
\langle S\rangle_t=\sum_{i=1}^{d}\langle S^{(i)}\rangle_t=\sum_{i=1}^{d}\int_{0}^{t}\frac{(B^{(i)}_s)^2}{R_s^2}{d}s=t
$$
By [[#^b655c5|the characterization of Brownian motion]], $S_t$ is one-dimensional Brownian motion.
In order to compute the SDE of $R_t$, we use the Itô rule for $f(x)=(x_1^2+\cdots+x_d^2)^{\frac{1}{2}},x\in\mathbb{R}^d$. But we only compute as formalism. 
$$
\frac{\partial f}{\partial x_i}=\frac{x_i}{\|x\|},\frac{\partial^2 f}{\partial x_i \partial x_j}=\frac{\delta_{ij}}{\|x\|}-\frac{x_ix_j}{\|x\|^3}
$$
then
$$
\begin{align}
dR_t&=df(\symbf{B}_t)\\
&=\sum_{i=1}^{d}\frac{B^{(i)}_t}{R_t}{d}B^{(i)}_t+\frac{1}{2}\sum_{i=1}^{d}\sum_{j=1}^{d}\left(\frac{\delta_{ij}}{R_t}-\frac{B^{(i)}_tB^{(j)}_t}{R_t^3}\right){d}\langle B^{(i)},B^{(j)}\rangle_t\\
&=\sum_{i=1}^{d}\frac{B^{(i)}_t}{R_t}{d}B^{(i)}_t+\frac{d-1}{2R_t}{d}t
\end{align}
$$
It seems to be no problem. But we should note that $f(x)$ is not differential at origin and thus we can not use the Itô rule. The idea is "make a hole" at origin and take suitable function. 
**QED**
> [!proposition] Nonattainability of the Origin by the Brownian Path in Dimension $d \ge 2$
> The Bessel process $R_t$ satisfies
> $$
> \mathbb{P}[R_t>0,0\le t<\infty]=1
> $$

**Proof**
It suffices to show the case of $d=2$. For $d>2$, $R_t=0\Longrightarrow W^{(1)}_t+W^{(2)}_t=0$.
For $r>0$, there exists $k\in\mathbb{N}_+$ s.t. $(\frac{1}{k})^k\le r\le k$ and we define the stopping times 
$$
T_k=\inf\{t\ge0:R_t=(\frac{1}{k})^k\},S_k=\inf\{t\ge0:R_t=k\},\tau_k=T_k\wedge S_k\wedge n
$$
where $n\in\mathbb{N}$ is fixed. Now we use the Itô rule for $\log(R_t)$. Since $f(x)=\log(x)$ and $f\in C^2[(\frac{1}{k})^k,k]$, then 
$$
\log(R_t)=\log(r)+\sum_{i=1}^{d}\int_{0}^{t}\frac{B^{(i)}_s}{R_s^2}{d}B^{(i)}_s
$$
we take the stopping time $\tau_k$ and obtain
$$
\log(R_{\tau_k})=\log(r)+\sum_{i=1}^{d}\int_{0}^{\tau_k}\frac{B^{(i)}_s}{R_s^2}{d}B^{(i)}_s
$$
Since $|\frac{1}{R_t}|$ is bounded for $0\le t\le \tau_k$ and $\tau_k$ is also bounded. Therefore, We have 
$$
\mathbb{E}\int_{0}^{\tau_k}\frac{B^{(i)}_s}{R_s^2}{d}B^{(i)}_s=0
$$
and 
$$
\begin{align}
\log(r)&=\mathbb{E}\log(R_{\tau_k})\\
&=-k\log(k)\mathbb{P}(T_k\le S_k\wedge n)+\log(k)\mathbb{P}(S_k\le T_k\wedge n)+\mathbb{E}[\log(R_n)\mathbb{1}_{\{n<S_k\wedge T_k\}}]
\end{align}
$$
On $\{n<S_k\wedge T_k\}$, $\log(R_n)$ is between $(\frac{1}{k})^k$ and $k$ and thus is bounded. Recall [[The Brownian Sample Paths#^795b12|the sample path of Brownian motion is unbounded]], then we have 
$$
\mathbb{P}\left[\bigcap_{k=1}^{\infty}\{S_k<\infty\}\cap\{\lim_{k\to\infty}S_k=\infty\}\right]=1
$$
It implies $R_t$ can reach sufficiently large value $a.s.-\mathbb{P}$. Then let $n\to\infty$, we obtain
$$
\mathbb{P}\left[n<S_k\wedge T_k\right]\to0\Longrightarrow\mathbb{E}[\log(R_n)\mathbb{1}_{\{n<S_k\wedge T_k\}}]\to0
$$
Hence, 
$$
\begin{align}
\log(r)&=-k\log(k)\mathbb{P}(T_k\le S_k)+\log(k)\mathbb{P}(S_k\le T_k)\\
\Longrightarrow\mathbb{P}(T_k\le S_k)&=\frac{1}{k+1}-\frac{\log(r)}{(k+1)\log(k)}\to0 \ as \ k\to\infty
\end{align}
$$
We define $T=\inf\{t\ge0:R_t=0\}$. Note that $T_k\le T$, then 
$$
\mathbb{P}(T<\infty)=\lim_{k\to\infty}\mathbb{P}(T<S_k)\le \lim_{k\to\infty}\mathbb{P}(T_k\le S_k)=0
$$
Hence, $\mathbb{P}(T<\infty)=0$ i.e. $\mathbb{P}[R_t>0,0\le t<\infty]=1$. 
For $r=0$, for any $\varepsilon>0$, by [[#^db7104|strong Markov property of Bessel process]], 
$$
\hat{\mathbb{P}}^r(R_t>0;\varepsilon\le t<\infty)=\mathbb{E}\left[\hat{\mathbb{P}}^{R_t}(R_t>0;0\le t<\infty)\right]=1
$$
**QED**
# Martingale Moment Inequalities
For any $M\in\mathcal{M}^{c,loc}$, we denote by 
$$
M^*_t=\max_{0\le s\le t}|M_s|
$$
> [!proposition]
> Consider the continuous martingale $M$ and ite quadratic variation process $\langle M\rangle$. For any stopping time $T$, we have 
> 1. $$\mathbb{E}(|M_T|^{2m})\le C'_m\mathbb{E}\langle M\rangle_T^m, \ \ \ m>0$$
> 2. $$B_m\mathbb{E}\langle M\rangle_T^m\le \mathbb{E}(|M_T|^{2m}),\ \ \ m>\frac{1}{2}$$
> 3. $$B_m\mathbb{E}\langle M\rangle_T^m\le\mathbb{E}((M_T^*)^{2m})\le C_m\mathbb{E}\langle M\rangle_T^m,\ \ \ m>\frac{1}{2}$$
> 
> where $C_m,B_m$ for suitable positive constants are only depended on $m$.

**Proof**
Consider the process $Y_t$ as follow,
$$
Y_t=\delta+\varepsilon\langle M\rangle_t+M_t^2
$$
where $\delta,\varepsilon\ge0$ are constants to be chosen after. We use the Itô rule for $f(x)=x^m$ and replace $t$ with $T$. Then we have 
$$
\begin{align}
Y_T^m=&\delta^m+m(1+\varepsilon)\int_{0}^{T}Y^{m-1}_s{d}\langle M\rangle_s+2m(m-1)\int_{0}^{T}Y^{m-2}_sM_s^2{d}\langle M\rangle_s\\
&+2m\int_{0}^{T}Y_s^{m-1}M_s{d}M_s
\end{align}
$$
Since $M,Y,\langle M\rangle_t$ are bounded, by [[Continuous, Square-Integrable Martingales#^e5c0a3|Exercise]] and [[Continuous-Time Martingales#^1b13f7|Optional sampling theorem]], we obtain 
$$
\mathbb{E}\int_{0}^{T}2mY_s^{m-1}M_s{d}M_s=0
$$
Then we have 
$$
\mathbb{E}Y^m_T=\delta^m+m(1+\varepsilon)\mathbb{E}\int_{0}^{T}Y_s^{m-1}{d}\langle M\rangle_s+2m(m-1)\mathbb{E}\int_{0}^{T}Y_s^{m-2}M_s^2{d}\langle M\rangle_s\tag{$*$}
$$
Now we discuss the inequalities with different $m$. 
**Case1:$0<m\le 1$. We W.T.S upper bound**
Note that the item 
$$
2m(m-1)\mathbb{E}\int_{0}^{T}Y_s^{m-2}{d}\langle M\rangle_s\le 0
$$
Then we can "throw" this item. And by $m\le 1$, with $\delta\downarrow0$
$$
\begin{align}
\mathbb{E}\left[\varepsilon\langle M\rangle_T+M^2_T\right]^m\le\mathbb{E}(Y^m_T)&\le m(1+\varepsilon)\mathbb{E}\int_{0}^{T}Y_s^{m-1}{d}\langle M\rangle_s\\
&\le m(1+\varepsilon)\varepsilon^{m-1}\mathbb{E}\int_{0}^{T}\langle M\rangle_s^{m-1}{d}\langle M\rangle_s\\
&=(1+\varepsilon)\varepsilon^{m-1}\mathbb{E}\langle M\rangle_T^{m}
\end{align}\tag{$**$}
$$
Recall the inequality, for $m\le 1,x,y\ge0$, 
$$
2^{m-1}(x^{m}+y^m)\le (x+y)^m
$$
Therefore, we have 
$$
2^{m-1}\left(\varepsilon^m\mathbb{E}\langle M\rangle_T+\mathbb{E}|M_T|^{2m}\right)\le (1+\varepsilon)\varepsilon^{m-1}\mathbb{E}\langle M\rangle^m_T
$$
hence, 
$$
\mathbb{E}|M_T|^{2m}\le \left((1+\varepsilon)(\frac{\varepsilon}{2})^{m-1}-\varepsilon^m\right)\mathbb{E}\langle M\rangle_T^m
$$
$\varepsilon$ can be chosen in $(0,\frac{1}{2^{m-1}-1})$. 
**Case2: $m>1$. We W.T.S. lower bound**
Note that the above inequalities are based on $m\le 1$, i.e. if $m>1$ and thus the all inequalities are reversed. Then we have 
$$
\mathbb{E}|M_T|^{2m}\ge \left((1+\varepsilon)(\frac{\varepsilon}{2})^{m-1}-\varepsilon^m\right)\mathbb{E}\langle M\rangle_T^m
$$
**Case3: $\frac{1}{2}<m\le 1$. We W.T.S. lower bound**
First, let $\varepsilon=0$ and $\delta\downarrow0$ for $(*)$, we obtain
$$
\mathbb{E}|M_T|^{2m}=2m(m-\frac{1}{2})\mathbb{E}\int_{0}^{T}|M_s|^{2(m-1)}{d}\langle M\rangle_s
$$
We use the $(**)$
$$
2^{m-1}\left(\varepsilon^m\mathbb{E}\langle M\rangle_T^m+\mathbb{E}|M_T|^{2m}\right)\le m(1+\varepsilon)\mathbb{E}\int_{0}^{T}M_s^{2(m-1)}{d}\langle M\rangle_s
$$
and we have 
$$
\mathbb{E}|M_T|^{2m}\ge\frac{\frac{(1+\varepsilon)}{2(m-\frac{1}{2})}-2^{m-1}}{2^{m-1}\varepsilon^m}\mathbb{E}\langle M\rangle_T^{m}\triangleq B_m\mathbb{E}\langle M\rangle_T^{m}
$$
**Case4: $m>1$. We W.T.S. upper bound**
Note that the inequalities of case3 are based on $m\le 1$, i.e. if $m>1$ and thus the all inequalities are reversed. Then we have 
$$
\mathbb{E}|M_T|^{2m}\le B_m\mathbb{E}\langle M\rangle_T^{m}
$$
Above all, Case1+Case4 $\Longrightarrow$ inequality 1. Case2+Case3 $\Longrightarrow$ inequality 2. For 3. we consider use [[Continuous-Time Martingales#^bd276e|Doob's maximal inequalities]] for $M^*_{T\wedge t}$
$$
\begin{align}
B_m\mathbb{E}\langle M\rangle^m_{T\wedge t}\le \mathbb{E}|M_{T\wedge t}|^{2m}&\le \mathbb{E}|M_{T\wedge t}^*|^{2m}\\
&\le \left(\frac{2m}{2m-1}\right)\mathbb{E}|M_{T\wedge t}|^{2m}\\
&\le \left(\frac{2m}{2m-1}\right)C'_m\mathbb{E}\langle M\rangle_{T\wedge t}^{2m}
\end{align}
$$
Let $t\to\infty$ and obtain the inequality we desired. 
**QED**
> [!thm] Burkholder-Davis-Gundy Inequalities
> Let $M\in\mathcal{M}^{c,loc}$. For $m>0$, there exists $b_m,B_m$ s.t. 
> $$
> b_m\mathbb{E}\langle M\rangle_T^m\le\mathbb{E}(M_T^*)^{2m}\le B_m\mathbb{E}\langle M\rangle_T^m
> $$ 

^6cf33d

**Proof**
By above proposition, we have dealt the case $m>\frac{1}{2}$. Now we consider $0<m<\frac{1}{2}$.
We should recall a [[The Doob-Meyer Decomposition#^f31d9e|Exercise]] and give a corollary. 
$$
\mathbb{E}(V_T^p)\le \frac{2-p}{1-p}\mathbb{E}(A_T^p),0<p<1
$$
Now we take $V_T=(M^*_T)^2,A_T=C\langle M\rangle_T$ and we have 
$$
\mathbb{E}|M^*_T|^{2m}\le \frac{2-m}{1-m}C^m\mathbb{E}\langle M\rangle_T^m,
$$
And for lower bound, we can choose $V_T=C\langle M\rangle_T,A_T=(M^*_T)^2$
$$
\frac{1-m}{2-m}C^m\mathbb{E}\langle M\rangle_T^m\le \mathbb{E}|M^*_T|^{2m}
$$
**QED**

---
# Exercises
> [!question]
> With ${Z_t; 0 \le t < \infty}$ as in Example 3.9, set $Y_t = 1/Z_t$; $0 \le t < \infty$, which is well defined because $\mathbb{P}[\inf_{0 \le t \le T} Z_t > 0] = \mathbb{P}[\inf_{0 \le t \le T} \zeta_t > -\infty] = 1$. Show that $Y$ satisfies the stochastic differential equation $$ dY_t = Y_t X_t^2 dt - Y_t X_t dW_t, \quad Y_0 = 1. $$

> [!done]
> 

> [!question]
> Let $W_t = (W_t^{(1)}, W_t^{(2)}, W_t^{(3)})$ be a three-dimensional Brownian motion starting at the origin, and define $$ X = \prod_{i=1}^3 \text{sgn}(W_1^{(i)}), $$ $$ M_t^{(1)} = W_t^{(1)}, \quad M_t^{(2)} = W_t^{(2)} \quad \text{and} \quad M_t^{(3)} = X W_t^{(3)}. $$ Show that each of the pairs $(M^{(1)}, M^{(2)})$, $(M^{(1)}, M^{(3)})$ and $(M^{(2)}, M^{(3)})$ is a two-dimensional Brownian motion, but $(M^{(1)}, M^{(2)}, M^{(3)})$ is not a three-dimensional Brownian motion. Explain why this does not provide a counter-example to Theorem 3.16, i.e., a three-dimensional process which is not a Brownian motion but which has components in $\mathcal{M}^{c, \text{loc}}$ and satisfies (3.11). 

> [!done]
> 

> [!question]
> Let $W = \{W_t = (W_t^{(1)}, \dots, W_t^{(d)}), \mathcal{F}_t; 0 \le t < \infty\}$ be a $d$-dimensional Brownian motion starting at the origin, and let $Q$ be a $d \times d$ orthogonal matrix ($Q^T = Q^{-1}$). Show that $\tilde{W}_t \triangleq Q W_t$ is also a $d$-dimensional Brownian motion. We express this property by saying that "$d$-dimensional Brownian motion starting at the origin is rotationally invariant."

> [!done]
> 

> [!question]
> Show that for each $d \ge 2$, the Bessel family with dimension $d$ is a strong Markov family (where we modify Definition 2.6.3 to account for the state space $[0, \infty)$).

^db7104

> [!done]
> 

> [!question]
> Let $R = \{R_t, \mathcal{F}_t; 0 \leq t < \infty\}$ be a Bessel process with dimension $d \geq 2$ starting at $r > 0$, and define $$ m = \inf_{0 \leq t < \infty} R_t. $$ 
> 1. Show that if $d = 2$, then $m = 0$ a.s. $\mathbb{P}$. 
> 2. Show that if $d \geq 3$, then $m$ has the beta distribution $$ \mathbb{P}[m \leq c] = \left( \frac{c}{r} \right)^{d-2}, \quad 0 \leq c \leq r. $$

> [!done]
> 

> [!question]
> With $W = \{W_t, \mathcal{F}_t; 0 \leq t < \infty\}$ a standard, one-dimensional Brownian motion and $X$ a measurable, adapted process satisfying $$ \mathbb{E} \int_0^T |X_t|^{2m} dt < \infty $$ for some real numbers $T > 0$ and $m \geq 1$, show that $$ \mathbb{E} \left| \int_0^T X_t dW_t \right|^{2m} \leq (m(2m-1))^m T^{m-1} \mathbb{E} \int_0^T |X_t|^{2m} dt. $$

> [!done]
> 

> [!question]
> Let $R$ be a Bessel process with dimension $d \ge 3$ starting at $r \ge 0$. Show that $$ \mathbb{P}\left[\lim_{t \to \infty} R_t = \infty\right] = 1. $$

> [!done]
> 

> [!question]
> Let $M = (M^{(1)}, \dots, M^{(d)})$ be a vector of continuous, local martingales, i.e., $M^{(i)} \in \mathscr{M}^{c, \text{loc}}$, and denote $$ \|M\|_t^* \triangleq \max_{0 \leq s \leq t} \|M_s\|, \quad A_t \triangleq \sum_{i=1}^d \langle M^{(i)} \rangle_t; \quad 0 \leq t < \infty. $$ Show that for any $m > 0$, there exist (universal) positive constants $\lambda_m, \Lambda_m$ such that $$ \lambda_m \mathbb{E}(A_T^m) \leq \mathbb{E}\left( (\|M\|_T^*)^{2m} \right) \leq \Lambda_m \mathbb{E}(A_T^m) $$ holds for every stopping time $T$.

^400644

> [!question]
> Define polynomials $H_n(x, y)$ for $n=0,1,2,\dots$ by $$ H_n(x, y)=\left.\frac{\partial^n}{\partial \alpha^n} \exp \left(\alpha x-\frac{1}{2} \alpha^2 y\right)\right|_{\alpha=0}, \quad x, y \in \mathbb{R} $$ (e.g., $H_0(x, y)=1$, $H_1(x, y)=x$, $H_2(x, y)=x^2-y$, $H_3(x, y)=x^3-3 x y$, $H_4(x, y)=x^4-6 x^2 y+3 y^2$, etc.). These polynomials satisfy the recursive relations $$ \frac{\partial}{\partial x} H_n(x, y)=n H_{n-1}(x, y), \quad n=1,2, \dots $$ as well as the backward heat equation $$ \frac{\partial}{\partial y} H_n(x, y)+\frac{1}{2} \frac{\partial^2}{\partial x^2} H_n(x, y)=0, \quad n=0,1, \dots $$ For any $M \in \mathscr{M}^{c, \text{loc}}$, verify (i) the multiple Itô integral computation $$ \int_0^t \int_0^{t_1} \cdots \int_0^{t_{n-1}} d M_{t_n} \cdots d M_{t_2} d M_{t_1}=\frac{1}{n!} H_n\left(M_t,\langle M\rangle_t\right), $$ (ii) and the expansion $$ \exp \left(\alpha M_t-\frac{\alpha^2}{2}\langle M\rangle_t\right)=\sum_{n=0}^{\infty} \frac{\alpha^n}{n!} H_n\left(M_t,\langle M\rangle_t\right). $$ (The polynomials $H_n(x, y)$ are related to the Hermite polynomials $$ h_n(x) \triangleq \frac{(-1)^n}{\sqrt{n!}} e^{x^2 / 2} \frac{d^n}{d x^n} e^{-x^2 / 2} $$ by the formula $H_n(x, y)=\sqrt{n!}\, y^{n/2} h_n(x/\sqrt{y})$.) 

> [!question]
> Consider a function $\sigma: \mathbb{R} \to (0, \infty)$ which is of class $C^1$ and such that $1/\sigma$ is not integrable at either $\pm\infty$. Let $c, \rho$ be two real constants, and introduce the (strictly increasing in $x$) function $$ f(t, x)=e^{c t} \int_0^x \frac{dy}{\sigma(y)}, \quad 0 \le t < \infty,\ x \in \mathbb{R} $$ and the continuous, adapted process $$ \xi_t=\xi_0+\rho \int_0^t e^{c s}\,ds+\int_0^t e^{c s}\,d W_s, \quad \mathscr{F}_t;\ 0 \le t < \infty. $$ Let $g(t,\cdot)$ denote the inverse of $f(t,\cdot)$. Show that the process $X_t=g(t,\xi_t)$ satisfies the stochastic integral equation $$ X_t=X_0+\int_0^t b(X_s)\,ds+\int_0^t \sigma(X_s)\,d W_s, \quad 0 \le t < \infty $$ for an appropriate continuous function $b: \mathbb{R} \to \mathbb{R}$, which you should determine. 

> [!question]
> Consider two real numbers $\delta, \mu$; a standard, one-dimensional Brownian motion $W$; and let $W_t^{(\mu)}=W_t+\mu t$, $0 \le t < \infty$. Show that the process $$ X_t=\int_0^t \exp \left[\delta\left\{W_t^{(\mu)}-W_s^{(\mu)}\right\}-\frac{1}{2} \delta^2(t-s)\right] ds, \quad 0 \le t < \infty $$ satisfies the Shiryaev–Roberts stochastic integral equation $$ X_t=\int_0^t \big(1+\delta \mu X_s\big)\,ds+\delta \int_0^t X_s\,d W_s. $$ 

> [!question]
> Let $W$ be a standard, one-dimensional Brownian motion and $0<T<\infty$. Show that $$ \lim_{\beta \to \infty} \sup_{0 \le t \le T} \left|e^{-\beta t} \int_0^t e^{\beta s}\,d W_s\right|=0, \quad \text{a.s.} $$ 

> [!question]
> Establish the Wald identities $$ \mathbb{E}\left(W_T\right)=0,\quad \mathbb{E}\left(W_T^2\right)=\mathbb{E}\,T. $$

> [!question]
> Let $R$ be a Bessel process with dimension $d \ge 3$, starting at $r=0$. Show that $M_t \triangleq 1/R_t^{d-2}$, $1 \le t < \infty$ (i) is a local martingale, (ii) satisfies $\sup_{1 \le t < \infty} \mathbb{E}(M_t^p)<\infty$ for every $0<p<d/(d-2)$ (and is thus uniformly integrable), (iii) is not a martingale.

> [!question]
> Let $R$ be a Bessel process with dimension $d=2$ starting at $r=0$. Show that $X_t=-\log R_t$, $1 \le t < \infty$ is a local martingale with $\mathbb{E}\,e^{\alpha X_t}<\infty$ for $-\infty<\alpha<2$, $t \ge 1$, but $X$ is not a martingale. 

> [!question]
> Let $X$ be a continuous process and $A$ a continuous, increasing process with $X_0=A_0=0$, a.s. (i) Suppose that for every $\theta \in \mathbb{R}$, the process $$ Z_t^{(\theta)} \triangleq \exp \left(\theta X_t-\frac{1}{2} \theta^2 A_t\right), \quad 0 \le t < \infty $$ is a local martingale. Prove that $X \in \mathscr{M}^{c, \text{loc}}$ and $\langle X\rangle=A$. (ii) Suppose that both $X$ and $Z^{(1)}=\exp\big(X-\frac12 A\big)$ are local martingales. Then again $\langle X\rangle=A$.

> [!question]
> Let $X$ be a continuous semimartingale of the form $$ X_t=X_0+M_t+B_t, $$ and $\{B^{(n)}\}_{n=1}^\infty$ a sequence of processes of bounded variation, such that $$ \mathbb{P}\!\left[\lim_{n \to \infty} B_t^{(n)}=X_t\right]=1 $$ holds for every finite $t>0$. If the function $f: \mathbb{R} \to \mathbb{R}$ is of class $C^1(\mathbb{R})$, show that $$ \lim_{n \to \infty} \int_0^t f\big(B_s^{(n)}\big)\,d B_s^{(n)} =\int_0^t f(X_s)\,d X_s+\frac{1}{2} \int_0^t f'(X_s)\,d\langle M\rangle_s $$ holds a.s. $\mathbb{P}$ for every fixed $t>0$.