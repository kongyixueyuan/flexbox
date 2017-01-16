



# 从零到壹玩转Flexbox
## 提纲
- CSS介绍
- 盒子模型
- 什么是flexbox
- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content
- order
- flex-grow
- flex-shrink
- flex-basis
- flex
- align-self

[Flexbox基础+项目实战视频](http://kongyixueyuan.com/course/default/view?friendlyUrl=http%3A%2F%2Fwww.kongyixueyuan.com%2Fcourse%2F2625)

有问题添加春哥微信：liyc1215

# CSS介绍

## 参考文档
- [http://www.css88.com/book/css/](http://www.css88.com/book/css/)
- [http://www.w3school.com.cn/css3/index.asp](http://www.w3school.com.cn/css3/index.asp)
- [http://www.runoob.com](http://www.runoob.com)

## 什么是层叠样式表
CSS是Cascading Style Sheet（层叠样式表）的缩写。是用于（增强）控制网页样式并允许将样式信息与网页内容分离的一种标记性语言。

## 样式语法

```css
Selector {property:value}
```

## 如何将样式表加入您的网页

你可以用以下三种方式将样式表加入您的网页。而最接近目标的样式定义优先权越高。高优先权样式将继承低优先权样式的未重叠定义但覆盖重叠的定义。

### 内联方式 Inline Styles
内联定义即是在对象的标记内使用对象的style属性定义适用其的样式表属性。

```css
示例代码：

<p style="color:#f00;">这一行的字体颜色将显示为红色</p>
```

### 内部样式块对象 Embedding a Style Block
你可以在你的HTML文档的`<head></head>`标记里插入一个`<style></style>`块对象,再在`<style></style>`里面插入如下代码。

```css
示例代码：

body {
  background:#fff;
  color:#000;
}
p {
  font-size:14px;
}

```

### 外部样式表 Linking to a Style Sheet
你可以先建立外部样式表文件*.css，然后使用HTML的link对象。

```css
示例代码：

<link rel="stylesheet" href="*.css" />
```
# Flex布局

网页布局（layout）是CSS的一个重点应用。

## 传统布局

[![cover](http://ojp7xe8x3.bkt.clouddn.com/chuantong.gif)](http://ojp7xe8x3.bkt.clouddn.com/chuantong.gif)

布局的传统解决方案，基于盒状模型，依赖 display属性 + position属性 + float属性。

## Flexbox 布局
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox.png)](http://ojp7xe8x3.bkt.clouddn.com/flexbox.png)
CSS Flexible Box Layout Module 简称 Flexbox Layout，Flexbox 布局是CSS3中一种新的布局模式，用于改进传统模式中标签对齐、方向、以及排序等等缺陷。

The prime characteristic of the flex container is the ability to modify the width or height of its children to fill the available space in the best possible way on different screen sizes.

最重要的特点是当父视图因为不同的屏幕而改变自身大小时，父视图可以动态的改变子视图的宽和高来尽可能的填充父视图可用的空间。

许多设计师和开发者发现flexbox布局更容易使用，元素的定位相对于传统布局只需要使用更少的代码即可实现，使开发过程更简单。

## 最新的flexbox支持的浏览器

- Chrome 29+
- Firefox 28+
- Internet Explorer 11+
- Opera 17+
- Safari 6.1+ (prefixed with -webkit-)
- Android 4.4+
- iOS 7.1+ (prefixed with -webkit-)

[查看浏览器支持特性](http://caniuse.com/#feat=flexbox).


## flexbox用法
要想使用 flexbox 布局只需要在父标签设置display属性即可:

```javascript
.flex-container {
  display: -webkit-flex; /* Safari */
  display: flex;
}
```

如果你希望你的子元素能够使用flexbox布局，你可以这样写：

```javascript
.flex-container {
  display: -webkit-inline-flex; /* Safari */
  display: inline-flex;
}
```

`Note`:这是让container能够使用flexbox布局的唯一属性，它能够让所有的子视图立刻变成flex items。

# 盒子模型

在我们开始学习flexbox相关属性之前，我们先介绍一下flexbox model。
## 类和对象的类比
类：它是抽象的概念，比如`div`，`p`，`span`，`input`等等标签

对象：对象是具体的东西，比如`<div></div>`,`<p />`,`<span></span>`, `<input />`等等


## 盒子模型结构

### 代码

```CSS
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>flexbox-model</title>
    <style>

        .flexbox-model-container {
            background-color: #FECE3F;
            width: 600px;
            height: 250px;
            display: flex;
        }

        .flexbox-model {
            background-color: green;
            width: 200px;
            height: 50px;
            padding: 50px;
            border: 10px solid red;
            margin: 20px;
        }
    </style>
</head>
<body>

<div class="flexbox-model-container">
    <div class="flexbox-model">
        flexbox-model
    </div>
</div>

</body>
</html>
```


### 效果图

[![cover](http://ojp7xe8x3.bkt.clouddn.com/Snip20170114_38.png)](http://ojp7xe8x3.bkt.clouddn.com/Snip20170114_38.png)

### width和height计算
盒子的宽度 = 效果图中蓝色边框的宽度

盒子的高度 = 效果图中蓝色边框的高度

### 标准的盒子模型结构图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/box-model.png)](http://ojp7xe8x3.bkt.clouddn.com/box-model.png)

## flex-container和flex-item之间的关系

```CSS

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>flexbox-model</title>
    <style>
        .flex-item {
            width: 120px;
            height: 120px;
            background-color: white;
            margin: 20px;
        }

        .flex-container {
            background-color: #FECE3F;
            width: 600px;
            height: 220px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    </style>
</head>
<body>

<div class="flex-container">
    <div class="flex-item">flex-item</div>
    <div class="flex-item">flex-item</div>
    <div class="flex-item">flex-item</div>
</div>

</body>
</html>
```

## 效果图解析
下图中黄色的图是`flex-container`,三个白色的正方形是`flex-item`,`flex-container`是`flex-item`的父视图，我们通常叫`容器`,`flex-item`是`flex-container`的子视图，我们通常叫做`项目`,`容器`中可以有多个`项目`，一个`项目`只有一个直接的`容器`，`容器`里面的多个`项目`有排列方向，下图中，三个项目的排列方向是从左到右排列，我们把和排列方向一致的这条线叫做`主轴`，另外一条线叫做`交叉轴`.

[![cover](http://ojp7xe8x3.bkt.clouddn.com/CSS3-Flexbox-Model.jpg)](http://ojp7xe8x3.bkt.clouddn.com/CSS3-Flexbox-Model.jpg)

## 容器的flexbox属性
- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content

## 项目的flexbox属性
- order
- flex-grow
- flex-shrink
- flex-basis
- flex
- align-self

# flex-direction
CSS flex-direction 属性指定了内部元素是如何在 flex 容器中布局的，定义了主轴的方向(正方向或反方向)。

请注意，值 row 和 row-reverse 受 flex 容器的方向性的影响。 如果它的 dir 属性是 ltr，row 表示从左到右定向的水平轴，而 row-reverse 表示从右到左; 如果 dir 属性是 rtl，row 表示从右到左定向的轴，而 row-reverse 表示从左到右。

## row
flex容器的主轴被定义为与文本方向相同。 主轴起点和主轴终点与内容方向相同。

### Value

```JavaScript
.flex-container {
  -webkit-flex-direction: row; /* Safari */
  flex-direction: row;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-row.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-row.jpg)


## row-reverse
表现和row相同，但是置换了主轴起点和主轴终点
### Value

```JavaScript
.flex-container {
  -webkit-flex-direction: row-reverse; /* Safari */
  flex-direction: row-reverse;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-row-reverse.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-row-reverse.jpg)

## column
flex容器的主轴和块轴相同。主轴起点与主轴终点和书写模式的前后点相同
### Value

```JavaScript
.flex-container {
  -webkit-flex-direction: column; /* Safari */
  flex-direction: column;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-column.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-column.jpg)

## column-reverse
表现和column相同，但是置换了主轴起点和主轴终点.
### Value

```JavaScript
.flex-container {
  -webkit-flex-direction: column-reverse; /* Safari */
  flex-direction: column-reverse;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-column-reverse.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-direction-column-reverse.jpg)


Default value: `row`
# flex-wrap
这是属性主要是设置container中的items是否会换行。

## nowrap
### Value

```JavaScript
.flex-container {
  -webkit-flex-wrap: nowrap; /* Safari */
  flex-wrap: nowrap;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-wrap-nowrap.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-wrap-nowrap.jpg)

## wrap
### Value

```JavaScript
.flex-container {
  -webkit-flex-wrap: wrap; /* Safari */
  flex-wrap: wrap;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-wrap-wrap.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-wrap-wrap.jpg)



## wrap-reverse
### Value

```JavaScript
.flex-container {
  -webkit-flex-wrap: wrap-reverse; /* Safari */
  flex-wrap: wrap-reverse;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-wrap-wrap-reverse.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-wrap-wrap-reverse.jpg)


Default value: `nowrap`
# flex-flow

flex-flow是flex-direction和flex-wrap的组合。

### Values

```js
.flex-container {
  -webkit-flex-flow: <flex-direction> || <flex-wrap>; /* Safari */
  flex-flow:         <flex-direction> || <flex-wrap>;
}
```
### Default value: `row nowrap`
# justify-content
`justify-content`主要用设置`flex items`在`容器`里面严着主轴的排列方式。

## flex-start
### Value

```JavaScript
.flex-container {
  -webkit-justify-content: flex-start; /* Safari */
  justify-content: flex-start;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-flex-start.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-flex-start.jpg)

## flex-end
### Value

```JavaScript
.flex-container {
  -webkit-justify-content: flex-end; /* Safari */
  justify-content: flex-end;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-flex-end.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-flex-end.jpg)

## center
### Value

```JavaScript
.flex-container {
  -webkit-justify-content: center; /* Safari */
  justify-content: center;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-center.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-center.jpg)

## space-between
### Value

```JavaScript
.flex-container {
  -webkit-justify-content: space-between; /* Safari */
  justify-content: space-between;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-space-between.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-space-between.jpg)

## space-around
### Value

```JavaScript
.flex-container {
  -webkit-justify-content: space-around; /* Safari */
  justify-content: space-around;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-space-around.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-justify-content-space-around.jpg)

Default value: `flex-start`
# align-items
当`flex items`在主轴上只有`一排`时，`align-items`属性主要用于设置`交叉轴`上`flex items`的排列方式。

## stretch
### Value

```JavaScript
.flex-container {
  -webkit-align-items: stretch; /* Safari */
  align-items: stretch;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-stretch.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-stretch.jpg)

## flex-start
### Value

```JavaScript
.flex-container {
  -webkit-align-items: flex-start; /* Safari */
  align-items: flex-start;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-flex-start.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-flex-start.jpg)

## flex-end
### Value

```JavaScript
.flex-container {
  -webkit-align-items: flex-end; /* Safari */
  align-items: flex-end;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-flex-end.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-flex-end.jpg)

## center
### Value

```JavaScript
.flex-container {
  -webkit-align-items: center; /* Safari */
  align-items: center;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-center.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-center.jpg)

## baseline
### Value

```JavaScript
.flex-container {
  -webkit-align-items: baseline; /* Safari */
  align-items: baseline;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-baseline.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-items-baseline.jpg)

Default value: `stretch`
# align-content
当`flex items`在主轴上有`多排(只有一排时此属性不起作用)`时，`align-content`属性主要用于设置`交叉轴`上`flex items`的排列方式。

## stretch
### Value

```JavaScript
.flex-container {
  -webkit-align-items: stretch; /* Safari */
  align-items: stretch;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-stretch.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-stretch.jpg)

## flex-start
### Value

```JavaScript
.flex-container {
  -webkit-align-items: flex-start; /* Safari */
  align-items: flex-start;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-flex-start.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-flex-start.jpg)

## flex-end
### Value

```JavaScript
.flex-container {
  -webkit-align-items: flex-end; /* Safari */
  align-items: flex-end;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-flex-end.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-flex-end.jpg)

## center
### Value

```JavaScript
.flex-container {
  -webkit-align-items: center; /* Safari */
  align-items: center;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-center.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-center.jpg)

## space-between
### Value

```JavaScript
.flex-container {
  -webkit-align-items: space-between; /* Safari */
  align-items: space-between;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-space-between.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-space-between.jpg)


## space-around
### Value

```JavaScript
.flex-container {
  -webkit-align-items: space-around; /* Safari */
  align-items: space-around;
}
```

### 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-space-around.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-content-space-around.jpg)

Default value: `stretch`
# order
`order`用于改变`容器`中`项目`的默认的排列顺序。

## Value

```js
.flex-item {
  -webkit-order: <integer>; /* Safari */
  order: <integer>;
}
```
## 效果图
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-order.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-order.jpg)
通过修改flex-item的值可以让flex items重新按照`order`值重新排列。

Default value: `0`
# flex-grow
`flex-grow`属性的默认值为`0`,当它为0时，尽管`flex-container`剩余很多多余的空间，但是当前的`flex-item`并不会自动伸缩以填充`flex-container`多余的空间。

其实我们可以这么总结，`flex-grow`属性值决定它相对与其他兄弟视图自动填充`flex-container`剩余空间的比例。

### Values

```js

.flex-item {
  -webkit-flex-grow: <number>; /* Safari */
  flex-grow:         <number>;
}

```
当所有的`item`的`flex-grow`的值相同时，他们所占据的空间相同。
[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-grow-1.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-grow-1.jpg)

下图中5个`flex-item`的比例关系为:`1:3:1:1:1`

[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-grow-2.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-grow-2.jpg)

Default value: `Default value: 0`
# flex-shrink

`flex-shrink`属性和`flex-grow`相反，默认值为`0`,当`flex-container`空间就算不够时，也不允许缩小，当`flex-shrink`的值为非`0`的正数时，表示当前`flex-item`相对与其他的`兄弟item`的缩小比例值。

### Value

```js

.flex-item {
  -webkit-flex-shrink: <number>; /* Safari */
  flex-shrink: <number>;
}

```

假设下图中除了`2`的`flex-shrink`值为默认值`0`，其他的都为`1`，那么当空间不足时，`2`并不会变小，其它的兄弟视图等比例缩小。

[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-shrink.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-shrink.jpg)


Default value: `1`
# flex-basis
制定某一个`item`在主轴上的大小，或者在主轴上相对于`flex-container`大小的比例关系。

### Value

```js
.flex-item {
  -webkit-flex-basis: auto | <width>; /* Safari */
  flex-basis:         auto | <width>;
}
```

### 效果图

[![cover](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-basis.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-flex-basis.jpg)

Default value: `auto`
# flex
`flex`是`flex-grow`, `flex-shrink` and`flex-basis`的缩写，`auto`等价于`1 1 auto`,`none`等价于`0 0 auto`.

```javascript
.flex-item {
  -webkit-flex: none | auto | [ <flex-grow> <flex-shrink>? || <flex-basis> ]; /* Safari */
  flex:         none | auto | [ <flex-grow> <flex-shrink>? || <flex-basis> ];
}
```
Default value: `0 1 auto`
# align-self

`align-self`主要用在当因为`flex-container`上的属性`align-items`属性改变了自己的状态但是又希望自己的状态和其它兄弟视图之间的状态不一样时，就可以使用`align-self`来的自身的状态进行设置。

```js
.flex-item {
  -webkit-align-self: auto | flex-start | flex-end | center | baseline | stretch; /* Safari */
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

[![](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-self.jpg)](http://ojp7xe8x3.bkt.clouddn.com/flexbox-align-self.jpg)

Default value: `auto`



