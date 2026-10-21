全文 $\log$ 均表示自然对数。
>[!note] 弱大数定律在说什么？
>令
>$$
>S_n=X_1+\cdots+X_n.
>$$
>弱大数定律（Weak Law of Large Numbers，WLLN）的典型结论是
>$$
>\frac{S_n}{n}\xrightarrow{\mathbb P}\mu,
>$$
>也就是对每个 $\varepsilon>0$，
>$$
>\mathbb P\left(\left|\frac{S_n}{n}-\mu\right|>\varepsilon\right)\longrightarrow0
>$$
>样本平均与 $\mu$ 相差超过固定误差的概率，随着样本量增大而趋于 $0$。

>[!note] “弱”指什么？
>这里“弱”指结论采用**依概率收敛**。强大数定律的结论则是
>$$
>\mathbb P\left(\lim_{n\to\infty}\frac{S_n}{n}=\mu\right)=1.
>$$
>几乎处处收敛蕴含依概率收敛，反向一般不成立。WLLN 中的“弱”也不要直接等同于“弱收敛（依分布收敛）”；不过极限为常数时，依分布收敛与依概率收敛等价。

>[!thm] $L^2$ 弱大数定律
>设 $X_1,X_2,\ldots$ 两两不相关，i.e. $\mathbb{E}X_iX_j=\mathbb{E}X_i\mathbb{E}X_j$，且
>$$
>\mathbb E X_i=\mu,\qquad
>\operatorname{Var}(X_i)\le C<\infty,\qquad i\ge1.
>$$
>令 $S_n=\sum_{i=1}^nX_i$，则
>$$
>\frac{S_n}{n}\xrightarrow{L^2}\mu,
>\qquad\text{从而}\qquad
>\frac{S_n}{n}\xrightarrow{\mathbb P}\mu.
>$$

**Proof**

**第一步：计算样本平均的均值。**

由期望的线性性，
$$
\mathbb E\left(\frac{S_n}{n}\right)
=\frac1n\sum_{i=1}^n\mathbb E X_i=\mu.
$$
这一点不需要独立性或不相关性。

**第二步：计算方差，明确不相关性用在哪里。**

一般地，
$$
\begin{aligned}
\operatorname{Var}(S_n)
&=\mathbb E\left[\sum_{i=1}^n(X_i-\mathbb E X_i)\right]^2\\
&=\sum_{i=1}^n\operatorname{Var}(X_i)
+2\sum_{1\le i<j\le n}\operatorname{Cov}(X_i,X_j).
\end{aligned}
$$
两两不相关意味着每个交叉项为 $0$，所以
$$
\operatorname{Var}(S_n)
=\sum_{i=1}^n\operatorname{Var}(X_i)\le nC.
$$
于是
$$
\mathbb E\left|\frac{S_n}{n}-\mu\right|^2=\operatorname{Var}\left(\frac{S_n}{n}\right)=\frac{\operatorname{Var}(S_n)}{n^2}\le\frac{C}{n}\longrightarrow0\text{ as }n\to\infty
$$
这已经证明 $L^2$ 收敛。

**第三步：用 Chebyshev 不等式得到依概率收敛。**

对任意 $\varepsilon>0$，
$$
\mathbb P\left(\left|\frac{S_n}{n}-\mu\right|>\varepsilon\right)
\le\frac1{\varepsilon^2}
\mathbb E\left|\frac{S_n}{n}-\mu\right|^2
\le\frac{C}{n\varepsilon^2}\longrightarrow0.
$$

**QED**

>[!note] 假设可以怎样放宽？
>独立且具有有限二阶矩的变量必然不相关；上面的证明实际上只用到了不相关性。也不要求同分布。
>
>方差一致有界只是一个方便的充分条件。若均值仍为 $\mu$、变量两两不相关，只要
>$$
>\frac1{n^2}\sum_{i=1}^n\operatorname{Var}(X_i)\longrightarrow0,
>$$
>同样成立。更一般地，只要
>$$
>\frac{\mathbb E S_n}{n}\longrightarrow\mu,\qquad
>\frac{\operatorname{Var}(S_n)}{n^2}\longrightarrow0,
>$$
>就有 $S_n/n\to\mu$ 于 $L^2$；因为均方误差等于“方差加偏差的平方”。

