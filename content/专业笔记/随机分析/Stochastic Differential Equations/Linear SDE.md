> [!def] Linear SDE
> We consider 
> $$
> \begin{cases}
> dX_t=(A(t)X_t+a(t)){d}t+\sigma(t){d}W_t\\
> X_0=\xi
> \end{cases}\tag{$*1$}
> $$
> where $W_t$ is r-dimensional Brownian motion and $\left(A(t)\right)_{d\times d}$, $(a(t))_{d\times1}$ and $(\sigma(t))_{d\times r}$ are measurable, nonrandom and locally bounded. 

> [!proposition] Solution of $(*1)$
> Recall the result of ODE, similarly, we obtain by the Ito's rule, 
> $$
> X_t=\Phi(t)\left[X_0+\int_{0}^{t}\Phi^{-1}(s)a(s){d}s+\int_{0}^{t}\Phi^{-1}(s)\sigma(s){d}W_s\right]\tag{$*2$}
> $$

> [!proposition] Expectation and covariance function of $(*2)$
> We define $m(t)=\mathbb{E}(X_t)$, $\gamma(s,t)=\mathbb{E}[(X_t-m(t))(X_s-m(s))^\top]$ and $V(t)=\gamma(t,t)$. Then $(*2)$ has
> $$
> m_{X_t}(t)=\Phi(t)\left[m(0)+\int_{0}^{t}\Phi^{-1}(s)a(s){ds}\right]\tag{$*3$}
> $$
> $$
> \gamma(s,t)=\Phi(s)\left[V(0)+\int_{0}^{s\wedge t}\Phi^{-1}(u)\sigma(u)\left(\Phi^{-1}(u)\sigma(u)\right)^\top{d}u\right]\Phi^{\top}(t)\tag{$*4$}
> $$
> $$
> V(t)=\Phi(t)\left[V(0)+\int_{0}^{t}\Phi^{-1}(u)\sigma(u)\left(\Phi^{-1}(u)\sigma(u)\right)^\top{d}u\right]\Phi^{\top}(t)\tag{$*5$}
> $$

> [!def] Linear equation associated with $m(t)$ and $V(t)$ 
> We have 
> $$
> \begin{cases}
> \frac{dm(t)}{dt}=A(t)m(t)+a(t)\\
> \frac{dV(t)}{dt}=A(t)V(t)+V(t)A^\top(t)+\sigma(t)\sigma^\top(t)
> \end{cases}\tag{$*6$}
> $$

# Gauss-Markov Processes
We begin this section through a simple proposition.
> [!proposition]
> If $X_0=\xi\sim N_d(\mu,\Sigma)$, then $X_t$ of $(*2)$ is a Gaussian process.  

**Proof**
For $0\le t_1<\cdots<t_d$, we W.T.S. $(X_{t_1},\cdots,X_{t_d})$ is a Gaussian vector. We write as 
$$
\begin{align}
\begin{bmatrix}
X_{t_1}\\
\vdots\\
X_{t_d}
\end{bmatrix}&=\begin{bmatrix}
\Phi(t_1)\\
\vdots\\
\Phi(t_d)
\end{bmatrix}\xi+\begin{bmatrix}
\Phi(t_1)\int_{0}^{t_1}\Phi^{-1}(s)a(s){d}s\\
\vdots\\
\Phi(t_d)\int_{0}^{t_d}\Phi^{-1}(s)a(s){d}s
\end{bmatrix}+\begin{bmatrix}
\Phi(t_1)\int_{0}^{t_1}\Phi^{-1}(s)\sigma(s){d}W_s\\
\vdots\\
\Phi(t_d)\int_{0}^{t_d}\Phi^{-1}(s)\sigma(s){d}W_s
\end{bmatrix}\\
&:=B\xi+C+D
\end{align}
$$
It suffices to show that $D$ is also a Gaussian vector. Since $\Phi^{-1}(t)$ and $\sigma(t)$ are deterministic function, then 
$$
\int_{0}^{t_k}\Phi^{-1}(s)\sigma(s){d}W_s\sim N_d\left(\textbf{0},\int_{0}^{t_k}(\Phi^{-1})^2(s)\sigma^2(s){d}s\right)
$$
Hence, $X_t$ is a Gaussian process. 
**QED**
> [!question]
> Now our question is what additional condition can guarantee the nondegeneracy of the distribution of $X_t$ i.e. the positive of $(*6)$?

This problem is associated with control theory and thus we introduce some concept in control theory.
> [!def] Controllable
> The pair $(A,\sigma)$ is controllable on $[0,T]$ if for every $x,y\in\mathbb{R}^d$ there exists a function $u:[0,T]\to\mathbb{R}^r$ s.t. the process 
> $$
> Y(t)=x+\int_{0}^{t}A(s)Y(s){d}s+\int_{0}^{t}\sigma(s)u(s){d}s
> $$
> satisfies $Y(T)=y$. 

