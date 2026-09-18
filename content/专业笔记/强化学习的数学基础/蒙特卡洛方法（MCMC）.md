前面都是基于模型来讲的算法，从这一章开始是基于无模型的算法，当没有模型的时候我们就需要数据（采样）。
>[!example] 启发例子：求期望（大数定律）
>对于基于模型的情况，我们已知概率分布，可以直接求随机变量$X$的期望，
>$$
>\mathbb{E}[X]=\sum_{x\in\mathcal{X}}p(x)x
>$$
>对于无模型的情况，我们不知道概率分布，那么就需要数据$x_1,\cdots,x_n$，那么
>$$
>\bar{x}\triangleq\frac{1}{n}\sum_{i=1}^{n}x_i\approx\mathbb{E}[X]
>$$
>当数据足够多的时候，有
>$$
>\bar{x}\xrightarrow{\mathbb{P}}\mathbb{E}[X]\tag{WLLN}
>$$
>但必须要求估计期望的样本是独立同分布的。

>[!note] MC Basic
>MC方法是以[[值迭代和策略迭代#^617964|策略迭代算法]]为基础的，策略迭代分为两个步骤，策略评估和策略更新，策略更新展开为
>$$
>\pi_{k+1}=\arg\max_{\pi}\sum_{a}\pi(a|s)q_{\pi_k}(s,a)
>$$
>可以看出动作值是核心，第一步是计算动作值，第二步是寻找最大的动作值。
>- 基于模型的情况，动作值的计算为
>  $$
>  q_{\pi_k}(s,a)=\sum_{r}p(r|s,a)r+\gamma\sum_{s'}p(s'|s,a)v_{\pi_k}(s')
>  $$
>- 无模型的情况，我们需要数据，那么是怎样的数据呢？先回顾动作值的定义，
>  $$
> \begin{aligned}
> q_{\pi_k}(s,a)&=\mathbb{E}[G_t|S_t=s,A_t=a]\\
> &=\mathbb{E}[R_{t+1}+\gamma R_{t+2}+\cdots|S_t=s,A_t=a]
>\end{aligned}
> $$
>也就是智能体从$(s,a)$开始执行策略$\pi_k$，获得$n$个回合，设第$i$个回合得到的回报为$g^{(i)}_{\pi_k}(s,a)$，那么根据前面的启发性例子，
>$$
>q_{\pi_k}(s,a)\approx\frac{1}{n}\sum_{i=1}^{n}g^{(i)}_{\pi_k}(s,a)
>$$
>![[Pasted image 20260918162442.png]]

>[!note] MC Exploring Start 算法
> 