>[!thm] Bernstein 多项式逼近
>设 $f\in C([0,1])$，定义
>$$
>f_n(x)=\sum_{m=0}^n
>\binom nm x^m(1-x)^{n-m}f\left(\frac mn\right).
>$$
>则 $f_n$ 是次数不超过 $n$ 的多项式，并且
>$$
>\|f_n-f\|_\infty
>=\sup_{x\in[0,1]}|f_n(x)-f(x)|
>\longrightarrow0.
>$$
>因此得到 Weierstrass 逼近定理在 $[0,1]$ 上的一种概率证明。

**Proof**

**第一步：把多项式写成期望。**

固定 $p\in[0,1]$。取独立同分布的 Bernoulli$(p)$ 随机变量 $X_1,\ldots,X_n$，令 $S_n=\sum_{i=1}^nX_i$。则
$$
S_n\sim\operatorname{B}(n,p),\qquad
\mathbb P(S_n=m)=\binom nm p^m(1-p)^{n-m}.
$$
故
$$
\mathbb E f\left(\frac{S_n}{n}\right)
=\sum_{m=0}^n\mathbb P(S_n=m)f\left(\frac mn\right)
=f_n(p).
$$
$p=0,1$ 时，二项分布退化，分别直接有 $f_n(0)=f(0)$、$f_n(1)=f(1)$。

**第二步：使用与 $p$ 无关的方差上界。**

由于
$$
\mathbb E X_i=p,\qquad\operatorname{Var}(X_i)=p(1-p),
$$
Chebyshev 不等式给出：对每个 $\delta>0$，
$$
\mathbb P\left(\left|\frac{S_n}{n}-p\right|\ge\delta\right)
\le\frac{p(1-p)}{n\delta^2}
\le\frac1{4n\delta^2}.
\tag{W1}
$$
最后一个上界对所有 $p\in[0,1]$ 同时成立，是从逐点逼近提升到一致逼近的关键。

**第三步：把误差分成靠近 $p$ 和远离 $p$ 两部分。**

因为 $f$ 在紧区间上连续，所以它有界且一致连续。令
$$
M=\|f\|_\infty<\infty.
$$
给定 $\eta>0$，可取 $\delta>0$，使得对所有 $x,y\in[0,1]$，
$$
|x-y|<\delta\quad\Longrightarrow\quad |f(x)-f(y)|<\eta.
$$
这个 $\delta$ 不依赖 $p$。设
$$
A_{n,p}=\left\{\left|\frac{S_n}{n}-p\right|<\delta\right\}.
$$
在 $A_{n,p}$ 上函数值之差至多 $\eta$；在补集上至多 $2M$。因此
$$
\begin{aligned}
|f_n(p)-f(p)|
&=\left|\mathbb E\left[f(S_n/n)-f(p)\right]\right|\\
&\le\mathbb E\left|f(S_n/n)-f(p)\right|\\
&\le\eta\,\mathbb P(A_{n,p})+2M\,\mathbb P(A_{n,p}^c)\\
&\le\eta+\frac{M}{2n\delta^2}.
\end{aligned}
$$
对 $p$ 取上确界，
$$
\|f_n-f\|_\infty\le\eta+\frac{M}{2n\delta^2}.
$$
固定 $\eta$ 及其对应的 $\delta$，先令 $n\to\infty$，得
$$
\limsup_{n\to\infty}\|f_n-f\|_\infty\le\eta.
$$
再令 $\eta\downarrow0$，得到一致收敛。

**QED**

>[!def] 三角阵及行和
>三角阵是如下形式的随机变量族：
>$$
>\begin{matrix}
>X_{1,1}\\
>X_{2,1}&X_{2,2}\\
>X_{3,1}&X_{3,2}&X_{3,3}\\
>\vdots&\vdots&\vdots&\ddots
>\end{matrix}
>\qquad X_{n,k},\quad1\le k\le n.
>$$
>$n$ 是行号，$k$ 是该行中的位置。第 $n$ 行的和为
>$$
>S_n=\sum_{k=1}^nX_{n,k}.
>$$
>“行内独立”表示对每个固定 $n$，$X_{n,1},\ldots,X_{n,n}$ 相互独立；不要求不同行之间独立。

普通部分和是特殊情形 $X_{n,k}=X_k$。对一般三角阵，第 $n$ 行前 $n-1$ 项未必等于上一行，因此通常不能写
$$
S_n-S_{n-1}=X_{n,n}.
$$

