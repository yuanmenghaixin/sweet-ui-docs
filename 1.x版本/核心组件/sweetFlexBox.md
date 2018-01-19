# sweetFlexBox 弹性盒子 

> 基于目前的主流flexbox弹性盒子的布局方式来制定的一种sweet特有的盒子布局方式，所有都由`class`和`atr`控制

## 样式介绍

### 定义容器

#### .sw-flex/.sw-flex-show/.sw-flex-column

* 说明：定义一个父元素容器为伸缩容器，也就是弹性盒子容器。

#### .sw-flex-hide

* 说明：隐藏容器

### 排列方式

#### .sw-flex-row

* 说明：（默认值）在“ltr”排版方式下从左向右排列；在“rtl”排版方式下从右向左排列。

#### .sw-flex-row-reverse

* 说明：与`.sw-flex-row`排列方向相反，在“ltr”排版方式下从右向左排列；在“rtl”排版方式下从左向右排列。

#### .sw-flex-column

* 说明：类似于`.sw-flex-row`，不过是从上到下排列

#### .sw-flex-column-reverse

* 说明：类似于`.sw-flex-column`，不过是从下到上排列。

```
主轴起点与主轴终点方向分别等同于当前书写模式的始与结方向。其中“ltr”所指文本书写方式是“left-to-right”也就是从左向右书写；而“rtl”所指的刚好与“ltr”方式相反，其书写方式是“right-to-left”，也就是从右向左书写。
```

### 单行or多行

#### .sw-flex-nowrap

* 说明：（默认值）伸缩容器单行显示，“ltr”排版下，伸缩项目从左到右排列；“rtl”排版上伸缩项目从右向左排列。

#### .sw-flex-wrap

* 说明：伸缩容器多行显示，“ltr”排版下，伸缩项目从左到右排列；“rtl”排版上伸缩项目从右向左排列。

#### .sw-flex-wrap-reverse

* 说明：伸缩容器多行显示，“ltr”排版下，伸缩项目从右向左排列；“rtl”排版下，伸缩项目从左到右排列。（和`sw-flex-wrap`相反）

### 对齐方式 justify-content

> 这个是用来定义伸缩项目沿着主轴线的对齐方式。当一行上的所有伸缩项目都不能伸缩或可伸缩但是已经达到其最大长度时，这一属性才会对多余的空间进行分配。当项目溢出某一行时，这一属性也会在项目的对齐上施加一些控制。

![对齐方式](http://www.w3cplus.com/sites/default/files/styles/print_image/public/blogs/2013/flexbox-guide-2.jpg)

#### .sw-flex-left

* 说明：伸缩项目向一行的起始位置靠齐。

#### .sw-flex-center

* 说明：伸缩项目向一行的中间位置靠齐。

#### .sw-flex-right

* 说明：伸缩项目向一行的结束位置靠齐。


#### .sw-flex-space-between

* 说明：伸缩项目会平均地分布在行里。第一个伸缩项目一行中的最开始位置，最后一个伸缩项目在一行中最终点位置。

#### .sw-flex-space-around

* 说明：伸缩项目会平均地分布在行里，两端保留一半的空间。

### 对齐方式 align-item

> 这个主要用来定义伸缩项目可以在伸缩容器的当前行的侧轴上对齐方式。可以把他想像成侧轴（垂直于主轴）的“justify-content”。

![对齐方式](http://www.w3cplus.com/sites/default/files/styles/print_image/public/blogs/2013/flexbox-guide-3.jpg)

#### .sw-flex-top

* 说明：伸缩项目在侧轴起点边的外边距紧靠住该行在侧轴起始的边。

#### .sw-flex-middle

* 说明：伸缩项目的外边距盒在该行的侧轴上居中放置。

#### .sw-flex-bottom

* 说明：伸缩项目在侧轴终点边的外边距靠住该行在侧轴终点的边。

#### .sw-flex-stretch

* 说明：（默认值）伸缩项目拉伸填充整个伸缩容器。此值会使项目的外边距盒的尺寸在遵照「min/max-width/height」属性的限制下尽可能接近所在行的尺寸。

#### .sw-flex-baseline

* 说明：伸缩项目根据他们的基线对齐。


### 伸缩项目空间分配

#### .sw-flex-{number}

* 说明：number为1至6，代表在伸缩容器下根据number权重系数比例分配空间，根据伸缩容器的排列方式分配。

### 属性控制写法

属性 | 等效样式
--------- | -------------
`[sw-role='cell']`,`[sw-mode='x-equal']` | `.sw-flex`
`[sw-mode='y']`,`[sw-mode='y-equal']` | `.sw-flex-column`
`[sw-mode='wrap']` | `.sw-flex-wrap`
`[sw-show='true']` | `.sw-flex-show`
`[sw-show='false']` | `.sw-flex-hide`
`[sw-talign='left']` | `text-align: left`
`[sw-talign='center']` | `text-align: center`
`[sw-talign='right']` | `text-align: right`
`[sw-valign='bottom']` | `.sw-flex-bottom`且`.sw-flex-left`
`[sw-valign='middle']` | `.sw-flex-middle`且`.sw-flex-left`
`[sw-valign='top']` | `.sw-flex-top`且`.sw-flex-left`
`[sw-valign='baseline']` | `.sw-flex-baseline`
`[sw-align='center']` | `.sw-flex-center`且`text-align: center`
`[sw-align='right']` | `.sw-flex-right`且`text-align: right`
`[sw-align='left']` | `.sw-flex-left`且`text-align: left`
`[sw-valign='fit']` | `.sw-flex-stretch`
`[sw-layout='fit']` | `.sw-flex-1`
`[sw-flex='{1到6}']` | `.sw-flex-{1到6}`
`[sw-mode='{x或y}-equal']下的所有[sw-role='cell']元素 ` | 权重系数平均分配，即都为1



