>[!note] 主要工作
>发展了研究FBSDE的第二个方法: 四部框架法。考虑SDE中扩散项非退化的情况即$\sigma$和$Z_t$无关，
>$$
>\begin{cases}
>X_t=x+\int_{0}^{t}b(s,X_s,Y_s,Z_s){d}s+\int_{0}^{t}\sigma(s,X_s,Y_s){d}W_s\\
>Y_t=g(X_T)+\int_{t}^{T}\hat{b}(s,X_s,Y_s,Z_s){d}s+\int_{t}^{T}\hat{\sigma}(s,X_s,Y_s,Z_s){d}W_s
>\end{cases}
>$$
>这一个方法是用一个确定性的“解耦函数”，把强耦合的前向—后向随机微分方程转化为一个抛物型 PDE 和一个前向 SDE，并以此证明任意有限时间区间上的适定性，保证了FBSDE的解能在长时间内存在，克服了之前[[1993-Antonelli Backward-Forward Stochastic Differential Equations|Antonelli只能在小时间区间上存在的局限性]]。

>[!note] 四步框架法
>其目标是要找到形如下面的解，
>$$
>Y_t=u(t,X_t)
>$$
>其中要求$u(t,x)\in C^{1,2}([0,T]\times\mathbb{R}^n)$以保证能使用It$\hat{\text{o}}$公式。实际上就是使用It$\hat{\text{o}}$公式，然后和$Y_t$满足的倒向方程的系数进行比对，得到$u$满足的PDE，经过求解这个PDE从而得到FBSDE的解。那么经过下面四个步骤进行计算，就可以找到这样的解，
>**Step1: 求解一个代数方程得到$z(t,x,y,p)$** 满足
>$$
>p\sigma(t,x,y)+\hat{\sigma}(t,x,y,z(t,x,y,p))=0
>$$
>**Step2：用得到的$z$求解拟线性抛物型PDE**
>$$
>\begin{cases}
>u_t+\frac{1}{2}\text{tr}(u_{xx}\sigma(t,x,u)\sigma(t,x,u)^\top)+\langle b(t,x,u,z),u_x\rangle+\hat{b}(t,x,u,z)=0\\
>u(T,x)=g(x)
>\end{cases}
>$$
>**Step3：得到$u$之后只剩下求解SDE的解就可以得到$Y_t$和$Z_t$** 实际上还是把$Y_t=u(t,X_t)$代入到SDE中求解。
>**Step4：** 令$Y_t=u(t,X_t),Z_t=z(t,X_t,u(t,X_t),u_x(t,X_t))$

>[!warning] 局限性
>局限性其实非常明显，中间过程要求解一个拟线性抛物型偏微分方程，就需要非常多的正则性假设以保证PDE的解存在，详细可以看假设(A1)-(A4)。