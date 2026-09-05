重点：一个基本概念：状态值；一个基本工具：Bellman方程。
>[!def] 状态值
>对于时刻$t=0,1,\cdots$，智能体处于状态$S_t$，按照策略$\pi$会采取动作$A_t$转移到状态$S_{t+1}$并获得即使奖励$R_{t+1}$，这个过程简记为
>$$
>S_t\xrightarrow{A_t}S_{t+1},R_{t+1}
>$$
>其中$S_{t},S_{t+1},A_{t},R_{t+1}$都是随机变量。因此，按照策略$\pi$我们会得到一列“状态-动作-奖励”轨迹，
>$$
>S_t\xrightarrow{A_t}S_{t+1},R_{t+1}\xrightarrow{A_{t+1}}S_{t+2},R_{t+2}\xrightarrow{A_{t+1}}\cdots
>$$
>沿该轨迹得到总折扣回报
>$$
>G_t=R_{t+1}+\gamma R_{t+2}+\gamma^2R_{t+3}+\cdots
>$$
>状态值定义为$G_t$的期望值，
>$$
>v_\pi(s)\triangleq\mathbb{E}[G_t|S_t=s]
>$$

>[!warning] 
>- 由于状态值是由一个条件概率定义的，因此$v_\pi(s)$依赖于条件$S_t=s$。
>- $v_\pi(s)$和策略$\pi$有关
>- 但是$v_\pi(s)$不依赖于$t$。

