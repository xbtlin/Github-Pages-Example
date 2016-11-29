---
layout:     post
title:      线性模型
category: blog
description: 线性回归和LR回归
---

## 线性回归
有d个属性的示例
$$x=(x_1;x_2;...;x_d)$$
线性模型通过属性的线性组合来求预测函数：
$$
f(x)=w_1x_1+w_2x_2+...+w_dx_d+b,
$$
向量形式：
$$
f(x)=w^Tx+b
$$
其中$$w=(w_1;w_2;...;w_d)$$
w和b确定模型。

有数据集$$D={(x_1,y_1),(x_2,y_2),...,(x_m,y_m)}$$
其中
$$
x_i = (x_{i1};x_{i2};...;x_{id})
$$

线性回归试图学得
$$
f(x_i)=wx_i+b，使得f(x_i)约等于y_i
$$

如何衡量f(x)和y之间的差别？
**均方误差。**

$$（w^{\*},b^*）= argmin\Sigma_{i=1}^{m}(f(x_i-y_i)^2)    
= argmin\Sigma_{i=1}^{m}(y_i-wx_i-b)^2)  $$




## LR回归


## 线性判别分析（LDA）

