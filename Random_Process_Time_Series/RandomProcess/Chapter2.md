- [Random Process](#random-process)
  - [Chapter 2 随机过程基础知识](#chapter-2-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e5%9f%ba%e7%a1%80%e7%9f%a5%e8%af%86)
    - [2.1 随机过程的定义及分类](#21-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%ae%9a%e4%b9%89%e5%8f%8a%e5%88%86%e7%b1%bb)
    - [2.2 随机过程的分布](#22-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%88%86%e5%b8%83)
    - [2.3 随机过程的数字特征](#23-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e6%95%b0%e5%ad%97%e7%89%b9%e5%be%81)
    - [2.4 随机过程的基本类型](#24-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9f%ba%e6%9c%ac%e7%b1%bb%e5%9e%8b)

# Random Process

## Chapter 2 随机过程基础知识

### 2.1 随机过程的定义及分类

1. 随机过程定义

    设$\,(\Omega,F,P)\,$是概率空间,$\,T\subset R\,$,若对于每个$\,t\in T\,$,$\,X(t,\omega)\,$是概率空间$\,(\Omega,F,P)\,$上的随机变量，则称随机变量族
    $$\,X(t,\omega),t\in T\,$$

    是$\,(\Omega,F,P)\,$上的一个**随机过程**

    其中

    $\,T\,$是参数集

    当$\, T = \{1,2,\cdots , n\}\,$, $\, \{X(t,\omega),t\in T \} = (X_1,X_2,\cdots,X_n)\,$是一个**随机向量**

    当$\, T = \{1,2,\cdots , n,\cdots\}\,$,$\, \{X(t,\omega),t\in T \} = (X_1,X_2,\cdots)\,$是一个**时间序列**

    当$\, T = \{ (x,y): a < x < b, c < y < d \} \,$,$\, \{X(t,\omega),t\in T \}$是一个平面随机场

    **随机过程是$\,n\,$维随机变量**

    用$\,E\,$表示随机过程$\,X_T=\{X_t,t\in T \}\,$的值域，称$\,E\,$为过程的状态空间

    称$\, T \times \Omega = \{ (t,\omega): t\in T, \omega\in\Omega\,$是集合$\,T\,$与$\,\Omega\,$的积集

    随机过程$\,X(t,\omega)$可以看作定义在积集$\, T \times \Omega$上的二元函数:

    ① 当固定$\,t\in T, X_t(\omega)=X(t,\omega)\,$是一个定义在概率空间的随机变量

    ② 当固定$\,\omega_0 \in \Omega\,$(**对于特定的试验结果**)，$\,x(t,\omega_0)\,$是一个定义在$\,T\,$上的普通函数

    下图是关于随机过程的形象描绘,对于给定的一个$\,t\in T\,$,如$\,t_1\,$，对应的随机变量$\,X(t_1,\omega)\,$称为**截口变量**

    ![随机过程二元函数](..\captures\随机过程定义.PNG "随机过程二元函数")

2. 样本函数定义

    对于每一**固定**$\,\omega \in \Omega\,$,称$\,X_t(\omega)\,$是随机过程$\,X_T=\{X_t,t\in T \}\,$的一个**样本函数**。**注意，一旦开始时间，只有一条样本函数**

### 2.2 随机过程的分布

1. 分布函数定义

    随机过程$\,X_T=\{X_t,t\in T \}\,$对$\,\forall t \in T\,$，**随机变量**$\,X(t)\,$的**分布函数**
    $$\,F(t;x) = P\{ X(t) \leq x \}, x \in R\,$$

    称为**过程**$\,X_T\,$的一维分布函数

    同理 对$\,\forall t_1,t_2,\cdots, t_n \in T\,$，随机向量$\,(X(t_1),X(t_2),\cdots,X(t_n))\,$的**联合分布函数**
    $$\,F(t_1,t_2,\cdots,t_n;x_1,x_2,\cdots,x_n) = P\{X(t_1) \leq x_1,X(t_2) \leq x_2, \cdots , X(t_n) \leq x_n \}\,$$

    称为**过程**$\,X_T\,$的$\,n\,$**维分布函数**

    记
    $$\, F = \{ F(t_1,t_2,\cdots,t_n;x_1,x_2,\cdots,x_n):
          t_i \in T , x_i \in R_i, i=1,2,\cdots,n,n\geq 1 \} \,$$

    为**过程**$\,X_T\,$的**有限维分布函数族** 即随机过程的一维分布，二维分布，...,$\,n\,$维分布etc，其全体称为随机过程的有限维分布函数族

2. 随机过程存在定理

    **随机过程**的有限维分布函数有以下性质

    ① 对称性: 对于$\,1,2,\cdots,n\,$的任一排列$\,j_1,j_2,\cdots,j_n\,$，均有
    $$\,F(t_1,t_2,\cdots,t_n;x_1,x_2,\cdots,x_n) =
         F(t_{j_1},t_{j_2},\cdots,t_{j_n};x_{j_1},x_{j_2},\cdots,x_{j_n})\,$$

    ② 相容性：对任意固定的自然数$\,m < n\,$均有
    $$
    \begin{aligned}
        F(t_1,t_2,\cdots,t_m;x_1,x_2,\cdots,x_m)\\
        & = F(t_1,t_2,\cdots,t_m,\cdots,t_n;x_1,x_2,\cdots,x_m,\infty,\cdots,\infty ) \\
        & = \lim_{x_{m+1},\cdots,x_n \to +\infty} F(t_1,t_2,\cdots,t_n;x_1,\cdots,x_m,\cdots,x_n)
    \end{aligned}
    $$

    对称性可以这样解释：时间具有可追溯性，测量时间改变顺序，不会改变测量结果，即已发生的事无法改变，即使追溯也还是同样的结果

    相容性可以这样解释:**一旦开始某个随机过程的测量，得到了随机过程的一个样本函数，接下来所有的测量都只会观察到该样本，而不会观察到其他样本，也就是说，随机过程的样本在测量上是相互正交的**，像**量子力学里的光波粒二象性，对光进行观测的时候，要么观测到波动性，要么观测到粒子性**

    如果有限维分布函数族满足相容性和对称性，则存在一个概率空间上的一个随机过程$\,X_T\,$,以$\,F\,$为有限维分布函数族

3. Ex.1

    **题目**:

    设随机过程$\,X(t,\omega) , t\in R\,$只有两条样本函数
    $$X(t,\omega_1) = 2cost \, \, X(t,\omega_2) = -2cost$$
    且
    $$P(\omega_1) = \frac{2}{3} \,\,\, P(\omega_2) = \frac{1}{3}$$
    求① 一维分布函数$\,F(0;x)\,$和$\,F(\frac{\pi}{4};x)\,$

    ② 二维分布函数$\,F(0,\frac{\pi}{4};x,y)\,$

    **求解**：

    ① 只有两条样本函数 属于离散型 因此求得分布律 即可求得分布函数
    $$
    \text{对任意实数} t \in R，有
    $$
    $$

        \begin{array}{|c|c|c|}
            \hline
            X(t) & -2cost & 2cost \\
            \hline
            p & 1/3 & 2/3 \\
            \hline
        \end{array}

    $$
    $$
    \text{特别的}
    $$
    $$

        \begin{array}{|c|c|c|}
            \hline
            X(0) & -2 & 2 \\
            \hline
            p & 1/3 & 2/3 \\
            \hline
        \end{array}

    $$
    $$

        \begin{array}{|c|c|c|}
            \hline
            X(\frac{\pi}{4}) & -\sqrt{2} & \sqrt{2} \\
            \hline
            p & 1/3 & 2/3 \\
            \hline
        \end{array}

    $$
    ② 若开始测量，样本函数只有一条，所以在$\,t\,$为$\,0\,$和$\,\frac{\pi}{4}\,$时的截口变量必须在同一条样本函数曲线上,截口变量分别分布在两条曲线上的情况不存在 所以有

    $$
        \begin{array}{|c|c|c|}
            \hline
            (X(0),X(\pi/4)) & (-2,-\sqrt{2}) & (2,\sqrt{2}) \\
            \hline
            p & 1/3 & 2/3 \\
            \hline
        \end{array}
    $$

4. Ex.2(脉冲位置调制信号)

    **题目**

    ① 每个$\,T\,$秒输出宽度为$\,T/6\,$,幅度为$\,A\,$的脉冲

    ② 各脉冲开始时间为$\,X_j,j=1,2,\cdots,n\,$相互独立

    ③$\,X_j \text{服从} U(0,5/6T)\,$

    设$\,Y(t)\,$是$\,t\,$时刻接收到的信号幅度，求$\,Y(t)\,$的一维概率分布

    **求解**

    $\,X_j\,$的概率密度函数如下
    $$
        f_X(x) =
        \begin{cases}
            \frac{6}{5T} , & 0 \leq x \leq \frac{5}{6} T \\
            0,& \text{else}
        \end{cases}
    $$
    可以分为以下三种情况

    ![Ex2(1)](..\captures\Ex2(1).PNG "Ex2(1)")

    ![Ex2(2)](..\captures\Ex2(2).PNG "Ex2(2)")

    $$
        \text{当} 0 \leq t\leq T/6 \,\,\,P\{ Y(t,\omega)=A\} = P\{ 0 \leq X < t\} = \frac{6t}{5T}
    $$

    $$
        \text{当} T/6 \leq t < 5T/6 \,\,\, P\{ Y(t,\omega)=A\} =P\{t-\frac{T}{6} \leq X < t  \} = 1/ 5
    $$

    $$
        \text{当} 5T/6 \leq t < T \,\,\, P\{ Y(t,\omega)=A\} = P\{t-\frac{T}{6} < X < \frac{5T}{6}  \} = \frac{6}{5T}(T-t)
    $$

### 2.3 随机过程的数字特征

1. 均值函数定义(类似于均值)

    对于过程$\,X_t = \{ x(t), t\in T\}\,$
    $$
    m(t) = E[X(t)]= \int_{-\infty}^{+\infty} xdF(t;x) , t\in T 
    $$
    称为过程的均值函数

2. 方差函数定义

    对于过程$\,X_t = \{ x(t), t\in T\}\,$
    $$
    D(t) = D[X(t)]= E[X(t)-m(t)]^2
    $$
    称为过程的方差函数

    $\,\sqrt{D(t)}\,$称为过程的均方差函数

    由概率统计中方差和均值的关系有
    $$D(t)=E[X^2(t)]-[m(t)]^2$$

3. 协方差函数

    对于过程$\,X_t = \{ x(t), t\in T\}\,$
    $$
    C(s,t) = Cov[X(s),X(t)] = E\{ [X(s) - m(s)][X(t)-m(t)]\}
    $$
    称为过程的协方差函数

    由概率统计得

    $$
    C(s,t)=E[X(t)X(s)]-m(s)m(t)
    $$

4. 自相关函数

    对于过程$\,X_t = \{ x(t), t\in T\}\,$
    $$
    R(s,t)=E[X(s)X(t)]
    $$
    称为过程的自相关函数

    结合协方差的计算公式有
    $$
    C(s,t)=R(s,t)-m(s)m(t)
    $$

    **特别的**$\,m(t)=0\,$或$\,m(s)=0\,$时，即$\,X_T\,$是**零均值过程**
    $$
    C(s,t) = R(s,t)
    $$

    称
    $$
    \rho(s,t) = \frac{C(s,t)}{\sigma(s)\sigma(t)}
    $$
    为过程的**自相关系数函数**

5. 求数字特征的Examples

   - Ex.1

        **题目**：利用抛硬币的试验定义一个随机过程
        $$
            X(t) =  \begin{cases}
                cos\pi t, &出现正面 \\
                2t, & 出现反面
            \end{cases}
        $$
        求该过程的均值函数，方差函数，相关函数，协方差函数

        **求解**：
        $$
            \begin{array}{c|}
                X(t) & cos\pi t & 2t \\
                \hline
                p & \frac{1}{2} & \frac{1}{2}
            \end{array}
        $$
        $$
            m_X (t) = \frac{1}{2} cos\pi t + t \\
            E[X^2 (t)] = \frac{1}{2}cos^2 \pi t + 2t^2 \\
            \Rightarrow D_X (t) = E[X^2(t)]-[m_X (t)]^2 \,\,\text{就不算了} \\
            R_X(s,t) = E[X(s)X(t)] \,\, \text{注意该过程只有两条样本函数，有,}可令Y=X(s)X(t),这样好理解，即两个随机变量相乘得到新的一个随机变量，求它的期望
        $$
        $$
            \begin{array}{c|}
                (X(t),X(s)) & (cos\pi t, cos\pi s) & (2t,2s) \\
                \hline
                p & \frac{1}{2} & \frac{1}{2}
            \end{array}
        $$
        $$
            \Rightarrow R_X(s,t)= \frac{1}{2} cos\pi t cos\pi s + 2ts
        $$
   - Ex.2

        **题目**:设随机过程
        $$
            X(t) = Acos(\beta t + \Theta),\beta > 0\text{ and } \beta = constant
        $$
        随机变量$\,A,\Theta\,$相互独立，且$\,A\sim N(0,1), \Theta \sim U(0,2\pi)\,$，求过程的均值函数和自相关函数

        **求解**：
        $$
            \begin{aligned}
                m_X(t) & = E[Acos(\beta t + \Theta)] \,\,\text{A与}\Theta相互独立\\
                 & = E(A)E[cos(\beta t + \Theta)] \\
                 & = 0
            \end{aligned}
        $$
        $$
            \begin{aligned}
                R_X(s,t) & =E[X(s)X(t)] \\
                & = E[A^2 cos(\beta t + \Theta)cos(\beta s + \Theta)] \\
                & = E(A^2)E[cos(\beta t + \Theta)cos(\beta s + \Theta)]\,\text{  i.e }\,E(A^2)=D(A)+[E(A)]^2 \text{  将第二项视为求随机变量}\Theta的函数的数学期望\\
                & = \frac{1}{2\pi} \int_{0}^{2\pi} cos(\beta t + \theta)cos(\beta s + \theta) d\theta \text{  利用积化和差公式}\\
                & = \frac{1}{2} cos[\beta(t-s)]
            \end{aligned}
        $$

6. 随机分类

    ① 按状态空间和参数集进行分类

    $\,T,E\,$均是可列集

    $\,T\,$是可列集，$\,E\,$不可列

    $\,T\,$是不可列，$\,E\,$是可列集

    $\,T,E\,$均不可列

    当$\,T\,$是可列集时，称为**离散参数随机过程**(时间序列属于此种)

    当$\,E\,$是可列集时，称为**离散状态随机过程**

    ② 按概率结构进行分类

    二阶矩过程: 过程$\,X_t = \{ x(t), t\in T\}\,$,对$\,\forall t \in T \,\,\,X(t)\,$的二阶矩都存在

    独立过程：对任意整数$\,n\,$及任意$\,n\,$个不同的$\,t_i \in T\,$随机变量$\,X_{t_1},\cdots, X_{t_n}\,$相互独立

    独立增量过程：对任一正整数$\,n\,$及$\,\forall t \in T, \,\, t_1 < t_2 < \cdots < t_n \,$,随机变量
    $$
        X_{t_2}-X_{t_1}, X_{t_3}-X_{t_2},\cdots, X_{t_n}-X_{t_{n-1}}
    $$
    相互独立

    马尔可夫过程，正态过程 etc

### 2.4 随机过程的基本类型

1. 二阶矩过程

    对(实或复)随机过程，若对$\,\forall t \in T, E[\mid X_t \mid^2] < +\infty\,$,则称过程是二阶矩随机过程

2. 独立过程

    定义：对任意整数$\,n\,$及任意$\,n\,$个不同的$\,t_i \in T\,$随机变量$\,X_{t_1},\cdots, X_{t_n}\,$相互独立

    Ex.1 **最典型的独立过程——高斯白噪声**

    时间序列$\,X(n),n\in N\,$的
    $$
        E\{  X(n)  \} = 0 \,\,\,\,\,\,D\{  X(n)  \} = \sigma^2
    $$
    自相关函数
    $$
        R(m,n) = Cov(m,n)=
        \begin{cases}
            0 & m \neq n \\
            \sigma^2 & m = n
        \end{cases}
    $$
    称$\,X(n),n\in Z^+\,$为离散白噪声(序列)

    又若$\,X(n)\,$都服从正态分布，$\,X(n),n\in Z^+\,$是**高斯白噪声序列**

    对于$\,n\,$维正态随机变量
    $$
        \text{相互独立} \Leftrightarrow \text{不相关}
    $$
    所以高斯白噪声序列是独立时间序列

    若过程$\,\{   X(t), t \in R    \}\,$满足
    $$
        E[X(t)]=0, R(s,t)= \sigma^2 \delta (s-t) =
        \begin{cases}
            0 , & s \neq t \\
            \infty , & s = t
        \end{cases}
    $$
    称其为**连续参数白噪声**，若其是正态过程，称为**高斯白噪声过程**，它也是独立过程

    高斯白噪声是典型的**随机干扰数学模型**

3. 独立增量过程

    **定义**：若对$\, \forall n \geq 2 \text{及} t_0 = 0 < t_1 < t_2 < \cdots <  t_n\,$，增量序列
    $$
        X(t_1)-X(0),X(t_2)-X(t_1),\cdots,X(t_n)-X(t_{n-1})
    $$
    相互独立,称$\, \{ X(t), t \in T\}  , T = [0,\infty) \,$是独立增量过程

    **独立增量过程的性质**:

    独立增量过程的有限维分布由一维分布和增量分布确定

    **Attetion1**:对于独立增量过程$\,\{X(t),t\in T=[a,b] \}\,$若有
    $$
        P\{ X(a)=0 \} = 1
    $$
    根据$\,X(t)\,$的增量分布即可确定有限维分布,因为
    $$
        \forall t \in T, X(t)=X(t)-X(a)
    $$
    所以由增量分布可以确定一维分布，从而可以确定有限维分布

    **Attention2**：对于平稳独立增量过程$\,\{X(t),t\in T=[a,b] \}\,$若有
    $$
        P\{ X(a)=0 \} = 1
    $$
    根据$\,X(t)\,$的一维分布可以确定有限维分布，因为
    $$
        X(t_2)-X(t_1)与X(t_2-t_1+a)=X(t_2-t_1+a)-X(a)同分布
    $$

    **Attetion3**：不失一般性，设$\,X(0)=0\,$,有
    $$
        X(t_1),X(t_2)-X(t_1),\cdots,X(t_n)-X(t_{n-1})
    $$

    若独立增量过程$\, \{ X(t), t \in T\}  , T = [0,\infty) \,$，对$\, \forall s, t \in T,\text{及} h > 0\,$
    $$
        X(t+h)-X(s+h) \,\, \text{与} X(t)-X(s)
    $$
    有相同的分布函数，**注意，只是具有相同的分布函数，不一定相互独立**称该独立增量过程是**平稳独立增量过程**

    增量$\,X(t+\tau)-X(t)\,$的分布仅与$\,\tau\,$有关，与起始点$\,t\,$无关，称过程的增量具有**平稳性(齐性)**

    **Ex.2**

    若$\,X(n),n\in N^+\,$是**独立时间序列**，令
    $$
        Y(n)=\sum_{k=0}^{n} X(k) , \,\,\,\,\,X(0) = 0
    $$
    则$\,Y(n),n\in N^+\,$是**独立增量过程**，又若$\,X(n)\,$**相互独立同分布**，则$\,Y(n),n\in N^+\,$是**平稳独立增量过程**

    **证明Ex.2**:
    $$
        Y(2)-Y(1) = \sum_{k=0}^{2} X(k) - \sum_{k=0}^{1} X(k)= X(2)\\
        Y(3)-Y(2) = \sum_{k=0}^{3} X(k) - \sum_{k=0}^{2} X(k)=X(3) \\
        \vdots \\
        Y(n)-Y(n-1) = \sum_{k=0}^{n} X(k) - \sum_{k=0}^{n-1} X(k) = X(n)\\
        X(n)相互独立\Rightarrow Y(n)是独立增量过程\\
        若X(n)相互独立且同分布\Rightarrow Y(n)是平稳独立增量过程
    $$

    下面是**平稳独立增量过程($\,X(0)=0\,$)的数字特征**:

    ① **均值函数**$\,m(t)=mt \,\,\,\, \text{m是常数} \,$

    ② **方差函数**$\,D(t)=\sigma^2 t \,\,\,\, \sigma\text{是常数}\,$

    ③ **协方差函数**$\,C(s,t)=\sigma^2 min(s,t)\,$

    **对①进行证明**(②的证明与①类似)
    $$
        \begin{aligned}
            \forall s,t \in [0,\infty)\\
            m(t+s) & = E[X(t+s)] \\
            & = E[X(t+s)-X(s)+X(s)-X(0)] \\
            & = E[X(t+s)-X(s)]+E[X(s)-X(0)] \text{(根据平稳随机过程的性质)} \,\, X(t+s)-X(s)与X(t)-X(0)有相同的分布函数\\
            & = E[X(t)-X(0)]+E[X(s)-X(0)] \\
            & = E[X(t)]+E[X(s)] \\
            & = m(t)+m(s)
        \end{aligned}
    $$
    由数学分析的知识
    $$
        若y(s+t)=y(s)+y(t) \\
        对\forall t,有y(t)=ty(1)
    $$
    对于
    $$
        m(t+s)=m(t)+m(s) \implies m(t) = mt(m=m(1))
    $$

    **对③进行证明**
    $$
        \begin{aligned}
            t > s时\\
            C(s,t) &= E[X(t)X(s)]-m(s)m(t) \\
            & = E\{ [X(t)-X(s)+X(s)]X(s)\}-m(s)m(t)\\
            & = E\{ [X(t)-X(s)]X(s)+X^2(s)\}-m(s)m(t) i.e X(t)-X(s)与X(s)-X(0)相互独立，根据相互独立的随机变量的期望的性质\\
            & = E[X(t)-X(s)]E[X(s)]+E[X^2(s)]-m^2st \text{第二项利用方差公式}\\
            & = m(t-s)ms+\sigma^2s+m^2s^2-m^2st \\
            & = \sigma^2s
        \end{aligned}
    $$
    类似的$\,t<s\,$时，有$\,C(s,t)=\sigma^2t\,$,所以
    $$
        C(s,t)=\sigma^2 min(s,t)
    $$

4. 不相关过程与正交增量过程

    **定义**：过程$\,X(t),t\in T\,$,若对$\,\forall t \in T, E[\mid X(t) \mid^2] \,$存在，且对$\,t_1,t_2,t_3,t_4 \in T\,$满足
    $$
        E\{ [X(t_2)-X(t_1)]\overline{[X(t_4)-X(t_3)]}\}=E[X(t_2)-X(t_1)]E\overline{[X(t_4)-X(t_3)]}
    $$
    称过程为不相关过程(公式上面的横线应该是取共轭)

    若
    $$
        E\{ [X(t_2)-X(t_1)]\overline{[X(t_4)-X(t_3)]}\}=0
    $$
    称过程为正交增量过程