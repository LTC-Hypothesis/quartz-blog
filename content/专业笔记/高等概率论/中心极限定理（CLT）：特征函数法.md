>[!thm] 测试有界连续函数确定同分布
>设 $\xi,\eta$ 为实值随机变量，则
>$$
>\xi\stackrel d=\eta
>\quad\Longleftrightarrow\quad
>\mathbb{E}g(\xi)=\mathbb{E}g(\eta),
>\qquad\forall g\in C_b(\mathbb{R}),
>$$
>其中 $C_b(\mathbb{R})$ 表示所有有界连续实函数。

^bounded-continuous-determine-law

**Proof**

$\Longrightarrow$: 由[[随机变量与分布函数|分布]]相同及[[积分与期望|按分布计算期望]]直接得到，这是显然的。

$\Longleftarrow$：固定 $x\in\mathbb{R}$，令
$$
g_\varepsilon(y)=
\begin{cases}
1,&y\le x,\\
1-(y-x)/\varepsilon,&x<y<x+\varepsilon,\\
0,&y\ge x+\varepsilon.
\end{cases}
$$
则 $g_\varepsilon\in C_b(\mathbb{R})$，并且
$$
\mathbb{1}_{(-\infty,x]}
\le g_\varepsilon
\le\mathbb{1}_{(-\infty,x+\varepsilon]}.
$$
因此
$$
\begin{aligned}
\mathbb{P}(\xi\le x)=\int_{-\infty}^{x}f_\varepsilon(t)F_\xi(t)\le&\int_{-\infty}^{\infty}f_\varepsilon(t)F_\xi(dt)\\
=&\int_{-\infty}^{\infty}f_\varepsilon(t)F_\eta(dt)\\
=&\int_{-\infty}^{x+\varepsilon}f_\varepsilon(t)F_\eta(dt)=\mathbb{P}(\eta\le x+\varepsilon)
\end{aligned}
$$
令 $\varepsilon\downarrow0$，由分布函数右连续性，$F_\xi(x)\le F_\eta(x)$。交换 $\xi,\eta$ 即得 $F_\xi=F_\eta$。

**QED**

>[!def] 特征函数
>实值随机变量 $\xi$ 的特征函数定义为
>$$
>f_\xi(t)=\mathbb{E}e^{it\xi}
>=\mathbb{E}\cos(t\xi)+i\mathbb{E}\sin(t\xi),
>\qquad t\in\mathbb{R}.
>$$
>若 $\xi$ 的分布为 $\mu$，也记为
>$$
>f_\mu(t)=\int_{\mathbb{R}}e^{itx}\,\mu(dx).
>$$
>由于 $|e^{it\xi}|=1$，特征函数总是存在，不要求 $\xi$ 有一阶矩或密度。

^characteristic-function

>[!lemma] 从紧支撑测试函数推广到有界连续测试函数
>设 $\mu_n,\mu$ 都是 $\mathbb{R}$ 上的概率测度。如果
>$$
>\int g\,d\mu_n\longrightarrow\int g\,d\mu,
>\qquad\forall g\in C_c(\mathbb{R}),
>$$
>则对所有 $g\in C_b(\mathbb{R})$ 也成立。
>
>这里 $C_c(\mathbb{R})$ 为紧支撑连续函数的集合，
>$$
>\operatorname{supp}g=\overline{\{x:g(x)\ne0\}}.
>$$

^compact-tests

**Proof**

给定 $\varepsilon>0$。由 $\mu(\mathbb{R})=1$，可以选取充分大的 $R$ 及连续截断函数 $\chi$，使得
$$
0\le\chi\le1,\qquad
\chi=1\text{ on }[-R,R],\qquad
\chi=0\text{ outside }[-R-1,R+1],
$$
且 $\int\chi\,d\mu>1-\varepsilon$。由假设，对充分大的 $n$，
$$
\int(1-\chi)\,d\mu_n<2\varepsilon,
\qquad \int(1-\chi)\,d\mu<\varepsilon.
$$
对任意 $g\in C_b(\mathbb{R})$，$g\chi\in C_c(\mathbb{R})$，故
$$
\begin{aligned}
\left|\int g\,d\mu_n-\int g\,d\mu\right|
&\le\left|\int g\chi\,d\mu_n-\int g\chi\,d\mu\right|\\
&\quad+\|g\|_\infty
\left[\int(1-\chi)\,d\mu_n+\int(1-\chi)\,d\mu\right].
\end{aligned}
$$
先令 $n\to\infty$，再令 $\varepsilon\downarrow0$ 即得结论。这里用到了极限测度的总质量仍为 $1$。

**QED**

>[!def] 卷积与磨光化子
>在积分有意义时，定义
>$$
>(f*g)(x)=\int_{\mathbb{R}}f(x-y)g(y)\,dy
>=\int_{\mathbb{R}}f(y)g(x-y)\,dy.
>$$
>所以 $f*g=g*f$。对 $\varepsilon>0$，令
>$$
>\phi_\varepsilon(x)
>=\frac1{\sqrt{2\pi}\varepsilon}
>e^{-x^2/(2\varepsilon^2)},
>$$
>即 $N(0,\varepsilon^2)$ 的密度。用 $g*\phi_\varepsilon$ 逼近 $g$。

>[!lemma] 磨光逼近
>若 $g\in C_c(\mathbb{R})$，则
>$$
>g*\phi_\varepsilon\in C^\infty(\mathbb{R}),\qquad
>\|g*\phi_\varepsilon-g\|_\infty\longrightarrow0
>\quad(\varepsilon\downarrow0).
>$$

^gaussian-approximation

