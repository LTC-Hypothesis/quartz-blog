---
publish: 2013
tag: 随机控制, BSDE, FBSDE, 最大值原理, 动态规划, HJB
---

>[!note] 文献信息
>Jingtao Shi & Zhiyong Yu. *Relationship between Maximum Principle and Dynamic Programming for Stochastic Recursive Optimal Control Problems and Applications*. **Mathematical Problems in Engineering**, 2013, Article ID 285241, 12 pages.
>
>[DOI / 期刊原文](https://doi.org/10.1155/2013/285241)。阅读整理：2026-10-23。以下页码为论文自身页码；数字公式编号对应原文，带文字的编号为本笔记补充。

>[!note] 本文的主要工作
>- 在**确定性系数、凸控制域、价值函数足够光滑**的随机递归控制框架下，建立最大值原理（MP）的伴随过程与动态规划（DPP）的价值函数导数之间的关系。
>- 核心公式为沿最优轨道的$p=qV_x$及$k=q(V_{xx}\bar\sigma+V_x\bar f_z^\top)$；$q$是由生成元对$y,z$的导数决定的正随机积分因子。
>- 在已有必要最大值原理基础上，给出附加凸性和线性终端条件下的充分性结果；用一个LQ递归效用投资组合模型比较MP与HJB两条求解路线。
>- 本文没有证明一般价值函数的光滑性，也没有处理价值函数不光滑时的MP–DPP关系。不能将本文公式直接作为一般粘性解情形的结论。

>[!note] 查用入口
>- 模型、符号与假设：[[#问题与基本假设]]。
>- MP与HJB的具体形式：[[#动态规划与最大值原理]]。
>- 直接引用主定理：[[#主定理：MP与DPP的关系]]。
>- 可复用证明方法：[[#主定理的证明路线]]。
>- LQ模型与反馈公式：[[#应用：递归效用投资组合]]。
>- 原文问题及修正：[[#原文核查与使用边界]]。

# 问题与基本假设

>[!def] 受控FBSDE与递归控制问题（第2–3页，式(1)–(6)）
>固定$(t,x)\in[0,T)\times\mathbb R^n$，$W$为$d$维Brownian motion，控制域$U\subseteq\mathbb R^m$非空且凸。考虑
>$$
>\begin{cases}
>{d}X_s=b(s,X_s,u_s){d}s+\sigma(s,X_s,u_s){d}W_s,\\
>-{d}Y_s=f(s,X_s,Y_s,Z_s,u_s){d}s-Z_s^\top{d}W_s,\\
>X_t=x,\qquad Y_T=\Phi(X_T).
>\end{cases}\tag{1,3}
>$$
>其中$X\in\mathbb R^n$，$Y\in\mathbb R$，$Z\in\mathbb R^d$，$\sigma\in\mathbb R^{n\times d}$。$b,\sigma,f,\Phi$为确定性函数；前向系数不依赖于$(Y,Z)$，因此这里不是一般全耦合FBSDE。
>
>控制适应于从$t$开始的Brownian增量生成的通常增广滤过$\mathbb F^t$；用$\mathscr U[t,T]$表示可容许控制。原文对控制空间的可积性写得简略，使用时须保证状态、BSDE及下述期望、随机积分有意义。
>$$
>J(t,x;u):=-Y_t^{t,x;u},\qquad
>V(t,x):=\inf_{u\in\mathscr U[t,T]}J(t,x;u),\qquad V(T,x)=-\Phi(x).\tag{5,6}
>$$
>在本文的确定性系数与控制框架下，$V$为确定性函数。最优四元组记为$(\bar X,\bar Y,\bar Z,\bar u)$。

>[!warning] 符号约定
>本文最小化的是$-Y_t$。沿最优轨道应记住
>$$
>\bar Y_s=-V(s,\bar X_s),\qquad
>\bar Z_s=-\bar\sigma_s^\top V_x(s,\bar X_s).
>$$
>本笔记统一将$V_x,f_x,f_z,\Phi_x$写为列向量，将$Z_s^\top{d}W_s$写成标量随机积分；原文部分转置记法不统一。用$\sigma^j$表示$\sigma$的第$j$列，$\sigma_x^j$为其Jacobi矩阵。

>[!def] 基本假设（H1）–（H3）的查用版本
>**（H1）前向系数。** $b,\sigma$一致连续，对$(x,u)$一致Lipschitz，且原文要求对$u$一致的线性增长界：
>$$
>\begin{aligned}
>&|b(s,x,u)-b(s,x',u')|+|\sigma(s,x,u)-\sigma(s,x',u')|\\
>&\qquad\le C(|x-x'|+|u-u'|),\\
>&|b(s,x,u)|+|\sigma(s,x,u)|\le C(1+|x|).
>\end{aligned}
>$$
>**（H2）后向系数。** $f,\Phi$一致连续，$f$对$(x,y,z,u)$一致Lipschitz，$\Phi$对$x$一致Lipschitz，并满足
>$$
>\begin{aligned}
>&|f(s,x,y,z,u)-f(s,x',y',z',u')|\\
>&\qquad\le C(|x-x'|+|y-y'|+|z-z'|+|u-u'|),\\
>&|f(s,x,0,0,u)|+|\Phi(x)|\le C(1+|x|),\\
>&|\Phi(x)-\Phi(x')|\le C|x-x'|.
>\end{aligned}
>$$
>**（H3）可微性。** $b,\sigma$对$(x,u)$连续可微，$f$对$(x,y,z,u)$连续可微，$\Phi$对$x$连续可微；$b_x,\sigma_x,f_x,f_y,f_z,b_u,\sigma_u,f_u$有界，且
>$$
>|\Phi_x(x)|\le C(1+|x|).
>$$
>这是主定理的系数假设。$V$的额外光滑性另行假设，不能由这些条件直接推出。

# 动态规划与最大值原理

>[!def] 广义Hamiltonian与HJB（第3页，式(7)–(8)）
>为避免与伴随过程$p$混淆，将$G$的梯度参数记为$\xi$：
>$$
>G(s,x,r,\xi,A,u)
>=\frac12\operatorname{tr}(\sigma^\top A\sigma)
>+\langle\xi,b\rangle+f(s,x,r,\sigma^\top\xi,u).
>$$
>其中$b,\sigma$在$(s,x,u)$处取值。HJB方程为
>$$
>\begin{cases}
>-v_s(s,x)+\displaystyle\sup_{u\in U}G(s,x,-v,-v_x,-v_{xx},u)=0,\\
>v(T,x)=-\Phi(x).
>\end{cases}\tag{7}
>$$
>原文Lemma 2是相应的光滑验证定理：在运算与比较合法的解类内，经典解$v$满足$v(t,x)\le J(t,x;u)$；若某可容许控制沿自身轨道实现HJB上确界，则该控制最优并有$v(t,x)=V(t,x)$。式(11)的原证明需补足BSDE比较步骤，见[[#原文核查与使用边界]]。

>[!def] MP Hamiltonian与伴随方程（第4页，式(17)–(18)）
>定义
>$$
>H(s,x,y,z,u,p,q,k)=\langle p,b(s,x,u)\rangle-qf(s,x,y,z,u)+\operatorname{tr}(\sigma(s,x,u)^\top k).\tag{18}
>$$
>$p\in\mathbb R^n$，$q\in\mathbb R$，$k\in\mathbb R^{n\times d}$。横线表示沿$(\bar X,\bar Y,\bar Z,\bar u)$取值，例如$\bar f_y(s)=f_y(s,\bar X_s,\bar Y_s,\bar Z_s,\bar u_s)$。伴随方程为
>$$
>\begin{cases}
>-{d}p_s=\left[\bar b_x^\top p_s-\bar f_xq_s+\displaystyle\sum_{j=1}^d(\bar\sigma_x^j)^\top k_s^j\right]{d}s-k_s{d}W_s,\\
>{d}q_s=\bar f_yq_s{d}s+q_s\bar f_z^\top{d}W_s,\\
>p_T=-\Phi_x(\bar X_T)q_T,\qquad q_t=1.
>\end{cases}\tag{17}
>$$
>前向未知量是$q$，后向未知量是$(p,k)$。$G$与$H$不是同一个函数，不能混用。

>[!lemma] 必要最大值原理（Lemma 3，第5页）
>在（H1）–（H3）下，若$\bar u$最优，则
>$$
>\left\langle H_u(s,\bar X_s,\bar Y_s,\bar Z_s,\bar u_s,p_s,q_s,k_s),u-\bar u_s\right\rangle\ge0,\qquad\forall u\in U,\tag{19}
>$$
>按${d}s\otimes\mathbb P$几乎处处理解。这是凸控制域上的一阶变分必要条件；按照本文$J,H$的符号，它呈现极小化的一阶条件。一般不能仅凭此条件断言全局最优。

>[!lemma] 充分最大值原理（Lemma 4，第5–6页）
>在（H1）–（H3）下，给定可容许四元组及其伴随过程，进一步假定终端函数为线性函数$\Phi(x)=M_T^\top x$，且对固定伴随变量，$H$关于$(x,y,z,u)$联合凸。若该控制满足(19)，则其最优。
>
>原文的线性终端条件是充分性证明中消去终端差项的条件；不能在引用此引理时直接换成任意非线性$\Phi$。

**Proof（式(21)–(22)的机制）**

固定时间，记$\Delta X=\bar X-X^u$、$\Delta Y=\bar Y-Y^u$、$\Delta Z=\bar Z-Z^u$；$\bar H,H^u$使用同一组$(p,q,k)$。对$\Delta Yq+\langle\Delta X,p\rangle$应用Itô公式，终端项与初始状态差项消失，得到
$$
J(t,x;\bar u)-J(t,x;u)
=\mathbb E\int_t^T\left[\bar H-H^u-\langle\bar H_x,\Delta X\rangle-\bar H_y\Delta Y-\langle\bar H_z,\Delta Z\rangle\right]{d}s.\tag{21}
$$
最后一个等号仅是代入$H$的定义：
$$
\begin{aligned}
\bar H-H^u&=\langle p,\bar b-b^u\rangle-q(\bar f-f^u)+\operatorname{tr}((\bar\sigma-\sigma^u)^\top k),\\
\bar H_x&=\bar b_x^\top p-q\bar f_x+\sum_j(\bar\sigma_x^j)^\top k^j,\\
\bar H_y&=-q\bar f_y,\qquad\bar H_z=-q\bar f_z.
\end{aligned}
$$
由联合凸性，
$$
H^u\ge\bar H-\langle\bar H_x,\Delta X\rangle-\bar H_y\Delta Y-\langle\bar H_z,\Delta Z\rangle+\langle\bar H_u,u-\bar u\rangle.
$$
代入(21)，再用(19)，便有
$$
J(t,x;\bar u)-J(t,x;u)
\le\mathbb E\int_t^T\langle\bar H_u,\bar u-u\rangle{d}s\le0.\tag{22}
$$
**QED**

# 主定理：MP与DPP的关系

>[!thm] Theorem 5（第6–8页，式(23)–(25)）
>设（H1）–（H3）成立，固定$(t,x)$，最优四元组$(\bar X,\bar Y,\bar Z,\bar u)$存在，$(p,q,k)$满足伴随方程(17)。
>
>**第一层：HJB沿最优轨道取等号。** 若$V\in C^{1,2}([0,T]\times\mathbb R^n)$，则
>$$
>\begin{aligned}
>V_s(s,\bar X_s)
>&=G(s,\bar X_s,-V,-V_x,-V_{xx},\bar u_s)\\
>&=\max_{u\in U}G(s,\bar X_s,-V,-V_x,-V_{xx},u),
>\end{aligned}\tag{23}
>$$
>其中$V,V_x,V_{xx}$均在$(s,\bar X_s)$处取值，等式按${d}s\otimes\mathbb P$几乎处处理解。这里的最大值因已给定最优控制而沿该轨道达到，不是在一般非紧$U$上预先保证所有点都有最大元。
>
>**第二层：伴随过程的表示。** 若进一步$V\in C^{1,3}$且$V_{sx}$连续，则
>$$
>\begin{aligned}
>p_s&=q_sV_x(s,\bar X_s),\\
>k_s&=q_s\left[V_{xx}(s,\bar X_s)\bar\sigma_s+V_x(s,\bar X_s)\bar f_z(s)^\top\right],
>\end{aligned}\tag{24}
>$$
>其中
>$$
>q_s=\exp\left\{\int_t^s\left(\bar f_y(r)-\frac12|\bar f_z(r)|^2\right){d}r+\int_t^s\bar f_z(r)^\top{d}W_r\right\}>0.\tag{25}
>$$
>$p$的等式可取连续版本对所有$s\in[t,T]$同时成立；$k$的等式按${d}s\otimes\mathbb P$几乎处处理解。由$\bar Y=-V$与$\bar Z=-\bar\sigma^\top V_x$，(25)可完全写成沿最优轨道的$V,V_x$表达式。

>[!note] 公式的含义与退化情形
>$$
>\frac{p_s}{q_s}=V_x(s,\bar X_s),\qquad
>\frac{k_s}{q_s}-V_x(s,\bar X_s)\bar f_z^\top=V_{xx}(s,\bar X_s)\bar\sigma_s.
>$$
>$q$消去递归生成元的$f_y,f_z$项，是随机积分因子；$V_x\bar f_z^\top$是乘积扩散项带来的修正。
>
>若$f_y=f_z=0$，则$q\equiv1$，恢复$p=V_x$、$k=V_{xx}\bar\sigma$。若仅$f_z=0$，则$q_s=\exp(\int_t^s\bar f_y{d}r)$，一般仍可能随机；只有沿轨道的$\bar f_y$也是确定性时，$q$才是确定性函数。

# 主定理的证明路线

**Proof**

**Step1：DPP识别$\bar Y$，BSDE和鞅表示识别$\bar Z$。**

最优延续性质给出$V(s,\bar X_s)=-\bar Y_s$。将BSDE从$s$积分到$T$，取$\mathcal F_s^t$条件期望，得到
$$
V(s,\bar X_s)=-\bar Y_s
=-\mathbb E\left[\Phi(\bar X_T)+\int_s^T\bar f(r){d}r\,\middle|\,\mathcal F_s^t\right].\tag{26}
$$
前一个等号使用DPP与最优性；后一个等号使用适应性和随机积分的鞅性质。因为$\bar f$含有$(\bar Y,\bar Z)$，后者通常是隐式表示，并非把非线性BSDE显式解出。

原文定义平方可积鞅
$$
m_s=-\mathbb E\left[\Phi(\bar X_T)+\int_t^T\bar f(r){d}r\,\middle|\,\mathcal F_s^t\right],
\qquad {d}m_s=M_s^\top{d}W_s.
$$
由(26)，$V(s,\bar X_s)=m_s+\int_t^s\bar f(r){d}r$。另一方面，Itô公式给出
$$
{d}V(s,\bar X_s)
=\left[V_s+\langle V_x,\bar b\rangle+\frac12\operatorname{tr}(\bar\sigma\bar\sigma^\top V_{xx})\right]{d}s+V_x^\top\bar\sigma{d}W_s.
$$
比较半鞅分解，得到
$$
V_s+\langle V_x,\bar b\rangle+\frac12\operatorname{tr}(\bar\sigma\bar\sigma^\top V_{xx})=\bar f,
\qquad\bar Z_s=-\bar\sigma_s^\top V_x(s,\bar X_s).\tag{31,32}
$$
结合HJB即可得到(23)。

**Step2：固定最优控制的取值，对HJB残差求状态导数。**

固定使(23)成立的$(s,\omega)$，定义
$$
F(x)=-V_s(s,x)+G(s,x,-V(s,x),-V_x(s,x),-V_{xx}(s,x),\bar u_s(\omega)).
$$
由HJB，对所有$x$都有$F(x)\le0$；由最优性，$F(\bar X_s(\omega))=0$。因此该点为可微函数$F$的极大点，
$$
F_x(\bar X_s(\omega))=0.\tag{33,34}
$$
求导时固定$\bar u_s(\omega)$，**不对反馈控制$u^*(s,x)$求导**，因而不要求最优反馈关于$x$可微。这一步也解释了为什么需要$V_{xxx}$和$V_{sx}$。

**Step3：对$V_x(s,\bar X_s)$用Itô公式，再乘以$q_s$。**

为了看清抵消，先写$n=d=1$的计算。记
$$
A_s=V_x(s,\bar X_s),\qquad B_s=V_{xx}(s,\bar X_s)\bar\sigma_s.
$$
展开$F_x=0$并代入Itô公式，有
$$
{d}A_s=\left[-\bar b_xA_s-\bar\sigma_xB_s+\bar f_x-\bar f_yA_s-\bar f_z(\bar\sigma_xA_s+B_s)\right]{d}s+B_s{d}W_s.\tag{37}
$$
定义候选伴随过程
$$
\widetilde p_s=q_sA_s,\qquad\widetilde k_s=q_s(B_s+A_s\bar f_z).
$$
由乘积公式，
$$
{d}(qA)=q{d}A+A{d}q+{d}[q,A],\qquad {d}[q,A]_s=q_s\bar f_zB_s{d}s.
$$
其中$-q\bar f_yA$与$Aq\bar f_y$抵消，$-q\bar f_zB$与协变差项$q\bar f_zB$抵消。剩余部分为
$$
{d}\widetilde{p}_s=\left[-\bar{b}_x\widetilde{p}_s+\bar{f}_xq_s-\bar{\sigma}_x\widetilde{ k_s}\right]{d}s+\widetilde{k_s}{d}W_s.\tag{38}
$$
又有$\widetilde p_T=q_TV_x(T,\bar X_T)=-q_T\Phi_x(\bar X_T)$，因此候选过程满足伴随BSDE。多维时逐列计算扩散项，得到(24)。

**Step4：使用伴随方程解的唯一性。**

在候选过程属于相应解空间、Itô与取期望运算合法的前提下，由唯一性得到$(\widetilde p,\widetilde k)=(p,k)$。实际推广时应同时核对导数的增长、可积性，必要时先停时局部化再去局部化；不能只做形式计算便跳过解空间核查。

**QED**

>[!note] 两种控制一阶条件的对应（由主定理直接计算）
>令$\mathcal G(s,x,u)=G(s,x,-V,-V_x,-V_{xx},u)$。在最优轨道代入(24)，并将状态、伴随变量固定，有
>$$
>H_u(s,\bar X_s,\bar Y_s,\bar Z_s,\bar u_s,p_s,q_s,k_s)
>=-q_s\mathcal G_u(s,\bar X_s,\bar u_s).
>$$
>因为$q_s>0$，HJB最大化的一阶条件$\langle\mathcal G_u,u-\bar u\rangle\le0$转化为MP条件(19)。这是沿最优轨道的一阶对应，不表示$H$与$G$在所有控制值处成比例，也不表示一阶条件一般足以给出全局最优。

# 应用：递归效用投资组合

>[!def] 一维LQ模型（第8–9页，式(41)、(48)–(49)）
>$\rho_s$为无风险利率，$\mu_s$为风险资产收益率，$\sigma_s$为其波动率。原文取有界确定性系数、$\sigma_s\ne0$、$\mu_s>\rho_s$，$\beta\ge0$。$u_s$为投在风险资产上的金额，控制域$U=\mathbb R$。
>$$
>\begin{cases}
>{d}X_s=[\rho_sX_s+(\mu_s-\rho_s)u_s]{d}s+\sigma_su_s{d}W_s,\\
>-{d}Y_s=[\rho_sX_s+(\mu_s-\rho_s)u_s-\beta Y_s]{d}s-Z_s{d}W_s,\\
>X_t=x,\qquad Y_T=-\dfrac12(X_T-a)^2,
>\end{cases}\tag{48}
>$$
>$$
>J(t,x;u)=-Y_t,\qquad V(t,x)=\inf_uJ(t,x;u).
>$$
>这里$a$为给定的终端目标参数。本文求解的是这个固定参数的辅助控制问题；不能把它直接等同于已经求解给定期望约束的原始均值–方差问题。

## MP路线：线性伴随方程与仿射猜测

Hamiltonian与伴随方程为
$$
H=p[\rho_sx+(\mu_s-\rho_s)u]-q[\rho_sx+(\mu_s-\rho_s)u-\beta y]+k\sigma_su,
$$
$$
\begin{cases}
-{d}p_s=\rho_s(p_s-q_s){d}s-k_s{d}W_s,\\
{d}q_s=-\beta q_s{d}s,\\
p_T=(X_T-a)q_T,\qquad q_t=1.
\end{cases}\tag{51}
$$
于是$q_s=e^{-\beta(s-t)}$。受终端条件启发，令
$$
p_s=q_s(P_sX_s+\psi_s),\qquad P_T=1,\quad\psi_T=-a.
$$
这里$P$对应原文MP部分的$\phi$，$\psi$对应DP部分的$\varphi$。比较扩散项可得
$$
k_s=q_sP_s\sigma_su_s.\tag{56}
$$

>[!note] 式(58)的来源
>固定$(X^*,Y^*,p^*,q^*,k^*)$，$H$对控制变量$u$为精确的仿射函数，其斜率为
>$$
>H_u=(\mu_s-\rho_s)(p_s^*-q_s^*)+\sigma_sk_s^*.
>$$
>由于$U=\mathbb R$，(19)对$u=u_s^*+\varepsilon$和$u=u_s^*-\varepsilon$同时成立，故
>$$
>(\mu_s-\rho_s)(p_s^*-q_s^*)+\sigma_sk_s^*=0.\tag{58}
>$$
>从不等式推出等式的关键是可以双向变动控制。若有控制边界约束，边界最优点不必满足$H_u=0$。这是偏导数，不是对状态和伴随过程关于控制作全导数。

将$p,q,k$代入(58)，得到反馈候选
$$
u^*(s,x)=\frac{(\rho_s-\mu_s)(P_sx+\psi_s-1)}{P_s\sigma_s^2}.\tag{59,66}
$$
再比较$p$的漂移项。记$\alpha_s=(\mu_s-\rho_s)^2/\sigma_s^2$，得到
$$
\begin{cases}
\dot P_s=(\alpha_s-2\rho_s+\beta)P_s,\qquad P_T=1,\\
\dot\psi_s=(\alpha_s-\rho_s+\beta)\psi_s-\alpha_s+\rho_s,\qquad\psi_T=-a.
\end{cases}\tag{61,62}
$$
特别地，在系数可积时，
$$
P_s=\exp\left[-\int_s^T(\alpha_r-2\rho_r+\beta){d}r\right]>0.
$$
研究中查用上述终值ODE比直接套用原文的积分展开更稳妥。

## HJB路线：二次值函数与配方

猜测
$$
V(s,x)=\frac12P_sx^2+\psi_sx+\lambda_s,\qquad
(P_T,\psi_T,\lambda_T)=\left(1,-a,\frac12a^2\right).\tag{69,70}
$$
HJB中的被优化函数为
$$
\mathcal G(s,x,u)=-\frac12P_s\sigma_s^2u^2+(\mu_s-\rho_s)(1-P_sx-\psi_s)u+\rho_sx(1-P_sx-\psi_s)+\beta V(s,x).
$$
精确配方得到
$$
\begin{aligned}
\mathcal G(s,x,u)
=&-\frac12P_s\sigma_s^2[u-u^*(s,x)]^2\\
&+\left(\frac12\alpha_sP_s+\frac12\beta P_s-\rho_sP_s\right)x^2\\
&+\left[(\alpha_s-\rho_s+\beta)\psi_s-\alpha_s+\rho_s\right]x\\
&+\frac{\alpha_s}{2P_s}(\psi_s-1)^2+\beta\lambda_s.
\end{aligned}\tag{配方修正}
$$
由于$P_s>0$，最大元正好是MP得到的$u^*$。将$V_s=\sup_u\mathcal G$按$x^2,x,1$比较系数，前两个方程恢复(61)–(62)，常数项给出
$$
\boxed{\dot\lambda_s=\beta\lambda_s+\frac{\alpha_s}{2P_s}(\psi_s-1)^2,\qquad\lambda_T=\frac12a^2.}\tag{常数项修正}
$$
因此
$$
\lambda_s=e^{-\beta(T-s)}\frac12a^2-\int_s^T e^{-\beta(r-s)}\frac{\alpha_r}{2P_r}(\psi_r-1)^2{d}r.
$$

>[!warning] 与原文式(71)、(73)–(75)的区别
>上述常数项及$\lambda$方程是从(68)重新计算的修正结果。原文将配方后的常数项写为$-\alpha_s\psi_s/P_s+\beta\lambda_s$，遗漏了$\alpha_s(\psi_s^2+1)/(2P_s)$，所以不能直接引用原文$\lambda$公式作为价值函数。
>
>这个错误不改变$P,\psi$的ODE和反馈控制$u^*$，但影响价值函数的常数部分。原文(75)相较于(74)还多出一个$-\rho_r$积分项，故本笔记使用上面的独立重算结果。

>[!thm] LQ结果的查用形式（对应Theorems 7–8；常数项已修正）
>在$P,\psi,\lambda$满足上述终值ODE、候选反馈可容许且验证所需积分合法的条件下，
>$$
>u^*(s,x)=\frac{(\rho_s-\mu_s)(P_sx+\psi_s-1)}{P_s\sigma_s^2},\qquad
>V(s,x)=\frac12P_sx^2+\psi_sx+\lambda_s.
>$$
>应用时一组方便的充分条件是系数有界、$|\sigma_s|\ge c>0$，并对可容许控制施加足够的矩条件，使终端平方项、BSDE及Itô验证成立。原文仅写$\sigma_s\ne0$，不能据此自动断言$1/\sigma_s$有界或候选反馈可容许。

**验证方法（本笔记补充）**

此例$f$对$y$是线性的，对$z$独立。对$e^{-\beta(s-t)}Y_s$应用Itô公式可把目标改写为
$$
J(t,x;u)=\mathbb E\left[e^{-\beta(T-t)}\frac12(X_T^u-a)^2-\int_t^T e^{-\beta(s-t)}[\rho_sX_s^u+(\mu_s-\rho_s)u_s]{d}s\right].
$$
因而本例可还原为带折现的加性LQ目标，并不展示一般非线性递归生成元的全部困难。结合修正后的配方和对$e^{-\beta(s-t)}V(s,X_s^u)$的Itô计算，有
$$
J(t,x;u)-V(t,x)
=\frac12\mathbb E\int_t^T e^{-\beta(s-t)}P_s\sigma_s^2\left[u_s-u^*(s,X_s^u)\right]^2{d}s\ge0.\tag{LQ验证}
$$
取$u_s=u^*(s,X_s^u)$即达到等号。该验证直接给出最优性，不必把二次终端条件强行套入原文只陈述了线性终端条件的Lemma 4。

## 用LQ结果核对主定理

因为$f_y=-\beta$、$f_z=0$，有
$$
\begin{aligned}
q_s&=e^{-\beta(s-t)},\\
p_s^*&=q_s(P_sX_s^*+\psi_s)=q_sV_x(s,X_s^*),\\
k_s^*&=q_sP_s\sigma_su_s^*=q_sV_{xx}(s,X_s^*)\bar\sigma_s.
\end{aligned}\tag{65}
$$
这里财富方程的扩散系数是$\bar\sigma_s=\sigma_su_s^*$，不能把它误写成资产价格的波动率$\sigma_s$。主定理中的$f_z$修正项在此例为零。

# 原文核查与使用边界

>[!warning] 验证定理证明中的等式替换（第3–4页，式(11)）
>对于任意控制$u$，一般没有$Y_s^u=-V(s,X_s^u)$及$Z_s^u=-\sigma^\top V_x(s,X_s^u)$。因此不能直接把含$f(s,X_s^u,-V,-\sigma^\top V_x,u_s)$的期望积分识别为定义$J(t,x;u)$的积分。此问题是证明缺步，不能据此直接断言验证定理结论错误。

正确补法：给定HJB经典解$v$，令$\widetilde Y_s=-v(s,X_s^u)$、$\widetilde Z_s=-\sigma(s,X_s^u,u_s)^\top v_x(s,X_s^u)$。HJB保证残差
$$
r_s=\left[v_s+\langle v_x,b\rangle+\frac12\operatorname{tr}(\sigma\sigma^\top v_{xx})-f(s,x,-v,-\sigma^\top v_x,u)\right]_{(s,X_s^u,u_s)}\ge0.
$$
Itô公式给出
$$
-{d}\widetilde Y_s=[f(s,X_s^u,\widetilde Y_s,\widetilde Z_s,u_s)+r_s]{d}s-\widetilde Z_s^\top{d}W_s,\qquad\widetilde Y_T=\Phi(X_T^u).
$$
在满足比较定理所需可积性的解类内，由BSDE比较，$\widetilde Y_t\ge Y_t^u$，即$v(t,x)\le J(t,x;u)$；若控制使$r=0$，则由BSDE唯一性达到等号。

>[!warning] 第4节不逐字满足第2节全部假设
>- 终端函数$\Phi(x)=-\frac12(x-a)^2$不满足（H2）的全局Lipschitz及线性增长要求。
>- $U=\mathbb R$时，$b(s,x,u)=\rho_sx+(\mu_s-\rho_s)u$及扩散系数$\sigma_su$不满足（H1）对$u$一致的增长界；生成元也不满足（H2）对$u$一致的相应增长界。
>- Lemma 4要求线性终端函数，本例终端为二次函数。因此“所有前述条件均满足”的表述不准确。可使用适合LQ增长的假设并通过[[#HJB路线：二次值函数与配方|LQ验证]]重新证明。

>[!note] 记号与量词
>- 第4页式(16)定义$\bar\sigma$时右边误写成$b$，应为$\sigma$；式(17)后的文字把前向$q$与后向$(p,k)$说反。
>- 式(33)–(34)的控制取值随$(s,\omega)$固定；有关漂移、扩散系数的恒等式以${d}s\otimes\mathbb P$几乎处处为准，不额外假定控制时间连续。
>- $V\in C^{1,3}$是强的外加条件；应用唯一性识别候选伴随解时还应验证其所属解空间。原文没有详细展开这部分增长与局部化问题。
>- 原文结尾讨论非光滑关系作为当时的后续问题；这只描述2013年本文的研究边界，不代表当前文献状态。

# 研究查阅：可复用的结构

>[!note] 证明模板
>1. 利用DPP沿最优轨道识别$Y=-V$，再用半鞅分解识别$Z$。
>2. 固定最优控制取值，利用HJB残差的极值性质求状态导数，避免对最优反馈求导。
>3. 对$V_x$应用Itô公式；引入由$f_y,f_z$决定的随机积分因子$q$，用二次协变差消去递归项。
>4. 匹配终端条件并核对解空间，用伴随BSDE唯一性得到表示。
>5. 在LQ结构下，以伴随过程的仿射猜测或价值函数的二次猜测，将随机最优性系统化为确定性终值ODE，再独立验证可容许性与最优性。

>[!question] 推广时先检查什么
>- **非光滑值函数：**哪些导数关系能够改为半喷射包含关系？本文不提供相应定理。
>- **全耦合FBSDE：**若$b,\sigma$依赖$(Y,Z)$，$Z=-\sigma^\top V_x$可能成为隐式关系，当前推导不能原样套用。
>- **非凸控制域：**本文必要条件使用凸变分；不能直接代替一般非凸域的最大值原理。
>- **随机系数：**当前确定性HJB框架依赖Markov结构，随机系数情形需重新选择价值对象及方程框架。

相关工具笔记：[[随机LQ问题的开环解与闭环解]]、[[Linear SDE]]、[[Representations of Continuous Martingales in Terms of Brownian Motion]]、[[1990-Pardoux&Peng Adapted solution of a backward stochastic differential equation]]。
