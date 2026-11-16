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
>- 需要注意在$t$时刻，如果访问到状态$s$，则$\alpha_t(s)>0$，否则$\alpha_t(s)=0$，对于条件$\sum_t\alpha_t(s)=\infty$，理论上要求

**Proof**



**QED**