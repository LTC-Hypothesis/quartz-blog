先回忆有限维（线性代数）情况。
>[!note] 有限维空间的伴随算子
>设$\{e_i\}_{i=1}^{n}$为一组规范正交基，给定线性变换$T$使得
>$$
>Te_i=\sum_{j=1}^{n}a_{ij}e_j
>$$
>现在定义$T$的伴随变换$S$，满足$\langle Tx,y\rangle=\langle x,Sy\rangle,\forall x,y$，设
>$$
>Se_i=\sum_{j=1}^{n}b_{ji}e_j
>$$
>则
>$$
>\begin{aligned}
>\langle Te_i,e_j\rangle=a_{ij}=\langle e_i,Se_j\rangle=\bar{b}_{ji}
>\end{aligned}
>$$
>这意味着$T$和$S$所对应的矩阵互为共轭转置。

>[!question] 
>那么我们现在的问题是，在Hilbert空间中，给定有界线性算子$T:H_1\to H_2$，是否存在这样的有界线性算子$S:H_2\to H_1$满足
>$$
>\langle Th_1,h_2\rangle=\langle h_1,Sh_2\rangle
>$$

>[!done] 
>我们的目标是把一个内积表示成另一个内积的形式，那么只有一个定理是在解决这个问题，就是[[The Riesz Representation Theorem|Riesz表示定理]]。若将$\langle Th_1,h_2\rangle$看作一个线性算子，对固定的$h_2$，定义
>$$
>L:H_1\to\mathbb{C},h_1\mapsto\langle Th_1,h_2\rangle
>$$
>可以验证线性性，并且有界
>$$
>\|L(h_1)\|=\|\langle Th_1,h_2\rangle\|\le\|Th_1\|\|h_2\|\le \|T\|\|h_2\|\|h_1\|
>$$
>因此根据Riesz表示定理，存在唯一的$k\in H_1$使得
>$$
>L(h_1)=\langle h_1,k\rangle\text{ i.e. }\langle Th_1,h_2\rangle=\langle h_1,k\rangle
>$$
>此时我们定义$k$为$k\triangleq Sh_2$。容易验证$S$的有界性，根据Riesz表示定理，
>$$
>\|Sh_2\|=\|L\|\le \|T\|\|h_2\|\Longrightarrow\|S\|\le \|T\|
>$$
>容易验证线性性，
>$$
>\begin{aligned}
>&\langle Th_1,h_2+\tilde{h}_2\rangle=\langle h_1,S(h_2+\tilde{h}_2)\rangle\\
>=&\langle Th_1,h_2\rangle+\langle Th_1,\tilde{h}_2\rangle\\
>=&\langle h_1,Sh_2\rangle+\langle h_1,S\tilde{h}_2\rangle=\langle h_1,Sh_2+S\tilde{h}_2\rangle
>\end{aligned}
>$$
>我们记$T^*\triangleq S$，称为有界线性算子$T$的伴随算子。

>[!proposition] 伴随算子的性质
>1. $(\alpha T_1+\beta T_2)^*=\bar{\alpha}T^*_1+\bar{\beta}T^*_2$
>2. $(T_1T_2)^*=T_2^*T_1^*$
>3. $T^{**}=(T^*)^*=T$
>4. $\|T^*\|=\|T\|=\|T^*T\|^{\frac{1}{2}}$

>[!def] 自伴算子
>若有界线性算子$T$和伴随算子$T^*$满足$T=T^*$，则称$T$为自伴算子。

>[!proposition] 自伴算子的性质
>$T$为自伴算子当且仅当$\forall x\in H,\langle Tx,x\rangle\in\mathbb{R}$。

**Proof**

$\Longrightarrow:$ 显然。

