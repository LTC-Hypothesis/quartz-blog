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
>其中$v_\pi(s),v_\pi(s')$是未知量需要求解，$\Pi(s)$为状态$s$可选择的所有策略构成的集合。

此时我们要研究的问题转化为
- 存在性：Bellman最优方程是否有解？
- 唯一性：Bellman最优方程的解是否唯一？
- 算法：如何求解Bellman最优方程？
- 最优性：Bellman最优方程的解和最优策略之间有什么关系？

>[!note] Bellman最优方程的求解
>注意到$\sum_{a\in\mathcal{A}}\pi(a|s)=1$，实际上我们有
>$$
>\sum_{a\in\mathcal{A}}\pi(a|s)q_\pi(s,a)\le \sum_{a\in\mathcal{A}}\pi(a|s)\max_{\pi(s)\in\Pi(s)}q_\pi(s,a)=\max_{\pi(s)\in\Pi(s)}q_\pi(s,a)
>$$
>因此最大值的取等条件为
>$$
>\pi(a|s)=\begin{cases}
>1,&a=a^*\\
>0,&a\ne a^*
>\end{cases}
>$$
>其中$a^*=\arg\max_{a\in\mathcal{A}}q_\pi(s,a)$。因此对于状态$s$的最优策略$\pi^*$应该是选择具有最大$q(s,a)$的动作。此时，最优状态值为$v_{\pi^*}(s)=\max_{a\in\mathcal{A}}q(s,a)$。

>[!note] 矩阵向量形式
>和Bellman方程一样，我们有
>$$
>v=\max_{\pi\in\Pi}(r_\pi+\gamma P_\pi v)
>$$
>实际上方程右侧可看作$v$的函数$f(v)=\max_{\pi\in\Pi}(r_\pi+\gamma P_\pi v)$。

>[!thm] $f(v)$的压缩性
>我们说明函数$f(v)$在范数$\|\cdot\|_{\infty}$下是一个压缩映射即$\|f(v_1)-f(v_2)\|_\infty\le \gamma\|v_1-v_2\|_\infty$，对任意的$v_1,v_2\in\mathbb{R}^{|\mathcal{S}|}$，范数$\|\cdot\|_\infty$指的是向量中所有元素中的最大绝对值。

**Proof**

**QED**