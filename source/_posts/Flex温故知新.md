---
title: Flex温故知新
date: 2017-12-04 20:17:15
tags:
---


温故知新,今天来有空整理巩固一下它们的使用方法.
关于兼容性
![截至2017-12-04,完整部分请点击如下链接](http://upload-images.jianshu.io/upload_images/1808957-91826b01fd5cf18a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

参考自[caniuse网](https://caniuse.com/#search=flex)

1.在父级添加flex
```
<style>
			.parent{
				border:1px solid red;
				width: 100px;
				height: 30px;
				display: flex;
			}	
			.child{
				width: 30px;
				background: aquamarine;
			}
			
		</style>
	</head>
	<body>
		<div class="parent">
			<div class="child">1</div>
			<div class="child">2</div>
			<div class="child">3</div>
		</div>
	</body>
```
效果
![image.png](http://upload-images.jianshu.io/upload_images/1808957-af1b1875e61fc193.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
添加`display:inline-flex`亦可.
*注意:设为flex布局后子元素float属性失效.*(一些教程上说的子元素vertical-align失效亲测无效)
```
.child{
				width: 30px;
				background: aquamarine;
				float: right;
			}
```
![image.png](http://upload-images.jianshu.io/upload_images/1808957-a8199357d3f34337.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.容器的6个属性
2.1 flex-direction(元素的排列方向)
它有四个属性`row/row-reverse/column/column-reverse`(行列顺序及逆序),默认为row效果如上两图
![row-reverse](http://upload-images.jianshu.io/upload_images/1808957-531c1e44316bf517.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![column](http://upload-images.jianshu.io/upload_images/1808957-d9afae73915ceabc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![column-reverse](http://upload-images.jianshu.io/upload_images/1808957-28f51daa83e525d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.2 flex-wrap(定义一行排不下元素时的换行规则)
它的3个属性`nowrap/wrap/wrap-reverse`
###flex实例换行无效待更(有坑)
2.3 flex-flow
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为`row nowrap`。
2.4 justifty-content(元素在主轴上的对齐方式)
它有5个属性`flex-start/flex-end/center/space-between/space-around`

![flex-start(左对齐)](http://upload-images.jianshu.io/upload_images/1808957-bee424cceee94f8d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![flex-end(右对齐)](http://upload-images.jianshu.io/upload_images/1808957-13bec72a2bc3e355.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![center(居中)](http://upload-images.jianshu.io/upload_images/1808957-688eff448f5a7c5d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![space-between(两端对齐)](http://upload-images.jianshu.io/upload_images/1808957-a150b97d8eec2d13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![space-around(每个元素左右相等)](http://upload-images.jianshu.io/upload_images/1808957-89d79efcef79d44d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.5 align-items(垂直方向的对齐方式)
它有5个属性`flex-start/flex-end/center/strecth/baseline`
![上基线](http://upload-images.jianshu.io/upload_images/1808957-8aac4c31e3d42bd4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![下基线](http://upload-images.jianshu.io/upload_images/1808957-8dc583be1efe45cf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![居中](http://upload-images.jianshu.io/upload_images/1808957-30b583d91eaa6a29.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![baseline(首字基线,例子中首字加大了)](http://upload-images.jianshu.io/upload_images/1808957-e481ff7cedff6447.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![stretch(默认)](http://upload-images.jianshu.io/upload_images/1808957-cf054e8d4174c19f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.6 align-content(多根轴线竖直方向对齐方式)
3.添加在元素上的属性
基本6个`order/flex-grow/flex-shrink/flex-basis/flex/align-self`
1.order:定义项目排列顺序,数值越小,项目也靠前
![order](http://upload-images.jianshu.io/upload_images/1808957-fb13219e1d4975b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/1808957-46ad457298bc8ce8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.flex-grow:项目放大比例(默认1)
3.flex-shrink:项目缩小比例(默认0)
4.flex-basis:分配多余空间之前,项目占的主轴空间(默认auto)
5.flex:flex-grow,flex-shrink,flex-basis的简写,默认0 1 auto
它的两个快捷值auto(1 1 auto)和none(0 0 auto),建议优先使用这个属性
6.align-self
允许单个项目与其他项目不一样的对齐方式.
它的6个属性`auto | flex-start | flex-end | center | baseline | stretch`



参考:[阮一峰的博客](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)


























