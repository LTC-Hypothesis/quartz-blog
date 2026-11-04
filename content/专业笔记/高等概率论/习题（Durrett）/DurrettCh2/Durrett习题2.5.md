%% codex-grading-20261103:2.5.1:start %%
> [!info] 作业批改（2026-11-03）
> <span style="color:#ef5350;">总分：111 / 150 分。仅计本笔记已写的 14 份答案（按题／小问计），按批注前原稿评分。</span>
> <span style="color:#ef5350;">满分按难度分配，逐题列于答案开头。原文保留，红字为评分和必要修正；一般英文措辞不扣分，同源错误不重复扣分。有符号级数的“&lt;∞”按上下文理解为收敛到有限实数，不另扣措辞分。</span>
%% codex-grading-20261103:2.5.1:start %%

> [!question] 2.5.1.
> Suppose $X_1, X_2, \dots$ are i.i.d. with $\mathbb{E}X_i = 0$, $\text{var}(X_i) = C < \infty$. Use Theorem 2.5.5 with $n = m^\alpha$ where $\alpha(2p - 1) > 1$ to conclude that if $S_n = X_1 + \dots + X_n$ and $p > 1/2$ then $S_n/n^p \to 0$ almost surely.

> [!done]
>
> %% codex-grading-20261103:2.5.1:start %%
> <span style="color:#ef5350;">【评分】10 / 10 分。证明成立。</span>
>
> <span style="color:#ef5350;">【记号补充，不扣分】随机阈值应写作 </span>$\color{#ef5350}{N=N(\omega,k)}$<span style="color:#ef5350;">；末步补明 </span>$\color{#ef5350}{n_{m+1}/n_m\to1}$<span style="color:#ef5350;">。后面的集合表达已体现逐样本的量词。</span>
> %% codex-grading-20261103:2.5.1:end %%
>
> Firstly, we consider 
> $$
> \mathbb{P}\left(\max_{1\le k\le n}|S_k|\ge\varepsilon n^p\right)\le\frac{\text{Var}(S_n)}{\varepsilon^2 n^{2p}}\le\frac{C}{\varepsilon^2n^{(2p-1)}}
> $$
> We take $n=m^\alpha$ and obtain by $\alpha(2p-1)>1$ 
> $$
> \sum_{m=1}^{\infty}\frac{C}{\varepsilon^2m^{\alpha(2p-1)}}<\infty
> $$
> After passing subsequence $n_m=\left \lceil  m^\alpha\right \rceil$, we have 
> $$
> \mathbb{P}\left(\max_{1\le k\le n_m}|S_k|\ge\varepsilon n_m^p\right)\le\frac{C}{\varepsilon^2n_m^{(2p-1)}}\le\frac{C}{\varepsilon^2m^{\alpha(2p-1)}}
> $$
> By Borel-Cantelli's lemma,
> $$
> \sum_{m=1}^{\infty}\mathbb{P}\left(\max_{1\le k\le n_m}|S_k|\ge\varepsilon n_m^p\right)<\infty\Longrightarrow\mathbb{P}\left(\max_{1\le k\le n_m}|S_k|\ge\varepsilon n_m^p,\text{i.o.}\right)=0
> $$
> Then for any $k\in\mathbb{N}$, there exists $N\in\mathbb{N}$ and $\Omega_k$ with probability $1$, for $m\ge N$ and $\omega\in\Omega_k$, it holds 
> $$
> \max_{1\le j\le n_m}|S_j(\omega)|<\frac{1}{k}\cdot n_m^p
> $$
> Let $\Omega_*=\bigcap_{k=1}^{\infty}\Omega_k$, for $\omega\in\Omega_*$, 
> $$
> \mathbb{P}\left(\bigcap_{k=1}^{\infty}\bigcup_{N=1}^{\infty}\bigcap_{m=N}^{\infty}\left\{\frac{\max_{1\le j\le n_m}|S_j|}{n_m^p}\le\frac{1}{k}\right\}\right)=1
> $$
> It implies $\frac{\max_{1\le j\le n_m}|S_j|}{n_m^p}\xrightarrow{a.s.}0$. Now for any $n\in\mathbb{N}$, there exists $n_{m}\le n<n_{m+1}$
> $$
> \frac{|S_n|}{n^p}\le\frac{\max_{1\le k\le n_{m+1}}|S_k|}{n_m^p}=\frac{\max_{1\le k\le n_{m+1}}|S_k|}{n_{m+1}^p}\frac{n_{m+1}^p}{n_{m}^p}\to0\text{ a.s. }m\to\infty
> $$
> Hence, $\frac{S_n}{n^p}\xrightarrow{a.s.}0$.

> [!question] 2.5.2.
> The converse of Theorem 2.5.12 is much easier. Let $p > 0$. If $S_n/n^{1/p} \to 0$ a.s. then $\mathbb{E}|X_1|^p < \infty$.

> [!done]
>
> %% codex-grading-20261103:2.5.2:start %%
> <span style="color:#ef5350;">【评分】9 / 10 分。思路正确；BC 的事件对象写错，扣 1 分。</span>
>
> <span style="color:#ef5350;">【修正】第二 Borel–Cantelli 应推出 </span>$\color{#ef5350}{\mathbb P(A_n\ \mathrm{i.o.})=1}$<span style="color:#ef5350;">。同分布只给出 </span>$\color{#ef5350}{\mathbb P(A_n)=\mathbb P(Y>n)}$<span style="color:#ef5350;">，不能把无穷次发生事件换成同一个 </span>$\color{#ef5350}{Y}$<span style="color:#ef5350;"> 的尾事件；对有限的 </span>$\color{#ef5350}{Y}$<span style="color:#ef5350;">，</span>$\color{#ef5350}{\mathbb P(Y>n\ \mathrm{i.o.})=0}$<span style="color:#ef5350;">。</span>
> %% codex-grading-20261103:2.5.2:end %%
>
> Let $Y=|X_1|^p$, note that 
> $$
> \mathbb{E}Y<\infty\Longleftrightarrow\sum_{n=1}^{\infty}\mathbb{P}(Y>n)<\infty
> $$
> Since $\frac{S_n}{\sqrt[p]{n}}\xrightarrow{a.s.}0$, we have 
> $$
> \frac{X_n}{\sqrt[p]{n}}=\frac{S_n}{\sqrt[p]{n}}-\frac{S_{n-1}}{\sqrt[p]{n-1}}\sqrt[p]{\frac{n-1}{n}}\xrightarrow{a.s}0
> $$
> Therefore, denote the event by 
> $$
> A_n:=\{|X_n|>\sqrt[p]{n}\}\Longrightarrow\mathbb{P}(A_n,\text{i.o.})=0
> $$
> If $\sum_{n=1}^{\infty}\mathbb{P}(Y>n)=\infty$, since $A_n$ are independent, by 2nd Borel-Cantelli''s lemma, $\mathbb{P}(Y>n,\text{i.o.})=1\Longrightarrow\Longleftarrow$ with $\mathbb{P}(A_n,\text{i.o.})=0$. Hence, we prove it. 

> [!question] 2.5.3.
> Let $X_1, X_2, \dots$ be i.i.d. standard normals. Show that for any $t$
> $$
> \sum_{n=1}^\infty X_n \cdot \frac{\sin(n\pi t)}{n} \quad \text{converges a.s.}
> $$
> We will see this series again at the end of Section 8.1 [REF].

> [!done]
>
> %% codex-grading-20261103:2.5.3:start %%
> <span style="color:#ef5350;">【评分】5 / 5 分。对每个固定 t，独立性、零均值和可求和方差均满足所引定理。</span>
> %% codex-grading-20261103:2.5.3:end %%
>
> ![[Pasted image 20261031081350.png]]
> Let $Y_n:=X_n\cdot\frac{\sin{(n\pi t)}}{n}$, then 
> $$
> \mathbb{E}Y_n=0,\mathbb{E}Y_n^2=\frac{\sin^2(n\pi t)}{n^2}
> $$
> Since 
> $$
> \left|\frac{\sin^2(n\pi t)}{n^2}\right|\le\frac{1}{n^2}\Longrightarrow\sum_{n=1}^{\infty}\frac{\sin^2(n\pi t)}{n^2}<\infty
> $$
> Then 
> $$
> \sum_{n=1}^{\infty}Y_n<\infty\text{ with probability one}
> $$

> [!question] 2.5.4. (i)
> Let $X_1, X_2, \dots$ be independent with $\mathbb{E}X_n = 0$, $\text{var}(X_n) = \sigma_n^2$. (i) Show that if $\sum_n \sigma_n^2/n^2 < \infty$ then $\sum_n X_n/n$ converges a.s. and hence $n^{-1} \sum_{m=1}^n X_m \to 0$ a.s.

> [!done]
>
> %% codex-grading-20261103:2.5.4-i:start %%
> <span style="color:#ef5350;">【评分】6 / 10 分。级数收敛已证；遗漏题目要求的平均值极限，扣 4 分。</span>
>
> <span style="color:#ef5350;">【补全】由 </span>$\color{#ef5350}{\sum_n X_n/n}$<span style="color:#ef5350;"> 几乎必然收敛，对每条收敛的样本路径应用 Kronecker 引理（取权重 </span>$\color{#ef5350}{b_n=n}$<span style="color:#ef5350;">），得到 </span>$\color{#ef5350}{\frac1n\sum_{m=1}^nX_m\to0}$<span style="color:#ef5350;"> a.s.。</span>
> %% codex-grading-20261103:2.5.4-i:end %%
>
> Since 
> $$
> \sum_{n=1}^{\infty}\text{Var}\left(\frac{X_n}{n}\right)=\sum_{n=1}^{\infty}\frac{\sigma_{n}^2}{n^2}<\infty\Longrightarrow\sum_{n=1}^{\infty}\frac{X_n}{n}<\infty,\text{a.s.}
> $$

> [!question] 2.5.4. (ii)
> (ii) Suppose $\sum \sigma_n^2/n^2 = \infty$ and without loss of generality that $\sigma_n^2 \leq n^2$ for all $n$. Show that there are independent random variables $X_n$ with $\mathbb{E}X_n = 0$ and $\text{var}(X_n) \leq \sigma_n^2$ so that $X_n/n$ and hence $n^{-1} \sum_{m \leq n} X_m$ does not converge to 0 a.s.

> [!done]
>
> %% codex-grading-20261103:2.5.4-ii:start %%
> <span style="color:#ef5350;">【评分】10 / 10 分。构造与最后的逆否论证正确。</span>
>
> <span style="color:#ef5350;">【补充，不扣分】按所给边缘分布独立构造各 </span>$\color{#ef5350}{X_n}$<span style="color:#ef5350;">；此时 </span>$\color{#ef5350}{0\le p_n\le1/2}$<span style="color:#ef5350;">，可使用第二 Borel–Cantelli。</span>
> %% codex-grading-20261103:2.5.4-ii:end %%
>
> Define r.v. $X_n$ satisfies
> $$
> \mathbb{P}(X_n=\pm n)=\frac{p_n}{2},\mathbb{P}(X_n=0)=1-p_n
> $$
> We calculate the expectation and variance, 
> $$
> \mathbb{E}(X_n)=0,\text{Var}(X_n)=n^2p_n
> $$
> We hope $\text{Var}(X_n)\le \sigma_n^2$ and thus we take $p_n=\frac{\sigma_n^2}{2n^2}<1$. Now we denote the event by $A_n:=\{|X_n|=n\}$, by 2nd Borel-Cantelli's lemma, 
> $$
> \sum_{n=1}^{\infty}\mathbb{P}(A_n)=\sum_{n=1}^{\infty}\frac{\sigma_n^2}{2n^2}=\infty\Longrightarrow\mathbb{P}(A_n,\text{i.o.})=1
> $$
> It implies that $\{\frac{X_n}{n}=\pm1,\text{i.o.}\}$ with probability one and thus $\frac{X_n}{n}\nrightarrow0$. Suppose $S_n=\sum_{m=1}^{n}X_m$ and $\frac{S_n}{n}\to0$, then 
> $$
> \frac{X_n}{n}=\frac{S_n}{n}-\frac{n-1}{n}\frac{S_{n-1}}{n-1}\to0\Longrightarrow\Longleftarrow
> $$
> Hence, $\frac{S_n}{n}\nrightarrow0$.

> [!question] 2.5.5.
> Let $X_n \geq 0$ be independent for $n \geq 1$. The following are equivalent:
> (i) $\sum_{n=1}^\infty X_n < \infty$ a.s.
> 
> (ii) $\sum_{n=1}^\infty [\mathbb{P}(X_n > 1) + \mathbb{E}(X_n 1_{(X_n \leq 1)})] < \infty$
> 
> (iii) $\sum_{n=1}^\infty \mathbb{E}(X_n/(1 + X_n)) < \infty$.

^2d3d94

> [!done]
>
> %% codex-grading-20261103:2.5.5:start %%
> <span style="color:#ef5350;">【评分】9 / 15 分。第一箭头的有限性推断错误，扣 5 分；第三箭头漏写 Tonelli 关键步骤，扣 1 分。</span>
>
> <span style="color:#ef5350;">【修正】(i) 只给出 </span>$\color{#ef5350}{\sum_nX_n<\infty}$<span style="color:#ef5350;"> a.s.，不能推出 </span>$\color{#ef5350}{\mathbb E\sum_nX_n<\infty}$<span style="color:#ef5350;">；Tonelli 的等式仍可能两边都为无穷。第一箭头可改用三列级数定理的必要性（截断水平取 1）：尾概率级数及非负截断均值级数均收敛，正好得到 (ii)。</span>
>
> <span style="color:#ef5350;">【补证】(iii) 到 (i) 先写 </span>$\color{#ef5350}{\mathbb E\sum_n\frac{X_n}{1+X_n}=\sum_n\mathbb E\frac{X_n}{1+X_n}<\infty}$<span style="color:#ef5350;">，故该随机级数 a.s. 有限，后面的趋零与比较才有依据。另，(ii) 到 (iii) 的分解中 </span>$\color{#ef5350}{\{X_n<1\}}$<span style="color:#ef5350;"> 应改为 </span>$\color{#ef5350}{\{X_n\le1\}}$<span style="color:#ef5350;">。</span>
> %% codex-grading-20261103:2.5.5:end %%
>
> (i) $\Longrightarrow$ (ii): Note that 
> $$
>\mathbb{P}(X_n > 1) + \mathbb{E}(X_n 1_{(X_n \leq 1)})\le\mathbb{E}X_n 
> $$
> Now by [[Durrett习题1.6#^ce62b7|exchanging summation and expectation]], 
> $$
> \sum_{n=1}^{\infty}\mathbb{E}X_n=\mathbb{E}\sum_{n=1}^{\infty}X_n<\infty
> $$
> 
> (ii) $\Longrightarrow$ (iii): Note that 
> $$
> \frac{X_n}{1+X_n}=\frac{X_n}{1+X_n}\mathbb{1}_{\{X_n>1\}}+\frac{X_n}{1+X_n}\mathbb{1}_{\{X_n<1\}}\le \mathbb{1}_{\{X_n>1\}}+X_n\mathbb{1}_{\{X_n\le 1\}}
> $$
> Therefore, 
> $$
> \mathbb{E}\frac{X_n}{1+X_n}\le\mathbb{P}(X_n>1)+\mathbb{E}X_n\mathbb{1}_{\{X_n\le 1\}}
> $$
>  
> (iii) $\Longrightarrow$ (i): Since $\sum_{n=1}^{\infty}\mathbb{E}\frac{X_n}{1+X_n}<\infty$, 
> $$
> \frac{X_n}{1+X_n}\to0
> $$
> If $X_n>1\Longrightarrow \frac{X_n}{1+X_n}\ge\frac{1}{2}$, then there exists $N\in\mathbb{N}$ s.t. $n\ge N$, it holds $X_n\le 1$ and 
> $$
> X_n=(1+X_n)\frac{X_n}{1+X_n}\le2\frac{X_n}{1+X_n}
> $$
> Then 
> $$
> \sum_{n=1}^{\infty}X_n\le\sum_{n=1}^{N-1}X_n+\sum_{n=N}^{\infty}2\frac{X_n}{1+X_n}<\infty
> $$

> [!question] 2.5.6.
> Let $\psi(x) = x^2$ when $|x| \leq 1$ and $= |x|$ when $|x| \geq 1$. Show that if $X_1, X_2, \dots$ are independent with $\mathbb{E}X_n = 0$ and $\sum_{n=1}^\infty \mathbb{E}\psi(X_n) < \infty$ then $\sum_{n=1}^\infty X_n$ converges a.s.

> [!done]
>
> %% codex-grading-20261103:2.5.6:start %%
> <span style="color:#ef5350;">【评分】5 / 10 分。尾概率和截断二阶矩估计正确；误用 2.5.5，且未控制截断均值，合扣 5 分。</span>
>
> <span style="color:#ef5350;">【修正】不能由截断二阶矩可和推出绝对收敛。令 </span>$\color{#ef5350}{Y_n=X_n\mathbf1_{\{|X_n|\le1\}}}$<span style="color:#ef5350;">，改用三列级数定理：原稿已控制尾概率及方差；由零均值再补 </span>$\color{#ef5350}{|\mathbb EY_n|=|\mathbb E[X_n\mathbf1_{\{|X_n|>1\}}]|\le\mathbb E[|X_n|\mathbf1_{\{|X_n|>1\}}]\le\mathbb E\psi(X_n)}$<span style="color:#ef5350;">。因此截断均值绝对可和，得到原级数收敛；不要保留“绝对收敛”的推断。</span>
> %% codex-grading-20261103:2.5.6:end %%
>
> Note that 
> $$
> \begin{aligned}
>\mathbb{E}\psi(X_n)=&\mathbb{E}\psi(X_n)\mathbb{1}_{\{|X_n|\le 1\}}+\mathbb{E}\psi(X_n)\mathbb{1}_{\{|X_n|>1\}}\\
>=&\mathbb{E}X_n^2\mathbb{1}_{\{|X_n|\le 1\}}+\mathbb{E}|X_n|\mathbb{1}_{\{|X_n|>1\}}\\
>\ge&\mathbb{P}(|X_n|>1)+\mathbb{E}|X_n|^2\mathbb{1}_{\{|X_n|\le 1\}}
>\end{aligned}
> $$
> Then we obtain 
> $$
> \sum_{n=1}^{\infty}\left[\mathbb{P}(|X_n|>1)+\mathbb{E}|X_n|^2\mathbb{1}_{\{|X_n|\le 1\}}\right]\le\sum_{n=1}^{\infty}\mathbb{E}\psi(X_n)<\infty
> $$
> By [[#^2d3d94|E.x.2.5.5]], 
> $$
> \sum_{n=1}^{\infty}|X_n|<\infty,\text{a.s.}\Longrightarrow\sum_{n=1}^{\infty}X_n<\infty,\text{a.s.}
> $$

> [!question] 2.5.7.
> Let $X_n$ be independent. Suppose $\sum_{n=1}^\infty \mathbb{E}|X_n|^{p(n)} < \infty$ where $0 < p(n) \leq 2$ for all $n$ and $\mathbb{E}X_n = 0$ when $p(n) > 1$. Show that $\sum_{n=1}^\infty X_n$ converges a.s.

> [!done]
>
> %% codex-grading-20261103:2.5.7:start %%
> <span style="color:#ef5350;">【评分】10 / 15 分。尾部矩比较在 p(n)&lt;1 时失效，扣 2 分；截断均值不能直接删去，扣 3 分。</span>
>
> <span style="color:#ef5350;">【修正】尾概率直接用 </span>$\color{#ef5350}{\mathbb P(|X_n|>1)\le\mathbb E|X_n|^{p(n)}}$<span style="color:#ef5350;">，不经过 </span>$\color{#ef5350}{\mathbb E[|X_n|\mathbf1_{\{|X_n|>1\}}]}$<span style="color:#ef5350;">。对 </span>$\color{#ef5350}{n\in I}$<span style="color:#ef5350;">，</span>$\color{#ef5350}{\mathbb EX_n=0}$<span style="color:#ef5350;"> 不意味着 </span>$\color{#ef5350}{\mathbb EY_n=0}$<span style="color:#ef5350;">，而是 </span>$\color{#ef5350}{\mathbb EY_n=-\mathbb E[X_n\mathbf1_{\{|X_n|>1\}}]}$<span style="color:#ef5350;">，故 </span>$\color{#ef5350}{|\mathbb EY_n|\le\mathbb E|X_n|^{p(n)}}$<span style="color:#ef5350;">。将此项与 </span>$\color{#ef5350}{I^c}$<span style="color:#ef5350;"> 的原估计一起保留，才能得到总和有限；</span>$\color{#ef5350}{p(n)=2}$<span style="color:#ef5350;"> 同样适用。</span>
> %% codex-grading-20261103:2.5.7:end %%
>
> We want to use the three series theorem. Let $Y_n:=X_n\mathbb{1}_{\{|X_n|\le1\}}$. Note that for $0<p(n)<2$,
> $$
> \mathbb{P}(|X_n|>1)\le\mathbb{E}|X_n|\mathbb{1}_{|X_n|>1}\le\mathbb{E}|X_n|^{p(n)}
> $$
> $$
> \text{Var}(Y_n)\le\mathbb{E}Y_n^2=\mathbb{E}|X_n|^2\mathbb{1}_{\{|X_n|\le1\}}\le\mathbb{E}|X_n|^{p(n)}
> $$
> Then we obtain 
> $$
> \sum_{n=1}^{\infty}\mathbb{P}(|X_n|>1)<\infty,\sum_{n=1}^{\infty}\text{Var}(Y_n)<\infty,\text{a.s.}
> $$
> We only need to show that $\sum_{n=1}^{\infty}\mathbb{E}Y_n<\infty$. Denote the index set $I=\{n:p(n)>1\}$, then we have 
> $$
> \begin{aligned}
>\sum_{n=1}^{\infty}|\mathbb{E}Y_n|&=\sum_{n\in I}|\mathbb{E}Y_n|+\sum_{n\in I^c}|\mathbb{E}Y_n|\\
>&\le\sum_{n\in I^c}\mathbb{E}|X_n|\mathbb{1}_{\{|X_n|\le 1\}}\\
>&\le \sum_{n=1}^{\infty}\mathbb{E}|X_n|^{p(n)}<\infty
>\end{aligned}
> $$
> Hence, the conditions of three series hold and thus $\sum_{n=1}^{\infty}X_n<\infty,a.s.$

> [!question] 2.5.8.
> Let $X_1, X_2, \dots$ be i.i.d. and not $\equiv 0$. Then the radius of convergence of the power series $\sum_{n \geq 1} X_n(\omega)z^n$ (i.e., $r(\omega) = \sup\{c : \sum |X_n(\omega)|c^n < \infty\}$) is 1 a.s. or 0 a.s., according as $\mathbb{E}\log^+|X_1| < \infty$ or $= \infty$ where $\log^+ x = \max(\log x, 0)$.

> [!done]
>
> %% codex-grading-20261103:2.5.8:start %%
> <span style="color:#ef5350;">【评分】7 / 10 分。BC 事件对象两处同源错误合扣 2 分；无穷分支的阈值极限不完整，扣 1 分。</span>
>
> <span style="color:#ef5350;">【修正】根值公式应为 </span>$\color{#ef5350}{L=\limsup_n|X_n|^{1/n}}$<span style="color:#ef5350;">。两处 BC 都应作用于 </span>$\color{#ef5350}{\{Y_n>\varepsilon n\}}$<span style="color:#ef5350;">（有限分支也可用 </span>$\color{#ef5350}{\ge}$<span style="color:#ef5350;">），不能换成同一个 </span>$\color{#ef5350}{Y_1}$<span style="color:#ef5350;"> 的事件。有限分支取 </span>$\color{#ef5350}{\varepsilon=1/j}$<span style="color:#ef5350;"> 并作可数交；非零条件给出某个 </span>$\color{#ef5350}{b>0}$<span style="color:#ef5350;"> 满足 </span>$\color{#ef5350}{\mathbb P(|X_1|>b)>0}$<span style="color:#ef5350;">。无穷分支对每个整数 </span>$\color{#ef5350}{j\ge1}$<span style="color:#ef5350;"> 得 </span>$\color{#ef5350}{L\ge e^j}$<span style="color:#ef5350;"> a.s.，再作可数交才有 </span>$\color{#ef5350}{L=\infty}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{r=0}$<span style="color:#ef5350;">；一个固定的“大阈值”不够，且这里只能先写 </span>$\color{#ef5350}{\ge}$<span style="color:#ef5350;">。</span>
> %% codex-grading-20261103:2.5.8:end %%
>
> By Cauchy-Adamard's formula, 
> $$
> \frac{1}{r(\omega)}=\limsup_{n\to\infty}\sqrt[n]{X_n(\omega)}
> $$
> and let $Y_n:=\log^+{|X_n|}$. We W.T.S. $\frac{1}{r(\omega)}\le1$. For $\varepsilon>0$, consider 
> $$
> \mathbb{P}(|X_n|\ge e^{\varepsilon n})=\mathbb{P}(Y_n\ge\varepsilon n)=\mathbb{P}(Y_1\ge\varepsilon n)
> $$
> If $\mathbb{E}Y_n<\infty$, then 
> $$
> \sum_{n=1}^{\infty}\mathbb{P}(Y_1\ge\varepsilon n)<\infty
> $$
> By 1st Borel-Cantelli's lemma, $\mathbb{P}(Y_1\ge\varepsilon n,\text{i.o.})=0$, which implies $\limsup_{n\to\infty}|X_n|^\frac{1}{n}\le e^\varepsilon$ and let $\varepsilon\to0^+$, we obtain $r(\omega)\ge 1$. 
> Since $X_n$ are not $\equiv0$, there exists constant $b$ s.t. 
> $$
> \sum_{n=1}^{\infty}\mathbb{P}(|X_n|>b)=\infty
> $$
> By 2nd Borel-Cantelli's lemma, $\mathbb{P}(|X_n|>b,\text{i.o.})=1$ and thus $\limsup_{n\to\infty}|X_n|^{\frac{1}{n}}\ge1$. Hence, $r(\omega)=1$. 
> Now if $\mathbb{E}Y_1=\infty$, then 
> $$
> \sum_{n=1}^{\infty}\mathbb{P}(Y_1>\varepsilon n)=\infty\Longrightarrow\mathbb{P}(Y_1>\varepsilon n,\text{i.o.})=1
> $$
> Then $\limsup_{n\to\infty}|X_n|^\frac{1}{n}>e^\varepsilon$, we can choose sufficiently large $\varepsilon$ s.t. $r(\omega)=0$. 

> [!question] 2.5.9.
> Let $X_1, X_2, \dots$ be independent and let $S_{m,n} = X_{m+1} + \dots + X_n$. Then
> $$
> (\star) \qquad \mathbb{P} \left( \max_{m < j \leq n} |S_{m,j}| > 2a \right) \min_{m < k \leq n} \mathbb{P}(|S_{k,n}| \leq a) \leq \mathbb{P}(|S_{m,n}| > a)
> $$

> [!done]
>
> %% codex-grading-20261103:2.5.9:start %%
> <span style="color:#ef5350;">【评分】10 / 10 分。首次越界分解与概率估计成立；下标按同源笔误处理，不扣分。</span>
>
> <span style="color:#ef5350;">【记号修正】两处最大值事件均应写作 </span>$\color{#ef5350}{\{\max_{m<j\le n}|S_{m,j}|>2a\}}$<span style="color:#ef5350;">。补明 </span>$\color{#ef5350}{A_k}$<span style="color:#ef5350;"> 两两不交，故并集概率可求和；固定 </span>$\color{#ef5350}{k}$<span style="color:#ef5350;"> 时，</span>$\color{#ef5350}{A_k}$<span style="color:#ef5350;"> 与剩余尾和独立，故交事件概率可相乘（此处可写等号）。</span>
> %% codex-grading-20261103:2.5.9:end %%
>
> Define the event 
> $$
> A_k\triangleq\left\{|S_{m,j}|\le 2a,\forall m<j<k,|S_{m,k}|>2a\right\}
> $$
> and note that 
> $$
> \left\{\max_{m<k\le n}|S_{k,j}|>2a\right\}=\bigcup_{k=m+1}^{n}A_k
> $$
> For fixed $k$, when $A_k$ happen and $|S_{k,n}|\le a$, we have 
> $$
> |S_{m,n}|=|S_{m,k}+S_{k,n}|\ge|S_{m,k}|-|S_{k,n}|>a
> $$
> It implies 
> $$
> \bigcup_{k=m+1}^{n}(A_{k}\cap\{|S_{k,n}|\le a\})\subseteq\{|S_{m,n}|>a\}
> $$
> Taking probability and by independence, we obtain
> $$
> \begin{aligned}
>\mathbb{P}\{|S_{m,n}|>a\}\ge&\sum_{k=m+1}^{n}\mathbb{P}(A_k\cap\{|S_{k,n}|\le a\})\\
>\ge&\sum_{k=m+1}^{n}\mathbb{P}(A_k)\mathbb{P}(\{|S_{k,n}|\le a\})\\
>\ge&\mathbb{P}\left(\max_{m<k\le n}|S_{k,j}|>2a\right)\min_{m<k\le n}\mathbb{P}(\{|S_{k,n}|\le a\})
>\end{aligned}
> $$ 

> [!question] 2.5.10.
> Use $(\star)$ to prove a theorem of P. Lévy: Let $X_1, X_2, \dots$ be independent and let $S_n = X_1 + \dots + X_n$. If $\lim_{n \to \infty} S_n$ exists in probability then it also exists a.s.

> [!done]
>
> %% codex-grading-20261103:2.5.10:start %%
> <span style="color:#ef5350;">【评分】10 / 15 分。量词及事件记号合扣 1 分；缺少从概率估计到 a.s. 的递减事件论证，扣 4 分。</span>
>
> <span style="color:#ef5350;">【修正】起始量词应是“对每个 </span>$\color{#ef5350}{a>0}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{0<\varepsilon<1}$<span style="color:#ef5350;">，存在 </span>$\color{#ef5350}{N(a,\varepsilon)}$<span style="color:#ef5350;">”；最小概率因子控制的是 </span>$\color{#ef5350}{|S_n-S_k|}$<span style="color:#ef5350;">。令 </span>$\color{#ef5350}{D_m=\sup_{j,k>m}|S_j-S_k|}$<span style="color:#ef5350;">，它单调不增，且对 </span>$\color{#ef5350}{m\ge N(a,\varepsilon)}$<span style="color:#ef5350;"> 有 </span>$\color{#ef5350}{\mathbb P(D_m>4a)\le\varepsilon/(1-\varepsilon)}$<span style="color:#ef5350;">。此处用严格的 </span>$\color{#ef5350}{>}$<span style="color:#ef5350;">，与右侧阈值一致。</span>
>
> <span style="color:#ef5350;">【补证】先让 </span>$\color{#ef5350}{m\to\infty}$<span style="color:#ef5350;">，再让 </span>$\color{#ef5350}{\varepsilon\downarrow0}$<span style="color:#ef5350;">，由概率上连续性得 </span>$\color{#ef5350}{\mathbb P(\bigcap_m\{D_m>4a\})=0}$<span style="color:#ef5350;">。再取 </span>$\color{#ef5350}{a=1/(4r)}$<span style="color:#ef5350;"> 并作可数交，才得到 a.s. Cauchy；应在这个概率为 1 的交集内部论证。每个精度对应的阈值 </span>$\color{#ef5350}{N}$<span style="color:#ef5350;"> 可以依赖 </span>$\color{#ef5350}{r,\omega}$<span style="color:#ef5350;">。</span>
> %% codex-grading-20261103:2.5.10:end %%
>
> We should note that $S_{m,n}=S_{n}-S_m$. Since $S_n$ converges in probability, then $S_n$ is a Cauchy sequence in probability, i.e. 
> $$
> \forall\varepsilon,\exists N,\text{ for }n>m>N,\forall a>0,\mathbb{P}\left(|S_{n}-S_m|>a\right)\le\varepsilon
> $$
> Then for each $m<k<n$, it holds 
> $$
> \min_{m<k<n}\mathbb{P}(|S_m-S_k|\le a)\ge1-\varepsilon
> $$
> and by $(*)$, we have 
> $$
> \begin{aligned}
>&\mathbb{P} \left( \max_{m < j \leq n} |S_{m,j}| > 2a \right) \min_{m < k \leq n} \mathbb{P}(|S_{k,n}| \leq a) \leq \mathbb{P}(|S_{m,n}| > a)\\
>\Longrightarrow&\mathbb{P} \left( \max_{m < j \leq n} |S_{m,j}| > 2a \right)\le\frac{\varepsilon}{1-\varepsilon}
>\end{aligned}
> $$
> For fixed $m$, let $n\to\infty$, we obtain 
> $$
> \mathbb{P}\left(\sup_{j>m}|S_{m,j}|>2a\right)\le\frac{\varepsilon}{1-\varepsilon}
> $$
> for any $k,j>m$, we have 
> $$
> \sup_{j,k>m}|S_k-S_j|\le\sup_{j>m}|S_{m,j}|+\sup_{k>m}|S_{m,k}|
> $$
> Then 
> $$
> \begin{aligned}
>\mathbb{P}\left(\sup_{j,k>m}|S_j-S_k|\ge4a\right)&\le\mathbb{P}\left(\sup_{j>m}|S_{m,j}|>2a\right)+\mathbb{P}\left(\sup_{k>m}|S_{m,j}|>2a\right)\\
>&\le\frac{2\varepsilon}{1-\varepsilon}
>\end{aligned}\tag{$*1$}
> $$
> We can take $a=\frac{1}{4r}$ where $r\in\mathbb{N_+}$. It implies there exists $\omega\in\Omega_r$ s.t. $(*1)$ holds and let $\Omega_*:=\bigcap_{r=1}^{\infty}\Omega_r$. For $\omega\notin\Omega_*$ and its complement is with probability one, it holds 
> $$
> \text{ for any }j,k>m>N,|S_j-S_k|\le\frac{1}{r},\forall r\in\mathbb{N_+}
> $$
> It implies $S_n$ is a Cauchy sequence a.s. and thus $S_n$ converges a.s.

> [!question] 2.5.11.
> Let $X_1, X_2, \dots$ be i.i.d. and $S_n = X_1 + \dots + X_n$. Use $(\star)$ to conclude that if $S_n/n \to 0$ in probability then $(\max_{1 \leq m \leq n} S_m)/n \to 0$ in probability.

> [!done]
>
> %% codex-grading-20261103:2.5.11:start %%
> <span style="color:#ef5350;">【评分】8 / 10 分。分段控制正确；同源阈值错误扣 1 分，遗漏最后代回结论扣 1 分。</span>
>
> <span style="color:#ef5350;">【修正】首式应为 </span>$\color{#ef5350}{\mathbb P(\max_{1\le k\le n}|S_k|>2an)\,q_n\le\mathbb P(|S_n|>an)}$<span style="color:#ef5350;">，其中 </span>$\color{#ef5350}{q_n=\min_{0\le k<n}\mathbb P(|S_k|\le an)}$<span style="color:#ef5350;">；选择 </span>$\color{#ef5350}{N}$<span style="color:#ef5350;"> 时也用阈值 </span>$\color{#ef5350}{a}$<span style="color:#ef5350;">，不能由阈值 </span>$\color{#ef5350}{2a}$<span style="color:#ef5350;"> 的估计控制较小阈值。你已证明 </span>$\color{#ef5350}{q_n\to1}$<span style="color:#ef5350;">，代回即得最大值概率趋零，再用 </span>$\color{#ef5350}{|\max_{1\le k\le n}S_k|\le\max_{1\le k\le n}|S_k|}$<span style="color:#ef5350;"> 完成结论。概率数值的收敛不需写 a.s.。</span>
> %% codex-grading-20261103:2.5.11:end %%
>
> By $(*)$, we have 
> $$
> \mathbb{P}\left(\max_{1\le k<n}|S_k|>2an\right)\min_{0\le k<n}\mathbb{P}\left(|S_k|\le an\right)\le\mathbb{P}\left(|S_n|> 2an\right)
> $$
> For sufficiently large $n$, there exists $N$, when $n\ge N$, 
> $$
> \mathbb{P}\left(\frac{|S_n|}{n}>2a\right)\le\frac{\varepsilon}{2}
> $$
> Now we W.T.S. 
> $$
> \max_{0\le k<n}\mathbb{P}\left(|S_k|>an\right)\to0\text{ a.s. }n\to\infty
> $$
> we devide two parts, 
> $$
> \begin{aligned}
>\max_{0\le k<n}\mathbb{P}\left(|S_k|>an\right)\le&\max_{0\le k<N}\mathbb{P}\left(|S_k|>an\right)+\max_{N\le k<n}\mathbb{P}\left(|S_k|>an\right)\\
>\le&\max_{0\le k<N}\mathbb{P}\left(|S_k|>an\right)+\max_{N\le k<n}\mathbb{P}\left(|S_k|>ak\right)\\
>\le&\max_{0\le k<N}\mathbb{P}\left(|S_k|>an\right)+\frac{\varepsilon}{2}
>\end{aligned}
> $$
> Then we obtain 
> $$
> \limsup_{n\to\infty}\max_{0\le k<n}\mathbb{P}\left(|S_k|>an\right)\le\frac{\varepsilon}{2}
> $$
> It implies $\min_{0\le k<n}\mathbb{P}\left(|S_k|\le an\right)\to1$. 

^6b788d

> [!question] 2.5.12. (i)
> Let $X_1, X_2, \dots$ be i.i.d. and $S_n = X_1 + \dots + X_n$. Suppose $a_n \uparrow \infty$ and $a(2^n)/a(2^{n-1})$ is bounded. (i) Use $(\star)$ to show that if $S_n/a(n) \to 0$ in probability and $S_{2^n}/a(2^n) \to 0$ a.s. then $S_n/a(n) \to 0$ a.s.

> [!done]
>
> %% codex-grading-20261103:2.5.12-i:start %%
> <span style="color:#ef5350;">【评分】8 / 15 分。分块增量定义扣 1 分；极大不等式及目标指标扣 2 分；缺块内 BC 与有界比值插值，扣 4 分。</span>
>
> <span style="color:#ef5350;">【修正】应为 </span>$\color{#ef5350}{T_k=\sum_{j=2^{k-1}+1}^{2^k}X_j=S_{2^k}-S_{2^{k-1}}}$<span style="color:#ef5350;">，不是部分和 </span>$\color{#ef5350}{S_j}$<span style="color:#ef5350;"> 的总和。后文按正确含义给出了整块尾概率的可求和性，这部分思路成立。尾和最大值的方向也可以保留：将该块变量倒序后使用 </span>$\color{#ef5350}{(*)}$<span style="color:#ef5350;"> 即可。</span>
>
> <span style="color:#ef5350;">【补全】记 </span>$\color{#ef5350}{m_k=2^{k-1}}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{N_k=2^k}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{b_k=a(N_k)}$<span style="color:#ef5350;">，令 </span>$\color{#ef5350}{R_k=\max_{m_k<n\le N_k}|S_{n,N_k}|}$<span style="color:#ef5350;">、</span>$\color{#ef5350}{q_k=\min_{m_k\le n<N_k}\mathbb P(|S_{m_k,n}|\le\varepsilon b_k)}$<span style="color:#ef5350;">。需证明的是 </span>$\color{#ef5350}{q_k\to1}$<span style="color:#ef5350;">，由同分布和前题的小下标／大下标分段法得到；正确右端是整块概率 </span>$\color{#ef5350}{\mathbb P(|T_k|>\varepsilon b_k)}$<span style="color:#ef5350;">。最终 </span>$\color{#ef5350}{\mathbb P(R_k>2\varepsilon b_k)\le2\mathbb P(|T_k|>\varepsilon b_k)}$<span style="color:#ef5350;">，故左侧可求和；BC 加可数阈值给出 </span>$\color{#ef5350}{R_k/b_k\to0}$<span style="color:#ef5350;"> a.s.。</span>
>
> <span style="color:#ef5350;">【最后一步】对 </span>$\color{#ef5350}{m_k<n\le N_k}$<span style="color:#ef5350;">，</span>$\color{#ef5350}{\frac{|S_n|}{a(n)}\le\frac{a(N_k)}{a(m_k)}\left(\frac{|S_{N_k}|}{a(N_k)}+\frac{R_k}{a(N_k)}\right)\to0}$<span style="color:#ef5350;"> a.s.。这里才用到题设的相邻二进制归一化因子比值有界。</span>
> %% codex-grading-20261103:2.5.12-i:end %%
>
> Firstly, let $T_k=\sum_{j=2^{k-1}}^{2^k}S_j$ and we claim 
> $$
> \sum_{k=1}^{\infty}\mathbb{P}\left(|T_k|>\varepsilon\cdot a(2^k)\right)<\infty
> $$
> If the conclusion is not, then by independent and 2nd Borel-Cantelli's lemma, 
> $$
> \mathbb{P}\left(|T_k|>\varepsilon\cdot a(2^k),\text{i.o.}\right)=1\Longrightarrow\frac{T_k}{a(2^k)}\nrightarrow0
> $$
> But 
> $$
> \frac{T_k}{a(2^k)}=\frac{S_{2^k}}{a(2^k)}-\frac{a(2^{k-1})}{a(2^k)}\frac{S_{2^{k-1}}}{a(2^{k-1})}\xrightarrow{a.s.}0\Longrightarrow\Longleftarrow
> $$
> Then the claim holds and by 1st Borel-Cantelli's lemma, $\frac{T_k}{a(2^k)}\xrightarrow{a.s.}0$. Note that $T_k=S_{2^{k-1},2^k}$. By $(*)$, 
> $$
> \begin{aligned}
>&\mathbb{P}\left(\max_{2^{k-1}<n\le 2^k}|S_{n,2^k}|>2\varepsilon\cdot a(2^k)\right)\min_{2^{k-1}\le n<2^k}\mathbb{P}\left(|S_{2^{k-1},n}|\le\varepsilon a(2^k)\right)\\
>\le&\mathbb{P}(|S_{n,2^k}|>\varepsilon a(2^k))
>\end{aligned}
> $$
> We only need to show that 
> $$
> \max_{2^{k-1}\le n<2^k}\mathbb{P}(|S_{2^{k-1},2^k}|>\varepsilon a(2^k))\to0\text{ a.s. }k\to\infty
> $$
> We should note that the fact of the same distribution i.e. $S_{n,2^k}\overset{d}{=}S_{2^k-n}$, then with the same discussion of [[#^6b788d|final step]], we can obtain the result. 
> 

> [!question] 2.5.12. (ii)
> (ii) Suppose in addition that $\mathbb{E}X_1 = 0$ and $\mathbb{E}X_1^2 < \infty$. Use the previous exercise and Chebyshev's inequality to conclude that $S_n/n^{1/2}(\log_2 n)^{1/2+\epsilon} \to 0$ a.s.

> [!done]
>
> %% codex-grading-20261103:2.5.12-ii:start %%
> <span style="color:#ef5350;">【评分】4 / 5 分。归一化及两个概率界正确；最后漏写可求和性与 BC，扣 1 分。</span>
>
> <span style="color:#ef5350;">【补证】对固定 </span>$\color{#ef5350}{\delta>0}$<span style="color:#ef5350;">，</span>$\color{#ef5350}{\sum_k\mathbb P(|S_{2^k}|/a(2^k)>\delta)\le\frac{\operatorname{Var}(X_1)}{\delta^2}\sum_k k^{-(1+2\varepsilon)}<\infty}$<span style="color:#ef5350;">。用 BC 并取 </span>$\color{#ef5350}{\delta=1/j}$<span style="color:#ef5350;"> 才能得 a.s. 收敛，不能仅由概率趋零推出。比值式下标统一为 </span>$\color{#ef5350}{a(2^k)/a(2^{k-1})}$<span style="color:#ef5350;">，归一化从 </span>$\color{#ef5350}{n\ge2}$<span style="color:#ef5350;"> 开始即可；这些记号不另扣分。</span>
> %% codex-grading-20261103:2.5.12-ii:end %%
>
> Let $a(n)=n^\frac{1}{2}\log_2^{\frac{1}{2}+\varepsilon}{n}$. We should check 
> - $a(n)\uparrow\infty$
> - $\frac{a(2^n)}{a(2^{k-1})}=\sqrt{2}\left(\frac{n}{n-1}\right)^{\frac{1}{2}+\varepsilon}\le2^{1+\varepsilon}$
> - By Chebyshev's inequality, 
> $$
> \mathbb{P}\left(\frac{|S_n|}{n^\frac{1}{2}\log_2^{\frac{1}{2}+\varepsilon}{n}}>\delta\right)\le\frac{C}{\log_2^{1+2\varepsilon}n}\to0\Longrightarrow\frac{S_n}{a(n)}\xrightarrow{\mathbb{P}}0
> $$
> and 
> $$
> \mathbb{P}\left(\frac{|S_{2^n}|}{2^{\frac{n}{2}}n^{\frac{1}{2}+\varepsilon}}>\delta\right)\le\frac{C}{n^{1+2\varepsilon}}\to0\Longrightarrow\frac{S_{2^n}}{a(2^n)}\xrightarrow{a.s.}0
> $$
> 
>Hence, $\frac{S_{n}}{a(n)}\xrightarrow{a.s.}0$. 