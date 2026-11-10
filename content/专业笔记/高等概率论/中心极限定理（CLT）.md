>[!note] 中心极限定理
>令 $S_n=\sum_{i=1}^nX_i$。[[弱大数定律（WLLN）]]与[[强大数定律（SLLN）]]研究 $S_n/n$ 是否收敛到均值；中心极限定理（Central Limit Theorem，CLT）进一步研究样本平均在均值附近的波动。
>
>当 $X_1,X_2,\cdots$ 为 i.i.d.，$\mathbb{E}X_1=\mu$，$0<\operatorname{Var}(X_1)=\sigma^2<\infty$ 时，典型结论为
>$$
>\frac{S_n-n\mu}{\sigma\sqrt n}
>=\frac{\sqrt n}{\sigma}\left(\frac{S_n}{n}-\mu\right)
>\xrightarrow{d}N(0,1).
>$$
>这里是分布趋于正态分布，不是上述随机变量逐点趋于某个固定数。先从对称简单随机游走看起。

>[!thm] De Moivre–Laplace 中心极限定理：对称简单随机游走
>设 $X_1,X_2,\cdots$ 为 i.i.d.，且
>$$
>\mathbb{P}(X_i=1)=\mathbb{P}(X_i=-1)=\frac12,
>\qquad S_0=0,\quad S_n=\sum_{i=1}^nX_i.
>$$
>记标准正态密度及分布函数为
>$$
>\varphi(x)=\frac1{\sqrt{2\pi}}e^{-x^2/2},
>\qquad \Phi(x)=\int_{-\infty}^x\varphi(y)\,dy.
>$$
>则对任意 $-\infty<a<b<\infty$，
>$$
>\mathbb{P}\left(a\le\frac{S_n}{\sqrt n}\le b\right)
>\longrightarrow\int_a^b\varphi(x)\,dx.
>$$
>等价地，$S_n/\sqrt n\xrightarrow{d}N(0,1)$。

^de-moivre-laplace

**Proof**

先考虑偶数步。$S_{2n}=2k$ 等价于 $2n$ 次中恰有 $n+k$ 次向右走，因此
$$
\mathbb{P}(S_{2n}=2k)
=\binom{2n}{n+k}2^{-2n},
\qquad k=-n,-n+1,\cdots,n.
$$
由 Stirling 公式
$$
n!\sim\sqrt{2\pi n}\left(\frac ne\right)^n,
$$
当 $k=k_n$ 满足 $2k/\sqrt{2n}\to x$ 时，$k/n\to0$，从而
$$
\begin{aligned}
\mathbb{P}(S_{2n}=2k)
&\sim\frac1{\sqrt{\pi n}}
\left(1+\frac kn\right)^{-n-k-1/2}
\left(1-\frac kn\right)^{-n+k-1/2}\\
&=\frac1{\sqrt{\pi n}}
\left(1-\frac{k^2}{n^2}\right)^{-n-1/2}
\left(1+\frac kn\right)^{-k}
\left(1-\frac kn\right)^k.
\end{aligned}
$$
这里 $k$ 随 $n$ 变化，并且始终取整数。不能对任意实数 $x$ 直接令 $k=x\sqrt{n/2}$。

回顾一个常用极限：若 $c_n\to0$，$a_nc_n\to\lambda$，则
$$
(1+c_n)^{a_n}\to e^\lambda.
$$
事实上，$1+c_n>0$ 对充分大的 $n$ 成立，且
$$
a_n\log(1+c_n)
=a_nc_n\frac{\log(1+c_n)}{c_n}\longrightarrow\lambda.
$$
$c_n=0$ 时把后面的比值定义为 $1$ 即可。这里允许 $a_n$ 为负数；相关乘积形式见[[Durrett习题3.1]]。

