---
publish: 2019
tag: 强化学习, 随机控制, 均值方差, 熵正则化, 高斯探索
read: 2026-10-28
---

> [!note] 文献信息
> Haoran Wang & Xun Yu Zhou. *Continuous-Time Mean–Variance Portfolio Selection: A Reinforcement Learning Framework*.
> 本次阅读：2019 年 5 月预印本；[原文](https://arxiv.org/abs/1904.11392)。
> 前置：[[2020-Wang Haoran&Zariphopoulou Thaleia&Zhou Xun Yu-Reinforcement Learning in Continuous Time and Space A Stochastic Control Approach|连续时间探索控制框架]]。

# 问题与核心思想

在市场参数未知时，学习满足期望终端财富目标的最小方差投资策略。经典问题为 $\min_u\operatorname{Var}(X_T)$，约束 $\mathbb E[X_T]=z$。

**核心路线：**固定乘子 $w$，转化为终端二次损失；加入松弛控制和熵正则化，求解有限时域探索型 LQ 问题，再利用解析解结构设计学习算法。研究的是**预承诺解**，没有消除原 MV 偏好的时间不一致性。

# 主要结论

记 $\rho=(\mu-r)/\sigma$，$x$ 为贴现财富，$u$ 为风险资产投资金额。最优策略为（第二项是方差）
$$
\pi^*(\cdot;t,x,w)=\mathcal N\!\left(-\frac{\rho}{\sigma}(x-w),\frac{\lambda}{2\sigma^2}e^{\rho^2(T-t)}\right).
$$

- **相对无限时域的新变化：**探索方差随时间递减（$\rho\ne0$），但临近到期仍趋于 $\lambda/(2\sigma^2)>0$。
- **与经典解的联系：**策略均值等于经典最优控制；两者终端财富期望相同，故均值约束对应同一个 $w$。$\lambda\downarrow0$ 时策略弱收敛到经典确定性策略，价值函数也收敛；探索增加的终端方差为 $\lambda T/2$。
- **策略改进：**在光滑性、严格凸性及可容许性条件下，用当前准确价值函数构造的高斯策略使成本不增。特定初始高斯策略下，精确迭代两次到最优：第一次纠正均值，第二次纠正方差。

# 方法与算法

**证明主线：**拉格朗日变换 → HJB 中对密度优化得到高斯 → 二次价值函数求系数并验证；策略改进用 Hamiltonian 比较与 Itô 公式。

**EMV：**参数化二次价值函数 $V^\theta$ 与高斯策略 $\pi^\phi$，用采样轨迹的平方 TD 残差更新参数；以 $\theta_3=2\phi_2$ 联系价值函数和策略，并用终端条件确定常数项。每若干轮更新
$$
w\leftarrow w-\alpha(\overline X_T-z).
$$
可借鉴的是“**先求解的结构，再据此选择学习函数族**”，避免盲目使用通用网络。相关：[[值迭代和策略迭代]]、[[TD算法]]。

# 批判与后续

- 精确策略迭代的“两步收敛”不等于样本算法的收敛；本文的策略参数更新也不能直接当作通常的策略梯度。
- 式（42）—（43）需谨慎：Bellman 条件要求残差的**条件期望**为零，正确价值函数沿路径仍有布朗噪声；最小化样本 TD 平方会受二次变差影响。后续读 [Jia–Zhou（2022）的鞅方法](https://www.jmlr.org/papers/v23/21-0947.html)。
- “不显式估计市场参数”仍依赖模型结构；本文实验是模拟比较，不能据此推断普遍优于其他投资方法。
- **待检验的研究想法：**加入借贷利差，考察高斯策略及探索—利用分离是否失效。先查重和检查 HJB 可解性，尚不能认定为创新点。