>[!proposition] 三角阵行和的方差判据
>设 $S_n$ 具有有限二阶矩，记
>$$
>\mu_n=\mathbb E S_n,\qquad
>\sigma_n^2=\operatorname{Var}(S_n).
>$$
>若确定的数列 $b_n>0$ 满足
>$$
>\frac{\sigma_n^2}{b_n^2}\longrightarrow0,\tag{技术性条件}
>$$
>则
>$$
>\frac{S_n-\mu_n}{b_n}\xrightarrow{L^2}0,
>\qquad
>\frac{S_n-\mu_n}{b_n}\xrightarrow{\mathbb P}0.
>$$

**Proof**

直接计算
$$
\mathbb E\left|\frac{S_n-\mu_n}{b_n}\right|^2
=\frac{\operatorname{Var}(S_n)}{b_n^2}
=\frac{\sigma_n^2}{b_n^2}\longrightarrow0.
$$
再用 Chebyshev 不等式，
$$
\mathbb P\left(\left|\frac{S_n-\mu_n}{b_n}\right|>\varepsilon\right)
\le\frac{\sigma_n^2}{\varepsilon^2b_n^2}\longrightarrow0.
$$

**QED**

>[!example] 均匀集券模型
>固定 $n$ 种券，每次独立、等概率抽取一种。令
>$$
>\xi_1,\xi_2,\ldots\overset{\mathrm{i.i.d.}}{\sim}
>\operatorname{Unif}\{1,\ldots,n\}.
>$$
>为避免与等待时间 $X_{n,k}$ 混淆，用 $\xi_m$ 表示第 $m$ 次抽到的券种。定义
>$$
>\tau_k^n
>=\min\{m\ge0:\#\{\xi_1,\ldots,\xi_m\}\ge k\},
>\qquad 1\le k\le n,
>$$
>并约定 $\tau_0^n=0$，因此 $\tau_1^n=1$。令
>$$
>X_{n,k}=\tau_k^n-\tau_{k-1}^n,\qquad
>S_n=\sum_{k=1}^nX_{n,k}=\tau_n^n.
>$$
>$X_{n,k}$ 表示从已有 $k-1$ 种券到首次集齐 $k$ 种券，还要抽取的次数；$S_n$ 是集齐全部券的总次数。
>
>结论为
>$$
>\frac{S_n}{n\log n}\xrightarrow{\mathbb P}1
>\qquad(n\to\infty).
>$$

**Proof**

**第一步：等待时间服从几何分布。**

当已经集齐 $k-1$ 种券时，尚缺 $n-k+1$ 种，所以每次抽到新券的概率为
$$
p_{n,k}=\frac{n-k+1}{n}=1-\frac{k-1}{n}.
$$
在等到下一种新券之前，已收集的券种集合保持不变。连续 $r-1$ 次抽到旧券、然后抽到新券的概率为
$$
(1-p_{n,k})^{r-1}p_{n,k},\qquad r=1,2,\ldots.
$$
因此
$$
X_{n,k}\sim\operatorname{Geo}(p_{n,k}),
$$
采用取值在 $\{1,2,\ldots\}$ 上的几何分布约定。$k=1$ 时 $p_{n,1}=1$，$X_{n,1}=1$ 是退化情形。因为 $p_{n,k}>0$，每阶段无限等待的概率为 $\lim_{r\to\infty}(1-p_{n,k})^r=0$，所以各 $\tau_k^n$ 几乎必然有限。

**第二步：为什么各阶段的等待时间相互独立？**

仅说“使用了不同时间段的抽样”还不充分，因为时间段的端点是随机的。需要说明给定过去后，下一段等待时间的分布不变。

固定 $k\ge2$，考虑截至 $\tau_{k-1}^n$ 的任意可能抽样记录
$$
\xi_1=a_1,\ldots,\xi_t=a_t,\qquad \tau_{k-1}^n=t.
$$
这段记录确定了一个大小恰为 $k-1$ 的已收集集合 $D$。由于后续抽样独立于前 $t$ 次抽样，
$$
\begin{aligned}
&\mathbb P\bigl(
\xi_{t+1},\ldots,\xi_{t+r-1}\in D,\ \xi_{t+r}\notin D
\mid\text{上述记录}\bigr)\\
&\qquad=\left(\frac{k-1}{n}\right)^{r-1}\frac{n-k+1}{n}.
\end{aligned}
$$
右端只依赖 $n,k,r$，不依赖具体记录、$t$ 或集合 $D$ 的内容。

对所有与某个过去事件 $H$ 相容的有限记录求和，就得到
$$
\mathbb P(H\cap\{X_{n,k}=r\})
=\mathbb P(H)(1-p_{n,k})^{r-1}p_{n,k}.
$$
特别地，可取
$$
H=\{X_{n,1}=r_1,\ldots,X_{n,k-1}=r_{k-1}\}.
$$
故 $X_{n,k}$ 独立于此前全部等待时间。逐步使用这个乘积公式，得到整行
$$
X_{n,1},\ldots,X_{n,n}
$$
相互独立。由于这些变量取可数个值，逐点联合概率分解就足以证明独立性。

**第三步：计算几何分布的矩。**

若 $Y\sim\operatorname{Geo}(p)$，$q=1-p$，则
$$
\mathbb E z^Y=\sum_{r=1}^\infty p q^{r-1}z^r
=\frac{pz}{1-qz}.
$$
在 $z=1$ 处求一阶、二阶导数，得到
$$
\mathbb E Y=\frac1p,\qquad
\mathbb E[Y(Y-1)]=\frac{2q}{p^2}.
$$
从而
$$
\mathbb E Y^2=\frac{2-p}{p^2},\qquad
\operatorname{Var}(Y)=\frac{1-p}{p^2}\le\frac1{p^2}.
$$
$p=1$ 时也直接成立。

**第四步：估计总等待时间的均值和方差。**

记调和数
$$
H_n=\sum_{m=1}^n\frac1m.
$$
换元 $m=n-k+1$，
$$
\mu_n=\mathbb E S_n
=\sum_{k=1}^n\frac1{p_{n,k}}
=n\sum_{m=1}^n\frac1m=nH_n.
$$
由积分比较，
$$
\log(n+1)\le H_n\le1+\log n,
$$
所以 $H_n/\log n\to1$，即 $\mu_n\sim n\log n$。

再由独立性，
$$
\begin{aligned}
\sigma_n^2=\operatorname{Var}(S_n)
&=\sum_{k=1}^n\frac{1-p_{n,k}}{p_{n,k}^2}\\
&=\sum_{m=1}^n\left(\frac{n^2}{m^2}-\frac nm\right)\\
&=n^2\sum_{m=1}^n\frac1{m^2}-nH_n\\
&\le n^2\sum_{m=1}^\infty\frac1{m^2}
=\frac{\pi^2}{6}n^2.
\end{aligned}
$$

**第五步：归一化并应用方差判据。**

取 $b_n=n\log n$（以下 $n\ge2$），则
$$
\frac{\sigma_n^2}{b_n^2}
\le\frac{\pi^2}{6(\log n)^2}\longrightarrow0.
$$
因此
$$
\frac{S_n-\mathbb E S_n}{n\log n}\xrightarrow{\mathbb P}0.
$$
再利用 $\mathbb E S_n/(n\log n)=H_n/\log n\to1$，
$$
\boxed{\frac{S_n}{n\log n}\xrightarrow{\mathbb P}1.}
$$
实际上该证明还给出 $L^2$ 收敛，因为
$$
\mathbb E\left|\frac{S_n}{n\log n}-1\right|^2
=\frac{\sigma_n^2}{n^2(\log n)^2}
+\left(\frac{H_n}{\log n}-1\right)^2\longrightarrow0.
$$

**QED**

>[!note] 为什么是 $n\log n$，不是 $n$？
>已经集齐 $n-m$ 种时，找到下一种新券的平均等待时间为 $n/m$。最后一种平均就要等 $n$ 次；所有阶段的等待时间相加为
>$$
>n+\frac n2+\cdots+\frac nn=nH_n\sim n\log n.
>$$
>WLLN 还说明随机总时间相对于这个尺度的波动趋于零，而不仅是期望具有该量级。

>[!example] 均匀随机置换的循环数
>
设
$$
\begin{array}{c|ccccccccc}
i&1&2&3&4&5&6&7&8&9\\ \hline
\pi(i)&3&9&6&8&2&1&5&4&7
\end{array}.
$$
从 $1$ 开始追踪其像：
$$
1\to3\to6\to1.
$$
再从未出现的最小元素 $2$ 开始：
$$
2\to9\to7\to5\to2.
$$
最后是 $4\to8\to4$。因此
$$
\boxed{\pi=(1\,3\,6)(2\,9\,7\,5)(4\,8).}
$$
循环内部可以循环移位，例如 $(2\,9\,7\,5)=(9\,7\,5\,2)$；一般不能任意倒序。按手稿的映射表，第二个循环应为 $(2\,9\,7\,5)$，不能写成 $(2\,5\,7\,9)$。

以下规定：每个循环从其中最小元素写起，各循环按最小元素递增排列。这样每个置换都有唯一的书写方式。

>从 $\{1,\ldots,n\}$ 的 $n!$ 个置换中等概率选取 $\pi$。按照上述规则逐个写出循环分解中的 $n$ 个元素，定义
>$$
>X_{n,k}
>=\mathbf1_{\{\text{第 }k\text{ 个写出的元素恰好结束一个循环}\}},
>\qquad1\le k\le n.
>$$
>这里 $k$ 指书写位置，不一定等于元素的数值。循环总数为
>$$
>S_n=\sum_{k=1}^nX_{n,k}.
>$$
>则 $X_{n,1},\ldots,X_{n,n}$ 相互独立，且
>$$
>\mathbb P(X_{n,k}=1)=\frac1{n-k+1}.
>$$
>由此
>$$
>\frac{S_n}{\log n}\xrightarrow{\mathbb P}1.
>$$

本节重新用 $X_{n,k},S_n$ 表示循环指标和循环数，与上节集券等待时间是不同模型。对上面的 $n=9$ 例子，循环分别在第 $3,7,9$ 个书写位置结束，故 $X_{9,3}=X_{9,7}=X_{9,9}=1$，其他指标为 $0$。

**Proof**

**第一步：逐步生成均匀随机置换。**

先写下 $1$，开始第一个循环。假设目前已累计写出 $k$ 个元素，当前未闭合循环的起点为 $s$、末尾元素为 $a$，并已决定了前 $k-1$ 个箭头。

为了决定 $\pi(a)$，可以选择的像恰好是：

- 尚未写出的 $n-k$ 个元素；
- 当前循环起点 $s$。

已经闭合的循环中的元素，以及当前循环中除 $s$ 外的元素，都已经有前驱，不能再选作像。故合法选择共 $n-k+1$ 个。

在这些合法选择中均匀选一个。若选中尚未写出的元素，就把它接到当前循环末尾；若选中 $s$，则闭合当前循环，并在仍有未写元素时，用其中最小的一个开启下一循环。

每个指定置换都对应唯一的一串选择，所以它被生成的概率为
$$
\prod_{k=1}^n\frac1{n-k+1}=\frac1{n!}.
$$
因此这确实生成均匀随机置换。

**第二步：证明闭合指标相互独立。**

令 $\mathscr H_{n,k-1}$ 表示决定第 $k$ 个箭头之前已经知道的全部生成历史。此时 $n-k+1$ 个合法选择中，恰好只有选择 $s$ 会闭合循环，所以
$$
\mathbb P(X_{n,k}=1\mid\mathscr H_{n,k-1})
=\frac1{n-k+1}.
\tag{W2}
$$
右端是确定的常数，不依赖具体历史。因此 $X_{n,k}$ 独立于此前的指标。

具体地，记 $p_{n,k}=1/(n-k+1)$。对 $x_1,\ldots,x_n\in\{0,1\}$，用条件概率逐步迭代，
$$
\mathbb P(X_{n,1}=x_1,\ldots,X_{n,n}=x_n)
=\prod_{k=1}^n
\mathbb P(X_{n,k}=x_k),
$$
其中边际为 Bernoulli$(p_{n,k})$。最后一步 $p_{n,n}=1$，即最后一个循环必然闭合。整行指标的独立性得证。

**第三步：计算矩并应用方差判据。**

仍记 $H_n=\sum_{m=1}^n1/m$。则
$$
\mu_n=\mathbb E S_n
=\sum_{k=1}^n\frac1{n-k+1}=H_n\sim\log n.
$$
又由独立性，
$$
\begin{aligned}
\sigma_n^2=\operatorname{Var}(S_n)
&=\sum_{k=1}^n p_{n,k}(1-p_{n,k})\\
&=H_n-\sum_{m=1}^n\frac1{m^2}
\le H_n.
\end{aligned}
$$
取 $b_n=\log n$（$n\ge2$），则
$$
\frac{\sigma_n^2}{b_n^2}
\le\frac{H_n}{(\log n)^2}\longrightarrow0.
$$
因此
$$
\frac{S_n-H_n}{\log n}\xrightarrow{\mathbb P}0,\qquad
\frac{H_n}{\log n}\longrightarrow1,
$$
合起来得到
$$
\boxed{\frac{S_n}{\log n}\xrightarrow{\mathbb P}1.}
$$
同集券问题一样，这里也得到 $L^2$ 收敛。

**QED**

