---
title: Markdown语法入门及工具推荐
date: 2016-10-18 12:49:59
tags: 
---

前段时间学习了一下Markdown语法，现在记录一下，希望可以给初学者们带来帮助。

### 标题

标题可根据字体的大小分为六个级别，分别用若干个`#`表示。

【效果】
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题

【输入】

```
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题
```

我们也可以使用这样的形式来显示一级标题和二级标题：

【效果】
这是一个一级标题
============================
这是一个二级标题
--------------------------------------------------

【输入】

```
这是一个一级标题
============================
这是一个二级标题
--------------------------------------------------
```

### 文本

文本的显示形式可分为粗体、斜体两种，通过在文本前后输入若干个`*`。

【效果】
**这是粗体**
*这是斜体*
***这是斜体+粗体***

【输入】

```
**这是粗体**
*这是斜体*
***这是斜体+粗体***
```

### 图片

图片的输入语法为：
\!\[图片内容](图片链接)

【效果】

![我的简书个人主页](http://upload-images.jianshu.io/upload_images/291600-f1aa74cf4c14c6c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

【输入】

```
![我的简书个人主页](http://upload-images.jianshu.io/upload_images/291600-f1aa74cf4c14c6c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```

**注意**：这里的`!`、`[`、`]`、`(`、`)`均为英文输入法，且简书平台Markdown编辑器只要将图片文件拖入输入区域，即可生成Markdown文本，猿猿们只要修改描述图片的文本即可。

如果输入的图片链接找不到图片，其效果为：

![找不到图片了](aaa)

除了静态图片，Markdown支持Gif动图：

【效果】
![动图效果](http://upload-images.jianshu.io/upload_images/291600-3b00271942fef854.gif?imageMogr2/auto-orient/strip)

【输入】

```
![动图效果](http://upload-images.jianshu.io/upload_images/291600-3b00271942fef854.gif?imageMogr2/auto-orient/strip)
```

### 链接

链接的语法与图片类似，只要在图片的基础上去掉`!`即可。

【效果】

[这个是简书平台的链接](http://jianshu.com)

【输入】

```
[这个是简书平台的链接](http://jianshu.com)
```

### 列表

列表可分为**有序列表**和**无序列表**。

**无序列表**可通过在每行文本前输入`*`、`+`、`-`来实现。

【效果】

* **星号**实现的列表
* 记得符号与文本之间有一个**空格**
- **减号**实现的列表
+ **加号**实现的列表

【输入】

```
* **星号**实现的列表
* 记得符号与文本之间有一个**空格**
- **减号**实现的列表
+ **加号**实现的列表
```

**有序列表**可通过在每行文本前面输入`数字`+`.`+`空格`来实现。

【效果】
1. 第一行
这是第一行的内容
2. 第二行
这是第二行的内容
3. 第三行
这是第三行的内容
我是占位行
4. 第四行
这是第四行的内容

【输入】

```
1. 第一行
这是第一行的内容
2. 第二行
这是第二行的内容
3. 第三行
这是第三行的内容
我是占位行
4. 第四行
这是第四行的内容
```
### 引用

**引用**即我们文章中摘抄他人文章中写的内容，其可以通过 `>`来实现。

【效果】

> 这是一段引用文章的文字，此处省略1000字。。。

【输入】

```
> 这是一段引用文章的文字，此处省略1000字。。。
```

PS: 因引用文本底色与简书默认文本底色色差明显，所以本猿以**引用**作为文章段落的标题以明显区分文章不同部分，*纯属个人习惯*。

### 行内代码块

**行内代码块**可用于关键字词，将其与普通文本区分开来，其用法为在文字内容开始与结尾添加"\`"。

【效果】

`这是行内代码块`

【输入】

```
`这是行内代码块`
```

### 代码块

**代码块**实则为行内代码快的扩展，用于将多行代码或文本内容与其他文本内容区分开来，其效果如下：

【效果】

        public int add(int a, int b) {
            return a + b;
        }

【插入】

*实际输入为每一行代码前面加上4个Tab键或8个空格键。*

***注意***：简书的Markdown环境下，多行代码前需留出一个空行才能显示效果！

### 加强代码块

**加强代码块**是代码块的增强版，省去了多行代码每行输入Tab键的烦恼，只要在多行代码的开始和结尾输入"\`\`\`"即可。

【效果】

```
public int add(int a, int b) {
    return a + b;
}
```

【输入】

```
```
public int add(int a, int b) {
    return a + b;
}
` ` ` // 因为结尾的三个`在代码框里不好输入，在`之间用空格隔开，实际没有空格
```

### 表格

表格的语法主要用到的符号为`|`、`-`、`:`，我们先来看看效果：

【效果】

|默认|居中|左对齐|右对齐|
|--|:-:|:-|-:|
|换行\n换行失败|简书Markdown|不支持|换行|
|*支持斜体*|**粗体**|***斜体+粗体***||
|# 不支持标题|[支持链接](http://jianshu.com)|![支持图片](http://img1.imgtn.bdimg.com/it/u=627177226,2113594557&fm=15&gp=0.jpg)|`支持行内代码块` |

【输入】

```
|默认|居中|左对齐|右对齐|
|--|:-:|:-|-:|
|换行\n换行失败|简书Markdown|不支持|换行|
|*支持斜体*|**粗体**|***斜体+粗体***||
|# 不支持标题|[支持链接](http://jianshu.com)|![支持图片](http://img1.imgtn.bdimg.com/it/u=627177226,2113594557&fm=15&gp=0.jpg)|`支持行内代码块` |
```

猿猿们可以看到，表格的第一行默认为粗体居中，表格的其他语法，大家看【输入】+实际操作自己体会吧！

### 删除线

对于线的显示，Markdown也提供了支持，包括：

【效果】

~~删除线~~

【输入】

```
~~删除线~~
```


以上是本猿针对最最基本的Markdown用法对其进行了罗列，当然猿猿们也可以在其他平台上看到Markdown更加高阶的用法，如：[cmd Markdown](https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown#fn:footnote)对原声Markdown进行了更进一步的封装和扩展，可支持LaTex、Todo列表、Toc目录、Mermaid 序列图等，Markdown是一个很有意思的工具，感兴趣的猿猿们可以进行更进一步的探索！

### 分割线

分割线可使用`*`、`-`来实现。

【效果】

---
***

【输入】

```
---
***
```


---

### 附录一 Markdown工具

Markdown工具可分为**在线**和**客户端**两种，接下来本猿带领大家来看看Mac端Markdown熟悉工具。

**【在线】**

***[简书](http://jianshu.com)***

![图片来自简书](http://upload-images.jianshu.io/upload_images/291600-486b29859e021c70.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

猿猿们，如果你写**简书**还没有用过**Markdown**，本猿强烈推荐你尝试一下，相信你会爱上它的，正如我之前提到过的，Markdown让我放下了CSDN、Lofter的博客平台，提高了我写文章的速度和频率，让我从此痴迷其中！

**简书**设置Markdown编辑器方法如下：

![图片来自简书](http://upload-images.jianshu.io/upload_images/291600-89e5fc65cf97ad71.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击齿轮图标，进入设置；

![图片来自简书](http://upload-images.jianshu.io/upload_images/291600-6248d4b5443b6901.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

选择**基础设置**选项，在下方**选择常用的编辑器**选择`Markdown`，然后点击`保存`按钮即可；

![图片来自简书](http://upload-images.jianshu.io/upload_images/291600-cc0bf1c046d4b055.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**简书Markdown**可支持实时预览，这个功能带来了非常棒的用户体验，就好比刚开始学习Html的猿猿们，每输入一个字符都感觉自己完成了一项成就，***赞！***

***[作业部落](https://www.zybuluo.com)***

![图片来自作业部落](http://upload-images.jianshu.io/upload_images/291600-db35a832a1ecd54c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**作业部落**这个名字乍一听，有点学生气，有点小学时候用的错题本的感觉，但是其功能是非常强大的，**支持实时预览**，对Markdown进行了非常**完美的封装**，正如它说的“**Cmd Markdown是世界上最好的Markdown语言**”，用这句话形容它应该是不为过的，我们来看一下：

```
它支持
1. Todo列表
2. LaTex公式
3. 简易流程图
4. 序列图
5. 甘特图
6. TOC目录
7. 标签分类
8. 注脚
9. Mermaid 流程图
10. Mermaid 序列图
11. 定义型列表
12. 内嵌图标
```

可以说，使用Cmd Markdown完成一篇比较专业的学术论文是没问题的。本猿的Markdown语法就是从这里开始起步的，但是它有一个致命的缺点，就是：

**它太完美了，像毒品一样给人致命的依赖，导致一旦转移到其他Markdown平台，用户有一种`攀过五岳，从此看其他山都是平地`的感觉。**

正因为它封装地太多，在其他Markdown平台，一些功能用不了，所以本猿丢弃了这个***毒品***，转向更具有普适性的**简书Markdown**。

PS: 作业部落同时支持客户端，在线同步，可离线保存。

***[马克飞象](https://maxiang.io)***

![图片来自马克飞象](http://upload-images.jianshu.io/upload_images/291600-7299bfc2163bb81a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果你是**印象笔记**迷，那么**马克飞象**可以说是你的福音了，它支持将文本存到印象笔记，且功能特性与**作业部落**无几，但是有一点让人遗憾的是：

***马克飞象是一款收费软件，在10天的试用期结束后，只有通过收费才能继续使用！***

![图片来自马克飞象客户端](http://upload-images.jianshu.io/upload_images/291600-22e4e4b56b70be34.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

PS：同**作业部落**一样，**马克飞象**也支持客户端，支持本地缓存。

***[有道云笔记](http://note.youdao.com)***

![图片来自有道云笔记](http://upload-images.jianshu.io/upload_images/291600-ece80fd826efb38f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

或许你听惯了**有道词典**，这个八竿子打不着的**词典**与**Markdown**突然有一天走到一起产生了爱情的火花，诞生出了**有道云笔记**，想想就感觉像***吉利收购了沃尔沃***，再高端的东西被低端拿下了后多少印象分会大打折扣。

![图片来自有道云笔记](http://upload-images.jianshu.io/upload_images/291600-b9e1cf6d891de5b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

是的！你没看错，这就是有道云笔记，不得不说，**有道**支持**Markdown**确实吸引了不少路人粉。

![图片来自有道云笔记](http://upload-images.jianshu.io/upload_images/291600-2db580ea7b5f9563.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

有一个功能有道云笔记做的确实不错，就是可以**将自己的笔记发布到网上，他人可以像浏览网页一样查看自己的记录**。

***[小书匠](http://soft.xiaoshujiang.com)***

![图片来自小书匠](http://upload-images.jianshu.io/upload_images/291600-264af054aaa12c24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**小书匠**是一款内容丰富的个性化Markdown编辑工具，为什么说它个性化呢？我们来看看它的功能：

```
支持：
1. 全屏预览
2. 实时可获取html代码
3. 自定义CSS样式
4. 多方式预览：普通预览、ppt预览、pdf预览
5. 多种预览排版方式：上、下、左、右、浮动
6. 内容可以标题为节点隐藏
7. 映射关系
8 大纲查看，自动生成目录
```

![图片来自小书匠](http://upload-images.jianshu.io/upload_images/291600-902c6f72b766a08c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**土豪金**配上**经典黑**就足以闪瞎我们凡人的双眸，高逼格、高内涵、~~高血压~~高品质的Markdown编辑器，你值得拥有！

PS：这里强调一下：**小书匠支持windows、Linux、Mac、Web多端编辑！**

**【客户端】**

除了以上同时支持客户端的在线Markdown编辑器外，我们来说说其他的客户端Markdown编辑器。

***[Mou](http://25.io/mou/)***

![图片来自Mou](http://upload-images.jianshu.io/upload_images/291600-6fccd4a7583f4bef.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Mou**是本猿尝试的第一款Markdown客户端软件，支持最基本的Markdown语法，界面简洁。因其主题风格不是很心仪，后来本猿将它Kill掉了-_-#，但这并不影响Markdown迷们对它的喜爱！

***[MacDown](http://macdown.uranusjr.com)***

![图片来自MacDown](http://upload-images.jianshu.io/upload_images/291600-9f3ecabdc091dce1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**MacDown**是本猿使用Markdown编辑器以来用的最久的一款，其主题样式和预览效果都还是不错的，重要的是：它**开源*免费***，***免费***，***免费***，***免费！***

但是它有一个不足，就是：一个窗口只能打开一个文件，这就显得比较鸡肋了，后来本猿又将MacDown杀掉了-_-||

***[Atom](https://atom.io)***

![图片来自Atom](http://upload-images.jianshu.io/upload_images/291600-ead6377370329138.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Atom**是一款很强大比较成熟稳定的一款Markdown编辑器，支持多文件显示，文件目录缩进，有丰富的插件，其插件的下载方式为：

```
Preferences->install->想要插件的名称->搜索->下载
```

然后重启Atom即可，目前本猿正在使用这款APP。

***[Sublime](http://www.sublimetext.com)***

![图片来自Sublime](http://upload-images.jianshu.io/upload_images/291600-fdfb0c42a819590b.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Sublime**是一款通用型编辑器。**如果说Atom是17世纪的物理牛顿，那么Sublime就是15世纪的全能达芬奇。**之所以提到Sublime，是因为Sublime支持Markdown**插件**，通过安装下载，Sublime也同样可以实现Markdown编辑器的效果，但是它的预览还是挺鸡肋的，它只能像Html一样，在浏览器中预览，而且**不支持实时预览**。但是毕竟是老牌编辑器，强大的通用性让其在编辑器领域鹤立鸡群。

PS: 本文Markdown工具推荐借鉴自：[好用的Markdown编辑器一览](http://www.williamlong.info/archives/4319.html)，其中还包括windows端和Linux端的工具推荐，感兴趣可以看一下！

以上就是本猿对Markdown浏览器的推荐，上述每一张图片（除了Mou）都是都是本猿重新安装APP后截图得到的。嗯！非常实诚的笔者，如今已不多见了，本猿被自己感动到了-_-||

**如果猿猿们觉得这篇文章有用，请戳一戳文章下方的*喜欢*，*感谢大家的阅读！***