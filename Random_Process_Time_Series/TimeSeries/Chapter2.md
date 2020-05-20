- [Time Series Analysis](#time-series-analysis)
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
    - [2.3 ARMA序列的因果可逆性](#23-arma%e5%ba%8f%e5%88%97%e7%9a%84%e5%9b%a0%e6%9e%9c%e5%8f%af%e9%80%86%e6%80%a7)
      - [ARMA模型平稳解的存在唯一性](#arma%e6%a8%a1%e5%9e%8b%e5%b9%b3%e7%a8%b3%e8%a7%a3%e7%9a%84%e5%ad%98%e5%9c%a8%e5%94%af%e4%b8%80%e6%80%a7)
      - [ARMA序列的因果性](#arma%e5%ba%8f%e5%88%97%e7%9a%84%e5%9b%a0%e6%9e%9c%e6%80%a7)
      - [ARMA序列的可逆性](#arma%e5%ba%8f%e5%88%97%e7%9a%84%e5%8f%af%e9%80%86%e6%80%a7)
    - [2.4 ARMA模型的平稳域和可逆域](#24-arma%e6%a8%a1%e5%9e%8b%e7%9a%84%e5%b9%b3%e7%a8%b3%e5%9f%9f%e5%92%8c%e5%8f%af%e9%80%86%e5%9f%9f)

# Time Series Analysis

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
其中$\,\varphi(B)\,$称为沃尔德系数的**生成函数**或传递函数或称**格林函数**
$$
  \varphi(B) = 1 + \sum_{j=1}^{\infty} \varphi_j B^j = \sum_{j=0}^{\infty} \varphi_j B^j
$$

- 自回归形式

$$
  在适当条件下\{X(t),t\in Z\}可以表示为\\
  X_t = \varepsilon_t + \sum_{j=1}^\infty \pi_j X_{t-j},\,t \in Z \\
  也可这样表示\\
  \varepsilon_t = (1-\sum_{j=1}^\infty \pi_j B^j)X_t = \pi(B)X_t
$$
即
$$
  \pi(B) = (1-\sum_{j=1}^\infty \pi_j B^j)
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
  线性过程X_t=\varphi(B)\varepsilon_t,若传递函数绝对可和\sum_{j=0}^{\infty} |  \varphi_j |< \infty,则\\
  E(X_t) = 0,自相关函数为r(k) = \sigma^2_\varepsilon \sum_{j=0}^\infty \varphi_j \varphi_{j+k}
$$

#### 线性过程的平稳过程

👉 线性过程满足以下条件之一，序列具有平稳性

- 沃尔德系数绝对可和$\,\sum_{j=0}^{\infty} | \varphi_j |< \infty\,$
- 沃尔德系数生成函数$\,\varphi(z)=\sum_{j=0}^\infty \varphi_j z^j\,$当$\,|z|\leq 1\,$时收敛——在单位圆上或单位圆内级数收敛

#### 线性过程的可逆性条件

👉 什么条件下，线性过程的加权和表示白噪声序列
$$
  若存在常数序列\{\pi_j\}，满足\\
  \sum_{j=0}^{\infty} | \pi_j |< \infty 使\\
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
  A(B)X_t = 0, t \in Z\\
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

👉 **特征多项式的根和差分方程的根互为倒数**

👉 **关于差分方程的求解**，[看BLOG](https://www.cnblogs.com/xuanlvshu/p/5398695.html)

👉 定理
$$
  特征多项式的k个相异根有\\
  ①\,若全部根都在单位圆外，差分方程的任何解以负指数律收敛到零\\
  ②\,若单位圆上存在根，差分方程有周期解\\
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
AR(p)模型的通解为
$$
  Y_t = \sum_{j=0}^{\infty}\varphi_j\varepsilon_{t-j} +\sum_{j=1}^{k}\sum_{l=0}^{r(j)-1} U_{l,j}t^lz_j^{-t}
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
  \Phi(z) = 1- \phi_1 z - \cdots - \phi_p z^p\quad p阶自回归多项式(AR) \\
  \Theta(z) = 1 + \theta_1 z  + \cdots + \theta_q z^q \quad q次滑动平均多项式(MA)
$$
👉 $ARMA$过程
$$
  零均值平稳序列,\forall t 满足线性差分方程\\
  \Phi(B)X_t = \Theta(B)\varepsilon_t\\
  即X_t - \phi_1X_{t-1} - \cdots - \phi_pX_{t-p} = \varepsilon_t + \theta_1 \varepsilon_{t-1} + \cdots + \theta_q\varepsilon_{t-q}\\
  其中\{\varepsilon_t\}是WN(0,\sigma^2),实系数多项式\Phi(z)和\Theta(z)没有公共根，且\\
  \Phi(z) = 1- \phi_1 z - \cdots - \phi_p z^p,\phi_p \neq 0\\
  \Theta(z) = 1 + \theta_1 z  + \cdots + \theta_q z^q,\theta_q \neq 0\\
  称X_t为ARMA(p,q)过程
$$
👉 p阶自回归模型($AR(p)$)
$$
  若\Theta(z) = 1,\Rightarrow \Phi(B)X_t = \varepsilon_t\\
  X_t = \phi_1X_{t-1}+\cdots+\phi_pX_{t-p}+\varepsilon_t\\
  即X_t(当前值)=自身过去值的线性组合+\varepsilon_t
$$
要注意，在$AR$模型中白噪声$\,\varepsilon_t\,$不仅会直接影响当前值，还会对将来所有值产生影响

Ex. 单摆运动
$$
  X_t = aX_{t-1} + \varepsilon_t
$$
是一阶自回归模型($AR(1)$)

👉 q次滑动平均模型($MA(q)$)
$$
  若\Phi(z) = 1, \Rightarrow X_t = \Theta(B)\varepsilon_t \quad 线性过程传递形式\\
  X_t = \varepsilon_t + \theta_1\varepsilon_{t-1}+\cdots+\theta_q\varepsilon_{t-q}\\
  X_t(当前值) = 有限个过去值\varepsilon_t,\cdots,\varepsilon_{t-q}的线性组合+\varepsilon_t(当前值)
$$
注意，在$MA$模型中，白噪声$\,\varepsilon_t\,$仅对q个将来值产生影响

### 2.3 ARMA序列的因果可逆性

#### ARMA模型平稳解的存在唯一性

👉 平稳解：

$$
  X_t满足ARMA模型且是平稳序列
$$

Ex.单摆运动

对于单摆运动，不同a值对振幅变化是否有影响？

单摆运动是稳定系统的充要条件是特征多项式
$$
  \varPhi(z) = 1 -az的根z_1 = \frac{1}{a}在单位圆外
$$

👉 $MA(q)$模型有唯一的平稳解

👉 $AR(1)$模型有平稳解的充要条件是$\,| \varphi_1 | < 1\,$
，即特征多项式的根在单位圆外

👉 $AR(p)$模型有平稳解的充要条件是

$p阶多项式\varPhi(z)=0的根全在单位圆外\,$,多项式系数所满足的范围称为**平稳域**

注意：线性过程的传递形式(白噪声无穷阶滑动平均)与自回归形式互为逆转形式。

故线性过程要保证传递形式的**沃尔德系数绝对可和**或**格林函数的根都在单位圆内**

因自回归形式是其逆转形式，故自回归多项式的根须均落在单位圆外

#### ARMA序列的因果性

👉 若满足$ARMA(p,q)$模型的$ARMA$序列$\,X_t\,$是因果的

若存在Wold分解式
$$
  X_t = \varepsilon_t + \sum_{j=1}^{\infty} \varphi_j \varepsilon_{t-j}
$$
称其为$\,X_t\,$的因果函数

👉 显然$MA(q)$是因果的

👉 若一个时间序列满足ARMA模型，则序列是**因果ARMA序列**的充要条件是
$$
  自回归多项式的生成函数\varPhi(z)的所有根都在单位圆外 \\
  且格林函数\varphi(z)=\sum_{i=0}^{\infty} \varphi_j z^j由\frac{\Theta(z)}{\varPhi(z)}确定
$$
自回归多项式系数满足的范围称为**因果域**，显然因果域和可逆域是一样的。

可以根据👆得到格林函数的递推形式

![AR格林函数](../captures/AR格林函数.png "AR格林函数")

#### ARMA序列的可逆性

👉 若一个时间序列满足ARMA模型，则序列是**可逆ARMA序列**的充要条件是
$$
  滑动平均多项式的生成函数\Theta(z)的所有根都在单位圆外\\
  且格林函数的逆转形式\sum_{j=0}^{\infty} \pi_j z^j = \frac{\varPhi(z)}{\Theta(z)}
$$
滑动平均多项式系数满足的范围称为**可逆域**

可以根据👆得到沃尔德系数的生成函数逆转形式的递推形式

![MA格林函数逆转](../captures/MA格林函数逆转.png "MA格林函数逆转")

![MA格林函数逆转2](../captures/MA格林函数逆转2.png "MA格林函数逆转2")

### 2.4 ARMA模型的平稳域和可逆域

👉 平稳域和因果域相同

👉 AR(2)的平稳域和因果域为
$$
  \varphi_2 - \varphi_1 <1 \\
  \varphi_2 + \varphi_1 <1 \\
  | \varphi_2 | <1
$$

👉 MA(2)的可逆域为
$$
  \theta_1 +\theta_2 <1 \\
  \theta_1 - \theta_2 < 1 \\
  | \theta_2 | <1
$$
[来自blog](https://wenku.baidu.com/view/726d1719ba1aa8114431d9c8.html)

[推导见blog](https://wenku.baidu.com/view/6126f36f7e21af45b307a86c.html)

👉 JURY判别准则
$$
  对于ARMA模型\\
  若\varphi_1 < \varphi_2 < \cdots < \varphi_p < 0，则满足平稳性\\
  若\theta_1 < \theta_2 < \cdots < \theta_q < 0,则满足可逆性
$$
