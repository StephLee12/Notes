- [Big Data Mining](#big-data-mining)
  - [Hashing](#hashing)
    - [LSH(Local Sensitive Hashing,局部敏感哈希)](#lshlocal-sensitive-hashing局部敏感哈希)
      - [Shingling](#shingling)
      - [Minhashing(最小哈希)](#minhashing最小哈希)
        - [Signature Matrix](#signature-matrix)
      - [LSH——找相似的文档](#lsh找相似的文档)
  - [数据流挖掘](#数据流挖掘)
    - [概念漂移](#概念漂移)
      - [检测概念漂移](#检测概念漂移)
        - [基于分布的检测(Distribution-based detector)](#基于分布的检测distribution-based-detector)
        - [基于错误率的检测(Error-rate based detector)](#基于错误率的检测error-rate-based-detector)
    - [数据流分类](#数据流分类)
      - [Decision Tree Learning](#decision-tree-learning)
        - [VFDT(Very Fast Decision Tree)](#vfdtvery-fast-decision-tree)
    - [数据流聚类](#数据流聚类)
      - [Cluster Feature](#cluster-feature)
        - [CluStream](#clustream)
  - [Hadoop/Spark](#hadoopspark)
    - [Hadoop](#hadoop)
      - [HDFS](#hdfs)
      - [MapReduce](#mapreduce)
    - [Spark](#spark)
      - [RDD(resilient distributed dataset)](#rddresilient-distributed-dataset)

# Big Data Mining

## Hashing

### LSH(Local Sensitive Hashing,局部敏感哈希)

#### Shingling

👉 一个文档的k-shingle(也称k-gram):连续k个字符一起出现的序列

$$
\text{k = 2 doc = abcab} \\
\text{set of 2-shingles} = \{ab,bc,ca\}
$$

👉 通过Shingling技术，可以将文档转换为一个特征向量。将多个文档的特征向量组合即可得到一个矩阵

#### Minhashing(最小哈希)

👉 将Shingling得到的矩阵进行降维

👉 最小哈希步骤

- 计算签名矩阵
- 通过签名矩阵寻找相似的签名

##### Signature Matrix

👉 将每一列$C$转换为一个更小的$Sig(C)$，理论上可保证$Sim(C_1,C_2)$与$Sim(Sig(C_1),Sig(C_2))$相等

👉 计算相似度使用的是Jaccard Distance

👉 假设将一个列进行随机扰动，定义一个哈希方程$h(C)$，其函数值为扰动过的列中第一个值为1的行号(行号也为扰动过的行号)

👉 Case 1

![签名矩阵](captures/签名矩阵.PNG "签名矩阵")

- 未扰动时得到的签名矩阵第一行为$(3,1,1,2)$
- 第一次扰动得到的签名矩阵第二行为$(2,2,1,3)$
- 之后同理
- 将$7\times 4$的输入矩阵转换为$3\times 4$的签名矩阵

👉 为什么转换后的相似度还是相等

$$
Sim(C_1,C_2) = Pr(h(C_1)=h(C_2))
$$

- 因为$h(C)$的值为第一个出现1的行号，故$h(C_1)=h(C_2)$只能为两个列第一个出现1的行号相等,即为$1,1$(相当于计算Jaccard Distance中的a)，而$0,1$和$1,0$可以视为b,c，所以

$$
Pr(h(C_1)=h(C_2)) = \frac{a}{a+b+c} = Jaccard(C_1,C_2)
$$

- 但是扰动的次数一定要足够多，才能保证转换后的相似度不变

👉 Case 1 Continue

![签名矩阵2](captures/签名矩阵2.PNG "签名矩阵2")

👉 实际实现

伪代码如下，直接进行扰动开销太大，通过**哈希函数**进行扰动

![签名矩阵3](captures/签名矩阵3.PNG "签名矩阵3")

- ``M(i,c)``是初始化(每个元素都是$\infty$)的矩阵，``i``是扰动的次数,``c``是文档的个数
- Case 2 ![签名矩阵4](captures/签名矩阵4.PNG "签名矩阵4")
  - 对每一个数据进行两次扰动

#### LSH——找相似的文档

👉 即使是签名矩阵，两两计算相似度(枚举)时间开销是很大的

👉 将每一个文档通过哈希映射到不同的桶中，一个桶中的数据是相似的

👉 但一般不是把每个文档直接映射，而是将签名矩阵划分为几个bands，分别进行映射。**如果两个文档是相似的，则两个文档至少有一个band被映射到同一个桶中**

![LSH](captures/LSH.PNG "LSH")

## 数据流挖掘

👉 数据流具有的特征

- 依次到达(One by One)
- 没有边界(Potentially Unbounded)
- 概念漂移(Concept Drift)

### 概念漂移

- 目标变量的统计特征随着时间变化
- 变量的条件概率分布$P(C|X)$改变，C是类别,X是特征向量

![概念漂移1](captures/概念漂移1.PNG "概念漂移1")

👉 第三幅图为**虚假的概念漂移**，即条件概率分布没有发生变化，只是特征向量的分布发生了变化

#### 检测概念漂移

##### 基于分布的检测(Distribution-based detector)

👉 设置一个窗口大小，窗口截取不同时间段数据快照，检验分布是否发生变化

👉 缺点

- 很难确定窗口大小
- 学习概念漂移缓慢
- 会将虚假概念漂移视为真概念漂移

👉 **Adaptive Windowing**(ADWIN)

![ADWIN](captures/ADWIN.PNG "ADWIN")

👉 不断的丢掉旧的数据(从时间上看，旧的数据)，将一个窗口分为两部分，将分界线进行左右滑动，若无论怎么滑动，被分的两部分都没有显著性差异，则接受新的窗口；否则，一直丢掉旧的数据

##### 基于错误率的检测(Error-rate based detector)

👉 检测**分类错误率**的改变

👉 缺点

- 对噪声敏感
- 难以处理缓慢(渐变)的概念漂移
- 十分依赖于学习模型(模型本身的好坏)

👉 DDM算法

![DDM](captures/DDM.PNG "DDM")

- $p_i$是错误率，$s_i$是标准差，$p_{min},s_{min}$分别是历史最小的错误率和标准差

### 数据流分类

#### Decision Tree Learning

##### VFDT(Very Fast Decision Tree)

👉 算法流程如下所示

![VFDT](captures/VFDT.PNG "VFDT")

### 数据流聚类

👉 **Online**——在内存中会存储每个簇结构的一些统计特征，并会**实时动态更新**

- 内存中存储的是微簇(Micro-Cluster)
  - 将相似的点视为一个点
  - 压缩数据，并可以代表这些数据

👉 **Offline**——用K-Means或DBSCAN对数据进行聚类

#### Cluster Feature

👉 特征簇算法

👉 有三个特征$CF=(N,LS,SS)$

$$
  N为数据点的个数\\
  LS = \sum_{i=1}^{N} X_i \\
  SS = \sum_{i=1}^{N} X_i^2
$$

- 可以计算中心和半径

👉 当来了一个新数据$X_j$

$$
  CF^{'} = (N+1,LS+X_j,SS+X_j^2)
$$

- 可以增量式的计算

##### CluStream

👉 特征簇算法的经典算法

## Hadoop/Spark

### Hadoop

👉 通过分布式处理海量数据，基本思想：**分而治之**

- 自动进行并行化和分布式
- 为用户提供编程接口
- 错误容许和自动恢复
  - 某台机器崩了之后，会自动恢复

#### HDFS

👉 用于存储大数据

- **namenode**
  - 元数据的标记 ![hadoop_namenode](captures/hadoop_namenode.PNG "hadoop_namenode")
- **datanode** ![hadoop_datanode](captures/hadoop_datanode.PNG "hadoop_datanode")
  - 存储真实的数据
  - 每个文件被分为很多块
  - 每个块被复制N次(N默认为3)
- 利用namenode检测某个块是否**挂掉**，利用**心跳机制**，复制的每个块定时发送信息

#### MapReduce

👉 用于计算

![hadoop](captures/hadoop.PNG "hadoop")

👉 对于一次计算速度很快，但是对于多次计算，I/O开销太大

### Spark

👉 Spark主要是用于计算，解决了MapReduce存在的问题，发明了RDD

👉 Spark的存储仍然使用HDFS

#### RDD(resilient distributed dataset)

👉 弹性式分布数据集

![Spark](captures/Spark.PNG "Spark")