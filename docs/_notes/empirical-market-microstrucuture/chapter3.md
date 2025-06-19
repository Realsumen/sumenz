# Roll model

### Motivation
Roll model is a good starting point, focusing on the difference and interaction of quote, trade, and efficient prices.  

### Assumptions

- Price Dynamics: Using random walk (martingale) as the foundation of the efficient price movement dynamics, where the expected price drift $\mu$ is zero, following equation: 

$$m_t = m_{t-1} + u_t,\quad u_t \sim \mathcal{N}(0, \sigma_u^2)$$

- Trading Mechnism: Single market maker, with fixed cost $c$ per trade.
- Trading Direction: Indicator variable $q_t \in \{+1, -1\}$, with same probability and is independent of $u_t$
- Trade Price: $p_t=m_t+cq_t$

### Key Statistical Property

With random walk as the price movement dynamics, we study the price difference $\Delta p_t$. 

We have:

$$
\begin{aligned}
\mathbb{E}[\Delta p_t] &= \mathbb{E}[c(q_t-q_{t-1}) + u_t]=0,\\[1ex]
\mathbb{E}[u_t^2] &= \sigma_u^2,\\[1ex]
\mathbb{E}[q_t^2] &= 1
\end{aligned}
$$

The varaince is:

$$
\begin{align*}
\gamma_0 \equiv  \text{Var}(\Delta p_t) = \mathbb{E}(\Delta p_t)^2 &= \mathbb{E}\bigl[(c(q_t - q_{t-1}) + u_t)^2\bigr]\\[2ex]
\mathbb{E}\bigl[(c(q_t - q_{t-1}) + u_t)^2\bigr]
&= \mathbb{E}\Bigl[c^2 (q_t - q_{t-1})^2 \;+\; 2c\,u_t\,(q_t - q_{t-1}) \;+\; u_t^2\Bigr]\\[1ex]
&= c^2\,\mathbb{E}\bigl(q_t^2 - 2q_tq_{t-1} + q_{t-1}^2\bigr)
  + 2c\,\mathbb{E}[\,u_t\,(q_t - q_{t-1})\,]
  + \mathbb{E}[u_t^2]\\[1ex]
&= c^2\,(1 - 0 + 1) + 0 + \sigma_u^2
= 2c^2 + \sigma_u^2
\end{align*}
$$

The first order covariance is:

$$
\begin{align*}
\gamma_1 \;=\;\mathrm{Cov}(\Delta P_t,\Delta P_{t-1})
&= \mathrm{Cov}\bigl(c(q_t - q_{t-1}) + u_t,\;c(q_{t-1} - q_{t-2}) + u_{t-1}\bigr)\\[1ex]
&= \mathbb{E}[\Delta P_t\,\Delta P_{t-1}]
  - \mathbb{E}[\Delta P_t]\,\mathbb{E}[\Delta P_{t-1}]\\[1ex]
&= \mathbb{E}\bigl[c^2\,(q_t - q_{t-1})(q_{t-1} - q_{t-2})\bigr]\\[1ex]
&= -c^2\,\mathbb{E}[q_{t-1}^2]
= -c^2
\end{align*}
$$
