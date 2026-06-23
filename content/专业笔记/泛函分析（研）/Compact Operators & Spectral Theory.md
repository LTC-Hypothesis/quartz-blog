Suppose $E,F$ are two Banach space. 

# Compact Operator

> [!def] Compact operator
> A bounded operator $T\in\mathcal{L}(E,F)$ is **compact** if $\overline{T(B_E)}$ is compact in $F$ with the strong topology (**$T(B_E)$ is precompact**). 

> [!warning]
> $B_E$ can be replaced by any bounded set $B$. 

**Proof**
$\Longleftarrow$: Obviously.
$\Longrightarrow$: Suppose $B$ is a bounded set, then $\exists M>0$ s.t. $B\subset MB_E$. Then 
$$
T(B)\subset MT(B_E)\Longrightarrow\overline{T(B)}\subset\overline{MT(B_E)}
$$
Since $T(B_E)$ is precompact and by [[简明拓扑学#^163d7e|the closed subset of compact set is also compact]]， $\overline{T(B)}$ is compact and thus $T(B)$ is precompact. 
**QED**

> [!def]
> Let 
> $$
> \kappa(E,F)=\left\{T\mid T:E\to F\text{ is compact}\right\}
> $$
> and $\kappa(E)=\kappa(E,E)$.

> [!proposition]
> $\kappa(E,F)$ is a closed linear subspace of $\mathcal{L}(E,F)$ in the topology associated with $\|\cdot\|_{\mathcal{L}(E,F)}$. 

**Proof**
It is obviously that $\kappa(E,F)$ is a linear subspace. Suppose $\{T_n\}\subset\kappa(E,F)$ with $T_n\to T$ in $\mathcal{L}(E,F)$ as $n\to\infty$. It suffices to show that $T\in \kappa(E,F)$. Since $F$ is Banach and each $T_n(B_E)$ is precompact, then there exists finite ball $B_i\triangleq B_{\frac{\varepsilon}{2}}(y_i),i=1,\cdots,m$ s.t. 
$$
T_n(B_E)\subseteq\bigcup_{i=1}^{m}B_i
$$
Fixed sufficiently large $n$ s.t. $\|T_n-T\|<\frac{\varepsilon}{2}$. We check $T(B_E)$ is precompact. $\forall \ y\in T(B_E)$, there exists $x\in B_E$ s.t. $y=Tx$, then 
$$
\begin{align}
\|y\|_F=\|Tx\|\le \|Tx-T_nx\|_F+\|T_nx\|_F<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}=\varepsilon
\end{align}
$$
Then $$T(B_E)\subset\bigcup_{i=1}^{m}B_\varepsilon(y_i)$$
**QED**

> [!def] Finite rank
> An operator $T\in\mathcal{L}(E,F)$ is finite rank if $\text{dim} \ \text{Im}(T)<\infty$.

> [!thm] Compact operator can be approximated by operator with finite rank
> Let $\{T_n\}_{n=1}^{\infty}\subset\mathcal{L}(E,F)$ be a sequence of finite rank operators and $T\in\mathcal{L}(E,F)$ with $\|T_n-T\|_{\mathcal{L}(E,F)}\to0$ as $n\to\infty$. Then $T\in\kappa(E,F)$.

> [!proposition] Composition of compact operator and linear operator
> If $G$ is also a Banach space, $S\in \kappa(F,G),T\in\mathcal{L}(E,F)$. Then $S\circ T\in\kappa(E,G)$. 

**Proof**
Suppose $B$ is a bounded set and $T(B)$ is also compact, then $S\circ T(B)$ is precompact and thus $S\circ T\in\kappa(E,G)$. 
**QED**

> [!thm] Schauder (characterization with dual operator)
> $T\in\kappa(E,F)\Longleftrightarrow T^*\in \kappa(F^*,E^*)$. 

**Proof**
$\Longrightarrow$: We W.T.S $T^*(B_{F^*})$ is precompact. **Claim: for $\{v_n\}\subset B_{F^*}$, $T^*(v_n)$ has convergent subsequence**. Let $K=\overline{T(B_E)}$ is a compact metric space. Consider 
$$
\mathscr{H}=\left\{\varphi_n:K\ni x\mapsto \langle v_n,x\rangle\right\}\subset C(K)
$$
By Ascoli–Arzelà Thm, 
> [!lemma] Ascoli–Arzelà
> Let $K$ be a compact metric space and let $\mathscr{H}\subset C(K)$. Assume that $\mathscr{H}$ is uniformly equicontinuous i.e. 
> $$
> \forall\varepsilon>0,\exists\delta>0,\text{s.t }d(x_1,x_2)<\delta\Longrightarrow|f(x_1)-f(x_2)|<\varepsilon,\forall f\in\mathscr{H}
> $$
> Then $\overline{\mathscr{H}}$ is compact in $C(K)$.

Then $\overline{\mathscr{H}}$ is compact in $C(K)$ and thus there exists $\varphi_{n_k}$ s.t. $\varphi_{n_k}\rightrightarrows\varphi\in C(K)$ i.e. 
$$
\sup_{y\in B_E}|\langle v_{n_k},Ty\rangle-\varphi(T(y))|\xrightarrow{k\to\infty}0
$$
and thus 
$$
\sup_{y\in B_E}|\langle v_{n_k},Ty\rangle-\langle v_{n_l},Ty\rangle|\xrightarrow{k,l\to\infty}0\Longleftrightarrow\sup_{y\in B_E}|\langle T^*(v_{n_k}),y\rangle-\langle T^*(v_{n_l}),y\rangle|\xrightarrow{k,l\to\infty}0
$$
Then it implies $\|T^*v_{n_k}-T^*v_{n_l}\|_{F^*}\to0$ as $k,l\to\infty$ i.e. $T^*v_{n_k}$ converge in $F^*$. 
$\Longleftarrow$: Suppose $T^*\in\kappa(F^*,E^*)$. By "$\Longrightarrow$", $T^{**}\in \kappa(E^{**},F^{**})$ and thus $\overline{T^{**}(B_E)}$ is compact. Note that $T(B_E)=T^{**}(B_E)$ and $F$ is closed in $F^{**}$, then $\overline{T(B)}$ is compact in $F$. 
**QED**

> [!warning]
> $T\in\kappa(E,F)$ then for any bounded sequence $\{u_n\}\subset E$, $T(u_n)$ has convergent subsequence in $F$. 

> [!proposition]
> If $u_n\rightharpoonup u$ in $E$ and $T\in\kappa(E,F)$, then $Tu_n\to Tu$. Conversely, if $u_n\rightharpoonup u\Longrightarrow Tu_n\to Tu$ and $E$ is reflexive, then $T\in\kappa(E,F)$. 

**Proof**
$\Longrightarrow$: Since $u_n\rightharpoonup u$, then $u_n$ is bounded and thus $Tu_n$ has convergent subsequence denoted by $Tu_{n_k}\to v\in F$. For $\forall f\in F^*$, 
$$
\langle f,Tu_n\rangle=\langle T^*f,u_n\rangle\to\langle T^*f,u\rangle=\langle f,Tu\rangle
$$
i.e. $Tu_n\rightharpoonup Tu$. Therefore,
$$
\left.\begin{matrix}
Tu_n\rightharpoonup Tu\\
Tu_{n_k}\to v
\end{matrix}\right\}\Longrightarrow Tu=v
$$
Then every subsequence converge to $Tu$, then $Tu_n\to Tu$. 
$\Longleftarrow$: Suppose $\{u_n\}\subset B_E$. Since $E$ is reflexive, then there exists $u_{n_k}\rightharpoonup u\Longrightarrow Tu_{n_k}\to Tu$. Hence, $Tu_{n_k}$ is a convergent subsequence of $Tu_n$, then $T\in\kappa(E,F)$. 
**QED**

