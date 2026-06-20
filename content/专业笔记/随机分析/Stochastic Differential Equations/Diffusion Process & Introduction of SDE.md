Loosly speaking, The theorem of existence and uniqueness(E&U) problem for solutions of SDE is a study of **diffusion process**.
> [!def] Diffusion process
> **Diffusion=Markov family with continuous path + infinitesimal generator.**
> Consider Markov family $X_t,(\Omega,\mathcal{F}),\{\mathbb{P}^x\}_{x\in\mathbb{R}^d}$ and relate 
> $$
> \lim_{t\downarrow 0}\frac{1}{t}\mathbb{E}^x[f(X_t)-f(x)]=(\mathscr{A}f)(x)\tag{$*$}
> $$
> holds for $f\in C^2(\mathbb{R}^d)$, where LHS is the infinitesimal generator of the Markov family, and RHS is 2nd order differential operator
> $$
> \mathscr{A}=\frac{1}{2}\sum_{k=1}^{d}\sum_{i=1}^{d}a_{ik}(x)\frac{\partial^2}{\partial x_i\partial x_k}+\sum_{i=1}^{d}b_i(x)\frac{\partial}{\partial x_i}
> $$
> $b=(b_1,\cdots,b_d)$ is the vector of drift and $\{a_{ik}\}_{1\le i,k\le d}$ is the diffusion matrix which is sysmmetric and nonnegetive-definite. Take test function $f_i(x)=x_i$, we have 
> $$
> \mathbb{E}^x[X_t^{(i)}-x_i]=tb_i(x)+o(t)\tag{D1}
> $$
> and take test function $f_i(y)=(y_i-x_i)(y_k-x_k)$, we have 
> $$
> \mathbb{E}^x[(X^{(i)}-x_i)(X^{(k)}-x_k)]=ta_{ik}(x)+o(t)\tag{D2}
> $$
> (D1) implies that $b_i(x)$ measures the velocity of $X$ and $a_{ik}$ measures the rate of change in the covariance matrix of $X_t-x$. 
> We say $X$ is a **diffusion process** if $X$ holds **$(*)$, (D1) and (D2)** for $x\in\mathbb{R}^d$ and $f\in C^2(\mathbb{R}^d)$ which is bounded and has bounded 1st, 2nd derivatives and $X$ is a **strong Markov family with stopping time $S$**.  

^3fb7e2

> [!note] Purely analytical approach to study diffusion(Kolmogorov-Feller)
> Consider the transition probability density function $\Gamma(t;x,y)$
> $$
> \mathbb{P}^x[X_t\in{d}y]=\Gamma(t;x,y){d}y
> $$
> We often assume the $\Gamma(t;x,y)$ satisfies the **forward Kolmogorov equation(FKE)**
> $$
> \frac{\partial \Gamma}{\partial t}=\mathscr{A}^*\Gamma(t;x,y)
> $$
> where $\mathscr{A}^*$ is the adjoint operator of $\mathscr{A}$
> $$
> \mathscr{A}^*(f)=\frac{1}{2}\sum_{k=1}^{d}\sum_{i=1}^{d}\frac{\partial^2 f}{\partial x_i\partial x_k}-\sum_{i=1}^{d}\frac{\partial b_i(x)f}{\partial x_i}
> $$
> and **backward Kolmogorov equation(BKE)**
> $$
> \frac{\partial \Gamma}{\partial t}=\mathscr{A}\Gamma(t;x,y)
> $$
> We should solve the PDE and establish the Markov process. 

> [!note] Purely probabilistic approach to study diffusion(Ito)
> We consider the SDE
> $$
> X_t^{(i)}=x_0+\int_{0}^{t}b_i(X_s){d}s+\sum_{j=1}^{r}\int_{0}^{t}\sigma_{ij}(X_s){d}W^{(j)}_s\tag{SDE1}
> $$
> where $b=(b_1,\cdots,b_d)$, $\{\sigma_{ij}\}_{1\le i\le d,1\le j\le r}$ and $W$ is d-dimensional Brownian motion. Then we expect $(*)$, (D1) and (D2) holds with
> $$
> a_{ik}=\sum_{j=1}^{r}\sigma_{ij}\sigma_{kj}
> $$

^cefffc

> [!proposition]
> Assume that the coefficients $b_i, \sigma_{ij}$ are bounded and continuous, and the $\mathbb{R}^d$-valued process $X$ satisfies (SDE1). Show that (D1), (D2) hold for every $x \in \mathbb{R}^d$, and that $(*)$ holds for every $f \in C^2(\mathbb{R}^d)$ which is bounded and has bounded first- and second-order derivatives.

**Proof**
**For (D1).** 
We have 
$$
\begin{align}
\frac{1}{t}\mathbb{E}^x\left[X^{(i)}-x_i\right]&=\frac{1}{t}\mathbb{E}^x\left[\int_{0}^{t}b_i(X_s){d}s+\sum_{j=1}^{r}\int_{0}^{t}\sigma_{ij}(X_s){d}W_s^{(j)}\right]\\
&=\frac{1}{t}\mathbb{E}^x\left[\int_{0}^{t}b_i(X_s){d}s\right]\xrightarrow{t\downarrow0}\mathbb{E}^x[b_i(X_s)]\xrightarrow{s\downarrow0} b_i(x)
\end{align}
$$
**For (D2)**
$$
\begin{align}
&\frac{1}{t}\mathbb{E}^x\left[(X^{(i)}-x_i)(X^{(k)}-x_k)\right]\\
=&\frac{1}{t}\mathbb{E}^x\left[\int_{0}^{t}b_i(X_s){d}s\int_{0}^{t}b_k(X_s){d}s\right]\xrightarrow{t\downarrow0}0\\
&+\frac{1}{t}\mathbb{E}^x\left[\sum_{j=1}^{r}\int_{0}^{t}\sigma_{ij}(X_s)\sigma_{kj}(X_s){d}s\right]\xrightarrow{t\downarrow0,s\downarrow0}\sum_{j=1}^{r}\sigma_{ij}(x)\sigma_{kj}(x)
\end{align}
$$
By [[The Change-of-Variable Formula#^e6e674|the Ito's rule]] for $f(X_t)$, 
$$
f(X_t)-f(x)=\int_{0}^{t}(\mathscr{A}f)(X_s){d}s+\sum_{i=1}^{d}\sum^{r}_{j=1}\int_{0}^{t}\frac{\partial f}{\partial x_i}\sigma_{ij}(X_s){d}W_s^{(j)}
$$
Then 
$$
\frac{1}{t}\mathbb{E}^x\left[f(X_t)-f(x)\right]=\frac{1}{t}\mathbb{E}\left[\int_{0}^{t}(\mathscr{A}f)(X_s){d}s\right]\xrightarrow{t\downarrow0,s\downarrow0}(\mathscr{A}f)(x)
$$
**QED**