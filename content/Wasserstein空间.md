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
>- $W_p$ is 

>[!example] 
>