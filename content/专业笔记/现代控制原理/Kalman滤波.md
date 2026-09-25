>[!note] 滤波问题
>系统往往存在随机干扰，使得我们不能直接测量状态变量$X(t)$，能观测出来的往往是带有噪声的形式
>$$
>\hat{X}(t)=X(t)+\eta(t)\tag{$\eta$为噪声}
>$$
>那么滤波问题就是如何以最优的方式将噪声滤去，以得到观测值作为$X(t)$的最优估计。

>[!note] 滤波基本思想
>我们的目标是在$k+1$时刻，给出状态$X_{k+1}$的最优估计。但是问题在于，我们并没有观测数据$Y_{k+1}$，只能通过状态方程$X_{k+1}=\Phi_{k+1,k}X_k+W_k$和前一个时刻$k$的估计$\widehat{X}_k$来给出，但又因为随机噪声干扰$W_k$也未知，因此预报值只能是
>$$
>\widehat{X}_{k+1|k}=\Phi_{k+1,k}\widehat{X}_k\tag{1}
>$$
>在得到观测值$Y_{k+1}$之后，用预报值和观测值的差$Y_{k+1}-\widehat{X}_{k+1|k}=Y_{k+1}-C_{k+1}\Phi_{k+1,k}\widehat{X}_{k}$进行**修正**得到估计值，
>$$
>\widehat{X}_{k+1}=\Phi_{k+1,k}\widehat{X}_k+K_{k+1}(Y_{k+1}-C_{k+1}\Phi_{k+1,k}\widehat{X}_{k})\tag{2}
>$$
>其中矩阵$K_{k+1}$称为增益矩阵，可知只需要寻找合适的增益矩阵，使得估计值$\widehat{X}_{k+1}$和实际值$X_{k+1}$的**误差**足够小即可。这里我们选取的衡量误差的标准是方差
>$$
>P_{k+1}=\mathbb{E}\left[(X_{k+1}-\widehat{X}_{k+1})(X_{k+1}-\widehat{X}_{k+1})^\top\right]\tag{3}
>$$

>[!note] 无控制项的Kalman滤波公式
>考虑系统的状态方程与量测方程分别为
>
>$$
>X_{k+1} = \Phi_{k+1,k} X_k + W_k
>$$
>$$
>Y_k = C_k X_k + V_k
>$$
>
>其中 $\{W_k\}$ 与 $\{V_k\}$ 是互不相关的零均值噪声序列，即对任意的 $k$ 和 $j$，
>
>$$
>\mathbb{E}[W_k] = 0, \quad \mathbb{E}[V_k] = 0,
>$$
>$$
>\mathbb{E}[V_k V_j^T] = R_k \delta_{kj}, \quad \mathbb{E}[W_k W_j^T] = Q_k \delta_{kj}, \quad \mathbb{E}[W_k V_j^T] = 0,
>$$
>
>又设初始状态 $X_0$ 的统计特征为
>
>$$
>\mathbb{E}[X_0] = \bar{X}_0, \quad \mathbb{E}[(X_0 - \bar{X}_0)(X_0 - \bar{X}_0)^T] = P_0.
>$$
>
>且 $X_0$ 与 $\{W_k\}, \{V_k\}$ 不相关，即
>
>$$
>\mathbb{E}[(X_0 - \bar{X}_0)W_k^T] = 0, \quad \mathbb{E}[(X_0 - \bar{X}_0)V_k^T] = 0.
>$$
>相应的Kalman滤波公式为
>$$
>\begin{cases}
>P_{k+1|k} = \Phi_{k+1,k} P_k \Phi_{k+1,k}^T + Q_k, \\
>K_{k+1} = P_{k+1|k} C_{k+1}^T (C_{k+1} P_{k+1|k} C_{k+1}^T + R_{k+1})^{-1}, \\
>\widehat{X}_{k+1} = \Phi_{k+1,k} \widehat{X}_k + K_{k+1} (Y_{k+1} - C_{k+1} \Phi_{k+1,k} \widehat{X}_k), \\
>\begin{aligned}
>P_{k+1} = (I - K_{k+1} C_{k+1}) P_{k+1|k}.
>\end{aligned}
>\end{cases}\tag{K1}
>$$

