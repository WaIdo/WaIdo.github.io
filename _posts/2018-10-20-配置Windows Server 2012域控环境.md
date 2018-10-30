---
layout:     post
title:      配置Windows Server 2012域控环境,抓取域控和域用户hash
subtitle:   
date:       2018-10-20
author:     Waldo
header-img: img/post-bg-自然风景22.jpg
catalog: true
tags:
    - web安全 
    
---


# 主要任务
配置Windows Server 2012域控环境以及域用户的登录脚本和退出脚本，并抓取域控和域用户的hash

# 搭建域控环境
## 本地管理员登录
![本地管理员登录](https://upload-images.jianshu.io/upload_images/7216746-a9282e15807d3d32.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 设置静态IP
![设置静态IP](https://upload-images.jianshu.io/upload_images/7216746-790c97579d0aee5a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 安装Active Directory域服务
打开服务器管理器->仪表板->添加角色和功能->一直点下一步，直到在服务器角色中选择"Active Directory域服务"->在添加角色和功能向导中选择添加功能->一直点“下一步”直到“安装”->点击“安装”，等待安装完毕

![添加角色和功能](https://upload-images.jianshu.io/upload_images/7216746-4990541a8b85e524.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![安装Active Directory域服务](https://upload-images.jianshu.io/upload_images/7216746-4e6e1c5843f00164.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![点击“安装”](https://upload-images.jianshu.io/upload_images/7216746-d5c52672a2c26e3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![安装成功](https://upload-images.jianshu.io/upload_images/7216746-a807d711df829a9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 将此服务器提升为域控制器
回到【服务器管理器】界面，单击右上角【小旗子】，选择【将此服务器提升为域控制器】
![将此服务器提升为域控制器](https://upload-images.jianshu.io/upload_images/7216746-d2172fa84a2b0550.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 添加新林
在上一步弹出的窗口中添加新林，根域名填上域名称
![添加新林](https://upload-images.jianshu.io/upload_images/7216746-9683df070afe938e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 设置还原模式密码
请牢记密码，抓取Windows Server 2012 Hash中，某种特别情况下需要用到
![设置还原模式密码](https://upload-images.jianshu.io/upload_images/7216746-5574e07caab00bcd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 域控搭建完毕
一直下一步，安装完成后，系统会自动重启。【服务器管理器】界面左侧已经出现了管理的选项卡。
![AD DS](https://upload-images.jianshu.io/upload_images/7216746-682f3e288497b890.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 设置域控的域用户
此处以WinXP专业版作为域用户，家庭版无法添加到域

## 设置域用户静态IP，将DNS设置为域控的IP
![设置域用户静态IP，将DNS设置为域控的IP](https://upload-images.jianshu.io/upload_images/7216746-0b151bdbfdb93af2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 加入域控
![加入域控](https://upload-images.jianshu.io/upload_images/7216746-25b89be450ea8a26.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在弹出的窗口中，输入域控的用户名和密码
![输入域控的用户名和密码](https://upload-images.jianshu.io/upload_images/7216746-a691ad5d8a5f5e1d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在WinXP和WinServer2012，使用net view命令，查看域用户(WinXP)是否加入成功
![WinXP](https://upload-images.jianshu.io/upload_images/7216746-196a918233eeb457.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![WinServer2012](https://upload-images.jianshu.io/upload_images/7216746-d0fce06d29155c47.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 通过组策略设置域用户登录和注销脚本
在WinServer2012命令行运行```gpmc.msc```命令来启动启动“组策略管理编辑器”

在“组策略管理编辑器”左侧导航树上选择 “Default Domain Policy” -> 右键“编辑”->用户配置 -> 策略 -> Windows 设置 -> 脚本（登录/注销）

![步骤一](https://upload-images.jianshu.io/upload_images/7216746-0de13200ed81a9db.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![步骤二](https://upload-images.jianshu.io/upload_images/7216746-02c6bb0478cebcee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![步骤三](https://upload-images.jianshu.io/upload_images/7216746-1f13107306c4d958.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

双击 “登录”，在 “登录” 属性中添加上面的脚本。这里可以先在属性窗口的下部使用“显示文件”来查看默认脚本文件都放在什么地方，比如，在我的环境下是：
```
\\hiro.com\sysvol\hiro.com\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\User\Scripts\Logon
\\hiro.com\sysvol\hiro.com\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\User\Scripts\Logoff
```

将脚本放入上面的两个文件夹
![登录脚本](https://upload-images.jianshu.io/upload_images/7216746-424ee10992112ccd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![注销脚本](https://upload-images.jianshu.io/upload_images/7216746-a61277419e048e55.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

登录脚本代码：```Load.vbs```
```
MsgBox "Good morning", 48, "Title"
```
退出脚本代码：```Exit.vbs```
```
MsgBox "Bye Bye!", 64, "Title"
```
点击添加，将脚本的路径和文件名添加到登录属性的脚本
![添加登录脚本](https://upload-images.jianshu.io/upload_images/7216746-323cba1ac6aef279.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

当域用户开机时，将出现如下窗口：
![登录脚本运行](https://upload-images.jianshu.io/upload_images/7216746-ce972373ca8f4b0c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**“注销” 脚本和 “登录” 脚本类似。**

# 抓取域控和域用户hash
## 使用wce抓取hash
wce下载链接：
https://pan.baidu.com/s/1CxnyQCcTuUbFthQbMrjYaA 提取码: jkgj

以管理员运行cmd，切换到wce所在目录，输入命令```wce -l```即可
![使用wce抓取hash](https://upload-images.jianshu.io/upload_images/7216746-737070b7dc69546d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

第一行为域控(Win Server 2012)hash
第二行为域用户(WinXP)hash

## 使用mimikatz抓取hash
链接: https://pan.baidu.com/s/1N7Mml-LaoL8GF18JAlDZ0Q 提取码: 4cyy

mimikatz作为老牌的黑客工具已经升级到2.0的版本了，其中破解密码的功能也是非常方便，但对于杀软的防御也较弱，如果完全控制机器，关闭杀软也可，在msf中也要mimikatz的模块也可以在渗透中较为方便的获得密码

```
mimikatz# privilege::debug  //提升权限
mimikatz# sekurlsa::logonpasswords  //抓取密码
```

![使用mimikatz抓取hash](https://upload-images.jianshu.io/upload_images/7216746-7e785ea4d8b831de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个工具抓取的信息非常全面，甚至抓取到了明文密码