由 $k^2/n\to x^2/2$，
$$
\begin{aligned}
\left(1-\frac{k^2}{n^2}\right)^{-n-1/2}&\to e^{x^2/2},\\
\left(1+\frac kn\right)^{-k}&\to e^{-x^2/2},\\
\left(1-\frac kn\right)^k&\to e^{-x^2/2}.
\end{aligned}
$$
所以得到局部估计
$$
\mathbb{P}(S_{2n}=2k)
\sim\frac1{\sqrt{\pi n}}e^{-x^2/2}
=\frac2{\sqrt{2n}}\varphi(x).
$$

>[!note] 局部中心极限定理中的格点间距
>准确的非零极限是
>$$
>\frac{\sqrt{2n}}2\,\mathbb{P}(S_{2n}=2k_n)
>\longrightarrow\varphi(x),
>\qquad \frac{2k_n}{\sqrt{2n}}\to x.
>$$
>单个点的概率本身趋于 $0$。因子 $2/\sqrt{2n}$ 是 $S_{2n}/\sqrt{2n}$ 相邻可取值的距离，也就是把概率求和变成 Riemann 和时的 $\Delta x$。

接下来从局部估计推出区间上的结论。需要说明，在有界区间内上面的近似可以一致成立。

令
$$
h(v)=(1+v)\log(1+v)+(1-v)\log(1-v).
$$
当 $v\to0$ 时，$h(v)=v^2+O(v^4)$。对固定 $M<\infty$，当 $|k|\le M\sqrt n$ 时，Stirling 公式的相对误差一致趋于 $0$，且
$$
nh(k/n)=\frac{k^2}{n}+O\left(\frac{k^4}{n^3}\right)
=\frac{k^2}{n}+O(n^{-1})
$$
也一致成立。因此
$$
\mathbb{P}(S_{2n}=2k)
=\frac2{\sqrt{2n}}\,
\varphi\left(\frac{2k}{\sqrt{2n}}\right)(1+o(1)),
$$
其中 $o(1)$ 在 $|k|\le M\sqrt n$ 上一致。于是
$$
\begin{aligned}
\mathbb{P}\left(a\le\frac{S_{2n}}{\sqrt{2n}}\le b\right)
&=\sum_{a\le2k/\sqrt{2n}\le b}\mathbb{P}(S_{2n}=2k)\\
&=(1+o(1))
\sum_{a\le2k/\sqrt{2n}\le b}
\varphi\left(\frac{2k}{\sqrt{2n}}\right)\frac2{\sqrt{2n}}\\
&\longrightarrow\int_a^b\varphi(x)\,dx.
\end{aligned}
$$

再考虑奇数步。记
$$
U_n=\frac{S_{2n}}{\sqrt{2n}},\qquad
c_n=\sqrt{\frac{2n}{2n+1}},\qquad
\delta_n=\frac1{\sqrt{2n+1}}.
$$
因为 $|X_{2n+1}|=1$，
$$
\frac{S_{2n+1}}{\sqrt{2n+1}}
=c_nU_n+\frac{X_{2n+1}}{\sqrt{2n+1}},
$$
从而对充分大的 $n$，
$$
\begin{aligned}
\mathbb{P}\left(\frac{a+\delta_n}{c_n}\le U_n
\le\frac{b-\delta_n}{c_n}\right)
&\le\mathbb{P}\left(a\le\frac{S_{2n+1}}{\sqrt{2n+1}}\le b\right)\\
&\le\mathbb{P}\left(\frac{a-\delta_n}{c_n}\le U_n
\le\frac{b+\delta_n}{c_n}\right).
\end{aligned}
$$
两侧端点分别趋于 $a,b$；再用固定的 $a\pm\varepsilon,b\pm\varepsilon$ 夹逼，并利用正态分布函数连续，即得奇数步的结论。

最后，$\mathbb{E}(S_n/\sqrt n)^2=1$，Chebyshev 不等式给出
$$
\mathbb{P}\left(\left|S_n/\sqrt n\right|>M\right)\le M^{-2}.
$$
所以在区间结论中令左端点趋于 $-\infty$，就得到分布函数收敛。

