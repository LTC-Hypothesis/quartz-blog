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
>  |f(t,x_1,y_1)-f(t,x_2,y_2)|+|g(t,x_1,y_1)-g(t,x_2,y_2)|\le c(|x_1-x_2|+|y_1-y_2|) 
>  $$
> 3. $g$一致Lipschitz连续，
>    $$
>   |g(t,x,y_1)-g(t,x,y_2)|\ge\alpha|y_1-y_2| 
>   $$
>  
>则存在唯一解$(x,y)\in M_2(0,1;\mathbb{R}^d)\times M_2(0,1;\mathbb{R}^{d\times k})$。

>[!note] 证明的思路，方法和顺序
>- 证明思路：循循渐进，从简化的方程开始研究。Step1考虑的方程为
>  $$
>  x(t)+\int_{t}^{1}f(s){d}s+\int_{t}^{1}g(s)+y(s){d}s=X\tag{3}
>  $$
>  Step2考虑线性化的方程
>  $$
>  x(t)+\int_{t}^{1}f(s,y(s)){d}s+\int_{t}^{1}[g(s)+y(s)]{d}s=X\tag{4}
>  $$
>接下来才考虑方程（2）和（1）。
>- 主要方法：对简化的情形使用Picard迭代，这个在[[Strong solutions#^d1379b|证明SDE和ODE的存在唯一性]]都有用到。还有一个重要的定理是[[Representations of Continuous Martingales in Terms of Brownian Motion|鞅表示定理]]。

