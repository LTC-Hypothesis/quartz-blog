# Elementary Properties
```ad-def
title:Guassian vector 
An $\mathbb{R}^d$ valued stochastic process $X_t$ is called Guassian, if for $k\ge 1$ and real number $0\le t_1<t_2<\cdots<t_k<\infty$, vector $(X_{t_1},\cdots,X_{t_k})\sim N_k$. 
```

```ad-def
title:Stationary
The vector $(X_{t_1+t},\cdots,X_{t_k+t})$ is independent of $t$, we call it is stationary. 
```

```ad-def
title:Covariance matrix
Denote expectation vector $m(t)=\mathbb{E}(X_t)$ adn its covariance matrix 
$$
\gamma(s,t)=\mathbb{E}\left[(X_t-m(t))(X_s-m(s))^\top\right],s,t\ge0
$$
```

```ad-proposition
One-dimensional Brownian motion is a zero-mean Guassian vector and its covariance function is 
$$
\gamma(s,t)=s\wedge t,s,t\ge0
$$
```
**Proof**
If $s<t$, We have 
$$
\mathbb{E}[B_sB_t]=\mathbb{E}[(B_t-B_s)B_s+B_s^2]=s
$$
If $s\ge t$, we have $\mathbb{E}[B_sB_t]=t$. Above all, $\mathbb{E}[B_tB_s]=s\wedge t$ for any $s,t\ge0$. 
**QED**
```ad-proposition
title:SLLN of Brownian motion 
Suppose $W_t$ is one-dimensional Brownian motion. Then 
$$
\lim_{t\to\infty}\frac{W_t}{t}=0,a.s
$$
```
**Proof**
The idea is from [[Continuous-Time Martingales#^b55ecf|SLLN of Poisson process]]. Consider $\mathbb{P}\left(\sup_{2^n\le t\le 2^{n+1}}|\frac{W_t}{t}|\ge\varepsilon\right)$, since $\varepsilon\le \sup_{2^n\le t\le 2^{n+1}}|\frac{W_t}{t}|\le \frac{1}{2^n}\sup_{2^n\le t\le 2^{n+1}}|W_t|$ and $\sup_{2^n\le t\le 2^{n+1}}|W_t|\le \sup_{0\le t\le 2^{n+1}}|W_t|$, we have 
$$
\mathbb{P}\left(\sup_{2^n\le t\le 2^{n+1}}\left|\frac{W_t}{t}\right|\ge\varepsilon\right)\le \mathbb{P}\left(\sup_{2^n\le t\le 2^{n+1}}|W_t|\ge2^n\varepsilon\right)\le \mathbb{P}\left(\sup_{0\le t\le 2^{n+1}}|W_t|\ge2^n\varepsilon\right)
$$
Then 
$$
\begin{align}
\mathbb{P}\left(\sup_{0\le t\le 2^{n+1}}|W_t|\ge2^n\varepsilon\right)&\le \mathbb{P}\left(\sup_{0\le t\le 2^{n+1}}W_t\ge2^n\varepsilon\right)+
\mathbb{P}\left(\inf_{0\le t\le 2^{n+1}}W_t\le-2^n\varepsilon\right)\\
&=\mathbb{P}(M_{2^{n+1}}\ge2^n\varepsilon)+\mathbb{P}\left(-\sup_{0\le t\le 2^{n+1}}-W_t\le -2^n\varepsilon\right)\\
&=2\mathbb{P}(M_{2^{n+1}}\ge2^{n}\varepsilon)
\end{align}
$$
where $-W_t$ is also Brownian motion by follow proposition. We know the [[Computations Based on Passage Times#^f48608|distribution]] of $M_t$, then
$$
\begin{align}
2\mathbb{P}(M_{2^{n+1}}\ge2^n\varepsilon)&=2\int_{2^n\varepsilon}^{\infty}\frac{2}{\sqrt{2\pi2^{n+1}}}\exp\left(-\frac{x^2}{2^{n+1}}\right){d}x\\
&=\frac{4}{\sqrt{2\pi}}\int_{\varepsilon2^{\frac{n-1}{2}}}^{\infty}e^{-\frac{y^2}{2}}{d}y
\end{align}
$$
Hence, 
$$
\sum_{n=1}^{\infty}\mathbb{P}\left(\sup_{2^n\le t\le 2^{n+1}}\left|\frac{W_t}{t}\right|\ge\varepsilon\right)\le \sum_{n=1}^{\infty}\frac{4}{\sqrt{2\pi}}\int_{\varepsilon2^{\frac{n-1}{2}}}^{\infty}e^{-\frac{y^2}{2}}{d}y<\infty
$$
By Borel-Contelli lemma, $\frac{W_t}{t}\xrightarrow{a.s.}0$.
**QED**
```ad-proposition
When $W = \{W_t, \mathcal{F}_t; 0 \leq t < \infty\}$ is a standard Brownian motion, so are the processes obtained from the following "equivalence transformations":

1. **Scaling**: $X = \{X_t, \mathcal{F}_{ct}; 0 \leq t < \infty\}$ defined for $c > 0$ by
$$
X_t = \frac{1}{\sqrt{c}} W_{ct}, \quad 0 \leq t < \infty.
$$

2. **Time-inversion**: $Y = \{Y_t, \mathcal{F}_t^Y; 0 \leq t < \infty\}$ defined by
$$
Y_t = 
\begin{cases} 
t W_{1/t}, & 0 < t < \infty, \\
0, & t = 0.
\end{cases}
$$

3. **Time-reversal**: $Z = \{Z_t, \mathcal{F}_t^Z; 0 \leq t < \infty\}$ defined for $T > 0$ by
$$
Z_t = W_T - W_{T-t}, \quad 0 \leq t \leq T.
$$

4. **Symmetry**: $-W = \{ -W_t, \mathcal{F}_t; 0 \leq t < \infty\}$.
```
**Proof**
It only needs to check zero-mean and covariance.
1. We have $$\mathbb{E}(X_t)=\frac{1}{\sqrt{c}}\mathbb{E}(W_{ct})=0$$ and $$\gamma(s,t)=\mathbb{E}[X_sX_t]=\frac{1}{c}\mathbb{E}[W_{ct}W_{cs}]=\frac{1}{c}\cdot cs\wedge t=s\wedge t$$
2. We have $\mathbb{E}(Y_t)=t\mathbb{E}(W_{\frac{1}{t}})=0$ and $$\mathbb{E}[Y_sY_t]=st(\frac{1}{s}\wedge\frac{1}{t})=s\wedge t$$
3. We have $\mathbb{E}(Z_t)=0$ and $$\mathbb{E}[Z_sZ_t]=T-(T-t)-(T-s)+\mathbb{E}[W_{T-t}W_{T-s}]=t+s-t\vee s=t\wedge s$$
4. We have $\mathbb{E}(-W_t)=0$ and $$\mathbb{E}[W_tW_s]=t\wedge s$$

**QED**
```ad-proposition
The probability that Brownian motion returns to the origin infinitely often is one.
```

^b70ddc

**Proof**
By [[Brownian Filtrations#^e7729a|Brownian motion changes sign infinitely on small interval]], then for any small $\varepsilon>0$, the set $\{\omega:,t\in[0,\varepsilon],W_t(\omega)=0,i.o.\}$ has probability 1. Consider the time-inversion $Y_t$ is also Brownian motion, $Y_t$ changes sign infinitely on $[\frac{1}{\varepsilon},\infty)$ and thus the set $\{\omega:t\in[\frac{1}{\varepsilon},\infty),Y_t(\omega)=0\}$ has probability 1. Hence, the Brownian motion returns to origin infinitely on $[0,\infty)$ has probability 1.
**QED**
# The Zero Set and the Quadratic Variation
```ad-def
title:Zero set 
We define 
$$
\mathscr{Z}\triangleq\{(t,\omega)\in[0,\infty)\times\Omega:W_t(\omega)=0\}
$$
Fix $\omega\in\Omega$, we define 
$$
\mathscr{Z}_\omega=\{0\le t<\infty:W_t(\omega)=0\}
$$
```

```ad-thm
For $\mathbb{P}-a.s.\omega\in \Omega$, the zero set $\mathscr{Z}_\omega$
1. has Lebesgue measure zero, 
2. is closed and unbounded, 
3. has an accumulation point at $t = 0$, 
4. has no isolated point in $(0, \infty)$, 
5. is dense in $(0,\infty)$.
```

^47fc7b

**Proof**
1. We denote the Lebesgue measure as $\symrm{Leb}(\cdot)$. By Fubini Thm, $$\mathbb{E}[\symrm{Leb}(\mathscr{Z}_\omega)]=(\symrm{Leb}\times\mathbb{P})(\mathscr{Z})=\int_0^\infty\mathbb{P}[W_t(\omega)=0]{d}t=0$$ where $W_t$ has continuous path and the probability of taking value on one point is 0. Therefore, $\symrm{Leb}(\mathscr{Z}_\omega)=0$
2. Note that mapping $\mathscr{P}:t\mapsto W_t(\omega)$ is continuous, and $$\mathscr{Z}_\omega=\mathscr{P}^{-1}(\{0\})$$ Since $\{0\}$ is closed, $\mathscr{Z}_\omega$ is also closed. Since [[#^b70ddc|Brownian motion returns to the origin infinitely]], the set $\mathscr{Z}_\omega$ is unbounded.
3. Since [[Brownian Filtrations#^e7729a|Brownian motion changes sign infinitely on small interval]], for any neighborhood of $t=0$, there exists point in $[0,\varepsilon]$ for small $\varepsilon$. Hence, $t=0$ is accumulation point.
4. We have for $a,b\in\mathbb{Q}$, $$\{\omega\in\Omega:\mathscr{Z}_\omega\mbox{ has isolated point in }(0,\infty)\}=\bigcup_{a<b}\{\omega:\exists!s\in(a,b) \ s.t.\ W_s(\omega)=0 \}$$ We define the optional time $\beta_t=\inf\{s>t:W_s=0\}$. $\beta_t$ is surely finite. By 3. we have $\beta_0=0$. Consider $$\beta_{\beta_t(\omega)}(\omega)=\inf\{s>\beta_t(\omega):W_s=0\}=\beta_t(\omega)+\inf\{s>0:W_{s+\beta_t(\omega)}-W_{\beta_t(\omega)}=0\}$$ Note that $\beta_{\beta_t(\omega)}(\omega)=\beta_t(\omega)$, because $W_{s+\beta_t}-W_{\beta_t}$ is also [[The Strong Markov Property and the  Reflection Principle#^322053|standard Brownian motion]]. Therefore, for $0\le a<b<\infty$, $$\{\omega:\exists!s\in(a,b) \ s.t.\ W_s(\omega)=0 \}\subseteq\{\omega:\beta_a<b\mbox{ and }\beta_{\beta_a}>b\}$$ Then $\mathbb{P}\{\omega:\beta_a<b\mbox{ and }\beta_{\beta_a}>b\}=0$, hence$$\mathbb{P}\{\omega\in\Omega:\mathscr{Z}_\omega\mbox{ has isolated point in }(0,\infty)\}=0$$
5. It is obviously by 4.

**QED**
```ad-warning
If fix $b\in\mathbb{R}$, the level set $\mathscr{Z}_\omega(b)$ has the same properties from above theorem. 
```

```ad-proposition
title:Quadratic variation of Brownian motion
Let $\{\Pi_n\}_{n=1}^\infty$ be a sequence of partitions of the interval $[0, t]$ with  
$$
\lim_{n \to \infty} \|\Pi_n\| = 0.
$$
Then the quadratic variations  

$$
V_t^{(2)}(\Pi_n) \triangleq \sum_{k=1}^{m_n} |W_{t^{(n)}_k} - W_{t^{(n)}_{k-1}}|^2
$$

of the Brownian motion $W$ over these partitions converge to $t$ in $L^2$, as $n \to \infty$ i.e. 
$$
V^{(2)}_t\xrightarrow{L^2}t,\mbox{ as }n\to\infty
$$
If, furthermore, the partitions become so fine that $\sum_{n=1}^\infty \|\Pi_n\| < \infty$ holds, the preceding convergence takes place also with probability one.
```
**Proof**
We consider
$$
\begin{align}
\mathbb{E}\left|V^{(2)}_t-t\right|^2&=\mathbb{E}\left|\sum_{n=1}^{m}|W_{t^{(n)}_k}-W_{t^{(n)}_{k-1}}|^2-\sum_{k=1}^{m}(t_{k}^{(n)}-t^{(n)}_{k-1})\right|^2\\
&\le\sum_{k=1}^{m}|t^{(n)}_{k}-t^{(n)}_{k-1}|^2\mathbb{E}\left|\frac{(W_{t^{(n)}_k}-W_{t^{(n)}_k})^2}{t_k^{(n)}-t_{k-1}^{(n)}}-1\right|^2\\
&\le \|\Pi_n\|^2\sum_{k=1}^{m}\mathbb{E}(\chi_k^2(1)-1)^2\to0\mbox{ as }\|\Pi_n\|\to0
\end{align}
$$
**QED**
# Local Maxima and Points of Increase
```ad-thm
title:How oscillatory the Brownian path is
For almost every $\omega\in\Omega$, the sample path $W_.(\omega)$ is monotone in no interval.
```
**Proof**
For $s,t\in\mathbb{Q}$, set 
$$
F=\bigcup_{s<t}\{\omega\in\Omega:W_\cdot(\omega)\mbox{ is monotone on }[s,t]\}
$$
since every nonempty interval includes one with rational endpoints. By scaling and symmetry of Brownian motion, it suffices to show that $W_\cdot(\omega)$ is monotone for almost no $\omega$ on $[0,1]$. Let 
$$
A=\{\omega\in\Omega:W_\cdot(\omega) \mbox{ is nondecreasing on }[0,1]\}
$$
Note that 
$$
A=\bigcap_{n=1}^{\infty}\bigcap_{i=0}^{n-1}\{\omega\in\Omega:W_{\frac{i+1}{n}}-W_{\frac{i}{n}}\ge0\}
$$
By properties of Brownian motion,
$$
\begin{align}
\mathbb{P}\left(\bigcap_{i=0}^{n-1}\left\{\omega\in\Omega:W_{\frac{i+1}{n}}-W_{\frac{i}{n}}\ge0\right\}\right)&=\prod_{i=0}^{n-1}\mathbb{P}\left\{\omega\in\Omega:W_{\frac{i+1}{n}}-W_{\frac{i}{n}}\ge0\right\}=\frac{1}{2^n}
\end{align}
$$
Then $\mathbb{P}(A)=\lim_{n\to\infty}\mathbb{P}\left(\bigcap_{i=0}^{n-1}\left\{\omega\in\Omega:W_{\frac{i+1}{n}}-W_{\frac{i}{n}}\ge0\right\}\right)=0$. 
**QED**
```ad-def
title:Local maximum 
For $f:[0,\infty)\to\mathbb{R}$ be given function. A point $t$ of local maximum, if there exists a number $\delta > 0$ with $f(s) < f(t)$ valid for every $s \in[t - \delta, t+\delta]$; and a point of strict local maximum, if there exists a number $\delta > 0$ with $f(s) < f(t)$ valid for every $s\in[t-\delta,t+\delta]\setminus\{t\}$.
```

```ad-thm
For almost every $\omega\in\Omega$, the set of points of local maximum for the Brownian path $W_\cdot(\omega)$ is countable and dense in $[0, \infty)$, and all local maxima are strict.
```

```ad-def
title:A point of increase
A point of increase of size $\delta$, if for given $\delta > 0$ we have $f(s) \le f(t) \le f(u)$ for every $s \in [t - \delta, t)$ and $u \in (t, t + \delta]$; a point of strict increase of size $\delta$ if the preceding inequalities are strict;
A point of increase, if it is a point of increase of size $\delta$ for some $\delta > 0$; A point of strict increase, if it is a point of strict increase of size $\delta$ for some $\delta > 0$;
```

```ad-thm
title:Dvoretzky, Erdos,  Kakutani 
Almost every Brownian sample path has no point of increase (or decrease).
```
# Nowhere Differentiability
```ad-def
title:Dini derivates
For a continuous function $f:[0,\infty)\to\mathbb{R}$, we denote by 
$$
D^\pm f(t)=\varlimsup_{h\to0^\pm}\frac{f(t+h)-f(t)}{h},D_\pm f(t)=\varliminf_{h\to0^\pm}\frac{f(t+h)-f(t)}{h}
$$
$f$ is differentiable at $t$ from the right(left), if it holds $$D^+f(t)=D_+f(t)<\infty(D^-f(t)=D_-f(t)<\infty)$$
$f$ is differentiable at $t$, if it holds $D^+f(t)=D_+f(t)=D^-f(t)=D_-f(t)<\infty$
```

```ad-thm
title:Paley, Wiener, Zygmund
For almost every $\omega\in\Omega$, the Brownian sample path $W_\cdot(w)$ is nowhere differentiable. More precisely, the set
$$
\{\omega\in\Omega:\forall t\in[0,\infty),\mbox{ either }D^+W_t(\omega)=+\infty\mbox{ or }D_+W_t(\omega)=-\infty \}
$$
contains an event $F \in\mathcal{F}$ with $\mathbb{P}(F) = 1$.
```
# Law of the Iterated Logarithm
```ad-thm
title:Law of the iterated logarithm
For almost every $\omega \in \Omega$, we have
(i) 
$$
\limsup_{t \to 0} \frac{W_t(\omega)}{\sqrt{2t \log \log(1/t)}} = 1,
$$
(ii) 
$$
\liminf_{t \to 0} \frac{W_t(\omega)}{\sqrt{2t \log \log(1/t)}} = -1,
$$
(iii) 
$$
\limsup_{t \to \infty} \frac{W_t(\omega)}{\sqrt{2t \log \log t}} = 1,
$$
(iv) 
$$
\liminf_{t \to \infty} \frac{W_t(\omega)}{\sqrt{2t \log \log t}} = -1.
$$
```

^795b12