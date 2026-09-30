>[!def] 同构
>称两个Hilbert空间$H_1,H_2$之间的线性映射$T:H_1\to H_2$为同构，若$T$为满射且保持内积即$\langle Th_1,Th_2\rangle=\langle h_1,h_2\rangle$

>[!warning] 
>注意到单射只要保持内积就可以满足的，这是因为
>$$
>\|Th\|=\|h\|=0\Longrightarrow Th=0
>$$

>[!proposition] 
>Hilbert空间之间的等距映射同时保持内积，即$\|Th\|=\|h\|\Longleftrightarrow\langle Th_1,Th_2\rangle=\langle h_1,h_2\rangle$

**Proof**

考虑
$$
\begin{aligned}
&\langle T(h_1+h_2),T(h_1+h_2)\rangle=\langle h_1+h_2,h_1+h_2\rangle\\
=&\langle Th_1,Th_1\rangle+\langle Th_1,Th_2\rangle+\langle Th_2,Th_1\rangle+\langle Th_2,Th_2\rangle\\
=&\langle h_1,h_1\rangle+\langle h_1,h_2\rangle+\langle h_2,h_1\rangle+\langle h_2,h_2\rangle
\end{aligned}
$$
利用等距性质得到$\text{Re}\langle Th_1,Th_2\rangle=\text{Re}\langle h_1,h_2\rangle$。由于$h_1,h_2$是任意的，把$h_1$替换成$\lambda h_1,\forall\lambda\in\mathbb{C}$，则原式变为$\text{Re}\lambda\langle Th_1,Th_2\rangle=\text{Re}\lambda\langle h_1,h_2\rangle$。取$\lambda=1$得到$\text{Re}\langle Th_1,Th_2\rangle=\text{Re}\langle h_1,h_2\rangle$，取$\lambda=i$得到$\text{Im}\langle Th_1,Th_2\rangle=\text{Im}\langle h_1,h_2\rangle$，从而$\langle Th_1,Th_2\rangle=\langle h_1,h_2\rangle$。

**QED**

>[!thm] 
>$H_1,H_2$都是无限维可分Hilbert空间，则$H_1,H_2$同构。

**Proof**

取$H_1$和$H_2$的规范正交基$\{e_i\}_{i=1}^{\infty},\{f_i\}_{i=1}^{\infty}$

**QED**