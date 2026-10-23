---
publish: 2016
tag: 随机控制, BSDE, FBSDE, 最大值原理, 动态规划, HJB, 粘性解
---

>[!note] 文献信息
>Tianyang Nie, Jingtao Shi & Zhen Wu. *Connection between MP and DPP for Stochastic Recursive Optimal Control Problems: Viscosity Solution Framework in Local Case*. 2016.
>
>[arXiv:1603.02596v1](https://arxiv.org/abs/1603.02596v1)，2016-03-07，6页；arXiv注明已被2016 American Control Conference接收。本笔记依据所读的arXiv v1版本整理，不混用其他后续版本的结论。
>
>阅读整理：2026-10-23。以下页码为PDF页码；数字公式编号对应原文，带文字的编号为本笔记补充或修正。主定理和原文证明路线与补充解释、勘误分开标明。

>[!note] 本文的主要工作
>- 在**确定性系数、凸控制域、标量递归代价**的随机控制框架下，去掉价值函数的可微性假设，建立伴随过程与价值函数空间一阶上、下微分之间的关系。
>- 主结论为沿最优轨道的$D_x^{1,-}V\subseteq\{p/q\}\subseteq D_x^{1,+}V$。光滑时恢复$p=qV_x$，但本文没有给出关于$k,V_{xx}$或$V_t$的完整非光滑对应。
>- 证明的核心是**固定最优控制，扰动初始状态**，对FBSDE作一阶展开，再利用伴随对偶与DPP，把固定控制的代价敏感性变成价值函数的上支撑斜率。
>- 例3.1说明价值函数可在整段最优轨道上不可微，且主定理两侧的包含都可以严格。这里“整段”应排除终端时刻$T$。
>- 标题中的“Local Case”指凸控制域下的一阶局部最大值原理框架，不是短时间区间的FBSDE适定性结论。

>[!note] 查用入口
>- 模型、符号和假设：[[#问题与基本假设]]。
>- HJB与伴随系统：[[#动态规划与最大值原理]]。
>- 上、下微分及其判别：[[#空间一阶上微分与下微分]]。
>- 直接引用主定理：[[#主定理：非光滑MP与DPP的关系]]。
>- 核心证明和余项估计：[[#主定理的证明路线]]。
>- 非光滑例子：[[#例3.1：最优轨道上的不可微值函数]]。
>- 符号勘误和使用范围：[[#原文核查与使用边界]]。

# 问题与基本假设

>[!def] 受控FBSDE与递归控制问题（第2页，式(4)–(7)）
>固定$(t,x)\in[0,T)\times\mathbb R^n$，$W$为$d$维Brownian motion，$U\subseteq\mathbb R^m$非空且凸。考虑
>$$
>\begin{cases}
>{d}X_r=b(r,X_r,u_r){d}r+\sigma(r,X_r,u_r){d}W_r,\\
>-{d}Y_r=f(r,X_r,Y_r,Z_r,u_r){d}r-Z_r^\top{d}W_r,\\
>X_t=x,\qquad Y_T=\phi(X_T).
>\end{cases}\tag{4,5}
>$$
>其中$X\in\mathbb R^n$，$Y\in\mathbb R$，$Z\in\mathbb R^d$，$\sigma\in\mathbb R^{n\times d}$；$b,\sigma,f,\phi$为确定性函数。前向系数不依赖于$(Y,Z)$，因此不是一般全耦合FBSDE。
>$$
>J(t,x;u):=-Y_t^{t,x;u},\qquad
>V(t,x):=\inf_{u\in\mathscr U^w[t,T]}J(t,x;u),\qquad V(T,x)=-\phi(x).\tag{6,7}
>$$
>原文采用弱表述：$\mathscr U^w[t,T]$的元素是$(\Omega,\mathcal F,\mathbb P,W;u)$，概率空间也是可容许系统的一部分。滤过$\mathbb F^t$由从$t$开始的Brownian运动生成并作通常增广。最优四元组记为$(\bar X,\bar Y,\bar Z,\bar u)$，主定理以它已经存在为前提。

>[!warning] 符号和维数约定
>本文最小化$-Y_t$，不是$Y_t$。沿最优轨道的DPP关系为
>$$
>V(s,\bar X_s)=-\bar Y_s.
>$$
>本笔记把$V_x,f_x,f_z,\phi_x$统一写为列向量；用$\sigma^j$表示扩散矩阵的第$j$列，$\sigma_x^j\in\mathbb R^{n\times n}$表示其Jacobi矩阵。$k^j$为$k\in\mathbb R^{n\times d}$的第$j$列。原文部分转置及扩散导数的缩写不够明确，以下按维数一致的形式书写。

>[!def] 基本假设（H1）–（H3）（第2–3页）
>**（H1）前向系数。** $b,\sigma$关于$(s,x,u)$一致连续，对$x$一致Lipschitz，且对$u$一致满足线性增长：
>$$
>\begin{aligned}
>&|b(s,x,u)-b(s,x',u)|+|\sigma(s,x,u)-\sigma(s,x',u)|\le C|x-x'|,\\
>&|b(s,x,u)|+|\sigma(s,x,u)|\le C(1+|x|).
>\end{aligned}
>$$
>**（H2）后向系数。** $f,\phi$在各自变量上一致连续，$f$对$(x,y,z)$一致Lipschitz，$\phi$对$x$一致Lipschitz，并满足
>$$
>\begin{aligned}
>&|f(s,x,y,z,u)-f(s,x',y',z',u)|\le C(|x-x'|+|y-y'|+|z-z'|),\\
>&|f(s,x,0,0,u)|+|\phi(x)|\le C(1+|x|),\\
>&|\phi(x)-\phi(x')|\le C|x-x'|.
>\end{aligned}
>$$
>**（H3）状态方向可微性。** $b,\sigma$对$x$、$\phi$对$x$、$f$对$(x,y,z)$连续可微，相关一阶偏导一致有界。
>
>（H3）是系数的可微性假设，不是$V$的可微性假设。原文此处没有明确列出关于$u$的可微性；单独引用含$H_u$的Proposition 2.3时，应另行核对这一条件，见[[#原文核查与使用边界]]。

>[!proposition] 价值函数的基本性质（Propositions 2.1–2.2，第2–3页）
>在本文的确定性系数与控制框架下，$V$为确定性函数，并有
>$$
>|V(s,x)-V(s,x')|\le C|x-x'|,\qquad |V(s,x)|\le C(1+|x|).\tag{10}
>$$
>原文引用Peng的结果，将$V$识别为广义HJB的唯一粘性解。引用唯一性时应保留相应比较定理的增长类等条件，不应把它理解为对所有无增长限制的连续函数都唯一。

# 动态规划与最大值原理

>[!def] 广义Hamiltonian与HJB（第2页，式(8)–(9)）
>用$\xi$表示梯度参数，以免与伴随过程$p$混淆：
>$$
>G(s,x,r,\xi,A,u)=\frac12\operatorname{tr}(\sigma(s,x,u)^\top A\sigma(s,x,u))+\langle\xi,b(s,x,u)\rangle+f(s,x,r,\sigma(s,x,u)^\top\xi,u).\tag{9}
>$$
>HJB为
>$$
>\begin{cases}
>-v_s(s,x)+\displaystyle\sup_{u\in U}G(s,x,-v(s,x),-v_x(s,x),-v_{xx}(s,x),u)=0,\\
>v(T,x)=-\phi(x).
>\end{cases}\tag{8}
>$$
>粘性下解：$v(T,x)\le-\phi(x)$，且当$\psi\in C^{1,2}$使$v-\psi$在$(s,x)$局部取极大时，
>$$
>-\psi_s+\sup_{u\in U}G(s,x,-v,-\psi_x,-\psi_{xx},u)\le0.
>$$
>粘性上解把终端不等式反向、局部极大改为局部极小，并要求算子值$\ge0$；同时满足两者即为粘性解。注意代入的是函数值$v$及测试函数的导数。

>[!def] MP Hamiltonian与伴随方程（第3页，式(12)–(13)）
>定义
>$$
>H(s,x,y,z,u,p,q,k)=\langle p,b(s,x,u)\rangle-qf(s,x,y,z,u)+\operatorname{tr}(\sigma(s,x,u)^\top k).\tag{13}
>$$
>横线表示沿$(\bar X,\bar Y,\bar Z,\bar u)$取值，伴随系统为
>$$
>\begin{cases}
>-{d}p_r=\left[\bar b_x(r)^\top p_r-\bar f_x(r)q_r+\displaystyle\sum_{j=1}^d(\bar\sigma_x^j(r))^\top k_r^j\right]{d}r-k_r{d}W_r,\\
>{d}q_r=\bar f_y(r)q_r{d}r+q_r\bar f_z(r)^\top{d}W_r,\\
>p_T=-\phi_x(\bar X_T)q_T,\qquad q_t=1.
>\end{cases}\tag{12}
>$$
>$p\in\mathbb R^n$，$q\in\mathbb R$，$k\in\mathbb R^{n\times d}$。这里$q$为前向过程，$(p,k)$由线性BSDE确定；$G$与$H$是不同的Hamiltonian。

>[!lemma] 正的随机积分因子（由式(12)直接求解）
>$$
>q_s=\exp\left\{\int_t^s\left(\bar f_y(r)-\frac12|\bar f_z(r)|^2\right){d}r+\int_t^s\bar f_z(r)^\top{d}W_r\right\}>0.\tag{积分因子}
>$$
>所以$q_s^{-1}$存在。由$\bar f_y,\bar f_z$有界，可获得$q,q^{-1}$的有限阶矩估计。$p/q$是经递归代价积分因子归一化后的状态敏感性；即使系数是确定性函数，沿轨道取值的$\bar f_y,\bar f_z$以及$q$一般仍然随机。

>[!proposition] 必要最大值原理（Proposition 2.3，第3页，式(14)）
>在所引用MP的正则性条件下，最优控制满足
>$$
>\left\langle H_u(s,\bar X_s,\bar Y_s,\bar Z_s,\bar u_s,p_s,q_s,k_s),u-\bar u_s\right\rangle\ge0,\qquad\forall u\in U,\tag{14}
>$$
>按${d}s\otimes\mathbb P$几乎处处理解。这是凸控制域的一阶变分必要条件，不是一般的充分最优性条件。
>
>主定理3.1的证明使用**伴随方程本身与已知最优性**，不直接使用(14)中的$H_u$不等式。原文Remark 2.2说明：MP原结果采用强表述，本文为了DPP采用弱表述；结论在给定最优四元组所在的概率空间上讨论。

# 空间一阶上微分与下微分

>[!def] 一阶super-/sub-jet（第3页，式(15)）
>固定$s$，对$V(s,\cdot)$定义
>$$
>\begin{aligned}
>D_x^{1,+}V(s,x_0)&=\left\{a\in\mathbb R^n:V(s,x_0+h)\le V(s,x_0)+\langle a,h\rangle+o(|h|)\right\},\\
>D_x^{1,-}V(s,x_0)&=\left\{a\in\mathbb R^n:V(s,x_0+h)\ge V(s,x_0)+\langle a,h\rangle+o(|h|)\right\}.
>\end{aligned}\tag{15}
>$$
>等价地，上微分要求归一化差商的$\limsup\le0$，下微分要求$\liminf\ge0$，其中差商为
>$$
>\frac{V(s,x_0+h)-V(s,x_0)-\langle a,h\rangle}{|h|},\qquad h\to0.
>$$
>上、下指支撑的位置，不指左右导数，也不是Clarke广义梯度。这是一阶空间jet，不是HJB检验使用的时空二阶jet。

>[!note] 与光滑接触的联系
>$a\in D_x^{1,+}V(s,x_0)$等价于存在局部$C^1$函数$\psi$从上方接触$V(s,\cdot)$，且$D\psi(x_0)=a$；下微分对应从下方接触。上方测试函数用来检验粘性下解，下方测试函数用来检验粘性上解。
>
>允许$o(|h|)$意味着只要求一阶支撑。例如$f(x)=x^2$在$0$有$D^-f(0)=D^+f(0)=\{0\}$，虽然直线$y=0$在抛物线下方；因为$h^2=o(|h|)$，也可用$2x^2$从上方接触。

>[!lemma] 上下微分同时非空则可微（内点的一阶结论）
>若$a\in D^+v(x_0)$、$b\in D^-v(x_0)$，则$a=b$，且$v$在$x_0$可微。因此
>$$
>D^+v(x_0)\ne\varnothing,\quad D^-v(x_0)\ne\varnothing
>\quad\Longrightarrow\quad D^-v(x_0)=D^+v(x_0)=\{Dv(x_0)\}.
>$$

**Proof**

由上下支撑有$\langle b-a,h\rangle\le o(|h|)$。分别取$h=\varepsilon e$与$h=-\varepsilon e$，$\varepsilon\downarrow0$，得到$\langle b-a,e\rangle=0$，故$a=b$。再由上下夹逼得到$v(x_0+h)-v(x_0)=\langle a,h\rangle+o(|h|)$。

**QED**

>[!example] 典型折角
>$$
>\begin{aligned}
>&D^-|x|(0)=[-1,1],\qquad D^+|x|(0)=\varnothing,\\
>&D^-(-|x|)(0)=\varnothing,\qquad D^+(-|x|)(0)=[-1,1].
>\end{aligned}
>$$
>对向下折角，上方可以有多个支撑斜率，下方则没有一阶支撑。主定理允许的不可微性正包括这种情形。

# 主定理：非光滑MP与DPP的关系

>[!thm] Theorem 3.1（第3页，式(16)）
>设（H1）–（H3）成立，$U$非空且凸，固定$(t,x)\in[0,T)\times\mathbb R^n$。假设$\bar u$是最优控制，$(\bar X,\bar Y,\bar Z)$为相应最优状态，$(p,q,k)$满足(12)。则
>$$
>\boxed{
>D_x^{1,-}V(s,\bar X_s)
>\subseteq\left\{p_sq_s^{-1}\right\}
>\subseteq D_x^{1,+}V(s,\bar X_s).
>}\tag{16}
>$$
>原文表述为$\forall s\in[t,T],\mathbb P$-a.s.；证明首先固定确定性$s$再构造概率1事件。查用时至少可按“对每个固定$s$，几乎处处成立”理解；若需同一事件上所有$s$同时成立，需另核对版本与正则性，不能交换量词而不说明。
>
>原文$\subset$表示允许相等的包含。终端处$V(T,x)=-\phi(x)$，故两侧微分均为$\{-\phi_x(\bar X_T)\}$，与$p_T/q_T$一致。

>[!note] 结论的准确含义
>1. 对给定最优控制，$p_s/q_s$给出一个空间上微分；因此沿该轨道上微分非空。
>2. 下微分若存在，只能等于$p_s/q_s$；但它可以为空，因此不能由(16)断言$V$沿最优轨道可微。
>3. 若$V(s,\cdot)$在$\bar X_s$可微，则
>   $$
>   p_sq_s^{-1}=V_x(s,\bar X_s).\tag{28}
>   $$
>4. 不同最优控制可能选出不同的上微分。主定理没有证明上微分集合等于所有最优控制所产生的$p/q$的集合。
>5. 此结论推广了光滑关系的**梯度部分**；不能据此推出$k=q(V_{xx}\bar\sigma+V_x\bar f_z^\top)$在不可微情形仍有经典意义。

# 主定理的证明路线

>[!note] 证明骨架
>固定最优控制并扰动状态$\Longrightarrow$条件矩估计与一阶余项$\Longrightarrow$对$\langle\widehat X,p\rangle+\widehat Yq$用Itô公式$\Longrightarrow$固定控制代价的一阶展开$\Longrightarrow$DPP给出上支撑$\Longrightarrow$上下支撑夹逼。
>
>证明不对$V$使用Itô公式，也不对最优反馈关于$x$求导；不需要在此重新用Crandall–Ishii引理证明HJB比较定理。

**Proof**

**Step1：固定$s$，固定控制$\bar u$，扰动状态。**

从$(s,x^1)$出发，在$[s,T]$仍使用原控制$\bar u$，记新解为$(X^{s,x^1;\bar u},Y^{s,x^1;\bar u},Z^{s,x^1;\bar u})$，定义
$$
\widehat X_r=X_r^{s,x^1;\bar u}-\bar X_r,\qquad
\widehat Y_r=Y_r^{s,x^1;\bar u}-\bar Y_r,\qquad
\widehat Z_r=Z_r^{s,x^1;\bar u}-\bar Z_r,
\qquad h=x^1-\bar X_s.
$$
这里$h$在原概率空间中是$\mathcal F_s^t$可测的。原文用正则条件概率$\mathbb P(\cdot\mid\mathcal F_s^t)(\omega)$固定过去历史，使后续系统成为从$s$出发的可容许系统，并用于与确定性值函数$V(s,x^1)$比较。

记$\mathbb E_s=\mathbb E[\cdot\mid\mathcal F_s^t]$。对整数$m\ge1$，条件稳定性估计给出
$$
\mathbb E_s\left[\sup_{s\le r\le T}|\widehat X_r|^{2m}+\sup_{s\le r\le T}|\widehat Y_r|^{2m}+\left(\int_s^T|\widehat Z_r|^2{d}r\right)^m\right]\le C_m|h|^{2m}.\tag{18,19}
$$
$\widehat X,\widehat Y$有上确界矩估计，而$\widehat Z$的基本控制是时间$L^2$范数，不能把后者换成逐时刻或上确界估计。

**Step2：把状态差方程写成线性部分加余项。**

沿原最优轨道展开，得到
$$
\begin{cases}
{d}\widehat X_r=[\bar b_x(r)\widehat X_r+\varepsilon_1(r)]{d}r+\displaystyle\sum_{j=1}^d[\bar\sigma_x^j(r)\widehat X_r+\varepsilon_2^j(r)]{d}W_r^j,\\
\widehat X_s=h,
\end{cases}\tag{20}
$$
$$
\begin{cases}
-{d}\widehat Y_r=[\langle\bar f_x(r),\widehat X_r\rangle+\bar f_y(r)\widehat Y_r+\langle\bar f_z(r),\widehat Z_r\rangle+\varepsilon_3(r)]{d}r-\widehat Z_r^\top{d}W_r,\\
\widehat Y_T=\langle\phi_x(\bar X_T),\widehat X_T\rangle+\varepsilon_4.
\end{cases}\tag{21}
$$
例如
$$
\varepsilon_1(r)=\int_0^1[b_x(r,\bar X_r+\theta\widehat X_r,\bar u_r)-\bar b_x(r)]\widehat X_r\,{d}\theta.
$$
$\varepsilon_2^j$同理用$\sigma_x^j$定义，$\varepsilon_4$用$\phi_x$定义。记
$$
\Delta f_i(r,\theta)=f_i(r,\bar X_r+\theta\widehat X_r,\bar Y_r+\theta\widehat Y_r,\bar Z_r+\theta\widehat Z_r,\bar u_r)-\bar f_i(r),\quad i=x,y,z,
$$
则
$$
\varepsilon_3(r)=\int_0^1\left[\langle\Delta f_x(r,\theta),\widehat X_r\rangle+\Delta f_y(r,\theta)\widehat Y_r+\langle\Delta f_z(r,\theta),\widehat Z_r\rangle\right]{d}\theta.
$$

原文(22)–(23)以$\delta(\rho)/\rho\to0$的余项模量表述估计；对后面的对偶计算，所需的量级可概括为
$$
\mathbb E_s\left[\int_s^T(|\varepsilon_1(r)|^2+|\varepsilon_2(r)|^2){d}r+|\varepsilon_4|^2\right]=o(|h|^2),\tag{22概括}
$$
以及对某个$\alpha\in(0,1)$，
$$
\mathbb E_s\int_s^T|\varepsilon_3(r)|^{1+\alpha}{d}r=o(|h|^{1+\alpha}).\tag{23}
$$
这些是**条件矩意义下的余项估计**，不是声称每个时刻都有$\varepsilon_i(r)=o(|h|)$。原文还需要在固定历史后取得适合所有邻近扰动的余项控制，才能在Step5得到路径上的jet结论。

**Step3：处理含$\widehat Z$的余项，使用$1+\alpha<2$留出Hölder余量。**

设$A_r=\int_0^1\Delta f_z(r,\theta){d}\theta$。关键项为
$$
I_z=\mathbb E_s\int_s^T|A_r|^{1+\alpha}|\widehat Z_r|^{1+\alpha}{d}r.
$$
取共轭指数$a=2/(1-\alpha)$、$b=2/(1+\alpha)$，先在时间上使用Hölder，再在条件期望上使用Cauchy–Schwarz，得到
$$
\begin{aligned}
I_z\le&\left\{\mathbb E_s\left(\int_s^T|A_r|^{\frac{2(1+\alpha)}{1-\alpha}}{d}r\right)^{1-\alpha}\right\}^{1/2}\\
&\quad\cdot\left\{\mathbb E_s\left(\int_s^T|\widehat Z_r|^2{d}r\right)^{1+\alpha}\right\}^{1/2}
=o(1)\,O(|h|^{1+\alpha}).
\end{aligned}
$$
第二因子由(19)及矩的插值控制；第一因子来自$f_z$有界、连续以及扰动收敛，可用有界性与收敛论证使其趋于0。$\Delta f_x\widehat X$和$\Delta f_y\widehat Y$类似处理。

不能仅从$\widehat Z\to0$于时间$L^2$，便宣称任意扰动族都逐时刻几乎处处收敛。严格推广时应明确使用的测度收敛、子列、条件版本及统一余项控制。

**Step4：伴随对偶，消去所有一阶状态差。**

令
$$
S_r=\langle\widehat X_r,p_r\rangle+\widehat Y_rq_r.
$$
按列计算Itô乘积公式，其漂移分别为
$$
\begin{aligned}
{d}\langle\widehat X,p\rangle\big|_{{d}r}
&=q\langle\bar f_x,\widehat X\rangle+\langle\varepsilon_1,p\rangle+\sum_{j=1}^d\langle\varepsilon_2^j,k^j\rangle,\\
{d}(\widehat Yq)\big|_{{d}r}
&=-q\langle\bar f_x,\widehat X\rangle-q\varepsilon_3.
\end{aligned}\tag{对偶抵消}
$$
其中$\bar b_x$项、$\bar\sigma_x$与协变差项、$\bar f_y$项、$\bar f_z$与协变差项依次抵消。因此
$$
{d}S_r=\left[\langle\varepsilon_1(r),p_r\rangle+\langle\varepsilon_2(r),k_r\rangle_F-\varepsilon_3(r)q_r\right]{d}r+{d}M_r,
$$
其中$\langle A,B\rangle_F=\operatorname{tr}(A^\top B)$，$M$表示随机积分项；取条件期望前使用相应可积性或先局部化。终端条件给出$S_T=\varepsilon_4q_T$，于是
$$
\begin{aligned}
\widehat Y_sq_s
=&-\langle h,p_s\rangle+\mathbb E_s[\varepsilon_4q_T]
-\mathbb E_s\int_s^T\langle\varepsilon_1(r),p_r\rangle{d}r\\
&-\mathbb E_s\int_s^T\langle\varepsilon_2(r),k_r\rangle_F{d}r
+\mathbb E_s\int_s^T\varepsilon_3(r)q_r{d}r.
\end{aligned}\tag{24修正}
$$
**按原文(21)的$\varepsilon_3$定义，最后一项应为正号；原文(24)印成负号。** 该符号不影响将余项取绝对值后证明$o(|h|)$，但记录精确对偶恒等式时应修正。

例如，扩散余项应估计为
$$
\left|\mathbb E_s\int_s^T\langle\varepsilon_2,k\rangle_F{d}r\right|
\le\left(\mathbb E_s\int_s^T|\varepsilon_2|^2{d}r\right)^{1/2}
\left(\mathbb E_s\int_s^T|k|^2{d}r\right)^{1/2}=o(|h|).
$$
令$\beta=(1+\alpha)/\alpha$，递归余项则由
$$
\begin{aligned}
\left|\mathbb E_s\int_s^T\varepsilon_3q\,{d}r\right|
&\le\left(\mathbb E_s\sup_{s\le r\le T}|q_r|^\beta\right)^{1/\beta}
\left[\mathbb E_s\left(\int_s^T|\varepsilon_3(r)|{d}r\right)^{1+\alpha}\right]^{1/(1+\alpha)}\\
&=o(|h|)
\end{aligned}
$$
控制。其他余项同理由条件Cauchy–Schwarz控制。得到
$$
\widehat Y_sq_s=-\langle h,p_s\rangle+o(|h|),\qquad
\widehat Y_s=-\langle p_sq_s^{-1},h\rangle+o(|h|).\tag{25,26}
$$

**Step5：DPP与最优性把代价展开变成价值函数上支撑。**

在原文的条件概率框架下，对固定历史$\omega$，原控制的延续是从$s$出发的可容许控制。因此
$$
V(s,x^1)\le-Y_s^{s,x^1;\bar u},\qquad V(s,\bar X_s)=-\bar Y_s.
$$
第一式只用可容许性，第二式用DPP及最优延续性质。二式相减并代入(26)，得到
$$
V(s,x^1)-V(s,\bar X_s)
\le-\widehat Y_s
=\langle p_sq_s^{-1},x^1-\bar X_s\rangle+o(|x^1-\bar X_s|).\tag{27}
$$
故$p_sq_s^{-1}\in D_x^{1,+}V(s,\bar X_s)$。

这里不能省略随机参数与零测集的处理：原文先在有理坐标的$x^1$上取可数交，得到共同概率1事件，再利用$V(s,\cdot)$的连续性及固定历史下统一的余项控制延拓到所有$x^1$。仅说“每个$x^1$分别几乎处处成立”不足以得到路径上的jet不等式。

**Step6：下微分包含由两侧夹逼得到。**

取$\xi\in D_x^{1,-}V(s,\bar X_s)$，与(27)合并可得
$$
\langle\xi-p_sq_s^{-1},h\rangle\le o(|h|).
$$
分别取$h=\varepsilon e$与$h=-\varepsilon e$并令$\varepsilon\downarrow0$，得到$\xi=p_sq_s^{-1}$。若下微分为空，左侧包含自动成立。至此得到(16)。

**QED**

# 例3.1：最优轨道上的不可微值函数

>[!example] 模型与值函数（第5页，式(29)–(33)）
>令$n=d=1$、$U=[0,1]$，考虑
>$$
>\begin{cases}
>{d}X_r=X_ru_r{d}r+X_r{d}W_r,\qquad X_t=x,\\
>-{d}Y_r=(X_r-Y_r){d}r-Z_r{d}W_r,\qquad Y_T=X_T,\\
>J(t,x;u)=-Y_t.
>\end{cases}\tag{29–31}
>$$
>对应HJB为
>$$
>\begin{cases}
>-v_t-\dfrac12x^2v_{xx}+x+v+\displaystyle\sup_{u\in[0,1]}\{-xuv_x\}=0,\\
>v(T,x)=-x.
>\end{cases}\tag{32}
>$$
>价值函数为
>$$
>V(t,x)=\begin{cases}
>-x,&x\le0,\\
>-(T-t+1)x,&x>0.
>\end{cases}\tag{33}
>$$
>原文(29)直接写$X_t=0$，是后面比较最优轨道时的特殊初值；讨论全空间值函数(33)时应使用一般初值$x$。

**值函数的直接核验（本笔记补充）**

前向解为
$$
X_r=x\exp\left\{\int_t^r(u_a-\tfrac12){d}a+W_r-W_t\right\},
$$
符号保持不变。线性BSDE给出
$$
Y_t=\mathbb E_t\left[e^{-(T-t)}X_T+\int_t^T e^{-(r-t)}X_r{d}r\right].
$$
当$x>0$时，同一Brownian路径下$X_r^u\le X_r^{u\equiv1}$，故$u\equiv1$最大化$Y_t$，得到$Y_t=x(T-t+1)$；当$x<0$时，$X_r^u\le X_r^{u\equiv0}$，故$u\equiv0$最优，得到$Y_t=x$。当$x=0$时，任何控制均有$X=Y=Z=0$，所以全部可容许控制都最优。这直接验证了(33)。

>[!note] 沿$\bar u\equiv0$的主定理核验
>取$x=0$、$\bar u\equiv0$，则$\bar X_s\equiv0$，伴随系统为
>$$
>\begin{cases}
>-{d}p_s=[\bar u_sp_s-q_s+k_s]{d}s-k_s{d}W_s,\\
>{d}q_s=-q_s{d}s,\\
>p_T=-q_T,\qquad q_t=1.
>\end{cases}\tag{34}
>$$
>解为$(p_s,q_s,k_s)=(-e^{t-s},e^{t-s},0)$，从而$p_s/q_s=-1$。对$s<T$，
>$$
>D_x^{1,-}V(s,0)=\varnothing,\qquad D_x^{1,+}V(s,0)=[-(T-s+1),-1].\tag{35}
>$$
>因此
>$$
>\varnothing\subsetneq\{-1\}\subsetneq[-(T-s+1),-1].
>$$
>到$s=T$时，$V(T,x)=-x$，两侧微分均为$\{-1\}$；原文“整个$[t,T]$上不可微”和下微分恒空的表述应修正为$s<T$。

>[!note] 不同最优控制可对应不同支撑斜率（本笔记补充）
>在同一个初值$x=0$上，$\bar u\equiv1$也最优。此时$q_s=e^{t-s}$、$k_s=0$，令$R_s=p_s/q_s$，由(34)得$\dot R_s=1$、$R_T=-1$，故
>$$
>\frac{p_s}{q_s}=-(T-s+1).
>$$
>它给出上微分区间的另一个端点。这说明$p/q$依赖所选最优控制，而价值函数及其上微分集合是同一个对象。

# 原文核查与使用边界

>[!warning] 确认的符号与排版问题
>- **式(24)的$\varepsilon_3$项符号。** 按(21)的正余项定义，$S=\langle\widehat X,p\rangle+\widehat Yq$的漂移中为$-q\varepsilon_3$，积分后移项到$S_s$得到$+\mathbb E_s\int\varepsilon_3q$。原文写成负号，参见[[#主定理的证明路线|Step4的修正恒等式]]。余项的绝对值估计及主结论不受此处符号影响。
>- **第5页含$k$的余项估计。** 应是$\varepsilon_2$而非$\varepsilon_3$，并使用$\mathbb E_s\int|\varepsilon_2|^2$与$\mathbb E_s\int|k|^2$的Cauchy–Schwarz估计；原文该处的下标和积分平方写法不宜直接照抄。
>- **第3页$\bar\sigma$定义。** 右端误写成$b(s,\bar X_s,\bar u_s)$，应为$\sigma(s,\bar X_s,\bar u_s)$。
>- **（H1）的时间变量。** 扩散Lipschitz不等式中的$\sigma(t,x,u)$应与另一项统一为同一时间$s$。
>- **例3.1的终端时刻。** 式(35)中下微分为空只对$s<T$成立；$s=T$时上下微分都为$\{-1\}$。

>[!warning] 假设陈述与证明使用时应区分的事项
>- **$H_u$的存在。** 本文印出的（H3）只写状态变量$(x,y,z)$的连续可微性，但Proposition 2.3使用$H_u$。调用该MP命题需补核对关于控制变量的可微性或所采用的适当变分版本；这不应被误写成主定理固定控制状态扰动步骤需要对$u$求导。
>- **例子与“一致连续”的字面要求。** $b(x,u)=xu$在$\mathbb R\times[0,1]$上不联合一致连续。例如$(x_n,u_n)=(n,0)$与$(x_n',u_n')=(n,1/n)$的距离趋于0，而$b$之差为1。因此例3.1不逐字满足（H1）关于所有变量全局一致连续的表述；它满足对$x$的一致Lipschitz和线性增长，例子的结论可由上面的显式计算独立核验。
>- **共同零测集与余项模量。** 原文以统一的$\delta$和有理点可数化完成路径结论。推广到新系数类时，要核对导数连续性的范围、条件估计的版本以及邻近扰动的统一性；单纯的逐点收敛或逐参数几乎处处成立不足以替代这些步骤。
>- **“每个$s$几乎处处”与“几乎处处对所有$s$”。** 本文证明先固定$s$。若研究中需要同时的路径结论、随机时刻或停时版本，不能只引用该固定时刻证明便跳过补充论证。

>[!note] 本文没有解决的范围
>- 主结论以最优控制存在为前提，不是最优控制存在性定理，也不是仅凭jet包含即可判断最优的充分性定理。
>- 不要求$V$可微，但保留了系数的一阶可微性和有界导数假设。
>- 得到的是空间一阶关系，未建立一般二阶空间jet及时间jet与伴随变量的完整对应。
>- 本文没有处理非凸控制域的一般最大值原理、一般全耦合FBSDE或随机系数下的随机价值场。
>- 结尾对非凸控制域及二阶展开困难的讨论，是2016年这个版本的研究边界，不能直接作为当前文献状态的判断。

# 研究查阅：与光滑结果的衔接及可复用方法

>[!note] 与2013年Shi–Yu工作的区别
>前置笔记：[[2013-Shi Jingtao&Yu Zhiyong-Relationship between Maximum Principle and Dynamic Programming for Stochastic Recursive Optimal Control Problems and Applications]]。
>
>光滑路线对$V_x(s,\bar X_s)$应用Itô公式，乘$q$构造候选伴随过程，再用伴随BSDE唯一性识别；因此需要足够高阶的$V$导数。
>
>本文路线对状态扰动$\widehat X,\widehat Y,\widehat Z$作一阶展开，用已给定的伴随过程作对偶，得到固定控制代价的线性敏感性，再通过最优性构造$V$的上支撑。它用“一侧支撑关系”替代了“对$V$求导”。

>[!note] 可以复用的证明模板
>1. 先明确代价符号、优化方向和终端条件，以确定最后得到上支撑还是下支撑。
>2. 固定最优控制、扰动状态；不要求最优反馈可微，也不对最优控制映射求导。
>3. 用条件稳定性估计获得$X,Y,Z$的扰动量级，区分$S^p$与$H^p$范数。
>4. 选择与线性化方程对偶的伴随系统，对$\langle\widehat X,p\rangle+\widehat Yq$使用Itô公式消去一阶项。
>5. 对只有时间$L^2$控制的$Z$使用$1+\alpha<2$的余项估计，避免无依据地要求更强正则性。
>6. 通过DPP取得接触点的等号，通过可容许性取得邻近点的单侧不等式。
>7. 处理条件概率、共同零测集及余项的一致性，最后转为路径上的jet包含；下微分包含由双向取扰动方向得到。

>[!question] 后续研究时值得检查的问题
>- **非凸控制域与控制依赖扩散：**需要何种spike variation、二阶伴随系统与二阶jet关系？本篇一阶证明不能直接替代这些工作。
>- **全耦合系统：**若前向系数依赖$Y,Z$，对偶消项及状态扰动适定性如何改变？
>- **非唯一最优控制：**所有最优控制产生的$p/q$与整个上微分集合之间，还能得到什么关系？本文只证明逐个最优控制的包含。
>- **随机时刻与路径结论：**在停时版本或同时对所有时间成立的版本中，哪些连续性、可测性和条件估计需要补足？

相关工具笔记：[[粘性解框架下的HJB方程]]、[[HJB方程与最大值原理]]、[[Linear SDE]]、[[1990-Pardoux&Peng Adapted solution of a backward stochastic differential equation]]。