**Proof**
对于 $h>0$ ，考虑
$$
\begin{aligned}
\frac{g*\phi_\varepsilon(x+h)-g*\phi_\varepsilon(x)}{h}=\int_{-\infty}^{\infty}g(y)\frac{\phi_\varepsilon(x+h-y)-\phi_\varepsilon(x-y)}{h}{d}y
\end{aligned}
$$
注意到上述积分实际上可以限制在 $g$ 的支撑上积分。由DCT，令 $h\to0$，得到
$$
\frac{d}{dx}g*\phi_\varepsilon(x)=\int_{-\infty}^{\infty}g(y)\phi_\varepsilon'(x-y){d}y
$$
类似地，通过数学归纳法，可以证明
$$
\frac{d^m}{dx^m}g*\phi_\varepsilon(x)=\int_{-\infty}^{\infty}g(y)\phi_\varepsilon^{(m)}(x-y){d}y,\forall m\ge1
$$
再看一致逼近。取 $Z\sim N(0,1)$，注意到
$$
\begin{aligned}
(g*\phi_\varepsilon)(x)&=\frac{1}{\sqrt{2\pi}\varepsilon}\int_{-\infty}^{\infty}\exp\left(-\frac{y^2}{2\varepsilon^2}\right)g(x-y){d}y\\
&\overset{y=\varepsilon z}{=}\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}\exp\left(-\frac{y^2}{2}\right)g(x-\varepsilon z){d}\\
&=\mathbb{E}g(x-\varepsilon Z).
\end{aligned}
$$
于是
$$
\begin{aligned}
\sup_{x\in\mathbb{R}}\left|g*\phi_\varepsilon(x)-g(x)\right|=&\sup_{x\in\mathbb{R}}\left|\mathbb{E}[g(x-\varepsilon\cdot Z)-g(x)]\right|\\
\le&\mathbb{E}\sup_{x\in\mathbb{R}}|g(x-\varepsilon\cdot Z)-g(x)|\to0,\text{ as }\varepsilon\to0^+
\end{aligned}
$$

**QED**

>[!warning] 
>- 这与[[Approximation of bad functions by good functions#Regularization|磨光与近似恒等核]]的思想相同。这里使用的是高斯核；它不具有紧支撑，因此 $g*\phi_\varepsilon$ 一般也没有紧支撑。
>- 磨光后的函数无穷次可微的原因，主要是能将导数转移到具有无穷次可微的磨光化子上。

>[!lemma] 磨光后的 Fourier 配对公式
>记函数 $g$ 的 Fourier 变换为：
>$$
>\widehat g(t)=\int_{\mathbb{R}}e^{itx}g(x)\,dx,
>\qquad f_\xi(t)=\mathbb{E}e^{it\xi}.
>$$
>对任意 $g\in C_c(\mathbb{R})$、$\varepsilon>0$，
>$$
>\mathbb{E}[(g*\phi_\varepsilon)(\xi)]
>=\frac1{2\pi}\int_{\mathbb{R}}
>e^{-\varepsilon^2t^2/2}\widehat g(t)\overline{f_\xi(t)}\,dt.
>$$
^gaussian-fourier-pairing

**Proof**

我们直接从RHS开始计算，
$$
\begin{aligned}
\frac{1}{2\pi}\int_{-\infty}^{\infty}e^{-\frac{\varepsilon^2t^2}{2}}\hat{g}(\xi)\overline{f_\xi(t)}{d}t=&\frac{1}{2\pi}\int_{-\infty}^{\infty}e^{-\frac{\varepsilon^2t^2}{2}}\left(\int_{-\infty}^{\infty}e^{itx}g(x){d}x\right)\left(\int_{-\infty}^{\infty}e^{-ity}F_\xi(dy)\right)dt\\
=&\frac{1}{2\pi}\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}e^{-\frac{\varepsilon^2t^2}{2}}e^{it(x-y)}{d}t\cdot g(x){d}xF_\xi(dy)\\
=&\frac{1}{2\pi}\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}2\pi\phi_\varepsilon(x-y)\cdot g(x){d}xF_\xi(dy)\\
=&\int_{-\infty}^{\infty}g*\phi_\varepsilon(y)F_\xi(dy)=\mathbb{E}[g*\phi_\varepsilon(\xi)]
\end{aligned}
$$

**QED**

>[!thm] 特征函数唯一确定分布
>对实值随机变量 $\xi,\eta$，
>$$
>\xi\stackrel d=\eta
>\quad\Longleftrightarrow\quad
>f_\xi(t)=f_\eta(t),\qquad\forall t\in\mathbb{R}.
>$$
>也就是说，只需检验所有频率的 $\cos(tx),\sin(tx)$，就能确定分布。

^characteristic-uniqueness

**Proof**

$\Longrightarrow$: 显然。

