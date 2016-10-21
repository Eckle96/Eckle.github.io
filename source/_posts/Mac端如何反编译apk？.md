---
title: Mac端如何反编译apk？
date: 2016-10-21 09:30:14
tags: 反编译
---
### 前情提要

今天上班的时候，我的一位专于web安全的网友联系我，让我帮忙分析一款app的架构和运行方式。虽然之前没有弄过这一块，但是出于好奇，也希望在安卓相关方面多接触点陌生的东西，我欣然地接受了。分析一款app，首先需要拿到源码，而拿到源码的第一步就是反编译，本篇文章我们来讲解反编译的工具的使用，因本人使用的是Mac电脑，所以本片文章基于Mac平台。

### 下载反编译工具

反编译用到的相关工具主要有三个，分别为：
* dex2jar
* jd-gui
* AndroidCrackTool

三者的作用分别是：
* 将dex文件转为jar文件
* 查看jar包里的源码
* 字节码转源码


反编译工具已上传csdn，[点击这里](http://download.csdn.net/detail/wj_november/9657372)跳转下载页面。

### 使用反编译工具

反编译工具的使用操作步骤如下：

1. 得到dex文件
使用解压工具将apk安装包解压缩，在解压后的文件根目录下得到以**classes.dex**命名的dex文件。

2. dex文件转jar文件
下载好反编译工具并解压后得到命名为**dex2jar-0.0.9.15**的文件夹，将**classes.dex**文件拷贝至该文件夹下，打开终端，执行命令：
```
cd dex2jar-0.0.9.15文件路径
shdex2jar.shclasses.dex
```
待命令行如下图所示，表示文件转换成功：
![图片截自Terminal](http://upload-images.jianshu.io/upload_images/291600-bd2fbeba071a5a95.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
转换成功后，可在dex2jar目录下找到**classes-dex2jar.jar**文件。

3. 查看源码
安装jd-gui软件，并在该软件中打开**classes-dex2jar.jar**文件，可以看到工程包下的源码：
![图片截自jd-gui](http://upload-images.jianshu.io/upload_images/291600-aeb2abdcc2c1fd68.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
因apk的代码经过混淆，所以我们查看到的类名多为abcd等形式，尽管如此，我们依然可以通过源码中的细节去推敲类的作用。

### 查看manifest.xml配置文件

若我们查看混淆后的源码有些吃力，查看manifest文件可以帮助我们分析，里面包含了所有的activity、权限、服务等信息。但是查看直接解压后的manifest文件，我们可以看到里面只有十六进制的字节码，这时候我们需要用到AndroidCrackTool工具。

![图片截自AndroidCrackTool](http://upload-images.jianshu.io/upload_images/291600-e8646bcd2701f4a7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击**浏览**选择需要反编译的apk文件，点击**打开**选择crack后的文件路径，点击执行，待控制台窗口显示如上图，则说明crack结束。打开crack后的文件夹，打开其中的manifest.xml，即可查看apk的配置文件。

本人对反编译的掌握尚处于认识的程度，若有过来人对于如何分析源码有好的建议，欢迎在文章下方评论交流！