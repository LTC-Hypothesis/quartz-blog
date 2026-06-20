```ad-question
Let $\Omega$ be a non-empty set. Let $\mathcal{F}_0$ be the collection of all subsets such that either $A$ or $A^c$ is finite.
**(a)** Show that $\mathcal{F}_0$ is a field.
Define for $E \in \mathcal{F}_0$ the set function $P$ by
$$
P(E) = 
\begin{cases}
0, & \text{if } E \text{ is finite}, \\
1, & \text{if } E^c \text{ is finite}.
\end{cases}
$$
**(b)** If $\Omega$ is countably infinite, show $P$ is finitely additive but not $\sigma$-additive.
**(c)** If $\Omega$ is uncountable, show $P$ is $\sigma$-additive on $\mathcal{F}_0$.
```

```ad-done
title:Done for (a)
We check the definition.
1. Since $\Omega^c=\emptyset$ is finite, $\Omega\in\mathcal{F}_0$.
2. Suppose $A\in\mathcal{F}_0$. If $A^c$ is finite, then $A^c\in\mathcal{F}_0$. If $A$ is finite, then $(A^c)^c=A$ is finite, $A^c\in\mathcal{F}_0$.
3. Suppose $A,B\in\mathcal{F}_0$. If $A,B$ are finite, $A\cap B$ is finite. If $A^c$ or $B^c$ finite, then $A^c\cap B^c\subseteq A^c$ or $A^c\cap B^c\subseteq B^c$ are finite. If $A^c,B^c$ are finite, $(A\cup B)^c=A^c\cap B^c$ is finite.
```

```ad-done
title:Done for (b)
Suppose $E_1,E_2,\cdots,E_n$ are disjoint. If $\bigcup_{i=1}^{n}E_i$ is finite, then each $E_i$ is finite. $\mathbb{P}(\bigcup_{i=1}^{n}E_i)=0$ and $\sum_{i=1}^{n}\mathbb{P}(E_i)=0$.Hence, $\mathbb{P}(\bigcup_{i=1}^{n}E_i)=\sum_{i=1}^{n}\mathbb{P}(E_i)$. If $\bigcup_{i=1}^{n}E_i$ is infinite, $\bigcap_{i=1}^{n}E^c_i$ is finite and exists $E_i$ is infinite. If there exists $E_i,E_j$ are infinite, $E_i\cap E_j=\emptyset$. Then $E^c_i$ is finite and $E_j\subset E^c_i$, but $E_j$ is infinite it is a contration! Hence, there only exists one infinite set. $\mathbb{P}(\bigcup_{i=1}^{n}E_i)=1$, $\sum_{i=1}^{n}\mathbb{P}(E_i)=1$. 
$\mathbb{P}$ is not $\sigma$-additive. Since $\Omega$ is counably infinite, we can write $\Omega=\bigcup_{\omega\in\Omega}\{\omega\}$. Since $\Omega^c=\emptyset$, then $\mathbb{P}(\Omega)=1$. $\sum_{\omega\in\Omega}\mathbb{P}(\{\omega\})=0$. Hence, $\mathbb{P}$ is not $\sigma$-additive.
```

```ad-done
title:Done for (c)
Suppose $\{E_n\}_{n=1}^{\infty}\subseteq\mathcal{F}_0$ are disjoint. If $\bigcup_{n=1}^{\infty}E_n$ is finite, it must have infinite $E_i=\emptyset$. Without loss of generality, $E_k=\emptyset,k> m$. Then $\mathbb{P}(\bigcup_{n=1}^{\infty}E_n)=\mathbb{P}(\bigcup_{n=1}^{m}E_n)=0$ and $\sum_{n=1}^{\infty}\mathbb{P}(E_n)=\sum_{n=1}^{m}\mathbb{P}(E_n)=0$. If $\bigcup_{n=1}^{\infty}E_n$ is infinite. If each $E_n$ is finite, then $\bigcup_{n=1}^{\infty}E_n$ is at most countablset, $\bigcup_{n=1}^{\infty}E_n\notin\mathcal{F}_0$. Therefore, only one $E_k$ is finite, $\mathbb{P}(\bigcup_{n=1}^{\infty}E_n)=1$ and $\mathbb{P}(E_k)=1,\mathbb{P}(E_n)=0,n\ne k$.
```

```ad-question
Let $\mathcal{A}$ be the smallest field over the $\pi$-system $\mathcal{P}$. Use the inclusion-exclusion formula to show that probability measures agreeing on $\mathcal{P}$ must agree also on $\mathcal{A}$.
```

```ad-done

```