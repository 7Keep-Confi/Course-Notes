# 机器学习总复习(按复习要点)

## 机器学习基础

## lambda的解释

「ML = lambda」

机器学习 - Machine Learning

机器学习中的「机器」实际上就是 **函数**。这个函数有许多待求解的参数，提供的输入与这些参数相互作用后，就会产生输出

什么是学习？ **造机器，调参数**。确定函数的「形状」之后再进行调参，也就是在调参数之前需要明白这个机器大致长什么样子

有一个已知的数据集 DATA ，

Machine Learning = Lambda

机器=函数，学习=参数求解。

机器学习=Lambda。

**L = Loss， A = Algorithm， M = Model，BD = BigData，A = Application**

首先，有一个大的数据集 Big Data, 数学描述语言实际上它就是一个矩阵；模型 Model 实际上就是一个函数，该函数的作用是将 $x$ 映射到 $y$ ，模型中有许多未知的参数需要调整；预测值与真实值之间存在一定的误差，这时我们有一个部件叫 Loss 损失函数，该损失函数是关于这个模型参数的一个函数，用来评估预测值与真实值之间的误差；因此，有了这个损失函数Loss之后，还需要设计一套算法 Algorithm ，根据前面的误差，依据这套算法去调整模型的参数；然后我们再把输入样本送入模型中，比较输出的预测值与真实值之间的差距，当这个差距缩小到一定程度时，我们的算法就会停止。把上述这样的过程称之为训练Training，训练完毕之后就可以拿这个模型去做应用Application，应用后又可以获得一批新的数据，再将这些数据去训练原有模型，使其更适合当下的应用

机器学习的三要素：模型、算法与策略(又叫Loss)

## 线性回归

## 线性分类

## 无监督学习

## 强化学习

## EM算法
