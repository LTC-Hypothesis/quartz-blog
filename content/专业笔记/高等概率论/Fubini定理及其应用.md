首先回故[[随机变量与分布函数#^bf1fba|乘积空间]]。我们现在的任务是在乘积空间上构造合适的概率测度。一个简单的方法是按照笛卡尔积，分别作用在各自空间相应的集合上。
>[!def] 乘积概率测度
>对$A\times B\in\mathscr{F}_1\otimes\mathscr{F}_2$，定义其上的概率测度为
>$$
>\mathbb{P}_1\otimes\mathbb{P}(A\times B):=\mathbb{P}_1(A)\mathbb{P}_2(B)
>$$
>实际上容易验证$\mathbb{P}_1\otimes\mathbb{P}_2$为$\mathscr{A}$上的测度，其中$\mathscr{A}=\left\{A\times B:A\in\mathscr{F}_1,B\in\mathscr{F}_2\right\}$。根据[[测度论基础#^fa2ae7|Caretheodory延拓定理]]，可以延拓为$\mathscr{F}_1\otimes\mathscr{F}_2$上的测度。

>[!def] 核函数方法（马氏过程）
>**概率核**：设 $(\Omega_1,\mathscr F_1)$、$(\Omega_2,\mathscr F_2)$ 为可测空间。若 $K:\Omega_1\times\mathscr F_2\to[0,1]$ 满足：固定 $x$ 时，$K(x,\cdot)$ 是概率测度；固定 $B\in\mathscr F_2$ 时，$x\mapsto K(x,B)$ 可测，则称 $K$ 为概率核。
>
>**构造联合测度**：给定 $\Omega_1$ 上的概率测度 $\mu$，在 $\mathscr F_1\otimes\mathscr F_2$ 上定义
>$$
>(\mu\otimes K)(C)=\int_{\Omega_1}\left[\int_{\Omega_2}\mathbf1_C(x,y)K(x,dy)\right]\mu(dx).
>$$
>特别地，$(\mu\otimes K)(A\times B)=\int_A K(x,B)\mu(dx)$。这表示“先按 $\mu$ 选取 $x$，再按 $K(x,\cdot)$ 选取 $y$”。可测性可由矩形集经 $\pi$–$\lambda$ 定理推广，可列可加性由单调收敛定理得到。
>
>**与独立性的关系**：这一般只是乘积空间上的联合测度；若 $K(x,B)=\nu(B)$ 不依赖 $x$，就退化为普通乘积测度 $\mu\otimes\nu$，两个坐标独立。
>
>**构造马氏链**：在同一状态空间 $(S,\mathscr S)$ 上，给定初始分布 $\mu_0$ 和转移核 $K$，通过迭代积分定义有限维分布
>$$
>\mathbb P(X_0\in A_0,\ldots,X_n\in A_n)
>=\int_{A_0}\mu_0(dx_0)\int_{A_1}K(x_0,dx_1)\cdots\int_{A_n}K(x_{n-1},dx_n).
>$$
>Ionescu–Tulcea 定理保证这些分布唯一确定 $S^{\mathbb N_0}$ 的乘积 $\sigma$-代数上的概率测度。坐标过程满足
>$$
>\mathbb P(X_{n+1}\in B\mid\sigma(X_0,\ldots,X_n))=K(X_n,B)\quad\text{a.s.}
>$$
>即下一步的条件分布只依赖当前状态；马氏性一般不意味着各时刻的随机变量相互独立。

通常情况我们的乘积测度都是第一种。在乘积测度下容易构造相应的积分。
>[!def] 乘积测度下重积分
>可测函数$f:\Omega_1\times\Omega_2\to\mathbb{R},(x,y)\mapsto f(x,y)$，积分定义为
>$$
>\iint_{\Omega_1\times\Omega_2}f(x,y)d\mathbb{P}_1\otimes\mathbb{P}_2
>$$
>一个很自然的问题是是否能将重积分写成累次积分的形式，不同测度下积分号是否可以交换？这就是Fubini定理。

>[!thm] Fubini定理
>要求$f(x,y)$可积，即$\iint|f(x,y)|d\mathbb{P}_1\otimes\mathbb{P}_2<\infty$，则成立
>$$
>\iint_{\Omega_1\times\Omega_2} f(x,y){d\mathbb{P}_1}\otimes\mathbb{P}_2=\int_{\Omega_2}\int_{\Omega_1} f(x,y)d\mathbb{P}_1d\mathbb{P}_2=\int_{\Omega_1}\int_{\Omega_2} f(x,y){d}\mathbb{P}_2d\mathbb{P}_1
>$$

>[!warning] 
>实际上，条件可以换成只要三项中某一项存在，则上述等式成立。

>[!example] 期望计算方法
>若$\mathbb{E}|X|<\infty$，成立
>$$
>\mathbb{E}|X|=\int_{0}^{\infty}\mathbb{P}(|X|>t){d}t
>$$

**Proof**

直接计算
$$
\begin{aligned}
\int_{0}^{\infty}\mathbb{P}(|X|>t){d}t&=\int_{0}^{\infty}\int_{\Omega}\mathbb{1}_{\{|X|>t\}}{d}\mathbb{P}dt=\int_{\Omega}\int_{0}^{\infty}\mathbb{1}_{\{|X|>t\}}{d}td\mathbb{P}\\
&=\int_{\Omega}|X|{d}\mathbb{P}=\mathbb{E}|X|
\end{aligned}
$$

**QED**

>[!example] $p-$矩计算方法
>若$\mathbb{E}|X|<\infty,p>0$,成立
>$$
>\mathbb{E}|X|^p=\int_{0}^{\infty}pt^{p-1}\mathbb{P}(|X|>t){d}t
>$$

^f5a22d

>[!example] 可积的充要条件
>$\mathbb{E}|X|<\infty$当且仅当成立
>$$
>\sum_{n=1}^{\infty}\mathbb{P}(X>n)<\infty
>$$

**Proof**

注意到
$$
\begin{aligned}
\mathbb{E}|X|=\int_{0}^{\infty}\mathbb{P}(|X|>t){d}t=\sum_{n=0}^{\infty}\int_{n}^{n+1}\mathbb{P}(|X|>t){d}t
\end{aligned}
$$
有不等式成立
$$
\sum_{n=0}^{\infty}\mathbb{P}(|X|>n+1)\le\sum_{n=0}^{\infty}\int_{n}^{n+1}\mathbb{P}(|X|>t){d}t\le\sum_{n=0}^{\infty}\mathbb{P}(|X|>n)
$$

**QED**

>[!example] 
>若$\mathbb{E}|X|<\infty$，则成立
>$$
>\lim_{t\to\infty}\mathbb{P}(|X|>t)=0,\lim_{t\to\infty}t\mathbb{P}(|X|>t)=0
>$$

**Proof**

$\mathbb{E}|X|<\infty$可以得到
$$
\sum_{n=1}^{\infty}\mathbb{P}(|X|>n)<\infty
$$
则通项收敛到0，第一个极限成立。对于第二个极限，根据可积性考虑，
$$
\lim_{u\to\infty}u\mathbb{P}(|X|>2u)\le \lim_{u\to\infty}\int_{u}^{2u}\mathbb{P}(|X|>t)=0
$$

**QED**

>[!example] 
>若$X_n\xrightarrow{\mathbb{P}}X$，$X_n\ge0,X\ge0,X_n\le1$，证明：$\lim_{n\to\infty}\mathbb{E}X_n=\mathbb{E}X$。

^42f750

**Proof**

由于$X_n\xrightarrow{\mathbb{P}}X$，因此$\mathbb{P}(|X_n-X|\ge\varepsilon)\to0\text{ as }n\to\infty$且$X\le1$。我们证明更强的结论，$\mathbb{E}|X_n-X|\to0$，
$$
\begin{aligned}
\mathbb{E}|X_n-X|&=\int_{\Omega}|X_n-X|{d}\mathbb{P}\\
&=\int_{\{|X_n-X|<\varepsilon\}}|X_n-X|{d}\mathbb{P}+\int_{\{|X_n-X|\ge\varepsilon\}}|X_n-X|{d}\mathbb{P}\\
&\le \varepsilon+2\mathbb{P}\left(|X_n-X|\ge\varepsilon\right)
\end{aligned}
$$

**QED**

>[!warning] 依概率收敛下的控制收敛定理
>若$X_n\xrightarrow{\mathbb{P}}X$且$|X_n|\le Y$，其中$Y$满足$\mathbb{E}|Y|<\infty$，则满足
>$$
>\lim_{n\to\infty}\mathbb{E}X_n=\mathbb{E}X
>$$

^fd31fb

>[!example] 
>若$\mathbb{P}(X_n>t)\to\mathbb{P}(X>t)\text{ as }n\to\infty,\forall t>0$，即$X_n\xrightarrow{d}X$，$X_n\ge0,X\ge0,X_n\le1,X\le1$，证明：$\lim_{n\to\infty}\mathbb{E}X_n=\mathbb{E}X$。

**Proof**

由期望计算公式，这里可以直接使用DCT，这是因为实际上$t\in(0,1)$，
$$
\mathbb{E}[X_n-X]=\int_{0}^{\infty}\mathbb{P}(X_n>t)-\mathbb{P}(X>t){d}t=\int_{0}^{1}\mathbb{P}(X_n>t)-\mathbb{P}(X>t){d}t
$$

**QED**

>[!example] 
>若$\mathbb{P}(X_n>t)\to\mathbb{P}(X>t)\text{ as }n\to\infty,\forall t>0$，$\mathbb{E}[X_n^2]\le1$，证明：$\lim_{n\to\infty}\mathbb{E}X_n=\mathbb{E}X$。

**Proof**

先考虑$X_n,X\ge0$的情况。由Chebyshev不等式，
$$
\mathbb{P}(X_n>t)\le\min\left\{1,\frac{1}{t^2}\right\}\text{ and }\int_{0}^{\infty}\min\left\{1,\frac{1}{t^2}\right\}{d}t=2
$$


**QED**

>[!example] 
>$X_1,\cdots,X_n,i.i.d.$，$\mathbb{E}X_n=0,\mathbb{E}X_n^2=1$，令$S_n=\sum_{i=1}^{n}X_i$，证明：
>$$
>\lim_{n\to\infty}\mathbb{E}\left[\frac{|S_n|}{\sqrt{n}}\right]=\sqrt{\frac{2}{\pi}}=\mathbb{E}[|N|],N\sim \text{N}(0,1)
>$$

