> [!question] 2.4.1. **Lazy janitor.**
> Suppose the $i$th light bulb burns for an amount of time $X_i$ and then remains burned out for time $Y_i$ before being replaced. Suppose the $X_i, Y_i$ are positive and independent with the $X$'s having distribution $F$ and the $Y$'s having distribution $G$, both of which have finite mean. Let $R_t$ be the amount of time in $[0, t]$ that we have a working light bulb. Show that $R_t/t \to \mathbb{E}X_i/(\mathbb{E}X_i + \mathbb{E}Y_i)$ almost surely.

> [!done]
> We should note the procedure of the problem, 
> $$
> \text{i th bulb works} \xrightarrow{X_i\text{ times }}\text{ burn }\xrightarrow{Y_i \text{wait time}}\text{i+1 th bulb works}
> $$
> Let $T_n$ be the time from 1 th bulb works to n+1 th bulb begin to work. Then 
> $$
> T_n=\sum_{i=1}^{n}X_i+\sum_{i=1}^{n}Y_i
> $$
> Let $R_{T_n}$ be the amout of time in $[0,T_n]$ that we have a working bulb, which is that 
> $$
> R_{T_n}=\sum_{i=1}^{n}X_i\Longrightarrow\text{ by SLLN }\frac{R_{T_n}}{T_n}\xrightarrow{a.s.}\frac{\mathbb{E}X}{\mathbb{E}(X+Y)}
> $$
> For each time $t$, there exists $T-n\le t<T_{n+1}$, we have 
> $$
> \frac{R_{T_n}}{T_n}\frac{T_n}{T_{n+1}}=\frac{R_{T_n}}{T_{n+1}}\le\frac{R_t}{t}\le\frac{R_{T_{n+1}}}{T_n}=\frac{R_{T_{n+1}}}{T_{n+1}}\frac{T_{n+1}}{T_{n}}
> $$
> and 
> $$
> \frac{T_{n+1}}{T_n}=\frac{\frac{n+1}{n}\frac{1}{n+1}\sum_{i=1}^{n+1}(X_i+Y_i)}{\frac{1}{n}\sum_{i=1}^{n}(X_i+Y_i)}\to1
> $$
> Hence, 
> $$
> \frac{R_t}{t}\xrightarrow{a.s.}\frac{\mathbb{E}X}{\mathbb{E}(X+Y)}
> $$

> [!question] 2.4.2.
> Let $X_0 = (1,0)$ and define $X_n \in \mathbf{R}^2$ inductively by declaring that $X_{n+1}$ is chosen at random from the ball of radius $|X_n|$ centered at the origin, i.e., $X_{n+1}/|X_n|$ is uniformly distributed on the ball of radius 1 and independent of $X_1, \dots, X_n$. Prove that $n^{-1} \log |X_n| \to c$ a.s. and compute $c$.

> [!done]
> 

> [!question] 2.4.3. **Investment problem.**(i)
>  We assume that at the beginning of each year you can buy bonds for $\$1$ that are worth $\$ a$ at the end of the year or stocks that are worth a random amount $V \geq 0$. If you always invest a fixed proportion $p$ of your wealth in bonds, then your wealth at the end of year $n+1$ is $W_{n+1} = (ap + (1 - p)V_n)W_n$. Suppose $V_1, V_2, \dots$ are i.i.d. with $\mathbb{E}V_n^2 < \infty$ and $\mathbb{E}(V_n^{-2}) < \infty$.
>   (i) Show that $n^{-1} \log W_n \to c(p)$ a.s.

> [!done]

> [!question] 2.4.3. (ii)
> (ii) Show that $c(p)$ is concave. [Use Theorem A.5.1 in the Appendix to justify differentiating under the expected value.]

> [!done]

> [!question] 2.4.3. (iii)
> (iii) By investigating $c'(0)$ and $c'(1)$, give conditions on $V$ that guarantee that the optimal choice of $p$ is in $(0,1)$.

> [!done]

> [!question] 2.4.3. (iv)
> (iv) Suppose $\mathbb{P}(V = 1) = \mathbb{P}(V = 4) = 1/2$. Find the optimal $p$ as a function of $a$.

> [!done]