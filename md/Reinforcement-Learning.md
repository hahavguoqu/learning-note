

Episodic Task（情节任务） -> Continuing Task（持续任务）



## Bellman Equation:

#### bootstrapping（自举法）：

用已有的价值估计来更新当前的价值估计。
$$
V(s_t)~\leftarrow~V(s_t)+\alpha\left(\underbrace{Target_t}_\text{学习目标}-V(s_t)\right)
$$


其中**Target** 就是对状态价值的估计目标



#### State Value（状态价值）:

在某个状态下，按照策略$\pi$











