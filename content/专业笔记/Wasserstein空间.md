>[!def] Couple (Coupling)
>Set $\mathcal{P}(X)$ be the set of all Borel probability measure on $X$. For $\mu,\nu\in\mathcal{P}(X)$, we define the couple set 
>$$
>\Pi(\mu,\nu)=\left\{\pi\in\mathcal{P}(X\times X):(\text{proj}_1)_\#\pi=\mu,(\text{proj}_2)_\#\pi=\nu\right\}
>$$
>marginal distribution can be represented by 
>$$
>\pi(A\times X)=\mu(A),\pi(X\times B)=\nu(B)
>$$

>[!def] Wasserstein distance
>Let $(\mathcal{X},d)$ be a Polish metric space and $p\in[1,\infty)$. For any two probability measure $\mu,\nu$ on $\mathcal{X}$, the Wasserstein distance is defined by the formula
>$$
>\begin{aligned}
>W_p(\mu,\nu)&=\left(\inf_{\pi\in\Pi(\mu,\nu)}\int_{X}d(x,y)^p{d}\pi(x,y)\right)^{\frac{1}{p}}\\
>&=\inf\left\{\mathbb{E}[d(X,Y)^p]^{\frac{1}{p}},\text{law}(X)=\mu,\text{law}(Y)=\nu\right\}
>\end{aligned}
>$$

**Proof of $W_p$ satisfies the axioms of a distance**

It is clear that $W_p(\mu,\nu)=W_p(\nu,\mu)$. If $W_p(\mu,\nu)=0$, then there exists a transference plan which is entirely concentrated on the diagonal $y=x$ in $\mathcal{X}\times\mathcal{X}$ denoted by $\Delta$. Therefore, 
$$
\pi(\Delta)=1,\pi(\Delta^c)=0
$$
For any Borel set $A$, 
$$
\mu(A)=\pi(A\times X),\nu(A)=\pi(X\times A)
$$
Note that
$$
(A\times X)\cap\Delta=(X\times A)\cap \Delta
$$
Then 
$$
\mu(A)=\pi(A\times X)=\pi((A\times X)\cap \Delta)=\pi((X\times A)\cap \Delta)=\nu(A)
$$
Hence, $W_p(\mu,\nu)=0\Longleftrightarrow \mu=\nu$. Finally, we W.T.S. the triangle inequality. We need a lemma called **Gluing Lemma**.

>[!lemma] Gluing lemma
>Let $(\mathcal{X}_i, \mu_i), i = 1, 2, 3,$ be Polish probability spaces. If $(X_1, X_2)$ is a coupling of $(\mu_1, \mu_2)$ and $(Y_2, Y_3)$ is a coupling of $(\mu_2, \mu_3)$, then one can construct a triple of random variables $(Z_1, Z_2, Z_3)$ such that $(Z_1, Z_2)$ has the same law as $(X_1, X_2)$ and $(Z_2, Z_3)$ has the same law as $(Y_2, Y_3)$.

Suppose the measure $\mu,\nu,\theta$. $(X_1,X_2)$ is a coupling of $(\mu,\nu)$ and $(Y_2,Y_3)$ is a coupling of $(\nu,\theta)$. By Gluing lemma, there exists $(Z_1,Z_2,Z_3)$ s.t. $(Z_1,Z_2)$ has the sam law as $(X_1,X_2)$ and $(Z_2,Z_3)$ has the same law as $(Y_2,Y_3)$. Then we have 
$$
\begin{aligned}
W_p(\mu,\theta)
\end{aligned}
$$

**QED**

>[!warning] 
>- $W_1$ is called the Kantorovich–Rubinstein distance. 
>- $W_p$ is still not a distance in the strict sense, because it might take the value $+\infty$.

>[!example] 
>For two Dirac measure, there is noly one transport way, 
>$$
>W_p(\delta_x,\delta_y)=d(x,y)
>$$

>[!example] 
>Consider for $\varepsilon\in(0,1)$, the measure $\mu=(1-\varepsilon)\delta_0+\varepsilon\delta_R,\nu=\delta_0$ on $\mathbb{R}$. Compute $W_p(\mu,\nu)$.
>We should find couple and marginal distribution. Since the second marginal distribution is $\delta_0$, we have 
>$$
>\pi(\mathbb{R}\times\{0\})=1
>$$
>For the first marginal distribution, 
>$$
>\pi(\{0\}\times\mathbb{R})=(1-\varepsilon),\pi(\{R\}\times\mathbb{R})=\varepsilon
>$$
>Then the adimissable couple is 
>$$
>\pi=(1-\varepsilon)\delta_{(0,0)}+\varepsilon\delta_{(R,0)}
>$$
>Hence, the Wasserstein distance is computed
>$$
>W_p(x,y)=\left(\int_{\mathbb{R}}|x-y|^p{d}\pi(x,y)\right)^{\frac{1}{p}}=\varepsilon^{\frac{1}{p}} R
>$$

>[!example] 
>We can generalize the above example. If 
>$$
>\mu=\sum_{k=1}^{m}a_k\delta_{x_k},\nu=\sum_{k=1}^{n}b_k\delta_{y_k}
>$$
>Then the Wasserstein distance is 
>$$
>W_p(\mu,\nu)=\left(\min_{\pi_{ij}\ge0}\sum_{i,j=1}d(x_i,y_j)^p\pi_{ij}\right)^{\frac{1}{p}}
>$$
>where $(\pi_{ij})_{m\times n}$ be a matrix satisfying 
>$$
>\sum_{j}\pi_{ij}=a_i,\sum_{i}\pi_{ij}=b_j
>$$

>[!def] Wasserstein space
>