以下$\mathbb F=\mathbb R$或$\mathbb C$，内积对第一个变量线性，对第二个变量共轭线性。

# 内积与范数

>[!def] 内积空间
>设$X$为$\mathbb F$上的线性空间。若映射$\langle\cdot,\cdot\rangle:X\times X\to\mathbb F$满足
>
>1. 正定性：$\langle x,x\rangle\ge0$，且$\langle x,x\rangle=0\Longleftrightarrow x=0$
>2. 共轭对称性：$\langle x,y\rangle=\overline{\langle y,x\rangle}$
>3. 线性性：$\langle\alpha x+\beta y,z\rangle=\alpha\langle x,z\rangle+\beta\langle y,z\rangle$
>
>其中$x,y,z\in X,\alpha,\beta\in\mathbb F$，则称$\langle\cdot,\cdot\rangle$为$X$上的内积，$X$为内积空间。
^i112101

由共轭对称性和第一个变量的线性性，得到
$$
\langle x,\alpha y+\beta z\rangle
=\overline\alpha\langle x,y\rangle+\overline\beta\langle x,z\rangle
$$
特别地，$\langle x,0\rangle=\langle0,x\rangle=0$。在实数域上，共轭线性就是线性。

>[!def] 半内积
>若只要求$\langle x,x\rangle\ge0$，不要求$\langle x,x\rangle=0$推出$x=0$，其余条件不变，则称$\langle\cdot,\cdot\rangle$为半内积。

>[!thm] Cauchy-Schwarz不等式
>设$\langle\cdot,\cdot\rangle$为$X$上的半内积，则对任意$x,y\in X$，
>$$
>|\langle x,y\rangle|^2\le\langle x,x\rangle\langle y,y\rangle
>$$
>等号成立当且仅当存在不全为$0$的$\alpha,\beta\in\mathbb F$，使得
>$$
>\langle\alpha x+\beta y,\alpha x+\beta y\rangle=0
>$$
>若$\langle\cdot,\cdot\rangle$为内积，则等号成立当且仅当$x,y$线性相关。
^970a9c

**Proof**

记$a=\langle x,x\rangle,b=\langle y,y\rangle,c=\langle x,y\rangle$。对任意$\lambda\in\mathbb F$，
$$
0\le\langle x-\lambda y,x-\lambda y\rangle
=a-\overline\lambda c-\lambda\overline c+|\lambda|^2b
$$
若$b>0$，取$\lambda=c/b$，得到
$$
0\le a-\frac{|c|^2}{b}\Longrightarrow|c|^2\le ab
$$
若$b=0$，取$\lambda=tc,t>0$，则$a-2t|c|^2\ge0$对任意$t>0$成立，只能有$c=0$，不等式同样成立。

若等号成立，当$b>0$时，向量$x-(c/b)y$的半内积平方为$0$；当$b=0$时，直接取向量$y$即可。

反过来，若$\alpha,\beta$不全为$0$，且$v=\alpha x+\beta y$满足$\langle v,v\rangle=0$，由已证明的不等式，$\langle v,x\rangle=\langle v,y\rangle=0$。因此
$$
\begin{cases}
\alpha a+\beta\overline c=0\\
\alpha c+\beta b=0
\end{cases}
$$
这个齐次方程组有非零解，所以$ab-|c|^2=0$。若半内积为内积，$\langle v,v\rangle=0$等价于$v=0$，也就是$x,y$线性相关。

**QED**

>[!proposition] 内积诱导范数
>设$X$为内积空间，定义
>$$
>\|x\|=\sqrt{\langle x,x\rangle}
>$$
>则$\|\cdot\|$为$X$上的范数，即
>
>1. $\|x\|\ge0$，且$\|x\|=0\Longleftrightarrow x=0$
>2. $\|\alpha x\|=|\alpha|\|x\|$
>3. $\|x+y\|\le\|x\|+\|y\|$
>
>若$X$上只有半内积，则上式定义半范数，此时可能有$x\ne0$但$\|x\|=0$。

**Proof**

正定性由内积的定义得到。又
$$
\|\alpha x\|^2=\langle\alpha x,\alpha x\rangle
=|\alpha|^2\langle x,x\rangle=|\alpha|^2\|x\|^2
$$
因此$\|\alpha x\|=|\alpha|\|x\|$。由Cauchy-Schwarz不等式，
$$
\begin{aligned}
\|x+y\|^2
&=\|x\|^2+2\text{Re}\langle x,y\rangle+\|y\|^2\\
&\le\|x\|^2+2\|x\|\|y\|+\|y\|^2
=(\|x\|+\|y\|)^2
\end{aligned}
$$
两边开平方即得三角不等式。这些计算对半内积也成立。

**QED**

>[!proposition] 范数展开公式
>对内积空间中的$x,y$，
>$$
>\|x+y\|^2=\|x\|^2+2\text{Re}\langle x,y\rangle+\|y\|^2
>$$
>$$
>\|x-y\|^2=\|x\|^2-2\text{Re}\langle x,y\rangle+\|y\|^2
>$$

>[!thm] 内积的连续性
>设$X$为内积空间。若$x_n\to x,y_n\to y$，则
>$$
>\langle x_n,y_n\rangle\to\langle x,y\rangle
>$$
>特别地，固定$y\in X$，$x_n\to x$推出$\langle x_n,y\rangle\to\langle x,y\rangle$。
^i112102

**Proof**

因为$y_n\to y$，$\{\|y_n\|\}$有界。由Cauchy-Schwarz不等式，
$$
\begin{aligned}
|\langle x_n,y_n\rangle-\langle x,y\rangle|
&\le|\langle x_n-x,y_n\rangle|+|\langle x,y_n-y\rangle|\\
&\le\|x_n-x\|\|y_n\|+\|x\|\|y_n-y\|\to0
\end{aligned}
$$

