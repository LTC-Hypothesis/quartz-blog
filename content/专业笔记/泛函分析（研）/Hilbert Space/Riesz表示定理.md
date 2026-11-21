以下$H$为$\mathbb F$上的Hilbert空间，$\mathbb F=\mathbb R$或$\mathbb C$，内积对第一个变量线性。

# 有界线性泛函

>[!def] 线性泛函与有界线性泛函
>若映射$L:H\to\mathbb F$满足
>$$
>L(\alpha h_1+\beta h_2)=\alpha L(h_1)+\beta L(h_2),\quad
>h_1,h_2\in H,\quad\alpha,\beta\in\mathbb F
>$$
>则称$L$为线性泛函。若还存在$C\ge0$使得
>$$
>|L(h)|\le C\|h\|,\quad\forall h\in H
>$$
>则称$L$为有界线性泛函。

>[!proposition] 连续性与有界性等价
>对线性泛函$L:H\to\mathbb F$，下列条件等价：
>
>1. $L$连续。
>2. $L$在$0$处连续。
>3. $L$在某一点连续。
>4. $L$有界。

**Proof**

$(1)\Longrightarrow(2)\Longrightarrow(3)$显然。

$(3)\Longrightarrow(2)$：设$L$在$h_0$处连续。当$h\to0$时，$h+h_0\to h_0$，所以
$$
L(h)=L(h+h_0)-L(h_0)\to0=L(0)
$$
即$L$在$0$处连续。

$(2)\Longrightarrow(4)$：由$0$处的连续性，存在$\delta>0$使得$\|h\|<\delta$时$|L(h)|<1$。对$h\ne0$，
$$
\left\|\frac{\delta h}{2\|h\|}\right\|=\frac\delta2<\delta
\Longrightarrow\frac\delta{2\|h\|}|L(h)|<1
$$
因此$|L(h)|\le(2/\delta)\|h\|$，$h=0$时也成立，所以$L$有界。

$(4)\Longrightarrow(1)$：若$|L(h)|\le C\|h\|$，则
$$
|L(h)-L(k)|=|L(h-k)|\le C\|h-k\|
$$
所以$L$连续。

**QED**

>[!def] 有界线性泛函的范数
>对有界线性泛函$L$，定义
>$$
>\|L\|=\sup_{\|h\|\le1}|L(h)|
>=\inf\{C\ge0:|L(h)|\le C\|h\|,\ \forall h\in H\}
>$$
>当$H\ne\{0\}$时，也有
>$$
>\|L\|=\sup_{\|h\|=1}|L(h)|
>=\sup_{h\ne0}\frac{|L(h)|}{\|h\|}
>$$
>并且对每个$h\in H$，$|L(h)|\le\|L\|\|h\|$。

这些等式由线性性及对非零向量的归一化得到。所有有界线性泛函组成$H$的[[商空间#^f70301|对偶空间]]，记为$H^*$。

# Riesz表示定理

>[!thm] Riesz表示定理
>设$L:H\to\mathbb F$为线性泛函，则$L$有界当且仅当存在$h_0\in H$使得
>$$
>L(h)=\langle h,h_0\rangle,\quad\forall h\in H
>$$
>这个表示向量$h_0$唯一，并且
>$$
>\|L\|=\|h_0\|
>$$
^r112101

**Proof**

先设存在这样的$h_0$。由[[Hilbert空间简介#^970a9c|Cauchy-Schwarz不等式]]，
$$
|L(h)|=|\langle h,h_0\rangle|\le\|h\|\|h_0\|
$$
所以$L$有界，且$\|L\|\le\|h_0\|$。若$h_0\ne0$，取$h=h_0/\|h_0\|$，则$\|h\|=1$且
$$
L\left(\frac{h_0}{\|h_0\|}\right)
=\frac{\langle h_0,h_0\rangle}{\|h_0\|}=\|h_0\|
$$
故$\|L\|\ge\|h_0\|$，得到$\|L\|=\|h_0\|$。$h_0=0$时$L=0$，范数等式也成立。

反过来，设$L$有界。若$L=0$，取$h_0=0$即可。以下设$L\ne0$，记
$$
M=\text{Ker}(L)
$$
由$L$连续，$M=L^{-1}(\{0\})$为闭线性子空间，见[[简明拓扑学#^0f5727|连续映射的闭集原像闭]]。又$L\ne0$，所以$M\ne H$。由[[正交性#^o112102|正交分解定理]]，$M^\bot\ne\{0\}$。

取$0\ne f_0\in M^\bot$，记$a=L(f_0)$。若$a=0$，则$f_0\in M\cap M^\bot=\{0\}$，矛盾，因此$a\ne0$。

对任意$h\in H$，记$\alpha=L(h)$，则
$$
L\left(h-\frac\alpha a f_0\right)=\alpha-\frac\alpha a L(f_0)=0
$$
所以$h-(\alpha/a)f_0\in M$，从而
$$
0=\left\langle h-\frac\alpha a f_0,f_0\right\rangle
=\langle h,f_0\rangle-\frac\alpha a\|f_0\|^2
$$
整理得到
$$
L(h)=\alpha=\frac a{\|f_0\|^2}\langle h,f_0\rangle
=\left\langle h,\frac{\overline a}{\|f_0\|^2}f_0\right\rangle
$$
因此取
$$
h_0=\frac{\overline{L(f_0)}}{\|f_0\|^2}f_0
$$
便得到所需表示。

最后证明唯一性。若还有$h_1\in H$满足$L(h)=\langle h,h_1\rangle$，则
$$
\langle h,h_0-h_1\rangle=0,\quad\forall h\in H
$$
取$h=h_0-h_1$，得到$\|h_0-h_1\|^2=0$，所以$h_0=h_1$。

**QED**

>[!example] $L^2$空间上的有界线性泛函
>设$(X,\mathcal A,\mu)$为测度空间。若$F:L^2(\mu)\to\mathbb F$为有界线性泛函，则存在唯一的$g\in L^2(\mu)$使得
>$$
>F(f)=\int_X f\overline g\,{d}\mu,\quad\forall f\in L^2(\mu)
>$$
>并且$\|F\|=\|g\|_2$。这里的唯一性按几乎处处相等理解。

这是对$L^2(\mu)$的内积$\langle f,g\rangle=\int_X f\overline g\,{d}\mu$直接应用Riesz表示定理。
