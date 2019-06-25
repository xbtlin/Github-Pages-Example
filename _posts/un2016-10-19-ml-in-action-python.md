---
layout:     post
title:      机器学习实战读书笔记python
category: blog
description: ..
---

SciPy和NumPy使用底层语言（C和Fortran）编写。

Python清晰简练，易于理解，不足是性能问题。可以用Python编写实验程序，然后用C替换核心代码以改进性能。

	>>> from numpy import *
	>>> random.rand(4,4)
	array([[ 0.0060785 ,  0.63564272,  0.01711972,  0.45528635],
       [ 0.33130262,  0.77913325,  0.76410941,  0.73594375],
       [ 0.47316152,  0.83300403,  0.28350677,  0.09444501],
       [ 0.5635714 ,  0.08921871,  0.51945807,  0.04997578]])
       
	>>> eye(4)
	array([[ 1.,  0.,  0.,  0.],
       [ 0.,  1.,  0.,  0.],
       [ 0.,  0.,  1.,  0.],
       [ 0.,  0.,  0.,  1.]])
    >>> randMat = mat(random.rand(4,4)) # 数组传换成矩阵
    >>> randMat.I   # 求矩阵的逆
    >>> 