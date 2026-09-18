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
> >[!def] 访问
> >通过执行策略$\pi$可以得到一列样本，
> >$$
> >s_1\xrightarrow{a_2}s_2\xrightarrow{a_4}s_1\xrightarrow{a_2}s_2
> >$$
> >如果一个状态动作对在一个回合中出现一次，我们称状态-动作被访问一次。
> 
> 前面MC Basic估计动作值时，只是用一个回合中对状态-动作对的一次访问，这种方式很简单但是没有充分利用样本，一个回合中还会访问其他的状态-动作对，
> $$
>\begin{aligned}
>& s_1 \xrightarrow{a_2} s_2 \xrightarrow{a_4} s_1 \xrightarrow{a_2} s_2 \xrightarrow{a_3} s_5 \xrightarrow{a_1} \dots \quad [\text{原始回合}] \\
>& s_2 \xrightarrow{a_4} s_1 \xrightarrow{a_2} s_2 \xrightarrow{a_3} s_5 \xrightarrow{a_1} \dots \quad [\text{从 } (s_2, a_4) \text{ 开始的子回合}] \\
>& s_1 \xrightarrow{a_2} s_2 \xrightarrow{a_3} s_5 \xrightarrow{a_1} \dots \quad [\text{从 } (s_1, a_2) \text{ 开始的子回合}] \\
>& s_2 \xrightarrow{a_3} s_5 \xrightarrow{a_1} \dots \quad [\text{从 } (s_2, a_3) \text{ 开始的子回合}] \\
>& s_5 \xrightarrow{a_1} \dots \quad [\text{从 } (s_5, a_1) \text{ 开始的子回合}]
>\end{aligned}
>$$
>MC Exploring Start 算法是充分利用回合中的每次访问，提高效率的技巧就是：在计算每个状态-动作开始获得的回报，采用回溯的方法，慢慢推回最初的状态-动作。这个算法需要一个条件Exploring-Start条件：对每个状态-动作，都要有足够多的回合从它出发。
>![[Pasted image 20260918175136.png]]
>但是这一个条件是不太好满足的，我们并不能保证每一个状态又能有足够的回合来采样。

在此我们引入一个软策略的方法，即一个策略能在任何状态下有非零概率选择任意动作。
>[!def] $\varepsilon$-Greedy策略
>这是一种常见的软策略，对于$\varepsilon\in[0,1]$，$\varepsilon$-Greedy策略有以下形式，
>$$
>\pi(a|s)=\begin{cases}
>1-\frac{\varepsilon}{|\mathcal{A}(s)|}(|\mathcal{A}(s)-1|),&\text{最大值动作}\\
>\frac{\varepsilon}{|\mathcal{A}(s)|},&\text{其他动作}
>\end{cases}
>$$
>注意到
>$$
>1-\frac{\varepsilon}{|\mathcal{A}(s)|}(|\mathcal{A}(s)-1|)=1-\varepsilon+\frac{\varepsilon}{|\mathcal{A}(s)|}\ge\frac{\varepsilon}{|\mathcal{A}(s)|}
>$$
>即选择最大动作值的概率会比选择其他动作的概率要高。当$\varepsilon=0$时，就是普通的贪婪策略，探索性最低；当$\varepsilon=1$时，选择每个动作的概率都是$\frac{1}{|\mathcal{A}(s)|}$，此时探索性最强。

>[!note] MC $\varepsilon$-Greedy 算法
>此时我们需要把策略改进步骤改为
>$$
>\pi_{k+1}=\arg\max_{\pi_k\Pi_\varepsilon}\sum_{a}\pi(a|s)q_{\pi_k}(s,a)
>$$
>$\Pi_\varepsilon$表示所有的$\varepsilon$-Greedy策略，不难得到
>$$
>\pi_{k+1}=\begin{cases}
>1-\frac{\varepsilon}{|\mathcal{A}(s)|}(|\mathcal{A}(s)-1|),&a=a^*_k\\
>\frac{\varepsilon}{|\mathcal{A}(s)|},&a\ne a^*_k
>\end{cases}
>$$
>其中$a^*_k=\arg\max_a q_{\pi_k}(s,a)$。
>![[Pasted image 20260918180821.png]]

>

