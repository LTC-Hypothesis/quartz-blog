>[!note] 2026.10.20 手稿整理
>本篇对应手稿第 4–6 页，沿用 $X_i,S_n,\mu,C$ 及三角阵 $X_{n,k}$、集券时刻 $\tau_k^n$ 等记号。包括 $L^2$ 弱大数定律、Bernstein 多项式、三角阵、集券问题及随机置换循环分解。最后补充截断法和仅要求一阶绝对矩有限的经典 WLLN；补充出处列于文末。
>
>相容性定理及独立变量的构造见 [[独立性#Kolmogorov 相容性定理]]。

全文 $\log$ 均表示自然对数。

## 1. 弱大数定律在说什么？

令
$$
S_n=X_1+\cdots+X_n.
$$
弱大数定律（Weak Law of Large Numbers，WLLN）的典型结论是
$$
\frac{S_n}{n}\xrightarrow{\mathbb P}\mu,
$$
也就是对每个 $\varepsilon>0$，
$$
\mathbb P\left(\left|\frac{S_n}{n}-\mu\right|>\varepsilon\right)
\longrightarrow0.
$$
样本平均与 $\mu$ 相差超过固定误差的概率，随着样本量增大而趋于 $0$。

>[!note] “弱”指什么？
>这里“弱”指结论采用**依概率收敛**。强大数定律的结论则是
>$$
>\mathbb P\left(\lim_{n\to\infty}\frac{S_n}{n}=\mu\right)=1.
>$$
>几乎处处收敛蕴含依概率收敛，反向一般不成立。WLLN 中的“弱”也不要直接等同于“弱收敛（依分布收敛）”；不过极限为常数时，依分布收敛与依概率收敛等价。

## 2. 方差方法：$L^2$ 弱大数定律

>[!thm] 不相关且方差一致有界的 WLLN
>设 $X_1,X_2,\ldots$ 两两不相关，且
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
\mathbb E\left|\frac{S_n}{n}-\mu\right|^2
=\operatorname{Var}\left(\frac{S_n}{n}\right)
=\frac{\operatorname{Var}(S_n)}{n^2}
\le\frac Cn\longrightarrow0.
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

## 3. 应用：Bernstein 多项式与一致逼近

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
S_n\sim\operatorname{Bin}(n,p),\qquad
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

>[!note] 这里不能省略的一步
>固定 $p$ 后，WLLN 可以说明 $S_n/n\to p$，再结合有界连续性可推出 $f_n(p)\to f(p)$。但这只给出逐点收敛。要证明一致收敛，必须给出同时适用于所有 $p$ 的误差控制；这里依靠 $p(1-p)\le1/4$ 以及 $f$ 的一致连续性。

## 4. 三角阵与一般的方差判据

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
>\frac{\sigma_n^2}{b_n^2}\longrightarrow0,
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

该判据本身不需要独立性；独立性通常用来计算
$$
\sigma_n^2=\sum_{k=1}^n\operatorname{Var}(X_{n,k}).
$$
如果还知道 $\mu_n/b_n\to a$，则
$$
\frac{S_n}{b_n}
=\frac{S_n-\mu_n}{b_n}+\frac{\mu_n}{b_n}
\longrightarrow a
$$
于 $L^2$，从而也依概率收敛。后面的两个例子都按这个顺序处理。

## 5. 集券问题：集齐 $n$ 种券要多久？

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

>[!note] 参考讲义的一处笔误
>李立颖讲义第 40 页此处写为 $\mathbb E Y^2\le1/p^2$，该式一般不成立。后续方差估计实际需要、并且正确的是
>$$
>\operatorname{Var}(Y)\le1/p^2.
>$$
>例如 $p=1/2$ 时，$\mathbb E Y^2=6$，而 $1/p^2=4$。

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

## 6. 随机置换的循环数

手稿最后开始讨论循环分解；以下依据 Durrett Example 2.2.8 和 Lemma 2.2.9 补全其概率模型及大数定律。

### 6.1 先看手稿中的置换

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

### 6.2 用独立指标表示循环数

>[!example] 均匀随机置换的循环数
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

>[!note] 与 Rényi 破纪录问题的联系（补充）
>[[独立性#^renyi-record|Rényi 破纪录问题]]中，第 $k$ 次刷新纪录的指标相互独立，成功概率为 $1/k$。把本节指标反向编号后，成功概率也为 $1/k$。
>
>因此前 $n$ 次独立同分布连续观测的纪录总数，与 $n$ 元均匀置换的循环数**同分布**，均值和方差都分别为
>$$
>H_n,\qquad H_n-\sum_{k=1}^n\frac1{k^2}.
>$$
>这是一种分布上的联系，并不意味着两个不同模型中的随机变量天然逐点相等。

## 7. 补充：截断法与仅有一阶矩的 WLLN

前面的方差方法要求处理的变量具有有限二阶矩。若只知道 $\mathbb E|X_1|<\infty$，可以先截断变量，控制截断改变样本的概率，再对截断后的和使用方差估计。

### 7.1 截断三角阵

>[!thm] 三角阵的截断型弱大数定律
>对每个 $n$，设 $X_{n,1},\ldots,X_{n,n}$ 相互独立。取 $b_n>0$ 且 $b_n\to\infty$，定义
>$$
>\overline X_{n,k}
>=X_{n,k}\mathbf1_{\{|X_{n,k}|\le b_n\}},
>\qquad
>a_n=\sum_{k=1}^n\mathbb E\overline X_{n,k}.
>$$
>若
>$$
>\sum_{k=1}^n\mathbb P(|X_{n,k}|>b_n)\longrightarrow0,
>\tag{T1}
>$$
>且
>$$
>\frac1{b_n^2}\sum_{k=1}^n
>\mathbb E\overline X_{n,k}^{\,2}\longrightarrow0,
>\tag{T2}
>$$
>则对 $S_n=\sum_{k=1}^nX_{n,k}$，
>$$
>\frac{S_n-a_n}{b_n}\xrightarrow{\mathbb P}0.
>$$

注意 $a_n$ 是**截断后**的均值之和，不一定等于 $\mathbb E S_n$；原变量的期望甚至可能不存在。

**Proof**

令 $\overline S_n=\sum_{k=1}^n\overline X_{n,k}$。对任意 $\varepsilon>0$，
$$
\mathbb P\left(\left|\frac{S_n-a_n}{b_n}\right|>\varepsilon\right)
\le
\mathbb P(S_n\ne\overline S_n)
+
\mathbb P\left(\left|\frac{\overline S_n-a_n}{b_n}\right|>\varepsilon\right).
\tag{T3}
$$
这个估计来自事件包含：如果 $S_n=\overline S_n$，第一个和偏离 $a_n$ 就等价于截断和偏离 $a_n$。

对于第一项，只有至少一个变量被截断，两个和才可能不同，故
$$
\mathbb P(S_n\ne\overline S_n)
\le\mathbb P\left(\bigcup_{k=1}^n\{|X_{n,k}|>b_n\}\right)
\le\sum_{k=1}^n\mathbb P(|X_{n,k}|>b_n)\longrightarrow0.
$$
这里使用不等号：即使有变量被截断，其改变也可能相互抵消。

对于第二项，$\overline X_{n,k}$ 是分别作用于各 $X_{n,k}$ 的可测函数，因此仍然行内独立，且
$$
\mathbb E\overline S_n=a_n,\qquad
\operatorname{Var}(\overline S_n)
=\sum_{k=1}^n\operatorname{Var}(\overline X_{n,k})
\le\sum_{k=1}^n\mathbb E\overline X_{n,k}^{\,2}.
$$
由 Chebyshev 不等式，
$$
\mathbb P\left(\left|\frac{\overline S_n-a_n}{b_n}\right|>\varepsilon\right)
\le\frac1{\varepsilon^2b_n^2}
\sum_{k=1}^n\mathbb E\overline X_{n,k}^{\,2}
\longrightarrow0.
$$
代入式 $(\mathrm{T3})$ 即得结论。

**QED**

>[!note] 两个条件分别控制什么？
>$(\mathrm{T1})$ 控制“有样本越过截断阈值”的概率；$(\mathrm{T2})$ 控制截断和相对于 $b_n$ 的波动。保留的部分必须是 $\{|X_{n,k}|\le b_n\}$；讲义第 40 页式 (4.9) 中指标函数上的不等号有笔误，应以其分段定义为准。

### 7.2 独立同分布且可积的 WLLN

>[!thm] 经典弱大数定律
>若 $X_1,X_2,\ldots$ 独立同分布，且
>$$
>\mathbb E|X_1|<\infty,\qquad \mu=\mathbb E X_1,
>$$
>则
>$$
>\frac{X_1+\cdots+X_n}{n}\xrightarrow{\mathbb P}\mu.
>$$
>这里不要求 $\mathbb E X_1^2<\infty$。

**Proof**

在截断三角阵定理中取
$$
X_{n,k}=X_k,\qquad b_n=n,\qquad
\overline X_{n,k}=X_k\mathbf1_{\{|X_k|\le n\}}.
$$
分三步核对。

**第一步：大值出现的总概率趋于零。**

由同分布性，
$$
\begin{aligned}
\sum_{k=1}^n\mathbb P(|X_{n,k}|>n)
&=n\,\mathbb P(|X_1|>n)\\
&\le\mathbb E\left[|X_1|\mathbf1_{\{|X_1|>n\}}\right]
\longrightarrow0.
\end{aligned}
$$
最后一步由控制收敛定理：被积函数趋于 $0$，并由可积变量 $|X_1|$ 控制。

**第二步：截断二阶矩除以 $n$ 后趋于零。**

同分布性给出
$$
\frac1{n^2}\sum_{k=1}^n\mathbb E\overline X_{n,k}^{\,2}
=\mathbb E\left[\frac{X_1^2}{n}
\mathbf1_{\{|X_1|\le n\}}\right].
$$
对每个有限的 $X_1(\omega)$，括号内趋于 $0$；而在 $\{|X_1|\le n\}$ 上，
$$
0\le\frac{X_1^2}{n}\mathbf1_{\{|X_1|\le n\}}
\le |X_1|.
$$
再次由控制收敛定理，右端期望趋于 $0$。这一步不需要原变量具有有限二阶矩。

**第三步：将截断均值换回原均值。**

记
$$
m_n=\mathbb E\left[X_1\mathbf1_{\{|X_1|\le n\}}\right],
\qquad a_n=nm_n.
$$
这里用 $m_n$ 表示单个变量的截断均值，以免与前面 $\mu_n=\mathbb E S_n$ 混淆。

截断定理给出
$$
\frac{S_n}{n}-m_n\xrightarrow{\mathbb P}0.
$$
同时，$X_1\mathbf1_{\{|X_1|\le n\}}\to X_1$ 且绝对值被 $|X_1|$ 控制，所以
$$
m_n\longrightarrow\mathbb E X_1=\mu.
$$
因此，对任意 $\varepsilon>0$，当 $n$ 足够大时 $|m_n-\mu|<\varepsilon/2$，从而
$$
\mathbb P\left(\left|\frac{S_n}{n}-\mu\right|>\varepsilon\right)
\le
\mathbb P\left(\left|\frac{S_n}{n}-m_n\right|>\frac\varepsilon2\right)
\longrightarrow0.
$$

**QED**

>[!example] 一阶矩有限、二阶矩无限也可以使用 WLLN
>设 $X_i$ 独立同分布，密度为
>$$
>f(x)=\alpha x^{-\alpha-1}\mathbf1_{\{x\ge1\}},
>\qquad 1<\alpha<2.
>$$
>直接积分得到
>$$
>\mathbb E X_1=\frac{\alpha}{\alpha-1}<\infty,
>\qquad\mathbb E X_1^2=\infty.
>$$
>所以前面的有限方差证明不能直接用于原变量，但截断法给出
>$$
>\frac{S_n}{n}\xrightarrow{\mathbb P}\frac{\alpha}{\alpha-1}.
>$$

## 8. 复习时的主线与参考来源

方差方法的共同结构是
$$
\boxed{
\frac{S_n}{b_n}
=\frac{\mathbb E S_n}{b_n}
+\frac{S_n-\mathbb E S_n}{b_n},
\qquad
\frac{\operatorname{Var}(S_n)}{b_n^2}\to0.
}
$$
先确定均值的主要尺度，再证明波动相对于这一尺度可以忽略。二阶矩不可用时，先截断，再重复同一思路。

| 模型 | 中心或均值 | 尺度 | 所得结论 |
| --- | --- | --- | --- |
| 不相关、共同均值 $\mu$、方差一致有界 | $n\mu$ | $n$ | $S_n/n\to\mu$ 于 $L^2$ 及依概率 |
| 集齐 $n$ 种券的时间 | $nH_n$ | $n\log n$ | $S_n/(n\log n)\to1$ 于 $L^2$ 及依概率 |
| 均匀置换的循环数 | $H_n$ | $\log n$ | $S_n/\log n\to1$ 于 $L^2$ 及依概率 |
| i.i.d. 且 $\mathbb E|X_1|<\infty$ | 截断中心 $nm_n$，$m_n\to\mu$ | $n$ | $S_n/n\to\mu$ 依概率 |

参考来源及补充范围：

- **手稿《2026.10.20.pdf》第 4–6 页**：$L^2$ 弱律、Bernstein 多项式、三角阵的方差判据、集券问题，以及随机置换的循环分解例子。本篇补全其中的概率估计和独立性论证。
- **Rick Durrett, *Probability: Theory and Examples***，第五版，2019-01-11 版本，§2.2：
  - Theorems 2.2.1、2.2.3：方差公式与 $L^2$ WLLN，印刷第 56–57 页（PDF 第 64–65 页）。
  - Example 2.2.4：Bernstein 多项式，印刷第 58 页（PDF 第 66 页）。
  - Theorem 2.2.6、Example 2.2.7：三角阵方差判据与集券问题，印刷第 59–60 页（PDF 第 67–68 页）。
  - Example 2.2.8、Lemma 2.2.9：随机置换的循环数及闭合指标独立性，印刷第 60–61 页（PDF 第 68–69 页）。
  - Theorem 2.2.11：截断型三角阵 WLLN，印刷第 62–63 页（PDF 第 70–71 页）；Theorem 2.2.14：可积 i.i.d. 变量的 WLLN，印刷第 64 页（PDF 第 72 页）。
- **LI Liying, *Lecture Note for MAT8030: Advanced Probability***，2024-12-26 draft，§4.2，第 39–41 页：Proposition 4.6、Example 4.5、Theorems 4.7–4.8。沿用其 $\tau_k^n,X_{n,k}$ 记号，补全讲义略去的集券等待时间独立性；几何分布矩与截断定义中的笔误已在正文对应位置注明。
- **进一步补充**：循环数与 Rényi 纪录数同分布、一阶矩证明中的直接控制收敛论证，以及 Pareto 分布例子，用于说明结论之间的联系和假设的作用。
