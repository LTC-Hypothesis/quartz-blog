>[!note] 本文的主要工作
>- 1-dim BSDE的存在性，比较原理和稳定性，给的条件为漂移系数$F(t,Y,Z)$连续并且对$Z$有二次增长条件，终端有界。
>- 探究基于扩散过程的BSDE的解与对应半线性偏微分方程的粘性解或Sobolev解之间的联系。

# 带二次增长的BSDE存在性，稳定性和比较原理
两个例子说明对于二次增长条件可以通过**指数变换**消去二次项和为什么需要终端项有界。
>[!example] 

>[!example] 

>[!note] 共同设定与记号（第二节）
> 在通常增广的 $d$ 维布朗滤过 $(\mathcal F_t)_{t\ge0}$ 下，考虑实值倒向随机微分方程。$\tau$ 为停时，$\xi$ 为 $\mathcal F_\tau$-可测的终端随机变量，生成元 $F=F(\omega,t,y,z)$ 关于 $(\omega,t)$ 渐进可测，关于 $(y,z)\in\mathbb R\times\mathbb R^d$ 连续。下文省略随机参数 $\omega$。
>
> 对随机终端时间，解在 $\tau$ 之后延拓为 $Y_t=\xi$、$Z_t=0$，并对任意确定时刻 $0\le t\le T<\infty$ 满足
> $$
> Y_t=Y_T+\int_{t\wedge\tau}^{T\wedge\tau}F(s,Y_s,Z_s)\,ds-\int_{t\wedge\tau}^{T\wedge\tau}Z_s\,dW_s.
> $$
> 记 $\mathcal H_\tau^\infty(\mathbb R)$ 为本质有界的实值渐进可测过程空间，$\mathcal H_\tau^2(\mathbb R^d)$ 为满足
> $$
> \|Z\|_{\mathcal H_\tau^2}^2:=\mathbb E\int_0^\tau|Z_s|^2\,ds<\infty
> $$
> 的 $\mathbb R^d$-值渐进可测过程空间。“局部一致收敛”指生成元关于 $(t,y,z)$ 在 $\mathbb R_+\times\mathbb R\times\mathbb R^d$ 的每个紧集上一致收敛（对几乎所有 $\omega$）。下文的生成元不等式均按几乎处处的意义理解。

>[!thm] 主定理1：存在性（原文定理 2.3，第 565 页）
> **假设。** 给定 BSDE 的参数 $(F,\tau,\xi)$，假设：
>
> 1. **结构与增长条件（H1）。** 存在常数 $\alpha_0,\beta_0\in\mathbb R$、$b\ge0$ 及连续非减函数 $c:\mathbb R_+\to\mathbb R_+$，使得
>    $$
>    F(t,y,z)=a_0(t,y,z)y+F_0(t,y,z),
>    $$
>    且对所有 $(t,y,z)\in\mathbb R_+\times\mathbb R\times\mathbb R^d$，
>    $$
>    \beta_0\le a_0(t,y,z)\le\alpha_0,\qquad
>    |F_0(t,y,z)|\le b+c(|y|)|z|^2.\tag{H1}
>    $$
> 2. **终端条件有界。** $\xi\in L^\infty(\Omega,\mathcal F_\tau,\mathbb P)$。
> 3. **终端时间。** 以下两种情形至少有一种成立：
>    - 存在确定常数 $T<\infty$，使得 $\tau\le T$ 几乎处处成立；
>    - $\tau<\infty$ 几乎处处成立，且 $\alpha_0<0$（一致耗散条件）。
>
> **结论。** 该 BSDE 至少存在一个解
> $$
> (Y,Z)\in\mathcal H_\tau^\infty(\mathbb R)\times\mathcal H_\tau^2(\mathbb R^d),
> $$
> 且 $Y$ 具有连续样本路径。
>
> 此外，存在最小解 $(Y_*,Z_*)$ 和最大解 $(Y^*,Z^*)$：对该方程的任意解 $(Y,Z)$，均有 $Y_*\le Y\le Y^*$。更一般地，对具有相同终端时间的参数 $(G,\tau,\zeta)$ 及其上述解空间中的任意解 $(Y^G,Z^G)$，有
> $$
> F\le G,\quad\xi\le\zeta\quad\Longrightarrow\quad Y_*\le Y^G,
> $$
> $$
> F\ge G,\quad\xi\ge\zeta\quad\Longrightarrow\quad Y^*\ge Y^G.
> $$
> **说明。** 本定理只保证存在性及最大、最小解的存在，不保证唯一性；唯一性还需要比较原理的附加假设。

