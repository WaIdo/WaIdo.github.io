---
layout:     post
title:      scikit-learn中的机器学习算法封装
subtitle:   
date:       2018-03-09
author:     Waldo
header-img: img/post-bg-林间小路1.jpg
catalog: true
tags:
    - 机器学习
    - 机器学习算法
---

# 将kNN简便型算法写在kNN.py文件里
> 不是规范的scikit-learn格式

* 复习%run魔法命令
![image.png](https://upload-images.jianshu.io/upload_images/7216746-331e315282507fb4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/7216746-b6c2ffb8b294f8d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 传入数据得出预测值
![image.png](https://upload-images.jianshu.io/upload_images/7216746-a31e152ee135c1f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 通过kNN深入理解什么是机器学习
![image.png](https://upload-images.jianshu.io/upload_images/7216746-74629914a74cda96.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
kNN算法可以直接将输入样例送给训练数据集，投票得出预测值，k近邻算法可以被认为没有模型的算法，为了和其他算法统一，可以认为训练数据集就是模型本身。

# 使用scikit-learn中的kNN
![image.png](https://upload-images.jianshu.io/upload_images/7216746-2739c39f93932042.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/7216746-daf1e84e975d7f2b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


# 重新整理我们的kNN的代码
![image.png](https://upload-images.jianshu.io/upload_images/7216746-4717615eeca6adf1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## **kNN算法代码**
```
import numpy as np
from math import sqrt
from collections import Counter
from .metrics import accuracy_score

class KNNClassifier:

    def __init__(self, k):
        """初始化kNN分类器"""
        assert k >= 1, "k must be valid"
        self.k = k
        self._X_train = None
        self._y_train = None

    def fit(self, X_train, y_train):
        """根据训练数据集X_train和y_train训练kNN分类器"""
        assert X_train.shape[0] == y_train.shape[0], \
            "the size of X_train must be equal to the size of y_train"
        assert self.k <= X_train.shape[0], \
            "the size of X_train must be at least k."

        self._X_train = X_train
        self._y_train = y_train
        return self

    def predict(self, X_predict):
        """给定待预测数据集X_predict，返回表示X_predict的结果向量"""
        assert self._X_train is not None and self._y_train is not None, \
                "must fit before predict!"
        assert X_predict.shape[1] == self._X_train.shape[1], \
                "the feature number of X_predict must be equal to X_train"

        y_predict = [self._predict(x) for x in X_predict]
        return np.array(y_predict)

    def _predict(self, x):
        """给定单个待预测数据x，返回x的预测结果值"""
        assert x.shape[0] == self._X_train.shape[1], \
            "the feature number of x must be equal to X_train"

        distances = [sqrt(np.sum((x_train - x) ** 2))
                     for x_train in self._X_train]
        nearest = np.argsort(distances)

        topK_y = [self._y_train[i] for i in nearest[:self.k]]
        votes = Counter(topK_y)

        return votes.most_common(1)[0][0]

    def score(self, X_test, y_test):
        """根据测试数据集 X_test 和 y_test 确定当前模型的准确度"""

        y_predict = self.predict(X_test)
        return accuracy_score(y_test, y_predict)

    def __repr__(self):
        return "KNN(k=%d)" % self.k



```
