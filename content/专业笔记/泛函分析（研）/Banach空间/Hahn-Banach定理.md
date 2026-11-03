线性泛函、核与超平面的关系见[[商空间#线性泛函与超平面]]。下面考虑子空间上的有界线性泛函能否保范延拓到全空间。

# Hahn-Banach定理

>[!thm] 有界线性泛函的保范延拓
>设$X$为$\mathbb F$上的赋范线性空间，$\mathbb F=\mathbb R$或$\mathbb C$，$M$为$X$的线性子空间。若$f:M\to\mathbb F$为有界线性泛函，则存在有界线性泛函$F:X\to\mathbb F$，使得
>$$
>F|_M=f,\quad\|F\|=\|f\|
>$$
>称$F$为$f$的保范延拓。
^h70301

>[!note]
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

>[!note]
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
L=\sup_{m\in M}\{f(m)-p(m-x_0)\},\quad
U=\inf_{m\in M}\{p(m+x_0)-f(m)\}
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

由[[Hilbert空间上的基|Zorn引理]]，$\mathcal S$存在极大元$(N_{\max},F)$。若$N_{\max}\ne X$，取$x_0\notin N_{\max}$，由Step 1可以把$F$继续延拓到
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
>1. 若$F:X\to\mathbb C$为复线性泛函，令$g=\text{Re}\,F$，则$g:X\to\mathbb R$为实线性泛函，且
>$$
>F(x)=g(x)-ig(ix)
>$$
>2. 若$g:X\to\mathbb R$为实线性泛函，则
>$$
>F(x)=g(x)-ig(ix)
>$$
>是唯一满足$\text{Re}\,F=g$的复线性泛函。
>3. 若$X$为复赋范空间，则$F$有界当且仅当$g$有界，此时
>$$
>\|F\|=\|g\|
>$$
>其中$g$的范数是将$X$视为实赋范空间时的泛函范数。
^h70304

**Proof**

对第1条，$g$的实线性显然。由$F(ix)=iF(x)$，
$$
g(ix)=\text{Re}(iF(x))=-\text{Im}\,F(x)
$$
所以$F(x)=g(x)-ig(ix)$，这也说明复线性泛函由实部唯一确定。

对第2条，按公式定义$F$，它的可加性和实齐次性由$g$的实线性得到。又
$$
F(ix)=g(ix)-ig(-x)=g(ix)+ig(x)=iF(x)
$$
所以对任意$a,b\in\mathbb R$，
$$
F((a+ib)x)=aF(x)+bF(ix)=(a+ib)F(x)
$$
因此$F$复线性，且$\text{Re}\,F=g$。

对第3条，由$|g(x)|\le|F(x)|$，若$F$有界，则$g$有界，且$\|g\|\le\|F\|$。

反之，若$g$有界，对$F(x)\ne0$，写成$F(x)=e^{i\theta}|F(x)|$，则
$$
F(e^{-i\theta}x)=|F(x)|\in\mathbb R
$$
从而
$$
|F(x)|=g(e^{-i\theta}x)\le\|g\|\|e^{-i\theta}x\|=\|g\|\|x\|
$$
$F(x)=0$时不等式也成立。因此$F$有界，且$\|F\|\le\|g\|$。结合两个方向，$\|F\|=\|g\|$。

**QED**

# 复赋范空间上的保范延拓

现在证明[[#^h70301|Hahn-Banach保范延拓定理]]在$\mathbb F=\mathbb C$时成立。

**Proof**

设$f:M\to\mathbb C$为有界复线性泛函。把$X,M$看作实线性空间，令
$$
g=\text{Re}\,f:M\to\mathbb R
$$
由上面的引理，$g$有界且$\|g\|=\|f\|$。应用实数域的保范延拓，得到实线性泛函$G:X\to\mathbb R$，满足
$$
G|_M=g,\quad\|G\|=\|g\|
$$
定义
$$
F(x)=G(x)-iG(ix)
$$
则$F$为有界复线性泛函，并且$\|F\|=\|G\|=\|f\|$。

最后验证延拓性质。对$m\in M$，由于$M$是复线性子空间，$im\in M$，于是
$$
F(m)=G(m)-iG(im)=g(m)-ig(im)=f(m)
$$
所以$F|_M=f$，证毕。

**QED**

>[!note]
>用$|G(x)-iG(ix)|\le|G(x)|+|G(ix)|$只能得到带常数$2$的估计，不能说明保范。保范的关键是上面引理中的相位旋转，它给出$\|F\|=\|G\|$。

# 补充：非零有界线性泛函的存在

>[!proposition] 在给定非零向量上取到其范数
>设$X$为实或复赋范空间，$x_0\ne0$，则存在$F\in X^*$，使得
>$$
>\|F\|=1,\quad F(x_0)=\|x_0\|
>$$
^h70305

**Proof**

取$M=\text{span}\{x_0\}$，定义
$$
f:M\to\mathbb F,\quad f(ax_0)=a\|x_0\|
$$
则$f$线性，且
$$
|f(ax_0)|=|a|\|x_0\|=\|ax_0\|
$$
所以$\|f\|=1$。由Hahn-Banach定理，存在保范延拓$F\in X^*$，满足$\|F\|=1$及$F(x_0)=f(x_0)=\|x_0\|$。

**QED**

>[!proposition] 范数由有界线性泛函刻画
>对任意$x\in X$，
>$$
>\|x\|=\sup\{|F(x)|:F\in X^*,\ \|F\|\le1\}
>$$
>并且上确界可以取到。

**Proof**

若$\|F\|\le1$，则$|F(x)|\le\|F\|\|x\|\le\|x\|$，所以上确界不超过$\|x\|$。当$x\ne0$时，由上一命题可取$F$使得$F(x)=\|x\|$。$x=0$时取零泛函即可。

**QED**

>[!note]
>因此任意非零赋范空间上都存在非零有界线性泛函。进一步，若$x\ne y$，对$x-y$应用上面的结论，可以找到$F\in X^*$使得$F(x)\ne F(y)$。

>[!note] 参考
>手稿：2026.11.3，第4—5页。沿用“一维延拓—Zorn引理”的证明；实部恢复公式、范数相等及复数域的完整证明依据讲义与教材补全，末节为直接应用。
>
>《高等泛函》§4.4；Conway, *A Course in Functional Analysis*, 第III章§6，Theorem 6.2、Lemma 6.3、Corollary 6.5、Corollary 6.7与Lemma 6.9（书页78—81，PDF第92—95页）。
