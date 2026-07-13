考虑系统
$$
\begin{cases}
\dot{y}(t)=f(t,y(t),u(t)),a.e. \ t\in[0,T]\\
y(0)=y_0
\end{cases}\tag{1}
$$
其中$f:[0,T]\times\mathbb{R}^n\times U\to\mathbb{R}^n$。控制集为
$$
\mathscr{U}[0,T]=\{u(\cdot):[0,T]\to U|u(\cdot)\text{ 可测}\}
$$
指标泛函为
$$
J(u(\cdot))=\int_{0}^{T}f^0(t,y(t),u(t)){d}t+h(y(T))\tag{2}
$$
>[!def] 问题(D)
>寻找控制$\bar{u}(\cdot)\in\mathscr{U}[0,T]$使得
>$$
>J(\bar{u}(\cdot))=\inf_{u(\cdot)\in\mathscr{U}[0,T]}J(u(\cdot))
>$$

>[!note] 动态规划法的思想
>寻找一系列的最优控制问题，具有不同的初始状态和初始时间，使得原问题(D)成为一个特例。考虑$(t,x)\in[0,T)\times\mathbb{R}^n$，引入控制系统
>$$
>\begin{cases}
\dot{y}(s)=f(s,y(s),u(s)), a.e. \ s\in[t,T]\\
y(t)=x
\end{cases}\tag{3}
>$$
>此时控制集为
>$$
>\mathscr{U}[t,T]=\{u(\cdot):[t,T]\to U|u(\cdot)\text{ 可测}\}
>$$
>指标泛函为
>$$
>J(u(\cdot);t,x)=\int_{t}^{T}f^0(s,y(s),u(s)){d}s+h(y(T))\tag{4}
>$$

>[!def] 问题(D$_{tx}$)
>寻找最优控制$\bar{u}(\cdot)\in\mathscr{U}[t,T]$使得
>$$
>J(\bar{u}(\cdot);t,x)=\inf_{u(\cdot)\in\mathscr{U}[t,T]}J(u(\cdot);t,x)
>$$

>[!warning] 
>注意到当$t=0,x=y_0$时，问题(D$_{tx}$)退化为问题(D)。

>[!def] 假设(D1)-(D2)
>- (D1) $U\subseteq\mathbb{R}^m$可分度量空间，$T>0$
>- (D2) $f:[0,T]\times\mathbb{R}^n\times U\to\mathbb{R}^n,f^0:[0,T]\times\mathbb{R}^n\times U\to\mathbb{R}$都是可测的，且存在常数$L>0$和连续模$\omega:[0,+\infty)\to[0,+\infty)$使得对$\varphi=f,f^0$成立
>  $$
>  \begin{cases}
|\varphi(t,y,u)-\varphi(t,\hat{y},u)|\le L|y-\hat{y}|\\
|\varphi(t,0,u)|\le L
\end{cases},\forall t\in[0,T],y,\hat{y}\in\mathbb{R}^n,u\in U
>  $$

^fb3166

