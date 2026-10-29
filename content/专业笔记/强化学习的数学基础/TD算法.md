# 基础的TD算法
>[!def] 算法描述
>给定策略 $\pi$ , 我们想要估计所有的状态值 $v_\pi(s)$。由策略 $\pi$ 生成的经验样本 $(s_0,r_1,s_1,\cdots,s_t,r_{t+1},s_{t+1},\cdots)$, TD算法为
>$$
>\begin{cases}
>v_{t+1}(s_t)=v_t(s_t)-\alpha_t(s_t)(v_t(s_t)-(r_{t+1}+\gamma v_t(s_{t+1})))\\
>v_{t+1}(s)=v_t(s),s\ne s_t
>\end{cases}
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
>