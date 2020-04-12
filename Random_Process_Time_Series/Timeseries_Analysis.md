- [Time_Series_Analysis](#timeseriesanalysis)
  - [Chapter 1 时间序列](#chapter-1-%e6%97%b6%e9%97%b4%e5%ba%8f%e5%88%97)
    - [1.2 平稳序列](#12-%e5%b9%b3%e7%a8%b3%e5%ba%8f%e5%88%97)
    - [1.3 时间序列的平稳化预处理](#13-%e6%97%b6%e9%97%b4%e5%ba%8f%e5%88%97%e7%9a%84%e5%b9%b3%e7%a8%b3%e5%8c%96%e9%a2%84%e5%a4%84%e7%90%86)
    - [1.4 推移算子及数据预处理](#14-%e6%8e%a8%e7%a7%bb%e7%ae%97%e5%ad%90%e5%8f%8a%e6%95%b0%e6%8d%ae%e9%a2%84%e5%a4%84%e7%90%86)
  - [Chapter 2 线性平稳过程](#chapter-2-%e7%ba%bf%e6%80%a7%e5%b9%b3%e7%a8%b3%e8%bf%87%e7%a8%8b)
    - [2.1 一般线性过程](#21-%e4%b8%80%e8%88%ac%e7%ba%bf%e6%80%a7%e8%bf%87%e7%a8%8b)
      - [白噪声](#%e7%99%bd%e5%99%aa%e5%a3%b0)
      - [线性过程的两种等价形式](#%e7%ba%bf%e6%80%a7%e8%bf%87%e7%a8%8b%e7%9a%84%e4%b8%a4%e7%a7%8d%e7%ad%89%e4%bb%b7%e5%bd%a2%e5%bc%8f)
      - [线性过程的均值函数与自协方差函数](#%e7%ba%bf%e6%80%a7%e8%bf%87%e7%a8%8b%e7%9a%84%e5%9d%87%e5%80%bc%e5%87%bd%e6%95%b0%e4%b8%8e%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0)
      - [线性过程的平稳过程](#%e7%ba%bf%e6%80%a7%e8%bf%87%e7%a8%8b%e7%9a%84%e5%b9%b3%e7%a8%b3%e8%bf%87%e7%a8%8b)
      - [线性过程的可逆性条件](#%e7%ba%bf%e6%80%a7%e8%bf%87%e7%a8%8b%e7%9a%84%e5%8f%af%e9%80%86%e6%80%a7%e6%9d%a1%e4%bb%b6)
    - [2.2 平稳序列的线性数学模型](#22-%e5%b9%b3%e7%a8%b3%e5%ba%8f%e5%88%97%e7%9a%84%e7%ba%bf%e6%80%a7%e6%95%b0%e5%ad%a6%e6%a8%a1%e5%9e%8b)
      - [常系数齐次线性差分方程](#%e5%b8%b8%e7%b3%bb%e6%95%b0%e9%bd%90%e6%ac%a1%e7%ba%bf%e6%80%a7%e5%b7%ae%e5%88%86%e6%96%b9%e7%a8%8b)
      - [非齐次差分方程](#%e9%9d%9e%e9%bd%90%e6%ac%a1%e5%b7%ae%e5%88%86%e6%96%b9%e7%a8%8b)
      - [平稳时间序列的线性数学模型](#%e5%b9%b3%e7%a8%b3%e6%97%b6%e9%97%b4%e5%ba%8f%e5%88%97%e7%9a%84%e7%ba%bf%e6%80%a7%e6%95%b0%e5%ad%a6%e6%a8%a1%e5%9e%8b)

# Time_Series_Analysis

## Chapter 1 时间序列

### 1.2 平稳序列

👉 时间序列定义

若随机过程的参数集$\,T\in N \,or\, T\in Z\,$,称该过程为时间序列

当固定$\,t\,$,重复试验都到的数据称为**横剖面数据(截口数据，静态数据)**，研究这类数据的统计方法是**统计分析**

**横剖面数据**总体$\,X\,$是一个随机变量，总体的样本是独立同分布的一组随机向量，样本的观察值是**独立重复实试验的结果，与时间无关**

当固定$\,\omega\,$，时间序列的一条样本函数称为**纵剖面数据(动态数据，时间序列数据)**。时间序列数据是时间序列的一条**现实**

👉 时间序列的特性

- 动态性：即系统的记忆性，某一时刻进入系统的输入对系统后继时刻行为的影响

- 本质特征：具有动态性，相邻观察值有很强的依赖性

👉 时间序列的数字特征

与随机过程一样，注意时间序列**自协方差函数**的写法$\,\gamma_X (r,s) = Cov(X_r,X_s)\,$

👉 严平稳时间序列

定义与严平稳随机过程一样——**有限维分布不随时间的推移而改变**

👉 **(宽)平稳时间序列**

满足
$$
        E\mid X_t \mid^2 < + \infty\\
        E(X_t) = m(m=constant)\\
        \gamma_X (r,s)=\gamma_X (r+t,s+t)
$$

平稳序列的自协方差函数和自相关系数函数
$$
  \gamma_X (h) = \gamma_X (h,0)=Cov(X_{t+h},X_t) \\
  \rho_X (h) = \frac{\gamma_X (h)}{\gamma_X (0)}
$$

### 1.3 时间序列的平稳化预处理

👉 平稳性的检验

- 时序图检验
- 自相关图检验

👉 纯随机性检验

👉 定义

也称**白噪声序列**，满足
$$
  E(X_t) = \mu\\
  \gamma(t,s) =\begin{cases}
    \sigma^2 ,&t=s\\
    0,&t\neq s
  \end{cases}
$$

👉 性质

- 纯随机性$\,\gamma(k)=0 \quad \forall k \neq 0\,$,即各序列值之间没有任何相关关系，**没有记忆性**的序列
- 方差齐性$\,D(X_t)=\gamma(0)=\sigma^2\,$

👉 检验原理

如果一个时间序列是**纯随机的**，得到一个观察期为$\,n\,$的观察序列，则该序列**延迟非零期**的样本自相关系数近似服从**均值为0，方差为序列观察期数倒数的正态分布**
$$
  \rho_k \sim N(0,\frac{1}{n})\quad \forall k \neq 0
$$

👉 假设条件：

原假设：延迟期数小于或等于$\,m\,$期的序列值之间相互独立
$$
  H_0 : \rho_1 = \rho_2 = \cdots = \rho_m = 0, \quad \forall m \geq 1
$$

备择假设:
$$
  H_1 : \exist \rho_k \neq 0 ,\quad \forall m \geq 1 , k\leq m
$$

👉 检验统计量

Q统计量：

$$
  Q = \sum_{k=1}^{m} (\frac{\rho_k}{\sqrt{\frac{1}{n}}})^2 \sim \chi^2 (m)
$$

LB统计量：

$$
  LB=n(n+2)\sum_{k=1}^{m}(\frac{\rho_k^2}{n-k}) \sim \chi^2(m)
$$

👉 判别原则

拒接原假设：

当检验统计量大于$\,\chi^2_{1-\alpha}(\alpha)\,$分位点，或统计量的$\,P\,$值小于$\,\alpha\,$时，则可以以$\,1-\alpha\,$的置信水平拒绝原假设，认为该序列是非白噪声序列

接收原假设：

当检验统计量小于$\,\chi^2_{1-\alpha}(\alpha)\,$分位点，或统计量的$\,P\,$值大于$\,\alpha\,$时，则可以以$\,1-\alpha\,$的置信水平接收原假设，认为该序列是白噪声序列

[关于显著性水平和P-Value的链接](https://www.zhihu.com/question/23680352/answer/144892542)

👉 非平稳时间序列

- 均值非常数类非平稳序列
- 周期类非平稳序列
- 异方差类非平稳序列
- 混合类非平稳序列

建模思路：

- 选择适当的模型对序列进行**拟合**
- 对数据进行**平稳化预处理**

👉 一般非平稳时间序列的分解

大量时间序列观察样本都表现出**趋势性，季节性(周期性)和随机型**，可以分解为
$$
  X_t = m_t + s_t + Y_t\\
  m_t是趋势项，一般是实值函数\\
  S_t是季节项，周期为s的周期函数\\
  Y_t是平稳随机噪声项(残量)\\
  其中前两项是非随机的确定性成份
$$

分解的目的：**使噪声项成为平稳序列**

假定上述分解式满足
$$
  \begin{cases}
    E(Y_t) = 0 \\
    \sum_{j=1}^{s} s_{t+j} = C
  \end{cases}
$$

👉 趋势项和季节项的估计和分离

👉 **仅含趋势项**的识别与剔除$\,X_t = m_t + Y_t\,$

最小二乘法——拟合均值函数并将过程零均值化

滑动平均平滑方法——以直代曲，平滑数据，消去噪声项

- 取非负整数$\,q\,$
- 求$\,X_t = m_t + Y_t\,$的双边滑动平均$\,W_t = \frac{1}{2q+1}\sum_{j=-q}^{q}X_{t+j}\quad X_t及前后相邻2q个数据的算术平均值$
- 令$\,m_t = W_t\,$

### 1.4 推移算子及数据预处理

👉 推移算子和差分算子

👉 推移算子$\,B\,$:$\,BX_t = X_{t-1}\,$

性质

$$
  BY= Y\\
  B^n(aX_t) = aB^n X_t = aX_{t-n}\\
  B^{n+m}X_t  =B^nB^mX_t = X_{t-n-m}\\
  对于多项式 \psi(z) = \sum_{j=0}^{p} c_jz^j有\,\psi(B)X_t = \sum_{j=0}^{p} c_jX_{t-j}\\
  对多项式 \psi(z) = \sum_{j=0}^{p} c_jz^j和\phi(z) = \sum_{j=0}^{p} d_jz^j的乘积A(z)=\psi(z)\phi(z)有 A(B)X_t = \psi(B)[\phi(B)X_t]=\phi(B)[\psi(B)X_t]\\
  对时间序列\{X_t\},\{Y_t\},多项式\psi(z) = \sum_{j=0}^{p} c_jz^j以及随机变量U,V,W有 \psi(B)(UX_t+VY_t+W)= U\psi(B)X_t+V\psi(B)Y_t+W\psi(1) \quad \text{为啥这里是}\psi(1)
$$

👉 差分算子$\,\nabla\,$:$\,\nabla X_t = X_t - X_{t-1} = (1-B)X_t\,$

差分算子的幂运算
$$
  \nabla^j (X_t) = \nabla(\nabla^{j-1}(X_t)) = (1-B)^j X_t\\
  \nabla^0 (X_t) = X_t
$$

👉 **延迟$\,d\,$步**差分算子$\,\nabla_d\,$ (与差分算子的$\,d\,$次幂不同)
$$
  \nabla_d X_t = X_t - X_{t-d} = (1-B^d)X_t
$$

👉 推移算子和差分算子进行**序列分解**

基本思想：用差分方法删除趋势项 不断差分，直到趋势项为常数

👉 Ex
$$
  设X_t = m_t + Y_t= at+b+Y_t\\
  \begin{aligned}
    \nabla X_t &= X_t - X_{t-1}\\
    &= a + Y_t - Y_{t-1}\\
    &= a+ \nabla Y_t\\
    \nabla^2 (X_t) &= \nabla(\nabla (X_t))\\
    &= \nabla(a) + \nabla^2(Y_t)\\
    &= \nabla^2(Y_t)
  \end{aligned}\\
$$

👉 若序列$\,X_t = m_t + Y_t\,$中的趋势项为$\,m_t  =\sum_{j=0}^{k} a_jt^j\,$,$\,\{Y_t\}\,$是零均值平稳过程，则
$$
  k阶差分算子作用于k次多项式的趋势项，结果是常数\\
  \nabla^k m_t = \nabla^k (\sum_{j=0}^{k} a_jt^j) = k!a_k\\
  \nabla^k X_t = k!a_k + \nabla^k Y_t\\
  \Rightarrow X_t的k阶差分是均值为k!a_k的平稳过程
$$

👉 平稳过程差分后仍是平稳过程

👉 差分方法也可以适用于含有季节项

设序列$\,X_t = m_t + +s_t + Y_t\,$周期为$\,d\,$,可以用延迟d步差分法剔除季节项
$$
  \nabla_d (X_t) = (m_t-m_{t-d}) + (Y_t - Y_{t-d})
$$

## Chapter 2 线性平稳过程

### 2.1 一般线性过程

#### 白噪声

👉 最常用的平稳序列是线性平稳序列——由白噪声的**线性组合**构成的平稳序列

👉 白噪声定义
$$
  \{\varepsilon_t,t\in Z\}是零均值序列且自相关函数满足\\
  r(h) = \begin{cases}
    \sigma^2_\varepsilon ,&h=0\\
    0,&h\neq 0
  \end{cases}
$$
若$\, \{\varepsilon_t,t\in Z\}\,$是正态时间序列，则称为正态白噪声($\,WN(0,\sigma^2)\,$)

若存在$\,q\geq 0\,$和常数$\,a_0,a_1,\cdots,a_q\,$，使时间序列可以表示为
$$
  X_t = a_0\varepsilon_t + a_1\varepsilon_{t-1} + \cdots + a_q\varepsilon_{t-q}
$$
👆式称为序列的白噪声滑动平均

👉 可将$\,\{X_t\}\,$视为线性滤波器的输出，白噪声堪称驱动系统的扰动序列(激励)

#### 线性过程的两种等价形式

- 传递形式

将顺序值之间高度依赖的时间序列看成由**一系列独立“冲击”序列**生成。

通常将“冲击”序列理想化为白噪声过程，时间序列即为白噪声的线性组合

👉 Wold分解式(正交分解)
$$
  任意零均值纯非确定的平稳过程都可表示为线性形式\\
  X_t = \sum_{j=0}^{\infty} \varphi_j \varepsilon_{t-j} \,t\in Z \quad i.e.白噪声的无穷阶滑动平均\\
  权系数\{\varphi_j,j=0,1,2,\cdots\},\varphi_0 = 1\\
  称为沃尔德系数
$$
👆可以表示为算子形式(算子级数)
$$
  X_t = \varphi(B)\varepsilon_t
$$
其中$\,\varphi(B)\,$称为沃尔德系数的**生成函数**或传递函数

- 自回归形式

$$
  在适当条件下 \{X(t),t\in Z\}可以表示为\\
  X_t = \varepsilon_t + \sum_{j=1}^\infty \pi_j X_{t-j},\,t \in Z\\
  也可这样表示\\
  \varepsilon_t = (1-\sum_{j=1}^\infty \pi_j B^j)X_t = \pi(B)X_t
$$

- $\,\varepsilon_t =\pi(B)X_t\,$和$\,X_t = \varphi(B)\varepsilon_t\,$互为逆转形式 有$\,\pi(B)=\varphi(B)^{-1}\,$

#### 线性过程的均值函数与自协方差函数

👉 Levi单调收敛定理
$$
  若非负随机变量序列单调不减，则当X_n\rightarrow X\,a.s.s时\\
  \lim_{n\rightarrow \infty} E(X_n) = E(X)
$$
👉 控制收敛定理
$$
  若随机变量序列满足|X_n| \neq X_0,a.s.和E|X_0|<\infty\\
  当X_n \rightarrow X,a.s.时，有E(|X|)<\infty且\lim_{n\rightarrow \infty} E(X_n) = E(X)
$$

👉
$$
  时间序列满足sup_tE|X_t| < + \infty(sup是最小上界),如果 \sum_{j=-\infty}^{+\infty} |\psi_j| < +\infty,则序列\\
  \psi(B)X_t = \sum_{j=-\infty}^{+\infty} \psi_jB^jX_t = \sum_{j=-\infty}^{+\infty} \psi_j X_{t-j}依概率1收敛
$$

👉
$$
  线性过程X_t=\varphi(B)\varepsilon_t,若传递函数绝对可和\sum_{j=0}^{\infty} < \infty,则\\
  E(X_t) = 0,自相关函数为r(k) = \sigma^2_\varepsilon \sum_{j=0}^\infty \phi_j \phi_{j+k}
$$

#### 线性过程的平稳过程

👉 线性过程满足以下条件之一，序列具有平稳性

- 沃尔德系数绝对可和$\,\sum_{j=0}^{\infty} < \infty\,$
- 沃尔德系数生成函数$\,\varphi(z)=\sum_{j=0}^\infty \varphi_j z^j\,$当$\,|z|\leq 1\,$时收敛——在单位圆上或单位圆内级数收敛

#### 线性过程的可逆性条件

👉 什么条件下，线性过程的加权和表示白噪声序列
$$
  若存在常数序列\{\pi_j\}，满足\\
  \sum_{j=0}^{\infty} < \infty 使\\
  \varepsilon_t = \sum_{j=0}^{\infty} \pi_j X_{t-j}
$$
称平稳线性过程是可逆的

### 2.2 平稳序列的线性数学模型

#### 常系数齐次线性差分方程

👉 定义
$$
  给定实数a_1,a_2,\cdots,a_p \neq 0,称\\
  X_t - [a_1X_{t-1}+a_2X_{t-2}+\cdots+a_pX_{t-p}] = 0 ,t \in Z\\
  为p阶常系数齐次线性(随机)差分方程
$$
该方程的解$\,\{X(t)\}\,$可由$\,p\,$个初值$\,X_0,X_1,\cdots,X_{p-1}\,$递推得到

该方程的算子等价形式为
$$
  A(B)X_t = ,0 t \in Z\\
  其中A(z) = 1 - \sum_{j=1}^{p} a_jz^j\,称为👆方程的特征多项式
$$

👉 定理
$$
  特征多项式有k个互不相同的零点z_1,z_2,\cdots,z_k,其中z_j是r(j)重零点，则\\
  {z_j^{-t}t^l},l=0,1,\cdots,r(j)-1;j=1,2,\cdots,k\\
  是差分方程的k个线性无关解，且其任何解均可以表示为通解形式：\\
  X_t = \sum_{j=1}^{k}\sum_{l=0}^{r(j)-1} U_{l,j}t^lz_j^{-t},t\in Z\\
  其中随机变量U_{l,j}由初值唯一确定\\
  满足差分方程的实值时间序列可表示为\\
  X_t = \sum_{j=1}^{k}\sum_{l=0}^{r(j)-1} U_{l,j}t^l\rho_j^{-t}cos(\lambda_j t -\theta_{l,j}),t\in Z
$$

👉 定理
$$
  特征多项式的k个相异根有\\
  ①\,若全部根都在单位圆外，差分方程的任何解以负指数律收敛到零\\
  ②\,若单位元上存在根，差分方程有周期解\\
  ③\,若存在单位圆内的根，差分方程有发散解
$$

#### 非齐次差分方程

👉 定义
$$
  A(B)X_t = Y_t ,t \in Z \quad Y_t是实值时间序列
$$
通解为
$$
  X_t = X_t^{(0)} + \sum_{j=1}^{k}\sum_{l=0}^{r(j)-1} U_{l,j}t^lz_j^{-t},t\in Z
$$

#### 平稳时间序列的线性数学模型

👉 **一阶动态性**——系统的输入只影响**下一时刻的行为**

👉引理
$$
  谱分布函数可分解为\\
  F(x) = \varphi(x) + r(x) + s(x)\\
  \varphi(x) 是绝对连续函数\\
  r(x)是阶梯形跳跃函数\\
  r(x)是奇异函数
$$
若有
$$
  F(x) = \varphi(x),则称序列具有纯连续谱
$$
纯连续谱中最具有广泛意义的是**有理谱密度**

👉引理
$$
  一个具有纯连续谱的零均值平稳时间序列具有有理谱密度的充要条件是X_t满足线性差分方程\\
  \Phi(B)X_t = \Theta(B)\varepsilon_t
$$
其中
$$
  \Phi(z) = 1- \varphi_1 z - \cdots - \varphi_p z^p\quad p阶自回归多项式(AR) \\
  \Theta(z) = 1 + \theta_1 z  + \cdots + \theta_q z^q \quad q次滑动平均多项式(MA)
$$
👉 ARMA过程
$$
  零均值平稳序列,\forall t 满足线性差分方程\\
  \Phi(B)X_t = \Theta(B)\varepsilon_t\\
  其中\{\varepsilon_t\}是WN(0,\sigma^2),实系数多项式\Phi(z)和\Theta(z)没有公共根，且\\
  \Phi(z) = 1- \varphi_1 z - \cdots - \varphi_p z^p,\varphi_p \neq 0\\
  \Theta(z) = 1 + \theta_1 z  + \cdots + \theta_q z^q,\theta_q \neq 0\\
  称X_t为ARMA(p,q)过程
$$
👉 P阶自回归模型(AR(p))
$$
  若\Theta(z) = 1,\Rightarrow \Phi(B)X_t = \varepsilon_t\\
  X_t = \varphi_1X_{t-1}+\cdots+\varphi_pX_{t-p}+\varepsilon_t\\
  即X_t(当前值)=自身过去值的线性组合+\varepsilon_t
$$
要注意，在AR模型中白噪声$\,\varepsilon_t\,$不仅会直接影响当前值，还会对将来所有值产生影响

Ex. 单摆运动
$$
  X_t = aX_{t-1} + \varepsilon_t
$$
是一阶自回归模型(AR(1))

👉 q次滑动平均模型(MA(q))
$$
  若\Phi(z) = 1, \Rightarrow X_t = \Theta(B)\varepsilon_t \quad 线性过程传递形式\\
  X_t = \varepsilon_t + \theta_1\varepsilon_{t-1}+\cdots+\theta_q\varepsilon_{t-q}\\
  X_t(当前值) = 有限个过去值\varepsilon_t,\cdots,\varepsilon_{t-q}的线性组合+\varepsilon_t(当前值)
$$
注意，在MA模型中，白噪声$\,\varepsilon_t\,$仅对q个将来值产生影响