本笔记作为随机LQ问题的工具箱使用，保留定义、可解性判据和求解公式，不展开一般性证明。主要参考Sun–Yong第一本书第2、3章，以及第二本书第1章。

>[!note] 查用入口
>- 判断开环最优：[[#开环解：凸性与FBSDE]]。
>- 构造闭环策略：[[#闭环解：正则Riccati方程]]、[[#非齐次项：BSDE与完整闭环判据]]。
>- 快速得到唯一解：[[#一致凸性与强正则解]]。
>- 只有凸性时：[[#正则化：寻找开环解]]。
>- 无限时域：[[#无限时域：稳定化代数Riccati方程]]。

# 问题与记号

以下$W$为一维标准Brownian motion，$\mathbb{F}$为其通常增广的自然滤过。状态$X\in\mathbb{R}^n$，控制$u\in\mathbb{R}^m$；矩阵系数为确定性的，非齐次项可以是随机过程。公式中省略同一时刻$s$的变量。

>[!def] 有限时域随机LQ问题（SLQ）
>状态方程为
>$$
>\begin{cases}
>{d}X(s)=(AX+Bu+b){d}s+(CX+Du+\sigma){d}W(s),\quad s\in[t,T],\\
>X(t)=x.
>\end{cases}\tag{SLQ}
>$$
>控制空间为
>$$
>\mathscr{U}[t,T]=L^2_{\mathbb{F}}(t,T;\mathbb{R}^m),\qquad
>\|u\|_{\mathscr{U}}^2=\mathbb{E}\int_t^T|u(s)|^2{d}s.
>$$
>指标泛函为
>$$
>\begin{aligned}
>J(t,x;u)=\mathbb{E}\bigg\{&\langle GX(T),X(T)\rangle+2\langle g,X(T)\rangle\\
>&+\int_t^T\big[\langle QX,X\rangle+2\langle SX,u\rangle+\langle Ru,u\rangle\\
>&\hspace{45mm}+2\langle q,X\rangle+2\langle\rho,u\rangle\big]{d}s\bigg\}.
>\end{aligned}\tag{J}
>$$
>其中$Q,G\in\mathbb{S}^n$，$R\in\mathbb{S}^m$，$S\in\mathbb{R}^{m\times n}$，交叉项的块矩阵为$\begin{bmatrix}Q&S^\top\\S&R\end{bmatrix}$。定义
>$$
>V(t,x)=\inf_{u\in\mathscr{U}[t,T]}J(t,x;u).
>$$
>令$b=\sigma=q=\rho=g=0$得到齐次问题（SLQ）$^0$，相应指标与值函数记为$J^0,V^0$。

>[!note] 基本假设（H1）–（H2）
>下文有限时域结论默认满足原书的可积性假设：
>$$
>\begin{aligned}
>&A\in L^1,\quad B,C\in L^2,\quad D\in L^\infty,\\
>&Q\in L^1(0,T;\mathbb{S}^n),\quad S\in L^2,\quad R\in L^\infty(0,T;\mathbb{S}^m),\quad G\in\mathbb{S}^n,\\
>&b,q\in L^2_{\mathbb{F}}(\Omega;L^1(0,T;\mathbb{R}^n)),\quad\sigma,\rho\in L^2_{\mathbb{F}},\quad g\in L^2_{\mathcal{F}_T}.
>\end{aligned}
>$$
>未注明的空间按变量取相应维数，时间区间为$(0,T)$。其中$L^2_{\mathbb{F}}(\Omega;L^1)$表示渐进可测且$\mathbb{E}(\int_0^T|f|{d}s)^2<\infty$。这些假设**不要求**$Q,R,G$非负。

# 开环与闭环的区别

>[!def] 开环最优控制
>固定初始对$(t,x)$，若$\bar{u}(\cdot;t,x)\in\mathscr{U}[t,T]$满足
>$$
>J(t,x;\bar{u})\le J(t,x;u),\qquad\forall u\in\mathscr{U}[t,T],
>$$
>则称$\bar{u}$为该初始对的开环最优控制。对每个$(t,x)$都存在这样的控制，称问题开环可解。

>[!def] 闭环最优策略
>闭环策略是一对
>$$
>(\Theta,v)\in L^2(t,T;\mathbb{R}^{m\times n})\times\mathscr{U}[t,T],
>$$
>其中$\Theta$为确定性函数，$v$为渐进可测过程。它生成控制
>$$
>u(s)=\Theta(s)X(s)+v(s).
>$$
>闭环状态满足
>$$
>\begin{cases}
>{d}X=[(A+B\Theta)X+Bv+b]{d}s+[(C+D\Theta)X+Dv+\sigma]{d}W,\\
>X(t)=x.
>\end{cases}
>$$
>若同一对$(\bar{\Theta},\bar{v})$对**所有**$x\in\mathbb{R}^n$都生成开环最优控制，则称其为$[t,T]$上的闭环最优策略；存在这样的策略，称问题在$[t,T]$上闭环可解。

>[!warning] 区别在量词与可容许性
>开环控制允许依赖初始状态$x$；闭环策略$(\Theta,v)$须独立于$x$，但它生成的控制仍通过$X$依赖$x$。
>
>开环控制可以是随机的、适应的，也可能具有反馈表示；“开环”不等于“确定性控制”。只把某个最优控制写成$\Theta X+v$，还不能说明它来自闭环最优策略。
>$$
>\text{闭环可解}\Longrightarrow\text{开环可解}\Longrightarrow\text{值函数有限},
>$$
>有限时域下，反向推论一般不成立。

# 开环解：凸性与FBSDE

>[!thm] 开环最优性的充要条件
>固定$(t,x)$。控制$\bar{u}\in\mathscr{U}[t,T]$开环最优，当且仅当以下两点同时成立：
>
>1. **凸性**：
>$$
>J^0(t,0;h)\ge0,\qquad\forall h\in\mathscr{U}[t,T].\tag{C}
>$$
>2. **最优性系统有适应解**$(\bar{X},\bar{Y},\bar{Z},\bar{u})$：
>$$
>\begin{cases}
>{d}\bar{X}=(A\bar{X}+B\bar{u}+b){d}s+(C\bar{X}+D\bar{u}+\sigma){d}W,\\
>{d}\bar{Y}=-(A^\top\bar{Y}+C^\top\bar{Z}+Q\bar{X}+S^\top\bar{u}+q){d}s+\bar{Z}{d}W,\\
>\bar{X}(t)=x,\qquad\bar{Y}(T)=G\bar{X}(T)+g,\\
>B^\top\bar{Y}+D^\top\bar{Z}+S\bar{X}+R\bar{u}+\rho=0.
>\end{cases}\tag{FBSDE}
>$$
>最后一式为驻值条件，按${d}s\otimes\mathbb{P}$几乎处处理解。它使前后向方程产生耦合。

判据的依据是二次展开：对任意控制$u$及其状态、伴随过程$(X,Y,Z)$，
$$
\begin{aligned}
J(t,x;u+h)-J(t,x;u)
=J^0(t,0;h)+2\mathbb{E}\int_t^T\langle B^\top Y+D^\top Z+SX+Ru+\rho,h\rangle{d}s.
\end{aligned}
$$
因此，**仅解出驻值条件不够，还必须检查凸性**；凸性成立时，驻值控制就是全局最优控制。

>[!proposition] Hilbert空间中的同一判据
>固定$(t,x)$后，可以把指标写成
>$$
>J(t,x;u)=\langle Mu,u\rangle_{\mathscr{U}}+2\langle\ell,u\rangle_{\mathscr{U}}+c,
>$$
>其中$M$为有界自伴算子，$\ell$为给定元素。于是
>$$
>\text{开环可解}\Longleftrightarrow M\ge0\text{ 且 }\ell\in\operatorname{Ran}M,
>$$
>最优控制满足$M\bar{u}+\ell=0$。若已有一个最优控制$\bar{u}_0$，则全体最优控制为$\bar{u}_0+\ker M$，因而唯一性等价于$\ker M=\{0\}$。
>
>若$M\ge\lambda I$，$\lambda>0$，则$\bar{u}=-M^{-1}\ell$唯一。一般的$M\ge0$不能保证最小值能取到，甚至不能单独保证值函数有限。

# 闭环解：正则Riccati方程

>[!def] 三个常用矩阵
>对$P\in\mathbb{S}^n$定义
>$$
>\begin{cases}
>\mathcal{Q}(P)=PA+A^\top P+C^\top PC+Q,\\
>\mathcal{S}(P)=B^\top P+D^\top PC+S,\\
>\mathcal{R}(P)=R+D^\top PD.
>\end{cases}\tag{QSR}
>$$
>$\mathcal{R}(P)$是反馈公式中实际需要处理的控制权重。$M^\dagger$表示Moore–Penrose伪逆，$\operatorname{Ran}M$表示矩阵的值域。

>[!def] 广义Riccati方程与正则解
>考虑
>$$
>\begin{cases}
>\dot{P}+\mathcal{Q}(P)-\mathcal{S}(P)^\top\mathcal{R}(P)^\dagger\mathcal{S}(P)=0,\\
>P(T)=G.
>\end{cases}\tag{GRE}
>$$
>解$P\in C([t,T];\mathbb{S}^n)$还须满足微分方程的积分形式。称$P$为**正则解**，若几乎处处满足
>$$
>\begin{cases}
>\mathcal{R}(P)\ge0,\\
>\operatorname{Ran}\mathcal{S}(P)\subseteq\operatorname{Ran}\mathcal{R}(P),\\
>\mathcal{R}(P)^\dagger\mathcal{S}(P)\in L^2(t,T;\mathbb{R}^{m\times n}).
>\end{cases}\tag{REG}
>$$
>三条分别保证非负性、矩阵方程的相容性、反馈增益的可容许性。

>[!proposition] 齐次问题的闭环判据
>（SLQ）$^0$在$[t,T]$上闭环可解，当且仅当（GRE）存在正则解$P$。可取
>$$
>\Theta_0=-\mathcal{R}(P)^\dagger\mathcal{S}(P),\qquad v_0=0,
>$$
>从而$\bar{u}=\Theta_0\bar{X}$，且
>$$
>V^0(t,x)=\langle P(t)x,x\rangle.
>$$
>正则解$P$若存在则唯一，但最优策略可能因$\mathcal{R}(P)$的核而不唯一。

>[!warning] 不能只检查Riccati方程本身
>“有对称解”与“有正则解”是两个不同的条件。尤其当$\mathcal{R}(P)$奇异时，不能只是把逆替换为伪逆，还要检查值域条件和增益的$L^2$可积性。

## 非齐次项：BSDE与完整闭环判据

>[!thm] 非齐次问题的闭环可解性
>一般（SLQ）在$[t,T]$上闭环可解，当且仅当：
>
>1.（GRE）有正则解$P$。
>
>2. 令$\Theta_0=-\mathcal{R}(P)^\dagger\mathcal{S}(P)$，求解
>$$
>\begin{cases}
>{d}\eta=-\big[(A+B\Theta_0)^\top\eta+(C+D\Theta_0)^\top\zeta\\
>\qquad\quad +(C+D\Theta_0)^\top P\sigma+\Theta_0^\top\rho+Pb+q\big]{d}s+\zeta{d}W,\\
>\eta(T)=g,
>\end{cases}\tag{BSDE}
>$$
>并记
>$$
>\kappa=B^\top\eta+D^\top\zeta+D^\top P\sigma+\rho,\qquad
>v_0=-\mathcal{R}(P)^\dagger\kappa.
>$$
>须进一步满足
>$$
>\kappa\in\operatorname{Ran}\mathcal{R}(P)\quad {d}s\otimes\mathbb{P}\text{-a.e.},\qquad
>v_0\in\mathscr{U}[t,T].\tag{COMP}
>$$
>此时全体闭环最优策略为
>$$
>\begin{cases}
>\bar{\Theta}=\Theta_0+[I_m-\mathcal{R}(P)^\dagger\mathcal{R}(P)]\Pi,\\
>\bar{v}=v_0+[I_m-\mathcal{R}(P)^\dagger\mathcal{R}(P)]\pi,
>\end{cases}\tag{FB}
>$$
>其中$\Pi\in L^2(t,T;\mathbb{R}^{m\times n})$、$\pi\in\mathscr{U}[t,T]$任意。实际求解时可先取$\Pi=\pi=0$。

>[!proposition] 值函数与配方恒等式
>在上述条件下，
>$$
>\begin{aligned}
>V(t,x)=\mathbb{E}\bigg\{&\langle P(t)x,x\rangle+2\langle\eta(t),x\rangle\\
>&+\int_t^T\big[\langle P\sigma,\sigma\rangle+2\langle\eta,b\rangle
>+2\langle\zeta,\sigma\rangle-\langle\mathcal{R}(P)^\dagger\kappa,\kappa\rangle\big]{d}s\bigg\}.
>\end{aligned}\tag{V}
>$$
>对任意$u\in\mathscr{U}[t,T]$及其对应状态$X=X(\cdot;t,x,u)$，
>$$
>J(t,x;u)-V(t,x)
>=\mathbb{E}\int_t^T\langle\mathcal{R}(P)(u-\bar{\Theta}X-\bar{v}),u-\bar{\Theta}X-\bar{v}\rangle{d}s.
>$$
>这里右侧用的是**待比较控制$u$自己的状态$X$**。这个恒等式可直接用于验证候选策略与计算最优性差距。

# 一致凸性与强正则解

>[!thm] 最常用的唯一可解性工具
>以下两条等价：
>$$
>J^0(0,0;u)\ge\lambda\mathbb{E}\int_0^T|u(s)|^2{d}s,
>\quad\forall u\in\mathscr{U}[0,T],\quad\text{某个 }\lambda>0;
>$$
>$$
>\text{（GRE）在 }[0,T]\text{ 上有强正则解，即 }\mathcal{R}(P)\ge\delta I_m\text{ a.e.，某个 }\delta>0.
>$$
>此时问题唯一开环可解，并在每个$[t,T]$上唯一闭环可解；伪逆可换成通常的逆：
>$$
>\bar{\Theta}=-\mathcal{R}(P)^{-1}\mathcal{S}(P),\qquad
>\bar{v}=-\mathcal{R}(P)^{-1}\kappa,\qquad
>\bar{u}=\bar{\Theta}\bar{X}+\bar{v}.
>$$

>[!proposition] 一个方便检查的充分条件
>若
>$$
>G\ge0,\qquad R\ge\delta I_m,\qquad Q-S^\top R^{-1}S\ge0,\quad\delta>0,
>$$
>则指标关于控制一致凸，因而上述唯一可解性结论成立。
>
>这是充分条件，并非必要条件。实际判据作用于整个泛函$J^0(t,0;\cdot)$；$R$本身不定甚至为负，仍可能由状态项和控制进入扩散项的作用获得一致凸性。

# 正则化：寻找开环解

当无法直接得到正则Riccati解时，仍可通过扰动问题寻找开环控制。

>[!proposition] $\varepsilon$-正则化判据
>固定$(t,x)$，先假设$J^0(t,0;h)\ge0$对所有$h$成立。定义
>$$
>J_\varepsilon(t,x;u)=J(t,x;u)+\varepsilon\|u\|_{\mathscr{U}}^2,\qquad\varepsilon>0.
>$$
>即把$R$替换为$R+\varepsilon I_m$，其余系数不变。每个扰动问题一致凸，可用Riccati方程和BSDE得到唯一最优控制$u_\varepsilon$。有
>$$
>\begin{aligned}
>\text{原问题在 }(t,x)\text{ 开环可解}
>&\Longleftrightarrow\sup_{0<\varepsilon\le1}\|u_\varepsilon\|_{\mathscr{U}}<\infty\\
>&\Longleftrightarrow u_\varepsilon\text{ 在 }\mathscr{U}[t,T]\text{ 中强收敛}.
>\end{aligned}
>$$
>极限是原问题的开环最优控制，并且是全体最优控制中范数最小的一个。这里只需要控制族$u_\varepsilon$有界，不能把它替换成反馈增益族$\Theta_\varepsilon$有界。

>[!example] 开环可解，但闭环不可解
>第一本书例2.1.6、§2.7：
>$$
>{d}X=(u_1+u_2){d}s+(u_1-u_2){d}W,\quad X(t)=x,\quad
>J(t,x;u)=\mathbb{E}|X(1)|^2.
>$$
>对每个$t<1$，取
>$$
>\bar{u}_1(s)=\bar{u}_2(s)=-\frac{x}{2(1-t)},\qquad
>\bar{X}(s)=\frac{1-s}{1-t}x,
>$$
>便有$\bar{X}(1)=0$，故$V(t,x)=0$且开环可解。
>
>但若同一闭环策略对所有$x$最优，则终端状态均为零。两初值$x_1\ne x_2$所生成状态的期望差却为
>$$
>\mathbb{E}X^{x_1}(1)-\mathbb{E}X^{x_2}(1)
>=\exp\left(\int_t^1(\Theta_1+\Theta_2){d}s\right)(x_1-x_2)\ne0,
>$$
>因为$\Theta\in L^2(t,1)$使该积分有限，产生矛盾。
>
>沿上述最优轨线可以形式上写成$\bar{u}_i(s)=-\bar{X}(s)/[2(1-s)]$，但这个增益不属于$L^2(t,1)$，因此不是本笔记定义下的闭环策略。

# 无限时域：稳定化代数Riccati方程

本节限于原书的**常系数**框架：$A,B,C,D,Q,S,R$为常矩阵，$b,\sigma,q,\rho$在$[0,\infty)$上渐进可测且平方可积。状态方程形式与（SLQ）相同，初值为$X(0)=x$；指标为运行费用在$[0,\infty)$上的积分，无终端项。

>[!def] 可容许控制与稳定化
>无限时域的可容许控制须同时满足
>$$
>\mathbb{E}\int_0^\infty|u(s)|^2{d}s<\infty,\qquad
>\mathbb{E}\int_0^\infty|X(s)|^2{d}s<\infty.
>$$
>若存在常矩阵$\Theta\in\mathbb{R}^{m\times n}$，使
>$$
>{d}X=(A+B\Theta)X{d}s+(C+D\Theta)X{d}W
>$$
>对所有初值都满足状态平方可积，则称系统$L^2$-可稳定化，$\Theta$称为稳定化增益。以下默认系统$L^2$-可稳定化。

>[!proposition] 检查给定增益是否稳定化
>令$A_\Theta=A+B\Theta$，$C_\Theta=C+D\Theta$。增益$\Theta$稳定化，当且仅当存在$H\in\mathbb{S}^n$使
>$$
>H>0,\qquad HA_\Theta+A_\Theta^\top H+C_\Theta^\top HC_\Theta<0.
>$$
>也可求解Lyapunov方程$HA_\Theta+A_\Theta^\top H+C_\Theta^\top HC_\Theta+I_n=0$并检查$H>0$。

>[!thm] 齐次无限时域问题的核心等价关系
>在上述常系数、$L^2$-可稳定化框架下，
>$$
>\text{开环可解}\Longleftrightarrow\text{闭环可解}\Longleftrightarrow\text{GARE存在稳定化解}.
>$$
>这里GARE为
>$$
>\begin{cases}
>\mathcal{Q}(P)-\mathcal{S}(P)^\top\mathcal{R}(P)^\dagger\mathcal{S}(P)=0,\\
>\operatorname{Ran}\mathcal{S}(P)\subseteq\operatorname{Ran}\mathcal{R}(P),\\
>\mathcal{R}(P)\ge0,
>\end{cases}\tag{GARE}
>$$
>未知量$P\in\mathbb{S}^n$为常矩阵。“稳定化解”还要求能选常矩阵$\Pi$，使
>$$
>\bar{\Theta}=-\mathcal{R}(P)^\dagger\mathcal{S}(P)
>+[I_m-\mathcal{R}(P)^\dagger\mathcal{R}(P)]\Pi
>$$
>成为稳定化增益。可取$\bar{v}=0$，且$V^0(x)=\langle Px,x\rangle$。只求出GARE的代数解还不够，必须检查稳定化。

>[!note] 非齐次无限时域问题
>仍有“开环可解$\Longleftrightarrow$闭环可解”，但仅有GARE稳定化解还不够。还须将[[#非齐次项：BSDE与完整闭环判据|（BSDE）]]中的$P$取为该常矩阵，$\Theta_0=-\mathcal{R}(P)^\dagger\mathcal{S}(P)$，在$[0,\infty)$上求解。
>
>无限时域用$L^2$-稳定适应解条件替代$\eta(T)=g$：$\eta$连续，$\eta,\zeta\in L^2_{\mathbb{F}}(0,\infty;\mathbb{R}^n)$。仍须检查$\kappa\in\operatorname{Ran}\mathcal{R}(P)$。由于$\mathcal{R}(P)^\dagger$为常矩阵，此时$\mathcal{R}(P)^\dagger\kappa$的平方可积性自动成立。
>
>最优策略仍由（FB）给出，但$\Pi$必须选成使$\bar{\Theta}$稳定化的常矩阵，$\pi\in L^2_{\mathbb{F}}(0,\infty;\mathbb{R}^m)$任意；不可直接假定$\Pi=0$就稳定。每个开环最优控制都可由某个闭环最优策略生成。

# 实际使用顺序

1. 确定有限或无限时域、齐次或非齐次，并检查系数维数及可积性。
2. 有限时域先检查一致凸性的充分条件；满足时直接解Riccati方程，非齐次问题再解BSDE。
3. 不满足方便的充分条件时，继续检查$J^0(t,0;\cdot)$的凸性，以及Riccati解的正则条件，不能仅凭$R$的符号作判断。
4. 只需固定初始对的开环控制时，使用FBSDE判据或$\varepsilon$-正则化；不能要求一定存在可容许的反馈增益。
5. 无限时域先检查可稳定化，再检查GARE的稳定化解；非齐次时补上无限时域BSDE与值域条件。

相关笔记：[[线性二次的最优控制]]、[[Linear SDE]]。取$C=D=\sigma=0$并令其余数据确定性，即得到确定性LQ的相应公式。

---
# 参考与定位

页码均指书内印刷页码。

- Sun, J. & Yong, J. (2020). *[Stochastic Linear-Quadratic Optimal Control Theory: Open-Loop and Closed-Loop Solutions](https://doi.org/10.1007/978-3-030-20922-3)*。
  - §1.3：Hilbert空间二次泛函与正则化，命题1.3.1、1.3.4，pp.6–10。
  - §2.1、§2.3–2.5：定义、开环与闭环判据、一致凸性，定理2.3.2、2.4.3、2.5.6，pp.13–18、26–48。
  - §2.6–2.7：正则化判据与反例，定理2.6.2、例2.1.6，pp.49–59。
  - §3.2、§3.6：稳定性与无限时域可解性，定理3.2.3、3.6.2、推论3.6.3，pp.63–67、89–98。
- Sun, J. & Yong, J. (2020). *[Stochastic Linear-Quadratic Optimal Control Theory: Differential Games and Mean-Field Problems](https://doi.org/10.1007/978-3-030-48306-7)*，仅使用第1章，pp.1–13。
  - 有限时域：定义1.1.1–1.1.11，定理1.1.9、1.1.12、1.1.14–1.1.15。
  - 无限时域：定义1.2.1–1.2.7，定理1.2.8；伪逆及无限时域BSDE：§1.3。

原作者相关论文核对入口：[有限时域的开环与闭环可解性](https://arxiv.org/abs/1508.02163)、[无限时域随机LQ问题](https://arxiv.org/abs/1610.05021)。
