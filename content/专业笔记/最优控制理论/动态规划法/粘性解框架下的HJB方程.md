在[[动态规划法与HJB方程#^be10f5|（HJB）方程]]中，我们要求值函数$V(t,x)\in C^1([0,T]\times\mathbb{R}^n)$。但一般来说，值函数的光滑性并没有这么好。
>[!example] 
>考虑系统
>$$
>\begin{cases}
>\dot{y}(s)=u(s)\\
>y(t)=x
>\end{cases}
>$$
>控制集为$U=[-1,1]$，泛函指标为
>$$
>J(u(\cdot);t,x)=\left|y(T;t,x,u(\cdot))\right|=\left|x+\int_{t}^{T}u(s){d}s\right|
>$$
>则值函数为
>$$
>V(t,x)=\inf_{u\in \mathscr{U}[t,T]}\left|x+\int_{t}^{T}u(s){d}s\right|
>$$