>[!note] Bellman方程及推导
>Bellman方程是研究状态值的核心工具，它描述了所有状态值之间的关系。我们下面来进行推导，注意到$G_t$可以写成
>$$
>\begin{aligned}
>G_t&=R_{t+1}+\gamma R_{t+2}+\gamma^2R_{t+3}+\cdots\\
>&=R_{t+1}+\gamma(R_{t+2}+\gamma R_{t+3}+\cdots)=R_{t+1}+\gamma G_{t+1}
>\end{aligned}
>$$
>那么两边取期望就得到状态值，
>$$
>v_{\pi}(s)=\mathbb{E}[R_{t+1}|S_{t}=s]+\gamma\mathbb{E}[G_{t+1}|S_t=s]
>$$
>我们需要分析这两项，对于第一项，根据条件期望的定义，这表示在状态$s$下，我采取动作转移到下一个状态所获得的即时奖励，那么根据全期望公式可以得到
>$$
>\begin{aligned}
>\mathbb{E}[R_{t+1}|S_t=s]&=\sum_{a\in\mathcal{A}}\pi(a|s)\mathbb{E}[R_{t+1}|S_t=s,A_{t}=a]\\
>&=\sum_{a\in\mathcal{A}}\pi(a|s)\sum_{r\in\mathcal{R}}p(r|s,a)\cdot r
>\end{aligned}
>$$
>对于第二项，表示的是未来奖励的期望值，可以计算
>$$
>\begin{aligned}
>\mathbb{E}[G_{t+1}|S_t=s]&=\sum_{s'\in\mathcal{S}}\mathbb{E}[G_{t+1}|S_t=s,S_{t+1}=s']p(s'|s)\\
>&=\sum_{s'\in\mathcal{S}}\mathbb{E}[G_{t+1}|S_{t+1}=s']p(s'|s)\qquad\text{(马氏性)}\\
>&=\sum_{s'\in\mathcal{S}}v_\pi(s')p(s'|s)\\
>&=\sum_{s'\in\mathcal{S}}v_\pi(s')\sum_{a\in\mathcal{A}}p(s'|s,a)\pi(a|s)
>\end{aligned}
>$$
>合并两项可以得到
>$$
>\begin{aligned}
>v_\pi(s)&=\sum_{a\in\mathcal{A}}\pi(a|s)\sum_{r\in\mathcal{R}}p(r|s,a)\cdot r+\gamma\sum_{s'\in\mathcal{S}}v_\pi(s')\sum_{a\in\mathcal{A}}p(s'|s,a)\pi(a|s)\\
>&=\sum_{a\in\mathcal{A}}\pi(a|s)\left[\sum_{r\in\mathcal{R}}p(r|s,a)r+\gamma\sum_{s'\in\mathcal{S}}p(s'|s,a)v_\pi(s')\right]
>\end{aligned}\tag{1}
>$$

>[!warning] 对Bellman公式的说明
>- $v_\pi(s)$和$v_\pi(s')$是未知量需要求解，实际上对于每个状态$s\in\mathcal{S}$都成立Bellman公式，那么联立所有式子就可以求解（后面矩阵向量形式会更简洁直观）。
>- $\pi(a|s)$是给定策略，是已知的，Bellman方程一定对应一个给定的策略。
>- $p(r|s,a),p(s'|s,a)$代表系统模型，我们一般先研究有模型的情况即这些量是已知的，在推广到无模型的情况。

>[!note] Bellman方程的等价形式
>1. $$v_\pi(s)=\sum_{a\in\mathcal{A}}\pi(a|s)\sum_{s'\in\mathcal{S}}\sum_{r\in\mathcal{R}}p(s',r|s,a)[r+\gamma v_\pi(s')]$$
>2. $$v_\pi(s)=\mathbb{E}[R_{t+1}+\gamma v_\pi(S_{t+1})|S_{t}=s],s\in\mathcal{S}$$
>3. $$v_\pi(s)=\sum_{a\in\mathcal{A}}\pi(a|s)\sum_{s'\in\mathcal{S}}p(s'|s,a)[r(s')+\gamma v_\pi(s')]$$

在(1)式中我们记
$$
r_\pi(s)=\sum_{a\in\mathcal{A}}\pi(a|s)\sum_{r\in\mathcal{R}}p(r|s,a)r
$$
$$
p_\pi(s'|s)=\sum_{a\in\mathcal{A}}\pi(a|s)p(s'|s,a)
$$
从而状态值可以写成
>[!note] 矩阵向量形式
>可以得到
>$$
>v_\pi(s)=r_\pi(s)+\gamma\sum_{s'\in\mathcal{S}}p_\pi(s'|s)v_\pi(s')
>$$
>对所有状态重新编号，假设$|\mathcal{S}|=n$，定义$v_\pi=(v_\pi(s_1),\cdots,v_\pi(s_n))^\top$，$r_\pi=(r_\pi(s_1),\cdots,r_\pi(s_n))$和状态转移矩阵$P_\pi=(p_\pi(s_j|s_i))_{n\times n}\in\mathbb{R}^{n\times n}$。最终得到矩阵向量形式
>$$
>v_\pi=r_\pi+\gamma P_\pi v_\pi
>$$

>[!note] 求解状态值（解析解）
>实际上我们可以直接得到
>$$
>v_\pi=(I-\gamma P_\pi)^{-1}r_\pi
>$$
>唯一需要注意的地方是矩阵$I-\gamma P_\pi$是否可逆，答案是肯定的。关于矩阵$I-\gamma P_\pi$还有以下性质
>- $(I-\gamma P_\pi)^{-1}\ge I$。实际上，根据矩阵的级数展开，
> $$
> (I-\gamma P_\pi)^{-1}=I+\gamma P_\pi+\gamma^2 P_\pi^2+\cdots\ge I
> $$
>- 单调性，即若对向量$r_1\ge r_2$，那么$(I-\gamma P_\pi)^{-1}r_1\ge (I-\gamma P_\pi)^{-1}r_2$。

>[!note] 求解状态值（数值法）
>从该方法开始，其实是强化学习算法的一个启蒙。解析解非常直观，但求解矩阵的逆需要复杂的数值算法来实现，因此一般只用于理论分析。我们可以通过数值迭代公式来求解，
>$$
>v_{k+1}=r_\pi+\gamma P_\pi v_k,k=0,1,2,\cdots
>$$
>我们会得到一列状态值$\{v_0,v_1,\cdots,v_n,\cdots\}$，可以证明$v_n\to v_{\pi}=(I-\gamma P_{\pi})^{-1}r_\pi,n\to\infty$

**Proof**
我们注意到$v_\pi=r_\pi+\gamma P_\pi v_\pi$，则
$$
\begin{aligned}
v_{k+1}-v_\pi=r_\pi+\gamma P_\pi v_k-v_\pi=\gamma P_\pi(v_k-v_\pi)
\end{aligned}
$$
我们记$\delta_{k}\triangleq v_k-v_\pi$，那么可以得到
$$
\delta_{k+1}=\gamma P_\pi\delta_k=\gamma^2P_\pi^2\delta_{k-1}=\cdots=\gamma^{k+1}P_\pi^{k+1}\delta_0
$$
由于$\gamma\in(0,1)$则$\gamma^{k+1}\to\infty\text{ as }k\to\infty$。$0\le P_\pi\le 1$表示矩阵$P_\pi$每个元素都小于等于1，从而
$$
\delta_{k+1}=\gamma^{k+1}P_\pi^{k+1}\delta_0\to0\text{ as }k\to\infty\text{ .i.e. }v_k\to v_\pi
$$
**QED**
>[!def] 动作值
>对于一个状态-动作对$(s,a)$，其动作值定义为
>$$
>q_\pi(s,a)=\mathbb{E}[G_t|S_t=s,A_t=a]
>$$
>含义为智能体在一个状态$s$采取动作$a$之后获得的回报的期望值。

>[!warning] 动作值和状态值的关系
>注意到
>$$
>\begin{aligned}
>v_\pi(s)&=\mathbb{E}[G_t|S_t=s]=\sum_{a\in\mathcal{A}}\mathbb{E}[G_t|S_t=s,A_t=a]\pi(a|s)\\
>&=\sum_{a\in\mathcal{A}}q_\pi(s,a)\pi(a|s)=\mathbb{E}_{A_t\sim\pi(s)}[q(s,A_t)]
>\end{aligned}
>$$
>另外从Bellman公式(1)来看，和上式比较可以得到
>$$
>\begin{aligned}
>q_\pi(s,a)&=\sum_{r\in\mathcal{R}}p(r|s,a)r+\gamma\sum_{s'\in\mathcal{S}}p(s'|s,a)v_\pi(s')\\
>&=\mathbb{E}[R_{t+1}+\gamma v_\pi(S_{t+1})|S_{t}=s,A_{t}=a]
>\end{aligned}
>$$

>[!warning] 易错点
>一个动作不会被策略选择，但是仍然会具有动作值。一些动作没有被选择到，不是因为这些动作不够好，相反这些很可能是好的动作，强化学习本质是在学习最优的策略，因此必须探索所有的动作才能找到每个状态下的最优动作。

>[!note] 基于动作值的Bellman方程
>