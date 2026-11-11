下面考虑子空间上的有界线性泛函能否保范延拓到全空间。

# Hahn-Banach定理

>[!thm] 有界线性泛函的保范延拓
>设$X$为$\mathbb F$上的赋范线性空间，$\mathbb F=\mathbb R$或$\mathbb C$，$M$为$X$的线性子空间。若$f:M\to\mathbb F$为有界线性泛函，则存在有界线性泛函$F:X\to\mathbb F$，使得
>$$
>F|_M=f,\quad\|F\|=\|f\|
>$$
>称$F$为$f$的保范延拓。
^h70301

>[!warning] 
>这里不要求$X$完备，也不要求$M$闭。因为$F|_M=f$，必有$\|f\|\le\|F\|$，因此构造延拓时只需要证明$\|F\|\le\|f\|$。
>
>先证明实线性空间上由次线性函数控制的延拓定理，再取$p(x)=\|f\|\|x\|$得到保范延拓。复数域的情形通过实部转化为实数域的情形。

# 实线性空间上的延拓

>[!def] 次线性函数
>设$X$为实线性空间。函数$p:X\to\mathbb R$称为次线性函数，若
>$$
>\begin{cases}
>p(x+y)\le p(x)+p(y),&x,y\in X\\
>p(tx)=tp(x),&x\in X,\ t\ge0
>\end{cases}
>$$
^h70302

>[!warning] 
>$p$不一定非负，也不一定满足$p(-x)=p(x)$。例如实线性泛函本身就是次线性函数。
>
>由定义，$p(0)=0$，且$0\le p(x)+p(-x)$。正齐次性只对非负实数成立，所以延拓证明中需要分正、负两种情况处理系数。

>[!thm] 实Hahn-Banach定理
>设$X$为实线性空间，$p:X\to\mathbb R$为次线性函数，$M$为线性子空间，$f:M\to\mathbb R$为线性泛函，且
>$$
>f(m)\le p(m),\quad\forall m\in M
>$$
>则存在实线性泛函$F:X\to\mathbb R$，使得
>$$
>F|_M=f,\quad F(x)\le p(x),\quad\forall x\in X
>$$
^h70303

**Proof**

**Step 1：延拓一个维度。** 若$M\ne X$，取$x_0\notin M$，记
$$
\widetilde M=M+\text{span}\{x_0\}=\{m+tx_0:m\in M,t\in\mathbb R\}
$$
因为$x_0\notin M$，每个元素的上述表示唯一。只需要选定$\alpha=\widetilde f(x_0)$，就能定义线性延拓
$$
\widetilde f(m+tx_0)=f(m)+t\alpha
$$
接下来选择$\alpha$使得$\widetilde f\le p$。

当$t>0$时，要求
$$
f(m)+t\alpha\le p(m+tx_0)
$$
由正齐次性，等价于
$$
\alpha\le p\left(\frac mt+x_0\right)-f\left(\frac mt\right)
$$
由于$m/t$遍历$M$，所以只需要
$$
\alpha\le p(m+x_0)-f(m),\quad\forall m\in M
$$

当$t<0$时，令$s=-t>0$，要求
$$
f(m)-s\alpha\le p(m-sx_0)
$$
等价于
$$
\alpha\ge f\left(\frac ms\right)-p\left(\frac ms-x_0\right)
$$
所以只需要
$$
\alpha\ge f(m)-p(m-x_0),\quad\forall m\in M
$$
当$t=0$时，条件就是原来已有的$f(m)\le p(m)$。

因此只需要在下面两个数之间选取$\alpha$：
$$
L=\sup_{m\in M}\{f(m)-p(m-x_0)\},\quad U=\inf_{m\in M}\{p(m+x_0)-f(m)\}
$$
即证明$L\le U$，并且两者有限。

任取$m_1,m_2\in M$，由$f\le p$和$p$的次可加性，
$$
\begin{aligned}
f(m_1)+f(m_2)&=f(m_1+m_2)\\
&\le p(m_1+m_2)\\
&=p((m_1-x_0)+(m_2+x_0))\\
&\le p(m_1-x_0)+p(m_2+x_0)
\end{aligned}
$$
移项得到
$$
f(m_1)-p(m_1-x_0)\le p(m_2+x_0)-f(m_2)
$$
对$m_1$取上确界、对$m_2$取下确界，得到$L\le U$。再分别取$m=0$，可得
$$
-p(-x_0)\le L\le U\le p(x_0)
$$
所以$L,U$都是实数。选取$\alpha\in[L,U]$，则$\widetilde f(m+tx_0)=f(m)+t\alpha$满足
$$
\widetilde f|_M=f,\quad\widetilde f\le p\text{于}\widetilde M
$$
这样就完成了一维延拓。

