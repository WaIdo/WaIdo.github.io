---
layout:     post
title:      Jupyter Notebook 高级-魔法命令
subtitle:   run、time、timeit
date:       2018-01-23
author:     Waldo
header-img: img/post-bg-coffee.jpg
catalog: true
tags:
    - 机器学习
---

# %run
> 作用：%run+空格+文件相对路径，可以在Jupter Notebook里面运行。
                可以将整个脚本加载进Notebook，可以直接调用脚本里面的函数。


![image.png](http://upload-images.jianshu.io/upload_images/7216746-e7cd16437893f614.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 如何加整个模块或者包加载进Notebook？
![image.png](http://upload-images.jianshu.io/upload_images/7216746-f22222ca14c364fc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# %timeit（后面只能接一句话）
> 帮助我们测试代码性能


![image.png](http://upload-images.jianshu.io/upload_images/7216746-0b4eaea00fcf98f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
运行1000次，选择其中最快的7次，算出一个平均值，得出运行这句话大约需要949 µs ± 276 µs。
![image.png](http://upload-images.jianshu.io/upload_images/7216746-99eef2c5dc67ff2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
循环多少次是由Jupter Notebook决定的。这里只运行了一次。
![image.png](http://upload-images.jianshu.io/upload_images/7216746-5f1c98d247022b2f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
这里运行了10000次。

# %%timeit
> 度量这个单元格内整理所消耗的时间
![image.png](http://upload-images.jianshu.io/upload_images/7216746-b8d25de4c5e6b297.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# %time
> 只执行一次

Wall time是人类所感知的时间。
![image.png](http://upload-images.jianshu.io/upload_images/7216746-613a6a8c53198689.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
但是，**一次数据具有不稳定性**
![image.png](http://upload-images.jianshu.io/upload_images/7216746-ccd04e33293936e0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# %%time
> 区域化测试执行一次代码的时间


![image.png](http://upload-images.jianshu.io/upload_images/7216746-ebe4bb08bba559f9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 其他魔法命令
![image.png](http://upload-images.jianshu.io/upload_images/7216746-0b6e1768e9de26f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