$\Longleftarrow:$ 对任意的$x,y\in H$，要证明$\langle Tx,y\rangle=\langle x,Ty\rangle$。考虑引入参数$\lambda\in\mathbb{C}$，根据假设$\langle T(x+\lambda y),x+\lambda y\rangle\in\mathbb{R}$，于是
$$
\begin{aligned}
\langle Tx,x\rangle+\lambda\langle Ty,x\rangle+\bar{\lambda}\langle Tx,y\rangle+|\lambda|^2\langle Ty,y\rangle\in\mathbb{R}
\end{aligned}
$$
从而$\lambda\langle Ty,x\rangle+\bar{\lambda}\langle Tx,y\rangle\in\mathbb{R}$，对于实数取一次共轭依然是自身，因此有
$$
\begin{aligned}
&\overline{\lambda\langle Ty,x\rangle+\bar{\lambda}\langle Tx,y\rangle}=\lambda\langle Ty,x\rangle+\bar{\lambda}\langle Tx,y\rangle\\
=&\bar{\lambda}\langle x,Ty\rangle+\lambda\langle y,Tx\rangle
\end{aligned}
$$
取$\lambda=1$得到
$$
\langle x,Ty\rangle+\langle y,Tx\rangle=\langle Ty,x\rangle+\langle Tx,y\rangle
$$
取$\lambda=i$得到
$$
\langle y,Tx\rangle-\langle x,Ty\rangle=\langle Ty,x\rangle-\langle Tx,y\rangle
$$
两式相减即可得到$\langle Tx,y\rangle=\langle x,Ty\rangle$

**QED**

>[!proposition] 自伴算子的算子范数
>若$T$为自伴算子，则$\|T\|=\sup_{\|x\|=1}|\langle Tx,x\rangle|$。

**Proof**

记$M\triangleq\sup_{\|x\|=1}|\langle Tx,x\rangle|$，注意到
$$
|\langle Tx,x\rangle|\le\|Tx\|\|x\|\le \|T\|\tag{$\|x\|=1$}
$$
因此$M\le \|T\|$，只需要证明$\|T\|\le M$。对于$\|x\|=\|y\|=1$，有
$$
\begin{aligned}
\langle T(x\pm y),x\pm y\rangle&=\langle Tx,x\rangle\pm\langle Tx,y\rangle\pm\langle Ty,x\rangle+\langle Ty,y\rangle\\
&=\langle Tx,x\rangle\pm\langle Tx,y\rangle\pm\overline{\langle Tx,y\rangle}+\langle Ty,y\rangle\\
&=\langle Tx,x\rangle\pm\text{Re}\langle Tx,y\rangle+\langle Ty,y\rangle
\end{aligned}
$$
两式相减得到
$$
4\text{Re}\langle Tx,y\rangle=\langle T(x+y),x+y\rangle-\langle T(x-y),x-y\rangle
$$
容易验证$|\langle Tx,x\rangle|\le M\|x\|^2$，从而
$$
\begin{aligned}
4\text{Re}\langle Tx,y\rangle&\le M(\|x+y\|^2+\|x-y\|^2)\\
&\le 2M(\|x\|^2+\|y\|^2)\\
&=4M
\end{aligned}
$$

**QED**

>[!proposition] 推论
>若$T$为自伴算子，且对$\forall x\in H$满足$\langle Tx,x\rangle=0$，则$T=0$。

>[!proposition] 推论
>对有界算子$T$满足对$\forall x\in H$成立$\langle Tx,x\rangle=0$，则$T=0$。

**Proof**

考虑把$T$写成$T_1+iT_2$的形式，只需要取
$$
T_1=\frac{T+T^*}{2},T_2=\frac{T-T^*}{2i}
$$

**QED**

>[!def] 正规算子
>若有界线性算子$T$和伴随算子$T^*$满足$TT^*=T^*T$，则称$T$为正规算子。

>[!proposition] 正规算子的性质
>以下命题等价
>1. $TT^*=T^*T$
>2. $\|Tx\|=\|T^*x\|$
>3. 若$T=T_1+iT_2$，则$T_1T_2=T_2T_1$

>[!thm] 
>若$T$有界，则$\text{Ker} \ T=(\text{range} \ T^*)^\bot$

**Proof**

$\Longrightarrow:$ 对$x\in\text{Ker} \ T$则$Tx=0$，注意到对任意的$y\in H$，
$$
0=\langle Tx,y\rangle=\langle x,T^*y\rangle\Longrightarrow x\in(\text{range} \ T^*)^\bot
$$

$\Longleftarrow:$ 对$x\in(\text{range} \ T^*)^\bot$，对任意的$y\in H$，
$$
0=\langle x,T^*y\rangle=\langle Tx,y\rangle\Longrightarrow Tx=0
$$

**QED**
>[!proposition] 推论
>1. $\text{Ker} \ T^*=(\text{range} \ T)^{\bot}$
>2. $(\text{Ker} \ T)^\bot=\overline{\text{range} \ T^*}$
>3. $(\text{Ker} \ T^*)^\bot=\overline{\text{range} \ T}$