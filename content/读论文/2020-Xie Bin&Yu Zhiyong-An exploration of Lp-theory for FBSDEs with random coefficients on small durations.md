---
publish: 2020
tag: FBSDE, Lp理论
---
以往的解的存在唯一性定理和估计都是在$L^2$理论下解决的。
```ad-note
title:$L^p$ 理论的发展历程$(p>2)$
- (2002)Delarue：第一次得到$L^p$的结果，在$\sigma$与$z$独立的情况下
- (2014)Li and Wei：在$\sigma$对$z$项Lipschitz系数充分小或者$\sigma$有界且独立于$z$的情况下得到$L^p$结果
- 以上两个都是在小时间区间上的结果。在充分大的时间区间上，(2015)马进、张德涛、吴臻、张进等人得到一维FBSDEs的$L^p$结果
- 在充分大的时间区间上，(2018)Hu等人在$b,\sigma$对$(y,z)$的Lipschitz常数充分小的情况下得到$L^p$结果
- (2018)Feng: 当$b,\sigma$都和$z$独立的情况下，得到$L^p$结果
- (2019)Yong: 更深入地思考
```

```ad-question
title:共同的问题或者约束条件
1. $L_z$为$\sigma$对$z$的Lipschitz常数，$L_z$充分小
2. $L_x$为终端函数$\Phi$的Lipschitz常数，$L_xL_z$充分小
   
注意到第二个条件似乎不依赖于时间长度。这个条件看上去是无法克服的，Ma和Yong的FBSDE专著给出例子，当$p=2,L_xL_z=1$是有FBSDE无解。学者一般假设条件为$L_xL_z<1$.
```

```ad-todo
title:本文的主要工作
- 主要结果：对小时间区间上随机系数的FBSDEs得到$L^p$结果
- 创新点：突破$L_xL_z<1$条件的约束，建立**可测全局隐函数定理**
- 灵感来源：Hu-Peng，Peng-Wu连续性方法（引入单调性条件），Zhang-Ge全局隐函数定理
```

```ad-def
title:主要研究的FBSDE
在时间区间$s\in[t,t']$上，考虑以下形式的FBSDE
$$
\begin{cases}
dX(s)=b(s,\Theta(s)){d}s+\sum_{i=1}^{d}\sigma_i(s,\Theta(s)){d}W_i(s)\\
{d}Y(s)=g(s,\Theta(s)){d}s+\sum_{i=1}^{d}Z_i(s){d}W_i(s)\\
X(t)=\xi,Y(t')=GX(t')+\eta
\end{cases}
$$
$\xi,\eta$为r.v.，$G\in\mathbb{R}^{n\times m}$为满秩矩阵，$\Theta(s)=(X^T(s),Y^T(s),Z^T(s))^T$, $Z(s)=(Z_1^T(s),\cdots,Z_d^T(s))^T$, $W(s)=(W^T_1(s),\cdots,W^T_d(s))^T$, $\Gamma(s)=(g^T(s),b^T(s),\sigma^T(s))^T$, $\sigma(s)=(\sigma_1^T(s),\cdots,\sigma_d^T(s))^T$
```

^082c3b

```ad-def
title:基本假设
1. $\xi$是$\mathcal{F_t}$可测的，$\eta$是$\mathcal{F}_{t'}$可测的
2. 映射$\Gamma=(g^T,b^T,\sigma^T)^T:\Omega\times[t,t']\times\mathbb{R}^{n+m+md}\to\mathbb{R}^{n+m+md}$是$\mathcal{G}\otimes\mathcal{B}(\mathbb{R}^{n+m+md})/\mathbb{R}^{n+m+md}可测的$
3. $(H1)\Gamma$是对$\theta$一致Lipschitz连续，Lipschitz常数为$L$
```

