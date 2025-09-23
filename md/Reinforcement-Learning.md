

Episodic Task（情节任务） -> Continuing Task（持续任务）



## Bellman Equation:

#### bootstrapping（自举法）：

用已有的价值估计来更新当前的价值估计。
$$
V(s_t)~\leftarrow~V(s_t)+\alpha\left(\underbrace{Target_t}_\text{学习目标}-V(s_t)\right)
$$


其中**Target** 就是对状态价值的估计目标



#### State Value（状态价值）:

从状态s出发，按照策略$\pi$行动，未来能期望得到多少奖励。

**公式：**
$$
v_\pi(s)=\mathbb{E}_\pi[G_t\mid S_t=s]
$$
其中：$G_t$表示“实际回报”，而$\mathbb{E}_\pi$具有期望的含义



#### Bellman Equation:

The Bellman equation describes **the ralstionship among the values of all states**.

**First**, calculate the first term $\mathbb{E}[R_{t+1}|S_{t}=s]$:

which denotes *the expected **immediate reward** obtained at the next step given state $s$*:
$$
\begin{aligned}\mathbb{E}[R_{t+1}|S_{t}=s]&=\sum_{a}\pi(a|s)\mathbb{E}[R_{t+1}|S_{t}=s,A_{t}=a]\\&=\sum_{\alpha}\pi(a|s)\sum_{x}p(r|s,a)r\end{aligned}
$$


Where:

- $\pi(a|s)$denotes the probability of taking action $a$ given state $s$.

- $p(r|s,a) $denotes the probability of receiving reward $r$ when taking action $a$ in state s.

**Second**,calculatethe second term $\mathbb{E}[G_{t+1}|S_{t}=s]$:

which denotes *the expected **future return** from the next time step onward given state $s$*
$$
\begin{aligned}\mathbb{E}[G_{t+1}|S_{t}=s]&=\sum_{s^{\prime}}\mathbb{E}[G_{t+1}|S_{t}=s,S_{t+1}=s^{\prime}]p(s^{\prime}|s)\\&=\sum_{s^{\prime}}\mathbb{E}[G_{t+1}|S_{t+1}=s^{\prime}]p(s^{\prime}|s)\\&=\sum_{s^{\prime}}v_{\pi}(s^{\prime})p(s^{\prime}|s)\\&=\sum_{s^{\prime}}v_{\pi}(s^{\prime})\sum_{a}p(s^{\prime}|s,a)\pi(a|s)\end{aligned}
$$
Where:

- $\mathbb{E}[G_{t+1}|S_{t}=s,S_{t+1}=s^{\prime}]$ denotes that, given the system transitions from state $s$ to $s'$ by taking some action, **then** starting from time step $t+1$ in state $s'$, it represents the expected **discounted** sum of all future rewards.  

The relationship between the first equation and the second equation reflects **the Markov property**.

Therefore ,we have **the Bellman eqution**:
$$
\begin{aligned}v_{\pi}(s)&=\mathbb{E}[R_{t+1}|S_{t}=s]+\gamma\mathbb{E}[G_{t+1}|S_{t}=s],\\&=\underbrace{\sum_a\pi(a|s)\sum_rp(r|s,a)r}_\text{mean of future rewards}+\underbrace{\gamma\sum_a\pi(a|s)\sum_{s^{\prime}}p(s'|s,a)v_\pi(s'),}_{\text{mean of future rewards}}\\&=\sum_a\pi(a|s)\left[\sum_rp(r|s,a)r+\gamma\sum_{s^{\prime}}p(s^{\prime}|s,a)v_\pi(s^{\prime})\right],\quad\forall s\in\mathcal{S}.\end{aligned}
$$
Note that:

A set of equations: every state has an equation like this.$\quad\forall s\in\mathcal{S}$

$v_{\pi}(s)$and$v_{\pi}(s^{\prime})$are state values to be calculated via **Bootstrapping**.

**Question:**
 Why do we separate the “**mean of immediate rewards**” and the “**mean of future rewards**” in the Bellman equation? Why not just combine them into one formula?

**Answer:**

- **Distinguish** between immediate rewards and future rewards to reflect **the recursive(递归的) structure** and **bootstrapping**.

- This makes it easier to handle expectations from **different sources separately**.

- It also provides a more intuitive way to show the effect of **the discount factor** $\gamma$ on future rewards.



#### Matrix-vector form of the Bellman Equation:

Suppose the states could be indexed as$s_{i}\left(i=1,\ldots,n\right)$.
For state $S$,the Bellman equation is :
$$
v_\pi(s_i)=r_\pi(s_i)+\gamma\sum_{s_j}p_\pi(s_j|s_i)v_\pi(s_j)
$$
Rewrite to a matrix-vector form:
$$
v_{\pi}=r_{\pi}+\gamma P_{\pi}v_{\pi}
$$
Where:
- $v_{\pi}=[v_{\pi}(s_{1}),\ldots,v_{\pi}(s_{n})]^{T}\in\mathbb{R}^{n}$
- $r_{\pi}=[r_{\pi}(s_{1}),\ldots,r_{\pi}(s_{n})]^{T}\in\mathbb{R}^{n}$
- $P_{\pi}\in\mathbb{R}^{n\times n}$, where $[P_{\pi}]_{ij}=p_{\pi}(s_{j}|s_{i})$,is **the state transition matrix**

For example:
$$
\begin{bmatrix}
v_{\pi}(s_1) \\
v_{\pi}(s_2) \\
v_{\pi}(s_3) \\
v_{\pi}(s_4)
\end{bmatrix}
=
\begin{bmatrix}
r_{\pi}(s_1) \\
r_{\pi}(s_2) \\
r_{\pi}(s_3) \\
r_{\pi}(s_4)
\end{bmatrix}
+
\gamma
\begin{bmatrix}
p_{\pi}(s_1|s_1) & p_{\pi}(s_2|s_1) & p_{\pi}(s_3|s_1) & p_{\pi}(s_4|s_1) \\
p_{\pi}(s_1|s_2) & p_{\pi}(s_2|s_2) & p_{\pi}(s_3|s_2) & p_{\pi}(s_4|s_2) \\
p_{\pi}(s_1|s_3) & p_{\pi}(s_2|s_3) & p_{\pi}(s_3|s_3) & p_{\pi}(s_4|s_3) \\
p_{\pi}(s_1|s_4) & p_{\pi}(s_2|s_4) & p_{\pi}(s_3|s_4) & p_{\pi}(s_4|s_4)
\end{bmatrix}
\begin{bmatrix}
v_{\pi}(s_1) \\
v_{\pi}(s_2) \\
v_{\pi}(s_3) \\
v_{\pi}(s_4)
\end{bmatrix}
$$
***Why** to solve state values $v_\pi(s)$?*
Given a *policy*, finding out the corresponding state values is called **policy evaluation**! It is a fundamental problem in RL. It is the foundation to *find better policies*.





