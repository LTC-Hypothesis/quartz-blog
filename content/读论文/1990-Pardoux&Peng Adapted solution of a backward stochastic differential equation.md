# 梦开始的地方

>[!note] 研究主题
>完全非线性倒向随机微分方程(BSDE)解的存在唯一性，
>$$
>x(t)+\int_{t}^{1}f(s,x(s),y(s)){d}s+\int_{t}^{1}[g(s,x(s),y(s))]{d}W_s=X\tag{1}
>$$
>实际上方程（1）是推广情形，随机控制理论中常见的BSDE是线性化后的，
>$$
>x(t)+\int_{t}^{1}f(s,x(s),y(s)){d}s+\int_{t}^{1}[g(s,x(s))+y(s))]{d}W_s=X\tag{2}
>$$

>[!thm] 主定理
>现有以下基本假设，
>1. $X\in L^2(\Omega,\mathscr{F}_1,\mathbb{P};\mathbb{R}^d)$，$f,g:\Omega\times\mathbb{R}^d\times\mathbb{R}^{d\times k}\to\mathbb{R}^d(\mathbb{R}^{d\times k})$关于$\mathscr{F}\otimes\mathscr{B}^d\otimes\mathscr{B}^{d\times k}/\mathscr{B}^{d}(\mathscr{B}^{d\times k})$可测，并且满足
>  $$
>  f(\cdot,0,0)\in M(0,1;\mathbb{R}^d),g(\cdot,0,0)\in M^2(0,1;\mathbb{R}^{d\times k}) 
>  $$
>2. Lipschitz条件：
>   $$
>  |f()| 
>  $$