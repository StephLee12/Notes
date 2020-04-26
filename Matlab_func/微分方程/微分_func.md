- [微分方程求解](#%e5%be%ae%e5%88%86%e6%96%b9%e7%a8%8b%e6%b1%82%e8%a7%a3)
  - [常微分方程求解——ode工具箱](#%e5%b8%b8%e5%be%ae%e5%88%86%e6%96%b9%e7%a8%8b%e6%b1%82%e8%a7%a3ode%e5%b7%a5%e5%85%b7%e7%ae%b1)
  - [偏微分方程(PDE)求解](#%e5%81%8f%e5%be%ae%e5%88%86%e6%96%b9%e7%a8%8bpde%e6%b1%82%e8%a7%a3)

# 微分方程求解

## 常微分方程求解——ode工具箱

👉 ode23和ode45的代码使用方式都是一样的

- ode23 解**非刚性微分方程**，低精度，使用**R-K**二三阶算法
- ode45 解**非刚性微分方程**，中等精度，使用**R-K**四五阶算法

    其他解**刚性方程**的ode函数，[见blog](https://blog.csdn.net/yf210yf/article/details/38345445?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1)和**matlab官方文档**

👉 函数调用(以ode45为例)

``[t,y] = ode45(odefun,tspan,y0)``

👉 参数解释

- ``tspan = [t0,tf]``是求微分方程组$\,y^{'}=f(t,y)\,$从$\,t_0\,$到$\,t_f\,$的积分
- ``y0``是微分方程组的初始条件

  注意微分方程组中的微分方程都是一阶的，若高阶微分方程，要转化为一阶

👉 示例代码

- 求解$\,y^{'}=2t\,$

```matlab
function ex1_ode
tspan = [0,5];
y0 = 0;
[t,y] = ode45(@odefun,tspan,y0)
plot(t,y,'-o')

function dydt = odefun(t,y)
dydt = zeros(1,1);
dydt(1) = 2*t;
```

- 求解 ![ode](captures/ode.png "ode")

```matlab
function ex2_ode
tspan = [0,20];
y0 = [2,0];
[t,y] = ode45(@odefun,tspan,y0)
plot(t,y(:,1),'-o',t,y(:,2),'-o')

function dydt = odefun(t,y)
dydt = zeros(2,1);
dydt(1) = y(2);
dydt(2) = (1-y(1)^2)*y(2)-y(1);
```

## 偏微分方程(PDE)求解