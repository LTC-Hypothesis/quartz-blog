以下$\mathbb F=\mathbb R$或$\mathbb C$。

# 代数与Banach代数

>[!def] 代数
>设$X$为$\mathbb F$上的线性空间。若$X$上定义了乘法$(x,y)\mapsto xy$，满足
>
>1. 结合律：$(xy)z=x(yz)$
>2. 分配律：$(x+y)z=xz+yz$，$x(y+z)=xy+xz$
>3. 与数乘相容：$\lambda(xy)=(\lambda x)y=x(\lambda y)$
>
>其中$x,y,z\in X,\lambda\in\mathbb F$，则称$X$为$\mathbb F$上的代数。若还满足$xy=yx$，则称$X$为交换代数。

>[!def] 赋范代数与Banach代数
>设$X$为代数。若$X$上有范数$\|\cdot\|$使其成为赋范线性空间，并且
>$$
>\|xy\|\le\|x\|\|y\|,\quad\forall x,y\in X
>$$
>则称$X$为赋范代数。若$X$在此范数下完备，则称$X$为Banach代数。
^b112501

>[!def] 单位元
>若存在$e\in X$使得
>$$
>ex=xe=x,\quad\forall x\in X
>$$
>则称$e$为$X$的单位元，也记为$1$，并称$X$为含幺代数。

单位元唯一。事实上，若$e,e'$都是单位元，则$e=ee'=e'$。以下讨论含幺代数时均假设$e\ne0$。

>[!proposition] 乘法的连续性
>若$x_n\to x,y_n\to y$于赋范代数$X$，则$x_ny_n\to xy$。

**Proof**

因为$x_n\to x$，$\{\|x_n\|\}$有界，且
$$
\begin{aligned}
\|x_ny_n-xy\|
&=\|x_n(y_n-y)+(x_n-x)y\|\\
&\le\|x_n\|\|y_n-y\|+\|x_n-x\|\|y\|\to0
\end{aligned}
$$

**QED**

>[!example] Banach代数的例子
>
>1. $\mathbb R,\mathbb C$在通常的乘法与绝对值下为含幺交换Banach代数。
>2. $C[0,1]$在逐点乘法及上确界范数下为含幺交换Banach代数，单位元为常值函数$1$。
>3. 若$E$为非零Banach空间，则$\mathcal B(E)$在算子复合与算子范数下为含幺Banach代数，单位元为恒等算子$I$。
>4. 矩阵代数$M_n(\mathbb F)$可看作$\mathcal B(\mathbb F^n)$，赋予相应的算子范数后成为Banach代数。当$n\ge2$时，一般不交换。

对$C[0,1]$中的$f,g$，
$$
\|fg\|_\infty=\max_{t\in[0,1]}|f(t)g(t)|
\le\max_{t\in[0,1]}|f(t)|\max_{t\in[0,1]}|g(t)|
=\|f\|_\infty\|g\|_\infty
$$
对$T,S\in\mathcal B(E)$，$\|TS\|\le\|T\|\|S\|$；又$E$完备，所以$\mathcal B(E)$完备。

>[!example] 紧算子代数
>设$E$为无限维Banach空间，记$\mathcal B_0(E)$为$E$上的紧算子全体。则$\mathcal B_0(E)$在算子复合与算子范数下为无单位元的Banach代数。

**Proof**

紧算子的范数极限仍紧，且紧算子与有界算子的复合仍紧，参见[[紧算子]]。因此$\mathcal B_0(E)$是$\mathcal B(E)$的闭线性子空间，并对乘法封闭，所以是Banach代数。