>[!proposition]
>[[#^fb3166|假设(D1)-(D2)]]成立，则对任意的$(t,x)\in[0,T)\times\mathbb{R}^n$和$u(\cdot)\in\mathscr{U}[t,T]$，系统(3)有唯一解且性能指标有定义。进一步成立估计，存在$K>0$使得
>$$
>|y(s;t,x,u)|\le K(1+|x|),\forall s\in[t,T],u(\cdot)\in\mathscr{U}[t,T],(t,x)\in[0,T)\times\mathbb{R}^n
>$$
>以及
>$$
>|y(s;t,x,u)-y(s;\bar{t},\bar{x},u)|\le K\left(|x-\bar{x}|+(1+|x|\vee|\bar{x}|)|t-\bar{t}|\right)
>$$

^6ab1ca

**Proof**
由唯一解可以得到
$$
\begin{aligned}
|y(s;t,x,u)|&\le |x|+\int_{t}^{s}|f(r,y(r),u(r))|{d}r\\
&\le |x|+L(T-t)+L\int_{t}^{s}|y(r)|{d}r
\end{aligned}
$$
由[[Strong solutions#^5fc0f3|Gronwall不等式]]，可以得到
$$
|y(s;t,x,u)|\le (|x|+L(T-t))e^{L(T-t)}\le K(1+|x|)
$$
对于第二个不等式，我们记$\bar{y}(s)\triangleq y(s;\bar{t},\bar{x},u)$, 先不妨假设$t<\bar{t}$，
$$
\begin{aligned}
|y(s;t,x,u)-y(s;\bar{t},\bar{x},u)|&\le |x-\bar{x}|+\left|\int_{t}^{s}f(r,y(r),u(r)){d}r-\int_{\bar{t}}^{s}f(r,\bar{y}(r),u(r)){d}r\right|\\
&\le |x-\bar{x}|+\int_{t}^{\bar{t}}|f(r,y(r),u(r))|{d}r+L\int_{\bar{t}}^{s}|y(r)-\bar{y}(r)|{d}r\\
&\le |x-\bar{x}|+L(\bar{t}-t)+K_1L(\bar{t}-t)(1+|x|)+L\int_{\bar{t}}^{s}|y(r)-\bar{y}(r)|{d}r
\end{aligned}
$$
由Gronwall不等式
$$
\begin{aligned}
|y(s;t,x,u)-y(s;\bar{t},\bar{x},u)|&\le (L(\bar{t}-t)(K_1(1+|x|)+1)+|x-\bar{x}|)e^{L(T-\bar{t})}\\
&\le K((\bar{t}-t)(1+|x|)+|x-\bar{x}|)
\end{aligned}
$$
类似可以得到$t\ge\bar{t}$的情况，
$$
|y(s;t,x,u)-y(s;\bar{t},\bar{x},u)|\le K((t-\bar{t})(1+|\bar{x}|)+|x-\bar{x}|)
$$
综合两式即可得到
$$
|y(s;t,x,u)-y(s;\bar{t},\bar{x},u)|\le K\left(|x-\bar{x}|+(1+|x|\vee|\bar{x}|)|t-\bar{t}|\right)
$$
**QED**

>[!def] 值函数
>根据上述命题已知指标泛函$J(u(\cdot);t,x)$有定义，我们可以定义以下函数
>$$
>\begin{cases}
>V(t,x)=\inf_{u(\cdot)\in\mathscr{U}[t,T]}J(u(\cdot);t,x),&\forall (t,x)\in[0,T)\times\mathbb{R}^n\\
>V(T,x)=h(x),&\forall x\in\mathbb{R}^n
>\end{cases}\tag{5}
>$$
>称$V(\cdot,\cdot)$为问题(D)的值函数。

>[!proposition] 值函数的性质
>[[#^fb3166|假设(D1)-(D2)]]成立，则存在常数$K>0$满足
>$$
>|V(t,x)|\le K(1+|x|),\forall(t,x)\in[0,T)\times\mathbb{R}^n\tag{6}
>$$
>$$
>|V(t,x)-V(\bar{t},\bar{x})|\le K\left(|x-\bar{x}|+(1+|x|\vee|\bar{x}|)|t-\bar{t}|\right)\tag{7}
>$$

**Proof**
由[[#^6ab1ca|命题]]得到，
$$
\begin{aligned}
|J(u(\cdot);t,x)|&\le L\int_{0}^{T}|y(t)|{d}t+LT+L|y(T)|+L\\
&\le LTK(1+|x|)+LK(1+|x|)+L(T+1)\\
&\le L(T+1)(K(1+|x|)+1)\le K(1+|x|)
\end{aligned}
$$
同理可得
$$
|J(u(\cdot);t,x)-J(u(\cdot);t,\bar{x})|\le K|x-\bar{x}|
$$
$$
|J(u(\cdot);t,x)-J(u(\cdot);\bar{t},x)|\le K(1+|x|\vee|\bar{x}|)|t-\bar{t}|
$$
对以上不等式在左边取下确界即可得到(6)(7)。
**QED**

>[!thm] Bellman最优性原理
>[[#^fb3166|假设(D1)-(D2)]]成立, 则对任意的$(t,x)\in [0,T)\times\mathbb{R}^n$成立
>$$
>V(t,x)=\inf_{u(\cdot)\in\mathscr{U}[t,\hat{t}]}\left\{\int_{t}^{\hat{t}}f^0(s,y(s;t,x,u(\cdot)),u(s)){d}s+V(\hat{t},y(\hat{t};t,x,u(\cdot)))\right\}\tag{8}
>$$

>[!note] 动态规划思想
>其实是某种“无后效性”。最优控制的传统观点是要在整个时间段$[0,T]$上寻找控制$\bar{u}(\cdot)$，但动态规划是考虑如果走到某个时刻$\hat{t}\in[0,T]$，该如何选取$\hat{t}$之后的控制，使得未来的

**Proof**

**QED**

>[!proposition] Hamilton-Jacobi-Bellman (HJB) 方程
>[[#^fb3166|假设(D1)-(D2)]]成立, 且值函数$V\in C^1([0,T]\times\mathbb{R}^n)$，则值函数满足一阶PDE终值问题
>$$
>\begin{cases}
>-V_t+\sup_{u\in U}H(t,x,u,-V_x)=0,&(t,x)\in[0,T)\times\mathbb{R}^n\\
>V(T,x)=h(x),&x\in\mathbb{R}^n
>\end{cases}\tag{HJB}
>$$
>其中$H$为Hamilton函数
>$$
>H(t,x,u,p)=\left\langle p,f(t,x,u)\right\rangle-f^0(t,x,u)
>$$

