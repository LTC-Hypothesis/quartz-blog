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
>Let $(X,d)$ be a Polish metric space and $p\in[1,\infty)$. For any two probability measure $\mu,\nu$ on $X$, the Wasserstein distance is defined by the formula
>$$
>\begin{aligned}
>W_p(\mu,\nu)&=\left(\inf_{\pi\in\Pi(\mu,\nu)}\int_{X}d(x,y)^p{d}\pi(x,y)\right)^{\frac{1}{p}}\\
>&=\inf\left\{\mathbb{E}[d(X,Y)^p]^{\frac{1}{p}},\text{law}(X)=\mu,\text{law}(Y)=\nu\right\}
>\end{aligned}
>$$

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

