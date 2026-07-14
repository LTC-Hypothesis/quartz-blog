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
>[[#^fb3166|假设(D1)-(D2)]]成立, 则对任意的$(t,x)\in [0,T)\times\mathbb{R}^n$和$0\le t\le \hat{t}\le T$成立
>$$
>V(t,x)=\inf_{u(\cdot)\in\mathscr{U}[t,\hat{t}]}\left\{\int_{t}^{\hat{t}}f^0(s,y(s;t,x,u(\cdot)),u(s)){d}s+V(\hat{t},y(\hat{t};t,x,u(\cdot)))\right\}\tag{8}
>$$

>[!note] 动态规划思想
>其实是某种“无后效性”。最优控制的传统观点是要在整个时间段$[0,T]$上寻找控制$\bar{u}(\cdot)$，但动态规划是考虑如果走到某个时刻$\hat{t}\in[0,T]$，该如何选取$\hat{t}$之后的控制，使得未来的效果最好。如果$\bar{u}$是总体的最优控制，那么$\bar{u}\mid_{[\hat{t},T]}$就是$[\hat{t},T]$上的最优控制，即总体最优$\Longrightarrow$局部最优。
>
>形式上，我们可以这么描述，考虑在$[0,\hat{t}]$上取固定值的控制$u(\cdot)$
>$$
>\begin{aligned}
>J(u(\cdot))=&\int_{0}^{T}f^0(t,y(t),u(t)){d}t+g(y(T))\\
>=&\textcolor{red}{\int_{0}^{\hat{t}}f^0\left(t, y(t; 0, y_0, u\bigg|_{[0, \hat{t}]} ),u \bigg|_{[0, \hat{t}]} (t)\right)dt}\\
>&\textcolor{blue}{+\int_{\hat{t}}^{T} f^0\left(t, y(t; \hat{t}, y(\hat{t})), u \mid_{[\hat{t}, T]} (\cdot)\right)dt+g\left(y(T;\hat{t},y(\hat{t}),u\bigg|_{[\hat{t},T]})\right)}
>\end{aligned}
>$$
>注意到红色部分$u(\cdot)$的取值和$[\hat{t},T]$上取值无关，蓝色部分又与$[0,\hat{t}]$上无关，因此我们只需要考虑在$[\hat{t},T]$上$u(\cdot)$的取值，使得指标泛函最小，而这个问题恰好就是问题(D$_{\hat{t}y(\hat{t})}$)

**Proof**
我们记
$$
\overline{V}(t,x)=\inf_{u(\cdot)\in\mathscr{U}[t,\hat{t}]}\left\{\int_{t}^{\hat{t}}f^0(s,y(s;t,x,u(\cdot)),u(s)){d}s+V(\hat{t},y(\hat{t};t,x,u(\cdot)))\right\}
$$
则对于$\forall u(\cdot)\in\mathscr{U}[t,\hat{t}]$, 
$$
\begin{aligned}
V(t,x)\le J(u(\cdot);t,x)=\int_{t}^{\hat{t}}f^0(s,y(s),u(s)){d}s+J(u(\cdot)|_{[\hat{t},T]};\hat{t},y(\hat{t}))
\end{aligned}
$$
对右边取下确界$u(\cdot)\in\mathscr{U}[\hat{t},T]$，则可以得到$V(t,x)\le \overline{V}(t,x)$。另一方面对$u(\cdot)\in\mathscr{U}[t,T]$
$$
\begin{aligned}
J(u(\cdot);t,x)&=\int_{t}^{\hat{t}}f^0(s,y(s),u(s)){d}s+J(u(\cdot);\hat{t},y(\hat{t};u(\cdot)|_{[t,\hat{t}]}))\\
&\ge\int_{t}^{\hat{t}}f^0(s,y(s),u(s)){d}s+V(\hat{t},y(\hat{t}))\ge \overline{V}(t,x)
\end{aligned}
$$
对左边取下确界$u(\cdot)\in\mathscr{U}[t,T]$，可以得到$V(t,x)\ge \overline{V}(t,x)$。
**QED**

>[!warning] 
>实际上动态规划法也给出了最优控制的一个必要条件。当$u(\cdot)$在$[0,\hat{t}]$的取值固定，那么$J(u(\cdot))$的下确界必须为
>$$
>\int_{0}^{\hat{t}}f^0\left(t,y(t;0,y_0,u|_{[0,\hat{t}]})\right)+V(\hat{t},y(\hat{t}))
>$$

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

**Proof**
我们固定$u(s)\equiv u$，根据(8)式，可以得到
$$
\begin{aligned}
&V(t,x)\le \int_{t}^{\hat{t}}f^0(s,y(s),u){d}s+V(\hat{t},y(\hat{t}))\\
\Longrightarrow&-\frac{V(\hat{t},y(\hat{t}))-V(t,x)}{\hat{t}-t}-\frac{1}{\hat{t}-t}\int_{t}^{\hat{t}}f^0(s,y(s),u){d}s\le 0
\end{aligned}
$$
此时令$\hat{t}\to t$可以得到
$$
-V_t(t,x)+\left\langle V_x,f(t,y(t),u)\right\rangle-f^0(t,y(t),u)\le 0
$$
即可得到
$$
-V_t+\sup_{u\in U}H(t,x,u,-V_x)\le 0
$$
另一方面对$\varepsilon>0$和$0\le t<\hat{t}\le T$，存在$u(\cdot)=u_{\varepsilon,\hat{t}}(\cdot)$使得
$$
\begin{aligned}
&V(t,x)+\varepsilon(\hat{t}-t)\le \int_{t}^{\hat{t}}f^0(s,y(s),u(s)){d}s+V(\hat{t},y(\hat{t}))\\
\Longrightarrow&-\frac{V(\hat{t},y(\hat{t}))-V(t,x)}{\hat{t}-t}-\frac{1}{\hat{t}-t}\int_{t}^{\hat{t}}f^0(s,y(s),u(s)){d}s\le-\varepsilon
\end{aligned}
$$
**QED**

（HJB）方程的作用就是帮助我们找到最优对，下面讲解如何通过（HJB）方程的解寻找最优对。

>[!note] Step1 求解（HJB）方程得到值函数$V(t,x)$

>[!note] Step2 确定最优控制$\bar{u}$

>[!note] Step3  取$(t,x)=(0,y_0)$求解最优状态轨线，从而得到最优对

