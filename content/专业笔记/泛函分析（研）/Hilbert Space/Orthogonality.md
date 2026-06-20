# Orthogonality
Orthogonality is the greatest advantage of a Hilbert space. By the properties of orthogonality, we can introduce the well-known projection theorem.

> [!def] Orthogonality of elements
> If $H$ is a Hilbert space and $f,g\in H$, then $f$ and $g$ are **orthogonal** if $\left\langle f,g\right\rangle = 0$, denoted $f\bot g$

> [!def] Orthogonality of sets
> If $A,B\subset H$, $A\bot B$ if $f\bot g$ for $\forall f\in A,\forall g\in B$

> [!thm] The Pythagorean Theorem
> If $f_1 , f_2 , \cdots ,f_n$ are pairwise orthogonal vectors in $H$, then $$||f_1 + f_2 + \cdots +f_n||^2 = ||f_1||^2 + \cdots +||f_n||^2$$

> [!thm] Parallelogram Law
> If $H$ is a Hilbert space and $f, g\in H$, then $$||f-g||^2 + ||f+g||^2 = ||f||^2 + ||g||^2$$
> 
> ^758567

> [!def] Convex set
> If $X$ is any vector space over $\mathbb{F}$ and $A \subset X$, then $A$ is a convex set if for any $x$ and $y$ in $A$ and $0 \le t \le 1$, $tx + (1 - t)y\in A$.

> [!warning]
> - $\{tx + (1-t)y : 0\le t\le 1\}$ is the straight-line segment joining $x$ and $y$
> - If $X$ is a vector space, then any linear subspace in $X$ is a convex set.
> - A singleton set is convex
> - The intersection of any collection of convex sets is convex
> - If $H$ is a Hilbert space, then every open ball $B(f; r) = \{g\in H:|| f - g || < r\}$ is convex, as is every closed ball.

> [!thm]
> If $H$ is a Hilbert space, $K$ is a **closed convex** nonempty subset of $H$, and $h\in H$, then there is a **unique** point $k_0$ in $K$ such that 
> $$||h - k_0|| = dist(h,K) = \inf_{k\in K}||h - k||$$

