---
layout:     post
title:      Python之operator.itemgetter函数和sorted函数
subtitle:   Python
date:       2018-07-23
author:     Waldo
header-img: img/post-bg-FaceTheSea.jpg
catalog: true
tags:
    - Python 
    
---

# operator.itemgetter函数

operator模块提供的itemgetter函数用于获取对象不同维的数据(理解看下面的例子),参数为需要获取的 数据在对象中的序号：

```
from operator import itemgetter
#从operator模块导入itemgetter函数 
>>> a=[1,2,3]
>>> b=itemgetter(1)
>>> b=(a)
2

>>> b=itemgetter(0,1)
>>> b(a)
(1,2)
```

要注意,operaot.itemgetter函数获取的不是值，而是定义了一个函数，通过该函数作用到对象上才能获取值。

# sorted函数

Python内置的排序函数sorted可以对list获知iterator进行排序。

该函数原型为：```sorted(iterable[, cmp[, key[, reverse]]])```

参数解释：
* [literable](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/00143178254193589df9c612d2449618ea460e7a672a366000)为指定要排序的可迭代对象

* cmp为函数，指定排序时进行比较的函数，可以指定一个函数或者lambda函数

例：

students为一个list，每个成员有三个域，用sorted函数进行比较时可以自己定按照什么进行排序，也就是设定cmp函数。这里要按照第三个域来排序：

```
>>> students = [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
>>> sorted(students, key=lambda student : student[2])
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

* key为函数，指定取待排序元素的哪一项进行排序，举例如下：

```
>>> students = [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
>>> sorted(students, key=lambda student : student[2]) 
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

key指定的lambda函数功能是去元素student的第三个域（即：student[2]），因此sorted排序时，会以students所有元素的第三个域来进行排序。

有了上面的```operator.itemgetter```函数，也可以用该函数来实现，例如要通过student的第三个域排序，可以这么写：

```sorted(students, key=operator.itemgetter(2)) ```

sorted函数也可以进行多级排序，例如要根据第二个域和第三个域进行排序，可以这么写：

```sorted(students, key=operator.itemgetter(1,2)) ```

#  综合示例

假设我们用一组tuple表示学生名字和成绩：

```
L = [('Bob', 75), ('Adam', 92), ('Bart', 66), ('Lisa', 88)]
```

用```sorted```对上述列表按名字排序，再按成绩从低到高排序，以及按照成绩从高到低排序：

```
from operator import itemgetter
students = [('Bob', 75), ('Adam', 92), ('Bart', 66), ('Lisa', 88)]

print(sorted(students, key=itemgetter(0)))
print(sorted(students, key=lambda t: t[1]))
print(sorted(students, key=itemgetter(1), reverse=True))
```

![综合示例.png](https://upload-images.jianshu.io/upload_images/7216746-12f71945a9a91143.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


