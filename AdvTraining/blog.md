# 看博客学习的笔记

## 对抗攻击基本概念

- 攻击分类
  - 黑盒攻击
    - 攻击者对模型一无所知，只能通过输入和输出进行交互
  - 白盒攻击
    - 与黑盒恰恰相反
  - 灰盒攻击
    - 介于黑白盒之间
- 攻击目的
  - 无目标攻击
    - 只要错误分类即可
  - 有目标攻击
    - 要分类的指定的一个错误类
- 扰动强度大小 $\mid\mid x \mid\mid_p = (\sum_{i=1}^{n} \mid x_i \mid ^p)^{\frac{1}{p}}$
  - 无穷范数攻击
    - 当$p\rightarrow \infty$时，表示扰动中最大的一个
  - 二范数攻击
  - 0范数攻击(单像素攻击)
    - 限制可以改变的像素个数
- 基于梯度的攻击
  - FGSM
  - PGD
  - MIM
- 基于优化的攻击
  - CW  
- 基于决策面的攻击
  - DEEPFOOL

## 基于梯度的攻击

### FGSM(Fast Gradient Sign Method)

👉 在**白盒**环境下，求模型(用损失函数表示)对输入函数的导数，然后用**符号函数**得到梯度方向，接着乘以一个步长，得到的**扰动**加在原输入上，得到一个对抗样本

👉 这种方法 只是一次迭代，但产生对抗样本的速度快

$$
x^{'} = x + \varepsilon \times sign(\nabla_x J(x,y))
$$

👉 所有基于梯度的攻击方法都是基于**让模型的损失函数增大**来做的


$$
x^{adv} = x + \varepsilon sign(\nabla_x J(\theta,x,y))
$$

$$
\mid \mid \delta \mid \mid_{\infty} < \varepsilon
$$

$$
\nabla_\theta \rho(\theta)
$$


