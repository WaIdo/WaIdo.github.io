---
layout:     post
title:      PHPforeach循环语句
subtitle:   用于数组
date:       2018-04-27
author:     Waldo
header-img: img/post-bg-自然风景7.jpg
catalog: true
tags:
    - PHP
---

在PHP 5中，foreach循环只能用于数组和对象的循环。
该语句的语法格式为：

```
foreach (array_expression as  $value)
         statement;
或
foreach (array_expression as $key => $value)
         statement;
```

foreach循环语句将遍历数组array_expression。每次循环时，将当前数组中的值赋给$value(或$key和$value)，同时，将数组指针向后移动直到遍历结束。当使用foreach循环语句时，数组指针自动被重置，所以不需要手动设置指针位置。
例:

```
<?php	
	$name=array("1"=>"智能机器人","2"=>"数码相机","3"=>"天翼5G手机","4"=>"瑞士手表");
	$price=array("1"=>"14998元","2"=>"2588元","3"=>"2666元","4"=>"66698元");
	$counts=array("1"=>1,"2"=>1,"3"=>2,"4"=>1);
	foreach ($name as $key => $value) {
		# code...
		echo "商品名称: $value"." 商品单价:".$price[$key]." 购买数量: ".$counts[$key]." 总价格: ".$counts[$key]*$price[$key];
		echo "<p>";
	}
?>
```
运行结果：
![image.png](https://upload-images.jianshu.io/upload_images/7216746-c6d7378acc7ea032.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

