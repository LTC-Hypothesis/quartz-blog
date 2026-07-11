$H$ is the Hilbert space.
# Maximal Monotone Operators
>[!def] Monotone operator and maximal monotone operator
>An unbounded operator $A:D(A)\subset H\to H$ is monotone operator if it satisfies for $\forall v\in D(A)$, $(Av,v)\ge0$. If it is called maximal monotone operator , inaddition, $\text{Im}(I+A)=H$ i.e. 
>$$
>\forall f\in H, \exists u\in D(A), \text{ s.t. }u+Au=f
>$$

>[!proposition]
>Let $A$ be a maximal monotone operator, then
>1. $D(A)$ is dense in $H$.
>2. $A$ is a closed operator.
>3. $\forall\lambda>0$, $I+\lambda A:D(A)\to H$ is bijective and $(I+\lambda A)^{-1}$ is a bound operator, $\|(I+\lambda A)^{-1}\|_{\mathcal{L}(H)}\le 1$. 

**Proof**

1. Note that $D(A)$ is dense in $H$ i.e. $D(A)^\bot=\{0\}$. It suffices to show that for $\forall f\in H$ satisfies $(f,v)=0$, $\forall v\in D(A)$, then $f=0$. Since $A$ is maximal monotone operator, there exists $v_0$ s.t. $v_0+Av_0=f$. we have 
    $$
    0=(f,v_0)=|v_0|^2+(Av_0,v_0)\ge|v_0|^2\Longrightarrow v_0=0\text{ and thus }f=0
    $$
2. **Claim: For $\forall f\in H$, there exists unique $u\in D(A)$ s.t. $u+Au=f$**. If there exists another $\bar{u}\in D(A)$, we have $u-\bar{u}+A(u-\bar{u})=0$ and we take inner product with $u-\bar{u}$, we can obtain $u-\bar{u}=0$. We denote the map $(I+A)^{-1}:f\mapsto u,H\to H$, which is bound linear operator and $\|(I+A)^{-1}\|_{\mathcal{L}(H)}\le1$. We claim $A$ is closed operator. 

**QED**
# The Evolution Problem

# Regularity

# The Self-Adjoint Case
