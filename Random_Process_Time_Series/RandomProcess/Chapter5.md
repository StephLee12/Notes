- [Random Process](#random-process)
  - [Chapter 5 平稳随机过程](#chapter-5-%e5%b9%b3%e7%a8%b3%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b)
    - [5.1 平稳随机过程的概念](#51-%e5%b9%b3%e7%a8%b3%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e6%a6%82%e5%bf%b5)
    - [5.2 平稳过程的自相关函数](#52-%e5%b9%b3%e7%a8%b3%e8%bf%87%e7%a8%8b%e7%9a%84%e8%87%aa%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0)
    - [5.3 平稳过程的各态历经性](#53-%e5%b9%b3%e7%a8%b3%e8%bf%87%e7%a8%8b%e7%9a%84%e5%90%84%e6%80%81%e5%8e%86%e7%bb%8f%e6%80%a7)

# Random Process

## Chapter 5 平稳随机过程

### 5.1 平稳随机过程的概念

1. 严平稳过程

    👉 定义：
    $$
        X(t)是实随机过程，若对n>1,t_1,t_2,\cdots,t_n \in T和\tau \in R,当t_1 + \tau,t_2 + \tau ,\cdots,t_n+\tau \in T时\\
        (X(t_1),\cdots,X(t_n))与(X(t_1+\tau),\cdots,X(t_n+\tau))有相同的联合分布函数，称X(t)时严(强、狭义)平稳过程
    $$

    👉 注意：

    严平稳过程描述的物理系统的**概率特征**不随时间的推移而改变

    严平稳过程的**一维分布与时间无关**，**二维分布仅与时间间隔有关**，与时间起点无关

2. 宽平稳过程

    👉 定义：
    $$
        设X(t)是二阶矩过程，若\\
        \forall t\in T, m_X(t) = m_X(常数) \\
        \forall s,t\in T,R_X(s,t) = R_X(t-s)=R_X(\tau) i.e\quad 自相关函数只t-s相关\\
        称X(t)是宽(弱、广义)平稳过程，简称平稳过程
    $$

### 5.2 平稳过程的自相关函数

1. 自相关函数的性质

    $$
        R(0) = E[X^2(t)] \geq 0 \\
        \mid R_X(\tau) \mid \leq R_X(0)\\
        R_X(-\tau) = R_X(\tau)\\
        \text{非负定性}
    $$

    $$
        若X(t)是以L为周期的平稳过程，即P\{X(t+L)=X(t)\}=1\\
        \Rightarrow R_X(\tau)也是周期函数，周期也为L
    $$

2. 实平稳过程均方连续充要条件

    $$
        自相关函数R_X(\tau)在\tau = 0处连续，且此时R_X(\tau)处处连续\\
        i.e. \quad 证明时证明在\tau=0处左连续，右连续且收敛到R_X(0)
    $$

3. 平稳过程均方可微的充要条件

    $$
        R_X(\tau)在\tau =0处一阶导数存在，二阶导数存在\\
        即\lim_{\Delta \tau \rightarrow 0^{-}} \frac{R(0+\Delta \tau) - R(0)}{\Delta \tau} = \lim_{\Delta \tau \rightarrow 0^{+}} \frac{R(0+\Delta \tau) - R(0)}{\Delta \tau}\\
        \Leftrightarrow R(0+0) = R(0-0)\\
        二阶导同样有\quad R^{'}(0+0) = R^{'}(0-0)
    $$

    $$
        若X_T均方可微，其均方导数过程仍是平稳过程，且有\\
        \begin{aligned}
            均值函数\quad m_{X^{'}}(t) &= 0 \\
            自相关函数\quad R_{X^{'}}(\tau) = -R_X^{''}(\tau)
        \end{aligned}
    $$

    👉**突然领悟**：自相关函数是用来描述一个随机过程在**两个时间点上对应的随机变量**的相关程度，平稳过程中的自相关函数，如果这两个时间点的**间隔**相同，则函数值相同。牢记这个公式
    $$
        R_X(s,t) = E[X(s)X(t)] = R_X(t-s) = R(\tau)
    $$

    👉推论1
    $$
        若X(t)是均方可微的实平稳过程，则\,\forall t \in T, X(t)与X^{'}(t)不相关
    $$
    👉推论2
    $$
        若X(t)是均方可微的实正态平稳过程，则则\,\forall t \in T, X(t)与X^{'}(t)相互独立 \quad i.e.\quad 对于正态分布，不相关\Leftrightarrow独立
    $$

4. 平稳过程的均方积分

    $$
        对于实平稳过程X(t)\\
        E[\int_a^b X(t) dt] = m_X(b-a)\\
        E[\int_a^b X(t)dt]^2 = 2\int_0^{b-a} [(b-a)-\mid \tau \mid] R(\tau) d\tau
    $$

### 5.3 平稳过程的各态历经性

👉 主要思想：用**一条样本函数**去估计随机过程的数字特征。用时间平均去代替统计平均

1. 平稳过程的时间平均和时间相关函数

    👉时间平均
    $$
        <X(t)> = l.i.m_{T \rightarrow \infty} \frac{1}{2T} \int_{-T}^T X(t)dt
    $$
    👉时间相关函数
    $$
        对于固定的\tau \\
        <X(t)X(t+\tau)> = l.i.m_{T \rightarrow \infty} \frac{1}{2T} \int_{-T}^T X(t)X(t+\tau)dt
    $$

    👉注意

    ① 保证$\,X(t)\,$在任意有限区间上均方可积

    ② 时间平均是随机变量,时间相关函数是随机过程(参数是$\,\tau\,$)

2. 平稳过程的各态历经性

    👉均值的各态历经性
    $$
        P\{<X(t)> = m_X\} = 1，称X(t)的均值具有各态历经性(均方遍历性)
    $$
    👉相关函数的各态历经性
    $$
        \forall \tau, P\{<X(t)X(t+\tau)> = R_X(\tau)\} = 1,称X(t)相关函数有各态历经性
    $$
    称均值和相关函数都具有各态历经性的平稳过程为各态历经过程

    👉一个随机过程具备各态历经性，可以通过研究它的一条样本函数来获得过程的全部信息

3. 均值各态历经性定理

    $$
        若实随机过程X(t)是平稳过程，则其均值各态历经的充要条件是\\
        \lim_{T \rightarrow \infty} \frac{1}{T} \int_0^{2T} (1-\frac{\tau}{2T}) C_X(\tau) d\tau = 0
    $$

    👉推论
    $$
        若\int_{-\infty}^{+\infty} \mid C_X(\tau) \mid d\tau < \infty，则实平稳过程的均值各态历经 \\
        若相关函数满足\lim_{\tau \rightarrow \infty} R_X(\tau) = m_X^2,则实平稳过程的均值各态历经
    $$

4. 相关函数各态历经性定理

    $$
        X(t)是均方连续的平稳过程，且对固定的\tau,X(t)X(t+\tau)也是均方连续的平稳过程，则X(t)的相关函数各态历经的充要条件是\\
        \lim_{T \rightarrow \infty} \frac{1}{T} \int_{-2T}^{2T} (1-\frac{\mu}{2T}) [B(\mu) - R_X^2(\tau)] d\mu = 0\\
        其中B(\mu) = E[X(t)X(t+\tau)X(t+\mu)X(t+\tau+\mu)]
    $$
