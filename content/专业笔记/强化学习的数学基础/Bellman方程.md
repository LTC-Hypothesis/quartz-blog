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
>&=\sum_{s'\in\mathcal{S}}\mathbb{E}[G_{t+1}|S_{t+1}=s']p(s'|s)\\
>&=、sum
>\end{aligned}
>$$