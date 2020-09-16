# Experiment_1

实验1过程中一些需要记录的东西

👉 list to array ``np.array(list)``

👉 array to list ``array.tolist()``

👉 对于array,可以计算很多数字特征``array.mean()`` ``array.min()`` ``array.max()``等

👉 加载arff文件，从``scipy.io``导入``arff``，执行``dataset = arff.loadarff('文件名')``，之后获得``dataset``,要获得``@data``部分的数据，用``data_tuple = dataset[0]``获取对应的元组

👉 加载后的arff文件信息，可以用``print(dataset.info())``

👉 加载arff文件后，由于每个属性都有一个**Label**(列名)，用``pandas``包下的``DataFrame``数据结构进行处理，每个对象作为一行，每个属性作为一列。注意``DataFrame``的行列的``index``都是从开始0的

👉 获取属性Label的方式``columns = list(df)``

👉 对于``DataFrame``中行列的选取，有几种方式:

```python
    df = pd.DataFrame(dataset[0])
    # df.loc，基于列label，可以选取特定行(根据行index)
    df.loc[0:1,['label_1','label_2']] #注意这里选中的是第0行和第1行，label为label_1和label_2的列
    # df.iloc 基于行列的index选取
    df.iloc[0:1,[1,2]] #注意这里选中的只是第0行，此处x1:x2表示左闭右开区间
    # 一般loc/iloc用于行列选取 at/iat用于定位元素
    # df.at 根据行index和列label，定位元素
    # df.iat 根据行列的index定位元素
    df.at[0,'label_1']
    df.iat[0,0]
```

👉 ``DataFrame``也可以进行数据处理，对于选取的某一列或行，是一个``Series``类型，可以计算均值，众数，中位数``series.mode(),series.mean(),series.median()``，获取众数``mode = series.mode().get(0)``

👉 获取``DataFrame``行列数

```python
    df.shape[0] #获取行数
    df.shape[1] #获取列数
    #其他数据类型 如矩阵也可以用shape[0],shape[1]获取行列数
```

👉 只获取``DataFrame``中的数据``value = df.values``

👉 将``DataFrame``转换为矩阵

```python
    df_list = df.values.tolist() #先转换为list
    df_mat = np.mat(df_list) #list转矩阵
```

注意转换为矩阵之后，矩阵中的每个值都是字符串类型``b''``

👉 将转换完后矩阵的数值属性的值变为``float``类型

```python
    column = mat[:,column_index]
    column = list(map(float,column)) #先做一个映射 然后将map转为list
    column = np.array(column) #将list转换为array就可进行计算操作
```

👉 在array中判断此array或某个值是否为``nan``,并找到为``nan``的下标

```python
    np.isnan(array) #会返回系列的bool值
    index = np.argwhere(np.isnan(array)) #得到为nan的值的下标
```

👉 在``Dataframe``中对于数值属性的数据判断缺失值``pd.isnull(df)``

👉 若要直接判断某个值是否为``nan``

```python
    import math
    math.isnan(elem) #返回一个bool值
```

👉 在``Dataframe``中对于数值属性的数据替换缺失值

```python
    series = df[column]
    mean = series.mean()
    df[column].fillna(mean,inplace=True)
```

👉 在``Dataframe``中可以进行类似在Matlab中的寻找满足条件的新Series，如

```python
    series = df[column]
    new_series = series[series != b'?'] #找到series中 值不为b'?'的元素，组成一个新的序列
```

👉 在``Dataframe``中进行如下操作``df[df[x_att] = elem]``会返回所有``x_att``属性的值为``elem``的数据对象

👉 在数据结构中学过 用生成式构建二维列表，这里再回顾一下

```python
    list_2d = [[0 for i in range(mat.shape[0])]
                 for j in range(mat.shape[1])]
```

👉 在``Dataframe``中可以进行概率的计算

实现1

```python
    new_data_att = df[att_name].unique() #df.unique()是去除重复值
    pr = []
    for i in new_data_att:
        tmp_pr = sum(df[att_name] == i) /df.shape[0] #计算att_name这一属性值为i的概率
        pr.append(tmp_pr)
```

实现2

```python
    pr_x = df[x_att].value_counts() /df.shape[0]
    #df[x_att].value_counts()是一个series，以元素值作为索引，序列中的值表示该元素出现的次数
```
