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
* 求解J最小，得到回归参数θ

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
损失函数（待更新）

求解J最小，得到回归参数θ
----
（待更新）

算法实践
====

* 主要是利用sklearn.linear_model的LogisticRegression算法包
* 主要流程:首先读入或构造数据；然后利用LR算法fit数据，即用数据算法训练模型；然后利用matplotlib去可视化样本点和边界；最后可以用LR.predcit去预测新的数据，进行分类。

算法细节
-----
* np.linspace(start,end,gap)构建等差数列
* np.meshgrid(a,b)生成网格点坐标矩阵,用a中的每个元素，与纵坐标矩阵b中对应位置元素组成坐标点，返回一个list,包含两个array,一个是这些坐标点的x值，另外一个是这些点的y值
* np.c_[a,b] :np.r_是按列连接两个矩阵，就是把两矩阵上下拼接，要求列数相等。np.c_是按行连接两个矩阵，就是把两矩阵左右拼接，要求行数相等。
* np.ravel(a):展开铺平矩阵，numpy.ravel()返回a,修改a;numpy.flatten()不返回矩阵，不修改a
* 但是文中np.c_(np.ravel(a),np.ravel(b))是把a，b做成n*1的矩阵，然后再左右拼接，
* lr.predict直接预测分类，lr.predcit_proba预测出来属于各个类别的概率
* plt.scatter绘制散点图，plt.contour绘制散点的轮廓图，这里解释一下最后的一行代码：plt.contour(x_grid, y_grid, z_proba, [0.5], linewidths=2., colors='blue')
x_grid, y_grid绘制了网格，有200*100个点，然后z_probe给出来这200*100个点属于1的概率，[0.5]的意思是只有概率值为0.5的才会绘制轮廓线，linewidths=2., colors='blue'线性和颜色。
* plt.annotate(s='str', xy=(x,y) , xytext=(l1,l2) , ...))用于标注文字,其中s为注释文本内容，xy为被注释的坐标点，xytest为注释文字的坐标位置

鸢尾花采用逻辑回归实践
====

需要采用的工具包
----
numpy,pandas数据处理
matplotlib,seaborn绘图工具

分析步骤
----
* 首先用sklearn导出iris的数据，然后将数据转化为pandas。查看数据的简单信息，比如feature，label
* 利用seaborn对数据进行可视化，sns.pairplot不同标签组合的散点可视化，sns.boxplot箱型图可以得到不同类别在不同特征上的分布差异情况
* 还可取三个特征绘制三维的散点图
* 利用回归模型进行训练和预测：包括了样本拆分，train_test_split,进行二分类，三分类(都是只需要数据输入即可，二分类中输入的数据的label只有两个，多分类中输入的数据的label有多个)
* 结果评价用到了混淆矩阵 metrics.confusion_matric()
