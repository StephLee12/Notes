- [Random Process](#random-process)
  - [Chapter 3 几种常见的随机过程](#chapter-3-%e5%87%a0%e7%a7%8d%e5%b8%b8%e8%a7%81%e7%9a%84%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b)
    - [3.1 正态过程](#31-%e6%ad%a3%e6%80%81%e8%bf%87%e7%a8%8b)
    - [3.2 维纳过程](#32-%e7%bb%b4%e7%ba%b3%e8%bf%87%e7%a8%8b)
    - [3.3 泊松过程](#33-%e6%b3%8a%e6%9d%be%e8%bf%87%e7%a8%8b)

# Random Process

## Chapter 3 几种常见的随机过程

### 3.1 正态过程

1. 概率密度与特征函数

    **2维正态分布**
    $$
        (X,Y)\sim N(\mu_1,\sigma_1^2;\mu_2,\sigma_2^2;\rho)
    $$
    $(X,Y)\,$的**联合概率密度**(矩阵形式)
    $$
        \varphi(x,y)= \frac{1}{2\pi\mid B \mid^{\frac{1}{2}}} exp
        \{ -\frac{1}{2}(X-\mu)^TB^{-1}(X-\mu)\} \\
        \mu = E \begin{bmatrix}
            X\\
            Y
        \end{bmatrix}=\begin{bmatrix}
            E(X) \\
            E(Y)
        \end{bmatrix}=\begin{bmatrix}
            \mu_1 \\
            \mu_2
        \end{bmatrix} \\ \\
        X=\begin{bmatrix}
            x \\
            y
        \end{bmatrix} B=\begin{bmatrix}
            \sigma_1^2 & \rho\sigma_1\sigma_2 \\
            \rho\sigma_1\sigma_2 & \sigma_2^2
        \end{bmatrix} \,\,\text{B是协方差矩阵，满足}\mid B \mid \neq 0
    $$
    记为$\,(X,Y)\sim N(\mu, B)\,$

    **$\,n\,$维正态分布**(用概率密度定义)：

    设$\,B=(b_{ij})\,$是$\,n\,$阶**正定对称矩阵**

    **补充：正定对称矩阵**
    $$
        A\in R^{n\times n},若A=A^T,\forall X \in R^n且X \neq 0, X^TAX>0 \\
        \text{称A为正定对称矩阵}
    $$

    $\,\mu\,$是$\,n\,$维实值列向量$\,\mu=(\mu_1,\mu_2,\cdots,\mu_n)^T\,$,是$\,n\,$维随机向量$\,X\,$的均值向量

    $\,B\,$是$\,n\,$维随机向量$\,X\,$的协方差矩阵

    定义$\,n\,$维随机向量$\,X=(X_1,X_2,\cdots,X_n)^T\,$的联合概率密度为
    $$
        \varphi(x,y)= \frac{1}{(2\pi)^{\frac{n}{2}} \mid B \mid^{\frac{1}{2}}} exp
        \{ -\frac{1}{2}(X-\mu)^TB^{-1}(X-\mu)\}
    $$
    称$\,X\,$服从$\,X\,$维正态分布

    注意当$\,B\,$是$\,n\,$阶正定对称阵时有$\,\mid B \mid \neq 0\,$
    若$\,\mid B \mid = 0 \text{ 即半正定}\,$,则不能用上式给出概率密度

    **定义$\,n\,$维正态分布随机向量的特征函数**：
    $$
        \phi(u) = exp\{ i\mu^T\mu - \frac{1}{2} \mu^T B \mu\}
    $$

    **$\,n\,$维正态分布**(用特征函数定义)：

    若$\,\mu\,$是$\,n\,$维实向量，$\,B\,$是$\,n\,$阶**非负定对称阵**，则以上式为特征函数的$\,n\,$维随机变量$\,X\,$服从$\,n\,$维正态分布 **注意这里只要求是非负定，因为在特征函数的定义中对于协方差矩阵$\,B\,$不用求逆(因为若为半正定阵，则矩阵不可逆)**

    若有$\,\mid B \mid = 0\,$，则称$\,X\,$服从**退化正态分布**或**奇异正态分布**

2. 边缘分布及二阶矩

    假定$\,n\,$维随机向量$\,X=(X_1,X_2,\cdots,X_n)^T\,$服从$\,N(\mu,B)\,$

    **定理1**：$\,X\,$的任一子向量
    $$
        (X_{k_1},X_{k_2},\cdots,X_{k_m})^T \,\,\,\, (m \leq n)
    $$
    也服从正态分布$\,N(\widetilde{\mu},\widetilde{B})\,$,其中$\,\widetilde{\mu} = (\mu_{k_1},\mu_{k_2},\cdots,\mu_{k_m})\,$,$\, \widetilde{B}是B保留第k_1,k_2,\cdots,k_m行及列所得到m阶矩阵\,$

    即多维正态分布的边缘分布仍是正态分布

3. 独立性问题

    **定理2**：$\,n\,$维正态随机向量$\,X=(X_1,X_2,\cdots,X_n)^T\,$**相互独立**的**充要条件**是它们两两不相关，即$\,Cov(X_i,X_j)=0\,\,(i\neq j)\,$,等价于$\,B\,$是**对角阵**

4. 正态随机向量的线性变换

    **定理3**：对$\,X\,$的线性组合
    $$
        Y=\sum_{j=1}^n l_jX_j=LX,\,\,\, L = (l_1,l_2,\cdots,l_n)
    $$
    有
    $$
        E(Y)=\sum_{j=1}^n l_j\mu_j=L\mu\\
        D(Y)=\sum_{j=1}^n \sum_{k=1}^n l_j l_k b_{jk} = LBL^T
    $$
    服从一维正态分布$\,N(E(Y),D(Y))\,$
    $\,X\,$服从$\,n\,$维正态分布的**充要条件**是它的任意一个**非零线性组合**服从**一维正态分布**

    **定理4**：对$\,X\,$作线性变换。

    $\,K=(k_{ij})_{m\times n}\,$是任意矩阵，则作线性变换($\,X\,$由$\,n\,$维随机向量变为$\,m\,$维随机向量)$\,Y=KX\,$服从$\,m\,$维正态分布$\,N(K\mu,KBK^T)\,$,变换后的随机向量的均值向量$\,E(Z)=K\mu\,$,协方差矩阵为$\,KBK^T\,$

    即**正态分布线性变换的不变性**，注意这里所说的正态分布**包含非退化和退化正态分布**

    但是线性变换之后不能保证服从**非退化正态分布**

    **e.g:**

    题目：设随机变量$\,X_0,V\,$相互独立，都服从标准正态分布，令
    $$
        X(1)=X_0+V, X(2)=X_0+2V,X(3)=X_0+3V
    $$
    问$\,(X(1),X(2),X(3))\,$是否服从非退化正态分布

    求解：
    $$
        X = \begin{bmatrix}
            X(1)\\
            X(2)\\
            X(3)
        \end{bmatrix}=\begin{bmatrix}
            1 & 1\\
            1 & 2 \\
            1 & 3
        \end{bmatrix}\begin{bmatrix}
            X_0\\
            V
        \end{bmatrix}=C\begin{bmatrix}
            X_0\\
            V
        \end{bmatrix}
    $$
    $$
        \begin{bmatrix}
            X_0\\
            V
        \end{bmatrix} \sim N(\mu,B) \,\,\,
        \mu = \begin{bmatrix}
            0 \\
            0
        \end{bmatrix} \,\,\,\,
        B = \begin{bmatrix}
            1 & 0 \\
            0 & 1
        \end{bmatrix}
    $$
    $X\,$的协方差矩阵为
    $$
        CBC^T=C\begin{bmatrix}
            1 & 0 \\
            0 & 1
        \end{bmatrix}C^T=
        \begin{bmatrix}
            1 & 1\\
            1 & 2\\
            1 & 3
        \end{bmatrix}
        \begin{bmatrix}
            1 & 1 & 1\\
            1 & 2 & 3
        \end{bmatrix}
    $$
    $$
        \mid CBC^T \mid = 0
    $$
    所以$\,X\,$不服从非退化正态分布

    **总结**：一般地，若$\,X=(X_1,X_2)\,$是非退化二维正态随机向量，其线性变换$\,Y=CX\,$有：

    ① 每一分量服从正态分布

    ②不能构成二维以上地非退化正态分布

    **但是**非退化正态分布随机向量$\,X\,$的**行满秩**线性变换仍服从非退化正态分布

    **定理5**：对$\,n\,$维随机变量$\,X\,$作正交变换

    存在一个正交阵$\,U\,$,使得线性变换后的$\,Y=UX\,$是一个相互独立的正态随机向量

    **补充：正交阵 满足$\,AA^T=I\,$**

    **证明定理5**：
    根据矩阵理论，对实正定对称阵，存在正交阵，满足下式
    $$
        UBU^T=D=
        \begin{bmatrix}
            d_1 & 0 & \cdots & 0 \\
            0 & d_2 & \cdots & 0 \\
            \vdots & \vdots & \ddots & \vdots \\
            0 & 0 & \cdots & d_n
        \end{bmatrix}
    $$
    其中$\,d_i\,$是$\,B\,$的特征值，$\,U\,$式以单位正交特征向量为列构成的正交阵，令$\,Y=UX\,$即得证(因为协方差矩阵为对角阵)

    ① 若$\,n\,$维随机向量$\,X\,$是非退化正态向量，所以其协方差矩阵$\,B\,$是正定阵(即非奇异)

    这里补充一点 正定阵的行列式不为0，所以一定满秩(线性代数)

    所以协方差矩阵满秩，即协方差矩阵有$\,n\,$个线性无关的特征向量 线性变换得到的随机向量仍服从非退化正态分布

    ② 若$\,n\,$维随机向量$\,X\,$是退化正态向量，即协方差矩阵非正定，假设$\,R(B)=r<n\,$此时正态分布退化到一个$\,r\,$维子空间上

5. 定义正态过程

    某一随机过程$\,X_t,t\in T\,$,若任意正整数$\,n \geq 1\,$及任意的$\, t_1, t_2 ,\cdots, t_n \in T\,$，随机变量$\,X_{t_1},X_{t_2},\cdots, X_{t_n}\,$的联合分布是$\,n\,$维正态分布，则称该过程是**正态过程**,(即任意有限维分布都是联合正态分布)

6. 如何验证随机过程$\,X_t,t\in T\,$是正态过程

    ① 计算$\,X\,$的$\,n\,$维协方差矩阵$\,B\,$

    ② 验证$\,B\,$的正定性

    ③ 求正交矩阵$\,U\,$，使$\,UBU^T=D\,$

    ④ 令$\,Y=UX\,$ (称将$\,X\,$去相关)

    ⑤ 检验$\,Y\,$的独立性

    ⑥ 检验$\,Y\,$的一维分布的正态性

    若检验得$\,Y\,$是相互独立的正态随机向量，则可做逆变换$\,X=U^{-1}Y\,$是$\,n\,$维正态随机变量，即$\,X_t,t\in T\,$是正态过程

7. 例题

    - Ex.1

        **题目**：随机振幅电信号
        $$
            X(t) = \xi cos\omega t + \eta sin\omega t, t\in R \\
            E(\xi) = E(\eta) = 0, E(\xi^2)=E(\eta^2)=\sigma^2
        $$
        随机变量$\,\xi,\eta\,$相互独立且服从正态分布

        (1) 求$\,X(t)\,$的均值函数和自相关函数

        (2)写出$\,X(t)\,$的一维概率密度和二维概率密度

        **求解**：

        (1):
        $$
            E[X(t)] = cos\omega tE(\xi) + sin\omega t E(\eta)\,\,又 E(\xi) = E(\eta) = 0 \\
            \Rightarrow E[X(t)] = 0
        $$
        $$
            \begin{aligned}
                R_X(s,t) & = E[X(t)X(s)]  \\
                & = E[(\xi cos\omega t + \eta sin\omega t)(\xi cos\omega s + \eta sin\omega s)] \\
                & = cos\omega t cos\omega sE(\xi^2)+ sin\omega t sin\omega s\eta^2 + cos\omega t sin\omega s E(\xi \eta) + sin\omega t cos\omega s E(\xi \eta) \text{    i.e }\xi和\eta相互独立\Rightarrow E(\xi \eta) = E(\xi)E(\eta) = 0\\
                & = \sigma^2 (cos\omega t cos\omega s+sin\omega t sin\omega s) \\
                & = \sigma^2 cos\omega(t-s)
            \end{aligned}
        $$
        (2):
        $$
            二维随机向量(\xi,\eta)^T，服从二维正态分布且相互独立 \\  
            \text{利用正态分布线性组合的性质 X服从一维正态分布} \\
            已知E[X(t)]=0\\
            D[X(t)]=Cov(t,t)=R(t,t)=\sigma^2\\
            所以一维概率密度为\\
            f(x,t)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{x^2}{2\sigma^2}}
        $$
        对于二维概率密度可以利用**现有的$\,\xi,\eta\,$的分布和两个随机变量间的关系**，再利用**正态分布的线性变换不变性求解**
        $$
            X=\begin{bmatrix}
                X(s)\\
                X(t)
            \end{bmatrix}=\begin{bmatrix}
                cos\omega s & sin\omega s \\
                cos\omega t & sin\omega t
            \end{bmatrix}\begin{bmatrix}
                \xi \\
                \eta
            \end{bmatrix}
        $$
        $$
            记为X=CL\\
            其中二维随机变量的均值向量为\mu = (0,0)^T\\
            协方差矩阵B为\begin{bmatrix}
                \sigma^2 & 0 \\
                0 & \sigma^2
            \end{bmatrix}
        $$
        $$
            经过线性变换后X的均值向量为C\mu = (0,0)^T \\
            协方差矩阵K = CBC^T=\begin{bmatrix}
                \sigma^2 & \sigma^2 cos\omega(s-t) \\
                \sigma^2 cos\omega(s-t) & \sigma^2
            \end{bmatrix} \,\,有\mid K \mid \neq 0 \\
            X服从二维非退化正态分布
            二维概率密度函数为
        $$
        $$
            f(x_1,x_2;s,t) = \frac{1}{2\pi \mid B \mid^{\frac{1}{2}}}exp(-\frac{1}{2}X^TK^{-1}X)
        $$
    - Ex.2——结论，两个相互独立的正态过程相加还是正态过程

### 3.2 维纳过程

1. 定义

    设一粒花粉每隔$\,\Delta t\,$时间，随机以$\,p=\frac{1}{2}\,$向右移动$\,\Delta x\,$，且每次移动相互独立

    若用$\,X_t\,$表示$\,t\,$时刻质点的位置，有
    $$
        X_t=\Delta x (X_1 + X_2+\cdots + X_{[\frac{t}{\Delta t}]})
    $$
    每次移动都服从两点分布，因此$\,E(X_i)=0,D(X_i)=E(X_i^2)=1,\,\,i = 1, 2, \cdots\,$，故
    $$
        E(X_t)=0,\,\,D(X_t)=(\Delta x)^2[\frac{t}{\Delta t}]
    $$
    以上只是微小粒子在直线上做不规则运动的近似描述，实际例子的不规则运动是连续进行的，**需要考虑$\,\Delta t \rightarrow 0\,$的情形**。在物理实验中，通常有$\,\Delta t \rightarrow 0, \,\, \Delta x \rightarrow 0\,$，许多情况下满足
    $$
        \Delta x= c \sqrt{\Delta t},\,\, c=constant
    $$
    下面考虑此种条件下的极限情形

    当$\,\Delta t \rightarrow 0\,$时，显然$\,E(X_t)=0\,$而
    $$
    \lim_{\Delta t \rightarrow 0} D(X_t)=
    \lim_{\Delta t \rightarrow 0} (\Delta x)^2[\frac{t}{\Delta t}]=
    \lim_{\Delta t \rightarrow 0} c^2 \Delta t [\frac{t}{\Delta t}]=
    c^2t
    $$
    另一方面，$\, X_t=\Delta x (X_1 + X_2+\cdots + X_{[\frac{t}{\Delta t}]})\,$可以看为$\,[\frac{t}{\Delta t}]\,$个相互独立同分布的随机变量之和，根据**2.4 3 Ex.2**，所得，过程是平稳独立增量过程。又由中心极限定理
    $$
        \lim_{\Delta t \rightarrow 0} P\{ \frac{X_t}{\sqrt{c^2t}} \leq x \} =
        \lim_{\Delta t \rightarrow 0} P\{ \frac{\sum_{i=0}^{[\frac{t}{\Delta t}]} \Delta x X_i-0}{\sqrt{c^2t}} \leq x \} = \Phi (x)
    $$
    即当$\,\Delta t \rightarrow 0\,$时,$\,X_t\,$趋于服从**正态分布**$\,N(0,c^2t)\,$

    由上可以定义出**维纳过程**

    若随机过程$\,\{ W_t,t\geq 0 \}\,$满足下述三条，即为**是参数$\,\sigma^2\,$维纳过程**,若$\,\sigma =1\,$，称之为标准维纳过程

    **Attetion**：PPT定义与PDF不同，下面是PPT的定义

    ① 具有平稳独立增量过程

    ② $\,E\{ W(r) \} = 0\,$

    ③ $\,W(r) \sim N(0,\sigma^2 r)\,$

    ④ $\,P\{ W(0) = 0 \} = 1\,$

2. 维纳过程的分布

    ① 一维分布$\,W(t) \sim N(0,\sigma^2 t)\,$

    ② 增量分布$\,\forall s,t \geq 0, W_t-W_s \sim N(0,\sigma^2 \mid t -s \mid),(\sigma > 0)\,$

    因为过程是平稳独立增量过程

    所以$\,W(t)-W(s)与W(t-s)-W(0)同分布N(0,\sigma^2 (t-s))\,$

    ③ 维纳过程是正态过程

    **证明**(利用平稳独立增量和正态分布线性变换不变性)

    任取$\,n\,$及$\,t_1<t_2<\cdots<t_n\,$
    $$
        X_k = W(t_k)-W(t_{k-1}),t_0=0,k=1,2,\cdots,n
    $$
    由维纳过程的增量分布得
    $$
        X_k \sim N(0,\sigma^2(t_k-t_{k-1}))
    $$
    且$\,n\,$维随机向量$\,X_n\,$相互独立$\,\Rightarrow\,$，过程$\,X(t)\,$是正态过程，且
    $$
        W(t_k) = X_1 + X_2 + \cdots + X_k
    $$
    转换为矩阵形式
    $$
        \begin{bmatrix}
            W(t_1) \\
            W(t_2) \\
            \vdots \\
            W(t_n)
        \end{bmatrix}=\begin{bmatrix}
            1 & 0 & 0 & 0 & 0 \\
            1 & 1 & 0 & 0 & 0 \\
            1 & 1 & 1 & 0 & 0 \\
            \vdots & \vdots & \vdots & \vdots & \vdots \\
            1 & 1 & 1 & 1 & 1
        \end{bmatrix}\begin{bmatrix}
            X_1 \\
            X_2 \\
            \vdots \\
            X_n
        \end{bmatrix}
    $$
    由于正态分布线性变换的不变性，所以维纳过程也是正态过程

3. 维纳过程的数字特征

    ① $\,E[W(t)]=0\,$

    ② $\,D[W(t)]=\sigma^2 t\,$

    ③ $\,C(s,t)=R(s,t)=\sigma^2 min(s,t)\,$

4. Ex

    **题目**：已知参数为$\,\sigma^2\,$的维纳过程，求下列过程的均值函数$\,m_X(t)\,$和相关函数$\,R_X(s,t)\,$
    $$
        (1) \,X(t) = W^2(t), t\geq 0 \\
        (2)\,X(t) = W(t+a)-W(t), t \geq 0\,且\,a = constant
    $$

    **求解**：

    (1):
    $$
        m_X(t) = E[W^2(t)] = D[W(t)]+\{ E[W(t)]\}^2 = \sigma^2 t
    $$
    $$
        不妨设s<t \\
        \begin{aligned}
            R_X(s,t)&=E[X(s)X(t)]=E[W^2(s)W^2(t)] \\
            & = E\{ W^2(s)[W(t)-W(s)+W(s)]^2 \} \\
            & = E\{W^2(s)[W(t)-W(s)]^2 \} + 2E\{ W^3(s)[W(t)-W(s)] \} + E[W^4(s)] \text{   i.e }W(s)-W(0)与W(t)-W(s)相互独立\,\,E[W(t)-W(s)]=0\\
            & = E[W^2(s)]E\{[W(t)-W(s)]^2\}+E[W^4(s)] \\
            & = \sigma^2 s \sigma^2 (t-s)+3\sigma^4 s^2 \\
            & = \sigma^4 (st+2s^2)\\
            &\Rightarrow R_X(s,t)= \sigma^4 (st+2min^2(s,t))
        \end{aligned}
    $$
    其中对于$\,E[W^4(s)]\,$,有
    $$
        若X\sim N(0,\sigma^2) \\
        E(X^n)=\begin{cases}
            0, & n = 1,3,5\cdots \\
            \sigma^n(n-1)(n-3)\cdots1, & n = 2,4,6 \cdots
        \end{cases}
    $$

    (2):
    $$
        m_X(t)= 0 \text{   因为是维纳过程是平稳独立增量过程} \\
    $$
    $$
        \begin{aligned}
            R_X(s,t) &= E[X(s)X(t)] = E\{ [W(s+a)-W(s)][W(t+a)-W(t)]\} \\
            & = R_W(s+a,t+a) - R_W(s+a,a)-R_W(a,t+a)+R_W(a,a)\\
            & = \sigma^2 min(s+a,t+a)-\sigma^2 a - \sigma^2 a + \sigma^2 a \\
            & = \sigma^2 min(s,t)
        \end{aligned}
    $$

### 3.3 泊松过程

1. 计数过程

    若$\,N(t)\,$表示在$\,(0,t)\,$内事件$\,A\,$出现的总次数,称该过程为随机过程

    计数过程应该满足：

    ① $\,N(t) \geq 0\,$

    ② $\,N(t)\,$取非负整数

    ③ 若$\,s < t, \,\, N(s)  \leq N(t)\,$

    ④ $\, s < t, N(t) - N(s)\,$表示在时间间隔内事件出现的次数

2. 齐次Poisson过程

    电话呼叫过程过程有以下的特点：

    ① **零初值性** $\,N(0)=0\,$

    ② **独立增量性** 任意两个不相重叠的时间间隔内到达的呼叫次数相互独立

    ③ **齐次性** 在$\,(s,t)\,$时间内到达的呼叫次数仅与时间间隔长度$\,t-s\,$有关，而与起始时间无关

    ④ **普通性** 在充分小的时间间隔内到达的呼叫次数最多仅有一次，即对于充分小的$\,\Delta t\,$，有
    $$
        P\{ N(\Delta t) = 0 \} = p_0(\Delta t) = 1 -\lambda\Delta t + o(\Delta t) \\
        P\{ N(\Delta t) = 1 \} = p_1(\Delta t) = \lambda\Delta t + o(\Delta t) \\
        P\{ N(\Delta t) \geq 2 \} = \sum_{k=2}^\infty p_k(\Delta t) = o(\Delta t)
    $$

    下面定义**齐次泊松过程**：若计数过程$\,\{ N(t),t\geq 0 \}\,$满足:

    ① $\,N(0)=0\,$

    ② 是平稳独立增量过程

    ③ $\,P\{ N(h) = 1 \} = \lambda h + o(h), \, \lambda > 0\,$

    ④ $\,P\{ N(h) \geq 2 \} = o(h)\,$

    称该计数过程是参数(或速率，强度)为$\,\lambda\,$的**齐次泊松过程**

    **定理**：齐次泊松过程在时间间隔$\,(t_0,t_0+t)\,$内时间出现$\,n\,$次的概率为
    $$
        P\{ [N(t_0+t)-N(t_0)] = n \} =
            \frac{(\lambda t)^n}{n!} e^{-\lambda t},
            (n = 0 ,1 ,2 ,\cdots)
    $$
    即服从参数为$\,\lambda t\,$的泊松分布(增量分布)

    特别的
    $$
        P\{ [N(t)] = k \} = P\{ [N(t)-N(0)] = k \} = 
            \frac{(\lambda t)^k}{k!} e^{-\lambda t},
            (n = 0 ,1 ,2 ,\cdots)
    $$
    所以泊松过程的一维分布服从$\,P(\lambda t)\,$

    由此定理可得**齐次泊松过程**的等价定义

    ① $\,N(0)=0\,$

    ② 过程是**独立增量过程**

    ③ $\,\forall 0 \leq s < t, N(t)-N(s)\sim P(\lambda(t-s))\,$

    **齐次泊松过程的数字特征**

    ① 均值函数 $\,m(t)=E[N(t)]=\lambda t\,$ 可得$\,\lambda = \frac{E[N(t)]}{t}\,$

    $\lambda\,$的**意义**是单位时间内事件出现的平均次数

    ② 方差函数 $\,D(t) = \lambda t\,$

    ③ 协方差函数 $\,C(s,t)=\lambda min(s,t)\,$

    ④ 自相关函数 $\,R(s,t)=C(s,t)+\lambda^2 st\,$

   **泊松过程的叠加**

   **定理**：设$\,\{N_1(t),t\geq 0\}\,$和$\,\{N_2(t),t\geq 0\}\,$是相互独立的强度分别为$\,\lambda_1,\lambda_2\,$的泊松过程，则$\,\{N(t)=N_1(t)+N_2(t),t\geq 0\}\,$是强度为$\,\lambda_1 + \lambda_2\,$的泊松过程

   **泊松过程的分解**：随机并联系统

   **定理**：设$\,\{N(t),t\geq 0\}\,$是强度为$\,\lambda\,$的泊松过程，全体事件可分为$\,r\,$类，第$\,i\,$类事件发生的概率为$\,0<p_i<1,i=1,2,\cdots,r\,$且$\,\sum_{i=1}^{r} p_i =1\,$，则该过程可分解为$\,r\,$相互独立的泊松过程之和，各泊松过程的参数分别为$\,\lambda p_i,i = 1,2,\cdots,r\,$

3. 非齐次泊松过程

    齐次泊松过程是平稳独立增量过程，可以假定到达率(强度)$\,\lambda\,$时=是常数，当过程的到达率随时间**缓慢变化**时，此假定合理

    但若到达率随时间变化，设到达率为时间函数$\,\lambda(t)\,$.如果技术过程满足下列条件：

    ① $\,N(0)=0\,$

    ② 是独立增量过程

    ③ $\,P\{ N(t+\Delta t) - N(t) = 1 \} = \lambda(t) \Delta t+ o(\Delta t), \, \lambda > 0\,$

    ④ $\,P\{ N(t+\Delta t) - N(t) \geq 2 \} = o(t)\,$

    称该计数过程是具有速率函数$\,\lambda(t)\,$的非齐次泊松过程
