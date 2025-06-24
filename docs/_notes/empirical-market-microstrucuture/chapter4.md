# 4.Univariate Time-Series Analysis

### **Motivation**

***Why do we perform Time Series Analysis?***

Time series data often exhibit dependence across observations, which violates the assumptions of independence required by the Law of Large Numbers and the Central Limit Theorem—both of which underpin the asymptotic properties of many estimators. We rely on alternative versions that assume **stationary** and **ergodicity**.

### **4.1 Stationary and Ergodicity**

**Stationary**

- Covariance Stationray:  $Cov(x_t, x_{t-k})=\gamma_k$
- Constant Mean: $Ex_t = \mu$

**Ergodic**

- Local Stochastic Behavior is (possibly in the limit) independent of the starting point.

- Mean Ergodic is defined as:
$$
\frac{1}{T} \sum_{t=1}^T f(X_t) \xrightarrow{a.s.} \mathbb{E}[f(X)]
\quad \text{When } T \to \infty 
$$
where $f$ is any integrable (measurable) function of the process.

- More generally, the statistical properties observed in a sample path converge to the corresponding properties of the underlying distribution. 

Covariance stationary is a necessary but not sufficient condition for ergodicity. If a process has even the most basic statistical structure (such as mean, covariance) that changes over time, its time average certainly cannot converge to a "fixed overall expectation".

**Roll Model**

For the Roll Model, the price itself is neither stationary or ergodic. In contrast, we have the price difference to be zero mean and covariance stationary. $\Delta p$ is independent of $\Delta p_{t-2}$ for $\text{k} \geq 2$, suggesting a price difference is ergodic.

Nonergodicity is introduced when the model has a drift term, recursively defined as $m_t=m_{t-1}+u_t+z$ where z is a zero-mean random variable drawn once at time zero.

### **4.2 Moving Average Models**

We start with a white noise process, where:

$$
E[\varepsilon_t] = 0,\qquad \mathrm{Var}(\varepsilon_t) = \sigma^2_\varepsilon, \qquad \mathrm{Cov}(\varepsilon_t, \varepsilon_s) = 0 \quad\text{for } s \ne t
$$

The moving averagemodel of order one (the MA(1) process) is:

$$
x_t=\varepsilon_t+\theta\varepsilon_{t-1}
$$

Same as $\Delta p_t$ in the Roll model, MA(1) model also has the property that autocovariances are zero beyond lag one. For this instance, the variance and first-order autocovariance are $\gamma_0=(1+\theta^2)\sigma_\epsilon^2, \gamma_1=\theta\sigma_\epsilon^2$, and $\gamma_k=0$ for $k\gt1$.

The general form of MA(*K*) process is:

$$
x_t=\varepsilon_t+\theta_1\varepsilon_{t-1}+ \ldots + \theta_K\varepsilon_{t-K}
$$

It has the property that $\gamma_j=0$ for $j>K$. If $K=\infty$, we arrive at the inifite-order moving average process.

**Roll Model**

From the MA(1) model, we can play around with $\theta$ and $\sigma_\varepsilon^2$ to match the variance and first-order autocovariance of the structural $\Delta p_t$ process. However, this can only ensure the equality of the first two moments. There's no guarantee that Higher-order joint distributions are consistent, especially in Roll model, there two independent sources of randomness: $u_t$ and $q_t$.

However, for economists, $u_t$ and $q_t$ are not observable, while we can model the market dynamics with price difference using price difference only with MA(1). According to Ansley–Spivey–Wrobleski theorem, if the autocovariances beyond lag $K$ are all zero, then the process must be an MA($K$).

From the autocovariances we can compute the moving average parameters.

$$
\theta = \dfrac{\gamma_0-\sqrt{\gamma_0^{2}-4\gamma_1^{2}}}{2\gamma_1},\qquad
\sigma_\varepsilon^{2} = \dfrac{\gamma_0+\sqrt{\gamma_0^{2}-4\gamma_1^{2}}}{2}
$$
We can see that $|\theta|\lt1$, which is invertible. Another set are $\theta^*=1/\theta$ and $\sigma_\varepsilon^{2*}=\theta^2\sigma^2_\varepsilon$. For noninvertible solution, $|\theta^*| \gt1$

### **4.3 Autoregressive Models**

We can rearrange $\Delta p_t=\varepsilon+\theta\varepsilon_{t-1}$ as $\varepsilon_t=\Delta p_t-\theta\varepsilon_{t-1}$. This gives us a backward recursion for $\varepsilon_t$, and evantually leads to:

$$
\Delta p_t = \theta \Delta p_{t-1} - \theta^2 \Delta p_{t-2} + \theta^3 \Delta p_{t-3} + \cdots + \varepsilon_t.
$$

This is the autoregressive form: $\Delta p$ is expressed as a linear function of its own lagged values and the current disturbance. Although the moving average representation is of order one, the autoregressive representationis of infinite order.

The condition $|\theta| \lt 0$ is convergent, indicating the coefficients of the lagged variables $\Delta p_t$ converge to zero. When a convergent autore-gressive representation exists, the moving average representation is said to be invertible.
The condition $|\theta| \lt 0$ thus defines the invertible solution for the MA(1)parameters

