##  Exercise 4.1

For the trade direction indicator $q_t$ in the Roll model, Madhavan, Richardson, and Roomans (1997) allow for serial dependence. Suppose that $q_t \in \{-1, +1\}$, and that

$$
\begin{aligned}
\Pr(q_{t+1} &= +1 \mid q_t = +1)=\Pr(q_{t+1} = -1 \mid q_t = -1)= \alpha \\
\Pr(q_{t+1} &= +1 \mid q_t = -1)=\Pr(q_{t+1} = -1 \mid q_t = +1)= 1 - \alpha.
\end{aligned}
$$

$\alpha$ is called the **continuation probability**.  

- If $\alpha = \tfrac12$, trade directions are uncorrelated.  
- If $\tfrac12 < \alpha < 1$, trade directions are persistent (buys tend to follow buys, etc.).

With this structure, $q_t$ may be expressed as the AR(1) process

$$
q_t = \phi\,q_{t-1} + v_t
$$

where $\mathbb{E}[v_t] = 0$, $\mathbb{E}[v_t^2] = \sigma_v^2$, and $\mathbb{E}[v_t\,v_{t-k}] = 0$ for $k \neq 0$.  The model may be analyzed by constructing a table of the eight possible realizations (paths) of $(q_t, q_{t+1}, q_{t+2})$.

---

### Problem (a) 

Assuming that $q_t$ is equally likely to be $\pm1$, compute the probabilities of each path.  Show that

$$
\phi = 2\alpha - 1.
$$

---

### Problem (b)

Compute $v_{t+1}$ and $v_{t+2}$.  Verify that

$$
\mathbb{E}[v_{t+1}] = \mathbb{E}[v_{t+2}] = 0
\quad\text{and}\quad
\mathrm{Cov}(v_{t+1}, v_{t+2}) = \mathbb{E}[v_{t+1}v_{t+2}] = 0.
$$

---

### Problem (c)

Demonstrate that the $v_t$ values are **not** serially independent by verifying that

$$
\mathrm{Cov}\bigl(v_{t+1},\,v_{t+2}^2\bigr) \;\neq\; 0.
$$

##  Exercise 4.1 -- Solution

### Problem (a)

The model can be expressed as:

$$
q_t = \phi\,q_{t-1} + v_t.
$$

From the continuation probability, we can have the expectation:

$$
\begin{aligned}
\mathbb{E}[q_t \mid q_{t-1}]
&= \alpha\,q_{t-1} - (1-\alpha)\,q_{t-1} \\[6pt]
&= (2\alpha-1)\,q_{t-1} \\[6pt]
&= \phi \, q_{t-1}
\end{aligned}
$$  

Therefore, we have:
$$
\mathbb{E}[q_t]
=\mathbb{E}\bigl[\mathbb{E}[q_t\mid q_{t-1}]\bigr]
=\phi\,\mathbb{E}[q_{t-1}].
$$

### Problem (b)

We have:

$$
v_{t+1}=q_{t+1}-\phi \,q_t.
$$


Condition $v_{t+1}$ on $q_t$:

$$
\mathbb{E}[v_{t+1}\mid q_t]
=\mathbb{E}[q_{t+1}\mid q_t]-\phi\,q_t
=\phi\,q_t-\phi\,q_t
=0.
$$

The unconditional expectation is 

$$
\mathbb{E}[v_{t+1}]
=\mathbb{E}\bigl[\mathbb{E}[v_{t+1}\mid q_t]\bigr]
=\mathbb{E}[0]=0.
$$

For the covariance, we need to calculate:

$$
\mathrm{Cov}(v_{t+1},v_{t+2})
=E\bigl[v_{t+1}\,v_{t+2}\bigr]
=E\Bigl[(q_{t+1}-\phi q_t)(q_{t+2}-\phi q_{t+1})\Bigr].
$$

We have $\mathbb{E}[q_i^2]=0$ since $q_i \in \{-1, 1\}$. Using continuation probability, we can prove that $\mathbb{E}[q_tq_{t-1}]=\phi$. This leads to $\mathrm{Cov}(v_{t+1},v_{t+2})=0$.

### Problem (c)

**Notation.**

- Let $q = q_t$  
- Let $q_1 = q_{t+1}$  
- Let $q_2 = q_{t+2}$  
- Let $v_1 = v_{t+1} = q_1 - \phi\,q$  

---

**Derivation**

$$
\begin{aligned}
\mathbb{E}\bigl[v_{t+1}\,v_{t+2}^2\bigr]
&= \mathbb{E}\Bigl[v_1\,\bigl(q_2^2 - 2\phi\,q_1q_2 + q_1^2\bigr)\Bigr] \\[6pt]
&= -2\phi\,\mathbb{E}\bigl[q_1q_2\,v_1\bigr] \\[6pt]
&= -2\phi\,\mathbb{E}\bigl[q_1q_2\,(q_1 - \phi\,q)\bigr].
\end{aligned}
$$

---

**Intermediate simplifications**

1. Since $q_1^2 = 1$,
$$
\mathbb{E}[q_1^2\,q_2] = \mathbb{E}[q_2].
$$

1. Using the Markov property and conditioning on $q$,

$$
\begin{aligned}
\mathbb{E}[q\,q_1q_2]
&= \mathbb{E}\bigl[q \,\mathbb{E}[q_1q_2\mid q]\bigr] \\[6pt]
&= \mathbb{E}\bigl[q \,\phi\bigr] \quad\bigl(\text{since }\mathbb{E}[q_1q_2\mid q]=\phi\bigr) \\[6pt]
&= \phi\,\mathbb{E}[q]. \\[6pt]
\end{aligned}
$$

This indicates that a serial dependence exists between them.