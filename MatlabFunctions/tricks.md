# Some Matlab Tricks

👉 对矩阵的行求和 ``sum(A,2)`` 列求和``sum(A,1)``

👉 matlab产生区间[a,b]的一个均匀分布随机数

```matlab
unifrnd(a,b);
a+(b-a)*rand;
```

产生随机数组

```matlab
unifrnd(a,b,m,n);
a+(b-a)*rand(m,n);
```

产生标准正态分布``randn(m,n)`` 

产生一般的正态分布``normrnd(\mu,\sigma,m,n)``

产生指数分布``exprnd(\mu,m,n)`` ($\,\mu\,$是期望值，指数分布的期望值为$\,\frac{1}{\lambda}\,$)

产生泊松分布``poissrnd(\lambda,m,n)``

👉 将某个向量累加求和

```matlab
new_x  = cumsum(x)
```

👉 一维插值``interp1`` 二维插值(对于网格结点数据)``interp2`` 散点插值``griddata``

👉 多项式拟合``polyfit`` 最小二乘拟合``lsqcurvefit lsqnonlin``