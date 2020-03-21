- [随机过程](#%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b)
  - [补充内容](#%e8%a1%a5%e5%85%85%e5%86%85%e5%ae%b9)
    - [特征函数(傅里叶变换警告！！)](#%e7%89%b9%e5%be%81%e5%87%bd%e6%95%b0%e5%82%85%e9%87%8c%e5%8f%b6%e5%8f%98%e6%8d%a2%e8%ad%a6%e5%91%8a)
    - [向量范数](#%e5%90%91%e9%87%8f%e8%8c%83%e6%95%b0)
  - [Chapter 2 随机过程基础知识](#chapter-2-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e5%9f%ba%e7%a1%80%e7%9f%a5%e8%af%86)
    - [2.1 随机过程的定义及分类](#21-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%ae%9a%e4%b9%89%e5%8f%8a%e5%88%86%e7%b1%bb)
    - [2.2 随机过程的分布](#22-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%88%86%e5%b8%83)
    - [2.3 随机过程的数字特征](#23-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e6%95%b0%e5%ad%97%e7%89%b9%e5%be%81)
    - [2.4 随机过程的基本类型](#24-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9f%ba%e6%9c%ac%e7%b1%bb%e5%9e%8b)
  - [Chapter 3 几种常见的随机过程](#chapter-3-%e5%87%a0%e7%a7%8d%e5%b8%b8%e8%a7%81%e7%9a%84%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b)
    - [3.1 正态过程](#31-%e6%ad%a3%e6%80%81%e8%bf%87%e7%a8%8b)
    - [3.2 维纳过程](#32-%e7%bb%b4%e7%ba%b3%e8%bf%87%e7%a8%8b)
    - [3.3 泊松过程](#33-%e6%b3%8a%e6%9d%be%e8%bf%87%e7%a8%8b)
  - [Chapter 4 均方微积分](#chapter-4-%e5%9d%87%e6%96%b9%e5%be%ae%e7%a7%af%e5%88%86)
    - [4.1 收敛性](#41-%e6%94%b6%e6%95%9b%e6%80%a7)
    - [4.2 二阶矩随机变量空间及均方极限](#42-%e4%ba%8c%e9%98%b6%e7%9f%a9%e9%9a%8f%e6%9c%ba%e5%8f%98%e9%87%8f%e7%a9%ba%e9%97%b4%e5%8f%8a%e5%9d%87%e6%96%b9%e6%9e%81%e9%99%90)
    - [4.3 随机过程的均方极限和均方连续](#43-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9d%87%e6%96%b9%e6%9e%81%e9%99%90%e5%92%8c%e5%9d%87%e6%96%b9%e8%bf%9e%e7%bb%ad)
    - [4.4 随机过程的均方导数](#44-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9d%87%e6%96%b9%e5%af%bc%e6%95%b0)
    - [4.5 随机过程的均方积分](#45-%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9d%87%e6%96%b9%e7%a7%af%e5%88%86)
  - [Chapter 5 平稳随机过程](#chapter-5-%e5%b9%b3%e7%a8%b3%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b)
    - [5.1 平稳随机过程的概念](#51-%e5%b9%b3%e7%a8%b3%e9%9a%8f%e6%9c%ba%e8%bf%87%e7%a8%8b%e7%9a%84%e6%a6%82%e5%bf%b5)
    - [5.2 平稳过程的自相关函数](#52-%e5%b9%b3%e7%a8%b3%e8%bf%87%e7%a8%8b%e7%9a%84%e8%87%aa%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0)
    - [5.3 平稳过程的各态历经性](#53-%e5%b9%b3%e7%a8%b3%e8%bf%87%e7%a8%8b%e7%9a%84%e5%90%84%e6%80%81%e5%8e%86%e7%bb%8f%e6%80%a7)

# 随机过程

## 补充内容

### 特征函数(傅里叶变换警告！！)

1. 定义

    设$\,X,Y\,$是实随机变量，定义复随机变量$\,Z=X+jY\,$,定义其数学期望为
    $$
        E(Z)=E(X)+jE(Y)
    $$
    特别对于复数$\,e^{juX}=cos(uX)+jsin(uX) \,\,\, \text{欧拉公式}\,$有
    $$
        \begin{aligned}
            E(e^{juX}) &= E(cosuX)+jE(sinuX) \\
            &= \int_{-\infty}^{+\infty} cosux\,dF(x) \,\, + j\int_{-\infty}^{+\infty} sinux\,dF(x)=\int_{-\infty}^{+\infty} e^{jux}\,dF(x)
        \end{aligned}
    $$
    是关于分布函数$\,F(x)\,$的**傅里叶-斯蒂阶变换**

    由上述推导可得：$\,\,E(e^{jux})$总存在，是**关于实变量$\,u\,$的函数**

    定义：设$\,X\,$是定义在概率空间上的随机变量，称
    $$
        \varphi_X(u)=E(e^{juX})=\int_{-\infty}^{+\infty} e^{jux}\,dF(x), \,\,\, u\in R
    $$
    为随机变量$\,X\,$的特征函数，或称为分布函数$\,F(x)\,$的特征函数

    当$\,X\,$是连续型随机变量，特征函数为
    $$
        \varphi_X(u)=E(e^{juX})=\int_{-\infty}^{+\infty} e^{jux}f(x)dx
    $$
    当$\,X\,$是离散型随机变量，特征函数为
    $$
        \varphi_X(u)=E(e^{juX})=\sum_k e^{jux_k}p_k
    $$

2. 常用分布随机变量的特征函数

    **二项分布 $\,X\,$~$\,B(n,p)\,$**
    $$
        P\{X=k \} = C_n^k p^k (1-p)^{n-k}, \,\,\, k=0,1,\cdots,n
    $$
    特征函数为
    $$
        \begin{aligned}
            \varphi (u) &= E(e^{juX}) \\
            &= \sum_k e^{jux_k}p_k \\
            &= \sum_k e^{jux_k} C_n^k p^k (1-p)^{n-k}\\
            &= \sum_k C_n^k (pe^{ju})^k (1-p)^{n-k} \\
            &= (q+pe^{ju})^n \,\,\, (q=1-p)
        \end{aligned}
    $$

    **泊松分布 $\,X\,$~$\,P(\lambda)\,$**,特征函数为
    $$
        \varphi(u)=e^{\lambda(e^{ju}-1)}
    $$

    **均匀分布 $\,X\,$~$\,U[-a,a]\,$**,特征函数为(用傅里叶-斯蒂阶变换计算，写出其概率密度函数即可计算)
    $$
        \varphi(u) = \frac{sinau}{au}
    $$

    **指数分布**，特征函数为
    $$
        \varphi(u)= (1-\frac{ju}{\lambda})^{-1}
    $$

    **正态分布 $\,X\,$~$\,N(a,\sigma^2)\,$**,特征函数
    $$
        \varphi(u)=e^{jau-\frac{1}{2} \sigma^2 u^2}
    $$
    特殊的对于标准正态分布，特征函数为
    $$
        \varphi(u)=e^{\frac{1}{2}u^2}
    $$

3. 特征函数的性质

    ① $\,\mid \varphi(u) \mid \leq \varphi(0) =1\,$

    ② $\,\overline{\varphi(u)} = \varphi(-u)\,$

    ③ 随机变量$\,X\,$的特征函数为$\,\varphi_X(u)\,$,则$\,Y=aX+b\,$的特征函数是
    $$
        \varphi_Y(u)=e^{jbu}\varphi_X(au)
    $$

    ④ 随机变量$\,X\,$的特征函数在$\,R\,$上**一致连续**，即
    $$
        \forall \varepsilon>0, \exist \delta>0,使\mid \Delta u\mid<\delta,对u\in R，一致有 \\
        \mid \varphi(u+\Delta u)-\varphi(u) \mid < \varepsilon
    $$

4. 特征函数相关定理

    **波赫纳-辛钦定理**：函数$\,\varphi(u)\,$是特征函数的充要条件是函数在$\,R\,$上**一致连续，**非负定**且$\,\varphi(0)=1\,$

    **定理**：若随机变量$\,X\,$的$\,n\,$阶矩存在，则$\,X\,$的特征函数$\,\varphi(u)\,$的$\,k\,$阶导数$\,\varphi^{(k)}(u)\,$存在，且
    $$
        E(X^k)=j^{(-k)}\varphi^{(k)}(0)
    $$

    由特征函数定义知**其分布函数可以惟一确定特征函数**，下述**反演公式**说明其逆也成立
    $$
        对于任意连续点x_1,x_2 \\
        F(x_2)-F(x_1)=\lim_{T\rightarrow +\infty} \frac{1}{2\pi} \int_{-T}^{T} \frac{e^{-jux_1}-e^{-jux_2}}{ju} \varphi(u)du
    $$
    由反演公式得到**惟一性定理**：两个分布函数恒等的充要条件是它们的特征函数恒等

    **推论**：

    若随机变量$\,X\,$的特征函数$\,\varphi_X(u)\,$在$\,R\,$上绝对可积，则$\,X\,$为连续型随机变量，其概率密度和特征函数分别为
    $$
        f(x)= \frac{1}{2\pi} \int_{\infty}^{\infty} e^{-jux} \varphi(t)du, \,\,\,\, \varphi(u)=\int_{\infty}^{\infty} e^{jux}f(x)dx
    $$

    若随机变量$\,X\,$是离散型的，其分布律为
    $$
        P\{X=k \} = p_k, \,\,\,\, k\in Z
    $$
    有
    $$
        \varphi(u)=\sum_{k=-\infty}^{+\infty} p_ke^{jku} \\
        p_k = \frac{1}{2\pi} \int_{-\pi}^{+\pi} e^{-juk}\varphi(u)du
    $$

### 向量范数

向量$\,\overrightarrow{v}\,$具有$\,n\,$个分量$\,v_1,v_2,\cdots,v_n\,$

1. 0范数

    $$
        \mid\mid \overrightarrow{v} \mid\mid_0 = 分量中非零元素的个数
    $$

2. 1范数

    可以用来表示曼哈顿距离
    $$
        \begin{aligned}
            \mid\mid \overrightarrow{v} \mid\mid_1 &= (\mid v_1 \mid^1 + \mid v_2 \mid^1 + \cdots + \mid v_n \mid^1)^1 \\
            &= \mid v_1\mid + \mid v_2 \mid + \cdots + \mid v_n \mid
        \end{aligned} 
    $$

3. 2范数

    可以用来表示欧氏距离
    $$
        \mid\mid \overrightarrow{v} \mid\mid_2 =
        (v_1^2+v_2^2+\cdots+v_n^2)^\frac{1}{2}
    $$

4. p范数

    $$
        \mid\mid \overrightarrow{v} \mid\mid_p =
        (v_1^p+v_2^p+\cdots+v_n^p)^\frac{1}{p}
    $$

5. 范数的性质

    ① 正定性
    $$
        \forall x \in H , \mid\mid X\mid\mid \geq 0\\
        且 \mid\mid X \mid\mid = 0 \Leftrightarrow P\{X=0\}=1
    $$
    ② 齐次性
    $$
        \forall a \in C, \forall x \in H,
        \mid\mid aX \mid\mid = \mid a \mid \mid\mid X\mid\mid
    $$
    ③ 三角不等式
    $$
        \forall X,Y\in H, \mid\mid X+Y \mid\mid \leq \mid\mid X\mid \mid + \mid\mid Y \mid\mid
    $$

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

    ![随机过程二元函数](captures\随机过程定义.PNG "随机过程二元函数")

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

    ![Ex2(1)](captures\Ex2(1).PNG "Ex2(1)")

    ![Ex2(2)](captures\Ex2(2).PNG "Ex2(2)")

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

    ![收敛性的关系](captures\收敛性的关系.PNG "收敛性的关系")

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

    ![均方不定积分](captures\均方不定积分.PNG "均方不定积分")
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
