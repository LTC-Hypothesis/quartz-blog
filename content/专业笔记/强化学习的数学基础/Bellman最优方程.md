**强化学习的终极目标是寻找最优策略。**
>[!def] 最优策略和最优状态值
>对于一个策略$\pi^*$，若对于任何状态$s\in\mathcal{S}$和任意策略$\pi$都有$v_{\pi^*}(s)\ge v_\pi(s)$，则称$\pi^*$为最优策略，对应的状态值称为最优状态值。

在此基础上我们需要研究最优策略和最优状态值的存在新、唯一性、随机性和算法。

>[!note] Bellman最优方程
>对每个$s\in\mathcal{S}$，成立
>$$
>\begin{aligned}
>v(s)&=\max_{\pi(s)\in\Pi(s)}\sum_{a\in\mathcal{A}}\pi(a|s)\left[\sum_{r\in\mathcal{R}}p(r|s,a)r+\gamma\sum_{s'\in\mathcal{S}}p(s'|s,a)v_\pi(s')\right]\\
>&=\max_{\pi(s)\in\Pi(s)}\sum_{a\in\mathcal{A}}\pi(a|s)q_\pi(s,a)
>\end{aligned}
>$$
>其中$v_\pi(s),v_\pi(s')$是未知量需要求解。

此时我们要研究的问题转化为
- 存在性：Bellman最优方程是否有解？
- 唯一性：Bellman最优方程的解是否唯一？
- 算法：如何求解Bellman最优方程？
- 最优性：Bellman最优方程的解和最优策略之间有什么关系？

>[!note] B