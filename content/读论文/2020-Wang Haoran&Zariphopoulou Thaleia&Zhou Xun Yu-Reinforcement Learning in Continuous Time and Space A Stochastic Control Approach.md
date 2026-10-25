---
publish: 2020
tag: 强化学习, 随机控制, 松弛控制, 熵正则化, HJB, LQ, 高斯探索
---

>[!note] 文献信息
>Haoran Wang, Thaleia Zariphopoulou & Xun Yu Zhou. *Reinforcement Learning in Continuous Time and Space: A Stochastic Control Approach*. **Journal of Machine Learning Research**, 21(198):1–34, 2020.
>
>[期刊页面](https://jmlr.org/papers/v21/19-144.html)；[期刊PDF](https://jmlr.org/papers/volume21/19-144/19-144.pdf)。阅读整理：2026-10-25。本笔记依据2020年期刊版；页码和数字公式编号均对应这一版本。
>
>原文结论、证明路线与本笔记补充推导分开标明。原文式(37)的$k_1$漏项已由式(34)重新核算；查用时使用下文修正式，不直接抄录原式(37)。

>[!note] 本文的主要工作
>- 建立连续时间、连续状态与连续动作空间中的**探索式随机控制框架**：把控制扩展为概率分布，在生成元层面对动作平均，得到松弛控制动力学。
>- 用**微分熵正则化**刻画探索偏好；HJB中的分布优化给出Gibbs策略，LQ下进一步得到高斯策略。
>- 对无限时域折现LQ问题给出显式解和验证定理：最优反馈均值是状态的仿射函数，方差为常数；在相应可解条件下，均值与经典最优反馈一致，方差正比于探索权重$\lambda$。
>- 建立二次价值函数框架下经典问题与探索问题的可解性联系，得到标量动作的探索成本$\lambda/(2\rho)$，以及$\lambda\downarrow0$时策略与价值函数的收敛。
>- 贡献主要在**建模与结构定理**。本文没有给出一般未知模型下的策略学习算法、样本复杂度或regret保证；熵最优不等于信息获取效率最优。

>[!note] 查用入口
>- 建模思想和生成元平均：[[#研究背景与核心思想]]、[[#探索动力学与熵正则目标]]。
>- 式(15)到式(17)的变分推导：[[#HJB与Gibbs最优分布]]。
>- LQ模型与可容许性：[[#LQ问题与可容许策略]]。
>- 常数价值函数：[[#定理2：奖励与状态无关]]。
>- 主定理、系数和高斯反馈：[[#定理4：一般LQ问题的显式解]]。
>- 最优性验证和矩估计：[[#定理4的证明路线]]。
>- 可解性、探索成本和零温极限：[[#经典问题与探索问题的关系]]。
>- 可复用方法和后续阅读：[[#可复用方法与研究接口]]。
>- 公式修正和使用边界：[[#原文核查与使用边界]]。

# 研究背景与核心思想

>[!note] 随机控制与强化学习的连接
>经典随机控制通常在模型给定后求最优策略；强化学习还需要从交互数据中学习。在模型未知时，一直选择目前估计最好的动作可能使其他动作得不到尝试，因此引入随机策略。
>
>本文将这件事拆为两步：
>1. **松弛控制**规定随机策略对应什么状态动力学；
>2. **熵正则化**规定优化目标如何奖励动作分布的分散程度。
>
>熵正则化改变目标函数；梯度下降或梯度上升是求解方法，二者不在同一层次。本文的Gibbs公式由变分优化直接得到。

>[!def] 经典无限时域折现控制问题（第5–6页，式(1)–(2)）
>状态、动作和Brownian motion均取一维：
>$$
>{d}x_t^u=b(x_t^u,u_t){d}t+\sigma(x_t^u,u_t){d}W_t,\qquad x_0^u=x.
>$$
>$$
>V^{\mathrm{cl}}(x)=\sup_{u\in\mathcal A^{\mathrm{cl}}(x)}\mathbb E_x\int_0^\infty e^{-\rho t}r(x_t^u,u_t){d}t,\qquad\rho>0.\tag{1,2}
>$$
>本文采用**奖励最大化**的符号约定。经典反馈$u^*(x)$在给定状态下指定一个动作；分布反馈$\pi(\cdot;x)$在给定状态下指定一个动作分布。

>[!note] 两种随机性与两个层次
>- 环境噪声由$W$描述；动作随机化由策略分布$\pi$描述。
>- 优化时选择分布$\pi(\cdot;x)$；执行时按照该分布抽取动作。熵奖励不是“随机挑选不同分布”的算法。
>- 给定状态下的策略密度是确定性函数，沿随机状态代入得到的$\pi_t=\pi(\cdot;X_t)$则是随机的、以概率测度为值的过程。
>- “每个连续时刻独立抽取动作”不能未经构造就视为一个合法的可测控制过程。原文第2节主要提供建模动机；一般的离散执行收敛定理需要另外证明。

# 探索动力学与熵正则目标

>[!def] 探索式动力学（第7–8页，式(6)–(11)）
>令$\mathcal P(\mathcal U)$表示关于Lebesgue测度绝对连续的概率密度集合。定义
>$$
>\widetilde b(x,\pi)=\int_{\mathcal U}b(x,u)\pi(u){d}u,\qquad
>\widetilde\sigma(x,\pi)=\left(\int_{\mathcal U}\sigma^2(x,u)\pi(u){d}u\right)^{1/2},
>$$
>$$
>{d}X_t^\pi=\widetilde b(X_t^\pi,\pi_t){d}t+\widetilde\sigma(X_t^\pi,\pi_t){d}W_t,\qquad X_0^\pi=x,\tag{6–8}
>$$
>$$
>\widetilde r(x,\pi)=\int_{\mathcal U}r(x,u)\pi(u){d}u.\tag{11}
>$$
>关键是**先平均扩散系数的平方，再开平方**，不是平均$\sigma$本身。多维时相应平均的是协方差矩阵$\sigma\sigma^\top$。

>[!proposition] 生成元与松弛控制解释（第8页脚注7；推导补充）
>经典生成元为
>$$
>\mathcal L^u f(x)=b(x,u)f'(x)+\frac12\sigma^2(x,u)f''(x).
>$$
>分布控制对应
>$$
>\mathcal L^\pi f(x)=\int_{\mathcal U}\mathcal L^u f(x)\pi(u){d}u
>=\widetilde b(x,\pi)f'(x)+\frac12\widetilde\sigma^2(x,\pi)f''(x).
>$$
>在适当可积性条件下，
>$$
>f(X_t^\pi)-f(x)-\int_0^t\mathcal L^{\pi_s}f(X_s^\pi){d}s
>$$
>为鞅。这与经典松弛控制的鞅问题表述一致。历史上松弛控制主要服务于控制集的凸化、紧化及最优控制存在性；本文将其用于解释探索。

**Proof（局部矩的理解）**

固定状态$x$，在一个长度为$h$的小区间开始时抽取动作$U$，使其独立于未来Brownian增量，则
$$
\Delta X\approx b(x,U)h+\sigma(x,U)\Delta W.
$$
在适当正则性与矩条件下，一阶主项为
$$
\mathbb E[\Delta X]=\mathbb E[b(x,U)]h+o(h),\qquad
\mathbb E[(\Delta X)^2]=\mathbb E[\sigma^2(x,U)]h+o(h).
$$
例如$\sigma(x,u)=u$且$U\sim N(0,1)$，有$\mathbb E\sigma=0$但$\mathbb E\sigma^2=1$。直接平均$\sigma$会错误地丢失二次变差。上述计算说明候选生成元的形式，不单独构成一般过程弱收敛的证明。

**QED**

>[!def] 熵正则化的探索目标（第8页，式(12)）
>$$
>\mathcal H(\pi):=-\int_{\mathcal U}\pi(u)\ln\pi(u){d}u,\qquad\lambda>0,
>$$
>$$
>V_\lambda(x)=\sup_{\pi\in\mathcal A(x)}J_\lambda(x;\pi),\qquad
>J_\lambda(x;\pi)=\mathbb E_x\int_0^\infty e^{-\rho t}\bigl[\widetilde r(X_t^\pi,\pi_t)+\lambda\mathcal H(\pi_t)\bigr]{d}t.\tag{12}
>$$
>本笔记用$V_\lambda$显式标记探索权重；原文通常简记为$V$。$\lambda$是外生温度参数，$\rho$是折现率。

>[!note] 为什么需要熵项
>固定候选价值函数后，未正则化的Hamiltonian对分布是线性的。若动作最大值存在，允许一般概率测度时，把全部质量放到一个最大化动作上即可达到最优；仅仅允许分布控制，并不会自动鼓励探索。
>
>加入熵后，目标兼顾较高奖励和分布分散程度。这里使用的是**微分熵**，可为负值；Dirac测度不在密度可行集中，不能直接代入该熵公式。熵不等于模型参数的信息增益，本文也未建立Bayesian后验学习模型。

# HJB与Gibbs最优分布

>[!def] 分布控制HJB（第9–10页，式(14)–(15)）
>对候选经典解$v$，记
>$$
>G_v(x,u):=r(x,u)+b(x,u)v'(x)+\frac12\sigma^2(x,u)v''(x).
>$$
>形式上的动态规划方程为
>$$
>\rho v(x)=\sup_{\pi\in\mathcal P(\mathcal U)}
>\left\{\int_{\mathcal U}G_v(x,u)\pi(u){d}u-\lambda\int_{\mathcal U}\pi(u)\ln\pi(u){d}u\right\}.\tag{15}
>$$
>第3节是形式推导；一般系数下的适定性、光滑性、积分有限性和验证定理并未在此完整建立。

>[!proposition] Gibbs反馈与soft HJB（式(17)；KL恒等式为补充证明）
>固定$x,v$，假设
>$$
>0<Z_v(x):=\int_{\mathcal U}\exp\left(\frac{G_v(x,u)}\lambda\right){d}u<\infty,
>$$
>且目标与后续积分有意义，则密度优化的最大化解为
>$$
>\pi_v^*(u;x)=\frac{\exp(G_v(x,u)/\lambda)}{Z_v(x)}.\tag{17}
>$$
>因此HJB可写为
>$$
>\rho v(x)=\lambda\ln\int_{\mathcal U}\exp\left(\frac{r(x,u)+b(x,u)v'(x)+\tfrac12\sigma^2(x,u)v''(x)}\lambda\right){d}u.\tag{soft HJB}
>$$

**Proof**

固定$x$，对约束$\int\pi=1$引入乘子$\eta$。一阶变分给出
$$
G_v(x,u)-\lambda(\ln\pi(u)+1)+\eta=0,
$$
所以$\pi(u)=C(x)e^{G_v(x,u)/\lambda}$，再由归一化得到$C(x)=Z_v(x)^{-1}$。

最大性可由更强的恒等式说明：
$$
\int G_v\pi+\lambda\mathcal H(\pi)
=\lambda\ln Z_v(x)-\lambda D_{\mathrm{KL}}(\pi\Vert\pi_v^*(\cdot;x)).\tag{KL恒等式}
$$
KL非负，故$\pi_v^*$达到全局最大值；等号要求两个密度几乎处处相等。这证明的是固定$x,v$时的静态最优性，完整控制最优性仍需验证。

**QED**

# LQ问题与可容许策略

>[!def] 标量LQ模型（第10–11页，式(19)–(23)）
>$$
>b(x,u)=Ax+Bu,\qquad\sigma(x,u)=Cx+Du,\qquad\mathcal U=\mathbb R,
>$$
>$$
>r(x,u)=-\left(\frac M2x^2+Rxu+\frac N2u^2+Px+Qu\right),\tag{19,20}
>$$
>其中$A,B,C,D,R,P,Q\in\mathbb R$，$M\ge0$，$N>0$。
>
>为避免与扩散系数$\sigma$混淆，本笔记将动作方差记为$s_t^2$（原文记为$\sigma_t^2$）：
>$$
>\mu_t=\int u\pi_t(u){d}u,\qquad s_t^2=\int u^2\pi_t(u){d}u-\mu_t^2.
>$$
>探索动力学为
>$$
>{d}X_t^\pi=(AX_t^\pi+B\mu_t){d}t+
>\sqrt{(CX_t^\pi+D\mu_t)^2+D^2s_t^2}\,{d}W_t.\tag{22}
>$$
>对应平均奖励为
>$$
>\widetilde r(x,\pi)=-\frac M2x^2-Rx\mu-\frac N2(\mu^2+s^2)-Px-Q\mu.
>$$
>当$D=0$且均值策略保持不变时，动作方差不直接改变探索极限状态方程，但仍通过$-Ns^2/2$及熵项影响目标。

>[!def] LQ可容许策略（第11页）
>令$L_\lambda(x,\pi):=\widetilde r(x,\pi)+\lambda\mathcal H(\pi)$。原文要求$\pi\in\mathcal A(x)$满足：
>1. 每个$t$，$\pi_t\in\mathcal P(\mathbb R)$，a.s.；
>2. 对任意Borel集合$E$，$\int_E\pi_t(u){d}u$关于$t$渐进可测；
>3. 对每个有限$T$，$\mathbb E\int_0^T(\mu_t^2+s_t^2){d}t<\infty$；
>4. $\liminf_{T\to\infty}e^{-\rho T}\mathbb E[(X_T^\pi)^2]=0$；
>5. $\mathbb E\int_0^\infty e^{-\rho t}|L_\lambda(X_t^\pi,\pi_t)|{d}t<\infty$。
>
>（3）支持状态方程适定性与有限时域矩估计；（4）是验证所需的横截条件；（5）保证无限时域奖励绝对可积。不能只检查密度归一化就宣称反馈策略可容许。

>[!proposition] LQ下的高斯结构（第15页，式(31)）
>定义
>$$
>S_v(x)=N-D^2v''(x),\qquad T_v(x)=CDxv''(x)+Bv'(x)-Rx-Q.
>$$
>Hamiltonian关于动作的部分为
>$$
>G_v(x,u)=-\frac12S_v(x)u^2+T_v(x)u+
>\frac12(C^2v''(x)-M)x^2+(Av'(x)-P)x.
>$$
>若$S_v(x)>0$，则配方并归一化得到
>$$
>\pi_v^*(\cdot;x)=\mathcal N\left(\frac{T_v(x)}{S_v(x)},\frac\lambda{S_v(x)}\right).\tag{31}
>$$
>高斯性来自**关于动作的严格凹二次Hamiltonian加熵变分**。它并不要求系数关于状态也线性；但一般状态非线性的情形仍需另外证明HJB正则性和策略可容许性。

由此，HJB化为
$$
\rho v=\frac{T_v^2}{2S_v}+\frac\lambda2\ln\frac{2\pi\lambda}{S_v}
+\frac12(C^2v''-M)x^2+(Av'-P)x.\tag{32}
$$
这里用$\ln(ea)-1=\ln a$简化了原文写法。

# 定理2：奖励与状态无关

>[!thm] 常数价值函数与状态无关高斯策略（第12–13页，定理2）
>当$M=R=P=0$，即$r(x,u)=-Nu^2/2-Qu$时，
>$$
>V_\lambda(x)=\frac{Q^2}{2\rho N}+\frac\lambda{2\rho}\ln\frac{2\pi\lambda}{N},\tag{26}
>$$
>$$
>\pi^*(\cdot;x)=\mathcal N\left(-\frac QN,\frac\lambda N\right).\tag{27}
>$$
>最优状态满足
>$$
>{d}X_t^*=\left(AX_t^*-\frac{BQ}N\right){d}t+
>\sqrt{\left(CX_t^*-\frac{DQ}N\right)^2+\frac{\lambda D^2}N}\,{d}W_t.\tag{28}
>$$
>**可容许性口径：**原文第13页脚注10说明，此状态无关奖励特例不需要验证前述条件（4）。引用定理2时应保留这一调整，不能无条件将其套在强制要求状态横截条件的另一控制类上。

**Proof**

式(25)是式(32)在$M=R=P=0$时的形式。尝试$v(x)\equiv c$，则$v'=v''=0$，得到
$$
\rho c=\frac{Q^2}{2N}+\frac\lambda2\ln\frac{2\pi\lambda}{N}.
$$
所以式(26)是一个常数候选解，并非式(25)的通解。

更直接的解释是逐时刻静态优化。令
$$
m=\sup_\pi\left\{\int(-Nu^2/2-Qu)\pi(u){d}u+\lambda\mathcal H(\pi)\right\}.
$$
Gibbs公式与高斯积分给出$m=Q^2/(2N)+(\lambda/2)\ln(2\pi\lambda/N)$。每个时刻的正则奖励都不超过$m$，故$J_\lambda(x;\pi)\le m/\rho$；始终采用上述高斯密度达到等号。常数价值函数来自奖励与可用动作不依赖状态。

**QED**

>[!note] HJB解不必是价值函数（补充例子）
>取$A=C=D=Q=0$，$B=N=\rho=\lambda=1$，式(25)成为
>$$
>v=\frac12(v')^2+\frac12\ln(2\pi).
>$$
>$v_1(x)=\frac12\ln(2\pi)$和$v_2(x)=\frac12x^2+\frac12\ln(2\pi)$都满足方程；静态上界表明只有$v_1$是价值函数。符号软件可以找出或检验候选解，但不会自动完成最优性验证。

# 定理4：一般LQ问题的显式解

>[!def] 定理4的充分条件（第14–16页）
>除$\lambda,\rho,N>0$、$M\ge0$外，要求
>$$
>R^2<MN,
>$$
>以及原文Assumption 3：
>$$
>\rho>2A+C^2+\max\left\{\frac{D^2R^2-2NR(B+CD)}N,0\right\}.\tag{Assumption 3}
>$$
>这里严格照录期刊PDF中的假设。它是文中的充分条件，不是本文证明过的必要条件。$R^2<MN$与$N>0$还蕴含$M>0$及奖励二次成本矩阵正定。

>[!thm] 二次价值函数与最优高斯反馈（定理4；$k_1$使用核算修正式）
>在上述条件下，取下文的$k_2<0$、$k_1$和$k_0$，有
>$$
>V_\lambda(x)=\frac12k_2x^2+k_1x+k_0.\tag{39}
>$$
>记
>$$
>S=N-D^2k_2>0,\qquad
>K=\frac{k_2(B+CD)-R}{S},\qquad
>h=\frac{Bk_1-Q}{S}.
>$$
>则最优反馈分布为
>$$
>\pi^*(\cdot;x)=\mathcal N\left(Kx+h,\frac\lambda S\right),\tag{40}
>$$
>最优状态方程可紧凑写成
>$$
>{d}X_t^*=\bigl[(A+BK)X_t^*+Bh\bigr]{d}t+
>\sqrt{\bigl[(C+DK)X_t^*+Dh\bigr]^2+\frac{\lambda D^2}S}\,{d}W_t.\tag{41}
>$$
>期刊原文式(37)与式(34)不一致，不能把本框中的$k_1$理解为原式(37)的照抄。修正推导及反例见[[#原文核查与使用边界]]。

>[!def] Riccati方程及系数计算
>代入$v(x)=\tfrac12k_2x^2+k_1x+k_0$并匹配$x^2,x,1$，得到
>$$
>\begin{aligned}
>\rho k_2&=\frac{[k_2(B+CD)-R]^2}{N-D^2k_2}+(2A+C^2)k_2-M,\\
>\rho k_1&=\frac{(Bk_1-Q)[k_2(B+CD)-R]}{N-D^2k_2}+Ak_1-P,\\
>\rho k_0&=\frac{(Bk_1-Q)^2}{2(N-D^2k_2)}+\frac\lambda2\ln\frac{2\pi\lambda}{N-D^2k_2}.
>\end{aligned}\tag{33–35}
>$$
>令$\delta=\rho-2A-C^2>0$、$\ell=B+CD$，并定义
>$$
>a=\ell^2+\delta D^2,\qquad b=\delta N+2\ell R-D^2M,\qquad c=MN-R^2>0.
>$$
>第一式等价于$ak_2^2-bk_2-c=0$。负根可写成
>$$
>k_2=-\frac{2c}{b+\sqrt{b^2+4ac}}<0.\tag{36等价形式}
>$$
>当$a>0$时，这等价于原式(36)的$(b-\sqrt{b^2+4ac})/(2a)$；当$a=0$时，$b=N\delta>0$，上述写法仍给出$k_2=-c/b$，避免原根式的$0/0$。
>
>后两式给出
>$$
>\boxed{k_1=-\frac{P+QK}{\rho-A-BK}},\tag{37修正}
>$$
>$$
>k_0=\frac{(Bk_1-Q)^2}{2\rho S}+\frac\lambda{2\rho}\ln\frac{2\pi\lambda}{S}.\tag{38}
>$$
>由下文的折现二阶矩稳定性，$\rho-A-BK>0$，因此此处分母非零。

>[!note] 利用与探索的分离
>系数匹配中，$\lambda$仅出现在常数项方程；$k_2,k_1,K,h$均与$\lambda$无关。因此给定状态$x$时，最优均值$Kx+h$不随温度改变，方差$\lambda/S$正比于温度且不依赖状态。
>
>这依赖于当前LQ与常系数结构。一般非线性问题中，$v_\lambda',v_\lambda''$也会随$\lambda$改变，即便条件策略仍为高斯，其均值与方差也未必保持这种分离。

# 定理4的证明路线

**Proof**

**第一步：解代数方程并选取负曲率分支。** 由上述系数方程得到$k_2<0$，进而$S=N-D^2k_2>0$，高斯密度可归一化。代入原HJB验证等式成立。找出一个代数根还不足以完成最优性证明。

**第二步：对任意可容许策略给出上界。** 由HJB，
$$
L_\lambda(x,\pi)+\mathcal L^\pi v(x)-\rho v(x)\le0.
$$
对$e^{-\rho t}v(X_t^\pi)$使用Itô公式。先用停止时刻局部化随机积分，再用有限时域矩估计和绝对可积性去掉停止，得到
$$
\mathbb E\int_0^T e^{-\rho t}L_\lambda(X_t^\pi,\pi_t){d}t+
\mathbb E[e^{-\rho T}v(X_T^\pi)]\le v(x).\tag{验证不等式}
$$
由于$v$为二次函数，条件$\liminf e^{-\rho T}\mathbb E[(X_T^\pi)^2]=0$允许选取$T_n\to\infty$使终端项趋于零；线性项由Cauchy–Schwarz处理。因此$J_\lambda(x;\pi)\le v(x)$，从而$V_\lambda(x)\le v(x)$。这里不能未经论证把$\liminf$写成对全部$T$的极限。

**第三步：验证候选策略可容许。** 设
$$
\widehat A=A+BK,\quad\widehat B=Bh,\quad
\widehat C=C+DK,\quad\widehat D=Dh,\quad e=\lambda D^2/S.
$$
闭环为${d}X=(\widehat AX+\widehat B){d}t+\sqrt{(\widehat CX+\widehat D)^2+e}{d}W$。其系数全局Lipschitz且线性增长。对一、二阶矩$n(t)=\mathbb EX_t$、$m(t)=\mathbb EX_t^2$有
$$
\begin{cases}
n'=\widehat A n+\widehat B,\\
m'=(2\widehat A+\widehat C^2)m+2(\widehat B+\widehat C\widehat D)n+\widehat D^2+e.
\end{cases}\tag{闭环矩方程}
$$
记$\gamma=2\widehat A+\widehat C^2$。利用Riccati方程，可以直接得到下列恒等式（本笔记补充的短证）：
$$
\boxed{k_2(\gamma-\rho)=M+2RK+NK^2>0.}\tag{折现稳定性}
$$
右侧由$R^2<MN$严格为正，而$k_2<0$，所以$\gamma<\rho$。又$2\widehat A\le\gamma$且$\rho>0$，因此$\widehat A<\rho$。矩方程给出
$$
e^{-\rho T}\mathbb E[(X_T^*)^2]\to0,\qquad
\mathbb E\int_0^\infty e^{-\rho t}(X_t^*)^2{d}t<\infty.
$$
最优策略的熵为常数，奖励至多二次增长，因此可容许性中的无限时域可积性也成立。这是**折现意义的矩控制**，不等价于未折现系统均方渐近稳定。

**第四步：达到上界。** 对$\pi^*$，验证不等式中的Hamiltonian不等式取等号；再消去终端项，得到$J_\lambda(x;\pi^*)=v(x)$，故$v=V_\lambda$。

**QED**

>[!note] 证明中各假设承担的作用
>- $N-D^2v''>0$：动作方向严格凹，配分函数有限。
>- 选择$k_2<0$：确定正确曲率分支，并配合正定奖励得到折现矩估计。
>- 局部平方可积和状态矩界：使Itô局部化及去停止合法。
>- 横截条件：控制$T\to\infty$时的终端项。
>- 奖励绝对可积：允许把有限时域目标传到无限时域。
>
>原文附录B采用展开闭环增长率的方式；上述Riccati恒等式给出一个更短、可直接复核的估计路线。

# 经典问题与探索问题的关系

>[!thm] 定理9：二次价值函数框架下的可解性等价（第20页）
>取$\alpha_2<0$、$\alpha_1,\alpha_0\in\mathbb R$，令$S_\alpha=N-D^2\alpha_2$，以及
>$$
>u^*(x)=\frac{[\alpha_2(B+CD)-R]x+B\alpha_1-Q}{S_\alpha}.
>$$
>原文建立以下两项的等价：
>1. 经典问题的价值函数为$w(x)=\tfrac12\alpha_2x^2+\alpha_1x+\alpha_0$，最优反馈为$u^*(x)$；
>2. 探索问题的价值函数为
>$$
>v_\lambda(x)=w(x)+\frac\lambda{2\rho}\ln\frac{2\pi\lambda}{S_\alpha},
>$$
>最优反馈分布为
>$$
>\pi_\lambda^*(\cdot;x)=\mathcal N\left(u^*(x),\frac\lambda{S_\alpha}\right).
>$$
>这里的“可解性等价”包含价值函数和最优策略的识别及可容许性；不是说任意非LQ问题或任意HJB形式解都可按此转换。定理9的表述也不应直接改写成定理4的充分条件是必要条件。

**Proof（查用路线）**

经典与探索HJB的差别是熵带来的常数项。对二次候选函数，这一常数平移不改变一、二阶导数，所以对应的均值反馈一致。

还须比较可容许性。原文附录C通过一、二阶矩方程比较两个最优状态过程。将探索与经典状态的二阶矩分别记为$m(t)$、$\widehat m(t)$。使用上述$\widehat A,\widehat B,\widehat C,\widehat D,e$记号，两者一阶矩相同，二阶矩之差满足
$$
(m-\widehat m)'=\gamma(m-\widehat m)+e,\qquad m(0)-\widehat m(0)=0,
$$
即
$$
m(t)-\widehat m(t)=e\int_0^t e^{\gamma(t-s)}{d}s.\tag{矩差公式}
$$
在定理4的充分条件下已有$\gamma<\rho$，因此这部分新增矩的折现积分有限且折现终端项消失。该计算明确解释了此情形中可容许性为何可以转移。引用更一般的定理9时，仍需保留其“二次价值函数与对应最优策略”的完整前提；不能把矩等价当作任意不稳定仿射SDE的无条件性质。

**QED**

>[!def] 探索成本（第21页，式(47)）
>在经典与探索问题均可解时，定义
>$$
>\mathcal C_\lambda(x)=V^{\mathrm{cl}}(x)-
>\mathbb E_x\int_0^\infty e^{-\rho t}\widetilde r(X_t^{\pi_\lambda^*},\pi_{\lambda,t}^*){d}t.\tag{47}
>$$
>第二项只计算**原始奖励**，已扣除熵奖励。它衡量执行熵正则最优策略所损失的原始回报，不是从数据学习策略过程中的累计regret。

>[!thm] 定理10：标量LQ的探索成本（第21–22页）
>在定理9任一等价陈述成立时，
>$$
>\boxed{\mathcal C_\lambda(x)=\frac\lambda{2\rho}},\qquad x\in\mathbb R.\tag{48}
>$$
>此标量结果不依赖初始状态和具体LQ系数；$\lambda$越大，原始回报损失越大；$\rho$越小，有效累计时间越长。

**Proof**

最优高斯策略的熵为状态无关常数
$$
\mathcal H(\pi_\lambda^*)=\frac12\ln\frac{2\pi e\lambda}{S_\alpha}.
$$
所以
$$
\begin{aligned}
J_{\mathrm{raw}}(x;\pi_\lambda^*)
&=V_\lambda(x)-\frac\lambda\rho\mathcal H(\pi_\lambda^*)\\
&=V^{\mathrm{cl}}(x)+\frac\lambda{2\rho}\ln\frac{2\pi\lambda}{S_\alpha}
-\frac\lambda{2\rho}\ln\frac{2\pi e\lambda}{S_\alpha}\\
&=V^{\mathrm{cl}}(x)-\frac\lambda{2\rho}.
\end{aligned}
$$
因此探索成本为$\lambda/(2\rho)$。不能用$V^{\mathrm{cl}}-V_\lambda$代替这个成本，因为两者的目标函数不同。

**QED**

>[!thm] 定理11：探索消失时的收敛（第22页）
>在定理9的前提下，对每个固定$x$，当$\lambda\downarrow0$时，
>$$
>\pi_\lambda^*(\cdot;x)\Rightarrow\delta_{u^*(x)},\qquad
>V_\lambda(x)\to V^{\mathrm{cl}}(x).
>$$
>这是最优解族随温度变化的结论，不是某个策略学习算法随迭代次数增加的收敛结论，也没有在本定理中证明状态路径收敛。

**Proof**

均值$u^*(x)$与$\lambda$无关，方差$\lambda/S_\alpha\to0$，得到概率测度的弱收敛。价值差为
$$
V_\lambda(x)-V^{\mathrm{cl}}(x)=\frac\lambda{2\rho}\ln\frac{2\pi\lambda}{S_\alpha}\to0.
$$
由同一显式公式还可读出：在固定模型参数下，价值差为$O(\lambda|\ln\lambda|)$，且该差与$x$无关。这是对原定理的直接补充。

**QED**

# 可复用方法与研究接口

>[!note] 可以迁移到其他问题的四个方法
>1. **生成元平均。** 给随机策略定义连续时间极限时，先研究生成元或鞅问题；多维扩散平均$\sigma\sigma^\top$。
>2. **熵变分的KL恒等式。** 把分布优化变为$\lambda\log\int e^{G/\lambda}$，同时得到全局最优性、唯一性和目标差。
>3. **LQ闭合与系数匹配。** 先识别Hamiltonian的动作二次结构，再用价值函数二次试探形式把HJB化成Riccati及线性代数方程；代数解必须结合验证选取。
>4. **验证定理与折现矩。** 用Itô公式给出全体策略的上界，再为候选策略验证矩、横截和可积性。Riccati恒等式可以替代冗长的参数展开。

>[!note] 对状态非线性但对动作保持LQ的推广（第18–19页，Remark 8）
>若
>$$
>{d}X_t=[A(X_t)+B(X_t)u_t]{d}t+[C(X_t)+D(X_t)u_t]{d}W_t,
>$$
>$$
>r(x,u)=-\frac12r_2(x)u^2-r_1(x)u-r_0(x),
>$$
>则形式上仍有高斯反馈，其方差为$\lambda/[r_2(x)-D(x)^2v''(x)]$。要得到严格结论，必须处理值函数正则性、严格正性、状态方程适定性和验证条件。原文Remark 8给出这一方向，但没有证明一个覆盖所有此类非线性模型的完整定理。

>[!question] 研究查阅时需要继续追问的问题
>- **学习层面：**既然最优策略公式仍含未知模型或未知价值导数，如何仅用轨迹估计价值、改进策略并证明收敛？
>- **执行层面：**离散抽样并分段保持动作，怎样逼近松弛控制扩散？误差依赖哪些正则性条件？
>- **极限层面：**当采样步长、探索温度和统计估计误差同时变化时，各误差项如何相互影响？
>- **模型层面：**动作约束、跳过程、非线性状态依赖或更一般正则项，会改变哪些结构？
>
>这些是阅读后形成的研究接口，不表示它们目前都无人研究；具体选题必须进一步查证已有结果。

>[!note] 后续阅读入口（不属于本文定理）
>- Jia & Zhou（2022），[Policy Evaluation and Temporal-Difference Learning in Continuous Time and Space: A Martingale Approach](https://jmlr.org/papers/v23/21-0947.html)：用鞅刻画策略评估，连接连续时间TD方法。
>- Jia & Zhou（2023），[q-Learning in Continuous Time](https://jmlr.org/papers/v24/22-0755.html)：研究连续时间的小$q$函数及基于鞅条件的学习方法；期刊页面另列有erratum，精读时一并查看。
>- Jia, Ouyang & Zhang，[Accuracy of Discretely Sampled Stochastic Policies in Continuous-time Reinforcement Learning](https://arxiv.org/abs/2503.09981)：研究离散抽样策略执行对探索动力学的逼近及相关估计误差。
>
>本库相关工具笔记：[[动态规划法与HJB方程]]、[[粘性解框架下的HJB方程]]、[[线性二次的最优控制]]。

# 原文核查与使用边界

>[!warning] 式(37)的$k_1$漏项：按式(34)修正
>令$\ell=B+CD$、$S=N-D^2k_2$。原文式(37)写为
>$$
>k_1^{\mathrm{printed}}=\frac{PS-QR}{k_2B\ell+(A-\rho)S-BR}.
>$$
>但原文式(34)要求
>$$
>[\rho S-AS-B(k_2\ell-R)]k_1=-Q(k_2\ell-R)-PS.
>$$
>因此应使用
>$$
>\boxed{k_1=\frac{PS+Qk_2\ell-QR}{k_2B\ell+(A-\rho)S-BR}
>=-\frac{P+QK}{\rho-A-BK}.}
>$$
>原式分子缺少$Qk_2(B+CD)$。当$Q=0$或该乘积为零时不受影响；一般情况下会改变价值函数的线性项及策略均值的截距。
>
>**直接检验：**取$A=C=D=R=P=0$，$B=M=N=\rho=Q=1$，满足定理4的条件。此时$k_2=(1-\sqrt5)/2$，式(34)变成$k_1=(k_1-1)k_2$，所以
>$$
>k_1=\frac{k_2}{k_2-1}=\frac{3-\sqrt5}{2}\ne0.
>$$
>原式(37)却给出$k_1=0$，代回式(34)不成立。这是依据所读期刊PDF进行的代数核查，不冒充作者正式勘误。

>[!warning] 附录B式(54)的展开分母
>令$\ell=B+CD$、$S=N-D^2k_2$，直接展开应为
>$$
>\gamma-\rho=2A+C^2-\rho+
>\frac{k_2(2N-k_2D^2)\ell^2-2NR\ell+D^2R^2}{S^2}.
>$$
>所读PDF中式(54)最后一行的两个分母写成$S$，与前一行不一致，应为$S^2$。本笔记使用$k_2(\gamma-\rho)=M+2RK+NK^2$的直接恒等式完成估计。

>[!warning] 其他查用边界
>- **式(24)的符号。** 其中第一行展开即时奖励时写出的$+Qu$与本节定义$r=-Nu^2/2-Qu$不一致；后续均值$-Q/N$及式(25)–(27)对应的是$-Qu$。使用时从式(20)的奖励定义出发。
>- **附录编号。** 第28页“Appendix C: Proof of Theorem 7”实际对应正文定理9的可解性等价证明。
>- **高斯性的条件。** 它是给定状态下的动作分布性质，不表示状态过程是高斯过程，也不保证对随机状态混合后的动作边际分布仍为高斯。
>- **动作空间。** 完整高斯公式使用$\mathcal U=\mathbb R$；有界动作区间上的同类凹二次Gibbs优化给出截断高斯，后续价值函数未必仍保持原来的二次闭合。
>- **纯熵最大化。** 整个$\mathbb R$上不存在均匀概率分布，且微分熵无有限最大值；“纯探索最优为均匀分布”需要有限测度动作域等额外条件。
>- **探索与学习。** 熵高只表示动作分布更分散，并不保证有效信息、状态覆盖或低regret。$\lambda\downarrow0$的最优解收敛不等于未知模型学习算法的收敛。
>- **方差比较。** 在定理4下$D\ne0$蕴含$\lambda/(N-D^2k_2)<\lambda/N$；这不是关于任意环境噪声强度的单调性定理，因为$k_2$本身也依赖模型参数。
>- **价值与成本。** $V_\lambda-V^{\mathrm{cl}}$含有熵项且可正可负；探索成本先扣除熵奖励，才等于$\lambda/(2\rho)$。

