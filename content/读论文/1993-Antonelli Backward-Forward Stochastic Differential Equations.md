>[!note] 主要工作
>第一次系统研究了如下类型的FBSDE，
>$$
>\begin{cases}
>U_t=J_t+\int_{0}^{t}f(s,U_s,V_s){d}A_s\\
>V_t=\mathbb{E}\left[\int_{t}^{T}g(s,U_s,V_s){d}C_s+Y|\mathscr{F}_t\right],V_T=Y
>\end{cases}
>$$
>其中$A_t,C_t$为有界变差过程，同时发展了研究FBSDE的第一个方法：压缩映像法。

>[!thm] 主定理
> 以下整理原文定理 3.1（pp.785–788）和定理 3.2（pp.788–790）；原文陈述与阅读核查备注分开列出。
>
> **共同设定与记号**
>
> 固定有限时间区间 $[0,T]$。滤过概率空间 $(\Omega,\mathscr F,(\mathscr F_t)_{0\le t\le T},\mathbb P)$ 满足通常条件（完备性与滤过右连续性），不要求是布朗滤过。未知量为一对实值适应过程 $(U,V)$；$Y$ 是给定的 $\mathscr F_T$-可测终端随机变量，$V_T=Y$。
>
> $f,g:[0,T]\times\Omega\times\mathbb R^2\to\mathbb R$ 联合可测，对每个固定 $(u,v)$，$f_t(\cdot,u,v)$、$g_t(\cdot,u,v)$ 均为 $\mathscr F_t$-可测。存在确定常数 $k>0$，使对 $h=f,g$，一致地有
> $$
> |h_t(\omega,u,v)-h_t(\omega,\widetilde u,\widetilde v)|
> \le k\bigl(|u-\widetilde u|+|v-\widetilde v|\bigr).
> $$
>
> **所用空间**
>
> 对适应、递增、càdlàg 过程 $D$，$D_0=0$，定义测度 $\mu$：对非负可测过程 $H$，
> $$
> \int_{\Omega\times[0,T]}H\,d\mu
> :=\mathbb E\int_0^T H_t\,dD_t.
> $$
> $L^1(\mu)$ 表示满足下式的过程等价类（按 $\mu$-几乎处处相同识别；求解时取相应适应可测过程）：
> $$
> \|H\|_{L^1(\mu)}:=\mathbb E\int_0^T|H_t|\,dD_t<\infty.
> $$
> 过程对使用和范数
> $$
> \|(U,V)\|_{L^1\times L^1}
> :=\|U\|_{L^1(\mu)}+\|V\|_{L^1(\mu)}.
> $$
> 对 $1<p<\infty$，$S^p$ 是适应 càdlàg 过程组成的空间，
> $$
> \|H\|_{S^p}:=\left(\mathbb E\sup_{0\le t\le T}|H_t|^p\right)^{1/p}<\infty,
> \qquad
> \|(U,V)\|_{S^p\times S^p}:=\|U\|_{S^p}+\|V\|_{S^p}.
> $$
> 对从零出发的半鞅 $R$，Protter 意义下的 $H^r$ 范数为
> $$
> \|R\|_{H^r}:=\inf_{R=L+B}
> \left\|[L]_T^{1/2}+|B|_T\right\|_{L^r},
> \qquad 1\le r\le\infty,
> $$
> 下确界取遍 $L_0=B_0=0$、$L$ 为 càdlàg 局部鞅、$B$ 为适应 càdlàg 有限变差过程的分解；$|B|_t:=\int_0^t|dB_s|$ 是总变差，$[L]$ 是二次变差。$H^\infty$ 指此范数有限的半鞅空间，即存在这样的分解使 $[L]_T^{1/2}+|B|_T$ 本质有界；不等于要求 $\sup_{t\le T}|R_t|$ 本质有界的 $S^\infty$。例如在 $[0,T]$ 上，$\|t\|_{H^\infty}=T$，标准布朗运动满足 $\|W\|_{H^\infty}=\sqrt T$。
>
> **定理 3.1：有限变差积分器，$L^1$ 框架（原文陈述）**
>
> 考虑
> $$
> \begin{cases}
> U_t=J_t+\displaystyle\int_0^t f_s(U_s,V_s)\,dA_s,\\[1mm]
> V_t=\mathbb E\!\left[Y+\displaystyle\int_t^T g_s(U_s,V_s)\,dC_s\,\middle|\,\mathscr F_t\right].
> \end{cases}
> $$
> 除共同设定外，假设：
>
> 1. $A,C$ 为适应 càdlàg 有限变差过程，$A_0=C_0=0$；存在确定常数 $\beta<\infty$，使 $|A|_T,|C|_T\le\beta$ a.s.（原文将其置于 $H^\infty$ 中）。
> 2. 按原文定义 $D_t:=\max\{|A|_t,|C|_t\}$，$\mu$ 为上面由 $D$ 诱导的测度，并要求
> $$
> \mathbb E\int_0^T|f_s(0,0)|\,dD_s<\infty,
> \qquad
> \mathbb E\int_0^T|g_s(0,0)|\,dD_s<\infty.
> $$
> 3. $Y\in L^1(\Omega,\mathscr F_T,\mathbb P)$；$J$ 为适应过程（沿用引言中的 càdlàg 设定），且
> $$
> \mathbb E\int_0^T|J_t|\,dD_t<\infty.
> $$
> 4. 满足原文的小性条件
> $$
> k\|D\|_{H^\infty}<1.
> $$
> **结论：** 以两条方程的右端定义固定点算子 $\Gamma$，则原文断言 $\Gamma$ 是 $L^1(\mu)\times L^1(\mu)$ 上的压缩映像，因而存在唯一适应解 $(U,V)\in L^1(\mu)\times L^1(\mu)$，方程在该空间的意义下成立。原文的压缩估计为
> $$
> \|\Gamma(U,V)-\Gamma(\widetilde U,\widetilde V)\|_{L^1\times L^1}
> \le k\|D\|_{H^\infty}
> \|(U-\widetilde U,V-\widetilde V)\|_{L^1\times L^1}.
> $$
> 特别地，$A_t=C_t=t$ 时，$D_t=t$、$\mu=d\mathbb P\,dt$，小性条件就是 $kT<1$。
>
> **定理 3.2：半鞅积分器，$S^p$ 框架（原文陈述）**
>
> 考虑
> $$
> \begin{cases}
> U_t=J_t+\displaystyle\int_0^t f_{s-}(U_{s-},V_{s-})\,dX_s,\\[1mm]
> V_t=\mathbb E\!\left[Y+\displaystyle\int_t^T g_{s-}(U_{s-},V_{s-})\,dZ_s\,\middle|\,\mathscr F_t\right].
> \end{cases}
> $$
> 此处 $X,Z$ 都是给定的积分器；$Z$ 不是现代 BSDE 记号中待求的鞅被积过程。左极限写法沿用原文；相应被积过程须可预测且随机积分有定义。
>
> 除共同的可测性、适应性和一致 $k$-Lipschitz 条件外，假设：
>
> 1. $X,Z\in H^\infty$，$X_0=Z_0=0$，其规范分解为
> $$
> X=M+A,\qquad Z=N+C,
> $$
> 其中 $M,N$ 为鞅，$A,C$ 为总变差有确定上界的有限变差过程；规范分解中的有限变差部分取可预测版本。
> 2. 对某个固定 $1<p<\infty$，
> $$
> f_\cdot(0,0),\ g_\cdot(0,0),\ J\in S^p,
> \qquad Y\in L^p(\Omega,\mathscr F_T,\mathbb P).
> $$
> 3. 令 $q=p/(p-1)$，$c_p$ 为半鞅范数估计 $\|R\|_{S^p}\le c_p\|R\|_{H^p}$ 中仅依赖于 $p$ 的常数。原文要求
> $$
> k\max\!\left(c_p\|X\|_{H^\infty},\ q\|C\|_{H^\infty}\right)<1.
> $$
> **结论：** 原文断言上述系统在 $S^p\times S^p$ 中存在唯一适应解 $(U,V)$，证明仍使用压缩映像原理。前向分量通过 Émery 不等式估计；在原文所用可积性条件下，后向积分的鞅部分具有零条件期望，因而其估计只涉及 $Z$ 的有限变差部分 $C$，再使用 Doob 的 $L^p$ 最大不等式。这也是 $p>1$ 和常数 $q$ 出现的原因。
>
> **阅读核查备注（与原文定理陈述区分）**
>
> - 定理 3.1 的一般积分器证明中，p.786 由 $D_t=\max\{|A|_t,|C|_t\}$ 推出 $d|A|,d|C|\le dD$，这一步一般不成立：累积量的逐点大小关系不能推出测度支配。例如 $A$ 先增加后保持常数、$C$ 随后在低于 $A$ 的水平内增加时，$D$ 不变但 $dC>0$。可改选共同支配过程 $\widehat D=|A|+|C|$，但需要同时重述测度、可积性与小性假设。$A=C=t$ 的特例没有这个支配问题。
> - 定理 3.2 在 p.788 定义的是和范数。按 pp.789–790 已列出的两个分量估计直接相加，得到的压缩常数为 $k(c_p\|X\|_{H^\infty}+q\|C\|_{H^\infty})$，而非定理中写出的 $k\max(c_p\|X\|_{H^\infty},q\|C\|_{H^\infty})$。因此原文的最大值条件需要进一步论证；按这两项估计作压缩论证时，应采用常数之和小于 $1$ 的较强条件。

>[!example] 反例说明只有Lipschitz条件不能保证FBSDE解的存在唯一性
>考虑系统
>$$
>\begin{cases}
>U_t=J_0+\int_{0}^{t}U_s+|V_s|{d}s\\
>V_t=\mathbb{E}\left[\int_{t}^{T}U_s+V_s{d}s+Y|\mathscr{F}_t\right]
>\end{cases}
>$$
>假设$J_0>0,Y>0$并且满足相应可测性和可积性。注意到$g(u,x)=u+|v|$和$f(u,v)=u+v$都是一致Lipschitz连续的，且Lipschitz常数为1。实际上可以解出，
>$$
>U_t=e^{t}\left(J_0+\int_{0}^{t}e^{-s}|V_s|{d}s\right),V_t=\mathbb{E}\left(e^{T-t}Y+\int_{t}^{T}e^{s-t}U_s{d}s|\mathscr{F}_t\right)
>$$
>因此可以知道$U_t,V_t>0$，因此不妨把原系统的绝对值去掉，取期望之后把两式相加得到，
>$$
>\mathbb{E}(U_t+V_t)=\mathbb{E}J_0+\mathbb{E}\int_{0}^{T}U_s+V_s{d}s+\mathbb{E}Y
>$$