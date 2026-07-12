考虑以下线性系统：

$$\dot{y}(t) = A(t)y(t) + B(t)u(t), \quad t \in [0, T]$$

以及性能指标

$$J(y(\cdot), u(\cdot)) = \int_0^T f^0(y(t), u(t)) dt + h(y(T)).$$

我们假设

> [!info] 假设 (L1)
> 函数 $A(\cdot)$ 和 $B(\cdot)$ 满足
> $$A(\cdot) \in L^\infty(0, T; \mathbb{R}^{n \times n}),$$
> $$B(\cdot) \in L^\infty(0, T; \mathbb{R}^{n \cdot m}).$$
> 控制区域 $U$ 是 $\mathbb{R}^m$ 中的凸紧集，状态约束为
> $$y(0) = y_0 \in \mathbb{R}^n.$$

> [!info] 假设 (L2)
> 函数 $f^0: \mathbb{R}^n \times \mathbb{R}^m \to \mathbb{R}$ 以及 $h: \mathbb{R}^n \to \mathbb{R}$ 为下半连续且有下界的凸函数。

> [!theorem] 定理 2.1
> 对于上述系统，假设 (L1)—(L2) 成立，则存在最优对 $(\tilde{y}(\cdot), \tilde{u}(\cdot)) \in \mathscr{P}_{ad}[0, T]$ 使得
> $$J(\tilde{y}(\cdot), \tilde{u}(\cdot)) = \inf_{(y(\cdot), u(\cdot)) \in \mathscr{P}_{ad}[0, T]} J(y(\cdot), u(\cdot)).$$

**Proof**
由假设可见 $\mathscr{U}[0, T] = \mathscr{U}_{ad}[0, T]$，且存在 $(y_k(\cdot), u_k(\cdot)) \in \mathscr{U}[0, T]$ 使得
$$
\lim_{k \to \infty} J(y_k(\cdot), u_k(\cdot)) = \bar{J} = \inf_{(y(\cdot), u(\cdot)) \in \mathcal{F}_{ad}[0, T]} J(y(\cdot), u(\cdot)) > -\infty.
$$
由 (L1) 可知 $U$ 是紧的，从而存在常数 $C > 0$ 使得
$$
\int_0^T |u_k(t)|^2 dt \leq C, \quad \forall k \geq 1.
$$
因此，由第二章定理 4.11，不妨假设在 $L^2(0, T; \mathbb{R}^m)$ 中，
$$
u_k(\cdot) \xrightarrow{w} \bar{u}(\cdot).
$$
而由 Mazur 定理，我们有 $u_k(\cdot)$ 的一列凸组合，使得在 $L^2(0, T; \mathbb{R}^m)$ 中
$$
\tilde{u}_k(\cdot) = \sum_{i \geq 1} \alpha_{ik} u_{i+k}(\cdot) \to \bar{u}(\cdot),
$$
其中
$$
\alpha_{ik} \geq 0, \quad \sum_{i \geq 1} \alpha_{ik} = 1.
$$
由于 $U \subseteq \mathbb{R}^m$ 凸紧，因此 $\bar{u}(\cdot) \in \mathcal{U}_{ad}[0, T]$。另一方面，由于系统是线性的，如果记
$$
\tilde{y}_k(\cdot) = y(\cdot; y_0, \tilde{u}_k(\cdot)),
$$
$$
y_k(\cdot) = y(\cdot; y_0, u_k(\cdot)),
$$
则
$$
\tilde{y}_k(\cdot) = \sum_{i \geq 1} \alpha_{ik} y_{i+k}(\cdot),
$$
且容易证明在 $C([0, T], \mathbb{R}^n)$ 中，
$$
\tilde{y}_k(\cdot) \to \tilde{y}(\cdot) \equiv y(\cdot; y_0, \bar{u}(\cdot)).
$$
于是利用 $f^0(\cdot)$ 和 $h(\cdot)$ 的凸性、下半连续性以及 Fatou 引理可得
$$
J(\tilde{y}(\cdot), \bar{u}(\cdot))
$$
$$
= h(\tilde{y}(T)) + \int_0^T f^0(\tilde{y}(t), \bar{u}(t)) dt
$$
$$
\leq \lim_{k \to \infty} \left\{ h(\tilde{y}_k(T)) + \int_0^T f^0(\tilde{y}_k(t), \tilde{u}_k(t)) dt \right\}
$$
$$
= \lim_{k \to \infty} J(\tilde{y}_k(\cdot), \tilde{u}_k(\cdot))
$$
$$
= \lim_{k \to \infty} J\left(\sum_{i \geq 1} \alpha_{ik} y_{i+k}(\cdot), \sum_{i \geq 1} \alpha_{ik} u_{i+k}(\cdot)\right)
$$
$$
\leq \lim_{k \to \infty} \sum_{i \geq 1} \alpha_{ik} J(y_{i+k}(\cdot), u_{i+k}(\cdot))= \bar{J}
$$
因此 $\bar{u}(\cdot)$ 是最优的。
**QED**