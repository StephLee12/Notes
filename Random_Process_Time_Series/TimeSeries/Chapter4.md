- [Time Series Analysis](#time-series-analysis)
  - [Chapter 4 平稳序列模型参数估计](#chapter-4-%e5%b9%b3%e7%a8%b3%e5%ba%8f%e5%88%97%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e4%bc%b0%e8%ae%a1)
    - [4.1 $AR$模型参数的矩估计](#41-math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmiamimirmimrowannotation-encoding%22applicationx-tex%22arannotationsemanticsmathar%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1)
      - [$AR(p)$自回归系数的矩估计($Yule-Walker$估计)](#math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmiamimirmimo-stretchy%22false%22momipmimo-stretchy%22false%22momrowannotation-encoding%22applicationx-tex%22arpannotationsemanticsmatharp%e8%87%aa%e5%9b%9e%e5%bd%92%e7%b3%bb%e6%95%b0%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmiymimiumimilmimiemimo%e2%88%92momiwmimiamimilmimikmimiemimirmimrowannotation-encoding%22applicationx-tex%22yule-walkerannotationsemanticsmathyule%e2%88%92walker%e4%bc%b0%e8%ae%a1)
      - [$AR(p)$噪声序列方差的矩估计](#math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmiamimirmimo-stretchy%22false%22momipmimo-stretchy%22false%22momrowannotation-encoding%22applicationx-tex%22arpannotationsemanticsmatharp%e5%99%aa%e5%a3%b0%e5%ba%8f%e5%88%97%e6%96%b9%e5%b7%ae%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1)
    - [Durbin-Levinson递推估计算法](#durbin-levinson%e9%80%92%e6%8e%a8%e4%bc%b0%e8%ae%a1%e7%ae%97%e6%b3%95)
    - [4.2 $MA$模型参数的矩估计](#42-math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmimmimiamimrowannotation-encoding%22applicationx-tex%22maannotationsemanticsmathma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1)
      - [直接消元](#%e7%9b%b4%e6%8e%a5%e6%b6%88%e5%85%83)
      - [递推计算法](#%e9%80%92%e6%8e%a8%e8%ae%a1%e7%ae%97%e6%b3%95)
      - [线性迭代法(收敛速度慢)](#%e7%ba%bf%e6%80%a7%e8%bf%ad%e4%bb%a3%e6%b3%95%e6%94%b6%e6%95%9b%e9%80%9f%e5%ba%a6%e6%85%a2)
      - [Newton-Raphson法](#newton-raphson%e6%b3%95)
      - [新息估计原理](#%e6%96%b0%e6%81%af%e4%bc%b0%e8%ae%a1%e5%8e%9f%e7%90%86)
      - [MA序列参数的新息估计](#ma%e5%ba%8f%e5%88%97%e5%8f%82%e6%95%b0%e7%9a%84%e6%96%b0%e6%81%af%e4%bc%b0%e8%ae%a1)
    - [4.3 $ARMA$模型参数的初估计](#43-math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmiamimirmimimmimiamimrowannotation-encoding%22applicationx-tex%22armaannotationsemanticsmatharma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e5%88%9d%e4%bc%b0%e8%ae%a1)
      - [矩估计](#%e7%9f%a9%e4%bc%b0%e8%ae%a1)
      - [逆函数法](#%e9%80%86%e5%87%bd%e6%95%b0%e6%b3%95)
        - [基本思想](#%e5%9f%ba%e6%9c%ac%e6%80%9d%e6%83%b3)
        - [如何估计逆函数](#%e5%a6%82%e4%bd%95%e4%bc%b0%e8%ae%a1%e9%80%86%e5%87%bd%e6%95%b0)
    - [4.4 $ARMA$模型参数的精估计——最小二乘估计](#44-math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmiamimirmimimmimiamimrowannotation-encoding%22applicationx-tex%22armaannotationsemanticsmatharma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%b2%be%e4%bc%b0%e8%ae%a1%e6%9c%80%e5%b0%8f%e4%ba%8c%e4%b9%98%e4%bc%b0%e8%ae%a1)
      - [$AR$参数的最小二乘估计](#math-xmlns%22httpwwww3org1998mathmathml%22semanticsmrowmiamimirmimrowannotation-encoding%22applicationx-tex%22arannotationsemanticsmathar%e5%8f%82%e6%95%b0%e7%9a%84%e6%9c%80%e5%b0%8f%e4%ba%8c%e4%b9%98%e4%bc%b0%e8%ae%a1)
      - [ARMA和MA的最小二乘估计](#arma%e5%92%8cma%e7%9a%84%e6%9c%80%e5%b0%8f%e4%ba%8c%e4%b9%98%e4%bc%b0%e8%ae%a1)
    - [4.5 ARMA模型参数的精估计——极大似然估计](#45-arma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%b2%be%e4%bc%b0%e8%ae%a1%e6%9e%81%e5%a4%a7%e4%bc%bc%e7%84%b6%e4%bc%b0%e8%ae%a1)

# Time Series Analysis

## Chapter 4 平稳序列模型参数估计

### 4.1 $AR$模型参数的矩估计

- 对于零均值因果自回归序列，考虑**自回归系数和噪声方差的估计**

#### $AR(p)$自回归系数的矩估计($Yule-Walker$估计)

![AR自回归系数矩估计](..\captures/AR自回归系数矩估计.PNG "AR自回归系数矩估计")

![AR自回归系数矩估计2](..\captures/AR自回归系数矩估计2.PNG "AR自回归系数矩估计2")

![AR自回归系数矩估计3](..\captures/AR自回归系数矩估计3.PNG "AR自回归系数矩估计3")

#### $AR(p)$噪声序列方差的矩估计

![AR噪声序列方差矩估计](..\captures/AR噪声序列方差矩估计.PNG "AR噪声序列方差矩估计")

### Durbin-Levinson递推估计算法

![AR序列自回归系数矩估计递推](..\captures/AR序列自回归系数矩估计递推.PNG "AR序列自回归系数矩估计递推")

### 4.2 $MA$模型参数的矩估计

👉 回顾$MA$模型的自相关函数

- $MA$模型的自相关函数与$AR$、$ARMA$不同，它是截尾的

![回顾MA自协方差函数](..\captures/回顾MA自协方差函数.PNG "回顾MA自协方差函数")

👉 建立求解模型

![MA系数求解方程](..\captures/MA系数求解方程.PNG "MA系数求解方程")

#### 直接消元

👉 对于低阶MA模型，可以直接消元，但要注意**模型的可逆性**

👉 Ex

![直接消元Ex](..\captures/直接消元Ex.PNG "直接消元Ex")

![直接消元Ex2](..\captures/直接消元Ex2.PNG "直接消元Ex2")

#### 递推计算法

#### 线性迭代法(收敛速度慢)

![MA线性迭代法1](..\captures/MA线性迭代法1.PNG "MA线性迭代法1")

![MA线性迭代法2](..\captures/MA线性迭代法2.PNG "MA线性迭代法2")

#### Newton-Raphson法

#### 新息估计原理

![MA新息估计1](..\captures/MA新息估计1.PNG "MA新息估计1")

![MA新息估计2](..\captures/MA新息估计2.PNG "MA新息估计2")

#### MA序列参数的新息估计

![MA新息估计3](..\captures/MA新息估计3.PNG "MA新息估计3")

![MA新息估计4](..\captures/MA新息估计4.PNG "MA新息估计4")

### 4.3 $ARMA$模型参数的初估计

#### 矩估计

👉 回顾[第三章计算自相关函数](Chapter3.md)

![captures](../captures/ARMA矩估计1.PNG "captures")

- 当$\,k > q\,$时，建立$\,p\,$个方程，即$\,k\,$从$\,q+1\,$开始取，可以求出自回归部分的系数
- 对于$MA$部分，有![ARMA矩估计2](../captures/ARMA矩估计2.PNG "ARMA矩估计2")可以利用$MA$模型的参数的矩估计(在4.2)

#### 逆函数法

##### 基本思想

👉 因果的$ARMA$序列在可逆域内有逆转形式,**注：在[第二章](Chapter2.md)中$\,I_j\,$是用$\,\pi_j\,$表示**

$$
\begin{aligned}
\varepsilon_t &= \sum_{j=0}^{\infty} I_j X_{t-j}\\
&= I(B)X_t\\
&= (1-I_1B-I_2B^2-\cdots)X_t
\end{aligned}
$$

👉 $ARMA$序列有$\,\Phi(B)X_t = \Theta(B)\varepsilon_t\,$将上式代入该式即$\,\Phi(B)=\Theta(B)I(B)\,$,即

$$
1 - \phi_1B - \phi_2B^2 - \cdots - \phi_pB^p = (1 -\theta_1B - \theta_2B^2 - \cdots - \theta_qB^q)(1-I_1B-I_2B^2-\cdots)
$$

比较系数可得

![ARMA逆函数估计1](../captures/ARMA逆函数估计1.PNG "ARMA逆函数估计1")

![ARMA逆函数估计2](../captures/ARMA逆函数估计2.PNG "ARMA逆函数估计2")

##### 如何估计逆函数

👉 用自回归系数近似逆函数

$$
I_j = \phi_j, j\leq p^{*}\\
I_j = 0, j > p^{*}
$$

- 由于$ARMA$的逆函数是指数衰减的，故对于**充分大**的$\,p^{*}\,$，可以用自回归系数近似
- 一般取$\,p^{*} = max(p,q) + q\,$

👉 算法步骤如下

![ARMA逆函数估计3](../captures/ARMA逆函数估计3.PNG "ARMA逆函数估计3")

将前两步结果带入![ARMA逆函数估计1](../captures/ARMA逆函数估计1.PNG "ARMA逆函数估计1")求得自回归系数的估计

### 4.4 $ARMA$模型参数的精估计——最小二乘估计

#### $AR$参数的最小二乘估计

👉 $AR$模型是关于参数$\,\phi = (\phi_1,\phi_2,\cdots,\phi_p)\,$的线性模型，**用线性最小二乘原理**进行估计，使残差平方和最小 ![AR最小二乘估计1](../captures/AR最小二乘估计1.PNG "AR最小二乘估计1")

![AR最小二乘估计2](../captures/AR最小二乘估计2.PNG "AR最小二乘估计2")

上式可写为 ![AR最小二乘估计3](../captures/AR最小二乘估计3.PNG "AR最小二乘估计3")

![AR最小二乘估计4](../captures/AR最小二乘估计4.PNG "AR最小二乘估计4")

由上式可得AR模型的最小二乘估计

![AR最小二乘估计5](../captures/AR最小二乘估计5.PNG "AR最小二乘估计5")

故可得高斯白噪声的最小二乘估计

![AR最小二乘估计6](../captures/AR最小二乘估计6.PNG "AR最小二乘估计6")

#### ARMA和MA的最小二乘估计

👉 非线性估计

### 4.5 ARMA模型参数的精估计——极大似然估计