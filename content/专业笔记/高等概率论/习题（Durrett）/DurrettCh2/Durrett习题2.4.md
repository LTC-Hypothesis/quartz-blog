> [!info] 作业批改
> <span style="color:#ef5350;">总分：80 / 100 分。范围：本笔记中 6 份已写答案（按题／小问计），按原稿评分。</span>
> <span style="color:#ef5350;">满分分配：2.4.1、2.4.2 各 20 分；2.4.3(i)–(iv) 依次为 15、15、10、20 分。原文全部保留，仅增红字评分与必要补证；一般英文措辞不扣分，同源错误不重复扣分。</span>

> [!question] 2.4.1. **Lazy janitor.**
> Suppose the $i$th light bulb burns for an amount of time $X_i$ and then remains burned out for time $Y_i$ before being replaced. Suppose the $X_i, Y_i$ are positive and independent with the $X$'s having distribution $F$ and the $Y$'s having distribution $G$, both of which have finite mean. Let $R_t$ be the amount of time in $[0, t]$ that we have a working light bulb. Show that $R_t/t \to \mathbb{E}X_i/(\mathbb{E}X_i + \mathbb{E}Y_i)$ almost surely.

> [!done]
>
> <span style="color:#ef5350;">【评分】20 / 20 分。证明正确。</span>
>
> We should note the procedure of the problem, 
> $$
> \text{i th bulb works} \xrightarrow{X_i\text{ times }}\text{ burn }\xrightarrow{Y_i \text{wait time}}\text{i+1 th bulb works}
> $$
> Let $T_n$ be the time from 1 th bulb works to n+1 th bulb begin to work. Then 
> $$
> T_n=\sum_{i=1}^{n}X_i+\sum_{i=1}^{n}Y_i
> $$
> Let $R_{T_n}$ be the amout of time in $[0,T_n]$ that we have a working bulb, which is that 
> $$
> R_{T_n}=\sum_{i=1}^{n}X_i\Longrightarrow\text{ by SLLN }\frac{R_{T_n}}{T_n}\xrightarrow{a.s.}\frac{\mathbb{E}X}{\mathbb{E}(X+Y)}
> $$
> For each time $t$, there exists $T-n\le t<T_{n+1}$, we have 
> $$
> \frac{R_{T_n}}{T_n}\frac{T_n}{T_{n+1}}=\frac{R_{T_n}}{T_{n+1}}\le\frac{R_t}{t}\le\frac{R_{T_{n+1}}}{T_n}=\frac{R_{T_{n+1}}}{T_{n+1}}\frac{T_{n+1}}{T_{n}}
> $$
> and 
> $$
> \frac{T_{n+1}}{T_n}=\frac{\frac{n+1}{n}\frac{1}{n+1}\sum_{i=1}^{n+1}(X_i+Y_i)}{\frac{1}{n}\sum_{i=1}^{n}(X_i+Y_i)}\to1
> $$
> Hence, 
> $$
> \frac{R_t}{t}\xrightarrow{a.s.}\frac{\mathbb{E}X}{\mathbb{E}(X+Y)}
> $$
>
> <span style="color:#ef5350;">【补充，不扣分】周期端点、夹逼及相邻时间比值均正确。补明 </span>$\color{#ef5350}{T_n/n\to\mathbb E(X+Y)>0}$<span style="color:#ef5350;">，因此 </span>$\color{#ef5350}{T_n\to\infty}$<span style="color:#ef5350;">，且 </span>$\color{#ef5350}{t\to\infty}$<span style="color:#ef5350;"> 时对应的 </span>$\color{#ef5350}{n(t)\to\infty}$<span style="color:#ef5350;">；夹逼只需用于 </span>$\color{#ef5350}{t\ge T_1}$<span style="color:#ef5350;">。原文 </span>$\color{#ef5350}{T-n}$<span style="color:#ef5350;"> 是 </span>$\color{#ef5350}{T_n}$<span style="color:#ef5350;"> 的笔误。</span>


> [!question] 2.4.2.
> Let $X_0 = (1,0)$ and define $X_n \in \mathbf{R}^2$ inductively by declaring that $X_{n+1}$ is chosen at random from the ball of radius $|X_n|$ centered at the origin, i.e., $X_{n+1}/|X_n|$ is uniformly distributed on the ball of radius 1 and independent of $X_1, \dots, X_n$. Prove that $n^{-1} \log |X_n| \to c$ a.s. and compute $c$.

> [!done]
>
> <span style="color:#ef5350;">【评分】15 / 20 分。扣分及修正见下方红字。</span>
>
> Let $Y_n:=\frac{X_{n+1}}{|X_n|}\Longrightarrow X_{n+1}=|X_n|Y_n\Longrightarrow |X_{n+1}|=|X_n||Y_n|\Longrightarrow\log|Y_n|=\log|X_{n+1}|-\log|X_n|$. Since $|X_0|=1,\log|X_0|=0$, we have 
> $$
> \frac{1}{n}\log|X_n|=\frac{1}{n}\sum_{i=1}^{n}\log|Y_i|
> $$
> Note that $|Y_i|$ are independent. We compute the expectation, 
> $$
> \begin{aligned}
>\mathbb{E}\log|Y_1|&=\int_{B(0,1)}\frac{1}{\pi}\log{\sqrt{y_1^2+y_2^2}}{d}y_1{d}y_2\\
>&=2\int_{0}^{1}r\log{r}{d}r=-\frac{1}{2}
>\end{aligned}
> $$
> By SLLN, 
> $$
> \frac{1}{n}\sum_{i=1}^{n}\log|Y_i|\xrightarrow{a.s.}-\frac{1}{2}
> $$
>
> <span style="color:#ef5350;">【下标，−1分】按开头 </span>$\color{#ef5350}{Y_n=X_{n+1}/|X_n|}$<span style="color:#ef5350;"> 的定义，望远镜求和应为 </span>$\color{#ef5350}{\frac1n\log|X_n|=\frac1n\sum_{i=0}^{n-1}\log|Y_i|}$<span style="color:#ef5350;">。</span>
>
> <span style="color:#ef5350;">【密度与常数，−4分】单位圆盘的均匀密度是 </span>$\color{#ef5350}{1/\pi}$<span style="color:#ef5350;">，原积分漏了此因子。因此 </span>$\color{#ef5350}{\mathbb E\log|Y_1|=2\int_0^1r\log r\,dr=-1/2}$<span style="color:#ef5350;">，最终 </span>$\color{#ef5350}{c=-1/2}$<span style="color:#ef5350;">。同时 </span>$\color{#ef5350}{\mathbb E|\log|Y_1||=1/2<\infty}$<span style="color:#ef5350;">，可使用 SLLN。此处及末行的错误常数属同源错误，只扣一次。</span>


> [!question] 2.4.3. **Investment problem.**(i)
>  We assume that at the beginning of each year you can buy bonds for $\$1$ that are worth $\$ a$ at the end of the year or stocks that are worth a random amount $V \geq 0$. If you always invest a fixed proportion $p$ of your wealth in bonds, then your wealth at the end of year $n+1$ is $W_{n+1} = (ap + (1 - p)V_n)W_n$. Suppose $V_1, V_2, \dots$ are i.i.d. with $\mathbb{E}V_n^2 < \infty$ and $\mathbb{E}(V_n^{-2}) < \infty$.
>   (i) Show that $n^{-1} \log W_n \to c(p)$ a.s.

> [!done]
>
> <span style="color:#ef5350;">【评分】12 / 15 分。扣分及修正见下方红字。</span>
>
> Note that $\log{W_{n+1}}-\log{W_n}=\log\left(ap+(1-p)V_n\right),W_1=1$, and thus 
> $$
> \frac{1}{n}\log{W_n}=\frac{1}{n}\sum_{i=1}^{n-1}\log{(ap+(1-p)V_i)}
> $$
> By SLLN, we have 
> $$
> \frac{1}{n}\sum_{i=1}^{n-1}\log{(ap+(1-p)V_i)}\xrightarrow{a.s}\mathbb{E}\log(ap+(1-p)V_1):=c(p)
> $$
>
> <span style="color:#ef5350;">【补证，−3分】需先验证对数可积。对 </span>$\color{#ef5350}{a>0}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{0\le p\le1}$<span style="color:#ef5350;">，</span>
> $$
> \color{#ef5350}{|\log(ap+(1-p)V)|\le|\log a|+|\log V|\le|\log a|+V+V^{-1}.}
> $$
> <span style="color:#ef5350;">右端由题设的二阶正、负矩条件可积，故可用 SLLN。</span>$\color{#ef5350}{W_1=1}$<span style="color:#ef5350;"> 可视为财富单位归一化，不扣分。</span>


> [!question] 2.4.3. (ii)
> (ii) Show that $c(p)$ is concave. [Use Theorem A.5.1 in the Appendix to justify differentiating under the expected value.]

> [!done]
>
> <span style="color:#ef5350;">【评分】11 / 15 分。扣分及修正见下方红字。</span>
>
> We compute directly, 
> $$
> c'(p)=\mathbb{E}\frac{a-V_1}{ap+(1-p)V_1},c''(p)=\mathbb{E}\frac{-(a-V_1)^2}{(ap+(1-p)V_1)^2}\le0\Longrightarrow c(p)\text{ is concave}
> $$
>
> <span style="color:#ef5350;">【补证，−4分】导数及凹性结论正确，但需按题意说明微分与期望可交换。令 </span>$\color{#ef5350}{q_p=ap+(1-p)V}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{B=a/V+V/a}$<span style="color:#ef5350;">，则对 </span>$\color{#ef5350}{0\le p\le1}$<span style="color:#ef5350;">，</span>
> $$
> \color{#ef5350}{\begin{aligned}|\partial_p\log q_p|&\le B,\qquad |\partial_p^2\log q_p|\le B^2,\\\mathbb EB^2&=a^2\mathbb EV^{-2}+2+a^{-2}\mathbb EV^2<\infty.\end{aligned}}
> $$
> <span style="color:#ef5350;">因此可由 A.5.1 两次交换微分与期望；端点导数按单侧理解。</span>


> [!question] 2.4.3. (iii)
> (iii) By investigating $c'(0)$ and $c'(1)$, give conditions on $V$ that guarantee that the optimal choice of $p$ is in $(0,1)$.

> [!done]
>
> <span style="color:#ef5350;">【评分】10 / 10 分。端点导数与内部最优的充分条件正确。</span>
>
> We compute 
> $$
> c'(0)=\mathbb{E}\frac{a-V_1}{V_1},c'(1)=\mathbb{E}\frac{a-V_1}{a}
> $$
> We give $c'(0)>0,c'(1)<0\Longleftrightarrow\mathbb{E}\frac{1}{V}>\frac{1}{a},\mathbb{E}V>a$, which guarantee that the optimal choice of $p$. 

> [!question] 2.4.3. (iv)
> (iv) Suppose $\mathbb{P}(V = 1) = \mathbb{P}(V = 4) = 1/2$. Find the optimal $p$ as a function of $a$.

> [!done]
>
> <span style="color:#ef5350;">【评分】12 / 20 分。扣分及修正见下方红字。</span>
>
> Let $c'(p)=0$, we have 
> $$
> \frac{1}{2}\cdot\frac{a-1}{ap+(1-p)}+\frac{1}{2}\frac{a-4}{ap+4(1-p)}=0\Longrightarrow p=\frac{8-5a}{2(a-1)(a-4)},\frac{8}{5}<a<\frac{5}{2}
> $$
>
> <span style="color:#ef5350;">【补全，−8分】内部驻点及其区间正确（分别得 8 分、4 分）；遗漏两个边界范围（各扣 4 分）。由 </span>$\color{#ef5350}{c'(0)=5a/8-1}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{c'(1)=1-5/(2a)}$<span style="color:#ef5350;"> 及严格凹性，完整答案为</span>
> $$
> \color{#ef5350}{p^*(a)=\begin{cases}0,&0<a\le\frac85,\\[3pt]\dfrac{8-5a}{2(a-1)(a-4)},&\frac85<a<\frac52,\\[5pt]1,&a\ge\frac52.\end{cases}}
> $$
