- [Time Series Analysis](#time-series-analysis)
  - [Chapter 4 平稳序列模型参数估计](#chapter-4-%e5%b9%b3%e7%a8%b3%e5%ba%8f%e5%88%97%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e4%bc%b0%e8%ae%a1)
    - [4.1 AR模型参数的矩估计](#41-ar%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1)
      - [AR(p)自回归系数的矩估计(Yule-Walker估计)](#arp%e8%87%aa%e5%9b%9e%e5%bd%92%e7%b3%bb%e6%95%b0%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1yule-walker%e4%bc%b0%e8%ae%a1)
      - [AR(p)噪声序列方差的矩估计](#arp%e5%99%aa%e5%a3%b0%e5%ba%8f%e5%88%97%e6%96%b9%e5%b7%ae%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1)
    - [Durbin-Levinson递推估计算法](#durbin-levinson%e9%80%92%e6%8e%a8%e4%bc%b0%e8%ae%a1%e7%ae%97%e6%b3%95)
    - [4.2 MA模型参数的矩估计](#42-ma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1)
      - [直接消元](#%e7%9b%b4%e6%8e%a5%e6%b6%88%e5%85%83)
      - [递推计算法](#%e9%80%92%e6%8e%a8%e8%ae%a1%e7%ae%97%e6%b3%95)
      - [线性迭代法(收敛速度慢)](#%e7%ba%bf%e6%80%a7%e8%bf%ad%e4%bb%a3%e6%b3%95%e6%94%b6%e6%95%9b%e9%80%9f%e5%ba%a6%e6%85%a2)
      - [Newton-Raphson法](#newton-raphson%e6%b3%95)
      - [新息估计原理](#%e6%96%b0%e6%81%af%e4%bc%b0%e8%ae%a1%e5%8e%9f%e7%90%86)
      - [MA序列参数的新息估计](#ma%e5%ba%8f%e5%88%97%e5%8f%82%e6%95%b0%e7%9a%84%e6%96%b0%e6%81%af%e4%bc%b0%e8%ae%a1)
    - [4.3 ARMA模型参数的初估计](#43-arma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e5%88%9d%e4%bc%b0%e8%ae%a1)
      - [ARMA模型参数的矩估计](#arma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%9f%a9%e4%bc%b0%e8%ae%a1)
    - [4.4 ARMA模型参数的精估计——最小二乘估计](#44-arma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%b2%be%e4%bc%b0%e8%ae%a1%e6%9c%80%e5%b0%8f%e4%ba%8c%e4%b9%98%e4%bc%b0%e8%ae%a1)
    - [4.5 ARMA模型参数的精估计——极大似然估计](#45-arma%e6%a8%a1%e5%9e%8b%e5%8f%82%e6%95%b0%e7%9a%84%e7%b2%be%e4%bc%b0%e8%ae%a1%e6%9e%81%e5%a4%a7%e4%bc%bc%e7%84%b6%e4%bc%b0%e8%ae%a1)

# Time Series Analysis

## Chapter 4 平稳序列模型参数估计

### 4.1 AR模型参数的矩估计

- 对于零均值因果自回归序列，考虑**回归系数和噪声方差的估计**

#### AR(p)自回归系数的矩估计(Yule-Walker估计)

![AR自回归系数矩估计](captures/AR自回归系数矩估计.PNG "AR自回归系数矩估计")

![AR自回归系数矩估计2](captures/AR自回归系数矩估计2.PNG "AR自回归系数矩估计2")

![AR自回归系数矩估计3](captures/AR自回归系数矩估计3.PNG "AR自回归系数矩估计3")

#### AR(p)噪声序列方差的矩估计

![AR噪声序列方差矩估计](captures/AR噪声序列方差矩估计.PNG "AR噪声序列方差矩估计")

### Durbin-Levinson递推估计算法

![AR序列自回归系数矩估计递推](captures/AR序列自回归系数矩估计递推.PNG "AR序列自回归系数矩估计递推")

### 4.2 MA模型参数的矩估计

👉 回顾MA模型的自相关函数

- MA模型的自相关函数与AR、ARMA不同，它是截尾的

![回顾MA自协方差函数](captures/回顾MA自协方差函数.PNG "回顾MA自协方差函数")

👉 建立求解模型

![MA系数求解方程](captures/MA系数求解方程.PNG "MA系数求解方程")

#### 直接消元

👉 对于低阶MA模型，可以直接消元，但要注意**模型的可逆性**

👉 Ex

![直接消元Ex](captures/直接消元Ex.PNG "直接消元Ex")

![直接消元Ex2](captures/直接消元Ex2.PNG "直接消元Ex2")

#### 递推计算法

#### 线性迭代法(收敛速度慢)

![MA线性迭代法1](captures/MA线性迭代法1.PNG "MA线性迭代法1")

![MA线性迭代法2](captures/MA线性迭代法2.PNG "MA线性迭代法2")

#### Newton-Raphson法

#### 新息估计原理

![MA新息估计1](captures/MA新息估计1.PNG "MA新息估计1")

![MA新息估计2](captures/MA新息估计2.PNG "MA新息估计2")

#### MA序列参数的新息估计

![MA新息估计3](captures/MA新息估计3.PNG "MA新息估计3")

![MA新息估计4](captures/MA新息估计4.PNG "MA新息估计4")

### 4.3 ARMA模型参数的初估计

#### ARMA模型参数的矩估计

👉 先求AR部分的自回归系数 再求MA的滑动平均系数和高斯白噪声

### 4.4 ARMA模型参数的精估计——最小二乘估计

### 4.5 ARMA模型参数的精估计——极大似然估计