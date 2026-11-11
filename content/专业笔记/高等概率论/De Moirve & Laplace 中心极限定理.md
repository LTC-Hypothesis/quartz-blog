>[!note] 中心极限定理
>令 $S_n=\sum_{i=1}^nX_i$。[[弱大数定律（WLLN）]]与[[强大数定律（SLLN）]]研究 $S_n/n$ 是否收敛到均值；中心极限定理（Central Limit Theorem，CLT）进一步研究样本平均在均值附近的波动。
>
>当 $X_1,X_2,\cdots$ 为 i.i.d.，$\mathbb{E}X_1=\mu$，$0<\operatorname{Var}(X_1)=\sigma^2<\infty$ 时，典型结论为
>$$
>\frac{S_n-n\mu}{\sigma\sqrt n}
>=\frac{\sqrt n}{\sigma}\left(\frac{S_n}{n}-\mu\right)
>\xrightarrow{d}N(0,1).
>$$
>这里是分布趋于正态分布，不是上述随机变量逐点趋于某个固定数。

先从对称简单随机游走看起。

>[!thm] De Moivre–Laplace 中心极限定理：对称简单随机游走
>设 $X_1,X_2,\cdots$ 为 i.i.d.，且
>$$
>\mathbb{P}(X_i=1)=\mathbb{P}(X_i=-1)=\frac12,
>\qquad S_0=0,\quad S_n=\sum_{i=1}^nX_i.
>$$
>记标准正态密度及分布函数为
>$$
>\varphi(x)=\frac1{\sqrt{2\pi}}e^{-x^2/2},
>\qquad \Phi(x)=\int_{-\infty}^x\varphi(y)\,dy.
>$$
>则对任意 $-\infty<a<b<\infty$，
>$$
>\mathbb{P}\left(a\le\frac{S_n}{\sqrt n}\le b\right)
>\longrightarrow\int_a^b\varphi(x)\,dx.
>$$
>等价地，$S_n/\sqrt n\xrightarrow{d}N(0,1)$。

^de-moivre-laplace

**Proof**

先考虑偶数步。$S_{2n}=2k$ 等价于 $2n$ 次中恰有 $n+k$ 次向右走，因此
$$
\mathbb{P}(S_{2n}=2k)
=\binom{2n}{n+k}2^{-2n},
$$
由 Stirling 公式
$$
n!\sim\sqrt{2\pi n}\left(\frac ne\right)^n,
$$
当 $k=k_n$ 满足 $2k/\sqrt{2n}\to x$ 时，$k/n\to0$，从而
$$
\begin{aligned}
\mathbb{P}(S_{2n}=2k)
&\sim\frac1{\sqrt{\pi n}}
\left(1+\frac kn\right)^{-n-k-1/2}
\left(1-\frac kn\right)^{-n+k-1/2}\\
&=\frac1{\sqrt{\pi n}}
\left(1-\frac{k^2}{n^2}\right)^{-n-1/2}
\left(1+\frac kn\right)^{-k}
\left(1-\frac kn\right)^k.
\end{aligned}
$$
这里 $k$ 随 $n$ 变化，并且始终取整数。不能对任意实数 $x$ 直接令 $k=x\sqrt{n/2}$。

回顾一个常用极限：若 $c_n\to0$，$a_nc_n\to\lambda$，则
$$
(1+c_n)^{a_n}\to e^\lambda.
$$
事实上，$1+c_n>0$ 对充分大的 $n$ 成立，且
$$
a_n\log(1+c_n)
=a_nc_n\frac{\log(1+c_n)}{c_n}\longrightarrow\lambda.
$$
$c_n=0$ 时把后面的比值定义为 $1$ 即可。这里允许 $a_n$ 为负数；相关乘积形式见[[Durrett习题3.1]]。

由 $k^2/n\to x^2/2$，
$$
\begin{aligned}
\left(1-\frac{k^2}{n^2}\right)^{-n-1/2}&\to e^{x^2/2},\\
\left(1+\frac kn\right)^{-k}&\to e^{-x^2/2},\\
\left(1-\frac kn\right)^k&\to e^{-x^2/2}.
\end{aligned}
$$
所以得到局部估计
$$
\mathbb{P}(S_{2n}=2k)
\sim\frac1{\sqrt{\pi n}}e^{-x^2/2}
$$