**Step 2：用Zorn引理延拓到全空间。** 令$\mathcal S$为所有有序对$(N,g)$组成的集合，其中$N$为$X$的线性子空间，$g:N\to\mathbb R$为实线性泛函，满足
$$
M\subseteq N\subseteq X,\quad g|_M=f,\quad g(x)\le p(x),\quad\forall x\in N
$$
由于$(M,f)\in\mathcal S$，$\mathcal S$非空。定义偏序
$$
(N_1,g_1)\preceq(N_2,g_2)
\Longleftrightarrow N_1\subseteq N_2,\quad g_2|_{N_1}=g_1
$$
即$g_2$为$g_1$的延拓。

任取一条非空链$\{(N_\alpha,g_\alpha)\}_{\alpha\in A}$，令
$$
N=\bigcup_{\alpha\in A}N_\alpha
$$
因为链中任意两个元素可比较，任意$x,y\in N$都属于某个共同的$N_\gamma$，所以$N$为线性子空间。定义
$$
g(x)=g_\alpha(x),\quad x\in N_\alpha
$$
若$x\in N_\alpha\cap N_\beta$，由链的可比较性，其中一个泛函延拓另一个，因此两者在$x$处取值相同，$g$良定义。

同样把任意两个向量放入一个共同的$N_\gamma$，可知$g$线性。又$g|_M=f$且$g\le p$，因此$(N,g)\in\mathcal S$，并为这条链的上界。空链也有上界$(M,f)$。