**Proof** WLOG, we assume $h = 0$. In fact, we can consider $K - h = \{k - h:k\in K\}$ instead of $K$. W.T.S: there is a unique vector $k_0$ in $K$ such that 
$$
||k_0|| = dist(0,K) = \inf_{k\in K}||k||
$$
Let $d = dist(0,K)$, by definition, there exists $\{k_n\}$ s.t. $||k_n||\to d$. By [[Orthogonality#^758567| Parallelogram Law]], 
$$
\left\|\frac{k_n -k_m}{2}\right\|^2 = \frac{1}{2}\left(\left\|k_n\right\|^2 + \left\|k_m\right\|^2\right) - \left\|\frac{k_n +k_m}{2}\right\|^2
$$
Since K is convex, $\frac{k_n +k_m}{2}\in K\Longrightarrow \left\|\frac{k_n +k_m}{2}\right\|^2\ge d^2$. For $\varepsilon>0$, $\exists N$, s.t. $n>N$,  $||k_n||^2<d^2+\frac{1}{4}\varepsilon^2$. Then, 
$$
\left\|\frac{k_n -k_m}{2}\right\|^2\le d^2+ \frac{1}{4}\varepsilon^2 - d^2\Longrightarrow||k_n-k_m||\le \varepsilon
$$
Hence, $\{k_n\}$ is a Cauchy sequence in $H$. Since $H$ is a Hilbert space and $K$ is closed,there exists $k_o$ s.t. $k_n\to k_0\in K$ in $H$ and for any $\{k_n\}$ 
$$
d\le ||k_0||\le ||k_n-k_0||+||k_n||\to d
$$
Hence, $||k_0|| = d$. Next we check the uniqueness. Suppose $h_0$ satisfy $||h_0|| = d$. By convexity, $\frac{1}{2}(k_0 + h_0)$. Hence, 
$$
d\le ||\frac{1}{2}(h_0 + k_0)||\le \frac{1}{2}(||h_0|| + ||k_0||) = d
$$
it implies $||\frac{1}{2}(h_0 +k_0)|| = d$. By [[Orthogonality#^758567| Parallelogram Law]], $d^2 = d^2 - ||\frac{h_0 - k_0}{2}||^2\Longrightarrow h_0 = k_0$. **QED**

> [!thm]
> If $M$ is a **closed linear subspace** of $H$, $h\in H$, and $f_0$ is the **unique** element of $M$ such that $||h - f_0|| = dist(h,M)$, then $h-f_0\bot M$. Conversely, if $f_0\in M$ s.t. $h - f_0\bot M$, then $|| h - f_0 || = dist(h, M)$.
> 
> ^45dc78

**Proof** ($\Longrightarrow$): Since $M$ is linear subspace, for $f\in M$, $f+f_0\in M$ and 
$$
\begin{equation}
\begin{aligned}
||h - f_0||^2 &\le ||h - (f_0+f)||^2 = ||(h-f_0)-f||^2\\
& = ||h-f_0||^2 - 2Re\left\langle h-f_0, f\right\rangle +||f||^2\\
\end{aligned}
\end{equation}
$$
$$
\begin{equation}
\begin{aligned}
\Longrightarrow 2Re\left\langle h-f_0, f\right\rangle\le ||f||^2, \forall f\in M
\end{aligned}
\end{equation}
$$
Fixed $f\in M$, let $\left\langle h- f_0,f \right\rangle = re^{i\theta}, r\in \mathbb{R}^+,\theta\in \mathbb{R}$, consider
$$
2Re\left\langle h-f_0,te^{i\theta}f \right\rangle\le t^2||f||^2,\forall t\in \mathbb{R}
$$
where $2Re\left\langle h-f_0,te^{i\theta}f\right\rangle = 2\overline{te^{i\theta}}\cdot re^{i\theta} = 2tr$. Hence, for all $f\in M$, let $t\to 0$, $r = 0$, that imply $\left\langle h- f_0,f \right\rangle = 0 \Longrightarrow  h- f_0\bot f\Longrightarrow h- f_0\bot M$,
($\Longleftarrow$): For all $f\in M$, then $h-f_0\bot f-f_0$ so that 
$$
||h-f||^2 = ||h-f_0||^2 + ||f_0 - f||^2\ge ||h-f_0|| 
$$
Hence, $||h - f_0|| = dist(h,M)$ **QED**

> [!def] Orthogonal complement
> If $A\subset H$, let 
> $$
> A^{\bot} = \left\{f\in H\ |\ f\bot g,\forall g\in A\right\}
> $$

> [!proposition]
> $A^{\bot}$ is a closed linear subspace of $H$

**Proof** It's easy to check linearity and we prove $A^{\bot}$ is closed. Suppose $\{f_n\}\subset A^{\bot}$, $f_n\to f$ in $H$ and $\forall g\in A$,
$$
|\left\langle f,g\right\rangle|\le |\left\langle f-f_n,g\right\rangle|+|\left\langle f_n,g\right\rangle|\le||f_n-f|| \ ||g||
\to 0
$$
$\left\langle f,g\right\rangle=0$. Hence, $f\bot g,f\in A^{\bot}$ **QED**

> [!warning]
> Recall the [[Introduction#^45dc78|thm]], if $M$ is a closed linear subspace of $H$ and $h\in H$, then there is a unique element $f_0$ in $M$ such that $h-f_0\in M^{\bot}$. We can define a map, in fact, we call it projection mapping
> $$
> \mathbb{P}:H\to M, \ \mathbb{P}(h) = f_0
> $$
> 
> ^337b31

Now we introduce the significant projection theorem.

> [!thm]
> If $M$ is a closed linear subspace of $H$ and $h\in H$, let $\mathbb{P}(h)$ be the unique point in $M$ such that $h-\mathbb{P}(h)\bot M$. Then
> 1. $\mathbb{P}$ is a linear transformation on $H$
> 2. $|| \mathbb{P}(h) || \le || h ||$ for every $h$ in $H$
> 3. $\mathbb{P}^2 = \mathbb{P}\circ  \mathbb{P}= \mathbb{P}$
> 4. $Ker( \mathbb{P}) = M^{\bot},Im( \mathbb{P}) = M$
> 
> ^73d5aa

**Proof**
1. By the statement of [[Introduction of Hilbert Space#^337b31|warning]], let $h_1,h_2\in H$, $\alpha,\beta\in \mathbb{F}$,then for $f\in M$$$\left\langle (\alpha h_1+\beta h_2)-(\alpha \mathbb{P}(h_1)+\beta\mathbb{P}(h_2)),f\right\rangle = \alpha\left\langle(h_1-\mathbb{P}(h_1),f\right\rangle+\beta\left\langle h_2-\mathbb{{P}}(h_2),f\right\rangle=0$$ Hence, $\mathbb{P}(\alpha h_1+\beta h_2) = \alpha \mathbb{P}(h_1)+\beta\mathbb{P}(h_2)$.
2. For $h\in H$, then $$h = h-\mathbb{P}(h) +\mathbb{P}(h),\mathbb{P}(h)\in M,h-\mathbb{P}(h)\in M^{\bot}$$$$\Longrightarrow ||h||^2 = ||\mathbb{P}(h)||^2 +||h-\mathbb{P}(h)||^2\ge ||\mathbb{P}(h)||^2$$
3. Note that $f\in M$, $\mathbb{P}(f) = f$. For $h\in H$, $\mathbb{P}(h) \in M$, then $\mathbb{P}^2(h) = \mathbb{P}(\mathbb{P}(h)) = \mathbb{P}(h)$. Hence, $\mathbb{P}^2=\mathbb{P}$ 
4. For $h\in Ker(\mathbb{P})$, $\mathbb{P}(h)=0$, then $h = h - \mathbb{P}(h)\in M^{\bot}$. Conversely, $h\in M^{\bot}$, $h - 0=h-\mathbb{P}(h)\in M^{\bot}$. By the uniqueness, $\mathbb{P}(h)=0$. Hence, $Ker(\mathbb{P})=M^{\bot}$. By $\mathbb{P}:H\to M$, then $Im(\mathbb{P}) = M$. **QED**

Next we formally define the orthogonal projection.

> [!def] orthogonal projection
> If $M$ is a closed linear subspace of $H$ and $\mathbb{P}$ is the linear map defined in the [[Hilbert Space and Operator#^73d5aa|preceding theorem]], then $\mathbb{P}$ is called the **orthogonal projection** of $H$ onto $M$. If we wish to show this dependence of $\mathbb{P}$ on $M$, we will denote $\mathbb{P}_M$.

> [!note] notation
> $M\le H$ means $M$ is a closed linear subspace of $H$.

> [!proposition]
> If $M\le H$, then $(M^{\bot})^{\bot}=M$

**Proof** Let $I$ is identity operator, i.e. $I:H\to H, I(h)=h$ and $\mathbb{P}=\mathbb{P}_M$, we claim $I-\mathbb{P}$ is the orthogonal projection from $H$ to $M^\bot$. In fact, firstly, $I-\mathbb{P}$ is a linear transform. And then, $h = h-\mathbb{P}(h) +\mathbb{P}(h)$, $||h||^2 = ||h-\mathbb{P}(h)||^2 + ||\mathbb{P}(h)||^2\ge ||h-\mathbb{P}(h)||^2$. Besides, $(I-\mathbb{P})^2 = I-2\mathbb{P}+\mathbb{P}^2 = I-\mathbb{P}$. Finally, $Ker(I-\mathbb{P}) = \{h\ |\ h = \mathbb{P}(h),h\in H\} = M$, $Im(I-\mathbb{P})=M^\bot$. Hence, $I-\mathbb{P}:H\to M^{\bot}$ is orthogonal projection. By [[Introduction of Hilbert Space#^73d5aa|projection theorem(4)]], $(M^\bot)^\bot = Ker(I-\mathbb{P}) =M$. **QED**

---

## Exercises

> [!question]
> If $A\subset H$, then $(A^{\bot})^{\bot}$ is the **closed linear span** of $A$ in H.

> [!def] closed linear span
> (Definition to be added)

**Proof** (To be completed) **QED**

> [!question]
> If $Y$ is a linear manifold in $H$, then $Y$ is dense in $H$ iff $Y^{\bot}=0$

**Proof** (To be completed) **QED**