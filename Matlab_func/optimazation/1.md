- [优化模型相关函数](#%e4%bc%98%e5%8c%96%e6%a8%a1%e5%9e%8b%e7%9b%b8%e5%85%b3%e5%87%bd%e6%95%b0)
  - [线性规划](#%e7%ba%bf%e6%80%a7%e8%a7%84%e5%88%92)
    - [linprog](#linprog)
    - [intlinprog](#intlinprog)
  - [非线性规划](#%e9%9d%9e%e7%ba%bf%e6%80%a7%e8%a7%84%e5%88%92)
    - [fmincon](#fmincon)
    - [fminbnd](#fminbnd)
    - [fminsearch](#fminsearch)
    - [fminunc](#fminunc)
    - [ga](#ga)
  - [多目标规划(Multi-Objective Optimization,MOO)](#%e5%a4%9a%e7%9b%ae%e6%a0%87%e8%a7%84%e5%88%92multi-objective-optimizationmoo)

# 优化模型相关函数

## 线性规划

### linprog

👉 求解一般的线性规划

👉 **都是求最小值**，若优化问题为最大值要转化为最小值

👉 优化模型
$$
    min \,\,f(x)\\
    \begin{aligned}
       s.t\, Ax &\leq b\\
    A_{eq}x &= b_{eq}\\
    lb \leq &x \leq ub
    \end{aligned}
$$

👉 调用方式

- ``[x,fval] = linprog(f,A,b,Aeq,beq,lb,ub)``

👉 参数解释

- ``A,b``是不等式约束条件的参数
- ``Aeq,beq``是等式约束条件的参数
- ``lb,ub``是决策变量``x``取值范围
- ``f``是目标函数决策变量前的系数

    ``f,x,b,beq,lb,ub``是向量，``A,Aeq``是矩阵

👉 示例代码

```matlab
%目标函数中决策变量前的系数
f = [0.03 0.22 0.38 0.5 0.35];
lb = [0 0 0.1 0.2 0.05];%每一个决策变量的下界
ub = [0.3 0.25 0.3 1 0.2];%每一个决策变量的上界
A = []; b = []; %A,b是不等式约束条件的参数
Aeq = [1 1 1 1 1]; beq = 1; %Aeq beq是等式约束条件的参数
[optx,optvalue,flag] = linprog(f,A,b,Aeq,beq,lb,ub)
```

### intlinprog

👉 可以求解**整数规划**(0-1规划)和**混合整数线性规划**

👉 调用方式

- ``[x,fval] = intlinprog(f,intcon,A,b,Aeq,beq,lb,ub)``

👉 参数解释

与``linprog``相比多了参数``intcon``,该参数决定了**整数决策变量**的**位置**

如``x1 x3``是整数决策变量，则``intcon = [1 3]``

``intcon``同样是一个向量

👉 示例代码

![intlinprog1](captures/intlinprog1.png "intlinprog1")

```matlab
f  = [-5 -8];
A  = [1 1; 5 9];
b =  [6 45];
lb = zeros(1,2);
intcon = [1,2];
[x,fval] = intlinprog(f,intcon,A,b,[],[],lb,[])
```

## 非线性规划

### fmincon

👉 解决非线性规划问题

👉 优化模型
$$
    min \,\, f(x)\\
    s.t.\begin{cases}
        Ax \leq b\\
        A_{eq}x = b_{eq}\\
        c(x) \leq 0\\
        c_{eq}(X) \leq 0\\
        lb \leq x \leq ub\\
    \end{cases}\\
    c(x)和c_{eq}(x)是向量函数
$$

👉 调用方法

``[x,fval] = fmincon(fun,x0,A,b,Aeq,beq,lb,ub,nonlcon)``

👉 参数解释

- ``nonlcon``是非线性向量函数约束
- ``fun``是定义的函数``f(x)``，代表非线性目标函数
- ``x0``是``x``的初始值
- ``A,b,Aeq,beq``定义了线性约束，如果没有，都为``[]``

👉 示例代码

![fmincon](captures/fmincon.png "fmincon")

```matlab
function testmain_fmincon
clear all;
[x,fval] = fmincon(@objfun,rand(3,1),[],[],[],[],zeros(3,1),[],@cons)

function f=objfun(x)
f = x(1)^2 + x(2)^2 + x(3)^2 + 8;

function [c,ceq] = cons(x)
c = [- x(1)^2+x(2)-x(3)^2; x(1)+x(2)^2+x(3)^2-20];
ceq = [-x(1)-x(2)^2+2; x(2)+2*x(3)^2-3];
```

### fminbnd

👉 解决**单变量有约束**非线性函数最值(最小值)问题

👉 调用方式

``[x,fval] = fminbnd(fun,x1,x2)``

👉 参数解释

- ``x1 x2``是变量的范围

👉 示例代码

```matlab
clear all;

fun = @(x)sin(x);
x1 = 0;
x2 = 2 * pi;
[x,fval] = fminbnd(fun,x1,x2)
```

### fminsearch

👉 解决单(**或多**)变量**无约束**非线性函数最值(最小值)问题

👉 调用方式

``[x,fval] = fminsearch(fun,x0)``

👉 参数解释

- ``x0``是初值

👉 示例代码
$$
    f(x) = 100(x_2 - x_1^2)^2 + (1-x_1)^2
$$

```matlab
clear all;
fun = @(x)100*(x(2)-x(1)^2)^2 + (1-x(1))^2;
x0 = [-1.2,1];
[x,fval] = fminsearch(fun,x0)
```

### fminunc

👉 解决单(**或多**)变量**无约束**非线性函数最值(最小值)问题

👉 与``fminsearch``类似

### ga

👉 解决非线性规划问题

👉 调用方法

- ``[x,fval] = ga(fun,nvars)`` ``nvars``是决策变量的数目
- ``[x,fval] = ga(fun,nvars,A,b,Aeq,beq,lb,ub,nonlcon,intcon,options)``

其中``options``可在**优化工具箱**中查看

## 多目标规划(Multi-Objective Optimization,MOO)

👉 Matlab无现成的函数，流行的算法是**基于遗传算法的多目标优化(NSGA2)**