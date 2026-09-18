前面都是基于模型来讲的算法，从这一章开始是基于无模型的算法，当没有模型的时候我们就需要数据（采样）。
>[!example] 启发例子：求期望（大数定律）
>对于基于模型的情况，我们已知概率分布，可以直接求随机变量$X$的期望，
>$$
>\mathbb{E}[X]=\sum_{x\in\mathcal{X}}p(x)x
>$$
>对于无模型的情况，我们不知道概率分布，那么就需要数据$x_1,\cdots,x_n$，那么
>$$
>\bar{x}\triangleq\frac{1}{n}\sum_{i=1}^{n}x_i\approx\mathbb{E}[X]
>$$
>当数据足够多的时候，有
>$$
>\bar{x}\xrightarrow{\mathbb{P}}\mathbb{E}[X]\tag{WLLN}
>$$
>但必须要求估计期望的样本是独立同分布的。

