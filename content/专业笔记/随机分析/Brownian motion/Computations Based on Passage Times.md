# Brownian Motion and Its Running Maximum
```ad-def
title:Running Maximum
Let $W_t,(\Omega,\mathcal{F}),\{\mathbb{P}^x\}$ be a 1-dimensional Brownian family. We define the running maximum,
$$
M_t=\max_{0\le s\le t}W_s
$$
```

```ad-proposition
For $t>0,x\le y$ and $y\ge0$,
$$
\mathbb{P}^0(W_t\in dx,M_t\in dy)=\frac{2(2y-x)}{\sqrt{2\pi t^3}}\exp\left(-\frac{(2y-x)^2}{2t}\right)dxdy
$$
```

^ca4621

**Proof**
By sysmmetry of Brownian motion, for $0\le s\le t$, 
$$
\begin{align}
(U_{t-s}\mathbb{1}_{(-\infty,x]})(y)=\mathbb{P}^y(W_{t-s}\le x)=\mathbb{P}^y(W_{t-s}\ge2y-x)=(U_{t-s}\mathbb{1}_{[2y-x,\infty)})(y)
\end{align}
$$
Since Brownian family is strong Markov family, by [[The Strong Markov Property and the  Reflection Principle#^1e90be|the proposition]], we have 
$$
\begin{align}
\mathbb{P}^0(W_t\le x|\mathcal{F}_{T_y+})=(U_{t-T_y}\mathbb{1}_{(-\infty,x]})(y)=(U_{t-T_y}\mathbb{1}_{[2y-x,\infty)})(y)=\mathbb{P}^0(W_t\ge2y-x|\mathcal{F}_{T_y+})
\end{align}
$$
The equality holds on $\{T_y\le t\},a.s.-\mathbb{P}^0$. Integrating both side on $\{T_y<t\}$, we have $\mathbb{P}^0(W_t\le x)=\mathbb{P}^0(W_t\ge2y-x)$ on $\{T_y<t\}$. Note that $\{T_y\le t\}=\{M_t\ge y\}$, then 
$$
\begin{align}
\mathbb{P}^0(W_t\le x,M_t\ge y)&=\mathbb{P}^0(W_t\le x,T_y\le t)=\mathbb{P}^0(W_t\le x)=\mathbb{P}^0(W_t\ge2y-x)\\
&=\frac{1}{\sqrt{2\pi t}}\int_{2y-x}^{\infty}e^{-\frac{u^2}{2t}}{d}u\\
\Longrightarrow\mathbb{P}^0(W_t\le x,M_t\le y)&=\mathbb{P}^0(W_t\le x)-\mathbb{P}^0(W_t\le x,M_t\le y)=\frac{1}{\sqrt{2\pi t}}\int_{x}^{2y-x}e^{-\frac{u^2}{2t}}du\\
\Longrightarrow\mathbb{P}^0(W_t\in dx,M_t\in dy)&=\frac{2(2y-x)}{\sqrt{2\pi t^3}}\exp\left(-\frac{(2y-x)^2}{2t}\right)dxdy
\end{align}
$$
**QED**
```ad-proposition
The process of passage time $T=\{T_a,\mathcal{F}_{T_a+}\}$ has the property that, under $\mathbb{P}^0$ and for $0 \le a < b$, the increment $T_b -T_a$, is independent of $\mathcal{F}_{T_a+}$ and has the density
$$
\mathbb{P}^0(T_b-T_a\in dt)=\frac{b-a}{\sqrt{2\pi t^3}}e^{-\frac{b-a}{2t}}{d}t
$$
In particular,
$$
\mathbb{E}^0[e^{-\alpha(T_b-T_a)}|\mathcal{F}_{T_a+}]=e^{-(b-a)\sqrt{2\alpha}}
$$
```

^405d7c

**Proof**
By [[The Strong Markov Property and the  Reflection Principle#^322053|Strong Markov property of Brownian motion]], we can write $T_b-T_a$ as
$$
T_b-T_a=\inf\{t\ge0:W_{T_a+t}-W_{T_a}=b-a\}
$$
$W_{T_a+t}-W_{T_a}$ is also a Brownian motion, then by [[#^ca4621|the distribution of running maximum]], we have 
$$
\mathbb{P}^0(T_b-T_a\in dt)=\frac{b-a}{\sqrt{2\pi t^3}}e^{-\frac{b-a}{2t}}{d}t
$$
**QED**
# Brownian Motion on a Half-Line
We consider Brownian motion is constrained to have state space $[0,\infty)$.
```ad-proposition
title:The transition density for Brownian motion absorbed at the origin
Brownian motion absorbed at the origin: $W_{t\wedge T_0}$ has transition density as follows, for $t>0,x,y>0$, 
$$
\mathbb{P}^x[W_t\in dy,T_0>t]=p_-(t;x,y){d}y\triangleq p(t;x,y)-p(t;x,-y){d}y
$$
where $p(t;x,y)$ is [[Kolmogorov's Construction of Brownian Motion#^dd51a8|Guassian kernal]].
```
**Proof**
Note that $\mathbb{P}^x[W_t\in dy]=p(t;x,y)dy$. By [[The Strong Markov Property and the  Reflection Principle#^48be42|Reflection Principle]], 
$$
\mathbb{P}^x[W_t\in dy,T_0\le t]=\mathbb{P}^{x}[W_t\in -dy]
$$
Then 
$$
\begin{align}
\mathbb{P}^x[W_t\in dy,T_0>t]&=\mathbb{P}^x[W_t\in dy]-\mathbb{P}^x[W_t\in dy,T_0\le t]\\
&=p(t;x,y)-p(t;x,-y)=p_-(t;x,y)
\end{align}
$$
**QED**
```ad-proposition
title:The transition density for Brownian motion reflected
Under $\mathbb{P}^0$, reflected Brownian motion $|W_t|$ is a Markov process with transition density,
$$
\mathbb{P}^0[|W_{t+s}|\in dy||W_t|=x]=p_+(t;x,y){d}y\triangleq p(t;x,y)+p(t;x,-y){d}y
$$
```
**Proof**
Since Brownian motion is Markov process, $|W_t|=f(W_t)$ where $f(x)=|x|$ is continuous. Then $|W_t|$ is also Markov process. 
$$
\mathbb{P}^0[|W_{t+s}|\in dy||W_t|=x]=\mathbb{P}^x[W_s\in dy]+\mathbb{P}^x[W_s\in -dy]=p_+(t;x,y)
$$
**QED**
```ad-proposition
Let $Y_t\triangleq M_t-W_t$. Under $\mathbb{P}^0$, the process $Y_t$ is Markov process and has transition density,
$$
\mathbb{P}^0[Y_{t+s}\in dy|Y_t=x]=p_+(t;x,y){d}y
$$
```
**Proof**
Since Brownian motion is Markov process, $M_t-W_t=f(W_t)$ where $f(x)=\max x-x$ and thus $Y_t$ is also Markov process. 
$$
\begin{align}
\mathbb{P}^0[Y_{t+s}\in dy|Y_t=x]=\mathbb{P}^x[Y_s\in dy]=\mathbb{P}^x[|W_s|\in dy]=p_+(t;x,y)
\end{align}
$$
where $Y_t$ and $|W_t|$ have the same distribution by [[#^f48608|Exercise]]. 
**QED**
# Brownian Motion on a Finite Interval
We consider the state space in $[0,a]$. 
```ad-def
Consider the function $\varphi:\mathbb{R}\to[0,a]$ which satisfies $\varphi(2na)=0,\varphi((2n+1)a)=a,$ $n=0,\pm1,\pm2,\cdots$,and linear between these point.
![[364bb2d70ae49d20c99daa9665fe8bcc.jpg]]
```

```ad-proposition
title:The transition density for Brownian motion absorbed at $0$ and $a$
Choose $0<x<a$. Then for $t>0,0<y<a$, 
$$
\mathbb{P}^x[W_t\in dy,T_0\wedge T_a>t]=\sum_{n=-\infty}^{\infty}p_-(t;x,y+2na){d}y
$$
```

^2932ef

```ad-proposition
For $t>0,0\le x\le a$, 
$$
\begin{align}
\mathbb{P}^x[T_0\wedge T_a\in dt]=&\frac{1}{\sqrt{2\pi t^3}}\sum_{n=-\infty}^{\infty}\bigr[(2na+x)\exp\left(-\frac{(2na+x)^2}{2t}\right)\\
&+(2na+a-x)\exp\left(-\frac{(2na+a-x)^2}{2t}\right)\bigr]dt
\end{align}
$$
```
**Proof**
By [[#^2932ef|the transition density]], we have 
$$
\begin{align}
\mathbb{P}^x[T_0\wedge T_a>t]&=\mathbb{P}^x[T_0\wedge T_a>t,W_t\le y]+\mathbb{P}^x[T_0\wedge T_a>t,W_t> y]\\
&=\frac{1}{\sqrt{2\pi t}}\sum_{n=-\infty}^{\infty}\left[\int_{0}^{y}p_-(t;x,u+2na){d}u+\int_{y}^{a}p_-(t;x,u+2na){d}u\right]\\
&=\frac{1}{\sqrt{2\pi t}}\sum_{n=-\infty}^{\infty}\left[\int_{0}^{a}p_-(t;x,u+2na){d}u\right]\\
&=\frac{1}{\sqrt{2\pi t}}\sum_{n=-\infty}^{\infty}\left[\int_{0}^{a}e^{-\frac{(x-(u+2na))^2}{2t}}-e^{-\frac{(x+u-2na)^2}{2t}}{d}u\right]
\end{align}
$$
By changes of variable, $v=\frac{x-u-2na}{\sqrt{2t}}$ and $v=\frac{x+u-2na}{\sqrt{2t}}$, we obtain
$$
\mathbb{P}^x[T_0\wedge T_a>t]=\frac{1}{\sqrt{\pi}}\sum_{n=-\infty}^{\infty}\left[\int_{\frac{2na-x}{\sqrt{2t}}}^{\frac{2na+a-x}{\sqrt{2t}}}e^{-v^2}{d}v-\int_{\frac{x-2na}{\sqrt{2t}}}^{\frac{x+a-2na}{\sqrt{2t}}}e^{-v^2}{d}v\right]
$$
Differentiation of $t$ leads to
$$
\begin{align}
\mathbb{P}^x[T_0\wedge T_a\in dt]&=-\frac{d}{dt}\mathbb{P}^x[T_0\wedge T_a>t]\\
&=-\frac{1}{2\sqrt{2\pi t^3}}\sum_{n=-\infty}^{\infty}\left[(2na+a-x)e^{-\frac{(2na+a-x)^2}{2t}}-(2na-x)e^{-\frac{(2na-x)^2}{2t}}\right]\\
&+\frac{1}{2\sqrt{2\pi t^3}}\sum_{n=-\infty}^{\infty}\left[(x+a-2na)e^{-\frac{(x+a-2na)^2}{2t}}-(x-2na)e^{-\frac{(2na-x)^2}{2t}}\right]{d}t\\
&=\frac{1}{\sqrt{2\pi t^3}}\sum_{n=-\infty}^{\infty}\bigr[(2na+x)\exp\left(-\frac{(2na+x)^2}{2t}\right)\\
&+(2na+a-x)\exp\left(-\frac{(2na+a-x)^2}{2t}\right)\bigr]dt
\end{align}
$$
**QED**
```ad-warning
We guess the decomposition,
$$
\mathbb{P}^0[T_0\in dt,T_0<T_a]=\frac{1}{\sqrt{2\pi t^3}}\sum_{n=-\infty}^{\infty}\left[(2na+x)\exp\left(-\frac{(2na+x)^2}{2t}\right)\right]
$$
$$
\mathbb{P}^0[T_a\in dt,T_a<T_0]=\frac{1}{\sqrt{2\pi t^3}}\sum_{n=-\infty}^{\infty}\left[(2na+a-x)\exp\left(-\frac{(2na+a-x)^2}{2t}\right)\right]
$$
```
# Distributions Involving Last Exit Times
```ad-def
title:Last exit times
We define 
$$
\theta_t=\sup\{0\le s\le t:W_s=M_t\}
$$
Note that $\theta_t$ is not stopping times.
```

```ad-proposition
For $a\in\mathbb{R},b\ge a^+,0<s<t$, we have 
$$
\mathbb{P}^0(W_t\in da,M_t\in db, \theta_t\in ds)=\frac{b(b-a)}{\pi\sqrt{s^3(t-s)^3}}\exp\left(-\frac{b^2}{2s}-\frac{(b-a)^2}{2(t-s)}\right)dadbds
$$
```

^e2a506

```ad-warning
First time attains maximum: $\hat{\theta}_t=\inf\{0\le s\le t:W_s=M_t\}$. $\hat{\theta}_t$ and $\theta_t$ have the same distribution.
```

---
# Exercises
```ad-question
Show that for $t > 0$, $$ P^0[M_t \in db] = P^0[|W_t| \in db] = P^0[M_t - W_t \in db] $$ $$ = \frac{2}{\sqrt{2\pi t}} e^{-b^2/2t} db; \quad b > 0. $$ 
```

^f48608

```ad-done
1. Note that $\{M_t\le b\}=\{T_b\ge t\}$, then 
   $$
   \begin{align}
\mathbb{P}^0(M_t\le b)=\mathbb{P}^0(T_b\ge t)=\int_{\frac{b}{\sqrt{t}}}^{\infty}\sqrt{\frac{2}{\pi}}e^{-\frac{x^2}{2}}{d}x\Longrightarrow\mathbb{P}^0(M_t\in db)=\frac{2}{\sqrt{2\pi t}} e^{-b^2/2t} db
\end{align}
   $$
2. We can calculate the distribution directly.
   $$
   \begin{align}
\mathbb{P}^0(|W_t|\le b)&=\mathbb{P}^0(-b\le W_t\le b)=\mathbb{P}^0(W_t\le b)-\mathbb{P}^0(W_t<-b)\\
&=\frac{2}{\sqrt{2\pi t}}\int_{0}^{b}e^{-\frac{x^2}{2t}}{d}x
\end{align}
   $$
   Differentiation leads to
   $$
   \mathbb{P}^0(|W_t|\in b)=\frac{2}{\sqrt{2\pi t}} e^{-b^2/2t} db
   $$
3. We denote $X=M_t,Y=W_t$, then 
   $$
   \begin{align}
\mathbb{P}^0(X-Y\le b)&=\mathbb{P}^0(X\le b+Y)\\
&=\int_{-\infty}^{\infty}\int_{-\infty}^{b+y}\frac{2(2x-y)}{\sqrt{2\pi t^3}}\exp\left(-\frac{(2x-y)^2}{2t}\right)dxdy
\end{align}
   $$
   Differentiation of $b$ leads to 
   $$
   \begin{align}
\mathbb{P}^0(X-Y\in db)&=\int_{-b}^{\infty}\frac{2(2b+y)}{\sqrt{2\pi t^3}}e^{-\frac{(2b+y)^2}{2t}}{d}y{d}b=\frac{2}{\sqrt{2\pi t}}\int_{\frac{b}{\sqrt{t}}}^{\infty}ue^{-\frac{u^2}{2}}{d}u{d}b\\
&=\frac{2}{\sqrt{2\pi t}} e^{-b^2/2t} db
\end{align}
   $$
```

```ad-question
Derive (8.6) (and consequently (8.5)) by applying the optional sampling theorem to the $\{\mathscr{F}_t\}$-martingale $$ X_t = \exp\left\{\lambda W_t - \frac{1}{2}\lambda^2 t\right\}; \quad 0 \leq t < \infty, $$ with $\lambda = \sqrt{2\alpha} > 0$.
```

```ad-warning
Laplace transform of $T_b$: $\mathbb{E}^0[e^{-\alpha T_b}]=e^{-\sqrt{2\alpha}b}$.
```

```ad-done
Since $\lambda=\sqrt{2\alpha}$, then $X_t=\exp\left\{\sqrt{2\alpha}W_t-\alpha t\right\}$. Let $t=T_b$, we have 
$$
\begin{align}
X_{T_b}=\exp(\sqrt{2\alpha}b)\cdot\exp(-\alpha T_b)
\end{align}
$$
By [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], 
$$
\mathbb{E}^0[\exp(-\alpha T_b)]=\exp(-\sqrt{2\alpha}b)\mathbb{E}^0[X_{T_b}]=\exp(-\sqrt{2\alpha}b)\mathbb{E}^0[X_{0}]=\exp(-\sqrt{2\alpha}b)
$$
```

```ad-question
Derive the formulas
$$ E^x[e^{-\alpha T_0} 1_{\{T_0 < T_a\}}] = \frac{\sinh((a - x)\sqrt{2\alpha})}{\sinh(a\sqrt{2\alpha})}, $$ $$ E^x[e^{-\alpha T_a} 1_{\{T_a < T_0\}}] = \frac{\sinh(x\sqrt{2\alpha})}{\sinh(a\sqrt{2\alpha})}. $$
by applying the optional sampling theorem to the martingale of $X_t$.
```

```ad-done
Consider the martingale $X_t=\exp\left\{\sqrt{2\alpha} W_t - \alpha t\right\}$ and $Y_t=\exp\left\{-\sqrt{2\alpha} W_t - \alpha t\right\}$. By [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], 
$$
\mathbb{E}^x[X_{T_0\wedge T_a}]=\mathbb{E}^x[X_0]=e^{\sqrt{2\alpha}x},\mathbb{E}^x[Y_{T_0\wedge T_a}]=\mathbb{E}^x[Y_0]=e^{-\sqrt{2\alpha}x}
$$
We decomposite the expectation by $\mathbb{1}_{\{T_0<T_a\}}$ and $\mathbb{1}_{\{T_a<T_0\}}$,
$$
\mathbb{E}^x[X_{T_0}\mathbb{1}_{\{T_0<T_a\}}]+\mathbb{E}^x[X_{T_a}\mathbb{1}_{\{T_a<T_0\}}]=e^{\sqrt{2\alpha}x}
$$
$$
\mathbb{E}^x[Y_{T_0}\mathbb{1}_{\{T_0<T_a\}}]+\mathbb{E}^x[Y_{T_a}\mathbb{1}_{\{T_a<T_0\}}]=e^{-\sqrt{2\alpha}x}
$$
Then we have the equations
$$
\begin{cases}
\mathbb{E}^x[e^{-\alpha T_0}\mathbb{1}_{\{T_0<T_a\}}]+e^{\sqrt{2\alpha}a}\mathbb{E}^x[e^{-\alpha T_a}\mathbb{1}_{\{T_a<T_0\}}]=e^{\sqrt{2\alpha}x}\\
\mathbb{E}^x[e^{-\alpha T_0}\mathbb{1}_{\{T_0<T_a\}}]+e^{-\sqrt{2\alpha}a}\mathbb{E}^x[e^{-\alpha T_a}\mathbb{1}_{\{T_a<T_0\}}]=e^{-\sqrt{2\alpha}x}
\end{cases}
$$
Solution leads to
$$
\begin{align}
\begin{cases}
\mathbb{E}^x[e^{-\alpha T_0}]=\frac{e^{\sqrt{2\alpha}(a-x)}-e^{-\sqrt{2\alpha}(a-x)}}{e^{\sqrt{2\alpha}a}-e^{-\sqrt{2\alpha}a}}=\frac{\sinh(\sqrt{2\alpha}(a-x))}{\sinh(\sqrt{2\alpha}a)}\\
\mathbb{E}^x[e^{-\alpha T_a}]=\frac{e^{\sqrt{2\alpha}x}-e^{-\sqrt{2\alpha}x}}{e^{\sqrt{2\alpha}a}-e^{-\sqrt{2\alpha}a}}=\frac{\sinh(\sqrt{2\alpha}x)}{\sinh(\sqrt{2\alpha}a)}
\end{cases}
\end{align}
$$
```

```ad-question
Show that for $a > 0, 0 \leq x \leq a$: $$ P^x[T_0 < T_a] = \frac{a - x}{a}, \quad P^x[T_a < T_0] = \frac{x}{a}. $$
```

```ad-done
Consider the Brownian motion $B_t$, by [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], 
$$
x=\mathbb{E}^x[B_{T_a\wedge T_a}]=0\mathbb{P}^x[T_0<T_a]+a\mathbb{P}^x[T_a<T_0]\Longrightarrow\mathbb{P}^x[T_a<T_0]=\frac{x}{a}
$$
```

```ad-question
Show that $E^x(T_0 \wedge T_a) = x(a - x); \quad 0 \leq x \leq a$.
```

```ad-done
Consider the martingale $B_t^2-t$, by [[Continuous-Time Martingales#^1b13f7|optional sampling theorem]], 
$$
x^2=\mathbb{E}^x[B_{T_0\wedge T_a}^2-T_0\wedge T_a]\Longrightarrow\mathbb{E}^x[T_0\wedge T_a]=0\frac{a-x}{a}+\frac{x}{a}a^2-x^2=x(a-x)
$$
```

```ad-question
Show that the doubly reflected Brownian motion $\{\varphi(W_t), \mathscr{F}_t; 0 \leq t < \infty\}$ satisfies $$ P^x[\varphi(W_t) \in dy] = \sum_{n=-\infty}^\infty p_+(t; x, y + 2na) dy; \quad 0 < y < a, 0 < x < a, t > 0. $$
```

```ad-done
Note that for $y\in(0,a)$, $\varphi^{-1}(y)=\bigcup_{n\in\mathbb{Z}}\{y+2na,-y+2na\}$, then 
$$
\begin{align}
\mathbb{P}^x[\varphi(W_t)\in dy]&=\mathbb{P}^x[W_t\in \varphi^{-1}(dy)]\\
&=\sum_{n=-\infty}^{\infty}\left[p(t;x,y+2na)+p(t;x,-y+2na)\right]{d}y\\
&=\sum_{n=-\infty}^{\infty}p_+(t,x,y+2na){d}y
\end{align}
$$
```

```ad-question
Show that for $b \geq 0, 0 < s < t$: $$ P^0[M_t \in db, \theta_t \in ds] = \frac{b}{\pi \sqrt{s^3(t-s)}} e^{-b^2/2s} db ds, $$ whence $$ P^0[\theta_t \in ds] = \frac{ds}{\pi \sqrt{s(t-s)}}, \quad P^0[M_t \in db \mid \theta_t = s] = \frac{b}{s} e^{-b^2/2s} db. $$ In particular, the conditional density of $M_t$ given $\theta_t$ does not depend on $t$. We say that $\theta_t$ obeys the *arc-sine law*, since $$ P^0[\theta_t \leq s] = \frac{2}{\pi} \arcsin \sqrt{\frac{s}{t}}; \quad 0 \leq s \leq t, t > 0. $$ 
```

```ad-done
 Integrating of $a$ in [[#^e2a506|density of the proposition]], we have 
 $$
\mathbb{P}^0[M_t \in db, \theta_t \in ds] = \frac{b}{\pi \sqrt{s^3(t-s)}} e^{-b^2/2s} db ds
 $$
 Integrating of $b$ again, 
 $$
\mathbb{P}^0[\theta_t \in ds] = \frac{ds}{\pi \sqrt{s(t-s)}}
 $$
Last
$$
\mathbb{P}^0(M_t\in db|\theta_t=s)=\frac{\mathbb{P}^0(M_t\in db, \theta_t=s)}{\mathbb{P}^0(\theta_t=s)}=\frac{\frac{b}{\pi \sqrt{s^3(t-s)}} e^{-b^2/2s} db ds}{\frac{ds}{\pi \sqrt{s(t-s)}}}=\frac{b}{s} e^{-b^2/2s} db
$$
```

```ad-question
Define the time of last exit from the origin before $t$ by $$ \gamma_t \triangleq \sup\{0 \leq s \leq t; W_s = 0\}. $$ Show that $\gamma_t$ obeys the arc-sine law; i.e., $$ P^0[\gamma_t \in ds] = \frac{ds}{\pi \sqrt{s(t-s)}}; \quad 0 < s < t. $$
```

```ad-done
Note that $Y_t$ and $|W_t|$ have the same distribution.  
$$
\begin{align}
\gamma_t&=\sup\{0 \leq s \leq t: W_s = 0\}=\sup\{0 \leq s \leq t: |W_s| = 0\}\\
&=\sup\{0 \leq s \leq t: Y_s = M_t\}=\theta_t
\end{align}
$$
Hence, $\mathbb{P}^0(\gamma_t\in ds)=\mathbb{P}^0(\theta_t\in ds)$.
```

```ad-question
With $\gamma_t$ defined as above, derive the quadrivariate density 
$$
\begin{align}
&P^0[W_t \in da, M_t \in db, \gamma_t \in ds, \theta_t \in du] \\
= &\frac{-2ab^2}{(2\pi u(s-u)(t-s))^{3/2}} \exp\left\{-\frac{ub^2}{2u(s-u)} - \frac{a^2}{2(t-s)}\right\} da db ds du
\end{align} 
$$ 
$$ 0 < u < s < t, a < 0 < b. $$
```

```ad-done

```