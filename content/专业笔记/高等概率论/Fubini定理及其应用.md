首先回故[[随机变量与分布函数#^bf1fba|乘积空间]]。我们现在的任务是在乘积空间上构造合适的概率测度。一个简单的方法是按照笛卡尔积，分别作用在各自空间相应的集合上。
>[!def] 乘积概率测度
>对$A\times B\in\mathscr{F}_1\otimes\mathscr{F}_2$，定义其上的概率测度为
>$$
>\mathbb{P}_1\otimes\mathbb{P}(A\times B):=\mathbb{P}_1(A)\mathbb{P}_2(B)
>$$
>实际上容易验证$\mathbb{P}_1\otimes\mathbb{P}_2$为$\mathscr{A}$上的测度，其中$\mathscr{A}=\left\{A\times B:A\in\mathscr{F}_1,B\in\mathscr{F}_2\right\}$。根据[[测度论基础#^fa2ae7|Caretheodory延拓定理]]，可以延拓为$\mathscr{F}_1\otimes\mathscr{F}_2$上的测度。

>[!def] 核函数方法（马氏过程）

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


$$

**QED**