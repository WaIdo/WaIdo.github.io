---
layout:     post
title:      如何在PyCharm同时配置python 2和3？
subtitle:   
date:       2018-02-25
author:     Waldo
header-img: img/post-bg-e2e-ux.jpg
catalog: true
tags:
    - 机器学习
    - 终端
---

PyCharm是IDE，和系统中的python环境无关。可以在系统中安装好两个python版本，之后再使用pycharm的时候，选择相应的python版本作为解析器即可。

![图片发自简书App](http://upload-images.jianshu.io/upload_images/7216746-6defd0e8c6089694.jpg)


不过由于不同的框架也存在Python版本以来的问题，所以如果使用Python的其他框架，还存在一个Python的其他相关库管理的问题。其实Anaconda提供非常方便的虚拟环境功能，可以使用Anaconda直接创建一个另外版本Python的虚拟环境，之后再PyCharm中进行选择。

以下截图就是我在我的机子上同时创建有Python3和Python2.7的环境：
![图片发自简书App](http://upload-images.jianshu.io/upload_images/7216746-c2e0b4de2627cd6c.jpg)


具体Anaconda中虚拟环境的管理方法，可以参考官方文档：
[https://conda.io/docs/user-guide/tasks/manage-environments.html](https://conda.io/docs/user-guide/tasks/manage-environments.html)或者自行搜索中文社区是否有详细介绍使用方法的文章：）

