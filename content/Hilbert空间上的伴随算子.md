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