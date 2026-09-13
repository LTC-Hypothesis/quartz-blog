>[!question] 1.3.1. 
>Show that if $\mathcal{A}$ generates $\mathcal{S}$, then $X^{-1}(\mathcal{A}) = \{\{X \in A\} : A \in \mathcal{A}\}$ generates $\sigma(X) = \{\{X \in B\} : B \in \mathcal{S}\}$.

>[!done] 
>We denote $\sigma(X^{-1}(\mathcal{A}))$ by $\mathcal{G}$. We W.T.S. $\mathcal{G}=\sigma(X)$. It is easy to check $\sigma(X)$ is also a $\sigma$-algebra. We prove $\mathcal{G}\subseteq \sigma(X)$ firstly. Note that 
>$$
>\mathcal{A}\subseteq\mathcal{S}\Longrightarrow\{X\in A\}\subseteq\{X\in B\}\Longrightarrow X^{-1}(\mathcal{A})\subseteq\sigma(X)
>$$
>Since $\mathcal{G}$ is the smallest $\sigma-$algebra containing $X^{-1}(\mathcal{A})$, $\mathcal{G}\subseteq\sigma(X)$. For another direction, 

>[!question] 1.3.2. 
>Prove Theorem 1.3.6 when $n = 2$ by checking $\{X_1 + X_2 < x\} \in \mathcal{F}$.

>[!done] 
>

>[!question] 1.3.3. 
>Show that if $f$ is continuous and $X_n \to X$ almost surely then $f(X_n) \to f(X)$ almost surely.

>[!done] 
>

>[!question] 1.3.4. (i) 
>Show that a continuous function from $\mathbf{R}^d \to \mathbf{R}$ is a measurable map from $(\mathbf{R}^d, \mathcal{R}^d)$ to $(\mathbf{R}, \mathcal{R})$. 

>[!question] 1.3.4.(ii) 
>Show that $\mathcal{R}^d$ is the smallest $\sigma$-field that makes all the continuous functions measurable.

>[!question] 1.3.5. 
>A function $f$ is said to be *lower semicontinuous* or l.s.c. if
>$$
>\liminf_{y \to x} f(y) \ge f(x)
>$$
>and *upper semicontinuous* (u.s.c.) if $-f$ is l.s.c. Show that $f$ is l.s.c. if and only if $\{x : f(x) \le a\}$ is closed for each $a \in \mathbf{R}$ and conclude that semicontinuous functions are measurable.

>[!question] 1.3.6. 
>Let $f : \mathbf{R}^d \to \mathbf{R}$ be an arbitrary function and let $f^\delta(x) = \sup\{f(y) : |y - x| < \delta\}$ and $f_\delta(x) = \inf\{f(y) : |y - x| < \delta\}$ where $|z| = (z_1^2 + \dots + z_d^2)^{1/2}$. Show that $f^\delta$ is l.s.c. and $f_\delta$ is u.s.c. Let $f^0 = \lim_{\delta \downarrow 0} f^\delta$, $f_0 = \lim_{\delta \downarrow 0} f_\delta$, and conclude that the set of points at which $f$ is discontinuous $= \{f^0 \ne f_0\}$ is measurable.
follows from the fact that $f^0 - f_0$ is.

>[!question] 1.3.7. 
>A function $\varphi : \Omega \to \mathbf{R}$ is said to be *simple* if
>$$
>\varphi(\omega) = \sum_{m=1}^n c_m 1_{A_m}(\omega)
>$$
>where the $c_m$ are real numbers and $A_m \in \mathcal{F}$. Show that the class of $\mathcal{F}$ measurable functions is the smallest class containing the simple functions and closed under pointwise limits.

>[!question] 1.3.8. 
>Use the previous exercise to conclude that $Y$ is measurable with respect to $\sigma(X)$ if and only if $Y = f(X)$ where $f : \mathbf{R} \to \mathbf{R}$ is measurable.

>[!question] 1.3.9. 
>To get a constructive proof of the last result, note that $\{\omega : m2^{-n} \le Y < (m+1)2^{-n}\} = \{X \in B_{m,n}\}$ for some $B_{m,n} \in \mathcal{R}$ and set $f_n(x) = m2^{-n}$ for $x \in B_{m,n}$ and show that as $n \to \infty$ $f_n(x) \to f(x)$ and $Y = f(X)$.