>[!thm] 主定理2：单调稳定性（原文命题 2.4，第 565–566 页）
> **假设。** 给定参数 $(F,\tau,\xi)$ 及参数序列 $(F^n,\tau,\xi^n)_{n\ge1}$，假设：
>
> 1. **数据收敛。** $F^n\to F$ 在 $\mathbb R_+\times\mathbb R\times\mathbb R^d$ 上局部一致收敛；对每个 $n$，$\xi^n\in L^\infty(\Omega,\mathcal F_\tau,\mathbb P)$，且
>    $$
>    \|\xi^n-\xi\|_{L^\infty(\Omega)}\longrightarrow0.
>    $$
> 2. **一致的二次增长控制。** 存在非负确定性函数 $k\in L^1_{\mathrm{loc}}(\mathbb R_+)$ 及常数 $C>0$，二者均与 $n$ 无关，使得对所有 $n,t,y,z$，
>    $$
>    |F^n(t,y,z)|\le k(t)+C|z|^2.
>    $$
>    这里 $k\in L^1_{\mathrm{loc}}(\mathbb R_+)$ 即对每个有限 $T>0$，$\int_0^T k(s)\,ds<\infty$。
> 3. **近似解存在、单调且一致有界。** 对每个 $n$，参数为 $(F^n,\tau,\xi^n)$ 的 BSDE 存在解
>    $$
>    (Y^n,Z^n)\in\mathcal H_\tau^\infty(\mathbb R)\times\mathcal H_\tau^2(\mathbb R^d).
>    $$
>    序列 $(Y^n)_n$ 关于 $n$ 单调（整体单调递增或整体单调递减），并且存在与 $n$ 无关的常数 $M>0$，使得
>    $$
>    \sup_{n\ge1}\|Y^n\|_\infty\le M.
>    $$
> 4. **终端时间有限。** $\tau<\infty$ 几乎处处成立。
>
> **结论（按原文陈述）。** 存在参数为 $(F,\tau,\xi)$ 的 BSDE 的解
> $$
> (Y,Z)\in\mathcal H_\tau^\infty(\mathbb R)\times\mathcal H_\tau^2(\mathbb R^d),
> $$
> 使得对任意有限 $T>0$，
> $$
> \sup_{0\le t\le T}|Y_t^n-Y_t|\longrightarrow0\quad\text{几乎处处},
> $$
> 并且
> $$
> \mathbb E\int_0^\tau|Z_s^n-Z_s|^2\,ds\longrightarrow0.
> $$
> 若每个 $Y^n$ 都具有连续样本路径，则 $Y$ 也具有连续样本路径。
>
> **说明。** 此处要求单调的是解序列 $(Y^n)_n$，而不是直接要求生成元序列 $(F^n)_n$ 单调。极限生成元不必满足比较原理，因此本命题所得极限解不一定唯一。

>[!thm] 主定理3：比较原理（原文定理 2.6，第 575 页）
> **假设。** 给定两组参数 $(F^1,\tau,\xi^1)$、$(F^2,\tau,\xi^2)$，其中终端条件有界，假设：
>
> 1. **数据有序。** $\xi^1\le\xi^2$ 几乎处处成立，且
>    $$
>    F^1(t,y,z)\le F^2(t,y,z)
>    $$
>    对所有 $(t,y,z)$ 几乎处处成立。
> 2. **至少一个生成元满足（H2）与（H3）。** $F^1$ 或 $F^2$ 中至少有一个（以下记为 $F^i$）关于 $(y,z)$ 局部 Lipschitz 连续，并具有如下性质：对任意 $M>0$、$\varepsilon>0$，存在时间函数
>    $$
>    l,l_\varepsilon\in L_\tau^1,\qquad k\in L_\tau^2
>    $$
>    以及常数 $C>0$，使得对所有 $t\ge0$、$|y|\le M$、$z\in\mathbb R^d$，
>    $$
>    \begin{aligned}
>    |F^i(t,y,z)|&\le l(t)+C|z|^2,\\
>    |\partial_zF^i(t,y,z)|&\le k(t)+C|z|
>    \end{aligned}\tag{H2}
>    $$
>    且
>    $$
>    \partial_yF^i(t,y,z)\le l_\varepsilon(t)+\varepsilon|z|^2.\tag{H3}
>    $$
>    偏导数按局部 Lipschitz 函数几乎处处可微的意义理解。$L_\tau^1,L_\tau^2$ 沿用原文关于终端时间的时间可积性记号；当 $\tau=T$ 为确定常数时，分别为 $L^1(0,T)$、$L^2(0,T)$。这些控制量可依赖于所选有界区间及 $\varepsilon$，但不能依赖于 $y,z$；条件（H3）要求对每个 $\varepsilon>0$ 成立。
> 3. **已有次解与上解。** $(Y^1,Z^1,A^1)$ 是第一组参数的次解，$(Y^2,Z^2,A^2)$ 是第二组参数的上解，其中
>    $$
>    Y^i\in\mathcal H_\tau^\infty(\mathbb R),\qquad Z^i\in\mathcal H_\tau^2(\mathbb R^d),
>    $$
>    $A^i$ 为适应、右连续、递增的过程。为明确符号，对任意确定时刻 $0\le t\le T$，次解满足
>    $$
>    \begin{aligned}
>    Y_t^1={}&Y_T^1+\int_{t\wedge\tau}^{T\wedge\tau}F^1(s,Y_s^1,Z_s^1)\,ds
>    -\int_{t\wedge\tau}^{T\wedge\tau}Z_s^1\,dW_s\\
>    &-(A^1_{T\wedge\tau}-A^1_{t\wedge\tau}),
>    \end{aligned}
>    $$
>    上解满足同样形式的等式，但递增过程的增量前取正号。两者在 $\tau$ 之后分别取终端值 $\xi^1,\xi^2$。
>
> **结论。** 对所有 $t\ge0$，
> $$
> Y_t^1\le Y_t^2\quad\text{几乎处处}.
> $$
> **唯一性推论。** 若同一生成元满足上述（H2）、（H3），则相同终端条件对应的 BSDE 在 $\mathcal H_\tau^\infty\times\mathcal H_\tau^2$ 中至多有一个解。该定理本身不承担存在性的证明。
>
> **补充（原文注 2.7）。** 全局的生成元序关系可以减弱为沿一个解轨道的序关系：若 $F^2$ 满足（H2）、（H3），只需 $F^1(t,Y_t^1,Z_t^1)\le F^2(t,Y_t^1,Z_t^1)$；若 $F^1$ 满足这些条件，只需 $F^1(t,Y_t^2,Z_t^2)\le F^2(t,Y_t^2,Z_t^2)$。

