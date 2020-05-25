- [Clustering and Outlier Detection](#clustering-and-outlier-detection)
  - [划分聚类方法](#划分聚类方法)
    - [K-Means](#k-means)
      - [K-Means算法步骤](#k-means算法步骤)
      - [K-Means评价](#k-means评价)
  - [层次聚类方法](#层次聚类方法)
    - [层次凝聚——AGNES算法](#层次凝聚agnes算法)
      - [AGNES算法步骤](#agnes算法步骤)
    - [层次分裂——DIANA算法](#层次分裂diana算法)
      - [DIANA算法步骤](#diana算法步骤)
  - [密度聚类方法](#密度聚类方法)
    - [密度聚类思想](#密度聚类思想)
    - [DBSCAN](#dbscan)
      - [DBSCAN基本定义](#dbscan基本定义)
      - [DBSCAN基本思想](#dbscan基本思想)
      - [DBSCAN算法步骤](#dbscan算法步骤)
      - [DBSCAN缺点](#dbscan缺点)
  - [网格聚类方法](#网格聚类方法)
    - [STING算法](#sting算法)

# Clustering and Outlier Detection

👉 聚类定义

- 将数据分为多个簇，使得在同一个簇内对象间具有较高的相似度，而不同簇间差别较大
- 是**无监督学习**
- 聚类目的——寻找数据中潜在的**自然分组结构**

👉 聚类算法分类

- 划分方法(partitioning method)
- 层次的方法(hierarchical method)
- 基于密度的方法(density-based method)
- 基于网格的方法(grid-based method)

## 划分聚类方法

👉 定义

- 将数据划分为$k$个簇，这些簇满足
  - 每个簇至少包含一个对象
  - 每一个对象属于且仅属于一个簇

👉 基本思想

- 对于给定的$k$，先给定一个初始划分方法
- **反复迭代**改变划分，使得改进后的划分方案比前一次更好

👉 常见的算法

- K-Means(K-均值)
- K-Medoids(K-中心点)

### K-Means

👉 聚类目标函数：簇对象到簇中心**平方误差**最小

$$
    E = \sum_{i=1}^{k} \sum_{x\in C_i} |x-\overline{x_i} |^2 \\
    \overline{x_i}是第i个簇的均值\\
    C_i代表第i个簇
$$

#### K-Means算法步骤

![K-Means](captures/K-Means.PNG "/K-Means")

![K-Means2](captures/K-Means2.PNG "/K-Means2")

#### K-Means评价

👉 优点

- 简单、快速
- 处理大数据集，相对可伸缩、高效

👉 缺点

- K-Means对于**球状分布数据**能取得较好结果
- **初值敏感**，初始点选取不同，结果会不同
- **噪声点(Outlier)敏感**，噪声点会严重影响K-Means的性能
  - K-中心点可以解决这个问题
  - 但K-中心点时间复杂度太高，用的少
- 必须事先给出$k$(parameter-free clustering algorithms)

👉 解决办法

- 先设置$k$值较大——大簇变小簇
  - 可以近似球状
  - 每个小簇的纯度很高

## 层次聚类方法

👉 对数据集进行层次的分解

👉 使用**距离**作为合并或分裂的标准，常见的距离度量

![层次聚类距离度量](captures/层次聚类距离度量.PNG "层次聚类距离度量")

- 用的最广的
  - Minimum distance——称为"Single Link"
  - Average distance——称为"Complete Link"

### 层次凝聚——AGNES算法

👉 **自底向上**的策略(像构造**哈夫曼树**的思想)，首先将每个对象作为一个簇，然后合并这些簇为更大的簇，相似度计算使用Minimum distance(Single Link)

#### AGNES算法步骤

![AGNES](captures/AGNES.PNG "AGNES")

### 层次分裂——DIANA算法

👉 **自顶向下**的策略(像DT)，首先将所有对象置于一个簇中，逐渐细分为更小的簇

👉 使用两种测度方法

- 簇的直径
  - 在一个簇中的任意两个数据点的距离中的最大值
- Average distance

#### DIANA算法步骤

![DIANA算法](captures/DIANA算法.PNG "DIANA算法")

## 密度聚类方法

### 密度聚类思想

👉 只要一个区域中的点的密度大于某个阈值，就将其加到与之相近的聚类中

- 可以克服基于距离算法**只能发现类圆形**的聚类的特点，可以发现任何形状的聚类，且对噪声不敏感

### DBSCAN

#### DBSCAN基本定义

- 对象的$\,\varepsilon\,$-邻域
  - 给定对象在半径$\,\varepsilon\,$内的区域
- 核心对象
  - 若一个对象的$\,\varepsilon\,$-邻域至少包含最小数目$MinPts$个对象，称该对象为核心对象
- 直接密度可达
  - 若$p$在$q$的$\,\varepsilon\,$-邻域内，而$q$是一个核心对象，则称$p$从$q$出发时直接密度可达的
- 密度可达(间接密度可达)
  - 存在一个对象链$p_1,p_2,\cdots,p_n,p_1=q,p_n = p$,对$p_i \in D$，$\,p_{i+1}\,$时从$\,p_i\,$直接密度可达的，则称对象$p$是从对象$q$密度可达的 ![DBSCAN密度可达](captures/DBSCAN密度可达.PNG "DBSCAN密度可达")
- 密度相连
  - 存在一个对象$o$，使得对象$p$和$q$时关于$o$密度可达的，则称对象$p$和$q$密度相连 ![DBSCAN密度相连](captures/DBSCAN密度相连.PNG "DBSCAN密度相连")
- 噪声
  - 一个基于密度的簇是基于**密度可达性**的**最大的密度相连对象的集合**
  - 不包含任何簇中的对象被认为是"噪声" ![DBSCAN噪声](captures/DBSCAN噪声.PNG "DBSCAN噪声")

#### DBSCAN基本思想

- 对于一个类中的每个对象，在其给定半径的邻域中包含的对象不能少于某一给定的最小数目
- 一个类能够被其中的任意一个核心对象所确定

#### DBSCAN算法步骤

![DBSCAN算法步骤](captures/DBSCAN算法步骤.PNG "DBSCAN算法步骤")

#### DBSCAN缺点

- 调参难
  - 对$\,\varepsilon和MinPts\,$敏感，但这两个参数的选取主要依靠主观判断。$MinPts$取$4\sim20$
- 数据库较大时要进行较大的IO开销
- 不同密度簇问题
  - 若不同簇的密度不同，很可能把密度稀疏的簇识别为噪声

## 网格聚类方法

👉 本质：密度聚类

👉 基本思想

- 将特征空间划分为网格结构

👉 优缺

- 优点
  - 处理速度很快
- 缺点
  - 难以处理高维数据

### STING算法