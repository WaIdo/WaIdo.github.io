---
layout:     post
title:      matplotlib基础(绘制简单的图像)
subtitle:   绘制三角函数和散点图像
date:       2018-03-01
author:     Waldo
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - 机器学习
    - matplotlib
---

# matplotlib.pyplot.plot()，绘制三角函数图像
* 第一个参数是横坐标对应的值，第二个参数是纵坐标对应值
* 必须要调用matplotlib.pyplot..show()函数，才能显示出图形
![image.png](http://upload-images.jianshu.io/upload_images/7216746-4027b557b366ba98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-9fdc9dcea53ea08a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 绘制出正弦函数图形
![image.png](http://upload-images.jianshu.io/upload_images/7216746-d07df6195a3c473a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 在一幅图像内，绘制两条曲线
![image.png](http://upload-images.jianshu.io/upload_images/7216746-52a6a28b9e001783.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-86010d3f3b484c2c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 变换颜色，更改图线的样式
![image.png](http://upload-images.jianshu.io/upload_images/7216746-5d03cbc1871e48e4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-03f54fed0b9390b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-f1f23451922e4e20.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-8fe99b044e151cbc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 调整x、y轴的范围
![image.png](http://upload-images.jianshu.io/upload_images/7216746-b57d9e4078232a39.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-0a2ab17960a51bec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* matplotlib.pyplot.axis([x1, x2, y1 ,y2])同时调整x，y轴的范围
![image.png](http://upload-images.jianshu.io/upload_images/7216746-603966ee824a9810.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 给坐标轴添加字符串，matplotlib.pyplot.xlabel()
![image.png](http://upload-images.jianshu.io/upload_images/7216746-b6fe56eafc7239df.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 给具有多根曲线的图像，加上图示，注意在show()上方需要添加matplotlib.pyplot..legend()方法
![image.png](http://upload-images.jianshu.io/upload_images/7216746-fabd9fe1867740f1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 给整个图取一个标题，使用matplotlib.pyplot.title()
![image.png](http://upload-images.jianshu.io/upload_images/7216746-138600338b455efd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


# Scatter Plot（散点图）
**散点图的横、纵两个轴都是特征**
![image.png](http://upload-images.jianshu.io/upload_images/7216746-50bbc3c0165c8d99.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-0e430af25bd17526.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-c0e5e902b68fd1b0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-9748d66e0a151fe8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
加入alpha参数，改变透明度
![image.png](http://upload-images.jianshu.io/upload_images/7216746-68e505ec5485f3be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/7216746-3a842b21f1f76bdc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
