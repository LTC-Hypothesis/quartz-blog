在[[动态规划法与HJB方程#^be10f5|（HJB）方程]]中，我们要求值函数$V(t,x)\in C^1([0,T]\times\mathbb{R}^n)$。但一般来说，值函数的光滑性并没有这么好。
>[!example] 
>考虑系统
>$$
>\begin{cases}
>\dot{y}(s)=u(s)\\
>y(t)=x
>\end{cases}
>$$
>控制集为$U=[-1,1]$，泛函指标为
>$$
>J(u(\cdot);t,x)=\left|y(T;t,x,u(\cdot))\right|=\left|x+\int_{t}^{T}u(s){d}s\right|
>$$
>则值函数为
>$$
>V(t,x)=\inf_{u\in \mathscr{U}[t,T]}\left|x+\int_{t}^{T}u(s){d}s\right|=\begin{cases}
>(x-T+t)^+,x>0\\
>(x+T-t)^-,x\le0
>\end{cases}
>$$

尽管系统和泛函指标涉及到的函数都是光滑的，值函数也不一定光滑。
>[!example] 
>考虑系统
>$$
>\begin{cases}
>\dot{y}(s)=u(s)y(s)\\
>y(t)=x
>\end{cases}
>$$
>控制集为$U=[-1,1]$，指标泛函为
>$$
>J(u(\cdot);t,x)=y(T;t,x)
>$$
>则值函数为
>$$
>V(t,x)=\inf_{u\in\mathscr{U}[t,T]}xe^{\int_{t}^{T}u(s){d}s}=\begin{cases}
>xe^{T-t},x\le 0\\
>xe^{t-T},x>0
>\end{cases}
>$$
>从而相应的HJB方程为
>$$
>\begin{cases}
>-v_t+|xv_x|=0\\
>v(T,x)=x
>\end{cases}\tag{1}
>$$

下面我们说明HJB方程(1)没有$C^1([0,T]\times\mathbb{R}^n)$的经典解。
**Proof**
若存在经典解$v(t,x)\in C^1([0,T]\times\mathbb{R}^n)$满足方程(1)，则对终端条件有$v_x(T,x)=1>0$，又根据$v$的连续性，对固定的$x$，存在$\delta_x>0$使得$v_x(t,x)>0$，$T-\delta_x<t\le T$，令函数$\varphi(x)=T-\delta_x$, 于是得到
$$
v_x(t,x)>0,\forall(t,x)\in\mathscr{N}\triangleq\left\{(t,x):\varphi(x)<t\le T\right\}
$$
实际上可以取
$$
\mathscr{N}^+\triangleq\mathscr{N}\cap\left\{(t,x):x\ge0,t\in[0,T]\right\}
$$
于是得到
$$
\begin{cases}
v_t=xv_x,(t,x)\in\mathscr{N}^+\\
v(T,x)=x
\end{cases}
$$
考虑变换
$$
\begin{cases}
s=t\\
z=xe^t
\end{cases},\Phi(s,z)\triangleq v(s,ze^{-s})
$$
对于$\Phi(s,z)$我们有
$$
\Phi_s=v_t-xv_x=0
$$
因此我们可以将其写为$\Phi(s,z)=\Phi(z)$，从而$v(t,x)=\Phi(xe^t)$，根据终端条件
$$
xe^{-T}=v(T,xe^{-T})=\Phi(x)\Longrightarrow v(t,x)=xe^{t-T},\forall(t,x)\in\mathscr{N}^+
$$
类似可以得到$v(t,x)=xe^{T-t},(t,x)\in\mathscr{N}\setminus\mathscr{N}^+$。因此$v(t,x)=V(t,x),(t,x)\in\mathscr{N}$，但是$V(t,x)$不是$C^1$函数因此和$v\in C^1$矛盾。
**QED**

>[!def] 粘性解
>函数$v(t,x)\in C([0,T]\times\mathbb{R}^n)$称为**粘性下解**，若满足
>$$
>v(T,x)\le h(x),\forall x\in\mathbb{R}^n\tag{2}
>$$
>且对任意的$\varphi(t,x)\in C^1([0,T]\times\mathbb{R}^n)$，只要$v-\varphi$在某点$(t,x)\in[0,T)\times\mathbb{R}^n$达到极大值，就可以成立
>$$
>-\varphi_t(t,x)+\sup_{u\in U}H(t,x,u,-\varphi_x(t,x))\le 0\tag{3}
>$$
>函数$v(t,x)\in C([0,T]\times\mathbb{R}^n)$称为**粘性上解**，若满足
>$$
>v(T,x)\ge h(x),\forall x\in\mathbb{R}^n\tag{4}
>$$
>且对任意的$\varphi(t,x)\in C^1([0,T]\times\mathbb{R}^n)$，只要$v-\varphi$在某点$(t,x)\in[0,T)\times\mathbb{R}^n$达到极小值，就可以成立
>$$
>-\varphi_t(t,x)+\sup_{u\in U}H(t,x,u,-\varphi_x(t,x))\ge 0\tag{5}
>$$
>若$v$既是粘性下解又是粘性上解，则称$v$为粘性解。

