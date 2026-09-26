>[!note] 主要工作
>发展研究FBSDE解的存在唯一性的第三种方法：连续性方法。引入单调性条件：$G_{m\times n}$为满秩矩阵，记
>$$
>u=(x,y,z),A(t,u)=\begin{bmatrix}
>-G^\top f\\
>Gb\\
>G\sigma
>\end{bmatrix}(u)
>$$
>满足
>$$
>\left\langle A(t,u)-A(t,u'),u-u'\right\rangle\le -\beta_1|G\Delta x_t|^2-\beta_2|G\Delta y_t|^2
>$$
>$$
>\langle\Phi(x)-\Phi(\bar{x},x-\bar{x})\ge0\rangle
>$$
>连续性方法的核心思想，是通过引入参数变量，相当于考虑一系列FBSDE（2.2）的解，从而逼近原来FBSDE的解。主要的是引理2.4的逻辑，当在某个$\alpha_0\in[0,1)$存在解时，那么存在$\delta_0$使得$\forall\delta\in[0,\delta_0]$，都存在$\alpha=\alpha_0+\delta$的解。那么把$\alpha_0+\delta$当作原来的$\alpha_0$，就可以反复利用这个引理，在有限步之内，得到$\alpha=1$时解也是存在的。在此基础上，就归结于，只需要证明$\alpha=0$时，引入的FBSDE有解即可。