由[[Hilbert空间上的基#^d11bce|Zorn引理]]，$\mathcal S$存在极大元$(N_{\max},F)$。若$N_{\max}\ne X$，取$x_0\notin N_{\max}$，由Step 1可以把$F$继续延拓到
$$
N_{\max}+\text{span}\{x_0\}
$$
且仍被$p$控制，这与极大性矛盾。因此$N_{\max}=X$，$F$就是所求延拓。

**QED**

>[!warning]
>这里的偏序是“定义域包含，并在原定义域上保持原泛函”，不是逐点比较$g_1(x)\le g_2(x)$。
>
>Zorn引理要求每条链都有上界，不要求整个偏序集是全序集。无限维情形中，仅说“反复做一维延拓”还不足以说明可以延拓到整个空间。

>[!proposition] 实赋范空间上的保范延拓
>若$X$为实赋范空间，$f:M\to\mathbb R$为有界线性泛函，则存在$F:X\to\mathbb R$，满足$F|_M=f$及$\|F\|=\|f\|$。

**Proof**

取$p(x)=\|f\|\|x\|$，则$p$为次线性函数，且对$m\in M$，
$$
f(m)\le|f(m)|\le\|f\|\|m\|=p(m)
$$
由实Hahn-Banach定理，存在实线性延拓$F$，满足$F(x)\le\|f\|\|x\|$。把$x$换成$-x$，又有
$$
-F(x)=F(-x)\le\|f\|\|-x\|=\|f\|\|x\|
$$
因此$|F(x)|\le\|f\|\|x\|$，即$\|F\|\le\|f\|$。另一方面，$F|_M=f$，所以$\|f\|\le\|F\|$，从而范数相等。

**QED**

# 复线性泛函与实部

把复线性空间$X$只看作实线性空间时，底层集合与加法不变，只把数乘限制为实数。

>[!lemma] 复线性泛函由实部唯一确定
>设$X$为复线性空间。
>1. 若$F:X\to\mathbb C$为复线性泛函，令$g=\text{Re}\,F$，则$g:X\to\mathbb R$为实线性泛函
>2. 若$g:X\to\mathbb R$为实线性泛函，则存在唯一满足$\text{Re}\,F=g$的复线性泛函。

**Proof**

(1) 写成$F(x)=f_1(x)+if_2(x)$，其中$f_1=\text{Re}\,F,f_2=\text{Im}\,F$。由$F$的可加性及对实数的齐次性，$f_1,f_2$都是实线性泛函。

再由$F(ix)=iF(x)$，
$$
f_1(ix)+if_2(ix)=-f_2(x)+if_1(x)
$$
比较实部和虚部，得到
$$
f_1(ix)=-f_2(x),\quad f_2(ix)=f_1(x)
$$
所以
$$
F(x)=f_1(x)-if_1(ix)
$$
因此复线性泛函完全由实部确定，特别地，$\text{Re}\,F_1=\text{Re}\,F_2\Longrightarrow F_1=F_2$。

(2) 给定实线性泛函$g:X\to\mathbb R$，定义
$$
F(x)=g(x)-ig(ix)
$$
则$F$可加且实齐次，$\text{Re}\,F=g$。只需要再证明$F(ix)=iF(x)$：
$$
F(ix)=g(ix)-ig(-x)=g(ix)+ig(x)=iF(x)
$$
于是对$a,b\in\mathbb R$，
$$
F((a+ib)x)=aF(x)+bF(ix)=(a+ib)F(x)
$$
所以$F$复线性。唯一性由第1条的实部恢复公式得到。

**QED**

# 复赋范空间上的保范延拓

下面证明[[#^h70301|Hahn-Banach定理]]的复数域情形。

**Proof**

设$f:M\to\mathbb C$为有界复线性泛函，取
$$
p(x)=\|f\|\|x\|,\quad f_1=\text{Re}\,f
$$
把$X,M$看作实线性空间，则$f_1$实线性，且对$m\in M$，
$$
f_1(m)\le|f(m)|\le p(m)
$$
由[[#^h70303|实Hahn-Banach定理]]，存在实线性泛函$F_1:X\to\mathbb R$，满足
$$
F_1|_M=f_1,\quad F_1(x)\le p(x)
$$
因为$F_1(-x)=-F_1(x)$且$p(-x)=p(x)$，也有$|F_1(x)|\le p(x)$。

定义
$$
F(x)=F_1(x)-iF_1(ix)
$$
由[[#复线性泛函与实部|实部恢复公式]]，$F$为复线性泛函，且$\text{Re}\,F=F_1$。因此
$$
\text{Re}(F|_M)=F_1|_M=f_1=\text{Re}\,f
$$
由于$F|_M,f$都是$M$上的复线性泛函，得到$F|_M=f$。

再证明$|F(x)|\le p(x)$。当$F(x)\ne0$时，写成$F(x)=e^{i\theta}|F(x)|$，则
$$
\begin{aligned}
|F(x)|&=e^{-i\theta}F(x)=F(e^{-i\theta}x)\\
&=\text{Re}\,F(e^{-i\theta}x)=F_1(e^{-i\theta}x)\\
&\le\|f\|\|e^{-i\theta}x\|=\|f\|\|x\|
\end{aligned}
$$
$F(x)=0$时也成立。因此$F$有界且$\|F\|\le\|f\|$。结合$F|_M=f$得到$\|f\|\le\|F\|$，从而$\|F\|=\|f\|$。

**QED**

# Hahn-Banach定理的推论

以下$X$为实或复赋范空间，记$X^*=\mathcal B(X,\mathbb F)$为对偶空间，见[[商空间#^f70301|有界线性泛函]]。

>[!proposition] 在给定非零向量上取到其范数
>若$x_0\in X,x_0\ne0$，则存在$f\in X^*$，使得
>$$
>\|f\|=1,\quad f(x_0)=\|x_0\|
>$$
^h71001

**Proof**

取$M=\text{span}\{x_0\}$，定义
$$
f_0:M\to\mathbb F,\quad f_0(\lambda x_0)=\lambda\|x_0\|
$$
则$f_0$线性，并且
$$
|f_0(\lambda x_0)|=|\lambda|\|x_0\|=\|\lambda x_0\|
$$
所以$\|f_0\|=1$。由Hahn-Banach定理，存在保范延拓$f\in X^*$，满足$f|_M=f_0$。于是$\|f\|=1$，且$f(x_0)=\|x_0\|$。

**QED**

>[!proposition] 用对偶空间刻画范数
>对任意$x\in X$，
>$$
>\|x\|=\sup_{f\in X^*,\ \|f\|\le1}|f(x)|
>$$
>并且上确界可以取到。
^h71002

**Proof**

对$\|f\|\le1$，有$|f(x)|\le\|f\|\|x\|\le\|x\|$，所以上确界不超过$\|x\|$。若$x\ne0$，由上一命题可以选取$f$使得$\|f\|=1,f(x)=\|x\|$。$x=0$时取零泛函即可。

**QED**

## 双对偶空间与自然嵌入

>[!def] 双对偶空间
>对偶空间$X^*$的对偶称为$X$的双对偶空间，记为
>$$
>X^{**}=(X^*)^*=\mathcal B(X^*,\mathbb F)
>$$
>对每个$x\in X$，定义
>$$
>\widehat x:X^*\to\mathbb F,\quad\widehat x(f)=f(x)
>$$

>[!proposition] 自然嵌入是线性等距映射
>对每个$x\in X$，$\widehat x\in X^{**}$，且$\|\widehat x\|=\|x\|$。因此
>$$
>\rho:X\to X^{**},\quad x\mapsto\widehat x
>$$
>是线性等距嵌入。
^h71003

**Proof**

$\widehat x$关于$f$线性，并且
$$
|\widehat x(f)|=|f(x)|\le\|f\|\|x\|
$$
所以$\widehat x$有界。由[[#^h71002|对偶空间对范数的刻画]]，
$$
\|\widehat x\|=\sup_{\|f\|\le1}|\widehat x(f)|
=\sup_{\|f\|\le1}|f(x)|=\|x\|
$$
又由$f$的线性，$\widehat{ax+by}=a\widehat x+b\widehat y$，因此$\rho$线性且保范，特别地是单射。

**QED**

>[!def] 自反空间
>若自然嵌入$\rho:X\to X^{**}$是满射，即
>$$
>X^{**}=\{\widehat x:x\in X\}=\rho(X)
>$$
>则称$X$为自反空间。
>
>这里把$X$写成$X^{**}$的子空间，或在自反时写$X=X^{**}$。
^h71004

## 点与闭子空间的分离

>[!thm] 分离定理
>设$M$为赋范空间$X$的闭线性子空间，$x_0\notin M$，则存在$f\in X^*$，使得
>$$
>f(x_0)=1,\quad f|_M=0,\quad\|f\|=\frac1{\text{dist}(x_0,M)}
>$$
^h71005

**Proof**

记$Q:X\to X/M$为商映射，
$$
d=\text{dist}(x_0,M)=\|[x_0]\|_{X/M}
$$
因为$M$闭且$x_0\notin M$，$d>0$。在赋范空间$X/M$上应用[[#^h71001|给定非零向量处取到范数的泛函]]，存在$\widetilde f\in(X/M)^*$，使得
$$
\|\widetilde f\|=1,\quad\widetilde f([x_0])=\|[x_0]\|_{X/M}=d
$$
定义
$$
f=\frac1d\widetilde f\circ Q,\quad f(x)=\frac1d\widetilde f([x])
$$
则$f$线性，$f(x_0)=1$，并且对$m\in M$，$f(m)=d^{-1}\widetilde f([0])=0$。由[[商空间#^q62708|商映射的有界性]]，
$$
|f(x)|\le\frac1d\|\widetilde f\|\|Qx\|_{X/M}\le\frac1d\|x\|
$$
所以$f\in X^*$且$\|f\|\le d^{-1}$。

反过来，由商范数的定义，存在$m_n\in M$使得$\|x_0+m_n\|\to d$。由于$f(x_0+m_n)=1$，
$$
\|f\|\ge\left|f\left(\frac{x_0+m_n}{\|x_0+m_n\|}\right)\right|
=\frac1{\|x_0+m_n\|}\to\frac1d
$$
因此$\|f\|=d^{-1}$。

**QED**

>[!proposition] 用有界线性泛函的核刻画子空间的闭包
>设$M$为赋范空间$X$的线性子空间，不要求$M$闭，则
>$$
>\overline M=\bigcap_{\substack{f\in X^*\\f|_M=0}}\text{Ker}(f)
>$$
^h71006

**Proof**

若$f\in X^*$且$f|_M=0$，则$M\subseteq\text{Ker}(f)$。由$f$连续，$\text{Ker}(f)$闭，见[[简明拓扑学#^0f5727|连续映射的闭集原像闭]]，因此$\overline M\subseteq\text{Ker}(f)$。对所有这样的$f$取交，得到
$$
\overline M\subseteq\bigcap_{\substack{f\in X^*\\f|_M=0}}\text{Ker}(f)
$$
若$x_0\notin\overline M$，对闭子空间$\overline M$应用分离定理，存在$f\in X^*$满足
$$
f(x_0)=1,\quad f|_{\overline M}=0
$$
于是$f|_M=0$而$x_0\notin\text{Ker}(f)$，所以$x_0$不属于右侧交集，得到反向包含。

**QED**


