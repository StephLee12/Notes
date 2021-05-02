- [Chapter 5 模型建立的准则与检验](#chapter-5-模型建立的准则与检验)
  - [5.1 时间序列的统计检验](#51-时间序列的统计检验)
    - [序列的平稳性检验](#序列的平稳性检验)
      - [判断平稳性](#判断平稳性)
      - [平稳性参数检验](#平稳性参数检验)
      - [平稳性的非参数检验——逆序检验法](#平稳性的非参数检验逆序检验法)
      - [平稳性的非参数检验——游程检验](#平稳性的非参数检验游程检验)
    - [正态性检验](#正态性检验)
      - [峰度偏度检验](#峰度偏度检验)
    - [白噪声检验](#白噪声检验)
      - [正态白噪声检验](#正态白噪声检验)
      - [白噪声正态分布检验法](#白噪声正态分布检验法)
  - [5.2 模型的适应性检验和零均值检验](#52-模型的适应性检验和零均值检验)
    - [适应性检验](#适应性检验)
      - [残量计算](#残量计算)
      - [残量的自相关检验法](#残量的自相关检验法)
    - [零均值检验](#零均值检验)
  - [5.3 模型类型的初步识别](#53-模型类型的初步识别)
    - [Box-Jenkins方法](#box-jenkins方法)
      - [样本自相关函数的截尾性检验](#样本自相关函数的截尾性检验)
        - [Barlett公式](#barlett公式)
        - [构造检验统计量](#构造检验统计量)
      - [样本偏相关函数的截尾性检验](#样本偏相关函数的截尾性检验)
  - [5.4 ARMA模型阶的确定](#54-arma模型阶的确定)
    - [利用5.3初步定阶](#利用53初步定阶)
    - [残差方差图定阶法](#残差方差图定阶法)
    - [最佳准则函数定阶法(重要！)](#最佳准则函数定阶法重要)
      - [FPE(最终预报误差)](#fpe最终预报误差)
      - [AIC准则](#aic准则)
      - [BIC准则](#bic准则)

# Chapter 5 模型建立的准则与检验

## 5.1 时间序列的统计检验

### 序列的平稳性检验

#### 判断平稳性

👉 即简要判断

1. 数据图分析
2. 求根判别——根都在单位圆内
3. 自相关、偏相关函数检验法

#### 平稳性参数检验

👉 基本思想——将一个时间序列分成很多段，分别计算每段样本的数字特征的统计量，这些段的统计量不应该有**显著差异**

#### 平稳性的非参数检验——逆序检验法

👉 基本思想——检验序列是否含有趋势性。同样对数据进行划分，求每段样本的均值

- 构造一个随机变量(相邻逆序数)
  - ![逆序检验1](../captures/逆序检验1.PNG "逆序检验1")
- 构造统计量
  - ![逆序检验2](../captures/逆序检验2.PNG "逆序检验2")
- 若是平稳序列且每段样本是独立同分布的，则有
  - ![逆序检验3](../captures/逆序检验3.PNG "逆序检验3")
- 因此构造检验统计量，$\,K\,$为分段的段数
  - ![逆序检验4](../captures/逆序检验4.PNG "逆序检验4")

#### 平稳性的非参数检验——游程检验

👉 游程定义：一个具有相同符号的连续串，在它前后相接的是与其不同的符号或完全无符号

👉 基本思想 ![游程检验1](../captures/游程检验1.PNG "游程检验1")

![游程检验2](../captures/游程检验2.PNG "游程检验2")

### 正态性检验

#### 峰度偏度检验

![正态性检验1](../captures/正态性检验1.PNG "正态性检验1")

![正态性检验2](../captures/正态性检验2.PNG "正态性检验2")

### 白噪声检验

#### 正态白噪声检验

![正态白噪声检验1](../captures/正态白噪声检验1.PNG "正态白噪声检验1")

![正态白噪声检验2](../captures/正态白噪声检验2.PNG "正态白噪声检验2")

#### 白噪声正态分布检验法

![白噪声正态分布检验1](../captures/白噪声正态分布检验1.PNG "白噪声正态分布检验1")

![白噪声正态分布检验2](../captures/白噪声正态分布检验2.PNG "白噪声正态分布检验2")

![白噪声正态分布检验3](../captures/白噪声正态分布检验3.PNG "白噪声正态分布检验3")

## 5.2 模型的适应性检验和零均值检验

### 适应性检验

👉 建立的模型**基本上解释了系统的动态性**，故模型中的噪声应为白噪声

👉 适应性检验即检验模型残差是否为白噪声，与上面不同，下面**构造检验统计量**来检验残量是否为白噪声序列

#### 残量计算

👉 AR模型可以直接算 MA和ARMA都要递推

#### 残量的自相关检验法

👉 基本原理 检验残量是否为独立随机变量

👉 构造统计量 ![残量的自相关检验法1](../captures/残量的自相关检验法1.PNG "残量的自相关检验法1")

![残量的自相关检验法2](../captures/残量的自相关检验法2.PNG "残量的自相关检验法2")

![残量的自相关检验法3](../captures/残量的自相关检验法3.PNG "残量的自相关检验法3")

![残量的自相关检验法4](../captures/残量的自相关检验法4.PNG "残量的自相关检验法4")

![残量的自相关检验法5](../captures/残量的自相关检验法5.PNG "残量的自相关检验法5")

### 零均值检验

![零均值检验1](../captures/零均值检验1.PNG "零均值检验1")

👉 根据Chapter3的Barlett公式，可以计算X的方差，常见的时间序列的方差如下

![零均值检验2](../captures/零均值检验2.PNG "零均值检验2")

![零均值检验2](../captures/零均值检验3.PNG "零均值检验3")

## 5.3 模型类型的初步识别

### Box-Jenkins方法

👉 依据样本自相关、偏相关函数的截尾性和拖尾性初步判定模型

👉 MA模型满足自相关函数q步截尾，偏相关函数拖尾

👉 AR模型满足偏相关函数p步截尾，自相关函数拖尾

👉 ARMA模型的自相关和偏相关函数都不截尾，只是负指数衰减

#### 样本自相关函数的截尾性检验

##### Barlett公式

![相关函数截尾性检验1](../captures/相关函数截尾性检验1.PNG "相关函数截尾性检验1")

![相关函数截尾性检验2](../captures/相关函数截尾性检验2.PNG "相关函数截尾性检验2")

![相关函数截尾性检验3](../captures/相关函数截尾性检验3.PNG "相关函数截尾性检验3")

![相关函数截尾性检验4](../captures/相关函数截尾性检验4.PNG "相关函数截尾性检验4")

##### 构造检验统计量

![相关函数截尾性检验5](../captures/相关函数截尾性检验5.PNG "相关函数截尾性检验5")

![相关函数截尾性检验6](../captures/相关函数截尾性检验6.PNG "相关函数截尾性检验6")

#### 样本偏相关函数的截尾性检验

![偏相关函数截尾性检验](../captures/偏相关函数截尾性检验.PNG "偏相关函数截尾性检验")

![偏相关函数截尾性检验1](../captures/偏相关函数截尾性检验1.PNG "偏相关函数截尾性检验1")

## 5.4 ARMA模型阶的确定

### 利用5.3初步定阶

### 残差方差图定阶法

![残差方差图定阶法](../captures/残差方差图定阶法.PNG "残差方差图定阶法")

![残差方差图定阶法2](../captures/残差方差图定阶法2.PNG "残差方差图定阶法2")

![残差方差图定阶法3](../captures/残差方差图定阶法3.PNG "残差方差图定阶法3")

### 最佳准则函数定阶法(重要！)

👉 定阶

![最佳准则函数定阶1](../captures/最佳准则函数定阶1.PNG "最佳准则函数定阶1")

#### FPE(最终预报误差)

👉 用来判定AR模型的阶数，当N充分大时，FPE也可用于ARMA模型的定阶

![最佳准则函数定阶2](../captures/最佳准则函数定阶2.PNG "最佳准则函数定阶2")

![最佳准则函数定阶3](../captures/最佳准则函数定阶3.PNG "最佳准则函数定阶3")

![最佳准则函数定阶4](../captures/最佳准则函数定阶4.PNG "最佳准则函数定阶4")

#### AIC准则

👉 基本思想——KL信息量

![最佳准则函数定阶5](../captures/最佳准则函数定阶5.PNG "最佳准则函数定阶5")

![最佳准则函数定阶6](../captures/最佳准则函数定阶6.PNG "最佳准则函数定阶6")

#### BIC准则

![最佳准则函数定阶7](../captures/最佳准则函数定阶7.PNG "最佳准则函数定阶7")