若$U\in\mathcal B_0(E)$是其中的单位元，取$u\in E$和$f\in E^*$使得$f(u)=1$。这样的$f$可由[[Hahn-Banach定理#^h71001|Hahn-Banach定理的推论]]取得。对任意$v\in E$，定义秩至多为$1$的算子
$$
T_v(y)=f(y)v
$$
则$T_v$紧，由$UT_v=T_v$得到$Uv=UT_vu=T_vu=v$。因此$U=I$。但无限维空间上的恒等算子不紧，矛盾。

**QED**

# 单位元的规范化与添加

若$e$为赋范代数$X$的单位元，则
$$
\|e\|=\|e^2\|\le\|e\|^2
$$
因为$e\ne0$，得到$\|e\|\ge1$，但未必有$\|e\|=1$。

>[!example] 单位元的范数可以大于$1$
>在对角矩阵代数
>$$
>X=\left\{\begin{pmatrix}a&0\\0&b\end{pmatrix}:a,b\in\mathbb C\right\}
>$$
>上定义$\|\text{diag}(a,b)\|=|a|+|b|$，则$X$为Banach代数，而$\|I\|=2$。

若直接定义$\|x\|'=\|x\|/2$，虽然$\|I\|'=1$，但取$p=\text{diag}(1,0)$，有
$$
\|p^2\|'=\frac12>\frac14=\|p\|'\|p\|'
$$
因此直接将范数除以$\|e\|$未必保持乘法不等式。

>[!thm] 含幺Banach代数的等价范数
>设$X$为非零含幺Banach代数，单位元为$e$。则存在与原范数等价的范数$\|\cdot\|_1$，使得
>$$
>\|e\|_1=1,\quad\|xy\|_1\le\|x\|_1\|y\|_1
>$$
>并且$X$在新范数下仍为Banach代数。
^b112502

**Proof**

对每个$x\in X$，定义左乘算子
$$
L_x:X\to X,\quad L_x(y)=xy
$$
则$L_x$线性，且$\|L_xy\|=\|xy\|\le\|x\|\|y\|$，所以$L_x\in\mathcal B(X)$并且$\|L_x\|\le\|x\|$。又
$$
L_{\alpha x+\beta y}=\alpha L_x+\beta L_y,\quad
L_{xy}=L_xL_y,\quad L_e=I
$$
因此$L:x\mapsto L_x$为线性保乘法映射。若$L_x=0$，则$x=L_xe=0$，所以$L$单射。

定义
$$
\|x\|_1=\|L_x\|_{\mathcal B(X)}
$$
由$L$线性且单射，$\|\cdot\|_1$为范数。因为
$$
\|x\|_1\le\|x\|,\quad
\|x\|=\|L_xe\|\le\|L_x\|\|e\|=\|e\|\|x\|_1
$$
两种范数[[商空间#^q62701|等价]]，故新范数下仍完备。最后，
$$
\|e\|_1=\|I\|=1,\quad
\|xy\|_1=\|L_xL_y\|\le\|L_x\|\|L_y\|=\|x\|_1\|y\|_1
$$
得到结论。

同时，$L(X)$是$\mathcal B(X)$的闭子代数。事实上，若$L_{x_n}\to T$于算子范数，则$x_n=L_{x_n}e\to Te$，于是$L_{x_n}\to L_{Te}$，从而$T=L_{Te}\in L(X)$。

**QED**

>[!thm] 添加单位元
>设$X$为无单位元的Banach代数。令$\widetilde X=X\times\mathbb F$，加法和数乘按坐标定义，乘法和范数定义为
>$$
>(x,\lambda)(y,\mu)=(xy+\lambda y+\mu x,\lambda\mu)
>$$
>$$
>\|(x,\lambda)\|=\|x\|+|\lambda|
>$$
>则$\widetilde X$为含幺Banach代数，单位元为$(0,1)$，且其范数为$1$。映射$x\mapsto(x,0)$保持线性运算、乘法和范数，并且
>$$
>\dim(\widetilde X/X)=1
>$$
^b112503

**Proof**

由$X$中乘法的结合律和分配律，直接展开可验证$\widetilde X$上的乘法满足代数的各条公理。又
$$
(0,1)(x,\lambda)=(x,\lambda)=(x,\lambda)(0,1)
$$
所以$(0,1)$为单位元。

对$(x,\lambda),(y,\mu)\in\widetilde X$，
$$
\begin{aligned}
\|(x,\lambda)(y,\mu)\|
&=\|xy+\lambda y+\mu x\|+|\lambda\mu|\\
&\le\|x\|\|y\|+|\lambda|\|y\|+|\mu|\|x\|+|\lambda||\mu|\\
&=(\|x\|+|\lambda|)(\|y\|+|\mu|)
\end{aligned}
$$
因此乘法不等式成立。$X$和$\mathbb F$均完备，故乘积空间在上述范数下也完备。

将$X$与$X\times\{0\}$对应，则这个对应保持范数与代数运算。每个$(x,\lambda)$都可唯一写成
$$
(x,\lambda)=(x,0)+\lambda(0,1)
$$
所以$\widetilde X/X$为一维线性空间。

**QED**

# 可逆元

以下$X$均为非零含幺Banach代数，单位元记为$1$，并取$\|1\|=1$。

>[!def] 可逆元
>设$x\in X$。若存在$y\in X$使得$yx=1$，称$y$为$x$的左逆；若存在$z\in X$使得$xz=1$，称$z$为$x$的右逆。
>
>若存在$y\in X$使得$xy=yx=1$，则称$x$可逆，$y$称为$x$的逆元，记为$x^{-1}$。记
>$$
>G(X)=\{x\in X:x\text{可逆}\}
>$$

若$x$同时有左逆$y$和右逆$z$，则
$$
y=y(xz)=(yx)z=z
$$
所以$x$可逆，且逆元唯一。

>[!proposition] 可逆元的乘积
>若$x,y\in G(X)$，则$xy\in G(X)$，且
>$$
>(xy)^{-1}=y^{-1}x^{-1}
>$$
>对任意可交换的$x,y\in X$，有
>$$
>xy\in G(X)\Longleftrightarrow x,y\in G(X)
>$$
^b112504

**Proof**

若$x,y$可逆，则
$$
(xy)(y^{-1}x^{-1})=1=(y^{-1}x^{-1})(xy)
$$
得到第一个结论。

反过来，设$xy=yx$且$xy$可逆，记$c=(xy)^{-1}$。因为
$$
(cy)x=c(yx)=c(xy)=1,\quad x(yc)=(xy)c=1
$$
$x$同时有左逆和右逆，故$x$可逆。同理$y$可逆。

**QED**

可逆元之和未必可逆，例如$1,-1$均可逆，但$1+(-1)=0$不可逆。

>[!thm] Neumann级数
>若$x\in X$且$\|x\|<1$，则$1-x$可逆，并且
>$$
>(1-x)^{-1}=\sum_{n=0}^{\infty}x^n,\quad
>\|(1-x)^{-1}\|\le\frac1{1-\|x\|}
>$$
>其中$x^0=1$，级数在范数下收敛。
^b112505

**Proof**

由乘法不等式，
$$
\sum_{n=0}^{\infty}\|x^n\|
\le\sum_{n=0}^{\infty}\|x\|^n
=\frac1{1-\|x\|}<\infty
$$
因为$X$完备，级数$\sum_{n=0}^{\infty}x^n$收敛。记$s_N=\sum_{n=0}^Nx^n$，则
$$
(1-x)s_N=s_N(1-x)=1-x^{N+1}
$$
令$N\to\infty$，由$\|x^{N+1}\|\le\|x\|^{N+1}\to0$及乘法的连续性，得到
$$
(1-x)\sum_{n=0}^{\infty}x^n
=\left(\sum_{n=0}^{\infty}x^n\right)(1-x)=1
$$
故逆元为上述级数，范数估计由三角不等式得到。

**QED**

将$x$换成$-x$，同样有
$$
(1+x)^{-1}=\sum_{n=0}^{\infty}(-1)^nx^n,\quad\|x\|<1
$$
条件$\|x\|<1$不能改为$\|x\|\le1$，因为$x=1$时$1-x=0$不可逆。

>[!thm] 可逆元集的开性与求逆的连续性
>$G(X)$是$X$中的开集，映射
>$$
>G(X)\to G(X),\quad x\mapsto x^{-1}
>$$
>连续。
^b112506

**Proof**

固定$x_0\in G(X)$。若
$$
\|x-x_0\|<\frac1{\|x_0^{-1}\|}
$$
则$\|x_0^{-1}(x-x_0)\|<1$。由Neumann级数，
$$
x=x_0\bigl(1+x_0^{-1}(x-x_0)\bigr)
$$
为两个可逆元的乘积，所以$x$可逆。因此
$$
B\left(x_0,\frac1{\|x_0^{-1}\|}\right)\subseteq G(X)
$$
说明$G(X)$开。

进一步，若$\|x-x_0\|<1/(2\|x_0^{-1}\|)$，则
$$
\begin{aligned}
\|x^{-1}\|
&=\left\|\bigl(1+x_0^{-1}(x-x_0)\bigr)^{-1}x_0^{-1}\right\|\\
&\le\frac{\|x_0^{-1}\|}{1-\|x_0^{-1}(x-x_0)\|}
\le2\|x_0^{-1}\|
\end{aligned}
$$
又
$$
x^{-1}-x_0^{-1}=x_0^{-1}(x_0-x)x^{-1}
$$
从而
$$
\|x^{-1}-x_0^{-1}\|
\le2\|x_0^{-1}\|^2\|x-x_0\|\to0
$$
故求逆映射在$x_0$处连续。

**QED**

# 理想与商代数

>[!def] 子代数与理想
>设$M$为$X$的线性子空间。
>
>1. 若$x,y\in M$时总有$xy\in M$，则称$M$为$X$的子代数。
>2. 若对任意$x\in X$都有$xM\subseteq M$且$Mx\subseteq M$，则称$M$为$X$的双边理想，以下简称理想。
>
>理想的定义不要求$M$闭。若$M\ne X$，称$M$为真理想。
^b112507

>[!def] 极大理想
>设$M$为$X$的真理想。若对任意理想$N$，
>$$
>M\subseteq N\subseteq X\Longrightarrow N=M\text{或}N=X
>$$
>则称$M$为极大理想。

理想一定是子代数。若理想$M$含有可逆元$x$，则$1=x^{-1}x\in M$，进而对任意$y\in X$，$y=y1\in M$，所以$M=X$。因此真理想不含任何可逆元，特别地不含$1$。

>[!example]
>
>1. 设$H$为Hilbert空间。紧算子全体$\mathcal B_0(H)$是$\mathcal B(H)$的闭双边理想，因为紧算子与有界算子的左右复合均紧。若$H$无限维，则它是真理想。
>2. 在$C[0,1]$中，
>$$
>M=\left\{f\in C[0,1]:f\left(\frac12\right)=0\right\}
>$$
>是闭真理想。

第二个例子中，$M$显然是线性子空间；若$f\in M,g\in C[0,1]$，则$(fg)(1/2)=0$，故为理想。若$f_n\in M$且$\|f_n-f\|_\infty\to0$，则
$$
\left|f\left(\frac12\right)\right|
=\left|f\left(\frac12\right)-f_n\left(\frac12\right)\right|
\le\|f-f_n\|_\infty\to0
$$
所以$f\in M$，$M$闭。又$1\notin M$，所以$M$为真理想。

>[!proposition] 真理想的闭包
>若$M$为含幺Banach代数$X$的真理想，则$\overline M$仍为真理想。
^b112508

**Proof**

$\overline M$为闭线性子空间。对$x\in X,m\in\overline M$，取$m_n\in M$使得$m_n\to m$，则
$$
xm_n\to xm,\quad m_nx\to mx
$$
因为$xm_n,m_nx\in M$，故$xm,mx\in\overline M$。所以$\overline M$为理想。

若$\overline M=X$，则存在$m\in M$使得$\|1-m\|<1$。由Neumann级数，$m=1-(1-m)$可逆，与真理想不含可逆元矛盾。因此$\overline M\ne X$。

**QED**

>[!cor] 极大理想是闭的
>若$M$为$X$的极大理想，则$M$闭。

**Proof**

$M\subseteq\overline M\subsetneq X$，且$\overline M$为理想。由极大性，$M=\overline M$。

**QED**

>[!thm] 商代数
>设$M$为Banach代数$X$的闭双边理想。在商空间$X/M$上定义
>$$
>[x][y]=[xy],\quad
>\|[x]\|=\inf_{m\in M}\|x+m\|
>$$
>则$X/M$为Banach代数。若$X$含单位元$1$、$\|1\|=1$且$M$为真理想，则$[1]$为$X/M$的单位元，并且$\|[1]\|=1$。
^b112509

**Proof**

先验证乘法与代表元的选取无关。若$m_1,m_2\in M$，则
$$
(x+m_1)(y+m_2)-xy=xm_2+m_1y+m_1m_2\in M
$$
所以$[x+m_1][y+m_2]=[xy]$，乘法良定义。结合律、分配律及与数乘的相容性均由$X$中的相应性质得到。

由[[商空间#^q62709|商空间的完备性]]，$X/M$在商范数下为Banach空间。对任意$m_1,m_2\in M$，
$$
\begin{aligned}
\|[xy]\|
&=\|[(x+m_1)(y+m_2)]\|\\
&\le\|(x+m_1)(y+m_2)\|\\
&\le\|x+m_1\|\|y+m_2\|
\end{aligned}
$$
分别对$m_1,m_2$取下确界，得到
$$
\|[x][y]\|\le\|[x]\|\|[y]\|
$$
故$X/M$为Banach代数。

若$M$为真理想，则$[1]\ne[0]$，且
$$
[1][x]=[x][1]=[x]
$$
所以$[1]$为单位元。由商范数的定义$\|[1]\|\le\|1\|=1$；另一方面，非零单位元的范数至少为$1$，故$\|[1]\|=1$。

**QED**

>[!example] 点值理想与商代数
>对$X=C[0,1]$及$M=\{f:f(1/2)=0\}$，映射
>$$
>\Phi:X/M\to\mathbb F,\quad\Phi([f])=f\left(\frac12\right)
>$$
>为保持范数与乘法的线性同构，且$M$为极大理想。

**Proof**

同一陪集中的函数在$1/2$处取值相同，故$\Phi$良定义。它保持线性运算与乘法，且
$$
f-f\left(\frac12\right)1\in M
\Longrightarrow[f]=\left[f\left(\frac12\right)1\right]
$$
因此每个陪集唯一对应一个常值函数，$\Phi$为双射。

对任意$m\in M$，
$$
\left|f\left(\frac12\right)\right|
=\left|(f+m)\left(\frac12\right)\right|
\le\|f+m\|_\infty
$$
取下确界，结合常值代表元的范数，得到
$$
\|[f]\|=\left|f\left(\frac12\right)\right|
$$

若$N$为严格包含$M$的理想，取$g\in N\setminus M$，则$g(1/2)\ne0$。又$g-g(1/2)1\in M\subseteq N$，所以$g(1/2)1\in N$，进而$1\in N$，故$N=X$。因此$M$为极大理想。

**QED**

# 谱与预解集

以下$X$为非零复含幺Banach代数，$\|1\|=1$。对$\lambda\in\mathbb C$，常将$\lambda1-x$简记为$\lambda-x$。

>[!def] 谱与预解集
>设$x\in X$，称
>$$
>\sigma(x)=\{\lambda\in\mathbb C:\lambda1-x\text{不可逆}\}
>$$
>为$x$的谱，称
>$$
>\rho(x)=\mathbb C\setminus\sigma(x)
>=\{\lambda\in\mathbb C:\lambda1-x\text{可逆}\}
>$$
>为$x$的预解集。对$\lambda\in\rho(x)$，记
>$$
>R_x(\lambda)=(\lambda1-x)^{-1}
>$$
>称为$x$的预解式。
^b112510

>[!example] 矩阵的谱
>若$A\in M_n(\mathbb C)$，则
>$$
>\sigma(A)=\{\lambda\in\mathbb C:\det(\lambda I-A)=0\}
>$$
>恰为$A$的所有特征值组成的集合。

>[!example] 连续函数的谱
>在复Banach代数$C[0,1]$中，对$f\in C[0,1]$，有
>$$
>\sigma(f)=f([0,1])
>$$

**Proof**

$g\in C[0,1]$可逆，当且仅当$g(t)\ne0$对所有$t\in[0,1]$成立。事实上，可逆时由$g(t)g^{-1}(t)=1$知$g(t)\ne0$；反过来，若$g$处处非零，则$1/g$连续，为其逆元。

因此$\lambda-f$不可逆，当且仅当存在$t\in[0,1]$使得$\lambda=f(t)$，即$\lambda\in f([0,1])$。

**QED**

>[!proposition] 谱的闭性与有界性
>对$x\in X$，$\sigma(x)$是$\mathbb C$中的闭集，并且
>$$
>\sigma(x)\subseteq\{\lambda\in\mathbb C:|\lambda|\le\|x\|\}
>$$

**Proof**

映射$\lambda\mapsto\lambda1-x$连续，而$G(X)$开，所以其原像$\rho(x)$开，$\sigma(x)$闭。这里用到[[简明拓扑学#^0f5727|连续映射的开集原像性质]]。

若$|\lambda|>\|x\|$，则$\|x/\lambda\|<1$，由Neumann级数，
$$
\lambda1-x=\lambda\left(1-\frac x\lambda\right)
$$
可逆，且
$$
R_x(\lambda)=\frac1\lambda\sum_{n=0}^{\infty}\left(\frac x\lambda\right)^n
=\sum_{n=0}^{\infty}\frac{x^n}{\lambda^{n+1}}
$$
因此$\lambda\in\rho(x)$，并且
$$
\|R_x(\lambda)\|
\le\frac1{|\lambda|}\frac1{1-\|x\|/|\lambda|}
=\frac1{|\lambda|-\|x\|}
$$
从而谱包含于上述闭圆盘。

**QED**

## Banach空间值的解析函数

>[!def] 解析函数
>设$E$为复Banach空间，$\Omega\subseteq\mathbb C$为开集，$f:\Omega\to E$。若对每个$z_0\in\Omega$，极限
>$$
>f'(z_0)=\lim_{z\to z_0}\frac{f(z)-f(z_0)}{z-z_0}
>$$
>在$E$的范数下存在，则称$f$在$\Omega$上解析。

若$\gamma:[a,b]\to\Omega$为分段光滑曲线，$f$连续，则定义
$$
\int_\gamma f(z)\,dz
=\int_a^b f(\gamma(t))\gamma'(t)\,dt
$$
右侧的积分由$E$中Riemann和的范数极限定义。由$E$完备，分段连续的被积函数可积，且
$$
\left\|\int_\gamma f(z)\,dz\right\|
\le\int_a^b\|f(\gamma(t))\||\gamma'(t)|\,dt
$$

>[!proposition] 幂级数的收敛半径
>若$a_n\in E$，则幂级数
>$$
>\sum_{n=0}^{\infty}a_n(z-z_0)^n
>$$
>的收敛半径为
>$$
>R=\frac1{\displaystyle\limsup_{n\to\infty}\|a_n\|^{1/n}}
>$$
>其中约定$1/0=\infty,1/\infty=0$。在$|z-z_0|<R$时级数绝对收敛，和函数解析；在$|z-z_0|>R$时级数发散。

这是对$\sum\|a_n\||z-z_0|^n$使用根值判别法的结果。在收敛圆内较小的闭圆盘上，级数及逐项求导后的级数均一致收敛，故可逐项求导。

>[!proposition] Cauchy公式与系数估计
>设$f:\Omega\to E$解析，$r>0$，闭圆盘$\{z:|z-z_0|\le r\}\subseteq\Omega$。则对$|z-z_0|<r$，
>$$
>f(z)=\frac1{2\pi i}\int_{|\zeta-z_0|=r}\frac{f(\zeta)}{\zeta-z}\,d\zeta
>$$
>并且
>$$
>f(z)=\sum_{n=0}^{\infty}a_n(z-z_0)^n,\quad
>a_n=\frac1{2\pi i}\int_{|\zeta-z_0|=r}\frac{f(\zeta)}{(\zeta-z_0)^{n+1}}\,d\zeta
>$$
>其中圆周取正向。若$M_r=\max_{|\zeta-z_0|=r}\|f(\zeta)\|$，则
>$$
>\|a_n\|\le\frac{M_r}{r^n}
>$$
^b112511

**Proof**

对任意$\varphi\in E^*$，$\varphi\circ f$为标量值解析函数；又有界线性泛函与上述积分可交换，因此对$\varphi\circ f$应用标量Cauchy公式，得到
$$
\varphi(f(z))
=\varphi\left(\frac1{2\pi i}\int_{|\zeta-z_0|=r}\frac{f(\zeta)}{\zeta-z}\,d\zeta\right)
$$
由[[Hahn-Banach定理#^h71002|有界线性泛函可以分离点]]，得到向量值Cauchy公式。

在圆周$|\zeta-z_0|=r$上展开
$$
\frac1{\zeta-z}
=\sum_{n=0}^{\infty}\frac{(z-z_0)^n}{(\zeta-z_0)^{n+1}}
$$
当$z$固定且$|z-z_0|<r$时，上述级数一致收敛，可以逐项积分，得到Taylor展开及系数公式。最后，
$$
\|a_n\|
\le\frac1{2\pi}\cdot2\pi r\cdot\frac{M_r}{r^{n+1}}
=\frac{M_r}{r^n}
$$

**QED**

>[!proposition] Liouville定理
>若$f:\mathbb C\to E$解析且有界，则$f$为常值函数。

**Proof**

对任意$\varphi\in E^*$，$\varphi\circ f$是有界整函数，由标量Liouville定理为常数。故对任意$z\in\mathbb C$，
$$
\varphi(f(z)-f(0))=0,\quad\forall\varphi\in E^*
$$
由Hahn-Banach定理的推论，$f(z)=f(0)$。

**QED**

## 谱的非空性

>[!proposition] 预解式的解析性
>$R_x:\rho(x)\to X$解析，并且
>$$
>R_x'(\lambda)=-R_x(\lambda)^2
>$$

**Proof**

对$\lambda,\mu\in\rho(x)$，有预解式恒等式
$$
\begin{aligned}
R_x(\lambda)-R_x(\mu)
&=R_x(\lambda)\bigl((\mu1-x)-(\lambda1-x)\bigr)R_x(\mu)\\
&=(\mu-\lambda)R_x(\lambda)R_x(\mu)
\end{aligned}
$$
固定$\mu$，由求逆映射连续，令$\lambda\to\mu$，得到
$$
\frac{R_x(\lambda)-R_x(\mu)}{\lambda-\mu}
=-R_x(\lambda)R_x(\mu)\to-R_x(\mu)^2
$$
故$R_x$解析，且导数如上。

**QED**

>[!thm] 谱是非空紧集
>设$X$为非零复含幺Banach代数，$x\in X$。则$\sigma(x)$为$\mathbb C$中的非空紧集，且
>$$
>\sigma(x)\subseteq\{\lambda\in\mathbb C:|\lambda|\le\|x\|\}
>$$
^b112512

**Proof**

已经证明$\sigma(x)$闭且有界，由$\mathbb C$中闭有界集的[[简明拓扑学#紧致性|紧致性]]，只需证明$\sigma(x)\ne\varnothing$。

反设$\sigma(x)=\varnothing$，则$R_x$在整个$\mathbb C$上解析。由
$$
\|R_x(\lambda)\|\le\frac1{|\lambda|-\|x\|},\quad|\lambda|>\|x\|
$$
知$R_x(\lambda)\to0$当$|\lambda|\to\infty$。又$R_x$在任意闭圆盘上连续且有界，所以$R_x$在整个$\mathbb C$上有界。由Liouville定理，$R_x$为常值函数，结合无穷远处趋于$0$，得到$R_x\equiv0$。

但对任意$\lambda\in\mathbb C$，
$$
(\lambda1-x)R_x(\lambda)=1\ne0
$$
矛盾。因此$\sigma(x)\ne\varnothing$。

**QED**

# 谱半径

>[!def] 谱半径
>对$x\in X$，定义
>$$
>r(x)=\sup\{|\lambda|:\lambda\in\sigma(x)\}
>$$
>称为$x$的谱半径。因为$\sigma(x)$为非空紧集，上述上确界可以取到，并且
>$$
>0\le r(x)\le\|x\|
>$$

>[!thm] 谱半径公式
>设$X$为非零复含幺Banach代数，$x\in X$，则极限$\lim_{n\to\infty}\|x^n\|^{1/n}$存在，且
>$$
>r(x)=\lim_{n\to\infty}\|x^n\|^{1/n}
>$$
^b112513

**Proof**

**Step 1：证明$r(x)\le\liminf_{n\to\infty}\|x^n\|^{1/n}$。**

先说明，若$\lambda\in\sigma(x)$，则$\lambda^n\in\sigma(x^n)$。事实上，
$$
\lambda^n1-x^n
=(\lambda1-x)\sum_{k=0}^{n-1}\lambda^{n-1-k}x^k
$$
右侧两个因子可交换。若$\lambda^n1-x^n$可逆，由[[#^b112504|可交换因子的乘积可逆的条件]]，$\lambda1-x$也可逆，与$\lambda\in\sigma(x)$矛盾。

因此对任意$n\ge1$及$\lambda\in\sigma(x)$，
$$
|\lambda|^n\le\|x^n\|
\Longrightarrow|\lambda|\le\|x^n\|^{1/n}
$$
对$\lambda$取上确界，再对$n$取下极限，得到
$$
r(x)\le\liminf_{n\to\infty}\|x^n\|^{1/n}
$$

**Step 2：证明$\limsup_{n\to\infty}\|x^n\|^{1/n}\le r(x)$。**

任取$s>r(x)$，考虑
$$
F(z)=(1-zx)^{-1}
$$
当$0<|z|\le1/s$时，$|1/z|\ge s>r(x)$，故$1/z\in\rho(x)$，且
$$
F(z)=\frac1zR_x\left(\frac1z\right)
$$
在$z=0$附近，由Neumann级数，
$$
F(z)=\sum_{n=0}^{\infty}x^nz^n,\quad |z|\|x\|<1
$$
所以$F$在包含闭圆盘$\{z:|z|\le1/s\}$的开集上解析，且它在$0$处的Taylor系数为$x^n$。

令
$$
M_s=\max_{|z|=1/s}\|(1-zx)^{-1}\|
$$
由[[#^b112511|Cauchy系数估计]]，
$$
\|x^n\|\le M_ss^n
$$
从而
$$
\limsup_{n\to\infty}\|x^n\|^{1/n}
\le\lim_{n\to\infty}M_s^{1/n}s=s
$$
由$s>r(x)$的任意性，
$$
\limsup_{n\to\infty}\|x^n\|^{1/n}\le r(x)
$$
结合两步，得到
$$
r(x)\le\liminf_{n\to\infty}\|x^n\|^{1/n}
\le\limsup_{n\to\infty}\|x^n\|^{1/n}\le r(x)
$$
故极限存在，并且等于$r(x)$。

**QED**
