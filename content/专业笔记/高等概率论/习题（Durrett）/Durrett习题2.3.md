> [!info] 作业批改｜163 / 200 分（81.5%）
> 范围：仅本笔记中 18 份已写答案（按题／小问计）；2.3.17(i)–(iv)、2.3.19、2.3.20 为空白，不计入本次满分或扣分。
> 赋分按题目难度及证明工作量分配。按原稿评分，红字为新增评分与必要补证；原文全部保留，批注不计作原稿已完成的证明。
> 评分侧重数学结论、关键推理、量词与符号；一般英文表达不扣分。有效的已有结果引用及等价证明方法予以认可。
> 主要失分集中在 2.3.7 的收敛构造与整列回推、2.3.18 的概率估计；其余多为漏项、量词或符号问题。

> [!question] 2.3.4.
> **Fatou's lemma.** Suppose $X_n \geq 0$ and $X_n \to X$ in probability. Show that $\liminf_{n \to \infty} \mathbb{E}X_n \geq \mathbb{E}X$.

> [!done]
>
> <span style="color:#c62828;">【评分】6 / 8 分。扣分说明见红色批注。</span>
> There exists further subsequence $X_{n(m_k)}\xrightarrow{a.s.}X$. Then 
> $$
> \mathbb{E}X\le \liminf_{k\to\infty}\mathbb{E}X_{n(m_k)}=\liminf_{n\to\infty}\mathbb{E}X_n
> $$
>
> <span style="color:#c62828;">【补证，−2分】先取 </span>$\color{#c62828}{n(m)}$<span style="color:#c62828;"> 使 </span>$\color{#c62828}{\mathbb EX_{n(m)}\to L:=\liminf_n\mathbb EX_n}$<span style="color:#c62828;">，再从中抽取几乎处处收敛子列，最后的等号才有依据。若 </span>$\color{#c62828}{L=\infty}$<span style="color:#c62828;">，结论直接成立；</span>$\color{#c62828}{X\ge0}$<span style="color:#c62828;"> a.s. 可由子列极限得到。</span>

> [!question] 2.3.5. **Dominated convergence.**
> Suppose $X_n \to X$ in probability and (a) $|X_n| \leq Y$ with $\mathbb{E}Y < \infty$ or (b) there is a continuous function $g$ with $g(x) > 0$ for large $x$ with $|x|/g(x) \to 0$ as $|x| \to \infty$ so that $\mathbb{E}g(X_n) \leq C < \infty$ for all $n$. Show that $\mathbb{E}X_n \to \mathbb{E}X$.

> [!done]
>
> <span style="color:#c62828;">【评分】15 / 18 分。扣分说明见红色批注。</span>
> For case (a), we have obtained [[Fubini定理及其应用#^fd31fb|the result]]. We only consider the case (b). Since $\frac{|x|}{g(x)}\to0\text{ as }|x|\to\infty$, for $\varepsilon>0$, there exists $R>0$, as $|x|>R$, we have 
> $$
> |x|\le \varepsilon\cdot g(x)
> $$
> We estimate 
> $$
> \mathbb{E}|X_n|\mathbb{1}_{\{|X_n|> R\}}\le\varepsilon\mathbb{E}g(X_n)\mathbb{1}_{\{|X_n|>R\}}\le C\varepsilon\tag{$*$}
> $$
> We define the truncation
> $$
> T_R(x)=\begin{cases}
>-R,&x<-R\\
>x,&-R\le x\le R\\
>R,&x>R
>\end{cases}
> $$
> Note that we have 
> $$
> |x-T_R(x)|\le |x|\mathbb{1}_{\{|x|>R\}}
> $$
> and 
> $$
> \begin{aligned}
>|\mathbb{E}X_n-\mathbb{E}X|\le\mathbb{E}|X_n-T_R(X_n)|+|\mathbb{E}T_R(X_n)-T_R(X)|+\mathbb{E}|T_R(X)-X|
>\end{aligned}
> $$
> For the first item, by estimation ($*$), we have $\mathbb{E}|X_n-T_R(X_n)|\le C\varepsilon$. 
> 
>For the second item, since $X_n\xrightarrow{\mathbb{P}}X$ and $T_R(x)$ is continuous and bounded, $T_R(X_n)\xrightarrow{\mathbb{P}}T_R(X)$ and $\mathbb{E}T_R(X_n)\to\mathbb{E}T_R(X)$ by [[Fubini定理及其应用#^42f750|the result]]. 
>
>For the final item, since $X_n\xrightarrow{\mathbb{P}}X$, we can take subsequence $X_{n_k}$ s.t. $X_{n_k}\xrightarrow{a.s.}X$ and $g(x)$ is continuous, by Fatou's lemma we obtain 
>$$
>\mathbb{E}g(X)\le \liminf_{k\to\infty}\mathbb{E}g(X_{n_k})\le C
>$$
>Then we can obtain the estimation of ($*$) similarly for the final item. Above all, we obtain
>$$
>|\mathbb{E}X_n-\mathbb{E}X|\le (2C+1)\varepsilon
>$$
>It implies $\mathbb{E}X_n\to\mathbb{E}X$. 
>
> <span style="color:#c62828;">【补充条件，−2分】截断期望的上界及 Fatou 的使用，都需先处理 </span>$\color{#c62828}{g}$<span style="color:#c62828;"> 的负部：按题意将“large x”理解为充分大的 </span>$\color{#c62828}{|x|}$<span style="color:#c62828;">，由连续性得 </span>$\color{#c62828}{g}$<span style="color:#c62828;"> 有下界，可加常数使 </span>$\color{#c62828}{g\ge0}$<span style="color:#c62828;">，并相应调整 </span>$\color{#c62828}{C}$<span style="color:#c62828;">。题面双侧正性的措辞问题不扣分。由 </span>$\color{#c62828}{|x|\le R+\varepsilon g(x)}$<span style="color:#c62828;"> 还应先说明 </span>$\color{#c62828}{X_n,X}$<span style="color:#c62828;"> 可积。</span>
>
> <span style="color:#c62828;">【笔误，−1分】三角不等式中第二项漏了极限项的期望，应为 </span>$\color{#c62828}{|\mathbb ET_R(X_n)-\mathbb ET_R(X)|}$<span style="color:#c62828;">。其余截断思路正确；(a) 的已有结论引用认可，有界情形的引用可经平移缩放使用。</span>


> [!question] 2.3.6.Metric for convergence in probability.(a) 
>  Show that $d(X,Y) = \mathbb{E}(|X-Y|/(1+|X-Y|))$ defines a metric on the set of random variables, i.e., (i) $d(X,Y) = 0$ if and only if $X = Y$ a.s., (ii) $d(X,Y) = d(Y,X)$, (iii) $d(X,Z) \leq d(X,Y) + d(Y,Z)$. 

> [!done]
>
> <span style="color:#c62828;">【评分】5 / 8 分。扣分说明见红色批注。</span>
> For (iii), note that de function $\frac{x}{1+x}$ is [[Durrett习题2.1#^9fde07|increasing]]. Since $|\cdot|$ is a metric, we have 
> $$
> |X-Z|\le|X-Y|+|Y-Z|\Longrightarrow\frac{|X-Z|}{1+|X-Z|}\le\frac{|X-Y|}{1+|X-Y|}+\frac{|Y-Z|}{1+|Y-Z|}
> $$
>
> <span style="color:#c62828;">【漏项，−2分】(i)、(ii) 也需交代：非负被积函数期望为零当且仅当它 a.s. 为零，故 </span>$\color{#c62828}{d(X,Y)=0\iff X=Y}$<span style="color:#c62828;"> a.s.；交换 </span>$\color{#c62828}{X,Y}$<span style="color:#c62828;"> 得对称性。</span>
>
> <span style="color:#c62828;">【补理由，−1分】(iii) 还用到了 </span>$\color{#c62828}{h(s+t)\le h(s)+h(t)}$<span style="color:#c62828;">，单调性本身不足以推出所写结论；可明确引用 2.1.3(i)，然后对点态不等式取期望。严格说这是按 a.s. 相等取等价类后的度量。</span>

>[!question] 2.3.6.Metric for convergence in probability.(b)
>Show that $d(X_n,X) \to 0$ as $n \to \infty$ if and only if $X_n \to X$ in probability. 

>[!done] 
>
> <span style="color:#c62828;">【评分】10 / 10 分。证明正确。</span>
>$\Longrightarrow:$ Since $d(X_n,X)\to0$ i.e. 
>$$
>\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}\to0\text{ as }n\to\infty
>$$
>Then for any $\varepsilon>0$, we have 
>$$
>\begin{aligned}
>\mathbb{P}(|X_n-X|\ge\varepsilon)&=\int_{\{|X_n-X|\ge\varepsilon\}}1d\mathbb{P}\\
>&=\int_{\{|X_n-X|\ge\varepsilon\}}\frac{|X_n-X|}{1+|X_n-X|}\cdot\frac{1+|X_n-X|}{|X_n-X|}{d}\mathbb{P}\\
>&\le \frac{1+\varepsilon}{\varepsilon}\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}\to0
>\end{aligned}
>$$
>Hence, $X_n\xrightarrow{\mathbb{P}}X$. 
>$\Longleftarrow:$ Suppose $X_n\xrightarrow{\mathbb{P}} X$, then for any $\varepsilon>0$
>$$
>\begin{aligned}
>\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}&=\left(\int_{\{|X_n-X|\ge\varepsilon\}}+\int_{\{|X_n-X|<\varepsilon\}}\right)\frac{|X_n-X|}{1+|X_n-X|}{d}\mathbb{P}\\
>&\le\frac{\varepsilon}{1+\varepsilon}+\mathbb{P}(|X_n-X|\ge\varepsilon)
>\end{aligned}
>$$
>We obtain
>$$
>\limsup_{n\to\infty}\mathbb{E}\frac{|X_n-X|}{1+|X_n-X|}\le\frac{\varepsilon}{1+\varepsilon}\text{ and }\varepsilon\to0^+
>$$

> [!question] 2.3.7.
> Show that random variables are a complete space under the metric defined in the previous exercise, i.e., if $d(X_m, X_n) \to 0$ whenever $m, n \to \infty$ then there is a r.v. $X_\infty$ so that $X_n \to X_\infty$ in probability.

> [!done]
>
> <span style="color:#c62828;">【评分】7 / 18 分。扣分说明见红色批注。</span>
> Note that 
> $$
> \mathbb{P}(|X_m-X_n|\ge\varepsilon)\le\frac{1+\varepsilon}{\varepsilon}d(X_m,X_n)\to0\text{ as }m,n\to\infty
> $$
> We can take subsequence $X_{n_k}$ s.t. 
> $$
> \mathbb{P}(|X_{n_{k+1}}-X_{n_k}|\ge\varepsilon)\le\frac{\varepsilon}{2^{k+1}}\Longrightarrow\sum_{k=1}^{\infty}\mathbb{P}(|X_{n_{k+1}}-X_{n_k}|\ge\varepsilon)\le\varepsilon
> $$
> By [[积分与期望#^5c2707|Borel-Cantelli's lemma]], 
> $$
> \mathbb{P}(|X_{n_{k+1}}-X_{n_k}|\ge\varepsilon,\text{i.o.})=0
> $$
> i.e. for any $\varepsilon>0$, there exists further subsequence $\{X_{n_{k}}\}$ converges and thus $X_n\to X_{\infty}$.
>
> <span style="color:#c62828;">【关键缺口，−7分】固定阈值下的相邻差最终变小，不能推出子列收敛；即使相邻差趋于零，也未必是 Cauchy 列。应一次选定子列，使 </span>$\color{#c62828}{\mathbb P(|X_{n_{k+1}}-X_{n_k}|>2^{-k})\le2^{-k}}$<span style="color:#c62828;">。由 Borel–Cantelli，a.s. 最终相邻差不超过 </span>$\color{#c62828}{2^{-k}}$<span style="color:#c62828;">；再将相邻差累加，利用几何级数尾和证明 Cauchy，得到有限极限 </span>$\color{#c62828}{X_\infty}$<span style="color:#c62828;">（零测例外集上定义为 0，保证可测）。</span>
>
> <span style="color:#c62828;">【整列回推，−4分】还需用依概率 Cauchy 条件，结合子列 a.s. 收敛推出的依概率收敛，补上：</span>
> $$
> \color{#c62828}{\mathbb P(|X_n-X_\infty|>\varepsilon)\le\mathbb P(|X_n-X_{n_k}|>\varepsilon/2)+\mathbb P(|X_{n_k}-X_\infty|>\varepsilon/2).}
> $$
> <span style="color:#c62828;">先选足够大的 k 使第二项小，并使 n_k 超过 Cauchy 阈值，再令 n 足够大使第一项小。</span>


> [!question] 2.3.8.
> Let $A_n$ be a sequence of independent events with $\mathbb{P}(A_n) < 1$ for all $n$. Show that $\mathbb{P}(\cup A_n) = 1$ implies $\sum_n \mathbb{P}(A_n) = \infty$ and hence $\mathbb{P}(A_n \text{ i.o.}) = 1$.

> [!done] 
>
> <span style="color:#c62828;">【评分】9 / 10 分。扣分说明见红色批注。</span>
> We consider 
> $$
> \mathbb{P}\left(\bigcup_{n=1}^{\infty}A_n\right)=1\Longrightarrow\mathbb{P}\left(\bigcap_{n=1}^{\infty}A_n^c\right)=\prod_{n=1}^{\infty}(1-\mathbb{P}(A_n))=0
> $$
> We suppose $\sum_{n=1}^{\infty}\mathbb{P}(A_n)<\infty$, then $\mathbb{P}(A_n)\to0$, for sufficiently large $M,N\in\mathbb{N}$, we have $\mathbb{P}(A_n)\le\frac{1}{2},n\ge N,M$. Then 
> $$
> \prod_{n=N}^{M}(1-\mathbb{P}(A_n))=e^{\sum_{n=N}^{M}\log{(1-\mathbb{P}(A_n))}}\ge e^{-2\sum_{n=N}^{M}\mathbb{P}(A_n)}\ge e^{-2\sum_{n=N}^{\infty}\mathbb{P}(A_n)}>0
> $$
> It is contradict with $\prod_{n=1}^{\infty}(1-\mathbb{P}(A_n))=0$. Hence, $\sum_{n=1}^{\infty}\mathbb{P}(A_n)=\infty$. 
>
> <span style="color:#c62828;">【结尾补充，−1分】还需由独立性和 Borel–Cantelli 第二引理写出 </span>$\color{#c62828}{\mathbb P(A_n\ \mathrm{i.o.})=1}$<span style="color:#c62828;">。乘积论证另补一句：固定 </span>$\color{#c62828}{N}$<span style="color:#c62828;">，前 </span>$\color{#c62828}{N-1}$<span style="color:#c62828;"> 个因子的乘积严格为正，故尾部的一致正下界使整个乘积也严格为正（此处视为可补明的省略，不另扣分）。</span>


> [!question] 2.3.9. (i)
> (i) If $\mathbb{P}(A_n) \to 0$ and $\sum_{n=1}^\infty \mathbb{P}(A_n^c \cap A_{n+1}) < \infty$ then $\mathbb{P}(A_n \text{ i.o.}) = 0$.

> [!done]
>
> <span style="color:#c62828;">【评分】12 / 12 分。证明正确。</span>
> We denote $B_n:=A_n^c\cap A_{n+1}$. By Borel-Cantelli's lemma, we have $\mathbb{P}(B_n,\text{i.o.})=0$. For fixed $m\in\mathbb{N}$, let 
> $$
> C_m\triangleq\bigcap_{n=m}^{\infty}A_n
> $$
> Note that for $n\ge m$, $C_m\subseteq A_n$ and $\mathbb{P}(A_n)\to0$,
> $$
> 0\le\mathbb{P}(C_m)\le\mathbb{P}(A_n)\to0
> $$
> Therefore, $\mathbb{P}(C_m)=0$ and thus $\mathbb{P}(\bigcup_{m=1}^{\infty}C_m)=0$. Now we claim that 
> $$
> \limsup_{n\to\infty}A_n\subseteq\limsup_{n\to\infty}B_n\cup\bigcup_{m=1}^{\infty}C_m
> $$
> For $\omega\in\limsup_{n\to\infty}A_n$, suppose $\omega\notin\limsup_{n\to\infty}B_n$ and we W.T.S. $\omega\in\bigcup_{m=1}^{\infty}C_m$. Since $\omega\notin\limsup_{n\to\infty}B_n$, it implies there exists $N\in\mathbb{N}$, for $n\ge N$, 
> $$
> \omega\notin B_n=A_n^c\cap A_{n+1}\Longrightarrow\omega\in A_n\cup A_{n+1}^c
> $$
> If $\omega\notin A_n$, then $\omega\in A_{n+1}^c$ i.e. $\omega\notin A_{n+1}$. If we suppose for some $k\ge N$ s.t. $\omega\notin A_k$ and thus $\omega\notin A_{k+1},A_{k+2},\cdots$, in other words, $A_n$ occurs finite times. It is a contradiction with $\omega\in\limsup_{n\to\infty}A_n$. Therefore, 
> $$
> \omega\in\bigcap_{n=N}^{\infty}A_n\subseteq\bigcup_{m=1}^{\infty}C_m
> $$
> Finally, we have 
> $$
> \mathbb{P}(A_n,\text{i.o.})\le\mathbb{P}(B_n,\text{i.o.})+\mathbb{P}\left(\bigcup_{m=1}^{\infty}C_m\right)=0\Longrightarrow\mathbb{P}(A_n,\text{i.o.})=0
> $$

> [!question] 2.3.9. (ii)
> (ii) Find an example of a sequence $A_n$ to which the result in (i) can be applied but the Borel-Cantelli lemma cannot.

> [!done]
>
> <span style="color:#c62828;">【评分】6 / 6 分。证明正确。</span>
> We take $\Omega=[0,1],\mathbb{P}=\text{Leb},A_n=[0,\frac{1}{n}]$. we have $\text{Leb}(A_n)=\frac{1}{n}\to0$ and $\text{Leb}(A_n^c\cap A_{n+1})=\text{Leb}(\emptyset)=0$, then $\mathbb{P}(A_n,\text{i.o.})=\text{Leb}(\{0\})=0$. But we check the condition of Borel-Cantelli lemma, 
> $$
> \sum_{n=1}^{\infty}\text{Leb}(A_n)=\sum_{n=1}^{\infty}\frac{1}{n}=\infty
> $$

> [!question] 2.3.10.**Kochen-Stone lemma.**
> Suppose $\sum \mathbb{P}(A_k) = \infty$. Use Exercises 1.6.6 and 2.3.1 to show that if
> $$
> \limsup_{n \to \infty} \left( \sum_{k=1}^n \mathbb{P}(A_k) \right)^2 \Bigg/ \left( \sum_{1 \leq j,k \leq n} \mathbb{P}(A_j \cap A_k) \right) = \alpha > 0
> $$
> then $\mathbb{P}(A_n \text{ i.o.}) \geq \alpha$. The case $\alpha = 1$ contains Theorem 2.3.7.

> [!done]
>
> <span style="color:#c62828;">【评分】13 / 14 分。扣分说明见红色批注。</span>
> Fix $m\in\mathbb{N}$, for $n\ge m$, consider 
> $$
> S_{m,n}=\sum_{k=m}^{n}\mathbb{1}_{A_k},\{S_{m,n}>0\}=\bigcup_{k=m}^{n}A_k
> $$
> By [[Durrett习题1.6#^5033bb|E.x.1.6.6]], we have 
> $$
> \mathbb{P}\left(\bigcup_{k=m}^{n}A_k\right)\ge\frac{\left(\sum_{k=m}^{n}\mathbb{P}(A_k)\right)^2}{\sum_{m\le j,k\le n}\mathbb{P}(A_j\cap A_k)}=\frac{\left(\sum_{k=m}^{n}\mathbb{P}(A_k)\right)^2}{\left(\sum_{k=1}^{n}\mathbb{P}(A_k)\right)^2}\frac{\left(\sum_{k=1}^{n}\mathbb{P}(A_k)\right)^2}{\sum_{m\le j,k\le n}\mathbb{P}(A_j\cap A_k)}
> $$
> Let $T_n:=\sum_{k=1}^{n}\mathbb{P}(A_k)$, note that 
> $$
> \frac{\left(\sum_{k=m}^{n}\mathbb{P}(A_k)\right)^2}{\left(\sum_{k=1}^{n}\mathbb{P}(A_k)\right)^2}=\frac{(T_n-T_{m-1})^2}{T_n^2}\to1\text{ as }n\to\infty
> $$
> Then we obtain
> $$
> \alpha=\limsup_{n\to\infty}\frac{\left(\sum_{k=1}^{n}\mathbb{P}(A_k)\right)^2}{\sum_{1\le j,k\le n}\mathbb{P}(A_j\cap A_k)}\le\mathbb{P}\left(\bigcup_{k=m}^{\infty}A_k\right)
> $$
> Note that LHS is decreasing and low bounded, then 
> $$
> \alpha\le \lim_{n\to\infty}\mathbb{P}\left(\bigcup_{k=m}^{\infty}A_k\right)=\mathbb{P}\left(\bigcap_{m=1}^{\infty}\bigcup_{k=m}^{\infty}A_k\right)=\mathbb{P}(A_n,\text{i.o.})
> $$
>
> <span style="color:#c62828;">【下标／文字，−1分】递减有下界的是右侧概率，变量是 </span>$\color{#c62828}{m}$<span style="color:#c62828;">：末行 </span>$\color{#c62828}{\lim_{n\to\infty}}$<span style="color:#c62828;"> 应改为 </span>$\color{#c62828}{\lim_{m\to\infty}}$<span style="color:#c62828;">，LHS 应改为 RHS，并由从上连续性取极限。前一步还用到尾部双和不超过从 1 开始的双和，建议补一句。直接用连续性替代 2.3.1 是有效证明，不扣方法分。</span>


> [!question] 2.3.11. (i)
> Let $X_1, X_2, \dots$ be independent with $\mathbb{P}(X_n = 1) = p_n$ and $\mathbb{P}(X_n = 0) = 1 - p_n$. Show that (i) $X_n \to 0$ in probability if and only if $p_n \to 0$.

> [!done]
>
> <span style="color:#c62828;">【评分】6 / 6 分。证明正确。</span>
> Note that $\mathbb{E}[X_n]=\mathbb{E}[X_n^2]=p_n$. "$\Longleftarrow$" is obviously. We prove "$\Longrightarrow$". We  can use the metric characterization of convergence in probability, we have 
> $$
> \mathbb{E}\frac{|X_n|}{1+|X_n|}\to0\Longrightarrow\frac{1}{2}p_n\to0
> $$

> [!question] 2.3.11. (ii)
> (ii) $X_n \to 0$ a.s. if and only if $\sum p_n < \infty$.

> [!done]
>
> <span style="color:#c62828;">【评分】8 / 8 分。证明正确。</span>
> $\Longleftarrow:$ For $0<\varepsilon<1$, note that 
> $$
> \sum_{n=1}^{\infty}\mathbb{P}(|X_n|\ge\varepsilon)=\sum_{n=1}^{\infty}\mathbb{P}(X_n\ge\varepsilon)=\sum_{n=1}^{\infty}p_n<\infty
> $$
> By Borel-Cantelli's lemma, 
> $$
> \mathbb{P}\left(\{|X_n|\ge\varepsilon\},\text{i.o.}\right)=0\text{ i.e. }\exists N\in\mathbb{N},n\ge N,|X_n|\le\varepsilon,\text{a.s.-}\mathbb{P}
> $$
> It implies $X_n\xrightarrow{a.s.}0$.
> 
>$\Longrightarrow:$ Suppose $\sum_{n=1}^{\infty}p_n=\infty$, by Borel-Cantelli's lemma, 
>$$
>\mathbb{P}(X_n=1,\text{i.o.})=1\text{ i.e. }X_n=1\text{ for infinite n}
>$$
>It is a contradiction with $X_n\xrightarrow{a.s.}0$.

> [!question] 2.3.12.
> Let $X_1, X_2, \dots$ be a sequence of r.v.'s on $(\Omega, \mathcal{F}, \mathbb{P})$ where $\Omega$ is a countable set and $\mathcal{F}$ consists of all subsets of $\Omega$. Show that $X_n \to X$ in probability implies $X_n \to X$ a.s.

> [!done]
>
> <span style="color:#c62828;">【评分】8 / 10 分。扣分说明见红色批注。</span>
> We consider the point $\{\omega\}$ with positive probability. If it satisfies for any $\varepsilon>0$, $|X_n(\omega)-X(\omega)|\ge\varepsilon$, i.e. 
> $$
> \{\omega\}\subseteq\left\{\omega:|X_n(\omega)-X(\omega)|\ge\varepsilon\right\}\Longrightarrow0<\mathbb{P}\{\omega\}\le\mathbb{P}(|X_n(\omega)-X(\omega)|\ge\varepsilon)
> $$ 
> But $\mathbb{P}(|X_n-X|\ge\varepsilon)\to\text{ as }n\to\infty$, we obtain $\mathbb{P}\{\omega\}=0\Longrightarrow\Longleftarrow$ with $\mathbb{P}\{\omega\}>0$. It implies that $\omega\notin\left\{\omega:|X_n(\omega)-X(\omega)|\ge\varepsilon\right\}$ and thus $\omega\in\left\{\omega:|X_n(\omega)-X(\omega)|<\varepsilon\right\}$ which is 
> $$
> \forall\varepsilon>0,\exists N\in\mathbb{N},\forall n\ge N,|X_n(\omega)-X(\omega)|<\varepsilon
> $$
> i.e. $X_n(\omega)\to X(\omega)$. Finally, we should consider the point with zero probability. We denote it by 
> $$
> N=\left\{\omega:\mathbb{P}\{\omega\}=0\right\}
> $$
> Since $\Omega$ is countable, and $N$ is at most coutable, therefore, 
> $$
> \mathbb{P}(N)=\sum_{\omega\in N}\mathbb{P}\{\omega\}=0
> $$
> Hence,  $X_n\xrightarrow{a.s.}X$. 
>
> <span style="color:#c62828;">【量词缺口，−2分】应固定正概率点及 </span>$\color{#c62828}{\varepsilon>0}$<span style="color:#c62828;">，假设偏差对无穷多个 </span>$\color{#c62828}{n}$<span style="color:#c62828;"> 成立，再沿这些下标取极限得到矛盾；不能把单个 </span>$\color{#c62828}{n}$<span style="color:#c62828;"> 上的不等式直接令 </span>$\color{#c62828}{n\to\infty}$<span style="color:#c62828;">。也可直接取 </span>$\color{#c62828}{N}$<span style="color:#c62828;"> 使所有 </span>$\color{#c62828}{n\ge N}$<span style="color:#c62828;"> 的偏差事件概率小于 </span>$\color{#c62828}{\mathbb P\{\omega\}}$<span style="color:#c62828;">。原文“</span>$\color{#c62828}{\to}$<span style="color:#c62828;"> as”漏写 0；最后的可数零概率集处理正确。</span>


> [!question] 2.3.13.
> If $X_n$ is any sequence of random variables, there are constants $c_n \to \infty$ so that $X_n/c_n \to 0$ a.s.

> [!done]
>
> <span style="color:#c62828;">【评分】6 / 8 分。扣分说明见红色批注。</span>
> We choose $c_n$ like 
> $$
> a_n=\min\left\{m:\mathbb{P}(|X_n|>m)<\frac{1}{2^n}\right\},c_n=n\cdot a_n
> $$
> such $c_n\ge n$ and thus $c_n\to\infty$, s.t. 
> $$
> \mathbb{P}\left(\left|\frac{X_n}{c_n}\right|\ge\frac{1}{n}\right)\le\frac{1}{2^n}
> $$
> By Borel-Cantelli's lemma, for large $n$, 
> $$
> \left|\frac{X_n}{c_n}\right|\le\frac{1}{n},\text{a.s.-}\mathbb{P}\Longrightarrow\frac{X_n}{c_n}\to0
> $$
>
> <span style="color:#c62828;">【定义，−1分】最小值须限定 </span>$\color{#c62828}{m\in\{1,2,\ldots\}}$<span style="color:#c62828;">；由每个固定 </span>$\color{#c62828}{n}$<span style="color:#c62828;"> 的尾概率趋于 0，说明此最小值存在，且 </span>$\color{#c62828}{a_n\ge1}$<span style="color:#c62828;">。</span>
>
> <span style="color:#c62828;">【事件符号，−1分】定义控制的是 </span>$\color{#c62828}{\mathbb P(|X_n|>a_n)}$<span style="color:#c62828;">，后面的事件应写 </span>$\color{#c62828}{|X_n/c_n|>1/n}$<span style="color:#c62828;">，不能直接改成 </span>$\color{#c62828}{\ge}$<span style="color:#c62828;">（变量可能在阈值处有原子）。改成严格大于后，Borel–Cantelli 的结论仍给出最终 </span>$\color{#c62828}{|X_n/c_n|\le1/n}$<span style="color:#c62828;">。</span>

> [!question] 2.3.14.
> Let $X_1, X_2, \dots$ be independent. Show that $\sup X_n < \infty$ a.s. if and only if $\sum_n \mathbb{P}(X_n > A) < \infty$ for some $A$.

> [!done]
>
> <span style="color:#c62828;">【评分】8 / 10 分。扣分说明见红色批注。</span>
> $\Longleftarrow:$ By Borel-Cantelli's lemma, $\mathbb{P}(X_n>A,\text{i.o.})=0$ which implies for such $A>0$, there exists $N\in\mathbb{N},\forall n\ge N$, $X_n\le A$. Let $M_1=\max\{X_1,\cdots,X_{N}\}$, then $\sup_{n}X_n\le M_1\wedge A<\infty$. 
> 
>$\Longrightarrow:$ Suppose $\sum_{n=1}^{\infty}\mathbb{P}(X_n>A)=\infty$ for any $A$, then by Borel-Cantelli's lemma, $\mathbb{P}(X_n>A,\text{i.o.})=1$ which implies for any $N\in\mathbb{N}$, there exists $n_0>N$ s.t. $X_{n_0}>A$. It is a contradiction with $\sup_{n}X_n<\infty$. 
>
> <span style="color:#c62828;">【符号，−1分】上界应为 </span>$\color{#c62828}{M_1\vee A=\max\{M_1,A\}}$<span style="color:#c62828;">，不是 </span>$\color{#c62828}{M_1\wedge A}$<span style="color:#c62828;">。</span>
>
> <span style="color:#c62828;">【量词，−1分】必要性中，超过某个固定 </span>$\color{#c62828}{A}$<span style="color:#c62828;"> 无穷次并不与上确界有限矛盾。应分别取 </span>$\color{#c62828}{A=1,2,\ldots}$<span style="color:#c62828;">，对这些概率为 1 的事件取可数交，才得到 </span>$\color{#c62828}{\sup_nX_n=\infty}$<span style="color:#c62828;"> a.s.，形成矛盾。</span>

> [!question] 2.3.15. (i)
> Let $X_1, X_2, \dots$ be i.i.d. with $\mathbb{P}(X_i > x) = e^{-x}$, let $M_n = \max_{1 \leq m \leq n} X_m$. Show that (i) $\limsup_{n \to \infty} X_n / \log n = 1$ a.s.

> [!done]
>
> <span style="color:#c62828;">【评分】9 / 10 分。扣分说明见红色批注。</span>
>  We consider 
> $$
> \mathbb{P}\left\{\frac{X_n}{\log{n}}>1+\varepsilon\right\}=\frac{1}{n^{1+\varepsilon}}\Longrightarrow\sum_{n=1}^{\infty}\mathbb{P}\left\{\frac{X_n}{\log{n}}>1+\varepsilon\right\}<\infty
> $$
> By Borel-Cantelli's lemma, we obtain $\mathbb{P}\left(\frac{X_n}{\log{n}}>1+\varepsilon,\text{i.o.}\right)=0$ i.e. there exists $N$, for $n\ge N$, we have 
> $$
> \frac{X_n}{\log{n}}\le 1+\varepsilon\Longrightarrow\limsup_{n\to\infty}\frac{X_n}{\log{n}}\le 1+\varepsilon
> $$
> and let $\varepsilon\to0^+$, we obtain $\limsup_{n\to\infty}\frac{X_n}{\log{n}}\le 1$. For another direction, 
> $$
> \mathbb{P}\left\{\frac{X_n}{\log{n}}>1\right\}=\frac{1}{n}\Longrightarrow\sum_{n=1}^{\infty}\mathbb{P}\left\{\frac{X_n}{\log{n}}>1\right\}=\infty
> $$
> By Borel-Cantelli's lemma, $\mathbb{P}\left(\frac{X_n}{\log{n}}>1,\text{i.o.}\right)=1$ i.e. $\limsup_{n\to\infty}\frac{X_n}{\log{n}}\ge1$. Above all, $\limsup_{n\to\infty}\frac{X_n}{\log{n}}=1,a\text{ a.s.}$
>
> <span style="color:#c62828;">【概率 1 事件，−1分】上界最后取 </span>$\color{#c62828}{\varepsilon=1/k}$<span style="color:#c62828;">，对 </span>$\color{#c62828}{k}$<span style="color:#c62828;"> 取可数个概率 1 事件的交，再令 </span>$\color{#c62828}{k\to\infty}$<span style="color:#c62828;">；下界所用第二引理的独立性来自 </span>$\color{#c62828}{X_n}$<span style="color:#c62828;"> 独立。所有含 </span>$\color{#c62828}{\log n}$<span style="color:#c62828;"> 的式子从 </span>$\color{#c62828}{n=2}$<span style="color:#c62828;"> 起写（起点笔误不另扣分）。</span>


> [!question] 2.3.15. (ii)
> (ii) $M_n / \log n \to 1$ a.s.

> [!done]
>
> <span style="color:#c62828;">【评分】13 / 14 分。扣分说明见红色批注。</span>
> It is well-known 
> $$
> \mathbb{P}(M_n\le x)=(1-e^{-x})^n
> $$
> Since $\limsup_{n\to\infty}\frac{X_n}{\log{n}}=1$, there exists $N\in\mathbb{N}$, for $n\ge m\ge N$, $X_m\le (1+\varepsilon)\log{n}$. Then 
> $$
> M_n(\omega)\le\max\left\{\max_{1\le k\le N}X_k,(1+\varepsilon)\log{n}\right\}
> $$
> For sufficiently large $n$, $(1+\varepsilon)\log{n}\ge\max_{1\le k\le N}X_k$. Therefore, 
> $$
> \limsup_{n\to\infty}\frac{M_n}{\log{n}}\le1+\varepsilon
> $$
> For another direction, we compute
> $$
> \mathbb{P}\left(\frac{M_n}{\log{n}}\le 1-\varepsilon\right)\le\left(1-e^{-(1-\varepsilon)\log{n}}\right)^n\le e^{-n^\varepsilon}\Longrightarrow\sum_{n=1}^{\infty}\mathbb{P}\left(\frac{M_n}{\log{n}}\le 1-\varepsilon\right)<\infty
> $$
> Then by Borel-Cantelli's lemma, we obtain $\mathbb{P}(\frac{M_n}{\log{n}}\le 1-\varepsilon,\text{i.o.})=0$, then 
> $$
> \liminf_{n\to\infty}\frac{M_n}{\log{n}}\ge1-\varepsilon
> $$
> Above all, we obtain
> $$
> 1-\varepsilon\le\liminf_{n\to\infty}\frac{M_n}{\log{n}}\le\limsup_{n\to\infty}\frac{M_n}{\log{n}}\le1+\varepsilon
> $$
> and let $\varepsilon\to0^+$, we have $\lim_{n\to\infty}\frac{M_n}{\log{n}}=1$. 
>
> <span style="color:#c62828;">【范围与共同事件，−1分】先固定 </span>$\color{#c62828}{0<\varepsilon<1}$<span style="color:#c62828;">、</span>$\color{#c62828}{n\ge2}$<span style="color:#c62828;">（分布公式用于 </span>$\color{#c62828}{x\ge0}$<span style="color:#c62828;">）；最后取 </span>$\color{#c62828}{\varepsilon=1/k}$<span style="color:#c62828;">、</span>$\color{#c62828}{k\ge2}$<span style="color:#c62828;">，在共同的概率 1 事件上夹逼。上下界证明思路正确；所用 </span>$\color{#c62828}{\sum_n e^{-n^\varepsilon}<\infty}$<span style="color:#c62828;"> 可由最终 </span>$\color{#c62828}{e^{-n^\varepsilon}\le n^{-2}}$<span style="color:#c62828;"> 说明。</span>


> [!question] 2.3.16.
> Let $X_1, X_2, \dots$ be i.i.d. with distribution $F$, let $\lambda_n \uparrow \infty$, and let $A_n = \{\max_{1 \leq m \leq n} X_m > \lambda_n\}$. Show that $\mathbb{P}(A_n \text{ i.o.}) = 0$ or $1$ according as $\sum_{n \geq 1} (1 - F(\lambda_n)) < \infty$ or $= \infty$.

> [!done]
>
> <span style="color:#c62828;">【评分】11 / 12 分。扣分说明见红色批注。</span>
>Let $B_n=\{X_n>\lambda_n\}$, we claim that 
>$$
>\{A_n,\text{i.o.}\}=\{B_n,\text{i.o.}\}
>$$
>It is obvious that $\{B_n,\text{i.o.}\}\subseteq\{A_n,\text{i.o.}\}$. Suppose $\omega\notin\{B_n,\text{i.o.}\}$, then there exists $k\in\mathbb{N}$, for $m\ge k$, $X_m(\omega)\le \lambda_n$. Consider 
>$$
>\max_{1\le m\le n}X_m(\omega)=\max\left\{\max_{1\le m\le k}X_m(\omega),\max_{k+1\le m\le n}X_m(\omega)\right\}
>$$
>We have obtained $\max_{k+1\le m\le n}X_m(\omega)\le \lambda_n$. For fixed $k$, there exists $n_0$ s.t. $n\ge n_0$, it holds $\lambda_n>\max_{1\le m\le k}X_m(\omega)$. Therefore, $\max_{1\le m\le n}X_m(\omega)\le \lambda_n$ for large $n$ $\Longrightarrow\Longleftarrow$ with $\omega\in\{A_n,\text{i.o.}\}$. 
>we have 
>$$
>\sum_{n=1}^{\infty}\mathbb{P}(B_n)<\infty\text{ or }=\infty\Longrightarrow\mathbb{P}(B_n,\text{i.o.})=\mathbb{P}(A_n,\text{i.o.})=0\text{ or }=1
>$$
>
> <span style="color:#c62828;">【下标，−1分】由 </span>$\color{#c62828}{B_m}$<span style="color:#c62828;"> 最终不发生，应先得 </span>$\color{#c62828}{X_m(\omega)\le\lambda_m}$<span style="color:#c62828;">，不是直接写 </span>$\color{#c62828}{\lambda_n}$<span style="color:#c62828;">；当 </span>$\color{#c62828}{m\le n}$<span style="color:#c62828;"> 时再用单调性得 </span>$\color{#c62828}{\lambda_m\le\lambda_n}$<span style="color:#c62828;">。之后实际已证明 </span>$\color{#c62828}{\omega\notin\{A_n\ \mathrm{i.o.}\}}$<span style="color:#c62828;">，可直接完成包含关系，无须另写未设定的反证前提。</span>


> [!question] 2.3.17. (i)
> Let $Y_1, Y_2, \dots$ be i.i.d. Find necessary and sufficient conditions for (i) $Y_n/n \to 0$ almost surely.

> [!done]

> [!question] 2.3.17. (ii)
> (ii) $(\max_{m \leq n} Y_m)/n \to 0$ almost surely.

> [!done]

> [!question] 2.3.17. (iii)
> (iii) $(\max_{m \leq n} Y_m)/n \to 0$ in probability.

> [!done]

> [!question] 2.3.17. (iv)
> (iv) $Y_n/n \to 0$ in probability.

> [!done]

> [!question] 2.3.18.
> Let $0 \leq X_1 \leq X_2 \dots$ be random variables with $\mathbb{E}X_n \sim an^\alpha$ with $a, \alpha > 0$, and $\text{var}(X_n) \leq Bn^\beta$ with $\beta < 2\alpha$. Show that $X_n/n^\alpha \to a$ a.s.

> [!done]
>
> <span style="color:#c62828;">【评分】11 / 18 分。扣分说明见红色批注。</span>
> Note that 
> $$
> \mathbb{P}\left(\left|\frac{X_n}{n^\alpha}-a\right|\ge\varepsilon\right)\le\frac{\text{Var}(X_n)}{\varepsilon^2n^\alpha}-\frac{2a\mathbb{E}X_n}{\varepsilon^2n^\alpha}+\frac{a^2(\mathbb{E}X_n)^2}{\varepsilon^2n^{2\alpha}}+\frac{a^2}{\varepsilon^2}\to0\text{ as }n\to\infty
> $$
> and we obtain
> $$
> \mathbb{P}\left(\left|\frac{X_n}{n^\alpha}-a\right|\ge\varepsilon\right)\sim\frac{1}{n^{2\alpha-\beta}}\text{ as }n\to\infty
> $$
>
> <span style="color:#c62828;">【概率估计，−5分】开头的二阶矩展开有误；正确展开为 </span>$\color{#c62828}{\operatorname{Var}(X_n)/n^{2\alpha}+(\mathbb EX_n/n^\alpha-a)^2}$<span style="color:#c62828;">。更不能由上界推出概率的渐近等价 </span>$\color{#c62828}{\sim n^{-\delta}}$<span style="color:#c62828;">，现有条件不保证偏差概率有这种下界。对固定 </span>$\color{#c62828}{\varepsilon>0}$<span style="color:#c62828;">，先取 </span>$\color{#c62828}{n}$<span style="color:#c62828;"> 足够大使 </span>$\color{#c62828}{|\mathbb EX_n/n^\alpha-a|<\varepsilon/2}$<span style="color:#c62828;">，然后使用：</span>
> $$
> \color{#c62828}{\mathbb P\!\left(\left|\frac{X_n}{n^\alpha}-a\right|\ge\varepsilon\right)\le\mathbb P\!\left(|X_n-\mathbb EX_n|\ge\frac{\varepsilon n^\alpha}{2}\right)\le\frac{4B}{\varepsilon^2}n^{-\delta},\quad\delta=2\alpha-\beta>0.}
> $$
>
> <span style="color:#c62828;">【取整，−1分】所选下标有效，但因为有向下取整，</span>$\color{#c62828}{C/n_k^\delta=C/k^{1+\delta}}$<span style="color:#c62828;"> 不是等式。对大 </span>$\color{#c62828}{k}$<span style="color:#c62828;">，用 </span>$\color{#c62828}{n_k\ge k^{1+1/\delta}/2}$<span style="color:#c62828;"> 得 </span>$\color{#c62828}{C/n_k^\delta\le C2^\delta/k^{1+\delta}}$<span style="color:#c62828;"> 即可。</span>
>
> <span style="color:#c62828;">【共同事件，−1分】Borel–Cantelli 后取 </span>$\color{#c62828}{\varepsilon=1/j}$<span style="color:#c62828;">，在可数交得到的概率 1 事件上令 </span>$\color{#c62828}{j\to\infty}$<span style="color:#c62828;">。最后的单调夹逼正确，补明 </span>$\color{#c62828}{n_{k+1}/n_k\to1}$<span style="color:#c62828;">，并对每个 </span>$\color{#c62828}{n}$<span style="color:#c62828;"> 选对应的 </span>$\color{#c62828}{k=k(n)}$<span style="color:#c62828;"> 即可。</span>
>
> We choose subsequence $n_k\triangleq\lfloor k^{1+\frac{1}{\delta}}\rfloor$ where $\delta=2\alpha-\beta$. Therefore, by above estimation, we have 
> $$
> \mathbb{P}\left(\left|\frac{X_{n_k}}{n_k^\alpha}-a\right|\ge\varepsilon\right)\le\frac{C}{n_k^{\delta}}=\frac{C}{k^{1+\delta}}
> $$
> By Borel-Cantelli's lemma, we have 
> $$
> \limsup_{k\to\infty}\left|\frac{X_{n_k}}{n_k^\alpha}-a\right|\le \varepsilon
> $$
> and let $\varepsilon\to0^+$, $\frac{X_{n_k}}{n_{k}^\alpha}\xrightarrow{a.s.}a$. For such $n_k$ and any $n\in\mathbb{N}$, note that $n_{k}\le n\le n_{k+1}$, it holds 
> $$
> \frac{X_{n_k}}{n_{k}^\alpha}\frac{n^\alpha_k}{n_{k+1}^\alpha}=\frac{X_{n_k}}{n_{k+1}^\alpha}\le\frac{X_n}{n^\alpha}\le\frac{X_{n_{k+1}}}{n_k^\alpha}=\frac{X_{n_{k+1}}}{n_{k+1}^\alpha}\frac{n^\alpha_{k+1}}{n_{k}^\alpha}
> $$
> as $k\to\infty$, LHS and RHS both converge to $a$ and thus $\frac{X_n}{n^\alpha}\xrightarrow{a.s.}a$. 

> [!question] 2.3.19.
> Let $X_n$ be independent Poisson r.v.'s with $\mathbb{E}X_n = \lambda_n$, and let $S_n = X_1 + \dots + X_n$. Show that if $\sum \lambda_n = \infty$ then $S_n / \mathbb{E}S_n \to 1$ a.s.

> [!done]
> 

> [!question] 2.3.20.
> Show that if $X_n$ is the outcome of the $n$th play of the St. Petersburg game (Example 2.2.16) then $\limsup_{n \to \infty} X_n/(n \log_2 n) = \infty$ a.s. and hence the same result holds for $S_n$. This shows that the convergence $S_n/(n \log_2 n) \to 1$ in probability proved in Section 2.2 does not occur a.s.

> [!done]
> 