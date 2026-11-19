# 基础的TD算法
>[!def] 算法描述
>给定策略 $\pi$ , 我们想要估计所有的状态值 $v_\pi(s)$。由策略 $\pi$ 生成的经验样本 $(s_0,r_1,s_1,\cdots,s_t,r_{t+1},s_{t+1},\cdots)$, TD算法为
>$$
>\begin{cases}
>v_{t+1}(s_t)=v_t(s_t)-\alpha_t(s_t)(v_t(s_t)-(r_{t+1}+\gamma v_t(s_{t+1})))\\
>v_{t+1}(s)=v_t(s),s\ne s_t
>\end{cases}\tag{TD1}
>$$
>其中$v_t(s_t)$为$t$时刻对状态值$v_{\pi}(s_t)$的估计，$\alpha_t(s_t)$为$t$时刻$s_t$的学习率。

TD算法的设计本质上是，对Bellman方程使用随机近似算法求解，通过[[随机近似算法#^e800d6|RM算法]]求解。

>[!note] 算法推导
>先回顾状态值的定义， 
>$$
>v_\pi(s)=\mathbb{E}\left[R_{t+1}+\gamma v_\pi(S_{t+1})|S_t=s\right]
>$$
>定义函数
>$$
>g(v_\pi(s_t))=v_{\pi}(s_t)-\mathbb{E}\left[R_{t+1}+\gamma v_\pi(S_{t+1})|S_t=s_t\right]
>$$
>则Bellman方程转换为$g(v_\pi(s_t))=0$。用$r_{t+1},s_{t+1}$表示为$R_{t+1},S_{t+1}$的采样，那么具有噪声的观测函数为
>$$
>\begin{aligned}
>\tilde{g}(v_{\pi}(s_t))=&v_\pi(s_t)-[r_{t+1}+\gamma v_\pi(s_{t+1})]\\
>=&\textcolor{red}{v_\pi(s_t)-\mathbb{E}\left[R_{t+1}+\gamma v_\pi(S_{t+1})|S_t=s_t\right]}\\
>&+\textcolor{blue}{\mathbb{E}\left[R_{t+1}+\gamma v_\pi(S_{t+1})|S_t=s_t\right]-[r_{t+1}+\gamma v_\pi(s_{t+1})]}\\
>:=&g(v_\pi(s_t))+\eta
>\end{aligned}
>$$
>那么计算$g(v_\pi(s_t))=0$的RM算法为
>$$
>\begin{aligned}
>v_{t+1}(s_{t})=&v_{t}(s_t)-\alpha_t(s_t)\tilde{g}(v_t(s_t))\\
>=&v_t(s_t)-\alpha_t(s_t)(v_t(s_{t})-(r_{t+1}+\gamma v_t(s_{t+1})))
>\end{aligned}
>$$

>[!warning] 性质分析
>关于算法（TD），
>$$
>\textcolor{red}{v_{t+1}(s_{t})}=\textcolor{blue}{v_t(s_t)}-\alpha_t(s_t)(\textcolor{green}{v_t(s_{t})-(r_{t+1}+\gamma v_t(s_{t+1})}))
>$$
>$\textcolor{red}{更新状态值}$，$\textcolor{blue}{当前状态值}$，$\textcolor{green}{TD误差}$。我们记
>$$
>\bar{v}_t\triangleq r_{t+1}+\gamma v_t(s_{t+1})
>$$
>称为TD目标。TD误差记作$\delta_t\triangleq v_t(s_t)-\bar{v}_t$。

>[!warning] TD目标的解读
>TD算法设计的目的，是让$v(s_t)$每次都更接近$\bar{v}_t$，从数学上可以这样看，
>$$
>\begin{aligned}
>v_{t+1}(s_t)-\bar{v}_t&=v_t(s_t)-\bar{v}_t-\alpha_t(s_t)(v_t(s_t)-\bar{v}_t)\\
>&=(1-\alpha_t(s_t))(v_{t}(s_t)-\bar{v}_t)
>\end{aligned}
>$$
>取绝对值之后，由于$0<\alpha_t(s_t)<1$，
>$$
>|v_{t+1}(s_t)-\bar{v}_t|\le|v_{t}(s_t)-\bar{v}_t|
>$$

>[!warning] TD误差的解读
>TD误差反映的是两个时刻，即$t$和$t+1$时刻两个状态值的差异，更重要的是反映了状态估计值$v_t(s_t)$和真实状态值$v_\pi(s_t)$之间的差异，如果估计值准确，在期望意义下应该为0，当$v_t=v_\pi$，则
>$$
>\begin{aligned}
>\mathbb{E}[\delta_t|S_t=s_t]=&\mathbb{E}\left[v_\pi(S_t)-(R_{t+1}+\gamma v_\pi(S_{t+1}))|S_t=s_t\right]\\
>=&v_\pi(s_t)-\mathbb{E}\left[(R_{t+1}+\gamma v_\pi(S_{t+1}))|S_t=s_t\right]=0
>\end{aligned}
>$$

>[!thm] (TD1)算法的收敛性
>对给定策略$\pi$，算法（TD1），若对所有状态$s\in\mathcal{S}$都满足$\sum_{t}\alpha_t(s)=\infty,\sum_t\alpha^2_t(s)<\infty$，则$v_t(s)\xrightarrow{a.s.} v_\pi(s)\text{ as }t\to\infty$。

>[!warning] 
>- 需要注意在$t$时刻，如果访问到状态$s$，则$\alpha_t(s)>0$，否则$\alpha_t(s)=0$，对于条件$\sum_t\alpha_t(s)=\infty$，理论上要求要访问状态$s$无穷次，但实际上只用访问足够多次即可，这个条件要求要有足够多的经验数据。
>- $\alpha_t$一般会选取一个较小的正数，这时条件$\sum_t\alpha_t^2(s)<\infty$反而不成立，这样选择是为了更好地利用后面的数据，如果$\alpha_t$逐渐收敛到0，则当$t$较大时得到的数据对估计的影响比较小。

**Proof**

我们证明的想法是使用[[随机近似算法#^ff3bb1|推广的Dvoretzky定理]]。

定义$\Delta_t(s)\triangleq v_t(s)-v_\pi(s)$，则当访问到$s_t$时
$$
\begin{aligned}
\Delta_{t+1}(s)&=v_{t+1}(s)-v_\pi(s)\\
&=v_t(s)-v_\pi(s)-\alpha_t(s)(v_t(s)-(r_{t+1}+\gamma v_{t}(s_{t+1})))\\
&=(1-\alpha_t(s))\Delta_t(s)+\alpha_t(s)(r_{t+1}+\gamma v_{t}(s_{t+1})-v_\pi(s))\\
&:=(1-\alpha_t(s))\Delta_t(s)+\alpha_t(s)\eta_t(s)
\end{aligned}
$$
未访问到状态$s_t$时，
$$
\Delta_{t+1}(s)=\Delta_t(s)=(1-\alpha_t(s))\Delta_t(s)+\alpha_t(s)\eta_t(s)
$$
其中$\alpha_t(s)=\eta_t(s)=0$。因此无论是否访问到状态$s_t$，我们都可以将过程表示为该种形式，只需要验证条件即可。

第一个条件和TD算法的假设相同。对第二个条件，注意到根据马氏性，$\eta_t(s)$不包含历史信息，即
$$
\mathbb{E}[\eta_t(s)|\mathcal{H}_t]=\mathbb{E}[\eta_t(s)]
$$
当未访问到状态$s_t$时，$\eta_t(s)=0$，$\mathbb{E}[\eta_t(s)]=0\le\gamma\|\Delta_t\|_\infty$。当访问到状态$s_t$时，
$$
\begin{aligned}
\mathbb{E}[\eta_t(s)]&=\mathbb{E}[\eta_t(s_t)]\\
&=\mathbb{E}[r_{t+1}+\gamma v_t(s_{t+1})-v_\pi(s_t)|s_t]\\
&=\mathbb{E}[r_{t+1}+\gamma v_t(s_{t+1})|s_t]-v_\pi(s_t)
\end{aligned}
$$
由$v_\pi(s_t)=\mathbb{E}[r_{t+1}+\gamma v_\pi(s_{t+1})|s_t]$，代入上式得到
$$
\begin{aligned}
\mathbb{E}[\eta_t(s)]&=\gamma\mathbb{E}[v_t(s_{t+1})-v_\pi(s_{t+1})|s_t]\\
&=\gamma\sum_{s'\in \mathcal{S}} p(s'|s_t)(v_t(s')-v_\pi(s'))
\end{aligned}
$$
取绝对值之后，
$$
|\mathbb{E}[\eta_t(s)]|\le\gamma\max_{s'\in\mathcal{S}}|v_t(s')-v_\pi(s')|\sum_{s'\in\mathcal{S}}p(s'|s_t)=\gamma\|\Delta_t\|_\infty
$$
因此得到$\|\mathbb{E}[\eta_t(s)]\|_\infty\le\gamma\|\Delta_t\|_\infty$。

对于第三个条件，未访问到状态$s_t$时，$\text{Var}[\eta_t(s)|\mathcal{H}_t]=0$。当访问到状态$s_t$时，
$$
\begin{aligned}
\text{Var}[\eta_t(s)|\mathcal{H}_t]&=\text{Var}[r_{t+1}+\gamma v_t(s_{t+1})-v_\pi(s_t)|s_t]\\
&\le C(1+\|\Delta_t\|_\infty^2)
\end{aligned}
$$
综上所述，可以得到$\Delta_t\xrightarrow{a.s.}0$ i.e. $v_t(s)\xrightarrow{a.s.}v_\pi(s)$。

**QED**

# 基于动作值的TD算法：Sarsa算法
>[!note] Sarsa算法描述
>给定策略$\pi$，由策略$\pi$生成的一列经验样本：$(s_0,a_0,r_1,s_1,a_1,\cdots,s_t,a_t,r_t,s_{t+1},a_{t+1},\cdots)$那么可以用如下算法估计状态的动作值，
>$$
>q_{t+1}(s_t,a_t)=q_t(s_t,a_t)-\alpha_t(s_t,a_t)(q_t(s_t,a_t)-(r_{t+1}+\gamma q_t(s_{t+1},a_{t+1})))\quad(\text{TD}2)
>$$
>$$
>q_{t+1}(s_t,a_t)=q_t(s_t,a_t),(s,a)\ne (s_t,a_t)
>$$

>[!warning] 
>Sarsa算法本质是在是在做动作值的随机近似算法，
>$$
>q_\pi(s,a)=\mathbb{E}[R_{t+1}+\gamma q_\pi(S',A')|s,a]
>$$
>实际上，上式是一个基于动作值的Bellman方程。

>[!thm] Sarsa算法的收敛性
>给定策略$\pi$，对上述Sarsa算法，若对所有的$(s,a)$满足$\sum_t\alpha_t(s,a)=\infty,\sum_t\alpha_t^2(s,a)<\infty$，则动作值估计值$q_t(s,a)\xrightarrow{a.s.}q_\pi(s,a)$。

>[!note] 利用Sarsa算法学习最优策略
>![[Pasted image 20261117083418.png]]

# n-step Sarsa算法
>[!note] n-step Sarsa算法描述
>先回顾动作值的定义，
>$$
>q_\pi(s,a)=\mathbb{E}[G_t|S_t=s,A_t=a]
>$$
>折扣回报为$G_t=R_{t+1}+\gamma R_{t+2}+\gamma^2 R_{t+3}+\cdots$，如果只把$G_t$写到$n$项，
>$$
>G_t^{(n)}=R_{t+1}+\gamma R_{t+2}+\cdots+\gamma^n q_\pi(S_{t+n},A_{t+n})
>$$
>此时代入回动作值定义，我们有
>$$
>\begin{aligned}
>q_\pi(s,a)&=\mathbb{E}[G_t^{(n)}|S_t=s,A_t=a]\\
>&=\mathbb{E}[R_{t+1}+\gamma R_{t+2}+\cdots+\gamma^n q_\pi(S_{t+n},A_{t+n})|s,a]
>\end{aligned}
>$$
>计算这个期望值的随机近似算法为
>$$
>\begin{aligned}
>q_{t+1}(s_t,a_t)=&q_t(s_t,a_t)\\
>&-\alpha_t(s_t,a_t)(q_t(s_t,a_t)-(r_{t+1}+\gamma r_{t+2}+\cdots+\gamma^n q(s_{t+n},a_{t+n})))
>\end{aligned}
>$$
>这就是n-step Sarsa算法。

>[!warning] 特殊情况
>- 当$n=1$时，n-step Sarsa算法变成Sarsa算法。
>- 当$n=\infty$，n-step Sarsa算法变成[[蒙特卡洛方法（MCMC）|MCMC算法]]。

# Q-Learning算法
Q-Learning算法是强化学习最经典的算法之一，前面的Sarsa只能估计给定策略的动作值，但Q-Learning可以直接估计最优动作值进而找到最优策略。

>[!note] Q-Learning算法描述
>Q-Learning算法的数学描述如下
>$$
>\begin{cases}
>q_{t+1}(s_t,a_t)=q_t(s_t,a_t)-\alpha(s_t,a_t)\left[q_t(s_t,a_t)-(r_{t+1}+\gamma)\right]
>\end{cases}
>$$

# TD算法的统一框架

