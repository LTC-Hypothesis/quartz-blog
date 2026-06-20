> [!proposition] Continuous $\Longleftrightarrow$ Bounded
> Let $H$ be a Hilbert space and $L: H\to\mathbb{F}$ a linear functional. The following statements are equivalent.
> 1. $L$ is continuous
> 2. $L$ is continuous at 0
> 3. $L$ is continuous at some point
> 4. $\exists c>0$, s.t. $|L(h)|\le c\|h\|$ for every $h\in H$

> [!def] Bounded linear functional
> A bounded linear functional $L$ on $H$ is a linear functional for which there is a constant $c>O$ such that $|L(h)|\le c\|h\|$ for all $h$ in $H$. The norm is defined as 
> $$
> \begin{align}
> \|L\|&=\sup_{\|h\|=1}|L(h)|\\
> &=\sup_{h\ne 0}\frac{|L(h)|}{\|h\|}\\
> &=\inf_{h\in H,|L(h)|\le c\|h\|}c
> \end{align}
> $$
> Also, we have $|L(h)|\le \|L\|\|h\|$.

> [!thm] The Riesz Representation Theorem
> If $L: H\to \mathbb{F}$ is a bounded linear functional, then there is a unique vector $h_0$ in $H$ such that $L(h) = \left\langle h, h_0\right\rangle$ for every $h$ in $H$. Moreover, $\|L\| = \|h_0\|$.

**Proof**
Let $M=Ker \ L$. Since $L$ is continuous and $M\le H$, $M\ne H$. Therefore, $M^{\bot}\ne\{0\}$. Hence there exists $f_0\in M^{\bot}$ , we note $a=L(f_0)$. For every $h\in H$, $\alpha=L(h)$, then $L(h-\frac{\alpha}{a}f_0)=L(h)-\frac{\alpha}{a}\cdot L(f_0)=0$. Then $h-\frac{\alpha}{a}f_0\in Ker \ L=M$. Hence, 
$$
0=\left\langle f_0,h-\frac{\alpha}{a}f_0\right\rangle=\left\langle f_0,h\right\rangle-\frac{\alpha}{a}\|f_0\|^2\Longrightarrow L(h)=\left\langle h,\frac{af_0}{\|f_0\|^2}\right\rangle
$$
Here is $h_0=\frac{af_0}{\|f_0\|^2}$. Next we prove the uniqueness. Suppose $h'\in H$ s.t. $\left\langle h,h_0\right\rangle=\left\langle h,h'\right\rangle$ then $\left\langle h,h_0-h'\right\rangle=0$ for every $h\in H$. Hence, $h_0=h'$. By [[Introduction of Hilbert Space#^970a9c|CBS inequality]], $|L(h)|\le\|h\|\|h_0\|$. Hence, $\|L\|\le\|h_0\|$. Take $h=\frac{h_0}{\|h_0\|}$, then $|L(\frac{h_0}{\|h_0\|})|=\left\langle h_0,\frac{h_0}{\|h_0\|}\right\rangle=\|h_0\|$. Hence, $\|L\|=\|h_0\|$.
**QED**

> [!example]
> If $(X, \Omega, \mu)$ is a measure space and $F: L^2 (\mu)\to\mathbb{F}$ is a bounded linear functional, then there is a unique $g\in L^2(\mu)$ such that
> $$
> F(f)=\int_{X}f\bar{g}{d}\mu
> $$
> for every $f\in X$

---
# Exercises
