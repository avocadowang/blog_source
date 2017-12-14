---
title: 谈谈JavaScript的Date
date: 2017-12-06 13:59:50
tags:
---
>在日常工作中总会用到Date相关的各种''姿势'',有时候总需要查阅一下文档才能使用,虽然与它相关的API有许多,但根据二八定律,常用的应该就一小部分,今天来整理一下它的常用部分巩固基础,熟记下来以后应用时可以省去不少时间.

首先new一个对象
![image.png](http://upload-images.jianshu.io/upload_images/1808957-277645a259c26377.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###  `var myTime = new Date();`
#### 1.最常用最基本的是获取年月日时分秒毫秒
分别对应
```
var year = myTime.getFullYear()//年
var month = myTime.getMonth()//月(0~11分别对应1~12月,对应要加1)
var date = myTime.getDate()//日(1~31)
var hour = myTime.getHours()//时(0~23)
var min = myTime.getMinutes()//分(0~59)
var sec = myTime.getSeconds()//秒(0~59)
var millSec = myTime.getMilliseconds()//毫秒(0~999)
```
>1.需要注意的是 月 和 星期几 对应的`getMonth()`和`getDay()`对应的数是从0开始所以具体结果要加1
>2.时分秒及毫秒要加"s"

`var time = myTime.getTime();//获取1970年1月1日至今毫秒数`
#### 2.设置时间把get换成set即可使用规则一样
#### 3.相互间的转换
```
var timeString = myTime.toString();//把日期装成字符串格式
```
![image.png](http://upload-images.jianshu.io/upload_images/1808957-77bf033e1ca79e77.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
var time1 = myTime.toTimeString();//把对象的时间部分转化成字符串
```
```
var time2 = myTime.toDateString();//日期部分转字符串
```
![image.png](http://upload-images.jianshu.io/upload_images/1808957-b0566e374a2c9eb3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
var time3 = myTime.toLocaleString();//Date对象转换成本地时间格式字符串
```
```
var time4 = myTime.toLocaleTimeString();//时间转换成本地时间格式
```
```
var time6 = myTime.toLocaleDateString();//Date对象的日期转成字符串
```
```
var time5 = myTime.toUTCString;//根据世界时间将Date()对象转成字符串
```
![image.png](http://upload-images.jianshu.io/upload_images/1808957-0101541d6014de08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
var timeJson = myTime.toJSON();//返回json数据格式的日期
```
![image.png](http://upload-images.jianshu.io/upload_images/1808957-17ebc8f1320f01aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
var time7 = Date.parse(myTime.toString);//1970.1.1到现在的毫秒数
```
![image.png](http://upload-images.jianshu.io/upload_images/1808957-3200e6f36c2ef8a7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
工作中常常对日期格式有一些要求,数量熟练以上方法后可以根据自己需求封装日期函数,减少代码量









