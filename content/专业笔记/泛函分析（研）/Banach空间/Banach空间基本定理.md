>[!def] 开映射
>设$X,Y$为度量空间，$T:X\to Y$为映射。若对任意$X$中的开集$U$，$T(U)$都是$Y$中的开集，则称$T$为开映射。

以下$X,Y$为同一数域上的赋范线性空间，$T:X\to Y$为线性映射，$B_X(x,r),B_Y(y,r)$均表示开球。

>[!note] 连续性的球刻画
>由[[有界线性算子|线性算子的连续性与有界性]]，
>$$
>T\text{连续}\Longleftrightarrow T\text{有界}
>\Longleftrightarrow\exists A>0,\ T(B_X(0,1))\subseteq B_Y(0,A)
>$$
>从拓扑上说，连续性等价于$Y$中每个开集$V$的原像$T^{-1}(V)$在$X$中开，见[[简明拓扑学#^0f5727|连续映射的刻画]]。这里$T^{-1}(V)$表示原像，不要求$T$可逆。

>[!thm] 开映射的球刻画
>设$X,Y$为赋范线性空间，$T:X\to Y$线性，则
>$$
>T\text{为开映射}\Longleftrightarrow\exists C>0,\ B_Y(0,1)\subseteq T(B_X(0,C))
>$$
>等价地，存在$\delta>0$使得$B_Y(0,\delta)\subseteq T(B_X(0,1))$。
^o71001

**Proof**

$\Longrightarrow:$ 因为$B_X(0,1)$开，$T(B_X(0,1))$是$Y$中的开集。又$T(0)=0$，所以存在$\delta>0$，使得
$$
B_Y(0,\delta)\subseteq T(B_X(0,1))
$$
由线性，等式两侧缩放$\delta^{-1}$，得到
$$
B_Y(0,1)\subseteq T(B_X(0,\delta^{-1}))
$$
取$C=\delta^{-1}$即可。

$\Longleftarrow:$ 任取$X$中的开集$U$，只需要证明$T(U)$开。对任意$y_0\in T(U)$，取$x_0\in U$使得$Tx_0=y_0$。由$U$开，存在$\varepsilon>0$使得
$$
B_X(x_0,\varepsilon)=x_0+B_X(0,\varepsilon)\subseteq U
$$
把假设中的包含关系缩放$\varepsilon/C$，得到
$$
B_Y\left(0,\frac\varepsilon C\right)\subseteq T(B_X(0,\varepsilon))
$$
因此
$$
\begin{aligned}
B_Y\left(y_0,\frac\varepsilon C\right)
&\subseteq y_0+T(B_X(0,\varepsilon))\\
&=T(B_X(x_0,\varepsilon))\subseteq T(U)
\end{aligned}
$$
所以$y_0$是$T(U)$的内点，$T(U)$开。

**QED**

>[!thm] 开映射定理
>设$X,Y$为Banach空间，$T\in\mathcal B(X,Y)$，且$\text{range}(T)=Y$，则$T$为开映射。
>
>由球刻画，等价地，存在$C>0$使得
>$$
>B_Y(0,1)\subseteq T(B_X(0,C))
>$$
^o71002

# 开映射定理的证明

先证明两个预备结论。

>[!lemma] 去掉像集的闭包
>设$X$为Banach空间，$Y$为赋范线性空间，$T\in\mathcal B(X,Y)$。若存在$C>0$使得
>$$
>B_Y(0,1)\subseteq\overline{T(B_X(0,C))}
>$$
>则
>$$
>B_Y(0,1)\subseteq T(B_X(0,2C))
>$$
^o71701

**Proof**

任取$y\in B_Y(0,1)$。由闭包的定义，存在$x_1\in B_X(0,C)$使得
$$
\|y-Tx_1\|<\frac12
$$
把假设中的包含关系缩放$1/2$，得到
$$
B_Y\left(0,\frac12\right)\subseteq\overline{T\left(B_X\left(0,\frac C2\right)\right)}
$$
所以存在$x_2\in B_X(0,C/2)$使得
$$
\|y-Tx_1-Tx_2\|<\frac14
$$
重复这个过程，得到$\{x_n\}\subseteq X$，满足
$$
\|x_n\|<\frac C{2^{n-1}},\quad
\left\|y-T\left(\sum_{k=1}^n x_k\right)\right\|<\frac1{2^n}
$$
记$s_n=\sum_{k=1}^n x_k$。对$m>n$，
$$
\|s_m-s_n\|\le\sum_{k=n+1}^m\|x_k\|
\le\sum_{k=n+1}^{\infty}\frac C{2^{k-1}}=\frac{2C}{2^n}\to0
$$
所以$\{s_n\}$为Cauchy列。由$X$完备，存在$x\in X$使得$s_n\to x$，且
$$
\|x\|\le\sum_{k=1}^{\infty}\|x_k\|
\le\|x_1\|+\sum_{k=2}^{\infty}\frac C{2^{k-1}}<2C
$$
又$T$连续，$Tx=\lim_{n\to\infty}Ts_n=y$。因此$y\in T(B_X(0,2C))$。

**QED**

>[!def] 稠密集与稀疏集
>设$(X,d)$为度量空间，$E\subseteq X$。
>1. 若$\overline E=X$，称$E$在$X$中稠密。
>2. 若$\overline E$的内部为空，即$\overline E$不包含任何非空开球，称$E$为稀疏集，也称无处稠密集。
>

>[!thm] Baire纲定理
>非空完备度量空间不能写成可数个稀疏集的并。即若
>$$
>X=\bigcup_{n=1}^{\infty}E_n
>$$
>则至少有一个$E_n$不稀疏，也就是$\overline{E_n}$包含一个非空开球。
^o71702

**Proof**

反证。设$X=\bigcup_{n=1}^{\infty}E_n$且每个$E_n$都稀疏。记
$$
\overline B(x,r)=\{y\in X:d(x,y)\le r\}
$$
为闭球。

因为$\overline{E_1}$内部为空，$X\setminus\overline{E_1}$是非空开集，可以选取$x_1\in X$和$0<r_1<1/2$使得
$$
\overline B(x_1,r_1)\subseteq X\setminus\overline{E_1}
$$
假设已经选出$x_{n-1},r_{n-1}$。由于$\overline{E_n}$不包含非空开球，
$$
B(x_{n-1},r_{n-1})\setminus\overline{E_n}
$$
仍为非空开集，因此可以取$x_n$及$0<r_n<2^{-n}$使得
$$
\overline B(x_n,r_n)\subseteq B(x_{n-1},r_{n-1})\setminus\overline{E_n}
$$
于是得到一列嵌套的闭球，并且第$n$个闭球与$E_n$不相交。

对$m>n$，$x_m\in\overline B(x_n,r_n)$，所以
$$
d(x_m,x_n)\le r_n<2^{-n}
$$
从而$\{x_n\}$是Cauchy列。由完备性，存在$x\in X$使得$x_n\to x$。固定$n$，序列的尾项都在闭集$\overline B(x_n,r_n)$中，故
$$
x\in\bigcap_{n=1}^{\infty}\overline B(x_n,r_n)
$$
所以对所有$n$都有$x\notin E_n$，这与$X=\bigcup_{n=1}^{\infty}E_n$矛盾。

**QED**

下面证明[[#^o71002|开映射定理]]。

**Proof**

由$T$满射，
$$
Y=\bigcup_{n=1}^{\infty}T(B_X(0,n))
$$
因为$Y$完备，由Baire纲定理，存在$n_0\in\mathbb N$及$y_0\in Y,r>0$使得
$$
B_Y(y_0,r)\subseteq\overline{T(B_X(0,n_0))}
$$
取$x_0\in X$使得$Tx_0=y_0$，再取$N>\max\{n_0,\|x_0\|\}$，则
$$
B_Y(y_0,r)\subseteq\overline{T(B_X(0,N))}
$$
任取$y\in B_Y(0,1)$，有$y_0+ry\in B_Y(y_0,r)$。因此存在$\{x_k\}\subseteq B_X(0,N)$使得
$$
Tx_k\to y_0+ry
$$
于是
$$
T\left(\frac{x_k-x_0}{r}\right)\to y,\quad
\left\|\frac{x_k-x_0}{r}\right\|<\frac{2N}{r}
$$
由$y$的任意性，得到
$$
B_Y(0,1)\subseteq\overline{T\left(B_X\left(0,\frac{2N}{r}\right)\right)}
$$
应用[[#^o71701|去掉闭包的引理]]，
$$
B_Y(0,1)\subseteq T\left(B_X\left(0,\frac{4N}{r}\right)\right)
$$
由[[#^o71001|开映射的球刻画]]，$T$为开映射。

**QED**

# 开映射定理的推论与应用

>[!thm] 逆算子定理
>设$X,Y$为Banach空间，$T\in\mathcal B(X,Y)$为双射，则
>$$
>T^{-1}\in\mathcal B(Y,X)
>$$
^o71703

**Proof**

$T^{-1}$线性。由开映射定理，存在$C>0$使得
$$
B_Y(0,1)\subseteq T(B_X(0,C))
$$
任取$y\in Y$和$r>\|y\|$，因为$y/r\in B_Y(0,1)$且原像唯一，
$$
\left\|T^{-1}\left(\frac yr\right)\right\|<C
\Longrightarrow\|T^{-1}y\|<Cr
$$
令$r\downarrow\|y\|$，得到$\|T^{-1}y\|\le C\|y\|$，所以$T^{-1}$有界。

**QED**

>[!def] 乘积空间与算子的图像
>在赋范线性空间$X,Y$的乘积$X\times Y$上定义范数
>$$
>\|(x,y)\|=\|x\|_X+\|y\|_Y
>$$
>对线性映射$T:X\to Y$，定义它的图像为
>$$
>G(T)=\{(x,Tx):x\in X\}\subseteq X\times Y
>$$

由乘积范数的定义，
$$
(x_n,y_n)\to(x,y)\Longleftrightarrow x_n\to x,\quad y_n\to y
$$
若$X,Y$都完备，则$X\times Y$也完备。事实上，乘积空间中Cauchy列的两个坐标分别是$X,Y$中的Cauchy列，两个坐标各自收敛，就得到乘积空间中的收敛。

由于$T$线性，$G(T)$为线性子空间。并且$G(T)$闭等价于：
$$
x_n\to x,\quad Tx_n\to y\Longrightarrow y=Tx
$$

>[!thm] 闭图定理
>设$X,Y$为Banach空间，$T:X\to Y$为定义在整个$X$上的线性映射，则
>$$
>T\in\mathcal B(X,Y)\Longleftrightarrow G(T)\text{为}X\times Y\text{的闭子空间}
>$$
^o71704

**Proof**

$\Longrightarrow:$ 若$x_n\to x$且$Tx_n\to y$，由$T$连续，$Tx_n\to Tx$。由极限唯一性，$y=Tx$，所以$G(T)$闭。

$\Longleftarrow:$ 因为$G(T)$是Banach空间$X\times Y$的闭子空间，所以$G(T)$也是Banach空间。考虑
$$
P:G(T)\to X,\quad P(x,Tx)=x
$$
则$P$为线性双射，并且
$$
\|P(x,Tx)\|=\|x\|\le\|x\|+\|Tx\|=\|(x,Tx)\|
$$
所以$P$有界。由[[#^o71703|逆算子定理]]，$P^{-1}$有界，即存在$C>0$使得
$$
\|x\|+\|Tx\|=\|(x,Tx)\|=\|P^{-1}x\|\le C\|x\|
$$
从而$\|Tx\|\le C\|x\|$，$T$有界。

**QED**

>[!thm] Banach空间的闭子空间直和
>设$X$为Banach空间，$M,N$为$X$的闭线性子空间，且
>$$
>X=M+N,\quad M\cap N=\{0\}
>$$
>则存在$P\in\mathcal B(X)$使得
>$$
>P^2=P,\quad\text{range}(P)=M,\quad\text{Ker}(P)=\text{range}(I-P)=N
>$$
^o71705

**Proof**

由假设，每个$x\in X$可以唯一写成$x=m+n$，其中$m\in M,n\in N$。定义
$$
P:X\to X,\quad P(m+n)=m
$$
则$P$线性，并且$P^2=P,\text{range}(P)=M,\text{Ker}(P)=\text{range}(I-P)=N$。只需要证明$P$有界。

因为$M,N$为闭子空间，所以它们都是Banach空间，$M\times N$在范数$\|(m,n)\|=\|m\|+\|n\|$下也完备。定义
$$
S:M\times N\to X,\quad S(m,n)=m+n
$$
由分解的存在性和唯一性，$S$为线性双射。又
$$
\|S(m,n)\|=\|m+n\|\le\|m\|+\|n\|=\|(m,n)\|
$$
所以$S$有界。由逆算子定理，存在$C>0$使得
$$
\|m\|+\|n\|=\|S^{-1}(m+n)\|\le C\|m+n\|
$$
因此对$x=m+n$，$\|Px\|=\|m\|\le C\|x\|$，即$P$有界。

**QED**

这里称$P$为沿$N$到$M$的投影，指的是满足$P^2=P$的[[幂等算子和不变子空间|幂等算子]]，不涉及正交性。

# 一致有界原理

>[!thm] 一致有界原理
>设$X$为Banach空间，$Y$为赋范线性空间，$\{T_\alpha\}_{\alpha\in A}\subseteq\mathcal B(X,Y)$。若
>$$
>\forall x\in X,\quad\sup_{\alpha\in A}\|T_\alpha x\|<+\infty
>$$
>则
>$$
>\sup_{\alpha\in A}\|T_\alpha\|<+\infty
>$$
>即逐点有界推出算子范数一致有界。
^o71706

**Proof**

记
$$
X_n=\left\{x\in X:\sup_{\alpha\in A}\|T_\alpha x\|\le n\right\}
$$
由逐点有界，对每个$x\in X$，总能找到$n$使得$x\in X_n$，所以
$$
X=\bigcup_{n=1}^{\infty}X_n
$$
每个$X_n$都是闭集。事实上，若$\{x_k\}\subseteq X_n$且$x_k\to x$，则对每个$\alpha$，由$T_\alpha$连续，
$$
T_\alpha x_k\to T_\alpha x,\quad\|T_\alpha x_k\|\le n
\Longrightarrow\|T_\alpha x\|\le n
$$
因此$x\in X_n$。

由[[#^o71702|Baire纲定理]]，存在$N$使得$X_N$不稀疏。又$X_N$闭，所以存在$x_0\in X,r>0$使得
$$
B_X(x_0,r)\subseteq X_N
$$
对$\|x\|<1$，有$x_0+rx\in X_N$且$x_0\in X_N$，于是对任意$\alpha\in A$，
$$
\begin{aligned}
\|T_\alpha x\|
&=\frac1r\|T_\alpha(x_0+rx)-T_\alpha x_0\|\\
&\le\frac{\|T_\alpha(x_0+rx)\|+\|T_\alpha x_0\|}{r}
\le\frac{2N}{r}
\end{aligned}
$$
对$\|x\|<1$取上确界，得到$\|T_\alpha\|\le2N/r$，这个上界与$\alpha$无关。

**QED**

>[!proposition] 用有界线性泛函判定集合有界
>设$X$为赋范线性空间，$E\subseteq X$。若
>$$
>\forall f\in X^*,\quad\sup_{x\in E}|f(x)|<+\infty
>$$
>则
>$$
>\sup_{x\in E}\|x\|<+\infty
>$$
^o71707

**Proof**

对每个$x\in E$，考虑[[Hahn-Banach定理#^h71003|自然嵌入]]给出的泛函
$$
\widehat x:X^*\to\mathbb F,\quad\widehat x(f)=f(x),\quad\|\widehat x\|=\|x\|
$$
虽然$X$未必完备，但$X^*=\mathcal B(X,\mathbb F)$是Banach空间，因为标量域$\mathbb F$完备。由假设，算子族$\{\widehat x:x\in E\}$在$X^*$上逐点有界：
$$
\forall f\in X^*,\quad\sup_{x\in E}|\widehat x(f)|=\sup_{x\in E}|f(x)|<+\infty
$$
应用一致有界原理，得到
$$
\sup_{x\in E}\|x\|=\sup_{x\in E}\|\widehat x\|<+\infty
$$

**QED**

>[!proposition] 有界线性算子列的逐点极限
>设$X$为Banach空间，$Y$为赋范线性空间，$\{A_n\}\subseteq\mathcal B(X,Y)$。若对每个$x\in X$，$\lim_{n\to\infty}A_nx$在$Y$中存在，则
>$$
>A:X\to Y,\quad Ax=\lim_{n\to\infty}A_nx
>$$
>为有界线性算子，且$\sup_n\|A_n\|<+\infty$。
^o71708

**Proof**

由极限的线性，$A$线性。对每个$x\in X$，$\{A_nx\}$收敛，所以$\sup_n\|A_nx\|<+\infty$。由一致有界原理，存在$C>0$使得
$$
\|A_n\|\le C,\quad\forall n\in\mathbb N
$$
因此对任意$x\in X$，
$$
\|Ax\|\le\|Ax-A_nx\|+\|A_nx\|
\le\|Ax-A_nx\|+C\|x\|
$$
令$n\to\infty$，得到$\|Ax\|\le C\|x\|$，故$A\in\mathcal B(X,Y)$。

**QED**

>[!note] 一致收敛与强收敛
>对$A_n,A\in\mathcal B(X,Y)$，称$\|A_n-A\|\to0$为一致收敛，即算子范数收敛；称
>$$
>\forall x\in X,\quad\|A_nx-Ax\|\to0
>$$
>为强收敛。由
>$$
>\|A_nx-Ax\|\le\|A_n-A\|\|x\|
>$$
>可知一致收敛推出强收敛，反过来一般不成立。

>[!example] 强收敛不推出一致收敛
>设$H$为具有可数无限规范正交基$\{e_i\}_{i=1}^{\infty}$的Hilbert空间，令
>$$
>P_nh=\sum_{i=n+1}^{\infty}\langle h,e_i\rangle e_i
>$$
>即$P_n$为到闭子空间$\overline{\text{span}}\{e_{n+1},e_{n+2},\cdots\}$上的正交投影。
>
>由[[Hilbert空间上的基|Parseval等式]]，对每个$h\in H$，
>$$
>\|P_nh\|^2=\sum_{i=n+1}^{\infty}|\langle h,e_i\rangle|^2\to0
>$$
>所以$P_n$强收敛到$0$。但$\|P_n\|\le1$且$P_ne_{n+1}=e_{n+1}$，故
>$$
>\|P_n\|=1,\quad\forall n\in\mathbb N
>$$
>因此$P_n$不在算子范数下收敛到$0$。
