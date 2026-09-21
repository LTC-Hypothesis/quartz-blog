>[!note] 主要工作
>发展了研究FBSDE的第二个方法: 四部框架法。考虑SDE中扩散项非退化的情况即$\sigma$和$Z_t$无关，这一个方法是用一个确定性的“解耦函数”，把强耦合的前向—后向随机微分方程转化为一个抛物型 PDE 和一个前向 SDE，并以此证明任意有限时间区间上的适定性，保证了FBSDE的解能在长时间内存在，克服了之前[[1993-Antonelli Backward-Forward Stochastic Differential Equations|Antonelli只能在小时间区间上存在的局限性]]。

>[!note] 四步框架法
>其目标是要找到形如下面的解，
>$$
>Y_t=u(t,X_t)
>$$
>其中要求$u\in C^{1,2}([0,T]\ti)$