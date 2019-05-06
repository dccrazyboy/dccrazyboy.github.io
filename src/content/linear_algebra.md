Title: 线性代数基础
Date: 2019-05-05
Slug: linear_algebra
Category: 机器学习
Tags: 线性代数

# 一、场景

线性代数简单来讲，是用来处理线性方程式相关的问题，从而让整个解法简单，容易理解。

例如对于下面的3个线性方程：

$$y_1 = 1 + 2 * x_1 + 3 * x_2\\
y_2 = 4 + 5 * x_1 + 6 * x_2\\
y_3 = 7+ 8 * x_1 + 9 * x_2$$

有如下样本数据：

$$
x_1, x_2\\
11,22\\
33,44\\
55,66\\
77,88
$$

需要计算出各自的$y_1, y_2, y_3$

如果按照常规的写法，可能类似于(python)：
```python
def f1(x1, x2):
    return 1 + 2 * x1 + 3 * x2
def f2(x1, x2):
    return 4 + 5 * x1 + 6 * x2
def f3(x1, x2):
    return 7 + 8 * x1 + 9 * x2

x = [
    (11,22),
    (33,44),
    (55,66),
    (77,88)
]
result = []
for x1, x2 in x:
    x_reslut = []
    for f in [f1, f2, f3]:
        x_reslut.append(f(x1, x2))
    result.append(x_reslut)

result
```
结果是：

```python
[[89, 191, 293], [199, 433, 667], [309, 675, 1041], [419, 917, 1415]]
```

写法较为复杂，用线性代数方式，可以通过构造两个矩阵
$$
X=
\begin{bmatrix}
1&11&22\\
1&33&44\\
1&55&66\\
1&77&88
\end{bmatrix}
$$

$$
Y=
\begin{bmatrix}
1&4&7\\
2&5&8\\
3&6&9
\end{bmatrix}
$$

然后通过 $X*Y$ 就可以计算出所有的结果(python+numpy)

```python
import numpy as np

X = np.array([
    [1,11,22],
    [1,33,44],
    [1,55,66],
    [1,77,88],
])
Y = np.array([
    [1,4,7],
    [2,5,8],
    [3,6,9],
])
np.dot(X, Y)
```
结果是：
```python
array([[  89,  191,  293],
       [ 199,  433,  667],
       [ 309,  675, 1041],
       [ 419,  917, 1415]])
```

这种方式不仅写法较为简单，而且都是矩阵操作，执行性能也非常高。

# 二、矩阵

一个$m*n$的矩阵是一个由$m$行（row）$n$列（column）元素排列成的矩形阵列。矩阵里的元素可以是数字、符号或数学式。以下矩阵$A$是一个由6个数字元素构成的2行3列的矩阵：

$$
A=
\begin{bmatrix}
1&2&3\\
4&5&6\\
\end{bmatrix}
$$

矩阵的概念比较简单，就是以指定的形式排列数据。

下面介绍几个特殊的矩阵：

1. 单位矩阵

一个$n$阶单位矩阵，是一个$n*n$的方形矩阵，其主对角线元素为1，其余元素为0，单位矩阵以$I_n$表示。例如：
$$
I_1 = 
\begin{bmatrix}
1
\end{bmatrix}
$$


$$
I_2 = 
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix}
$$

$$
I_3 = 
\begin{bmatrix}
1&0&0\\
0&1&0\\
0&0&1
\end{bmatrix}
$$

# 三、矩阵操作

## 3.1 矩阵加法 

只有维度相同的矩阵才能计算加法，将对应位置的元素相加即可，例如

$$
A=
\begin{bmatrix}
1&2&3\\
4&5&6\\
\end{bmatrix}
$$

$$
B=
\begin{bmatrix}
7&8&9\\
0&1&2\\
\end{bmatrix}
$$

$$
A+B=
\begin{bmatrix}
1+7&2+8&3+9\\
4+0&5+1&6+2\\
\end{bmatrix}
=
\begin{bmatrix}
8&10&12\\
4&6&8\\
\end{bmatrix}
$$