# The Riesz–Fredholm Theory

> [!lemma] Riesz
> Let $E$ be a normed vector space(n.v.s) and $M\subset E$ be a closed linear subspace with $M\ne E$. Then 
> $$
> \forall\varepsilon>0,\exists u\in E\text{ s.t. }\|u\|=1\text{ and }\text{dist}(u,M)\ge1-\varepsilon
> $$
> 
> ^7e3f42

**Proof**
We choose $v\in E,v\notin M$ and since $M$ is closed, $d\triangleq \text{dist}(v,M)>0$. We can choose $m_0\in M$ s.t. 
$$
d\le \|v-m_0\|\le \frac{d}{1-\varepsilon}
$$
Take $u=\frac{v-m_0}{\|v-m_0\|}$. For $\forall m\in M$, 
$$
\left\|\frac{v-m_0}{\|v-m_0\|}-m\right\|=\frac{\|v-(m_0+m\|v-m_0\|)\|}{\|v-m_0\|}\ge d\cdot\frac{1-\varepsilon}{d}=1-\varepsilon
$$
Note that $m_0+m\|v-m_0\|\in M$. 
**QED**

> [!thm] Riesz
> Let $E$ be an n.v.s. and $B_E$ is compact, then $\text{dim }E<\infty$.
> 
> ^a2e244

