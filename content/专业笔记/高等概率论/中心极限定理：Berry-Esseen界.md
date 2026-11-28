
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
这需要注意，傅里叶变换（特征函数变换）可以把分布的卷积的特征函数变成分布的特征函数的乘积，另外由于Pólya 分布的特征函数具有紧支撑，因此积分可以限制在 $[-L,L]$ 上。令 $a\to-\infty$。$\Delta_L(a)\to0$，而 $q_L\in L^1$，由[[Durrett习题1.4#^11afdb|Riemann–Lebesgue 引理]]，含 $e^{-ita}$ 的积分趋于 $0$。所以
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

先准备三个不等式估计。由 Taylor 余项界，
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
代回分布函数差的不等式，并把积分区间扩大为 $\mathbb{R}$，得到
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

**QED**