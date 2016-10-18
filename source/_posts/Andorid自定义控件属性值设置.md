---
title: Andorid自定义控件属性值设置
date: 2016-10-18 12:31:29
tags: android
---
### 背景提要

今天写一个简单的自定义控件，实现宽固定，高度根据自定义宽高比例自动调整；或高固定，宽度随比例调整。其中有一个 `solid`属性，想要像*android:layout_width="match_parent"* 里的**match_parent**一样可以输入标记表示一定的意义，这里的`solid`表示固定的是宽还是高，如：

```
app:solid="solid_width" // solid_height
```

### 找源码

我们知道自定义控件的属性是定义在attrs.xml文件里的，所以猜测Android自带的属性也为定义在其sdk的attrs.xml文件里到如下的路径下：

```
// 我使用的是版本23的sdk
/sdk/platforms/android-23/data/res/values/attrs.xml
```

因layout_width的属性有match_parent和我们想要实现的效果一致，我们可以搜索一下`layout_width`找找线索：

![sdk自带attrs.xml](http://upload-images.jianshu.io/upload_images/291600-f6da58b3f569395f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

我们可以看到除了通常定义的attr，还要在attr结点的节点内部添加enum常量。

### 具体实现

找到了模板，我们便可以依样画葫芦，编写下面的代码：

* attrs.xml里定义属性
```
<declare-styleable name="ScaleView">
    <attr name="scale" format="float" />
    <attr name="solid" format="integer">
        <enum name="solid_width" value="-1" />
        <enum name="solid_height" value="-2" />
    </attr>
</declare-styleable>
```

* 自定义控件java实现
```
public class ScaleImageView extends ImageView {
    // 常量标记：固定宽度
    public static final int SOLID_WIDTH = -1;
    // 常量标记：固定高度
    public static final int SOLID_HEIGHT = -2;
    
    // 常量标记：未设置比例
    private static final float NO_SCALE = -1;
    
    // 宽高比
    private float mScale = NO_SCALE;
    // 固定标记
    private int mSolid = SOLID_WIDTH;
    public ScaleImageView(Context context) {
        this(context, null);
    }
    public ScaleImageView(Context context, AttributeSet attrs) {
        this(context, attrs, 0);
    }
    public ScaleImageView(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
        TypedArray ta = context.obtainStyledAttributes(attrs, R.styleable.ScaleView);
        // 获取宽高比
        mScale = ta.getFloat(R.styleable.ScaleView_scale, NO_SCALE);
        // 获取固定标记
        mSolid = ta.getInteger(R.styleable.ScaleView_solid, SOLID_WIDTH);
    }
    @Override
    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        if (mScale < 0) {
            super.onMeasure(widthMeasureSpec, heightMeasureSpec);
            return;
        }
        // 计算ImageView的宽度
        int width = 0;
        // 根据自定义的宽高比例，高度适当比例改变
        int height = 0;
        if (mSolid == SOLID_WIDTH) {
            width = MeasureSpec.getSize(widthMeasureSpec);
            height = (int) (width / mScale);
        } else if (mSolid == SOLID_HEIGHT) {
            height = MeasureSpec.getSize(heightMeasureSpec);
            width = (int) (height * mScale);
        } else {
            super.onMeasure(widthMeasureSpec, heightMeasureSpec);
            return;
        }
        // 将重新定义后的宽度和高度设置为图片显示的大小
        setMeasuredDimension(width, height);
    }
}
```

* 布局中使用自定义控件
```
<自己应用的包名.ScaleImageView
    xmlns:custom="http://schemas.android.com/apk/res-auto" /*这句话可以定义在根节点*/
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:src="@drawable/img"
    android:scaleType="centerCrop"
    custom:scale="1.38"
    custom:solid="solid_width"/>
```

参考：
[Android:xml中使用的属性值定义值哪里？](http://blog.csdn.net/annkie/article/details/8315349)