---
title: Android Studio导入第三方库的三种方法
date: 2016-10-18 12:46:33
tags: android
---
### 叨叨在前

今天在项目中使用一个图片选择器的第三方框架——GalleryFinal，想要导入源码，以便于修改，于是上网查找了一下方法，想到之前用到过其他导入第三方库的方法，现在做个小总结，以防忘记。

* Android Studio导入第三方库的方法我个人知晓的有三种：
  * **Gradle抓取**
  * **libs导入**
  * **源码导入**

### Gradle抓取

Gradle抓取的方法最为简单，只需在Project->app文件夹下的build.gradle文件中添加依赖：

![build.gradle文件夹所在位置](http://upload-images.jianshu.io/upload_images/291600-4ff128ec46edc624.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在builde.gradle文件中制定位置添加如下代码：

![compile 'cn.finalteam:galleryfinal:1.4.8.7'](http://upload-images.jianshu.io/upload_images/291600-3f6058943db1948e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后同步一下工程即可。

### libs导入

将从网上下载对应的第三方库的jar包放入Project->app文件夹下的libs文件夹：

![libs文件夹所在位置](http://upload-images.jianshu.io/upload_images/291600-6b3092d9f4012cf3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后在单击jar包右键，选择“Add as library...”可实现导入；或者在我们上述的build.gradle文件中添加依赖：

![compile files('libs/galleryfinal.jar')](http://upload-images.jianshu.io/upload_images/291600-1cf670f13303bf32.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 源码导入

选择Android Studio菜单栏File->New->import Module...，弹出窗口选择Module的路径：

![](http://upload-images.jianshu.io/upload_images/291600-9f22f5114f0051e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

找到下载好的第三方库，找到其中用的Module：

![](http://upload-images.jianshu.io/upload_images/291600-de58119e5e1fbe13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

选择galleryfinal，点击OK。

同步一下工程，会出现这样的报错信息：

![](http://upload-images.jianshu.io/upload_images/291600-bf6de9766cc64a23.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击“Open File”，找到错误的地方：

![导入库的build.gradle位置](http://upload-images.jianshu.io/upload_images/291600-a3c2a478faa31244.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/291600-fd333bcbdd72f698.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

将“project_version”修改为版本名称，如`"1.0"`:

![](http://upload-images.jianshu.io/upload_images/291600-223fd59af2ee134b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

再次同步工程，又会出现报错信息：

![](http://upload-images.jianshu.io/upload_images/291600-ba52452d67b0ae3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

原因是找不到bintray.gradle文件，查找了以下网上的解决方法是删除或注释掉第三方库的build.gradle文件中的：

```
apply from: "../bintray.gradle"
```
然后我们继续同步工程，会发现Android Studio一直停留在：

![](http://upload-images.jianshu.io/upload_images/291600-dd0f800445d77738.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这是因为第三方库需要用到相应的jar文件或gradle文件或arr文件，如果觉得这个过程太慢，可以考虑以下方法：
* 翻墙
* 手动下载相应文件，参考：[听说你Android Studio更新Gradle很慢](http://www.jianshu.com/p/069514ef0d06)
* 放弃治疗，等待下载完毕

**这里强调一下**：*当项目中引入第三方源码库数量比较多时，工程的编译时间会非常漫长，所以为了提高效率，在没有修改源码的需求前提下，不建议使用源码方式引入第三方库。*

推荐：
一款优秀的本地图片选择框架[GalleryFinal](https://github.com/pengjianbo/GalleryFinal)