>[!thm] 主定理4：稳定性（原文定理 2.8，第 575–576 页）
> **假设。** 给定具有相同终端时间的参数序列 $(F^n,\tau,\xi^n)_{n\ge1}$ 及极限参数 $(F,\tau,\xi)$，假设：
>
> 1. **统一的结构与增长条件（H1）。** 存在与 $n$ 无关的常数 $\alpha_0,\beta_0\in\mathbb R$、$b\ge0$ 及连续非减函数 $c:\mathbb R_+\to\mathbb R_+$，使得对每个 $n$，
>    $$
>    F^n(t,y,z)=a_0^n(t,y,z)y+F_0^n(t,y,z),
>    $$
>    $$
>    \beta_0\le a_0^n(t,y,z)\le\alpha_0,\qquad
>    |F_0^n(t,y,z)|\le b+c(|y|)|z|^2.
>    $$
> 2. **近似方程已有解。** 对每个 $n$，参数为 $(F^n,\tau,\xi^n)$ 的 BSDE 存在解
>    $$
>    (Y^n,Z^n)\in\mathcal H_\tau^\infty(\mathbb R)\times\mathcal H_\tau^2(\mathbb R^d).
>    $$
> 3. **极限生成元满足比较原理的条件。** $F$ 关于 $(y,z)$ 局部 Lipschitz 连续；对任意 $M,\varepsilon>0$，存在 $l,l_\varepsilon\in L_\tau^1$、$k\in L_\tau^2$ 及 $C>0$，使得对所有 $t\ge0$、$|y|\le M$、$z\in\mathbb R^d$，
>    $$
>    \begin{aligned}
>    |F(t,y,z)|&\le l(t)+C|z|^2,\\
>    |\partial_zF(t,y,z)|&\le k(t)+C|z|,\\
>    \partial_yF(t,y,z)&\le l_\varepsilon(t)+\varepsilon|z|^2.
>    \end{aligned}
>    $$
>    即极限生成元 $F$ 满足定理 2.6 中的（H2）、（H3），其中时间可积性记号与主定理3一致。
> 4. **数据收敛。** $F^n\to F$ 在 $\mathbb R_+\times\mathbb R\times\mathbb R^d$ 上局部一致收敛，$\xi^n,\xi\in L^\infty(\Omega,\mathcal F_\tau,\mathbb P)$，且
>    $$
>    \|\xi^n-\xi\|_{L^\infty(\Omega)}\longrightarrow0.
>    $$
>
> **结论（按原文陈述）。** 极限 BSDE 存在唯一解
> $$
> (Y,Z)\in\mathcal H_\tau^\infty(\mathbb R)\times\mathcal H_\tau^2(\mathbb R^d),
> $$
> 并且对任意有限 $T>0$，
> $$
> \sup_{0\le t\le T}|Y_t^n-Y_t|\longrightarrow0\quad\text{几乎处处},
> $$
> 以及
> $$
> \mathbb E\int_0^\tau|Z_s^n-Z_s|^2\,ds\longrightarrow0.
> $$
> **说明。** 本定理不要求 $(Y^n)_n$ 单调，也不要求每个 $F^n$ 都满足比较原理；（H2）、（H3）施加于极限生成元 $F$，使所有可能的极限由唯一性确定为同一个解。
>
> **终端时间的上下文。** 原文定理 2.8 的条文未再次单列定理 2.3 的终端时间条件。通过定理 2.3 构造近似解并利用推论 2.2 取得一致先验界时，应同时核对：$\tau$ 有界，或 $\tau<\infty$ 几乎处处且统一的 $\alpha_0<0$。这属于应用时对前文存在性框架的核对，与上面逐项列出的原文假设加以区分。
# BSDE和PDE
