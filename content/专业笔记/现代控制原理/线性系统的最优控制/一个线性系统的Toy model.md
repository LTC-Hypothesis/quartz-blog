这是一个时间最优控制的简单例子，考虑系统
$$
\begin{cases}
\begin{bmatrix}
\dot{x}(t)\\
\dot{y}(t)
\end{bmatrix}=\begin{bmatrix}
0&1\\
0&0
\end{bmatrix}\begin{bmatrix}
x(t)\\
y(t)
\end{bmatrix}+\begin{bmatrix}
0\\
1
\end{bmatrix}u(t),t\ge 0\\
\begin{bmatrix}
x(0)\\
y(0)
\end{bmatrix}=\begin{bmatrix}
-H\\
0
\end{bmatrix}
\end{cases}\tag{1}
$$
现在希望寻求控制$u(t)\in U=[-1,1]$将$(-H,0)$移动到$(0,0)$。
>[!question] (1)该系统是否能控？

直接验证Kalman秩条件即可。这里
$$
A=\begin{bmatrix}
0&1\\
0&0
\end{bmatrix},B=\begin{bmatrix}
0\\
1
\end{bmatrix}\Longrightarrow(B,AB)=\begin{bmatrix}
0&1\\
1&0
\end{bmatrix}
$$
因此$\text{rank}(B,AB)=2$，所以该系统完全能控。

>[!question] (2)求最优时间



>[!question] (3)求最优控制和最优轨线