```ad-lemma
title:引理2.1（H1假设下且终端无约束$G=0$）
$p>1,0\le t<t'\le T$, (H1)假设成立。$\xi\in L^p_{\mathcal{F}_t}(\Omega,\mathbb{R}^n),\eta\in L^p_{\mathcal{F}_{t'}}(\Omega,\mathbb{R}^n),\Gamma(\cdot,0)\in\mathcal{M}^p_{\mathbb{F}}$. 则存在$\delta=\delta(p,L,T)>0$，使得当$t-t'<\delta$时，[[#^082c3b|FBSDE]]存在唯一解$\Theta(\cdot)\in M^p_{\mathbb{F}}$且成立以下$L^p$估计
$$
\begin{align}
\mathbb{E}^{\mathcal{F}_t}\left[\sup_{s\in[t,t']}|X(s)|^p+\sup_{s\in[t,t']}|Y(s)|^p+\left(\int_{t}^{t'}|Z(s)|^2{d}s\right)^{\frac{p}{2}}\right]\le C_p\mathbb{E}^{\mathcal{F}_t}\left[|\xi|^p+|\eta|^p+I(p)\right]
\end{align}
$$
这里$C=C(p,L,T)>0$为常数，$I(t,t';p)$为
$$
I(t,t';p)=\left(\int_{t}^{t'}|g(s,0)|{d}s\right)^p+\left(\int_{t}^{t'}|b(s,0)|{d}s\right)^p+\left(\int_{t}^{t'}|\sigma(s,0)|{d}s\right)^{\frac{p}{2}}
$$
```
**Proof**
主要证明方法是**压缩映像法**。给定$(y,z)\in L^p_\mathbb{F}(\Omega,C[t,t'])\times L^p_\mathbb{F}(\Omega,L^2[t,t'])$, 我们引入下面的解耦的FBSDEs，
$$
\begin{cases}
dX=b(X,y,z)ds+\sigma(X,y,z)dW_s\\
dY=g(X,Y,Z)ds+ZdW_s\\
X(t)=\xi,Y(t')=\eta
\end{cases}
$$
其中由SDE，BSDE的存在唯一性得到$(X,Y,Z)\in M^p_\mathbb{F}$为上述方程的解。可以定义压缩映射：
$$
\mathscr{J}:(y,z)\mapsto(Y,Z)
$$
定义差分过程$\hat{\phi}=\phi-\bar{\phi}$其中$\phi=X,Y,Z,y,z.etc$根据SDE的$L^p$标准估计，
$$
\begin{align}
|\hat{X}|^p\le C\left[\left(\int_{t}^{t'}|b(X,y,z)-b(\bar{X},\bar{y},\bar{z})|{d}s\right)^p+\sup_{[t,t']\subseteq[0,T]}\left|\int_{t}^{t'}\sigma(X,y,z)-\sigma(\bar{X},\bar{y},\bar{z}){d}s\right|^p\right]
\end{align}
$$
由BDG不等式和Lipschitz条件，
$$
\begin{align}
\mathbb{E}\left[\sup_{s\in[t,t']}|\hat{X}|^p\right]&\le C\mathbb{E}\left[\left(\int_{t}^{t'}|b(X,y,z)-b(\bar{X},\bar{y},\bar{z})|{d}s\right)^p+\left(\int_{t}^{t'}|\sigma(X,y,z)-\sigma(\bar{X},\bar{y},\bar{z})|{d}s\right)^\frac{p}{2}\right]\\
&\le C\mathbb{E}\left[(t-t')\sup_{s\in[t,t']}|\hat{X}|^p+(t-t')\sup_{s\in[t,t']}|\hat{y}|^p+\left(\int_{t}^{t'}|\hat{z}|^2{d}s\right)^{\frac{p}{2}}\right]\\
\Longrightarrow&\mathbb{E}\left[\sup_{s\in[t,t']}|\hat{X}|^p\right]\le C_FK\mathbb{E}\left[\sup_{s\in[t,t']}|\hat{y}|^p+\left(\int_{t}^{t'}|\hat{z}|^2{d}s\right)^{\frac{p}{2}}\right]
\end{align}
$$
这里需要$t'-t<\frac{1}{C}$, 其中$C_F=C_F(p,L,T)>0,K=K(p,L,T)>0$。由BSDE的$L^p$标准估计，
$$
\begin{align}
\mathbb{E}\left[\sup_{s\in[t,t']}|\hat{Y}|^p+\left(\int_{t}^{t'}|\hat{Z}|^2{ds}\right)^{\frac{p}{2}}\right]&\le C_B\mathbb{E}\left[\int_{t}^{t'}|g(X,Y,Z)-g(\bar{X},\bar{Y},\bar{Z})|{d}s\right]^p\\
&\le C_BL^p(t'-t)^p\mathbb{E}\left[\sup_{s\in[t,t']}|\hat{X}|^p\right]\\
&\le C_BC_FKL^p(t'-t)^p\mathbb{E}\left[\sup_{s\in[t,t']}|\hat{y}|^p+\left(\int_{t}^{t'}|\hat{z}|^2{d}s\right)^{\frac{p}{2}}\right]
\end{align}
$$
取$\delta=\min\{\frac{1}{2L\sqrt[p]{C_BC_FK}},\frac{1}{C}\}$，当$t'-t<\delta$时，映射$\mathscr{J}$为压缩映射。
**QED**
```ad-lemma
title:引理3.1（一维全局可测隐函数定理）
令$(\mathbb{X},\mathcal{G})$为可测空间，映射$f:\mathbb{X}\times\mathbb{R}\to\mathbb{R}$是$\mathcal{G}\otimes\mathcal{B}/\mathcal{B}$可测的。若对每个$x\in\mathbb{X}$，都存在一个$u(x)\in\mathbb{R}$使得$f(x,u(x))=0$且映射$u\mapsto f(x,u)$是连续的，则映射$u:\mathbb{X}\to\mathbb{R}$是$\mathcal{G}/\mathcal{B}$可测的。
```

^8107f1

**Proof**
由条件对固定的$x\in\mathbb{X}$，存在$u(x)$ s.t. $f(x,u(x))=0$并且$u\mapsto f(x,u)$是连续的。由介值性定理，对任何$v>u$都有$f(x,v)<0$或者$f(x,v)>0$。对固定的$M>0$，我们考虑以下集合
$$
\mathbb{X}^+_M=\{x:f(x,M)>0\},\mathbb{X}^-_M=\{x:f(x,M)<0\}
$$
由于$f$可测且$\mathbb{X}^+_M,\mathbb{X}^-_M$可以写成
$$
\mathbb{X}^+_M=\{x:f(x,v)>0\}\cap\{v=M\},\mathbb{X}^-_M=\{x:f(x,v)<0\}\cap\{v=M\}
$$
因此$\mathbb{X}^+_M,\mathbb{X}^-_M$都是$\mathcal{G}$可测的。注意到有以下分解$$\mathbb{X}^+_M=(\mathbb{X}^+_M\cap\{x:u(x)< M\})\cup(\mathbb{X}^+_M\cap\{x:u(x)\ge M\})$$
令$M\to\infty$时，$\mathbb{X}^+_M\cap\{x:u(x)< M\}$单调递增，$\mathbb{X}^+_M\cap\{x:u(x)\ge M\}\subseteq\{x:u(x)\ge M\}$单调递减为$\emptyset$，同样对$\mathbb{X}^-_M$也有同样的结果，记$\mathbb{X}_M^+\to\mathbb{X}^+,\mathbb{X}_M^-\to\mathbb{X}^-$。因此$\mathbb{X}=\mathbb{X}^++\mathbb{X}^-$，由极限保持可测性，因此$\mathbb{X}^+,\mathbb{X}^-$均$\mathcal{G}$可测。这里引用测度论的结果，
![[Pasted image 20260419185527.png]]
![[Pasted image 20260419185506.png]]
我们考虑证明集合$\{(x,v):u(x)<v\}$可测来证明$u$的可测性。我们断言
$$
\{(x,v):u(x)<v\}=((\mathbb{X}^+\times\mathbb{R})\cap\{(x,v):f(x,v)>0\})\cup((\mathbb{X}^-\times\mathbb{R})\cap\{(x,v):f(x,v)<0\})
$$
这是因为，对于固定的$x$，$v\mapsto f(x,v)$是连续的，且存在唯一零点$u$，因此

- $x\in\mathbb{X}^+$, $f(x,v)>0\Longrightarrow v>u(x)$
- $x\in\mathbb{X}^-$, $f(x,v)<0\Longrightarrow v>u(x)$

由于$f$可测，所以集合$\{(x,v):u(x)<v\}$可测，从而$u$是$\mathcal{G}/\mathcal{B}$可测。
**QED**
收到Peng-Hu，Peng-Wu引入单调性条件启发，通过引入但单调性条件可以建立一般的全局可测隐函数定理。
```ad-thm
title:定理3.3(全局可测隐函数定理)
令$(\mathbb{X},\mathcal{G})$为可测空间，映射$f:\mathbb{X}\times\mathbb{R}^n\times\mathbb{R}^m\to\mathbb{R}^m$是$\mathcal{G}\otimes\mathcal{B}(\mathbb{R}^n)\otimes\mathcal{B}(\mathbb{R}^m)/\mathcal{B}(\mathbb{R}^m)$可测的，假设以下条件：对任意的$(x,y)\in\mathbb{X}\times\mathbb{R}^n$, 
1. **($u$-单调)**存在一个满秩矩阵$U(x,y)\in\mathbb{R}^{n\times m}$满足$\|U(x,y)\|=1$和常数$c(x,y)>0$使得对任意的$u,\bar{u}\in\mathbb{R}^m$
   $$
   \langle U(x,y)(f(x,y,u)-f(x,y,\bar{u})),u-\bar{u}\rangle\ge c(x,y)|u-\bar{u}|^2
   $$
2. **($u$-Lipschitz连续)**存在常数$L_f(x,y)>0$，使得
   $$
   |f(x,y,u)-f(x,y,\bar{u})|\le L_f(x,y)|u-\bar{u}|
   $$

则对任意的$(x,y)\in\mathbb{X}\times\mathbb{R}^n$, 存在唯一的$u:\mathbb{X}\times\mathbb{R}^n\to\mathbb{R}^m$使得$f(x,y,u(x,y))=0$，并且$u$是$\mathcal{G}\times\mathcal{B}(\mathbb{R}^n)/\mathcal{B}(\mathbb{R}^m)$。进一步地，若$f$对$y$是Lipschitz连续的：对任意的$(x,u)\in\mathbb{X}\times\mathbb{R}_m$
$$
|f(x,y,u)-f(x,\bar{y},u)|\le M(x,y)|y-\bar{y}|
$$
则隐函数$u$满足对任意的$x\in\mathbb{X}$
$$
|u(x,y)-u(x,\bar{y})|\le \frac{M(x,y)}{c(x,y)}|y-\bar{y}|
$$
```

^1aef77

**Proof**
**Step1：证明隐函数的存在性。**
对固定的$(x_0,y_0)\in\mathbb{X}\times\mathbb{R}$，定义函数$\mathscr{P}:\mathbb{R}^m\to\mathbb{R}^m$如下：
$$
\mathscr{P}(u)=u-\frac{1}{C(x_0,y_0)}U(x_0,y_0)f(x_0,y_0,u)
$$
其中$C(x_0,y_0)$为待定常数，我们希望证明这是一个压缩映射。对任意的$u,\bar{u}\in\mathbb{R}^m$
$$
\begin{align}
|\mathscr{P}(u)-\mathscr{P}(\bar{u})|^2&=\left|(u-\bar{u})-\frac{1}{C(x_0,y_0)}U(x_0,y_0)\left(f(x_0,y_0,u)-f(x_0,y_0,\bar{u})\right)\right|^2\\
&=|u-\bar{u}|^2-\frac{2}{C(x_0,y_0)}\left\langle U(x_0,y_0)(f(x_0,y_0,u)-f(x_0,y_0,\bar{u})),u-\bar{u}\right\rangle\\
&+\frac{1}{C^2(x_0,y_0)}|f(x_0,y_0,u)-f(x_0,y_0,\bar{u})|^2\\
&\le |u-\bar{u}|^2-\frac{2c(x_0,y_0)}{C(x_0,y_0)}|u-\bar{u}|^2+\frac{L_f^2(x_0,y_0)}{C^2(x_0,y_0)}|u-\bar{u}|^2\\
\end{align}
$$
我们取$C(x_0,y_0)>\max\{\frac{L^2_f(x_0,y_0)}{c(x_0,y_0)},2c(x_0,y_0)\}$，这就证明了$\mathscr{P}$是一个压缩映射，由不动点定理，存在唯一一个不动点使得
$$
\mathscr{P}(u)=u\Longrightarrow f(x,y,u)=0
$$
**Step2：隐函数的Lipschitz连续性。**
对固定的$x\in\mathbb{X},y,\bar{y}\in\mathbb{R}^m$，$f(x,y,u(x,y))=f(x,\bar{y},u(x,\bar{y}))=0$。我们考虑
$$
\begin{align}
&\left\langle U(x,y)[f(x,y,u(x,y))-f(x,\bar{y},u(x,\bar{y}))],u(x,y)-u(x,\bar{y})\right\rangle\\
=&\left\langle U(x,y)[f(x,y,u(x,y))-f(x,y,u(x,\bar{y}))],u(x,y)-u(x,\bar{y})\right\rangle\\
&+\left\langle U(x,y)[f(x,y,u(x,\bar{y}))-f(x,\bar{y},u(x,\bar{y}))],u(x,y)-u(x,\bar{y})\right\rangle\\
\ge&c(x,y)|u(x,y)-u(x,\bar{y})|^2-M(x,y)|y-\bar{y}|\cdot|u(x,y)-u(x,\bar{y})|
\end{align}
$$
注意到
$$
\left\langle U(x,y)[f(x,y,u(x,y))-f(x,\bar{y},u(x,\bar{y}))],u(x,y)-u(x,\bar{y})\right\rangle=0
$$
所以
$$
|u(x,y)-u(x,\bar{y})|\le\frac{M(x,y)}{c(x,y)}|y-\bar{y}|
$$
**Step3：隐函数的可测性。**
考虑归纳法。当$m=1$时，根据[[#^8107f1|引理3.1证明最后一步]]，可知$u$是$\mathcal{G}\otimes\mathcal{B}(\mathbb{R}^n)/\mathcal{B}(\mathbb{R})$可测的。现假设对$m>1$时结论成立。
**QED**
```ad-proposition
title:推论3.4（Jacobi矩阵正定时可以得到连续可微的版本）
以下结论蕴含($u$-单调)和($u$-Lipschitz连续)条件：$f$对变量$u\in\mathbb{R}^m$连续可微。对任意的$(x,y)\in\mathbb{X}\times\mathbb{R}^n$,
1. 存在一个满秩矩阵$U(x,y)\in\mathbb{R}^{m\times m}$满足$\|U(x,y)\|=1$使得
   $$
   U(x,y)\frac{\partial f}{\partial u}(x,y,u)=U(x,y)\left(\frac{\partial f_i}{\partial u_j}(x,y,u)\right)_{m\times m}
   $$
   是一致正定的 i.e. 存在常数$c(x,y)>0$使得对任意的$\hat{u},u\in\mathbb{R}^m$
   $$
   \left\langle U(x,y)\frac{\partial f}{\partial u}(x,y,u)\hat{u},\hat{u}\right\rangle\ge c(x,y)|\hat{u}|^2
   $$
2. Jocobi矩阵$\frac{\partial f}{\partial u}(x,y,\cdot)$是有界的 i.e. 存在常数$L_f(x,y)>0$使得
   $$
   \left|\frac{\partial f}{\partial u}(x,y,u)\right|\le L_f(x,y)
   $$

因此[[#^1aef77|定理3.3]]的条件可以替换成上述两个条件，且所有结论依然成立。
```
**Proof**
由中值定理，对任意的$(x,y)\in\mathbb{X}\times\mathbb{R}^n$，$u,\bar{u}\in\mathbb{R}^m$，对每个分量$k=1,\cdots,m$，存在向量$\tilde{u}^k$ s.t. 
$$
f_k(x,y,u)-f_k(x,y,\bar{u})=\sum_{j=1}^{m}\frac{\partial f_k}{\partial u_j}(x,y,\tilde{u}^k)(u_j-\bar{u}_j)
$$
因此
$$
|f_k(x,y,u)-f_k(x,y,\bar{u})|\le L_f(x,y)\sum_{j=1}^{m}|u_j-\bar{u}_j|=L_f(x,y)|u-\bar{u}|
$$
从而
$$
|f(x,y,u)-f(x,y,\bar{u})|\le\sum_{k=1}^{m}|f_k(x,y,u)-f_k(x,y,\bar{u})|\le mL_f(x,y)|u-\bar{u}|
$$
另外定义函数$h:[0,1]\to\mathbb{R}$: 
$$
h(t)=\left\langle U(x,y)[f(x,y,\bar{u}+t(u-\bar{u}))-f(x,y,\bar{u})],u-\bar{u}\right\rangle
$$
显然$h(0)=0,h(1)=\left\langle U(x,y)[f(x,y,u)-f(x,y,\bar{u})],u-\bar{u}\right\rangle$, 从而
$$
\begin{align}
&h(1)-h(0)=h'(\alpha)\\
\Longleftrightarrow&\left\langle U(x,y)[f(x,y,u)-f(x,y,\bar{u})],u-\bar{u}\right\rangle\\
=&\left\langle U(x,y)\frac{\partial f}{\partial u}(x,y,\bar{u}+\alpha(u-\bar{u}))(u-\bar{u}),u-\bar{u}\right\rangle\ge c(x,y)|u-\bar{u}|^2
\end{align}
$$
**QED**
```ad-proposition
title:推论3.5（无单调性条件的情况下，可以让Lipschitz常数充分小）
以下结论蕴含($u$-单调)和($u$-Lipschitz连续)条件：对任意的$(x,y)\in\mathbb{X}\times\mathbb{R}^n$，存在常数$l(x,y)\in[0,1)$使得对$\bar{u},u\in\mathbb{R}_m$
$$
|(u+f(x,y,u))-(\bar{u}+f(x,y,\bar{u}))|\le l(x,y)|u-\bar{u}|
$$
因此[[#^1aef77|定理3.3]]的条件可以替换成上述两个条件，且所有结论依然成立。
```
**Proof**
实际上只需要验证$u$-单调条件即可，这是因为
$$
\begin{align}
|f(x,y,u)-f(x,y,\bar{u})|&\le |(u+f(x,y,u))-(\bar{u}+f(x,y,\bar{u}))|+|u-\bar{u}|\\
&\le (1+l(x,y))|u-\bar{u}|
\end{align}
$$
$u$-Lipschitz条件自然满足。对固定的$(x,y)\in\mathbb{X}\times\mathbb{R}^n$，取满秩矩阵为$I_m$
$$
\begin{align}
&-\left\langle f(x,y,u)-f(x,y,\bar{u}),u-\bar{u}\right\rangle\\
=&-\left\langle u+f(x,y,u))-(\bar{u}+f(x,y,\bar{u}),u-\bar{u}\right\rangle+|u-\bar{u}|^2\\
\ge&(1-l(x,y))|u-\bar{u}|^2
\end{align}
$$
**QED**
现在开始进入到FBSDEs的$L^p$理论。
```ad-def
title:记号
记
$$
\textbf{G}=\begin{bmatrix}
G &&\\
&G&\\
&&\ddots&\\
&&&G
\end{bmatrix}_{md\times nd}
$$
注意到$\|\textbf{G}\|=\|G\|$。对任意的$\omega\times s\in\Omega\times[t,t']$定义
$$
\tilde{\theta}=\begin{bmatrix}
\tilde{x}\\
\tilde{y}\\
\tilde{z}
\end{bmatrix}=\begin{bmatrix}
x\\
y-Gx\\
z-\textbf{G}\sigma(\omega,s,x,y,z)
\end{bmatrix},\theta=\begin{bmatrix}
x\\
y\\
z
\end{bmatrix}\in\mathbb{R}^{n+m+md}
$$
```

^bbc612

```ad-def
title:假设(H2)
存在满秩矩阵$U\in\mathbb{R}^{md\times md}$满足$\|U\|=1$和常数$c>0$使得对任意$(\omega,s,x,y)\in\Omega\times[t,t']\times\mathbb{R}^n\times\mathbb{R}^m$和对任意的$z,\bar{z}\in\mathbb{R}^{md}$，
$$
\left\langle U[((z-\bar{z})-\textbf{G}(\sigma(\omega,s,x,y,z)-\sigma(\omega,s,x,y,\bar{z})))],z-\bar{z}\right\rangle\ge c|z-\bar{z}|^2
$$
```

```ad-lemma
title:引理4.1
在(H1)(H2)假设下，存在一个函数$\varphi:\Omega\times[t,t']\times\mathbb{R}^{n+m+md}\to\mathbb{R}^{md}$使得
$$ 
\tilde{z} = \varphi(\omega, s, \tilde{\theta}) - \mathbf{G} \sigma\bigl(\omega, s, \tilde{x}, \tilde{y} + G \tilde{x}, \varphi(\omega, s, \tilde{\theta})\bigr),\forall  (\omega, s, \tilde{\theta}) \in \Omega \times [t, t'] \times \mathbb{R}^{n + m + md}
$$
进一步有
1. $\forall(\omega,s)\in\Omega\times[t,t']$[[#^bbc612|映射]]存在逆映射
   $$
   \theta=\begin{bmatrix}
x\\
y\\
z
\end{bmatrix}=\begin{bmatrix}
\tilde{x}\\
\tilde{y}+G\tilde{x}\\
\varphi(\omega,s,\tilde{x},\tilde{y},\tilde{z})
\end{bmatrix},\forall\tilde{\theta}=\begin{bmatrix}
\tilde{x}\\
\tilde{y}\\
\tilde{z}
\end{bmatrix}\in\mathbb{R}^{n+m+md}
   $$
2. $\varphi$是$\mathcal{G}\otimes\mathcal{B}(\mathbb{R}^{n+m+md})/\mathcal{B}(\mathbb{R}^{md})$可测的
3. 一致Lipschitz连续性：
   $$
   |\varphi(s,\tilde{\theta}_1)-\varphi(s,\tilde{\theta}_2)|\le L_\varphi(c,L,\|G\|)|\tilde{\theta}_1-\tilde{\theta}_2|
   $$
4. $\forall(\omega,s,\tilde{\theta})\in\Omega\times[t,t']\times\mathbb{R}^{n+m+md}$, 成立以下估计：
   $$
   |\varphi(\omega,s,\tilde{\theta})|\le\frac{1}{c}\big(|\tilde{z}|+\|G\||\sigma(\omega,s,\tilde{x},\tilde{y}+G\tilde{x},0)|\big)
   $$
```
**Proof**
定义映射$f:\Omega\times[t,t']\times\mathbb{R}^{n+m+md}\times\mathbb{R}^{md}\to\mathbb{R}^{md}$: 
$$
f(\omega,s,\tilde{\theta},z)=z-\symbf{G}\sigma(\omega,s,\tilde{\theta},z)-\tilde{z}
$$
我们希望使用全局可测隐函数定理证明$\varphi$的存在性和可测性。由于$\sigma$是$\mathcal{G}\otimes\mathcal{B}(\mathbb{R}^{md})/\mathbb{R}^{md}$可测的，所以$f$是$\mathcal{G}\otimes\mathcal{B}(\mathbb{R}^{n+m+md})/\mathcal{B}(\mathbb{R}^{md})$。我们要验证条件$u$-单调和$u$-Lipschitz连续，取假设(H2)中的满秩矩阵$U$，$z,z\in\mathbb{R}^{md}$
$$
\begin{align}
&\left\langle U(f(\omega,s,\tilde{\theta},z)-f(\omega,s,\tilde{\theta},\bar{z})),z-\bar{z}\right\rangle\\
=&\left\langle U((z-\bar{z})-\symbf{G}(\sigma(\omega,s,\tilde{x},\tilde{y}+G\tilde{x},\tilde{z})-\sigma(\omega,s,\tilde{x},\tilde{y}+G\tilde{x},z))),z-\bar{z}\right\rangle\\
\ge& c|z-\bar{z}|^2\tag{H2}
\end{align}
$$
由假设(H1)可以得到
$$
\begin{align}
&|f(\omega,s,\tilde{\theta},z)-f(\omega,s,\tilde{\theta},\bar{z})|\\
\le &(z-\bar{z})-\symbf{G}(\sigma(\omega,s,\tilde{\theta},z)-\sigma(\omega,s,\tilde{\theta},\bar{z}))\\
\le &(1+\|G\|L)|z-\bar{z}|
\end{align}
$$
**QED**
```ad-thm
title:定理4.2
$p>1,0\le t<t'\le T$, (H1)(H2)假设成立。$\xi\in L^p_{\mathcal{F}_t}(\Omega,\mathbb{R}^n),\eta\in L^p_{\mathcal{F}_{t'}}(\Omega,\mathbb{R}^n),\Gamma(\cdot,0)\in\mathcal{M}^p_{\mathbb{F}}$. 则存在$\delta=\delta(p,L,\|G\|,T,c)>0$，使得当$t-t'<\delta$时，[[#^082c3b|FBSDE]]存在唯一解$\Theta(\cdot)\in M^p_{\mathbb{F}}$且成立以下$L^p$估计
$$
\begin{align}
\mathbb{E}^{\mathcal{F}_t}\left[\sup_{s\in[t,t']}|X(s)|^p+\sup_{s\in[t,t']}|Y(s)|^p+\left(\int_{t}^{t'}|Z(s)|^2{d}s\right)^{\frac{p}{2}}\right]\le C_p\mathbb{E}^{\mathcal{F}_t}\left[|\xi|^p+|\eta|^p+I(p)\right]
\end{align}
$$
这里$C=C(p,L,\|G\|,T,c)>0$为常数，$I(t,t';p)$为
$$
I(t,t';p)=\left(\int_{t}^{t'}|g(s,0)|{d}s\right)^p+\left(\int_{t}^{t'}|b(s,0)|{d}s\right)^p+\left(\int_{t}^{t'}|\sigma(s,0)|{d}s\right)^{\frac{p}{2}}
$$
若还有一组系数$(\bar{\xi},\bar{\eta},\bar{G},\bar{\Gamma})$满足相同的条件，则成立
$$
\begin{align}
&\mathbb{E}^{\mathcal{F}_t}\left[\sup_{s\in[t,t']}|\hat{X}(s)|^p+\sup_{s\in[t,t']}|\hat{Y}(s)|^p+\left(\int_{t}^{t'}|\hat{Z}(s)|^2{d}s\right)^{\frac{p}{2}}\right]\\
\le &C_p\mathbb{E}^{\mathcal{F}_t}\left[|\hat{\xi}|^p+|G\bar{X}(t')+\hat{\eta}|^p+\hat{I}(t,t';p)\right]
\end{align}
$$
带有hat的都表示差分过程。
```

```ad-def
title:假设(H2)'
存在满秩矩阵$U\in\mathbb{R}^{md\times md}$满足$\|U\|=1$和常数$c>0$使得对任意$(\omega,s,\theta)\in\Omega\times[t,t']\times\mathbb{R}^{n+m+md}$和对任意的$z,\bar{z}\in\mathbb{R}^{md}$，
$$
\left\langle U[I_{md}-\symbf{G}\frac{\partial\sigma}{\partial z}(\omega,s,\theta)]\hat{z},\hat{z}\right\rangle\ge c|\hat{z}|^2
$$
```

```ad-proposition
title:推论4.3（定理4.2的连续可微版本）
把条件(H2)换成(H2)'，定理4.2的结论依然成立
```

```ad-def
title:假设(H2)''
$$\|G\|L_z<1$$
```

```ad-proposition
title:推论4.4
把条件(H2)换成(H2)''，定理4.2的结论依然成立
```

```ad-def
title:假设(H2)'''
$m=n$，存在常数$\mu>0$使得对任意的$(\omega,s,\theta)\in\Omega\times[t,t']\times\mathbb{R}^{n+m+md}$, $\bar{x}\in\mathbb{R}^n,\bar{z}\in\mathbb{R}^{md}$
$$ 
\big\langle G(x - \bar{x}),\, x - \bar{x} \big\rangle \ge \mu \, \lvert x - \bar{x} \rvert^2 \mbox{和}\big\langle \sigma(\omega, s, x, y, z) - \sigma(\omega, s, x, y, \bar{z}),\, z - \bar{z} \big\rangle \le 0
$$ 
或者
$$ \big\langle G(x - \bar{x}),\, x - \bar{x} \big\rangle \le -\mu \, \lvert x - \bar{x} \rvert^2\mbox{和}\big\langle \sigma(\omega, s, x, y, z) - \sigma(\omega, s, x, y, \bar{z}),\, z - \bar{z} \big\rangle \ge 0. $$
```

```ad-proposition
title:推论4.6
把条件(H2)换成(H2)'''，定理4.2的结论依然成立
```

