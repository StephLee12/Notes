- [Time Series Analysis](#time-series-analysis)
  - [Chapter 3 平稳序列的数字特征及其估计](#chapter-3-%e5%b9%b3%e7%a8%b3%e5%ba%8f%e5%88%97%e7%9a%84%e6%95%b0%e5%ad%97%e7%89%b9%e5%be%81%e5%8f%8a%e5%85%b6%e4%bc%b0%e8%ae%a1)
    - [3.1 平稳序列的均值及估计](#31-%e5%b9%b3%e7%a8%b3%e5%ba%8f%e5%88%97%e7%9a%84%e5%9d%87%e5%80%bc%e5%8f%8a%e4%bc%b0%e8%ae%a1)
      - [能否用一条现实求得$\,m_t\,$的良好估计](#%e8%83%bd%e5%90%a6%e7%94%a8%e4%b8%80%e6%9d%a1%e7%8e%b0%e5%ae%9e%e6%b1%82%e5%be%97math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmtext-mtextmsubmimmimitmimsubmtext-mtextmrowannotation-encoding%22applicationx-tex%22mtannotationsemanticsmathmt%e2%80%8b%e7%9a%84%e8%89%af%e5%a5%bd%e4%bc%b0%e8%ae%a1)
      - [估计量的统计性质](#%e4%bc%b0%e8%ae%a1%e9%87%8f%e7%9a%84%e7%bb%9f%e8%ae%a1%e6%80%a7%e8%b4%a8)
      - [估计量的渐进分布](#%e4%bc%b0%e8%ae%a1%e9%87%8f%e7%9a%84%e6%b8%90%e8%bf%9b%e5%88%86%e5%b8%83)
      - [样本长度](#%e6%a0%b7%e6%9c%ac%e9%95%bf%e5%ba%a6)
    - [3.2 ARMA序列自协方差函数及计算](#32-arma%e5%ba%8f%e5%88%97%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0%e5%8f%8a%e8%ae%a1%e7%ae%97)
      - [自协方差函数回顾](#%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0%e5%9b%9e%e9%a1%be)
      - [ARMA(p,q)的自协方差函数](#armapq%e7%9a%84%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0)
      - [MA(q)的自协方差函数](#maq%e7%9a%84%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0)
      - [AR(p)的自协方差函数](#arp%e7%9a%84%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0)
      - [自协方差函数的允许域](#%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0%e7%9a%84%e5%85%81%e8%ae%b8%e5%9f%9f)
    - [3.3 自协方差函数的估计](#33-%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0%e7%9a%84%e4%bc%b0%e8%ae%a1)
      - [自协方差函数估计量](#%e8%87%aa%e5%8d%8f%e6%96%b9%e5%b7%ae%e5%87%bd%e6%95%b0%e4%bc%b0%e8%ae%a1%e9%87%8f)
      - [估计量的优良性](#%e4%bc%b0%e8%ae%a1%e9%87%8f%e7%9a%84%e4%bc%98%e8%89%af%e6%80%a7)
      - [估计量的渐进分布(为啥会有重复标题2333)](#%e4%bc%b0%e8%ae%a1%e9%87%8f%e7%9a%84%e6%b8%90%e8%bf%9b%e5%88%86%e5%b8%83%e4%b8%ba%e5%95%a5%e4%bc%9a%e6%9c%89%e9%87%8d%e5%a4%8d%e6%a0%87%e9%a2%982333)
    - [3.4 ARMA序列的偏相关函数](#34-arma%e5%ba%8f%e5%88%97%e7%9a%84%e5%81%8f%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0)
      - [偏相关函数定义](#%e5%81%8f%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0%e5%ae%9a%e4%b9%89)
      - [预报系数的直接算法](#%e9%a2%84%e6%8a%a5%e7%b3%bb%e6%95%b0%e7%9a%84%e7%9b%b4%e6%8e%a5%e7%ae%97%e6%b3%95)
      - [预报系数的递推算法](#%e9%a2%84%e6%8a%a5%e7%b3%bb%e6%95%b0%e7%9a%84%e9%80%92%e6%8e%a8%e7%ae%97%e6%b3%95)
      - [AR(p)序列偏相关函数的截尾性](#arp%e5%ba%8f%e5%88%97%e5%81%8f%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0%e7%9a%84%e6%88%aa%e5%b0%be%e6%80%a7)
      - [MA，ARMA序列偏相关函数的拖尾性](#maarma%e5%ba%8f%e5%88%97%e5%81%8f%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0%e7%9a%84%e6%8b%96%e5%b0%be%e6%80%a7)
      - [时间序列分类性质总结](#%e6%97%b6%e9%97%b4%e5%ba%8f%e5%88%97%e5%88%86%e7%b1%bb%e6%80%a7%e8%b4%a8%e6%80%bb%e7%bb%93)
      - [平稳时间序列的偏相关函数的估计](#%e5%b9%b3%e7%a8%b3%e6%97%b6%e9%97%b4%e5%ba%8f%e5%88%97%e7%9a%84%e5%81%8f%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0%e7%9a%84%e4%bc%b0%e8%ae%a1)

# Time Series Analysis

## Chapter 3 平稳序列的数字特征及其估计

### 3.1 平稳序列的均值及估计

#### 能否用一条现实求得$\,m_t\,$的良好估计

平稳的随机过程的均值具有**均方遍历性**时，可以用时间平均代替统计平均
$$
  \hat{m_t} = \overline{X_N} = \frac{1}{N}\sum_{t=1}^{N}X_t
$$

👉 若时间序列是严平稳的

👉 定理
$$
  若\varepsilon_t \sim WN(0,\sigma^2),实数列a_j平方可和，则线性平稳序列\\
  X_t = \sum_{j=0}^{\infty} a_j \varepsilon_{t-j}\\
  是严平稳遍历的
$$

$$
  若X_t是严平稳遍历序列，则对任意多元函数\phi(x_1,x_2,\cdots,x_m)\\
  Y_t = \phi(X_{t-1},X_{t-2},\cdots,X_{t-m})
   \quad i.e.这是传递形式\\
  是严平稳遍历序列
$$

$$
  若X_t是严平稳遍历序列，则X_tX_{t+k}也是严平稳遍历序列
$$

#### 估计量的统计性质

👉 无偏估计
$\,\overline{X_N}是m_X的无偏估计量\,$

👉 相合估计

$$1.\quad 若X_t是严平稳的遍历序列，且E(|X_t|) < \infty\\
则\overline{X_N}是m_X的强相合估计量(即依概率1收敛)$$

$$
2. ①\quad 若(宽)平稳序列的自协方差函数\gamma(N) \rightarrow 0(当N \rightarrow \infty时)\\
即平稳序列是均值遍历的，则方差\\
Var[\overline{X_N}] = E[\overline{X_N} - m_X]^2 \rightarrow 0\\
即\overline{X_N}是均方收敛于m_X,故依概率收敛于m_X\\
所以\overline{X_N}是m_X的(弱)相合估计量
$$

$$
  2.②若(宽)平稳序列的自协方差函数绝对可和\sum_{h=-\infty}^{\infty} | \gamma(h) | < \infty\\
  则 N \times Var[\overline{X_N}] \rightarrow \sum_{h=-\infty}^{\infty} | \gamma(h) |\\
  根据👆，利用中心极限定理，可以认为时间估计服从\\
  均值为m_X方差为\frac{\sum_{h=-\infty}^{\infty} | \gamma(h) |}{N}的正态分布\\
$$

由2.②可推得公式
$$
  \begin{aligned}
     N \times Var[\overline{X_N}] &= \sum_{|h|<N} (1-\frac{|h|}{N}) \gamma(h) \\
     &= \gamma(0) + 2\sum_{h=1}^{N-1} (1-\frac{|h|}{N}) \gamma(h)\\
     &=\gamma(0)[1+2\sum_{h=1}^{N-1} (1-\frac{|h|}{N}) \rho(h)]\quad i.e \,\rho(h)是自相关系数函数
  \end{aligned}
$$

#### 估计量的渐进分布

$$
  平稳线性序列X_t = m_X  + \sum_{k= -\infty}^{\infty} \varphi_j \varepsilon_{t-j} \\
  若\sum_{k=-\infty}^{\infty} |\varphi_j| < \infty,\sum_{k=-\infty}^{\infty} \varphi_j \neq 0\\
  则\overline{X_N}渐进服从正态分布N(m_X,\frac{\sum_{h=-\infty}^{\infty} | \gamma(h) |}{N})
$$
但存在问题，如何根据**一条现实**估计出**自协方差函数**

#### 样本长度

### 3.2 ARMA序列自协方差函数及计算

#### 自协方差函数回顾

👉 因为研究的一般是**零均值的时间序列**，所以对**自相关函数**和**自协方差函数**不作区分

👉 平稳序列自相关函数性质(回顾)

- 非负性 $\,\gamma(0) \geq 0\,$
- 有界性 $\,|\gamma(h)| \leq \gamma(0)\,$
- 对称性 $\,\gamma(h) = \gamma(-h)\,$
- 非负定性

#### ARMA(p,q)的自协方差函数

👉 回顾
$$
  Wold分解\quad 任意零均值纯平稳过程都可以表示为线性形式\\
  X_t = \sum_{j=0}^{\infty} \varphi_j \varepsilon_{t-j}\\
  其自相关函数为\\
  r(k) = \sigma_\varepsilon^2 \sum_{j=0}^{\infty} \varphi_j \varphi_{j+k}\\
  自相关系数函数为\\
  \rho(k) = \frac{\sum_{j=0}^{\infty} \varphi_j \varphi_{j+|h|}}{\sum_{j=0}^{\infty} \varphi_j^2}
$$
由于Wold系数在**平稳域**内是**负指数衰减**的，所以ARMA序列的自协方差函数在平稳域内也必定是负指数衰减的

👉 若一个随机序列的自协方差函数不是**负指数衰减**，可以判定它不适宜用ARMA模型描述

👉 计算

- 内积法

👉 引理
$$
    若ARMA序列有因果性,则\\
      \begin{aligned} 若s > t ,Cov(\varepsilon_sX_t)=E[\varepsilon_sX_t]&= E[\varepsilon_s \sum_{j=0}^{\infty} \varphi_j \varepsilon_{t-j}]\\
      &= \sum_{j=0}^{\infty} \varphi_j E[\varepsilon_s \varepsilon_{t-j}]\\
      & = 0
  \end{aligned}
$$
$$
\begin{aligned}
    若s\leq t,E[\varepsilon_sX_t] &= \sum_{j=0}^{\infty} E[\varepsilon_s \varepsilon_{t-j}] \\
    &= \varphi_{t-s} \sigma^2_\varepsilon
  \end{aligned}
$$
👉 定理

$对于因果ARMA(p,q)模型，序列的自协方差函数满足方程组$ ![ARMA自协方差函数](..\captures\ARMA自协方差函数.PNG "ARMA自协方差函数")

👉 Ex
![ARMA自协方差函数2](..\captures\ARMA自协方差函数2.PNG "ARMA自协方差函数2")

![ARMA自协方差函数3](..\captures\ARMA自协方差函数3.PNG "ARMA自协方差函数3")

![ARMA自协方差函数4](..\captures\ARMA自协方差函数4.PNG "ARMA自协方差函数4")

![ARMA自协方差函数5](..\captures\ARMA自协方差函数5.PNG "ARMA自协方差函数5")

👉 ARMA自协方差函数具有**拖尾性**，即呈**负指数衰减**

- 递推法

![递推法1](..\captures/递推法1.png "递推法1")

![递推法2](..\captures/递推法2.png "递推法2")

#### MA(q)的自协方差函数

![MA自协方差函数](..\captures/MA自协方差函数.png "MA自协方差函数")

![MA自协方差函数2](..\captures/MA自协方差函数2.png "MA自协方差函数2")

![MA自协方差函数3](..\captures/MA自协方差函数3.png "MA自协方差函数3")

#### AR(p)的自协方差函数

👉 与ARMA(p,q)一样，具有**拖尾性**

#### 自协方差函数的允许域

👉 成为ARMA序列的自协方差函数需要满足

- 对称性
- 正定性
- 对应模型具有平稳性和可逆性

👉 **定义** ：使ARMA模型具有平稳可逆性的前**p+q+1**个自协方差函数所能取值的范围称为它们的**允许域**。

因为前p+q+1个自协方差函数能够解出$\,\varphi_1,\cdots,\varphi_p和\theta_1,\cdots,\theta_q,\sigma^2\,$,从而判断是否落在平稳域和可逆域

👉 Ex1

![允许域Ex1.1](..\captures/允许域Ex1.1.png "允许域Ex1.1")

![允许域Ex1.2](..\captures/允许域Ex1.2.png "允许域Ex1.2")

![允许域Ex2.1](..\captures/允许域Ex2.1.png "允许域Ex2.1")

![允许域Ex2.2](..\captures/允许域Ex2.2.png "允许域Ex2.2")

![允许域Ex2.3](..\captures/允许域Ex2.3.png "允许域Ex2.3")

### 3.3 自协方差函数的估计

#### 自协方差函数估计量

![自协方差函数估计量](..\captures/自协方差函数估计量.png "自协方差函数估计量")

第一个是有偏估计量 第二个是无偏估计量

👉 如何确定样本长度N和h

$$
  Box-Jenkins准则 \quad 一般h = N/10
$$

👉 讨论两个估计量

为了能够套用**AR MA ARMA**模型，希望样本的自协方差函数以很快的速度衰减到0(因为MA模型是截尾的 AR和ARMA是拖尾的 但都可以认为收敛到0)

- 估计量2的优势是**无偏**
- 估计量1的优势是**收敛到0的速度更快**
- 但是对于较大的N和绝对值较小的h，两个的精度相差不大
- 更关键的是 **估计量1矩阵是正定的，估计量2矩阵不能保证正定性**(本质性质)

常选用**估计量1**，下面默认采用该估计量

#### 估计量的优良性

$$
  若X_t是平稳遍历随机序列\\
  估计量是相合估计量，即依概率收敛到\gamma(h)\\
  估计量是渐进无偏估计量\\
  若X_t是严平稳遍历随机序列，估计量是强相合估计量,即依概率1收敛到\gamma(h)
$$

#### 估计量的渐进分布(为啥会有重复标题2333)

![自协方差函数渐进分布1](..\captures/自协方差函数渐进分布1.png "自协方差函数渐进分布1")

![自协方差函数渐进分布2](..\captures/自协方差函数渐进分布2.png "自协方差函数渐进分布2")

![自协方差函数渐进分布3](..\captures/自协方差函数渐进分布3.png "自协方差函数渐进分布3")

👉 Bartlett公式

![bartlett公式1](..\captures/bartlett公式1.png "bartlett公式1")

![bartlett公式2](..\captures/bartlett公式2.png "bartlett公式2")

![bartlett公式应用1](..\captures/bartlett公式应用1.png "bartlett公式应用1")

![bartlett公式应用2](..\captures/bartlett公式应用2.png "bartlett公式应用2")

### 3.4 ARMA序列的偏相关函数

👉 由于MA模型的自相关函数是**截尾的**，所以很容易区分，但是AR和ARMA模型的自相关函数都是拖尾的，因此引入了偏相关函数来区分AR和ARMA

#### 偏相关函数定义

- 称$\,\hat{E} = [X_t | X_{t-1},\cdots,X_{t-k}] = \hat{=} \sum_{j=1}^{k} \phi_{kj}X_{t-j}\,$为$\,X_t\,$的**线性预报量**，称$\,\phi_{k1},\phi_{k2},\cdots,\phi_{kk}\,$为**预报系数**，$\,\phi_{kk}\,$是第k步**偏相关值**，序列$\,\{\phi_{kk}\}\,$为$\,X_t\,$的偏相关函数
- $\,X_{t-1},X_{t-2},\cdots,X_{t-k}\,$是关于$\,X_t\,$的**最小方差线性估计
- 序列$\,\phi_{kj}\,$标明了$\,X_{t-j}\,$对$\,X_t\,$的**线性贡献程度

#### 预报系数的直接算法

![预报系数直接算法](..\captures/预报系数直接算法.png "预报系数直接算法")

#### 预报系数的递推算法

👉 Yule-Walker线性方程组

![预报系数递推算法](..\captures/预报系数递推算法.png "预报系数递推算法")

👉 若用自相关函数表示 则为

![预报系数递推算法2](..\captures/预报系数递推算法2.png "预报系数递推算法2")

👉 计算困难 有递推公式

![预报系数递推算法3](..\captures/预报系数递推算法3.png "预报系数递推算法3")

👉 递推公式流程图

![预报系数递推算法4](..\captures/预报系数递推算法4.png "预报系数递推算法4")

#### AR(p)序列偏相关函数的截尾性

- $\,平稳零均值序列为p阶自回归序列的充要条件是它的偏相关函数p步截尾\,$

#### MA，ARMA序列偏相关函数的拖尾性

- **可逆**的MA，ARMA序列偏相关函数满足$\,|\phi_{kk}| < g_1e^{-g_2k},g_1>0,g_2>0\,$，即具有拖尾性

#### 时间序列分类性质总结

![时间序列分类](..\captures/时间序列分类.png "时间序列分类")

![时间序列分类2](..\captures/时间序列分类2.png "时间序列分类2")

#### 平稳时间序列的偏相关函数的估计

👉 思想：由样本自相关函数的估计求样本偏相关函数的估计

👉 将Yule-Walker线性方程组中的自相关函数换为估计量，有一样的递推公式

👉 对于平稳正态序列

- $\,\hat{\phi_{kk}}\,$是$\,\phi_{kk}\,$的**渐近无偏估计量**和相合估计量
- $\,\hat{\phi_{kk}}\,$渐近服从正态分布，且N足够大时，方差为1/N