**QED**

>[!def] Hilbert空间
>设$H$为内积空间，赋予内积诱导的范数与距离
>$$
>\|h\|=\sqrt{\langle h,h\rangle},\quad d(h,k)=\|h-k\|
>$$
>若$H$在这个距离下完备，即每个Cauchy列都在$H$中收敛，则称$H$为Hilbert空间。
^i112103

因此有
$$
\text{内积空间}\Longrightarrow\text{赋范线性空间}\Longrightarrow\text{度量空间}
$$
Hilbert空间是完备的内积空间，其范数使它成为[[商空间#Banach空间与范数等价|Banach空间]]。

# 例子

## $L^2$空间

>[!example] $L^2(\mu)$
>设$(X,\mathcal A,\mu)$为测度空间，$L^2(\mu)$由平方可积函数的几乎处处相等类组成。定义
>$$
>\langle f,g\rangle=\int_X f\overline g\,{d}\mu,\quad
>\|f\|_2=\left(\int_X|f|^2\,{d}\mu\right)^{\frac12}
>$$
>则$L^2(\mu)$为Hilbert空间。

Cauchy-Schwarz不等式保证$f\overline g$可积，内积的正定性在几乎处处相等类的意义下成立，完备性由$L^2$空间的完备性得到。

## Bergman空间

>[!def] Bergman空间
>设$G\subseteq\mathbb C$为开集，记${d}A={d}x{d}y$为平面Lebesgue面积测度。定义
>$$
>L_a^2(G)=\left\{f:G\to\mathbb C:f\text{在}G\text{上解析},\ \int_G|f(z)|^2\,{d}A(z)<+\infty\right\}
>$$
>称为$G$上的Bergman空间。

把解析函数与其几乎处处相等类对应，则$L_a^2(G)$为$L^2(G,{d}A)$的线性子空间，内积和范数为
$$
\langle f,g\rangle=\int_G f(z)\overline{g(z)}\,{d}A(z),\quad
\|f\|_2=\left(\int_G|f(z)|^2\,{d}A(z)\right)^{\frac12}
$$
两个解析函数若几乎处处相等，由连续性可知它们处处相等，因此上述对应是单射。
^4d4530

>[!lemma] 解析函数的面积平均值公式
>若$f$在闭圆盘$\overline{B(a,r)}$的某个邻域内解析，则
>$$
>f(a)=\frac1{\pi r^2}\int_{B(a,r)}f(z)\,{d}A(z)
>$$
^53b497

**Proof**

由解析函数的平均值公式，对$0<t\le r$，
$$
f(a)=\frac1{2\pi}\int_{-\pi}^{\pi}f(a+te^{i\theta})\,{d}\theta
$$
使用极坐标，
$$
\begin{aligned}
\frac1{\pi r^2}\int_{B(a,r)}f(z)\,{d}A(z)
&=\frac1{\pi r^2}\int_0^r t\int_{-\pi}^{\pi}f(a+te^{i\theta})\,{d}\theta\,{d}t\\
&=\frac2{r^2}f(a)\int_0^r t\,{d}t=f(a)
\end{aligned}
$$

**QED**

>[!lemma] 点值估计
>设$f\in L_a^2(G),a\in G$，且$r>0$满足$\overline{B(a,r)}\subseteq G$，则
>$$
>|f(a)|\le\frac1{r\sqrt\pi}\left(\int_{B(a,r)}|f(z)|^2\,{d}A(z)\right)^{\frac12}
>\le\frac1{r\sqrt\pi}\|f\|_2
>$$
^b919d4

**Proof**

由[[#^53b497|面积平均值公式]]和[[#^970a9c|Cauchy-Schwarz不等式]]，
$$
\begin{aligned}
|f(a)|
&=\frac1{\pi r^2}\left|\int_{B(a,r)}f(z)\cdot1\,{d}A(z)\right|\\
&\le\frac1{\pi r^2}\left(\int_{B(a,r)}|f(z)|^2\,{d}A(z)\right)^{\frac12}(\pi r^2)^{\frac12}\\
&=\frac1{r\sqrt\pi}\left(\int_{B(a,r)}|f(z)|^2\,{d}A(z)\right)^{\frac12}
\le\frac1{r\sqrt\pi}\|f\|_2
\end{aligned}
$$

**QED**

>[!thm] Bergman空间的完备性
>$L_a^2(G)$是$L^2(G,{d}A)$的闭线性子空间，因此是Hilbert空间。

**Proof**

设$\{f_n\}\subseteq L_a^2(G)$，且$f_n\to f$于$L^2(G,{d}A)$，只需要证明$f$有解析代表。

任取紧集$K\subseteq G$。由紧性，可以取$r>0$使得对所有$a\in K$都有$\overline{B(a,r)}\subseteq G$。由[[#^b919d4|点值估计]]，
$$
\sup_{a\in K}|f_n(a)-f_m(a)|\le\frac1{r\sqrt\pi}\|f_n-f_m\|_2\to0
$$
所以$\{f_n\}$在每个紧集上一致Cauchy，从而局部一致收敛到某个函数$g$。由解析函数列的局部一致收敛定理，$g$在$G$上解析。

另一方面，由$L^2$收敛，可以选取子列$\{f_{n_k}\}$使得$f_{n_k}\to f$几乎处处成立。结合$f_{n_k}\to g$逐点成立，得到$f=g$几乎处处。因此$g\in L_a^2(G)$，$f$有解析代表，故$L_a^2(G)$闭。

**QED**
