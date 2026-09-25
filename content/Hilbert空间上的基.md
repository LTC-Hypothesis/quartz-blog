>[!def] Hamel基
>设$S\subseteq H$为一个基，若对$\forall h\in H$，$\exists\left\{s_1,\cdots,s_n\right\}\subseteq S$使得$h=\alpha_1 s_1+\cdots,\alpha_n s_n$

>[!lemma] Zorn引理
>设$X$为偏序集，若$X$的全序子集有界，则$X$有极大元。

>[!def] Hilbert空间上的基
>称$\left\{e_i\right\}_{i=1}^{n}$为Hilbert空间上一组基，若对任意的$h\in H$，都有$h=\sum_{i=1}^{\infty}\alpha_ie_i$。

>[!def] 正交集
>$S\subseteq H$称为正交集，若对任意的$s_1,s_2\in S$都有$s_1\bot s_2$。

>[!proposition] 
>正交集是线性无关集。

**Proof**

设$s_1,\cdots,s_n\in S$，考虑$\alpha_1s_1+\cdots+\alpha_ns_n=0$，要证明$\alpha_i=0,1\le i\le n$。做内积
$$
0=\langle\alpha_1s_1+\cdots+\alpha_ns_n,s_i\rangle=\alpha_i\langle s_i,s_i\rangle\Longrightarrow \alpha_i=0
$$

**QED**

>[!def] 规范正交集
>$S$称为规范正交集，若$S$为正交集且$\forall s\in S$有$\|s\|=1$。

>[!lemma] 
>$\{e_i\}_{i=1}^{n}$为规范正交集，$h\in H$，则$(h-\sum_{i=1}^{n}\langle h,e_i\rangle e_i)\bot e_j,1\le j\le n$

**Proof**

直接计算
$$
\left\langle h-\sum_{i=1}^{n}\langle h,e_i\rangle e_i,e_j\right\rangle=\langle h,e_j\rangle-\langle h,e_j\rangle=0
$$

**QED**

>[!warning] 
>若记$M\triangleq\text{span}\{e_i\}_{i=1}^{n}$，则$\sum_{i=1}^{n}\langle h,e_i\rangle e_i\in M$，则$\mathcal{P}$