**QED**

>[!thm] 有界连续函数可以确定分布
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

正向由[[随机变量与分布函数|分布]]相同及[[积分与期望|按分布计算期望]]直接得到。

反向，固定 $x\in\mathbb{R}$，令
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
F_\xi(x)\le\mathbb{E}g_\varepsilon(\xi)
=\mathbb{E}g_\varepsilon(\eta)\le F_\eta(x+\varepsilon).
$$
令 $\varepsilon\downarrow0$，由分布函数右连续性，$F_\xi(x)\le F_\eta(x)$。交换 $\xi,\eta$ 即得 $F_\xi=F_\eta$。

**QED**

>[!def] 特征函数
>实值随机变量 $\xi$ 的特征函数（characteristic function）定义为
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

>[!note] 特征函数的基本性质
>$$
>f_\xi(0)=1,\qquad |f_\xi(t)|\le1,\qquad
>f_\xi(-t)=\overline{f_\xi(t)},
>$$
>$$
>f_{a\xi+b}(t)=e^{itb}f_\xi(at).
>$$
>特征函数一致连续。事实上
>$$
>|f_\xi(t+h)-f_\xi(t)|
>\le\mathbb{E}|e^{ih\xi}-1|\longrightarrow0,
>$$
>右侧与 $t$ 无关，由[[积分与期望#^9122df|DCT]]得到收敛。
>
>若 $\xi,\eta$ [[独立性|独立]]，则
>$$
>f_{\xi+\eta}(t)
>=\mathbb{E}(e^{it\xi}e^{it\eta})
>=f_\xi(t)f_\eta(t).
>$$
>这就是特征函数方法适合研究独立随机变量之和的原因。

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

>[!def] 卷积与高斯平滑
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
>即 $N(0,\varepsilon^2)$ 的密度。用 $g*\phi_\varepsilon$ 逼近 $g$，称为高斯平滑。

>[!lemma] 高斯核是近似恒等核
>若 $g\in C_c(\mathbb{R})$，则
>$$
>g*\phi_\varepsilon\in C^\infty(\mathbb{R}),\qquad
>\|g*\phi_\varepsilon-g\|_\infty\longrightarrow0
>\quad(\varepsilon\downarrow0).
>$$

^gaussian-approximation

**Proof**

先看光滑性。因为高斯核的每阶导数都有界，
$$
\left|g(y)\phi_\varepsilon^{(m)}(x-y)\right|
\le |g(y)|\,\|\phi_\varepsilon^{(m)}\|_\infty,
$$
而 $g\in L^1(\mathbb{R})$。用均值定理控制差商，再用 DCT 交换微分与积分，得到
$$
\frac{d^m}{dx^m}(g*\phi_\varepsilon)(x)
=\int_{\mathbb{R}}g(y)\phi_\varepsilon^{(m)}(x-y)\,dy.
$$
导数连续性同样由 DCT 得到。

再看一致逼近。取 $Z\sim N(0,1)$，则
$$
(g*\phi_\varepsilon)(x)=\mathbb{E}g(x-\varepsilon Z).
$$
因为 $g$ 连续且紧支撑，所以在整个 $\mathbb{R}$ 上一致连续。令
$$
\omega_g(\delta)=\sup_{|x-y|\le\delta}|g(x)-g(y)|,
$$
则 $\omega_g(\delta)\to0$。对任意 $\delta>0$，
$$
\|g*\phi_\varepsilon-g\|_\infty
\le\omega_g(\delta)
+2\|g\|_\infty\mathbb{P}(|\varepsilon Z|>\delta).
$$
先令 $\varepsilon\downarrow0$，再令 $\delta\downarrow0$ 即可。

**QED**

>[!note]
>这与[[Approximation of bad functions by good functions#Regularization|磨光与近似恒等核]]的思想相同。这里使用的是高斯核；它不具有紧支撑，因此 $g*\phi_\varepsilon$ 一般也没有紧支撑。

>[!lemma] 高斯平滑后的 Fourier 配对公式
>统一采用下面的 Fourier 变换约定：
>$$
>\widehat g(t)=\int_{\mathbb{R}}e^{itx}g(x)\,dx,
>\qquad f_\xi(t)=\mathbb{E}e^{it\xi}.
>$$
>对任意 $g\in C_c(\mathbb{R})$、$\varepsilon>0$，
>$$
>\mathbb{E}[(g*\phi_\varepsilon)(\xi)]
>=\frac1{2\pi}\int_{\mathbb{R}}
>e^{-\varepsilon^2t^2/2}\widehat g(t)f_\xi(-t)\,dt.
>$$
>由于变换使用 $e^{itx}$，配对中出现的是 $f_\xi(-t)$，前面的常数为 $1/(2\pi)$。

^gaussian-fourier-pairing

**Proof**

先计算高斯的特征函数。令
$$
H(t)=\int_{\mathbb{R}}e^{itx}\varphi(x)\,dx.
$$
由 $\int|x|\varphi(x)\,dx<\infty$，可以在积分号下求导。再用 $\varphi'(x)=-x\varphi(x)$ 分部积分，
$$
H'(t)=i\int x e^{itx}\varphi(x)\,dx
=-i\int e^{itx}\varphi'(x)\,dx
=-tH(t).
$$
边界项为 $0$，且 $H(0)=1$，所以 $H(t)=e^{-t^2/2}$。换元得到
$$
\frac1{2\pi}\int_{\mathbb{R}}
e^{-\varepsilon^2t^2/2}e^{itu}\,dt
=\phi_\varepsilon(u).
$$

记 $\mu=\mathcal{L}(\xi)$。展开右侧的 $\widehat g$ 和 $f_\xi(-t)$：
$$
\begin{aligned}
&\frac1{2\pi}\int e^{-\varepsilon^2t^2/2}
\left(\int e^{ity}g(y)\,dy\right)
\left(\int e^{-itx}\,\mu(dx)\right)dt\\
&\qquad=\int\int g(y)
\left[\frac1{2\pi}\int
e^{-\varepsilon^2t^2/2}e^{it(y-x)}\,dt\right]dy\,\mu(dx)\\
&\qquad=\int\int g(y)\phi_\varepsilon(y-x)\,dy\,\mu(dx)\\
&\qquad=\mathbb{E}[(g*\phi_\varepsilon)(\xi)].
\end{aligned}
$$
其中交换积分次序由[[Fubini定理及其应用|Fubini 定理]]保证，因为三重积分的绝对值积分不超过
$$
\frac{\|g\|_1}{2\pi}
\int_{\mathbb{R}}e^{-\varepsilon^2t^2/2}\,dt<\infty.
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

正向显然。反向，若两特征函数处处相等，由上面的 Fourier 配对公式，对任意 $g\in C_c(\mathbb{R})$，
$$
\mathbb{E}[(g*\phi_\varepsilon)(\xi)]
=\mathbb{E}[(g*\phi_\varepsilon)(\eta)].
$$
于是
$$
|\mathbb{E}g(\xi)-\mathbb{E}g(\eta)|
\le2\|g*\phi_\varepsilon-g\|_\infty\longrightarrow0.
$$
所以二者对所有 $C_c$ 测试函数的期望相等。将[[#^compact-tests|紧支撑测试函数引理]]用于常值序列 $\mu_n=\mathcal{L}(\xi)$ 和 $\mu=\mathcal{L}(\eta)$，推广到所有 $C_b$ 测试函数，再由[[#^bounded-continuous-determine-law|有界连续函数确定分布]]得到 $\xi\stackrel d=\eta$。

**QED**

>[!def] 依分布收敛
>设 $\xi_n,\xi$ 的分布函数分别为 $F_n,F$。若对 $F$ 的每个连续点 $x$，
>$$
>F_n(x)\longrightarrow F(x),
>$$
>则称 $\xi_n$ 依分布收敛到 $\xi$（convergence in distribution），记为
>$$
>\xi_n\xrightarrow{d}\xi
>\qquad\text{或}\qquad \xi_n\Rightarrow\xi.
>$$
>此定义只涉及各自的分布，不要求这些随机变量原本定义在同一个概率空间上。

^convergence-in-distribution

>[!note] 为什么只要求在 $F$ 的连续点收敛
>例如 $\xi_n=1/n$，$\xi=0$。虽然 $\xi_n\to\xi$，但
>$$
>F_n(0)=0,\qquad F(0)=1.
>$$
>$0$ 恰好是 $F$ 的跳跃点。分布函数连续点的条件对应
>$$
>\mathbb{P}(\xi=x)=F(x)-F(x-)=0,
>$$
>并不要求 $F(x)=0$。

>[!def] 弱收敛与模糊收敛
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
>若只用 $C_c(\mathbb{R})$ 中的函数检验，称为模糊收敛（vague convergence），记为 $\mu_n\xrightarrow{v}\mu$。这个定义也适用于局部有限的 Borel 测度。

^weak-and-vague-convergence

>[!note]
>在 $\mathbb{R}$ 上，概率测度弱收敛与相应随机变量依分布收敛等价，下面证明。因此二者通常都记为 $\Rightarrow$。
>
>由[[#^compact-tests|紧支撑测试函数引理]]，如果模糊极限 $\mu$ 仍是概率测度，则模糊收敛也推出弱收敛。区别在于模糊收敛允许质量跑到无穷远：例如 $\delta_n\xrightarrow{v}0$，因为对每个 $g\in C_c$，$g(n)$ 最终为 $0$；但 $\delta_n$ 不可能弱收敛到零测度，取 $g\equiv1$ 即知。
>
>弱收敛定义中的“连续”不能省略。比如上面的 $\delta_{1/n}\Rightarrow\delta_0$，用有界但不连续的 $g=\mathbb{1}_{\{0\}}$ 检验就不收敛。

>[!thm] Baby Skorokhod：实数上的表示定理
>若 $\xi_n\xrightarrow{d}\xi$，则可以在一个新的概率空间上构造 $\eta_n,\eta$，使得
>$$
>\eta_n\stackrel d=\xi_n,\qquad
>\eta\stackrel d=\xi,\qquad
>\eta_n\xrightarrow{a.s.}\eta.
>$$
>这是通过[[概率耦合方法|耦合]]实现的 Skorokhod 表示定理，不涉及用 Brownian motion 的停时表示随机变量。

^skorokhod-representation

**Proof**

取概率空间
$$
(\Omega,\mathcal{F},\mathbb{P})
=((0,1),\mathcal{B}((0,1)),du).
$$
对分布函数 $F$，定义广义逆（分位数函数）
$$
Q(u)=F^{-1}(u)
:=\inf\{y:F(y)\ge u\}
=\sup\{y:F(y)<u\},\qquad0<u<1.
$$
同理定义 $Q_n=F_n^{-1}$，并令
$$
\eta_n(u)=Q_n(u),\qquad\eta(u)=Q(u).
$$
由分布函数的单调性、右连续性及两端极限，广义逆为有限实数，且
$$
Q(u)\le y\quad\Longleftrightarrow\quad u\le F(y).
$$
因此 $Q$ 可测，并且
$$
\mathbb{P}(\eta\le y)
=\int_0^1\mathbb{1}_{\{u\le F(y)\}}\,du
=F(y).
$$
所以 $\eta\stackrel d=\xi$。同理，$\eta_n\stackrel d=\xi_n$。这里均匀分布的是坐标 $u$，经过 $Q$ 变换后的 $\eta$ 具有分布函数 $F$；这也是[[随机变量与分布函数|利用分布函数广义逆构造随机变量]]的方法。

下面证明几乎处处收敛。$Q$ 单调，所以在 $(0,1)$ 中至多有可数个不连续点。令
$$
\Omega_0=\{u\in(0,1):Q\text{ 在 }u\text{ 连续}\}.
$$
则 $\mathbb{P}(\Omega_0)=1$。

固定 $u\in\Omega_0$，记 $q=Q(u)$。给定 $\varepsilon>0$，由于 $F$ 的不连续点至多可数，可以选取 $F$ 的两个连续点 $y,z$，使
$$
q-\varepsilon<y<q<z<q+\varepsilon.
$$
由 $y<Q(u)$，有 $F(y)<u$。另一方面，因为 $Q$ 在 $u$ 连续，可以选取 $v>u$ 足够接近 $u$，使 $Q(v)<z$，于是
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
y<Q_n(u)\le z.
$$
所以 $|Q_n(u)-Q(u)|<\varepsilon$，从而 $\eta_n(u)\to\eta(u)$。这对所有 $u\in\Omega_0$ 成立，即得到几乎处处收敛。

**QED**

>[!note]
>这里需要排除的是分位数函数 $Q=F^{-1}$ 在 $u\in(0,1)$ 上的不连续点。证明中另外选取的是分布函数 $F$ 在实轴上的连续点 $y,z$，这两种连续点作用不同。
>
>新构造只保留 $\eta_n$ 与 $\xi_n$ 各自的边缘分布，并不保留原来整列随机变量的联合分布。因此不能反过来说原来的 $\xi_n$ 已经几乎处处收敛。

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

“$\Leftarrow$”：固定 $F$ 的连续点 $x$，按照手稿用两条斜线夹住示性函数。对 $\beta\ge1$，令
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

>[!thm] Portmanteau 定理
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
>
>第 4 条中的集合称为极限分布的连续集；第 3 条中的闭集不要求有界。

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
于是 $F_n(x)\to F(x)$。

**QED**

>[!note] 与依概率收敛的关系
>在同一个概率空间上，
>$$
>\xi_n\xrightarrow{a.s.}\xi
>\ \Longrightarrow\
>\xi_n\xrightarrow{\mathbb{P}}\xi
>\ \Longrightarrow\
>\xi_n\xrightarrow{d}\xi.
>$$
>最后一步也可以直接由
>$$
>F(x-\varepsilon)-\mathbb{P}(|\xi_n-\xi|>\varepsilon)
>\le F_n(x)
>\le F(x+\varepsilon)+\mathbb{P}(|\xi_n-\xi|>\varepsilon)
>$$
>证明：先令 $n\to\infty$，再在 $F$ 的连续点令 $\varepsilon\downarrow0$。
>
>反向一般不成立。例如 $\xi$ 等概率取 $\pm1$，令 $\xi_n=-\xi$，则 $\xi_n\stackrel d=\xi$，但 $\mathbb{P}(|\xi_n-\xi|>1)=1$。
>
>若极限为常数 $c$，则有
>$$
>\xi_n\xrightarrow{d}c
>\quad\Longleftrightarrow\quad
>\xi_n\xrightarrow{\mathbb{P}}c.
>$$
>由依分布收敛推出依概率收敛时，在 Portmanteau 定理中取闭集 $K=\{x:|x-c|\ge\varepsilon\}$ 即可。这也说明[[弱大数定律（WLLN）]]中的常数极限可以用依分布收敛刻画。

>[!thm] Lévy 连续性定理：已知候选极限的形式
>设 $\xi_n,\xi$ 为实值随机变量，则
>$$
>\xi_n\xrightarrow{d}\xi
>\quad\Longleftrightarrow\quad
>f_{\xi_n}(t)\longrightarrow f_\xi(t),
>\qquad\forall t\in\mathbb{R}.
>$$

^levy-continuity

**Proof**

“$\Rightarrow$”：对每个固定的 $t$，$\cos(tx)$、$\sin(tx)$ 都属于 $C_b(\mathbb{R})$，由弱收敛的测试函数刻画即得结论。

“$\Leftarrow$”：固定 $g\in C_c(\mathbb{R})$、$\varepsilon>0$。由[[#^gaussian-fourier-pairing|Fourier 配对公式]]，
$$
\mathbb{E}[(g*\phi_\varepsilon)(\xi_n)]
=\frac1{2\pi}\int
e^{-\varepsilon^2t^2/2}\widehat g(t)f_{\xi_n}(-t)\,dt.
$$
被积函数逐点收敛，且
$$
\left|e^{-\varepsilon^2t^2/2}\widehat g(t)f_{\xi_n}(-t)\right|
\le e^{-\varepsilon^2t^2/2}\|g\|_1,
$$
右侧可积，所以由 DCT，
$$
\mathbb{E}[(g*\phi_\varepsilon)(\xi_n)]
\longrightarrow\mathbb{E}[(g*\phi_\varepsilon)(\xi)].
$$
再用
$$
\begin{aligned}
|\mathbb{E}g(\xi_n)-\mathbb{E}g(\xi)|
&\le2\|g*\phi_\varepsilon-g\|_\infty\\
&\quad+
\left|\mathbb{E}[(g*\phi_\varepsilon)(\xi_n)]
-\mathbb{E}[(g*\phi_\varepsilon)(\xi)]\right|.
\end{aligned}
$$
先令 $n\to\infty$，再令 $\varepsilon\downarrow0$，得到所有 $C_c$ 测试函数的期望收敛。由[[#^compact-tests|截断推广]]得到所有 $C_b$ 测试函数的期望收敛，即弱收敛，也就是依分布收敛。

**QED**

>[!note] 一般形式与 $0$ 点连续性
>更一般地，若特征函数 $f_{\xi_n}(t)$ 逐点趋于某个函数 $f(t)$，且 $f$ 在 $0$ 处连续，则 $f$ 必为某个概率分布的特征函数，并且相应分布弱收敛到该分布。
>
>上面的证明预先知道极限是 $f_\xi$。一般形式还需要证明极限分布存在，可以先证明分布族[[The continuous space, weak convergence, and Wiener measure#Tightness|紧]]，再提取弱收敛子列并用特征函数唯一性识别极限，见 Durrett Theorem 3.3.17、李立颖讲义 Theorem 5.13。
>
>$0$ 点连续性不能去掉。例如 $\xi_n\sim N(0,n)$ 时，
>$$
>f_{\xi_n}(t)=e^{-nt^2/2}\longrightarrow\mathbb{1}_{\{0\}}(t).
>$$
>这个极限在 $0$ 不连续，不是概率分布的特征函数；这列分布的质量不断向远处扩散。

>[!thm] i.i.d. 中心极限定理（补充）
>设 $X_1,X_2,\cdots$ 为 i.i.d.，$\mathbb{E}X_1=\mu$，$0<\operatorname{Var}(X_1)=\sigma^2<\infty$。则
>$$
>\frac{S_n-n\mu}{\sigma\sqrt n}\xrightarrow{d}N(0,1),
>\qquad S_n=\sum_{i=1}^nX_i.
>$$

^iid-clt

**Proof**

令
$$
Y_i=\frac{X_i-\mu}{\sigma},
\qquad\mathbb{E}Y_i=0,\quad\mathbb{E}Y_i^2=1,
$$
并记 $f=f_{Y_1}$。由二阶矩有限，在积分号下求导得到
$$
f'(t)=\mathbb{E}(iY_1)e^{itY_1},
\qquad
f''(t)=-\mathbb{E}Y_1^2e^{itY_1}.
$$
具体地，用 $|e^{ihy}-1|\le|hy|$ 控制第一次差商，第二次差商由 $Y_1^2$ 控制，再用 DCT。$f''$ 的连续性也由 DCT 得到，因此
$$
f(0)=1,\qquad f'(0)=0,\qquad f''(0)=-1,
$$
并有 Taylor 展开
$$
f(u)=1-\frac{u^2}{2}+o(u^2),\qquad u\to0.
$$
注意零均值对应的是 $f'(0)=i\mathbb{E}Y_1=0$。

由[[独立性]]，
$$
f_{(Y_1+\cdots+Y_n)/\sqrt n}(t)
=\left[f\left(\frac t{\sqrt n}\right)\right]^n.
$$
对每个固定的 $t$，令
$$
z_n=f(t/\sqrt n)-1
=-\frac{t^2}{2n}+o(n^{-1}).
$$
因为 $z_n\to0$，可以使用 $1$ 附近满足 $\log1=0$ 的复对数分支。由
$$
\log(1+z)=z+O(|z|^2),
$$
得到
$$
n\log f(t/\sqrt n)
=nz_n+O(n|z_n|^2)
\longrightarrow-\frac{t^2}{2}.
$$
所以
$$
\left[f\left(\frac t{\sqrt n}\right)\right]^n
\longrightarrow e^{-t^2/2}.
$$
右侧是标准正态的特征函数，应用 Lévy 连续性定理即得结论。这里只要求二阶矩有限，不需要三阶矩或密度。

**QED**

>[!note] 二项分布形式
>若 $B_n\sim\operatorname{Bin}(n,p)$，其中 $0<p<1$，令 $q=1-p$，将 $B_n$ 写成 $n$ 个独立 Bernoulli 变量之和，得到
>$$
>\frac{B_n-np}{\sqrt{npq}}\xrightarrow{d}N(0,1).
>$$
>即对固定 $a<b$，
>$$
>\mathbb{P}\left(a\le\frac{B_n-np}{\sqrt{npq}}\le b\right)
>\longrightarrow\Phi(b)-\Phi(a).
>$$
>这就是一般的 De Moivre–Laplace 形式；对称随机游走对应 $p=1/2$ 及 $S_n=2B_n-n$。

>[!note] 从一个随机变量的 CLT 到路径的弱收敛
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
>进一步的整理见[[The continuous space, weak convergence, and Wiener measure#The Invariance Principle and the Wiener Measure|Donsker 不变原理与 Wiener 测度]]。

>[!note] 几种证明方法
>本节的两条路线是：
>
>1. 精确概率公式 $\to$ Stirling 公式 $\to$ 局部估计 $\to$ Riemann 和，适合简单随机游走等可显式计算的模型。
>2. 独立性 $\to$ 特征函数的乘积 $\to$ 原点附近的 Taylor 展开 $\to$ Lévy 连续性定理，得到一般 i.i.d. CLT。
>
>后续还可以考虑 Lindeberg 替换法、Stein 方法，以及在矩足以确定分布时使用矩方法；Stein 方法也可处理某些存在依赖的模型。Stieltjes 变换是研究随机矩阵谱分布的另一种变换工具。若要给出正态近似的误差界，则进入 Berry–Esseen 型结果，这比仅证明收敛需要更多条件。

>[!note] 参考
>主体按 2026.11.10 手稿（6 页）整理，补全局部估计到区间极限、截断推广、分位数耦合及特征函数方法中的细节。
>
>- Durrett, *Probability: Theory and Examples*, 5th ed.：§3.1（印刷页 113–115），Theorems 3.2.8–3.2.11（印刷页 118–121），§3.3，尤其 Theorem 3.3.17。
>- 李立颖，*Advanced Probability* 讲义：Theorem 5.7（pp. 55–57），Theorem 5.13，Propositions 5.19、5.21 与 Theorem 5.22（pp. 62–64）。一般 i.i.d. CLT 的证明作为本节特征函数方法的补充。
