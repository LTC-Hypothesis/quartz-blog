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

^399850

**Proof**

直接计算
$$
\left\langle h-\sum_{i=1}^{n}\langle h,e_i\rangle e_i,e_j\right\rangle=\langle h,e_j\rangle-\langle h,e_j\rangle=0
$$

**QED**

>[!warning] 
>若记$M\triangleq\text{span}\{e_i\}_{i=1}^{n}$，则$\sum_{i=1}^{n}\langle h,e_i\rangle e_i\in M$，则$\mathcal{P}_M(h)=\sum_{i=1}^{n}\langle h,e_i\rangle e_i$。

>[!thm] Bessel不等式
>若$\{e_n\}_{n=1}^{\infty}$为规范正交集，则对$h\in H$成立
>$$
>\sum_{n=1}^{\infty}|\langle h,e_n\rangle|^2\le \|h\|^2
>$$

**Proof**

根据[[#^399850|引理]]直接计算
$$
\begin{aligned}
\|h\|^2&=\left\|h-\sum_{i=1}^{n}\langle h,e_i\rangle e_i+\sum_{i=1}^{n}\langle h,e_i\rangle e_i\right\|^2\\
&=\left\|h-\sum_{i=1}^{n}\langle h,e_i\rangle e_i\right\|^2+\left\|\sum_{i=1}^{n}\langle h,e_i\rangle e_i\right\|^2\\
&=\left\|h-\sum_{i=1}^{n}\langle h,e_i\rangle e_i\right\|^2+\sum_{i=1}^{n}|\langle h,e_i\rangle|^2\ge\sum_{i=1}^{n}|\langle h,e_i\rangle|^2
\end{aligned}
$$
令$n\to\infty$即可。

**QED**

>[!warning] 推论
>若$\{e_n\}_{n=1}^{\infty}$为规范正交集，则$\sum_{n=1}^{\infty}|\langle h,e_i\rangle|^2<+\infty$。

>[!warning] 推论
>$\sum_{n=1}^{\infty}\langle h,e_n\rangle e_n$收敛。这是因为只用考察对$\varepsilon>0$，存在$N$，当$m>n>N$时，
>$$
>\left\|\sum_{i=n+1}^{m}\langle h,e_i\rangle e_i\right\|^2=\sum_{i=n+1}^{m}|\langle h,e_i\rangle|^2<\varepsilon
>$$

>[!thm] 
>设$H$为Hilbert空间，$\{e_n\}_{n=1}^{\infty}$为规范正交集，则以下等价
>1. $\{e_n\}_{n=1}^{\infty}$为$H$中一组基,
>2. ${\{e_n\}_{n=1}^{\infty}}^\bot=\{0\}$,
>3. $\forall h\in H,h=\sum_{n=1}^{\infty}\langle h,e_n\rangle e_n$,
>4. $\forall h,g\in H$，$\langle h,g\rangle=\sum_{n=1}^{\infty}\langle h,e_n\rangle\langle e_n,g\rangle$,
>5. Parseval等式：$\|h\|^2=\sum_{n=1}^{\infty}|\langle h,e_n\rangle|^2$

**Proof**

$(1)\Longrightarrow(2)$: 显然

$(2)\Longrightarrow(3)$: 注意到
$$
\left\langle h-\sum_{n=1}^{\infty}\langle h,e_n\rangle e_n,e_j\right\rangle=0\Longrightarrow h-\sum_{n=1}^{\infty}\langle h,e_n\rangle e_n\in\{e_n\}^\bot=\{0\}
$$

$(3)\Longrightarrow(4)$: 只需要计算
$$
\langle h,g\rangle=\left\langle \sum_{n=1}^{\infty}\langle h,e_n\rangle e_n,\sum_{n=1}^{\infty}\langle g,e_n\rangle e_n\right\rangle=\sum_{n=1}^{\infty}\langle h,e_n\rangle\langle e_n,g\rangle
$$

$(4)\Longrightarrow(5)$: 显然。

$(5)\Longrightarrow(4)$: 若不然，存在$h$使得$\langle h,e_i\rangle=0,\forall i$，则$h=0$。

**QED**

注意到以上讨论的情况都是在可数基意义下，如果是不可数的情况下