> [!proposition] The controllable equivalent condition
> The pair $(A,\sigma)$ is controllable $\Longleftrightarrow$ the matrix
> $$
> M(T)\triangleq\int_{0}^{T}\Phi^{-1}(t)\sigma(t)(\Phi^{-1}(t)\sigma(t))^\top{d}t
> $$
> is nonsingular. 

The proof can refer to [[能控性]] and recall [[能控性#^c975cc|Kalman rank condition]].
> [!def] Constant case
> We consider the pair $(A,\sigma)$ is independent of time $t$. 
> $$
> \frac{dV(t)}{dt}=AV(t)+V(t)A^\top+\sigma\sigma^\top\tag{$*7$}
> $$
> and
> $$
> V(t)=e^{tA}\left[V(0)+\int_{0}^{t}e^{-sA}\sigma\sigma^\top e^{-sA^\top}{d}s\right]e^{tA^\top}\tag{$*8$}
> $$
> If we assume that all eigenvalues of $A$ **have negative real parts**, then the integral 
> $$
> V\triangleq\int_{0}^{\infty}e^{sA}\sigma\sigma^\top e^{sA^\top}{d}s
> $$
> converges. 

> [!proposition]
> $V$ solves the equation $(*7)$ and $(*8)$.

**Proof**
We should prove a lemma. 
> [!lemma]
> $V$ satisfies the algebraic matrix equation $$AV + VA^\top = -\sigma\sigma^\top$$

It is obviously that we use I.B.P and thus the conclusion holds.
$$
\begin{align}
AV + VA^\top&=\int_{0}^{\infty}Ae^{sA}\sigma\sigma^\top e^{sA^\top}{d}s+\int_{0}^{\infty}e^{sA}\sigma\sigma^\top e^{sA^\top}A^\top{d}s\\
&=-\sigma\sigma^\top-\int_{0}^{\infty}e^{sA}\sigma\sigma^\top e^{sA^\top}A^\top{d}s+\int_{0}^{\infty}e^{sA}\sigma\sigma^\top e^{sA^\top}A^\top{d}s\\
&=-\sigma\sigma^\top
\end{align}
$$
Now $(*7)$ holds naturally. For $(*8)$, 
$$
\begin{align}
&e^{tA}Ve^{tA^\top}+e^{tA}\int_{0}^{\infty}e^{-sA}\sigma\sigma^\top e^{-sA^\top}{d}se^{tA^\top}\\
=&\int_{0}^{\infty}e^{(t+s)A}\sigma\sigma^\top e^{(t+s)A^\top}+\int_{0}^{\infty}e^{(t-s)A}\sigma\sigma^\top e^{(t-s)A^\top}{d}s\tag{$u=t\pm s$}\\
=&\int_{t}^{\infty}e^{uA}\sigma\sigma^\top e^{uA^\top}+\int_{t}^{-\infty}e^{uA}\sigma\sigma^\top e^{uA^\top}{d}s=V
\end{align}
$$
**QED**
> [!thm] Solution of constant case
> Suppose in the SDE$(*1)$ that $\sigma(t) \equiv \sigma$, $a(t) \equiv 0$, all the eigenvalues of $A(t) \equiv A$ have negative real parts, and $\xi\sim N_d(0,\mathbb{E}(\xi\xi^\top))$. Then the solution $X$ is a **stationary**, zero-mean Gaussian process, with covariance function $$\gamma(s, t) = \begin{cases} e^{(s-t)A}V; & 0 \le t \le s < \infty, \\ V e^{(t-s)A^T}; & 0 \le s \le t < \infty. \end{cases} $$

> [!example] The Ornstein-Uhlenbeck(OU) Process 
> We consider the 1-dim case $d=r=1$. 
> $$
> \begin{cases}
> dX_t=-\alpha X_t{d}t+\sigma{d}W_t\\
> X_0=\xi
> \end{cases}\tag{OU}
> $$
> where $\alpha,\sigma>0$ are constants. Compute its solution, expectation and covariance functions.

**Solution**
The solution is 
$$
X_t=e^{-\alpha t}X_0+\int_{0}^{t}e^{-\alpha(t-s)}\sigma{d}W_t
$$
and 
$$
m(t)=e^{-\alpha t}m(0)
$$
$$
\gamma(s,t)=\left[V(0)+\frac{\sigma^2}{2\alpha}(e^{2\alpha (t\wedge s)}-1)\right]e^{-\alpha (t+s)}
$$
$$
V(t)=\left[V(0)-\frac{\sigma^2}{2\alpha}\right]e^{-2t\alpha}+\frac{\sigma^2}{2\alpha}
$$
**QED**
# Brownian Bridge
> [!def] Brownian bridge
> We consider
> $$
> \begin{cases}
> dX_t=\frac{b-X_t}{T-t}{d}t+{d}W_t\\
> X_0=a
> \end{cases}\tag{BB}
> $$
> We write as the form of $(*1)$, 
> $$
> dX_t=\left(-\frac{1}{T-t}X_t+\frac{b}{T-t}\right){d}t+{d}W_t
> $$
> The solution is 
> $$
> X_t=a(1-\frac{t}{T})+b\frac{t}{T}+(T-t)\int_{0}^{t}\frac{dW_s}{T-s}
> $$

> [!proposition]
> The process
> $$
> Y_t=\begin{cases}
> (T-t)\int_{0}^{t}\frac{dW_t}{T-s},&0\le t<T\\
> 0,&t=T
> \end{cases}
> $$
> is the continuous, zero-mean and Gaussian with covariance function
> $$
> \gamma(s,t)=(s\wedge t)-\frac{st}{T}
> $$

> [!proposition]
> The process
> $$
> X_t=\begin{cases}
> a(1-\frac{t}{T})+b\frac{t}{T}+(T-t)\int_{0}^{t}\frac{dW_s}{T-s},&0\le t<T\\
> b,&t=T
> \end{cases}
> $$
> is Gaussian with a.s. continuous paths, expectation function
> $$
> m(t)=a(1-\frac{t}{T})+b\frac{t}{T}
> $$
> and covariance function
> $$
> \gamma(s,t)=(s\wedge t)-\frac{st}{T}
> $$

> [!def] Brownian bridge from $a$ to $b$
> A Brownian bridge from $a$ to $b$ on $[0,T]$ is a continuous process $X_t$ with finite distributions 
> $$
> \begin{align}
> \mathbb{P}\left[X_{t_1}\in dx_1,\cdots,X_{t_n}\in dx_n\right]=\prod_{i=1}^{n}p(t_t-t_{i-1};x_{i-1},x_i)\frac{p(T-t_n;x_n,b)}{p(T;a,b)}dx_1\cdots dx_n
> \end{align}
> $$
> where $0=t_0<t_1<\cdots<t_n<T,x_0=a,(x_1,\cdots,x_n)\in\mathbb{R}^n$ and $p(t;x,y)$ is Gaussian kernel.

The most vivid way to think about Brownian bridge is this process.
> [!def]
> Let $W_t$ be a standard, 1-dim Brownian motion. Consider the process
> $$
> B_t^{a\to b}=a(1-\frac{t}{T})+b\frac{t}{T}+(W_t-\frac{t}{T}W_T)
> $$ 
> $B_t^{a\to b}$ is the Brownian bridge from $a$ to $b$.

# The General, One-Dimensional Linear Equation
> [!def] General case
> We consider the process
> $$
> dX_t=(A(t)X_t+a(t)){d}t+\sum_{j=1}^{r}(S_j(t)X_t+\sigma_j(t))dW_t^{(j)}\tag{$*9$}
> $$
> where $W_t$ is r-dim Brownian motion and $A,a,S_j,\sigma_j$ are measurable, $\{\mathcal{F}_t\}$-adapted and locally bounded process. Let 
> $$
> \zeta_t=\sum_{j=1}^{r}\int_{0}^{t}S_j(u){d}W^{(j)}_u-\frac{1}{2}\sum_{j=1}^{r}\int_{0}^{t}S_j^2(u){d}u\tag{$*10$}
> $$
> $$
> Z_t=\exp\left(\int_{0}^{t}A(u){d}u+\zeta_t\right)\tag{$*11$}
> $$

> [!proposition]
> The solution of $(*9)$ is 
> $$
> X_t=Z_t\left[X_0+\int_{0}^{t}\frac{1}{Z_u}(a(u)-\sum_{j=1}^{r}S_j(u)\sigma_j(u)){d}u+\sum_{j=1}^{r}\int_{0}^{t}\frac{\sigma_j(u)}{Z_u}{d}W_u^{(j)}\right]
> $$
> In particular, the solution of the SDE
> $$
> dX_t=A(t)X_t{d}t+\sum_{j=1}^{r}S_j(t)X_t{d}W^{(j)}_t
> $$
> is 
> $$
> X_t=Z_tX_0
> $$

**Proof**

**QED**
> [!proposition]
> In the constant case, $A(t)\equiv A,S_j(t)\equiv S_j$ with $2A<\sum_{j=1}^{r}S_j^2$, then $\lim_{t\to\infty}X_t=0$ for arbitrary $X_0$.

**Proof**

**QED**

---
# Exercises