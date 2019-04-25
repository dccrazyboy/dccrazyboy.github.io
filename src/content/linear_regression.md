Title: 线性回归
Date: 2019-04-25
Slug: linear_regression
Category: 机器学习
Tags: 回归, 线性模型

# 一、例子

有些数据间存在着线性的关系，因此可以用线性模型学习，先举个例子，构造一个简单的模型，其中X为特征，y为目标

```python
import numpy as np
from sklearn.linear_model import LinearRegression
data = np.array([
    [1, 2], 
    [2, 4], 
    [3, 6], 
    [4, 8]
])

X = data[:,0].reshape(-1, 1)
y = data[:,1]

print X
print y
```

```python
[[1]
 [2]
 [3]
 [4]]
[2 4 6 8]
```

很容易看出来，这个模型可以用 $y=2*x$ 来表示。

使用sklearn的 LinearRegression 进行fit和predict
```python
reg = LinearRegression().fit(X, y)
reg.predict(X)
```

```python
array([2., 4., 6., 8.])
```

可以看到预测的结果跟原始输入完全一致，看下特征系数

```python
print reg.coef_
```
```python
[2.]
```

很明显，模型学到了我们的模式 $y=2*x$ 

# 二、线性回归

线性回归（Linear Regression）是利用称为线性回归方程的最小二乘函数对一个或多个自变量和因变量之间关系进行建模的一种回归分析。

线性回归的思路很简单，通过构造一个线性函数，来预测目标的值

$y=w_0*x_0 + w_1*x_1 + ... + w_n*x_n + b$

例如上面的 $y=2*x$ 就是一个单自变量的线性模型，多变量的线性模型例如$y=2*x_0 + 3*x_1 + 4$  

因此，模型的核心问题，在于如何确定$(w_0, w_1, ... w_n, b)$ 的值，让y的误差最小。

较为通用的，一般是**最小二乘法**

# 三、最小二乘法



参考：

1. [sklearn.linear_model.LinearRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html){:target="_blank"}
2. [wikipedia-线性回归](https://zh.wikipedia.org/wiki/%E7%B7%9A%E6%80%A7%E5%9B%9E%E6%AD%B8){:target="_blank"}
