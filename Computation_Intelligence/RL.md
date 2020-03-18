# Reinforcement Learning

## Policy Gradient

### Basic Components

Agent——需要make policy

环境和Reward Function——都是已经设定好的，不能修改

Policy(通常用$\,\pi\,$表示)是一个含参$\,\theta\,$的网络

Policy的输入通常是**机器的画面(如游戏某时刻的画面)**，输入是用矩阵的形式输入(将画面抽象为像素)

And the output is **the scores of an action(probability)**, Actor takes the action based on the probability.

Policy的输出是**执行某一动作的概率**，Agent会根据这个概率来做出对应的Action

We define some symbols:

机器的画面$\,\rightarrow\, s_i$

reward $\,\rightarrow r_i\,$

action $\,\rightarrow a_i\,$

### Goal

$\,R = \sum_{i=1}^T r_i\,$，目标是通过调整Policy的参数$\,\theta\,$使$\,R\,$最大化

![Relationship among Actor,Env,Reward](Captures\RL1.PNG "Relationship among Actor,Env,Reward")

每一场游戏都有一个**trajectory**
$$
    \tau = \{ s_1,a_1,s_2,a_2,\cdots,s_T,a_T \}
$$
某一轨迹出现的概率计算如下
$$
    \begin{aligned} &
        p_\theta(\tau)\\ &
        =p(s_1)p_\theta(a_1 \mid s_1)p_(s_2\mid s_1,a_1)p_\theta(a_2,s_2)p(s_3|s_2,a_2) \\ &
        =p(s_1)\prod_{t=1}^T p_\theta(a_t\mid s_t)p(s_{t+1}\mid s_t,a_t)
    \end{aligned}
$$
要注意到$\,R\,$是一个随机变量，因为$\,s_i,a_i\,$具有随机性。若要最大化$\,R\,$，则要最大化$\,R\,$的期望

下面是计算$\,R\,$的期望的梯度(有最大似然估计的思想)
$$
    \begin{aligned} &
        \nabla \,\,\overline{R_\theta} \\
        &= \sum_\tau R(\tau)\nabla p_\theta(\tau) \\
        & =\sum_\tau R(\tau) p_\theta(\tau) \frac{\nabla p_\theta(\tau)}{p_\theta(\tau)} \\
        &= \sum_\tau R(\tau) p_\theta(\tau)  \nabla \log p_\theta(\tau) \\
        &= E_{\tau \sim p_\theta(\tau)} [R(\tau)\nabla\log p_\theta(\tau)] \\
        &\approx \frac{1}{N} \sum_{n=1}^N R(\tau^n)\nabla\log p_\theta(\tau^n) \,\,\text{note that n is index and we need to use sampling to compute} \\
        &= \frac{1}{N} \sum_{n=1}^N \sum_{t=1}^{T_n} R(\tau^n)\nabla
        \log p_\theta(a_t^n \mid s_t^n) \\
        &\text{In the last formula,note that in formula} \,p_\theta(\tau) \text{we cannot control} \,p(s_1) \text{because it's based on the Env so we only need to "gradient" the part with} \,\theta
    \end{aligned}
$$
即要优化的$\,R\,$的期望为(很像最大似然估计，$\,p_\theta\,$像概率密度函数)
$$
    \frac{1}{N} \sum_{n=1}^N \sum_{t=1}^{T_n} R(\tau^n)
        \log p_\theta(a_t^n \mid s_t^n)
$$

**i.e** There is a formula for the above demonstration:
$$
    \nabla f(x) = f(x) \nabla \log f(x)
$$

### Policy Gradient

![Compute Policy Gradient](Captures\RL2.PNG "Compute Policy Gradient")

训练好的Agent，进行数据的采集，带入公式计算之后调整参数得到新的模型，再次进行数据采集，不断调参

### Implementation

考虑为一个**分类(classification)** 的问题

![classfication](Captures/RL3.PNG "classfication")

input是某一state$\,s_t^n,$的界面，output是这个state下对应的action$\,a_t^n\,$,为了优化
$$
    \frac{1}{N} \sum_{n=1}^N \sum_{t=1}^{T_n} R(\tau^n)
        \log p_\theta(a_t^n \mid s_t^n)
$$
即告诉agent当遇到同样的state$\,s_t^n,$时，输出对应的action$\,a_t^n\,$，对应到公式上即为求梯度,即拉高遇到state$\,s_t^n,$时，输出action$\,a_t^n\,$的概率。但注意，reward是**整场游戏的reward**
$$
    \frac{1}{N} \sum_{n=1}^N \sum_{t=1}^{T_n} R(\tau^n)\nabla
        \log p_\theta(a_t^n \mid s_t^n)
$$

但是在Implement时会遇到问题，如下图所示

![baseline](Captures/RL4.PNG "baseline")

一般来说reward都是正的，假设在state$\,s_t^n,$可以执行三个action——a,b,c。所以执行a,b,c的概率都会增加，但是不同的action的reward不同，所以经过normalization之后，reward小的，如图中的b的概率就会下降

但是在**Sampling**时由于数据不能覆盖的全部的可能，可能会出现如action a没有被sampling到，但不能说明action a的reward就很小，但因为没有sampling到，action b和c的概率就会增大，action a的概率就会减小，这样就出现了问题

所以要设置一个**baseline**，当一个action的reward很小的时候，要降低执行此action的概率，引入
$$
    b \approx E[R(\tau)]
$$
所以$\,\nabla \overline{R_\theta}\,$的公式要改写为
$$
    \nabla \overline{R_\theta} \approx
    \frac{1}{N} \sum_{n=1}^N \sum_{t=1}^{T_n} (R(\tau^n)-b)\nabla
        \log p_\theta(a_t^n \mid s_t^n)
$$

此外，每一个state都要乘上同样的reward$\,(R(\tau^n)-b)\,$,这样其实是不公平的，每一个state乘上的reward应该是这个state之后(包括这个state)产生的reward之和，但两个state之间的时间间隔越长，后面的state的reward对该state的影响就会越小，因此还需要乘上一个discount，所以$\,R(\tau^n)\,$应该变为下式
$$
    \sum_{t^{'}}^{T_n} \gamma^{t'-t} r_{t'} ^n, \,\, \gamma < 1
$$
将
$$
    \sum_{t^{'}}^{T_n} \gamma^{t'-t} r_{t'} ^n -b
$$
称为Advantage Function $\,A^\theta(s_t,a_t)\,$,它能够表现出在state$\,s_t\,$，action$\,a_t\,$相较于其他的action有多好，因为减去了一个b，所以它是一个相对值