$\Longleftarrow$: 若两特征函数处处相等，由上面的 Fourier 配对公式，对任意 $g\in C_c(\mathbb{R})$，
$$
\mathbb{E}[(g*\phi_\varepsilon)(\xi)]
=\mathbb{E}[(g*\phi_\varepsilon)(\eta)].
$$
于是
$$
\begin{aligned}
|\mathbb{E}g(\xi)-\mathbb{E}g(\eta)|&\le|\mathbb{E}g(\xi)-\mathbb{E}g*\phi_\varepsilon(\xi)|+|\mathbb{E}g*\phi(\eta)-\mathbb{E}g(\eta)|\\
&\le2\|g*\phi_\varepsilon-g\|_\infty\longrightarrow0,\text{ as }\varepsilon\to0^+.
\end{aligned}
$$
所以二者对所有 $C_c$ 测试函数的期望相等。将[[#^compact-tests|紧支撑测试函数引理]]用于推广到所有 $C_b$ 测试函数，再由[[#^bounded-continuous-determine-law|有界连续函数确定分布]]得到 $\xi\stackrel d=\eta$。

**QED**

>[!def] 依分布收敛
>设 $\xi_n,\xi$ 的分布函数分别为 $F_n,F$。若对 $F$ 的每个连续点 $x$，
>$$
>F_n(x)\longrightarrow F(x),
>$$
>则称 $\xi_n$ 依分布收敛到 $\xi$，记为
>$$
>\xi_n\xrightarrow{d}\xi
>$$
>此定义只涉及各自的分布，不要求这些随机变量原本定义在同一个概率空间上。

^convergence-in-distribution

>[!warning] 为什么只要求在 $F$ 的连续点收敛
>例如 $\xi_n=1/n$，$\xi=0$。虽然 $\xi_n\to\xi$，但
>$$
>F_n(0)=0,\qquad F(0)=1.
>$$
>$0$ 恰好是 $F$ 的跳跃点。分布函数连续点的条件对应
>$$
>\mathbb{P}(\xi=x)=F(x)-F(x-)=0,
>$$
>并不要求 $F(x)=0$。

>[!def] 弱收敛与淡收敛
>设 $\mu_n,\mu$ 为 $\mathbb{R}$ 上的概率测度。如果
>$$
>\int g\,d\mu_n\longrightarrow\int g\,d\mu,
>\qquad\forall g\in C_b(\mathbb{R}),
>$$
>则称 $\mu_n$ 弱收敛到 $\mu$（weak convergence），记为 $\mu_n\Rightarrow\mu$。
>
>对于随机变量的分布 $\mu_n=\mathcal{L}(\xi_n)$、$\mu=\mathcal{L}(\xi)$，即
>$$
>\mathbb{E}g(\xi_n)\longrightarrow\mathbb{E}g(\xi),
>\qquad\forall g\in C_b(\mathbb{R}).
>$$
>
>若只用 $C_c(\mathbb{R})$ 中的函数检验，称为淡收敛，记为 $\mu_n\xrightarrow{v}\mu$。

^weak-and-vague-convergence

>[!thm] Baby Skorokhod 嵌入定理
>若 $\xi_n\xrightarrow{d}\xi$，则可以在一个新的概率空间上构造 $\eta_n,\eta$，使得
>$$
>\eta_n\stackrel d=\xi_n,\qquad
>\eta\stackrel d=\xi,\qquad
>\eta_n\xrightarrow{a.s.}\eta.
>$$
>这是通过[[概率耦合方法|耦合]]实现的 Skorokhod 表示定理。

^skorokhod-representation

**Proof**

取概率空间
$$
(\Omega,\mathcal{F},\mathbb{P})
=((0,1),\mathcal{B}((0,1)),\text{Leb}).
$$
对分布函数 $F$，定义广义逆，这个想法类似于[[随机变量与分布函数#^cef490|给定分布函数，构造相应的随机变量]]，
$$
F^{-1}(u)
:=\inf\{y:F(y)\ge u\}
=\sup\{y:F(y)<u\},\qquad0<u<1.
$$
同理定义 $F_n^{-1}$，并令
$$
\eta_n(u)=F_n^{-1}(u),\qquad\eta(u)=F^{-1}(u).
$$
由分布函数的单调性、右连续性及两端极限，广义逆为有限实数，且
$$
F^{-1}(u)\le y\quad\Longleftrightarrow\quad u\le F(y).
$$
因此 $Q$ 可测，并且
$$
\mathbb{P}(\eta\le y)
=\int_0^1\mathbb{1}_{\{u\le F(y)\}}\,du
=F(y).
$$
所以 $\eta\stackrel d=\xi$。同理，$\eta_n\stackrel d=\xi_n$。这里均匀分布的是坐标 $u$，经过变换后的 $\eta$ 具有分布函数 $F$；这也是[[随机变量与分布函数|利用分布函数广义逆构造随机变量]]的方法。

下面证明几乎处处收敛。$F^{-1}$ 单调，所以在 $(0,1)$ 中至多有可数个不连续点。令
$$
\Omega_0=\{u\in(0,1):F^{-1}\text{ 在 }u\text{ 连续}\}.
$$
则 $\mathbb{P}(\Omega_0)=1$。

固定 $u\in\Omega_0$，给定 $\varepsilon>0$，由于 $F$ 的不连续点至多可数，可以选取 $F$ 的两个连续点 $y,z$，使
$$
F^{-1}(u)-\varepsilon<y<F^{-1}(u)<z<F^{-1}(u)+\varepsilon.
$$
由 $y<F^{-1}(u)$，有 $F(y)<u$。另一方面，因为 $F^{-1}$ 在 $u$ 连续，可以选取 $v>u$ 足够接近 $u$，使 $F^{-1}(v)<z$，于是
$$
F(z)\ge v>u.
$$
因此
$$
F(y)<u<F(z).
$$
由于 $y,z$ 是 $F$ 的连续点，$F_n(y)\to F(y)$、$F_n(z)\to F(z)$，故对充分大的 $n$，
$$
F_n(y)<u<F_n(z).
$$
再由广义逆的性质，
$$
y<F^{-1}_n(u)\le z.
$$
所以 $|F^{-1}_n(u)-F^{-1}(u)|<\varepsilon$，从而 $\eta_n(u)\to\eta(u)$。这对所有 $u\in\Omega_0$ 成立，即得到几乎处处收敛。

**QED**

>[!thm] 依分布收敛 $\Longleftrightarrow$ 弱收敛
>对实值随机变量 $\xi_n,\xi$，
>$$
>\xi_n\xrightarrow{d}\xi
>\quad\Longleftrightarrow\quad
>\mathbb{E}g(\xi_n)\longrightarrow\mathbb{E}g(\xi),
>\qquad\forall g\in C_b(\mathbb{R}).
>$$

^distribution-weak-equivalence

**Proof**

“$\Rightarrow$”：用上面的表示定理，在同一个新概率空间构造 $\eta_n\stackrel d=\xi_n$、$\eta\stackrel d=\xi$，且 $\eta_n\to\eta$ a.s.。

若 $g\in C_b(\mathbb{R})$，则连续性给出 $g(\eta_n)\to g(\eta)$ a.s.，有界性给出共同控制函数 $\|g\|_\infty$。由[[积分与期望#^9122df|DCT]]，
$$
\mathbb{E}g(\xi_n)=\mathbb{E}g(\eta_n)
\longrightarrow\mathbb{E}g(\eta)=\mathbb{E}g(\xi).
$$
这里应用 DCT 的是构造后的 $\eta_n$，不能直接从依分布收敛对原来的 $\xi_n$ 使用 DCT。

“$\Leftarrow$”：固定 $F$ 的连续点 $x$，对 $\beta\ge1$，令
$$
f_\beta(y)=
\begin{cases}
1,&y\le x,\\
1+\beta(x-y),&x<y<x+1/\beta,\\
0,&y\ge x+1/\beta,
\end{cases}
$$
以及
$$
g_\beta(y)=
\begin{cases}
1,&y\le x-1/\beta,\\
\beta(x-y),&x-1/\beta<y<x,\\
0,&y\ge x.
\end{cases}
$$
则 $f_\beta,g_\beta\in C_b(\mathbb{R})$，且
$$
0\le g_\beta\le\mathbb{1}_{(-\infty,x]}
\le f_\beta\le1.
$$
先固定 $\beta$，利用测试函数期望收敛，得到
$$
\mathbb{E}g_\beta(\xi)
\le\liminf_{n\to\infty}F_n(x)
\le\limsup_{n\to\infty}F_n(x)
\le\mathbb{E}f_\beta(\xi).
$$
再令 $\beta\to\infty$，注意到
$$
g_\beta(y)\to\mathbb{1}_{(-\infty,x)}(y),
\qquad
f_\beta(y)\to\mathbb{1}_{(-\infty,x]}(y).
$$
由 DCT，
$$
F(x-)\le\liminf_nF_n(x)
\le\limsup_nF_n(x)\le F(x).
$$
因为 $x$ 是 $F$ 的连续点，$F(x-)=F(x)$，所以 $F_n(x)\to F(x)$。

**QED**

>[!warning] 
>在 $\mathbb{R}$ 上，概率测度弱收敛与相应随机变量依分布收敛等价，因此二者通常都可以记为 $\Rightarrow$，但我们依然把 $\Longrightarrow$ 符号只留给弱收敛。

>[!example] 依分布收敛和弱收敛等价，为何还需要重视弱收敛的概念？
>设 $X_i$ 为 i.i.d.，$\mathbb{E}X_i=0$、$\mathbb{E}X_i^2=1$，令 $S_0=0$。对 $0\le t\le1$，作线性插值
>$$
>W_n(t)=\frac1{\sqrt n}
>\left[S_{\lfloor nt\rfloor}
>+(nt-\lfloor nt\rfloor)X_{\lfloor nt\rfloor+1}\right].
>$$
>固定 $t$ 时，$W_n(t)$ 是实值随机变量；把整条路径作为一个对象时，
>$$
>W_n:\Omega\longrightarrow C[0,1]
>$$
>是取值于连续函数空间的随机元素。Donsker 不变原理断言
>$$
>W_n\Rightarrow B\quad\text{in }(C[0,1],\|\cdot\|_\infty),
>$$
>其中 $B$ 为标准 Brownian motion。
>
>此处弱收敛的意思是：对每个有界连续泛函 $H:C[0,1]\to\mathbb{R}$，$\mathbb{E}H(W_n)\to\mathbb{E}H(B)$。它包含各固定时刻的 CLT，但不能仅由逐个时刻的 CLT 推出；还要处理有限维分布与路径分布的紧性。
>
>但是注意到 $C[0,1]$ 是一个无穷维空间，无法在其上定义分布，因此也不能定义依分布收敛，因此只能使用弱收敛来刻画。
>
>关于不变原理见[[The continuous space, weak convergence, and Wiener measure#The Invariance Principle and the Wiener Measure|Donsker 不变原理与 Wiener 测度]]。

>[!thm] Portmanteau 定理（框架定理）
>设 $\xi_n,\xi$ 为实值随机变量。下列条件等价：
>
>1. $\xi_n\xrightarrow{d}\xi$。
>2. 对每个开集 $G\subset\mathbb{R}$，
>$$
>\liminf_{n\to\infty}\mathbb{P}(\xi_n\in G)
>\ge\mathbb{P}(\xi\in G).
>$$
>3. 对每个闭集 $K\subset\mathbb{R}$，
>$$
>\limsup_{n\to\infty}\mathbb{P}(\xi_n\in K)
>\le\mathbb{P}(\xi\in K).
>$$
>4. 对每个满足 $\mathbb{P}(\xi\in\partial A)=0$ 的 Borel 集 $A$，
>$$
>\mathbb{P}(\xi_n\in A)\longrightarrow\mathbb{P}(\xi\in A).
>$$

^portmanteau

**Proof**

$(1)\Rightarrow(2)$：仍使用 Skorokhod 构造的 $\eta_n\to\eta$ a.s.。因为 $G$ 为开集，若 $\eta(u)\in G$，则 $\eta_n(u)$ 最终也在 $G$ 内，因此
$$
\mathbb{1}_G(\eta)
\le\liminf_n\mathbb{1}_G(\eta_n)\qquad a.s.
$$
由[[积分与期望|Fatou 引理]]，
$$
\mathbb{P}(\xi\in G)
=\mathbb{E}\mathbb{1}_G(\eta)
\le\mathbb{E}\liminf_n\mathbb{1}_G(\eta_n)
\le\liminf_n\mathbb{P}(\xi_n\in G).
$$

$(2)\Longleftrightarrow(3)$：对补集使用
$$
\mathbb{P}(\xi_n\in K)
=1-\mathbb{P}(\xi_n\in K^c),
$$
并注意 $K$ 闭当且仅当 $K^c$ 开。

$(2),(3)\Rightarrow(4)$：因为 $A^\circ\subset A\subset\overline A$，
$$
\begin{aligned}
\mathbb{P}(\xi\in A^\circ)
&\le\liminf_n\mathbb{P}(\xi_n\in A)\\
&\le\limsup_n\mathbb{P}(\xi_n\in A)
\le\mathbb{P}(\xi\in\overline A).
\end{aligned}
$$
又 $\partial A=\overline A\setminus A^\circ$，且 $\mathbb{P}(\xi\in\partial A)=0$，两端都等于 $\mathbb{P}(\xi\in A)$。

$(4)\Rightarrow(1)$：若 $x$ 为 $F$ 的连续点，取 $A=(-\infty,x]$，则
$$
\partial A=\{x\},\qquad
\mathbb{P}(\xi\in\partial A)=F(x)-F(x-)=0.
$$
于是 $\mathbb{P}(\xi_n\le x)=F_n(x)\to F(x)=\mathbb{P}(\xi\le x)$。

**QED**

>[!thm] 特征函数连续性定理
>设 $\xi_n,\xi$ 为实值随机变量，则
>$$
>f_{\xi_n}(t)\longrightarrow f_\xi(t),\quad\forall t\in\mathbb{R}
>\quad\Longleftrightarrow\quad
>\xi_n\xrightarrow{d}\xi.
>$$

^levy-continuity

**Proof**

$\Longleftarrow$：由[[#^distribution-weak-equivalence|依分布收敛与弱收敛等价]]，分别用 $\cos(tx),\sin(tx)$ 作为有界连续测试函数即可。

$\Longrightarrow$：由[[#^compact-tests|紧支撑测试函数引理]]，只需证明对任意 $h\in C_c(\mathbb{R})$，
$$
\mathbb{E}h(\xi_n)\longrightarrow\mathbb{E}h(\xi).
$$
固定 $\delta>0$。由[[#^gaussian-approximation|磨光逼近]]，可取 $\varepsilon>0$，使
$$
\|h*\phi_\varepsilon-h\|_\infty<\delta.
$$
注意先固定这个 $\varepsilon$，再令 $n\to\infty$。由[[#^gaussian-fourier-pairing|磨光后的 Fourier 配对公式]]，
$$
\begin{aligned}
|\mathbb{E}h(\xi_n)-\mathbb{E}h(\xi)|
&\le|\mathbb{E}h(\xi_n)-\mathbb{E}(h*\phi_\varepsilon)(\xi_n)|\\
&\quad+|\mathbb{E}(h*\phi_\varepsilon)(\xi_n)
-\mathbb{E}(h*\phi_\varepsilon)(\xi)|\\
&\quad+|\mathbb{E}(h*\phi_\varepsilon)(\xi)-\mathbb{E}h(\xi)|\\
&\le2\delta+\frac1{2\pi}\int_{\mathbb{R}}
|\widehat h(t)|e^{-\varepsilon^2t^2/2}
|f_{\xi_n}(t)-f_\xi(t)|\,dt.
\end{aligned}
$$
由于 $h\in C_c(\mathbb{R})$，$\|\widehat h\|_\infty\le\|h\|_1<\infty$。最后的被积函数趋于 $0$，并且由可积函数
$$
2\|h\|_1e^{-\varepsilon^2t^2/2}
$$
控制。因此由[[积分与期望#^9122df|DCT]]，
$$
\limsup_{n\to\infty}
|\mathbb{E}h(\xi_n)-\mathbb{E}h(\xi)|\le2\delta.
$$
再令 $\delta\downarrow0$，得到结论。

**QED**

>[!note] By-product
>弱收敛也可以只用 $C_b^\infty(\mathbb{R})$ 中的测试函数检验，其中函数及各阶导数均有界。因为对任意 $h\in C_c$，$h*\phi_\varepsilon$ 属于这一类，且一致逼近 $h$；再用上面的三项分解及[[#^compact-tests|截断推广]]即可。

>[!thm] Lindeberg 替换法：光滑测试函数的误差估计
>设 $X_1,X_2,\cdots$ 为 i.i.d.，满足
>$$
>\mathbb{E}X_1=0,\qquad \mathbb{E}X_1^2=1,\qquad
>\rho:=\mathbb{E}|X_1|^3<\infty.
>$$
>令 $Y\sim N(0,1)$。对任意 $f\in C_b^3(\mathbb{R})$，有
>$$
>\left|\mathbb{E}f\left(\frac1{\sqrt n}\sum_{i=1}^nX_i\right)
>-\mathbb{E}f(Y)\right|
>\le\frac{\|f'''\|_\infty}{6\sqrt n}
>\left(\rho+\mathbb{E}|Y|^3\right).
>$$
>这里 $C_b^3$ 指 $f$ 及其一至三阶导数连续有界。常数$C\sim \rho,\|f'''\|_\infty$

^lindeberg-replacement

**Proof**

构造 $Y_1,Y_2,\cdots$ 为 i.i.d. $N(0,1)$，并且与整列 $\{X_i\}$ 独立。因为
$$
\mathbb{E}\exp\left(\frac{it}{\sqrt n}\sum_{i=1}^nY_i\right)
=\prod_{i=1}^n e^{-t^2/(2n)}=e^{-t^2/2},
$$
由[[#^characteristic-uniqueness|特征函数唯一性]]，
$$
\frac1{\sqrt n}\sum_{i=1}^nY_i\stackrel d=Y.
$$
因此可以把 $X_i$ 逐个替换为 $Y_i$。

定义
$$
R_i=\frac1{\sqrt n}
\left(\sum_{j=1}^{i-1}Y_j+\sum_{j=i+1}^nX_j\right),
\qquad1\le i\le n,
$$
空和记作 $0$。特别地，
$$
R_1=\frac1{\sqrt n}\sum_{j=2}^nX_j,\qquad
R_n=\frac1{\sqrt n}\sum_{j=1}^{n-1}Y_j.
$$
求和得到
$$
\begin{aligned}
&\mathbb{E}f\left(\frac1{\sqrt n}\sum_{i=1}^nX_i\right)
-\mathbb{E}f\left(\frac1{\sqrt n}\sum_{i=1}^nY_i\right)\\
&\qquad=\sum_{i=1}^n\mathbb{E}
\left[f\left(R_i+\frac{X_i}{\sqrt n}\right)
-f\left(R_i+\frac{Y_i}{\sqrt n}\right)\right].
\end{aligned}
$$
在 $R_i$ 处作 Taylor 展开：
$$
f(R_i+u)=f(R_i)+f'(R_i)u+\frac12f''(R_i)u^2+r_i(u),
\qquad
|r_i(u)|\le\frac{\|f'''\|_\infty}{6}|u|^3.
$$
由[[独立性]]，$R_i$ 分别与 $X_i,Y_i$ 独立。因此一阶项的期望都为 $0$，二阶项的期望相同：
$$
\mathbb{E}[f'(R_i)X_i]=\mathbb{E}[f'(R_i)Y_i]=0,
$$
$$
\mathbb{E}[f''(R_i)X_i^2]
=\mathbb{E}f''(R_i)
=\mathbb{E}[f''(R_i)Y_i^2].
$$
只剩余项，故
$$
\begin{aligned}
&\left|\mathbb{E}f\left(\frac1{\sqrt n}\sum_{i=1}^nX_i\right)
-\mathbb{E}f(Y)\right|\\
&\qquad\le\sum_{i=1}^n
\frac{\|f'''\|_\infty}{6n^{3/2}}
\left(\mathbb{E}|X_i|^3+\mathbb{E}|Y_i|^3\right)\\
&\qquad=\frac{\|f'''\|_\infty}{6\sqrt n}
\left(\rho+\mathbb{E}|Y|^3\right).
\end{aligned}
$$

**QED**

>[!warning] 两种分布距离
>对具有有限一阶矩的 $\xi,\eta$，记
>$$
>d(\xi,\eta)
>=\sup_{\operatorname{Lip}(h)\le1}
>|\mathbb{E}h(\xi)-\mathbb{E}h(\eta)|.
>$$
>这是 [[Wasserstein空间|Wasserstein-1 距离]]的对偶形式。必须限制 Lipschitz 常数不超过 $1$，否则测试函数可以任意放大。
>
>另记 Kolmogorov 距离
>$$
>\widetilde d(\xi,\eta)
>=\sup_{x\in\mathbb{R}}|F_\xi(x)-F_\eta(x)|.
>$$
>若 $\eta$ 的分布函数 $G$ 具有有界密度 $G'\le\lambda$，用宽度为 $\delta$ 的线性截断逼近示性函数，可得
>$$
>\widetilde d(\xi,\eta)\le\frac{d(\xi,\eta)}{\delta}
>+\frac{\lambda\delta}{2}.
>$$
>对 $\delta>0$ 取最优值得到 $\widetilde d\le\sqrt{2\lambda d}$。特别地，若 $\eta\sim N(0,1)$，则 $\lambda=1/\sqrt{2\pi}$，从而 $\widetilde d\le\sqrt d$。这里需要对参照分布的密度作控制。

>[!thm] Berry–Esseen 界
>设 $X_1,X_2,\cdots$ 为 i.i.d.，满足
>$$
>\mathbb{E}X_1=0,\qquad \mathbb{E}X_1^2=1,\qquad
>\rho=\mathbb{E}|X_1|^3<\infty.
>$$
>记
>$$
>F_n(x)=\mathbb{P}\left(\frac1{\sqrt n}\sum_{i=1}^nX_i\le x\right),
>\qquad \Phi(x)=\mathbb{P}(Y\le x),\quad Y\sim N(0,1).
>$$
>则对每个 $n\ge1$，
>$$
>\sup_{x\in\mathbb{R}}|F_n(x)-\Phi(x)|
>\le\frac{3\rho}{\sqrt n}.
>$$

^berry-esseen

在这之前我们需要逆转公式和一些不等式估计。

>[!thm] 特征函数的反演公式
>设 $\mu$ 为 $\mathbb{R}$ 上的概率测度，其特征函数为
>$$
>\varphi(t)=\int_{\mathbb{R}}e^{itx}\,\mu(dx).
>$$
>则对任意 $a<b$，
>$$
>\lim_{T\to\infty}\frac1{2\pi}\int_{-T}^T
>\frac{e^{-ita}-e^{-itb}}{it}\varphi(t)\,dt
>=\mu((a,b))+\frac12\mu(\{a,b\}).
>$$
>$t=0$ 处的比值按连续延拓取值 $b-a$。端点有原子时各计一半；两端点都是连续点时，右侧就是 $F(b)-F(a)$。

^characteristic-inversion

**Proof**

记左侧有限 $T$ 的积分为 $I_T$。因为
$$
\frac{e^{-ita}-e^{-itb}}{it}=\int_a^b e^{-ity}\,dy,
\qquad
\left|\frac{e^{-ita}-e^{-itb}}{it}\right|\le b-a,
$$
在有限区间 $[-T,T]$ 上可以用[[Fubini定理及其应用|Fubini 定理]]交换积分。于是
$$
I_T=\frac1{2\pi}\int_{\mathbb{R}}
\left[\int_{-T}^T
\frac{e^{it(x-a)}-e^{it(x-b)}}{it}\,dt\right]\mu(dx).
$$
虚部关于 $t$ 为奇函数，积分为 $0$。令
$$
R(\theta,T)=\int_{-T}^T\frac{\sin(\theta t)}{t}\,dt,
\qquad
S(A)=\int_0^A\frac{\sin u}{u}\,du,
$$
则
$$
I_T=\frac1{2\pi}\int
[R(x-a,T)-R(x-b,T)]\,\mu(dx),
$$
且
$$
R(\theta,T)=2\operatorname{sgn}(\theta)S(T|\theta|).
$$
由 Dirichlet 积分 $\int_0^\infty\sin u/u\,du=\pi/2$，有
$$
R(\theta,T)\longrightarrow\pi\operatorname{sgn}(\theta)\text{ as }T\to\infty.
$$
所以
$$
R(x-a,T)-R(x-b,T)\longrightarrow
\begin{cases}
2\pi,&a<x<b,\\
\pi,&x=a\text{ 或 }x=b,\\
0,&x<a\text{ 或 }x>b.
\end{cases}
$$
又因为 $S(A)$ 收敛且在有界区间上连续，所以 $\sup_{A\ge0}|S(A)|<\infty$。因此上面的被积函数关于 $x,T$ 一致有界，由[[积分与期望#^9122df|DCT]]得到结论。

**QED**

>[!def] Pólya 分布
>对 $L>0$，令
>$$
>h_L(x)=\frac{1-\cos(Lx)}{\pi Lx^2}\quad(x\ne0),
>\qquad h_L(0)=\frac{L}{2\pi}.
>$$
>由分部积分及 Dirichlet 积分，
>$$
>\int_{\mathbb{R}}h_L(x)\,dx
>=\frac2\pi\int_0^\infty\frac{1-\cos u}{u^2}\,du
>=\frac2\pi\int_0^\infty\frac{\sin u}{u}\,du=1.
>$$
>因此它是概率密度，其特征函数为
>$$
>W_L(t)=\left(1-\frac{|t|}{L}\right)^+
>=\begin{cases}
>1-|t|/L,&|t|\le L,\\
>0,&|t|>L.
>\end{cases}
>$$
>这对 Fourier 变换可由
>$$
>\frac1{2\pi}\int_{-L}^L e^{-itx}\left(1-\frac{|t|}{L}\right)dt
>=\frac1\pi\int_0^L\left(1-\frac tL\right)\cos(tx)\,dt
>=h_L(x)
>$$
>得到。
>
>对分布函数 $F$，记
>$$
>F_L(x)=(F*h_L)(x)=\int_{\mathbb{R}}F(x-y)h_L(y)\,dy.
>$$
>若 $X\sim F$，$Z_L$ 与 $X$ 独立且密度为 $h_L$，则 $F_L$ 是 $X+Z_L$ 的分布函数，因此其特征函数为 $\varphi_F(t)W_L(t)$。

^polya-smoothing-kernel

>[!lemma] 磨光前后的分布函数误差
>设 $F,G$ 为分布函数，$G$ 绝对连续，且 $0\le G'(x)\le\lambda$ a.e.，其中 $0<\lambda<\infty$。令
>$$
>\Delta(x)=F(x)-G(x),\qquad
>\eta=\sup_x|\Delta(x)|,
>$$
>$$
>\Delta_L=\Delta*h_L=F_L-G_L,\qquad
>\eta_L=\sup_x|\Delta_L(x)|.
>$$
>则
>$$
>\eta\le2\eta_L+\frac{24\lambda}{\pi L}.
>$$

^smoothing-error

**Proof**

$\eta=0$ 时显然。设 $\eta>0$，先考虑给定 $\epsilon>0$，取 $x_0$，使 $\Delta(x_0)\ge\eta-\epsilon$。由 $F$ 单调及 $G'\le\lambda$，对 $s\ge0$，
$$
\Delta(x_0+s)\ge\Delta(x_0)-\lambda s
\ge\eta-\epsilon-\lambda s.
$$
取
$$
\delta=\frac{\eta}{2\lambda},\qquad t=x_0+\delta.
$$
则当 $|x|\le\delta$ 时，
$$
\Delta(t-x)\ge\eta-\epsilon-\lambda(\delta-x)
=\frac\eta2-\epsilon+\lambda x;
$$
当 $|x|>\delta$ 时，总有 $\Delta(t-x)\ge-\eta$。

由于 $h_L$ 为偶函数，
$$
\int_{-\delta}^{\delta}xh_L(x)\,dx=0,
$$
并且
$$
q:=\int_{|x|>\delta}h_L(x)\,dx
\le2\int_\delta^\infty\frac{2}{\pi Lx^2}\,dx
=\frac4{\pi L\delta}.
$$
因此
$$
\begin{aligned}
\eta_L\ge\Delta_L(t)
&\ge\left(\frac\eta2-\epsilon\right)(1-q)-\eta q\\
&\ge\frac\eta2-\epsilon-\frac{3\eta}{2}q\\
&\ge\frac\eta2-\epsilon-\frac{12\lambda}{\pi L}.
\end{aligned}
$$
令 $\epsilon\downarrow0$，整理即得结论。

**QED**

>[!lemma] 用特征函数控制分布函数误差
>在上一个引理的条件下，记 $\varphi_F,\varphi_G$ 为 $F,G$ 的特征函数。则对任意 $L>0$，
>$$
>\sup_x|F(x)-G(x)|
>\le\frac1\pi\int_{-L}^L
>\frac{|\varphi_F(t)-\varphi_G(t)|}{|t|}\,dt
>+\frac{24\lambda}{\pi L}.
>$$

^fourier-smoothing-inequality

**Proof**

先证明一个磨光后的估计，若右侧积分为 $+\infty$，结论显然；否则函数
$$
q_L(t)=\frac{[\varphi_F(t)-\varphi_G(t)]W_L(t)}{it}
$$
可积，$t=0$ 的值不影响积分。磨光后的 $F_L,G_L$ 连续，其特征函数分别为 $\varphi_FW_L,\varphi_GW_L$，在 $[-L,L]$ 外为 $0$。对 $a<x$，由[[#^characteristic-inversion|反演公式]]，
$$
\begin{aligned}
\Delta_L(x)-\Delta_L(a)&=[F_L(x)-F_L(a)]-[G_L(x)-G_L(a)]\\
&=\lim_{T\to\infty}\frac{1}{2\pi}\int_{-T}^{T}(e^{-ita}-e^{-itx})\frac{\varphi_{F_L}(t)-\varphi_{G_L}(t)}{it}{d}t\\
&=\lim_{T\to\infty}\frac{1}{2\pi}\int_{-T}^{T}(e^{-ita}-e^{-itx})\frac{(\varphi_{F}(t)-\varphi_{G}(t))W_L(t)}{it}{d}t\\
&=\frac1{2\pi}\int_{-L}^L(e^{-ita}-e^{-itx})q_L(t)\,dt.
\end{aligned}
$$
这需要注意，傅里叶变换（特征函数变换）可以把分布的卷积的特征函数变成分布的特征函数的乘积，另外由于Pólya 分布的特征函数具有紧支撑，因此积分可以限制在 $[-L,L]$ 上。令 $a\to-\infty$。$\Delta_L(a)\to0$，而 $q_L\in L^1$，由[[Durrett习题1.4|Riemann–Lebesgue 引理]]，含 $e^{-ita}$ 的积分趋于 $0$。所以
$$
\Delta_L(x)
=-\frac1{2\pi}\int_{-L}^L
e^{-itx}\frac{[\varphi_F(t)-\varphi_G(t)]W_L(t)}{it}\,dt.
$$
由 $|W_L|\le1$，
$$
\eta_L\le\frac1{2\pi}\int_{-L}^L
\frac{|\varphi_F(t)-\varphi_G(t)|}{|t|}\,dt.
$$
再代入 $\eta\le2\eta_L+24\lambda/(\pi L)$ 即得结论。

**QED**

下面回到[[#^berry-esseen|Berry–Esseen 界]]的证明。

**Proof**

记 $\varphi(t)=\mathbb{E}e^{itX_1}$。由独立性，标准化和的特征函数为
$$
\mathbb{E}\exp\left(\frac{it}{\sqrt n}\sum_{i=1}^nX_i\right)
=\left[\varphi\left(\frac t{\sqrt n}\right)\right]^n.
$$
标准正态的特征函数为 $e^{-t^2/2}$，密度上界为 $\lambda=1/\sqrt{2\pi}$。因此由平滑不等式，
$$
\sup_x|F_n(x)-\Phi(x)|
\le\frac1\pi\int_{-L}^L
\frac{\left|\varphi(t/\sqrt n)^n-e^{-t^2/2}\right|}{|t|}\,dt
+\frac{24}{\pi\sqrt{2\pi}\,L}.
$$

先准备两个估计。由 Taylor 余项界，
$$
\left|e^{iu}-1-iu+\frac{u^2}{2}\right|
\le\frac{|u|^3}{6},
$$
结合 $\mathbb{E}X_1=0$、$\mathbb{E}X_1^2=1$，
$$
\left|\varphi(t)-1+\frac{t^2}{2}\right|
\le\frac{\rho|t|^3}{6}.
$$
特别地，当 $t^2\le2$ 时，
$$
|\varphi(t)|\le1-\frac{t^2}{2}+\frac{\rho|t|^3}{6}.
$$
另一个是幂的差：若 $|\alpha|,|\beta|\le\gamma$，则
$$
|\alpha^n-\beta^n|
\le n|\alpha-\beta|\gamma^{n-1}.
$$

由于 $\rho=\mathbb{E}|X_1|^3\ge(\mathbb{E}X_1^2)^{3/2}=1$，当 $n\le9$ 时，$3\rho/\sqrt n\ge1$，结论由分布函数之差不超过 $1$ 直接得到。下面设 $n\ge10$，取
$$
L=\frac{4\sqrt n}{3\rho}\le\sqrt{2n}.
$$
对 $|t|\le L$，有 $\rho|t|/\sqrt n\le4/3$，因此
$$
\begin{aligned}
\left|\varphi\left(\frac t{\sqrt n}\right)\right|
&\le1-\frac{t^2}{2n}+\frac{\rho|t|^3}{6n^{3/2}}\\
&\le1-\frac{5t^2}{18n}
\le e^{-5t^2/(18n)}.
\end{aligned}
$$
令
$$
\alpha=\varphi(t/\sqrt n),\qquad
\beta=e^{-t^2/(2n)},\qquad
\gamma=e^{-5t^2/(18n)}.
$$
则 $|\alpha|,|\beta|\le\gamma$。又因为 $n\ge10$，
$$
\gamma^{n-1}
=e^{-5(n-1)t^2/(18n)}
\le e^{-t^2/4}.
$$

另一方面，对 $v\ge0$，$|e^{-v}-(1-v)|\le v^2/2$。所以
$$
\begin{aligned}
n|\alpha-\beta|
&\le n\left|\varphi(t/\sqrt n)-1+\frac{t^2}{2n}\right|
+n\left|1-\frac{t^2}{2n}-e^{-t^2/(2n)}\right|\\
&\le\frac{\rho|t|^3}{6\sqrt n}+\frac{t^4}{8n}.
\end{aligned}
$$
结合幂的差估计，对 $0<|t|\le L$，
$$
\frac{\left|\varphi(t/\sqrt n)^n-e^{-t^2/2}\right|}{|t|}
\le e^{-t^2/4}
\left(\frac{\rho t^2}{6\sqrt n}+\frac{|t|^3}{8n}\right).
$$
代回平滑不等式，并把积分区间扩大为 $\mathbb{R}$，得到
$$
\begin{aligned}
\sup_x|F_n(x)-\Phi(x)|
&\le\frac1\pi\int_{\mathbb{R}}e^{-t^2/4}
\left(\frac{\rho t^2}{6\sqrt n}+\frac{|t|^3}{8n}\right)dt
+\frac{18\rho}{\pi\sqrt{2\pi}\sqrt n}.
\end{aligned}
$$
最后计算
$$
\int_{\mathbb{R}}t^2e^{-t^2/4}\,dt=4\sqrt\pi,
\qquad
\int_{\mathbb{R}}|t|^3e^{-t^2/4}\,dt=16.
$$
故
$$
\begin{aligned}
\sup_x|F_n(x)-\Phi(x)|
&\le
\left(\frac{2}{3\sqrt\pi}+\frac{18}{\pi\sqrt{2\pi}}\right)
\frac{\rho}{\sqrt n}+\frac{2}{\pi n}\\
&\le
\left(\frac{2}{3\sqrt\pi}+\frac{18}{\pi\sqrt{2\pi}}
+\frac{2}{\pi\sqrt{10}}\right)\frac{\rho}{\sqrt n}\\
&<\frac{3\rho}{\sqrt n}.
\end{aligned}
$$
第二步使用了 $\rho\ge1$、$n\ge10$。这也补全了手稿最后 $C/\sqrt n$ 中常数的计算。

**QED**

>[!thm] 中心极限定理：去掉三阶矩条件
>设 $X_1,X_2,\cdots$ 为 i.i.d.，仅要求
>$$
>\mathbb{E}X_1=0,\qquad\mathbb{E}X_1^2=1.
>$$
>则
>$$
>\frac1{\sqrt n}\sum_{i=1}^nX_i\xrightarrow{d}N(0,1).
>$$

^iid-clt

**Proof**

由[[#^levy-continuity|特征函数连续性定理]]，只需证明对每个固定 $t\in\mathbb{R}$，
$$
\varphi(t/\sqrt n)^n\longrightarrow e^{-t^2/2},
\qquad\varphi(u)=\mathbb{E}e^{iuX_1}.
$$
没有三阶矩时，不能再用 $\mathbb{E}|X_1|^3$ 控制余项。使用两种余项界：
$$
\left|e^{iu}-\sum_{k=0}^m\frac{(iu)^k}{k!}\right|
\le\min\left\{\frac{|u|^{m+1}}{(m+1)!},
\frac{2|u|^m}{m!}\right\}.
$$
它们由积分型 Taylor 余项得到：分别使用 $|e^{iv}|\le1$ 和 $|e^{iv}-1|\le2$。取 $m=2$，得到
$$
\left|e^{iu}-1-iu+\frac{u^2}{2}\right|
\le\min\left\{\frac{|u|^3}{6},|u|^2\right\}.
$$
令
$$
r_n(t)=\varphi(t/\sqrt n)-1+\frac{t^2}{2n},
$$
由 $\mathbb{E}X_1=0$、$\mathbb{E}X_1^2=1$，
$$
\begin{aligned}
n|r_n(t)|
&\le n\mathbb{E}\min\left\{
\frac{|tX_1|^3}{6n^{3/2}},\frac{|tX_1|^2}{n}\right\}\\
&=\mathbb{E}\min\left\{
\frac{|tX_1|^3}{6\sqrt n},|tX_1|^2\right\}
\longrightarrow0.
\end{aligned}
$$
最后一步由[[积分与期望#^9122df|DCT]]：被积函数逐点趋于 $0$，且由可积函数 $t^2X_1^2$ 控制。于是
$$
\varphi(t/\sqrt n)=1-\frac{t^2}{2n}+o(n^{-1}).
$$
为严谨地处理复数的 $n$ 次幂，仍用前面的幂差估计。对充分大的 $n$，$0\le1-t^2/(2n)\le1$，而 $|\varphi(t/\sqrt n)|\le1$，所以
$$
\left|\varphi(t/\sqrt n)^n-
\left(1-\frac{t^2}{2n}\right)^n\right|
\le n|r_n(t)|\longrightarrow0.
$$
又
$$
\left(1-\frac{t^2}{2n}\right)^n\longrightarrow e^{-t^2/2},
$$
故得到所需的特征函数收敛，从而得到 CLT。

**QED**

>[!note]
>这给出[[De Moirve & Laplace 中心极限定理]]之外的一般 i.i.d. 证明。有限三阶绝对矩是上面 Berry–Esseen 误差界所用的充分条件；仅证明 CLT 时，有限二阶矩已经足够。

