```ad-proposition
title:Continuous $\Longleftrightarrow$ Bounded
Let $H$ be a Hilbert space and $L: H\to\mathbb{F}$ a linear functional. The following statements are equivalent.
1. $L$ is continuous
2. $L$ is continuous at 0
3. $L$ is continuous at some point
4. $\exists c>0$, s.t. $|L(h)|\le c\|h\|$ for every $h\in H$
```

```ad-def
title:Bounded linear functional
A bounded linear functional $L$ on $H$ is a linear functional for which there is a constant $c>O$ such that $|L(h)|\le c\|h\|$ for all $h$ in $H$. The norm is defined as 
$$
\begin{align}
\|L\|&=\sup_{\|h\|=1}|L(h)|\\
&=\sup_{h\ne 0}\frac{|L(h)|}{\|h\|}\\
&=\inf_{h\in H,|L(h)|\le c\|h\|}c
\end{align}
$$
Also, we have $|L(h)|\le \|L\|\|h\|$.
```

```ad-thm
title:The Riesz Representation Theorem
If $L: H\to \mathbb{F}$ is a bounded linear functional, then there is a unique vector $h_0$ in $H$ such that $L(h) = \left\langle h, h_0\right\rangle$ for every $h$ in $H$. Moreover, $\|L\| = \|h_0\|$ .
```
**Proof**
Let $M=Ker \ L$. Since $L$ is continuous and $M\le H$, $M\ne H$. Therefore, $M^{\bot}\ne\{0\}$. Hence there exists $f_0\in M^{\bot}$ , we note $a=L(f_0)$. For every $h\in H$, $\alpha=L(h)$, then $L(h-\frac{\alpha}{a}f_0)=L(h)-\frac{\alpha}{a}\cdot L(f_0)=0$. THen $h-\frac{\alpha}{a}f_0\in Ker \ L=M$. Hence, 
$$
0=\left\langle f_0,h-\frac{\alpha}{a}f_0\right\rangle=\left\langle f_0,h\right\rangle-\frac{\alpha}{a}\|f_0\|^2\Longrightarrow L(h)=\left\langle h,\frac{af_0}{\|f_0\|^2}\right\rangle
$$
Here is $h_0=\frac{af_0}{\|f_0\|^2}$. Next we prove the uniqueness. Suppose $h'\in H$ s.t. $\left\langle h,h_0\right\rangle=\left\langle h,h'\right\rangle$ then $\left\langle h,h_0-h'\right\rangle=0$ for every $h\in H$. Hence, $h_0=h'$. By [[Introduction of Hilbert Space#^970a9c|CBS inequality]], $|L(h)|\le\|h\|\|h_0\|$. Hence, $\|L\|\le\|h_0\|$. Take $h=\frac{h_0}{\|h_0\|}$, then $|L(\frac{h_0}{\|h_0\|})|=\left\langle h_0,\frac{h_0}{\|h_0\|}\right\rangle=\|h_0\|$. Hence, $\|L\|=\|h_0\|$.
**QED**
```ad-example
If $(X, \Omega, \mu)$ is a measure space and $F: L^2 (\mu)\to\mathbb{F}$ is a bounded linear functional, then there is a unique $g\in L^2(\mu)$ such that
$$
F(f)=\int_{X}f\bar{g}{d}\mu
$$
for every $f\in X$
```
---
# Exercises
```ad-question
Let $\mathcal{H} = l^2(\mathbb{N})$. If $N \ge 1$ and $L: \mathcal{H} \to \mathbb{F}$ is defined by $L(\{\alpha_n\}) = \alpha_N$, find the vector $h_0$ in $\mathcal{H}$ such that $L(h) = \langle h, h_0 \rangle$ for every $h$ in $\mathcal{H}$.
```

```ad-done

```

```ad-question
Let $\mathcal{H} = l^2(\mathbb{N} \cup \{0\})$. 
1.  Show that if $\{\alpha_n\} \in \mathcal{H}$, then the power series $\sum_{n=0}^\infty \alpha_n z^n$ has radius of convergence $\ge 1$. 
2. If $|\lambda| < 1$ and $L: \mathcal{H} \to \mathbb{F}$ is defined by $L(\{\alpha_n\}) = \sum_{n=0}^\infty \alpha_n \lambda^n$, find the vector $h_0$ in $\mathcal{H}$ such that $L(h) = \langle h, h_0 \rangle$ for every $h$ in $\mathcal{H}$. 
3. What is the norm of the linear functional $L$ defined in (b)?
```

```ad-done

```

```ad-question
With the notation as in Exercise 3, define $L: \mathcal{H} \to \mathbb{F}$ by $L(\{\alpha_n\}) = \sum_{n=1}^\infty n \alpha_n \lambda^{n-1}$, where $|\lambda| < 1$. Find a vector $h_0$ in $\mathcal{H}$ such that $L(h) = \langle h, h_0 \rangle$ for every $h$ in $\mathcal{H}$.
```

```ad-done

```

```ad-question
Let $\mathcal{H}$ be the Hilbert space described in Example 1.8. If $0 < t \le 1$, define $L: \mathcal{H} \to \mathbb{F}$ by $L(h) = h(t)$. Show that $L$ is a bounded linear functional, find $\|L\|$, and find the vector $h_0$ in $\mathcal{H}$ such that $L(h) = \langle h, h_0 \rangle$ for all $h$ in $\mathcal{H}$.
```

```ad-done

```

```ad-question
Let $\mathcal{H} = L^2([0, 1])$ and let $C^{(1)}$ be the set of all continuous functions on $[0, 1]$ that have a continuous derivative. Let $t \in [0, 1]$ and define $L: C^{(1)} \to \mathbb{F}$ by $L(h) = h'(t)$. Show that there is no bounded linear functional on $\mathcal{H}$ that agrees with $L$ on $C^{(1)}$.
```

```ad-done

```