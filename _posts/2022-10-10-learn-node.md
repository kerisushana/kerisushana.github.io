---
title: 关于排列生成函数
date: 2022-10-9 10:34:00 +0800
categories: [算法]
tags: [学习]
pin: true
author: kerisuchiaki
author: minamichiaki
toc: true
comments: true
typora-root-url: ../../kerisuchiaki.github.io
math: true
mermaid: true
image:
  src: /C:\Users\minamichiaki\Pictures
  alt: 发布成功

---
# 为什么关于排列问题的母函数的公式每一部分的每一部分的分母要带阶乘？
例如A物品有3个，则他的公式为（x^0/0!+x^1/1!+x^2/2!+x^3/3!);  
X^0/0!表示从A什么都不选的排列的数量有一种；  
X^1/1!表示从A中选1种的的排列数量有1种；  
X^n/n!也是同样的道理都只有一种（毕竟都是一样的）  
那么当我们从不同的物品中选不同的数量进行排列，如果我们不加阶乘那么表示的结果其实就是组合问题中数量，根据排列与组合的关系即相差K!倍（k个物品的排列与k个物品的组合的数量），所以我们要在结果上化出分母是k!的阶乘的形式，但由于组合时就已经重复了，所以还要在结果分母乘以每一部分的阶乘才能消除排列时的重复。