**Proof**

我们的目标是让$(3)$式最小化。可以计算出，
$$
X_{k+1}-\widehat{X}_{k+1}=(I - K_{k+1}C_{k+1})[\Phi_{k+1,k}(X_k - \widehat{X}_k) + W_k] - K_{k+1}V_{k+1}
$$
于是
$$
P_{k+1} = (I - K_{k+1}C_{k+1})[\Phi_{k+1,k}P_k\Phi_{k+1,k}^T + Q_k](I - K_{k+1}C_{k+1})^T + K_{k+1}R_{k+1}K_{k+1}^T.
$$
定义预报误差
$$
\begin{aligned}
P_{k+1|k}&=\mathbb{E}\left[(X_{k+1}-\Phi_{k+1,k}\widehat{X}_k)(X_{k+1}-\Phi_{k+1,k}\widehat{X}_k)^\top\right]\\
&=\Phi_{k+1,k}P_k\Phi^\top_{k+1,k}+Q_k
\end{aligned}
$$
于是估计值的方差改写为
$$
\begin{aligned}
P_{k+1} &= (I - K_{k+1}C_{k+1})P_{k+1|k}(I - K_{k+1}C_{k+1})^T + K_{k+1}R_{k+1}K_{k+1}^T\\
&=P_{k+1|k}-K_{k+1}C_{k+1}P_{k+1|k}-P_{k+1|k}C^\top_{k+1}K^\top_{k+1}+K_{k+1}(R_{k+1}+C_{k+1}P_{k+1|k}C^\top_{k+1})K^\top_{k+1}
\end{aligned}
$$
记$S\triangleq(R_{k+1}+C_{k+1}P_{k+1|k}C^\top_{k+1})$，我们希望通过配方法将上式配出如下形式，
$$
P_{k+1}=(K_{k+1}-L)S(K_{k+1}-L)^\top
$$
其中$L$为待定矩阵，展开之后对比系数得到
$$
LS=P_{k+1|k}C^\top_{k+1}\Longrightarrow L=P_{k+1|k}C^\top_{k+1}S^{-1}
$$
展开之后会多出一项$P_{k+1|k}C^\top_{k+1}S^{-1}C_{k+1}P_{k+1|k}$所以要减去，因此得到
$$
\begin{aligned}
P_{k+1}=&(K_{k+1}-P_{k+1|k}C^\top_{k+1}S^{-1})P_{k+1|k}(K_{k+1}-P_{k+1|k}C^\top_{k+1}S^{-1})^{\top}\\
&+P_{k+1|k}-P_{k+1|k}C^\top_{k+1}S^{-1}C_{k+1}P_{k+1|k}
\end{aligned}
$$
把$S$代入回去，我们可以看出只需要取增益矩阵为
$$
K_{k+1}=P_{k+1|k}C^\top_{k+1}S^{-1}
$$
即可，综上就能得到公式组(K1)。

**QED**

>[!note] 带控制项的Kalman滤波公式
>当状态方程和量测方程中考虑控制 $u_k$ 的作用时，系统
>$$
>X_{k+1} = \Phi_{k+1,k} X_k + \Gamma_k u_k + B_k W_k,
>$$
>$$
>Y_k = C_k X_k + D_k u_k + V_k
>$$
>
>的 Kalman 滤波公式为
>
>$$
>\begin{cases}
>P_{k+1|k} = \Phi_{k+1,k} P_k \Phi_{k+1,k}^T + B_k Q_k B_k^T\\
>K_{k+1} = P_{k+1|k} C_{k+1}^T (C_{k+1} P_{k+1|k} C_{k+1}^T + R_{k+1})^{-1}\\
>\widehat{X}_{k+1} = \Phi_{k+1,k} \widehat{X}_k + \Gamma_k u_k + K_{k+1} [Y_{k+1} - D_{k+1} u_{k+1} - C_{k+1} (\Phi_{k+1,k} \widehat{X}_k + \Gamma_k u_k)]\\
>P_{k+1} = (I - K_{k+1} C_{k+1}) P_{k+1|k}
>\end{cases}
>$$
