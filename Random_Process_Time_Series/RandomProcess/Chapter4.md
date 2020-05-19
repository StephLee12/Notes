- [Random Process](#random-process)
  - [Chapter 4 均方微积分](#chapter-4-%e5%9d%87%e6%96%b9%e5%be%ae%e7%a7%af%e5%88%86)
    - [4.1 收敛性](#41-%e6%94%b6%e6%95%9b%e6%80%a7)
    - [4.2 二阶矩随机变量空间及均方极限](#42-%e4%ba%8c%e9%98%b6%e7%9f%a9%e9%9a%8f%e6%9c%ba%e5%8f%98%e9%87%8f%e7%a9%ba%e9%97%b4%e5%8f%8a%e5%9d%87%e6%96%b9%e6%9e%81%e9%99%90)
    - [4.3 随机过程的均方极限和均方连续](#43-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9d%87%e6%96%b9%e6%9e%81%e9%99%90%e5%92%8c%e5%9d%87%e6%96%b9%e8%bf%9e%e7%bb%ad)
    - [4.4 随机过程的均方导数](#44-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9d%87%e6%96%b9%e5%af%bc%e6%95%b0)
    - [4.5 随机过程的均方积分](#45-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9d%87%e6%96%b9%e7%a7%af%e5%88%86)

# Random Process

## Chapter 4 均方微积分

极限的核心就是对**距离**的刻画

### 4.1 收敛性

1. 依分布收敛

    随机变量序列$\,\{ X_n\}\,$的分布函数列$\,\{ F_n(x)\}\,$弱收敛于随机变量$\,X\,$的分布函数$\,F(x)\,$,称$\,\{X_n\}\,$**依分布收敛**于$\,X\,$，记为
    $$
        X_n \stackrel{W}{\longrightarrow}X, as \,\,\,n \longrightarrow \infty
    $$

2. 依概率收敛

    设$\,\{ X_n\}\,$是定义在概率空间上的随机变量序列，若对
    $$
        \forall \epsilon > 0, \lim_{n\rightarrow \infty} 
        P\{ \mid X_n -X \mid \geq \epsilon\} = 0
    $$
    称随机变量序列**依概率收敛**于$\,X\,$,记为
    $$
        X_n \stackrel{p}{\longrightarrow} X
    $$

3. 以概率为1收敛(几乎处处收敛)

    设$\,\{ X_n\}\,$是定义在概率空间上的随机变量序列,若
    $$
        P\{ \lim_{n\longrightarrow \infty} X_n = X\} = 1
    $$
    称随机变量序列**以概率为1收敛**于$\,X\,$,记为
    $$
        X_n \stackrel{a.s.}{\longrightarrow} X
    $$

    关于**依概率收敛**和**以概率为1收敛**的区别：

    前者不需要满足$\,\mid X_n(x) - X(x) \mid < \epsilon\,$在$\,x\,$所有取值范围上成立，也就是可能存在某个区间使$\,\mid X_n(x) - X(x) \mid \geq \epsilon\,$成立

    而后者，$\,x\,$只能在**某个值**时，使$\,\mid X_n(x) - X(x) \mid \geq \epsilon\,$成立

4. 均方收敛

    设$\,\{ X_n\}\,$是定义在概率空间上的随机变量序列，且$\,E(\mid X_n \mid^2) < \infty\,$,若
    $$
        \lim_{n\rightarrow \infty} E\{\mid X_n -X \mid^2\} = 0
    $$
    称随机变量序列**均方收敛**于$\,X\,$,记为
    $$
        l.i.m_{n\rightarrow\infty} X_n = X
    $$

5. 几种收敛性的关系

    ![收敛性的关系](..\captures\收敛性的关系.PNG "收敛性的关系")

### 4.2 二阶矩随机变量空间及均方极限

1. 二阶矩随机变量空间的一些概念

    **定义二阶矩随机变量空间**：在概率空间上具有有限二阶矩的随机变量的全体组成的集合
    $$
        H= \{ X \mid E[\mid X \mid^2] < +\infty\}
    $$
    为二阶矩随机变量空间

    在$\,H\,$中称两个随机变量相等$\,X,Y\,$为
    $$
        P\{X=Y\} = 1 \,\,记为X=Y,\,\,a.e.
    $$

    **定理**：$\,H\,$为线性空间，对任意复数$\,a,b,有aX+bY\in H\,$

    **定义范数**
    $$
        \mid\mid X \mid\mid = [E(\mid X\mid^2)]^\frac{1}{2}
    $$
    $\,H\,$构成一个**线性赋范空间**

    **定义距离**：
    $$
        \forall X,Y \in H, 令d(X,Y)=\mid\mid X-Y\mid\mid
    $$
    则$\,d(X,Y)\,$是$\,H\,$中的距离，满足三条性质，将$\,H\,$构成一个距离空间

    ① 非负性
    $$
        d(X,Y) \geq 0 \\
        且有X=Y\,\,a.e. \Leftrightarrow d(X,Y)=0
    $$
    ② 对称性
    $$
        d(X,Y)=d(Y,X)
    $$
    ③ 三角不等式
    $$
        d(X,Z) \leq d(X,Y) + d(X,Z)
    $$

2. 随机变量序列的均方极限

    设$\,X_n,X \in H, n = 1,2,\cdots,\,$,若
    $$
        \lim_{n \rightarrow \infty} d(X_n,X)  = \lim_{n \rightarrow \infty} \mid\mid X_n-X \mid\mid = 0
    $$
    称$\,X_n\,$均方收敛于$\,X\,$,记为
    $$
        l.i.m_{n \rightarrow \infty} X_n = X
    $$
    按照距离的定义，上式等价为
    $$
        \lim_{n \rightarrow \infty} E\{\mid\mid X_n-X\mid\mid^2\} = 0
    $$
    **注意**：均方极限有惟一性

    **定理：柯西收敛准则**：
    $$
        H中随机变量序列\{X_n\}均方收敛的充要条件为 \\
        \lim_{m,n\rightarrow \infty} \mid\mid X_m-X_n \mid\mid = 0
    $$
    称$\,\{X_n\}\,$是均方收敛基本列(柯西列)

    **Ex.1**:

    **题目**：

    判断相互独立的随机变量序列是否均方收敛
    $$
        X_n \sim \begin{bmatrix}
            n & 0 \\
            \frac{1}{n^2} & 1-\frac{1}{n^2}
        \end{bmatrix}
    $$
    i.e：序列的每个分量都服从两点分布

    **求解**：利用柯西收敛准则
    $$
        d^2(X_m,X_n) = \mid\mid X_m-X_n \mid\mid^2 = E(X_m^2-2X_mX_n+X_n^2) \\
        E(X_n^2) = n^2 \times \frac{1}{n^2} = 1 < \infty \Rightarrow X_n \in H \\
        \Rightarrow \mid\mid X_m-X_n \mid\mid^2 = 1 -2\frac{1}{m}\frac{1}{n} + 1 = 2(1-\frac{1}{mn}) \stackrel{m,n\rightarrow \infty}{\rightarrow} 2 \\
        \Rightarrow \{X_n\}不均方收敛
    $$

    **Ex.2**:

    **题目**：

    设$\,\{X_n\}\,$是相互独立同分布随机变量序列，均值为$\,\mu\,$,方差为1，定义
    $$
        Y_n = \frac{1}{n} \sum_{k=1}^{n} X_k
    $$
    证明$\,Y_n\,$均方收敛于$\,\mu\,$

    **证明**：
    $$
        \begin{aligned}
            \mid\mid Y_n - \mu \mid\mid^2 &= E[\mid Y_n -\mu \mid^2]\\
            & = E[(\frac{1}{n}\sum_{k=1}^{n} X_k -\mu)(\frac{1}{n}\sum_{k=1}^{n} X_k -\mu)] \\
            & = \frac{1}{n^2} \sum_{i=1}^{n}\sum_{k=1}^{n} E[(X_i-\mu)(X_k-\mu)]
            & = \frac{1}{n^2} \sum_{i=1}^{n}\sum_{k=1}^{n} Cov(X_i,X_k) \text{   i.e } \{X_n\}是相互独立同分布的随机变量序列,当i\neq k时，Cov(X_i,X_k)=0 \\
            & = \frac{1}{n^2} \sum_{k=1}^{n} D(X_k) = \frac{1}{n} \\
            &\Rightarrow \lim_{n\rightarrow \infty} \mid\mid Y_n - \mu \mid\mid^2 = 0 \\
            & \Rightarrow Y_n均方收敛于\mu
        \end{aligned}
    $$

3. 均方极限的性质

    **定理：线性性质**：
    $$
        l.i.m_{n\rightarrow \infty} X_n = X, l.i.m_{n\rightarrow \infty} Y_n = Y, a,b是复常数,有\\
        l.i.m_{n\rightarrow \infty} (aX_n+bY_n) = aX+bY
    $$

    **定理：数字特征**：
    设$\,l.i.m_{n \rightarrow \infty } X_n  = X,且l.i.m_{n \rightarrow \infty } Y_n = Y\,$，则
    $$
        \lim_{m,n\rightarrow\infty} E(X_mY_n) = E(XY) \\
        \lim_{n\rightarrow\infty} E(X_n) = E(l.i.m_{n\rightarrow \infty } X_n)  =E(X) \quad \text{期望数列收敛}\\
        \lim_{n \rightarrow \infty} E(\mid X_n \mid^2) = E(\mid l.i.m_{n \rightarrow \infty} X_n \mid^2) = E(\mid X \mid^2) \\
        \lim_{n \rightarrow \infty} D(X_n) = D(l.i.m_{n \rightarrow \infty} X_n) = D(X) \quad \text{方差数列收敛}\\
        E(e^{itl.i.m_{n \rightarrow\infty} X_n}) = E(e^{itX})  = \lim_{n \rightarrow \infty} E[e^{itX_n}] \quad \text{特征函数列收敛}
    $$

    **洛易夫均方收敛判别准则**：

    随机变量序列$\,\{ X_n\} \in H\,$均方收敛的充要条件是$\,\lim_{m,n\rightarrow \infty} E(X_mX_n)\,$存在

    此准则的意义是将随机变量均方收敛的问题变为**自相关函数收敛性**问题

### 4.3 随机过程的均方极限和均方连续

1. 二阶矩过程

    过程$\,X_T = \{ X(t), t\in T\}\,$,对$\,\forall t \in T\,$,有
    $$
        E\{\mid X(t) \mid^2\} < +\infty
    $$
    称过程是二阶矩过程。

    **Attention**：

    ① 二阶矩过程的均值函数和协方差函数一定存在

    ② 正态过程是二阶矩过程

2. 二阶矩过程的均方极限

    **定义**

    设过程是二阶矩过程，若
    $$
        \lim_{t \rightarrow t_0} d(X(t),X) = \lim_{t \rightarrow t_0} \mid\mid X(t) -X \mid\mid = 0
    $$
    称$\,X(t)\,$均方收敛于$\,X\,$,记为$\,l.i.m_{t \rightarrow t_0} X(t) = X\,$(很类似于定义函数的极限)

    **洛易夫均方收敛准则**：

    $\,X(t)\,$在$\,t_0\,$处收敛的充要条件是极限$\,\lim_{s,t\rightarrow t_0} E(X(s)X(t))\,$存在

3. 二阶矩过程的均方连续

    **定义**：

    若
    $$
        l.i.m_{t \rightarrow t_0} X(t) = X(t_0)
    $$
    称二阶矩过程在$\,t_0\,$处均方连续

    若对$\,\forall t \in T\,$都均方连续，则称过程是均方连续的

    **均方连续准则**：

    二阶矩过程在$\,t_0\,$处连续的充要条件是$\,\{X(t),t\in T\}\,$的相关函数$\,R(s,t)\,$在$\,(t_0,t_0)\,$处连续

    **重要结论**：

    二阶矩过程的均方连续相关函数$\,R(s,t)\,$在对角线上连续

    二阶矩过程的相关函数对$\,\forall t \in T\,$，在$\,(t,t)\,$处连续，则它在$\,T\times T\,$上连续

    二阶矩过程均方连续$\,\Rightarrow\,$其均值函数，方差函数均方连续

### 4.4 随机过程的均方导数

1. 均方导数概念

    **定义**：

    二阶矩过程，对确定的$\,t \in T\,$,若存在$\,Y \in H\,$,使得
    $$
        l.i.m_{\Delta t \rightarrow 0}
        \frac{X(t+ \Delta t)- X(t)}{\Delta t} = Y
    $$
    称$\,X(t)\,$在$\,t\,$处均方可微，$\,Y\,$是$\,X(t)\,$在$\,t\,$处的均方导数

    若对$\,\forall t \in T\,$，$\,X(t)\,$都均方可微，则称该过程为均方可微过程

    可以证明，均方可微过程仍是二阶矩过程

2. 广义二阶导数

    若
    $$
        \lim_{\Delta s \rightarrow 0, \Delta t \rightarrow 0}
         \frac{f(s+\Delta s ,t + \Delta t) - f(s+\Delta s , t) - f(s,t+\Delta t) + f(s,t)}
         {\Delta t \Delta s}
    $$
    称此极限为函数$\,f(s,t)在(s,t)的广义二阶导数\,$，称此函数在$\,(s,t)\,$处广义二阶可微

    **引理**：

    若二元函数$\,f(s,t)\,$的一阶偏导存在，二阶混合偏导存在并连续，则$\,f(s,t)\,$一定是**广义二阶可微**的，且有
    $$
        f_{st}^{''}(s,t) = f_{ts}^{''}(s,t)
    $$

    👉引理和定义都可以证明一个二元函数广义二阶可微

3. 均方可微准则

    二阶矩过程在$\,t_0\,$处均方可微的充要条件是其相关函数在$\,(t_0，t_0)\,$处广义二阶可微

    **推论**：

    若二阶矩过程的相关函数在$\,T\times T\,$的对角线上广义二阶可微，则
    $$
        R_{s}^{'}(s,t),R_{t}^{'}(s,t),R_{st}^{''}(s,t),R_{ts}^{''}(s,t)在T\times T上均存在 \\
    $$
    且对于导数过程$\,\{X^{'}(t),t \in T\}\,$,有
    $$
        m_{X^{'}}(t) = m_X^{'}(t) \\
        R_{X^{'}}(s,t) = R_{st}^{''}(s,t) = R_{ts}^{''}(s,t)\\
        R_{X^{'}X}(s,t) = R_{s}^{'}(s,t) \\
        R_{XX^{'}}(s,t)  = R_{t}^{'}(s,t)
    $$
    将关于导数过程的计算转换到**原过程**

4. 均方导数基本性质

    ① 均方可微必均方连续，其逆不真

    ② 均方导数在**概率为1**的意义下惟一
    $$
        若\quad X^{'}(t) = Y_1(t), X^{'}(t) = Y_2(t) \\
        则\quad Y_1(t) = Y_2(t) \quad (a.e)
    $$

    ③ 均方导数具有线性性
    $$
        X(t),Y(t)均方可微，则\{aX(t)+bY(t),t\in T\},a,b\in C,也均方可微，且\\
        [aX(t)+bY(t)]^{'} = aX^{'}(t) + bY^{'}(t)
    $$

    ④
    $$
        f(t)是定义在T上的普通可微函数，\{X(t)\}是均方可微过程，则\{f(t)X(t)\}也是可微过程，有\\
        [f(t)X(t)]^{'} = f^{'}(t)X(t) + f(t)X^{'}(t)
    $$

    ⑤
    $$
        X(t)是均方可微过程，且X^{'}(t) = 0,则X(t)是一个常随机变量(以概率为1)，即与指标t无关的随机变量 \\
        \Leftrightarrow 具有相等均方导数的两个随机过程，它们最多仅相差一个随机变量，即[X(t)+X]^{'} = X^{'}(t)
    $$

### 4.5 随机过程的均方积分

1. 均方积分概念

    **二阶矩过程$\,f(t)X(t)\,$的均方积分定义**:
    $$
        \{X(t),t \in [a,b]\}是二阶矩过程，f(t),t\in [a,b]是普通函数 \\
        \int_{a}^{b} f(t)X(t) dt为二阶矩过程f(t)X(t)在[a,b]上的均方积分 \\
        特别的，若f(t) \equiv 1,则\int_a^b X(t) dt称为随机过程在[a,b]上的积分
    $$

2. 均方积分准则

    二阶矩过程$\,f(t)X(t)\,$在$\,[a,b]\,$上均方可积的充要条件是二重积分
    $$
        \int_a^b \int_a^b f(s)f(t)R(s,t) dsdt\quad 存在
    $$

    在此准则的证明过程中，得出一个公式和两个推论

    **公式**：
    $$
        E[\mid \int_a^b f(t)X(t) dt \mid^2]
        = \int_a^b \int_a^b f(s)f(t)R(s,t) dsdt
    $$
    **推论1**：
    $$
        若二阶矩过程的自相关函数在[a,b] \times [a,b]上可积，则X(t)在[a,b]上均方可积 \\
        E[\mid \int_a^b X(t) dt \mid^2] = \int_a^b \int_a^b R(s,t) dsdt
    $$
    **推论2**：
    $$
        若X(t)在[a,b]上均方连续，则X(t)在[a,b]上均方可积\\
        \begin{aligned}
        &👉证明:\\
        &根据均方连续性准则，X(t)均方连续，R(s,t)在[a,b]\times [a,b]上连续\\
        &\Rightarrow R(s,t)在[a,b]\times[a,b]上可积
        \Rightarrow 由推论1 X(t)在[a,b]上均方可积
        \end{aligned}
    $$

3. 均方积分性质(类似于普通黎曼积分)

    **与普通黎曼积分相似的性质**

    👉**惟一性,线性性，可加性**(与普通黎曼积分一样)

    $$
        若X(t)在[a,b]均方连续，则\\
        \mid \mid \int_a^b X(t)dt \mid\mid
        \leq \int_a^b \mid\mid X(t) \mid\mid dt
    $$

    👉**均方积分的矩**
    $$
        若f(t)X(t)在[a,b]上均方可积，则有\\
        \begin{aligned}
            \quad&👉E[\int_a^b f(t)X(t)dt] = \int_a^b f(t)m_X(t)dt \\
            \quad&👉E[\mid\mid \int_a^b f(t)X(t)dt \mid\mid^2]
            = \int_a^b\int_a^b f(s)f(t)R(s,t)dsdt
        \end{aligned}
    $$

4. 均方不定积分

    👉定义：
    $$
        X(t)在[a,b]上均方连续，Y(t)=\int_a^t X(s)ds \quad \forall t \in [a,b]\\
        Y(t)称为X(t)在[a,b]上的均方不定积分
    $$

    👉性质：
    $$
        X(t)在[a,b]上均方连续，则Y(t)在[a,b]上均方可导，且\\
        \begin{aligned}
            Y^{'}(t) &= X(t) \\
            m_Y(t) &= \int_a^t m_X(s)ds\\
            R_Y(s,t) &= \int_a^s \int_a^t R_X(u,v)dudv
        \end{aligned}
    $$

    👉 牛顿-莱布尼兹公式
    $$
        X(t)在[a,b]上均方可导，X^{'}(t)均方连续，则\\
        \int_a^b X^{'}(t)dt = X(b) -X(a)
    $$

    👉 Ex

    **题目**：
    $$
        设\{W(t),t\geq 0 \}是参数为\sigma^2的维纳过程，求积分过程\\
        X(t)= \int_0^tW(s)ds,\quad t \geq 0 \quad 的均值函数和相关函数
    $$
    **求解**：
    $$
        \begin{aligned}
            m_X(t) &= \int_0^t m_W(s) ds = 0 \\
            R_X(s,t) &= \int_0^s \int_0^t R_W(u,v)dudv \\
                    &= \int_0^s \int_0^t \sigma^2 min(u,v)dudv
        \end{aligned}
    $$
    $R_X(s,t)\,$积分如下图所示，假设$\,s\leq t\,$,将二重积分变化为二次积分

    ![均方不定积分](..\captures\均方不定积分.PNG "均方不定积分")
    $$
        \begin{aligned}
            R_X(s,t) &= \sigma^2 \int_0^s du \int_0^u min(u,v)dv + \sigma^2 \int_0^s du \int_u^t min(u,v)dv\\
            &= \sigma^2 \int_0^s du \int_0^u vdv + \sigma^2 \int_0^s du \int_u^t udv \\
            &= \frac{\sigma^2 s^2}{6}(3t-s)
        \end{aligned}
    $$
    $$
        由s与t的对称性 \\
        R_X(s,t)=
        \begin{cases}
            \frac{\sigma^2 s^2}{6}(3t-s), & 0\leq s \leq t\\
            \frac{\sigma^2 t^2}{6}(3s-s), & 0 \leq t \leq s
        \end{cases}
    $$
    i.e. 维纳过程是均方连续，均方不可导，均方可积的二阶矩过程

5. 正态随机过程的均方微积分

    👉定理1：
    $$
        正态随机变量序列的均方极限仍为正态分布随机变量\\
        即 l.i.m_{n\rightarrow \infty} X_n = X \Rightarrow X是正态随机变量
    $$
    $$
        m维正态随机向量序列的均方极限仍为m维正态随机向量
    $$

    👉定理2：
    $$
        X(t)是一个正态过程，且在T上均方可微，则其导数过程\{X^{'}(t),t\in T\}也是正态过程
    $$

    👉 定理3：
    $$
        若X(t)是均方连续的正态过程，则\\
        Y(t) = \int_a^t X(s)ds,\quad t\in (a,b] \quad也是正态过程
    $$