**Proof**
By contradiction, suppose $\text{dim }E=\infty$. Then we can obtain a sequence of finite-dimensional linear subspace $E_{n-1}\subset E_n$ and $E_{n-1}\ne E_n$. By [[#^7e3f42|Riesz's lemma]], there is a sequence $\{u_n\}\subset E_n$ s.t. $\text{dist}(u_n,E_{n-1})\ge\frac{1}{2}$. Then for some $m<n$, $\|u_n-u_m\|\ge\frac{1}{2}$. It implies that $\{u_n\}$ doesn't have convergent subsequence. It is contradicts with $B_E$ is compact.
**QED**

> [!thm] Fredholm alternative
> Let $T\in\kappa(E)$, then
> 1. $\text{dim Ker}(I-T)<\infty$. 
> 2. $\text{Im}(I-T)$ is closed and $\text{Im}(I-T)=\text{Ker}(I-T)^\bot$
> 3. $\text{Ker}(I-T)=\{0\}\Longleftrightarrow\text{Im}(I-T)=E$
> 4. $\text{dim Ker}(I-T)=\text{dim Ker}(I-T^*)$

^b31a3a

**Proof**
1. Let $E_1=\text{Ker}(I-T)$, for $u\in E_1$ then it satisfies $Tu=u$ i.e. $\|u\|=\|Tu\|=1$. Then $B_{E_1}\subset T(B_E)\Longrightarrow\overline{B_{E_1}}\subset \overline{T(B_E)}$. By [[#^a2e244|Riesz's thm]], $\text{dim }E_1<\infty$
2. $\text{Im}(I-T)$ is $$\text{Im}(I-T)=\left\{v:v=u-Tu,u\in E\right\}$$Suppose $v_n=u_n-Tu_n\to v$ in $E$, we W.T.S. $v\in \text{Im}(I-T)$. Let $$d_n=\text{dist}(u_n,\text{Ker}(I-T))$$Since $\text{dim Ker}(I-T)<\infty$, there exists $t_n\subset\text{Ker}(I-T)$ s.t. $d_n=\|u_n-t_n\|$. We have $v_n=(u_n-t_n)-T(u_n-t_n)$. **We claim $\|u_n-t_n\|$ is bounded**. Suppose not, then there exists a subsequence s.t. $\|u_{n_k}-t_{n_k}\|\to\infty$. Let $w_n=\frac{u_n-t_n}{\|u_n-t_n\|}$, then $w_{n_k}-Tw_{n_k}\to0$ as $k\to\infty$. Since $T$ is compact operator, after passing the further subsequence, we assume that $Tw_{n_k}\to z$, then $w_{n_k}=w_{n_k}-Tw_{n_k}+Tw_{n_k}\to z$. Hence, $z\in\text{Ker}(I-T)$ so that $\text{dist}(w_{n_k},\text{Ker}(I-T))\to0$ as $k\to\infty$. Then $$\text{dist}(w_{n_k},\text{Ker}(I-T))=\frac{\text{dist}(u_n,\text{Ker}(I-T))}{\|u_n-t_n\|}=1\Longrightarrow\Longleftarrow$$ Hence, $\|u_n-t_n\|$ is bounded. Since $T$ is compact operator, after passing subsequence, $T(u_{n_k}-t_{n_k})\to l$, then $$u_{n_k}-t_{n_k}=u_{n_k}-t_{n_k}-T(u_{n_k}-t_{n_k})+T(u_{n_k}-t_{n_k})\to v+l$$Note that $T(u_{n_k}-t_{n_k})\to T(v+l)=l\Longrightarrow v+l-T(v+l)=v$. Hence, $v\in \text{Im}(I-T)$.
3. $\Longrightarrow$: Suppose not, let $E_1=\text{Im}(I-T)\ne E$. By 2., $E_1$ is a Banach space and $T(E_1)\subset E_1$. Then $T\mid_{E_1}\in\kappa(E_1)$ and let $E_2=(I-T)(E_1)$ is a closed subspace of $E_1$ Then $E_2\ne E_1$. let $E_n=(I-T)^n(E)$ and thus we obtain an decreasing sequence of closed subspace $E_{n}\subset E_{n+1}$. By [[#^7e3f42|Riesz's lemma]], we can construct a sequence $\{u_n\}$ s.t. $u_n\in E_n$ and $\|u_n\|=1$, $\text{dist}(u_n,E_{n+1})\ge\frac{1}{2}$. Then $$Tu_{n}-Tu_m=-(u_n-Tu_n)+(u_m-Tu_m)+(u_n-u_m)$$If $n>m$, $E_{n+1}\subset E_{n}\subset E_{m+1}\subset E_m$ and thus $$-(u_n-Tu_n)+(u_m-Tu_m)+u_n\in E_{m+1}$$ and then $$\|Tu_n-Tu_m\|\ge\text{dist}(u_m,E_{m+1})\ge\frac{1}{2}\Longrightarrow\Longleftarrow\text{ with }T\text{ is compact}$$Hence, $E=\text{Im}(I-T)$. 
   $\Longleftarrow$: Suppose $\text{Im}(I-T)=E\Longrightarrow \text{Ker}(I-T^*)=E^\bot=\{0\}$. Since $T^*\in\kappa(E^*)$, by "$\Longrightarrow$", we can obtain $\text{Im}(I-T^*)=E^*\Longrightarrow \text{Ker}(I-T)=\text{Im}(I-T^*)^\bot=\{0\}$.
4. Set $d:=\text{dim Ker}(I-T),d^*:=\text{dim Ker}(I-T^*)$. We W.T.S. $d^*\le d$. Suppose not i.e. $d<d^*$. Since $\text{dim Ker}(I-T)<\infty$, there exists a continuous projection $P:E\to\text{Ker}(I-T)$. Note that $d^*=\text{dim Ker}(I-T^*)^\bot=\text{dim Im}(I-T)$ and thus it admits a complement in $E$, denote by $F$. Since $d<d^*$, there exists a linear map $\Lambda:\text{Ker}(I-T)\to F$, which is injective and surjective. Let $S=T+\Lambda\circ P$ and thus $S\in\kappa(E)$. Since $\Lambda\circ P$ is finite rank, we claim that $\text{Ker}(I-S)=\{0\}$. If $u-Su=0$, then $$u-Su=(u-Tu)+(\Lambda\circ Pu)=0\Longrightarrow u-Tu=0,\Lambda\circ P(u)=0$$ $u\in\text{Ker}(I-T),\Lambda u\Longrightarrow u=0$. By 3., $\text{Im}(I-S)=E$ . But there exists $f\in F,f\notin \text{Im}(\Lambda)$ s.t. there is no solution of $u-Su=f$. It is a contradiction! Hence, $d^*\le d$. Now applying the fact to $T^*$, $$\text{dim Ker}(I-T^{**})\le \text{dim Ker}(I-T^*)\le \text{dim Ker}(I-T)$$Note that $\text{Ker}(I-T)\subset \text{Ker}(I-T^{**})\Longrightarrow d\le d^*$. 

**QED**

> [!warning] Alternative
> We should recall the cases in linear algebra. 
> $$
> \begin{cases}
> \text{case1:}Ax=b\\
> \text{case2:}Ax=0
> \end{cases}
> $$
> Either $Ax=b$ has unique solution and $Ax=0$ has unique zero solution or $Ax=b$ doesn't have unique solution and $Ax=0$ has nonzero solution. The case of solution only happen once. 
> Now for operator $I-T$ and equation $u-Tu=f$.
> - Either for every $f ∈ E$ the equation $u − T u = f$ has a unique solution,
> - or $u-Tu=0$ admits $n$ linearly independent solutions, and in this case, the inhomogeneous equation $u − T u = f$ is solvable if and only if $f$ satisfies $n$ orthogonality conditions i.e. $f\in\text{Ker}(I-T^*)^\bot$.

# The Spectrum of a Compact Operator

> [!def] Resolvent set 
> $T\in\mathcal{L}(E)$, 
> $$
> \rho(T)=\left\{\lambda\in\mathbb{R}\mid T-\lambda I:E\to E\text{ is bijective and }(T-\lambda I)^{-1}\in\mathcal{L}(E)\right\}
> $$

> [!def] Spectrum, eigenvalue(e-value) and eigenspace(e-space) 
> - **Spectrum**: $\sigma(T)\triangleq\mathbb{R}\setminus\rho(T)$
> - **Eigenvalue**: The $\lambda\in\mathbb{R}$ s.t. $\text{Ker}(T-\lambda I)\ne \{0\}$
> - **Eigenspace**: $\text{Ker}(T-\lambda I)$ is the eigenspace corresponding to $\lambda$
> - $EV(T)\triangleq\left\{\text{the all eigenvalues}\right\}$

>[!warning] 
>$EV(T)\subset\sigma(T)$, the inclusion can be strict i.e. $\exists\lambda\in\mathbb{R}$ s.t. 
>$$
>\text{Ker}(T-\lambda I)=\{0\},\text{Im}(T-\lambda I)=E
>$$

 >[!proposition]
 >Suppose $T$ is a bounded operator, then $\sigma(T)$ is compact and $\sigma(T)\subset[-\|T\|,\|T\|]$.
 
 **Proof**
 We choose $|\lambda|>\|T\|$. It suffices to show that $T-\lambda I$ is bijective for such $\lambda$ and thus $\lambda\in\rho(T)$. For $\lambda\in\sigma(T)$, then $\lambda\notin\rho(T)\Longrightarrow|\lambda|\le \|T\|$ i.e. $\sigma(T)\subset[-\|T\|,\|T\|]$. 
 Given $f\in E$, consider the equation $Tu-\lambda u=f$, we should find unique solution $u\in E$. We write the equation as $u=\lambda^{-1}(Tu-f)$ and by Banach's fixed point theorem, $\left\|\frac{T}{\lambda}\right\|<1$, there exist the unique solution $u$ and thus $T-\lambda I$ is surjective.
 Suppose $u_1,u_2\in E$ s.t. $Tu_1-\lambda u_1=Tu_2-\lambda u_2\Longrightarrow T(u_1-u_2)=\lambda(u_1-u_2)$ and then 
 $$
 \|\lambda (u_1-u_2)\|=|\lambda|\left\|u_1-u_2\right\|\le\left\|T\right\|\|u_1-u_2\|
 $$
 Since $|\lambda|>\|T\|$, then $\|u_1-u_2\|=0$ i.e. $u_1=u_2$ and thus $T-\lambda I$ is injective. Hence, $T-\lambda I$ is bijective and $\lambda\in\rho(T)$ with $|\lambda|>\|T\|$.
 Now we prove $\sigma(T)$ is compact. Since $\sigma(T)\subset[-\|T\|,\|T\|]$ is bounded, it suffices to show $\sigma(T)$ is closed $\Longleftrightarrow \rho(T)$ is open. Given $\lambda_0\in\rho(T)$, for $\lambda$ is closed to $\lambda_0$, consider 
 $$
 Tu-\lambda u=f\Longrightarrow Tu-\lambda_0u=f+(\lambda-\lambda_0)u
 $$ 
 We can write the equation as $u=(T-\lambda_0I)^{-1}(f+(\lambda-\lambda_0)u)$. It suffices to set $|\lambda-\lambda_0|\left\|(T-\lambda_0I)^{-1}\right\|<1$, we can obtain the unique solution $u$ of the equation by Banach's fixed point theorem. Hence, for given $\lambda_0$, there exist $r\triangleq\frac{1}{\|(T-\lambda_0I)^{-1}\|}$ s.t. 
 $$
 |\lambda-\lambda_0|<r\text{ .i.e. }B_r(\lambda_0)\subseteq\rho(T)
 $$
 Hence, $\rho(T)$ is open.
 **QED**

>[!thm]
>Let $T\in\kappa(E)$ with $\text{dim}(E)=\infty$, then we have: 
>1. $0\in\sigma(T)$
>2. $\sigma(T)\setminus\left\{0\right\}=EV(T)\setminus\{0\}$
>3. One of the following cases holds:
>     - $\sigma(T)=\{0\}$
>     - $\sigma(T)\setminus\{0\}$ is finite set
>     - $\sigma(T)\setminus\{0\}$ is a sequence converging to $0$

**Proof of 1. and 2.**

1. Suppose $0\notin\sigma(T)$ and thus $0\in \rho(T)$. Then $T$ is bijective and thus $I=T\circ T^{-1}$ is compact, so $B_E$ is compact. It implies $\text{dim}(E)<\infty\Longrightarrow\Longleftarrow$. 
2. It suffices to show that $\sigma(T)\setminus\{0\}\subseteq EV(T)\setminus\{0\}$. Suppose $0\ne \lambda\in\sigma(T)$ but $\lambda\notin EV(T)$ i.e. $\text{Ker}(T-\lambda I)=\{0\}$, by [[#^b31a3a|Fredholm alternative]], $\text{Im}(T-\lambda I)=E$, then $T-\lambda I$ is bijective and thus $\lambda\in\rho(T)\Longrightarrow\Longleftarrow$. 

**QED**
**Proof of 3.**
 We need the lemma.
 
 >[!lemma]
 >Let $T\in\kappa(E)$ and let $\left\{\lambda_n\right\}\subseteq\mathbb{R}$ be a distinct sequence with $\lambda_n\to\lambda$ as $n\to\infty$ and $\{\lambda_n\}\subseteq\sigma(T)\setminus\{0\}$. Then $\lambda=0$.
 
 
 
 
**QED**
# Spectral Decomposition of Self-Adjoint Compact Operators