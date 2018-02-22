---
layout:     post
title:      PHP strcmp函数漏洞
subtitle:   
date:       2018-2-22
author:     Waldo
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - iOS
    - iOS开发基础
---

# strcmp函数的返回值
![strcmp.jpg](http://upload-images.jianshu.io/upload_images/7216746-1d0ac039e83286f6.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

首先贴上官方文档的说明
> Note a difference between 5.2 and 5.3 versions
   echo (int)strcmp('pending',array());
   will output -1 in PHP 5.2.16 (probably in all versions prior 5.3)
   but will output 0 in PHP 5.3.3
   Of course, you never need to use array as a parameter in string comparisions.

意思是：在php 5.2版本之前，利用strcmp函数将数组与字符串进行比较会返回-1，但是从5.3开始，会返回0

示例代码：
```
<?php
  error_reporting();
  $flag=$_GET['flag'];
  if(strcmp('Waldo_cuit',$flag)){
      echo 'NO!';
   }
  else{
      echo 'YES!';
  }
?>
```
当传入flag[]=1时，会导致
```0 = strcmp('Waldo_cuit',$flag)```，也就是```flase = strcmp('Waldo_cuit',$flag)```，显示出 Yes!。大家可以自行测试一下~~~
在ctf里可以用这个漏洞绕过判断条件，这里附一道Bugku的题[前女友](http://47.93.190.246:49162/)
