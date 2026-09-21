>[!note] 主要工作
>第一次系统研究了如下类型的FBSDE，
>$$
>\begin{cases}
>U_t=J_t+\int_{0}^{t}f(s,U_s,V_s){d}X_s\\
>V_t=\mathbb{E}\left[\int_{t}^{T}g(s,U_s,V_s){d}Z_s+Y|\mathscr{F}_t\right],V_T=Y
>\end{cases}
>$$
>发展了研究FBSDE的第一个方法，压缩映像法。

>[!thm] 主定理
>

>[!example] 反例说明只有Lipschitz条件不能保证FBSDE解的存在唯一性
>