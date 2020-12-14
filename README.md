逻辑回归的基本理论的要点（也是在Github上的第一篇日记）
====
优缺点
---
优点：简单，易于理解和实现，速度快<br>
缺点：容易欠拟合，分类精度可能不高<br>

一般步骤
----
* 寻找预测函数h
* 构造损失函数J
* 求解J最小，得到回归参数theta

构造预测函数h(x)
----
1）Logistic函数（又称Sigmoid函数）：g(z) = 1/(1+e(-z))<br>
2) 边界条件z = sum(θ*x) <br>
3) 将2）代入到1）中得到：g(z) = 1/(1+e(-sum(θ*x)) <br>

用Logistic函数来表达分类结果为类别1或者类别0的概率：<br>
P(y = 1|x;θ) = h_θ(x) <br>
P(y = 0|x;θ) = 1- h_θ(x) <br>

构造损失函数J(x)
----
损失函数
