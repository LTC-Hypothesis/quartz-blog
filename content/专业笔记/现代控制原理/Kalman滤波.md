>[!note] 滤波问题
>系统往往存在随机干扰，使得我们不能直接测量状态变量$X(t)$，能观测出来的往往是带有噪声的形式
>$$
>\hat{X}(t)=X(t)+\eta(t)\tag{$\eta$为噪声}
>$$
>那么滤波问题就是如何以最优的方式将噪声滤去，以得到观测值作为$X(t)$的最优估计。

>[!note] 滤波基本思想
>

# 无控制项的Kalman滤波公式
>[!note] 
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
>\end{cases}
>$$

**Proof**



**QED**

# 带控制项的Kalman滤波公式
>[!note] 
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
