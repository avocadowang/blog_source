---
title: javaScript引用类型之Array
date: 2018-04-25 16:11:08
tags:
---
#### 总结<js高级教程>Array常用的18个api
* 栈方法(LIFO数据结构--last in first out 最新添加的项最早被移除)
 1 .`push()`接受任务数量参数,把他们逐个添加到末尾,返回`修改后数组的长度`
2 .`pop()`方法从末尾移除一项,减少数组length值,返回`移除的项`


![image.png](https://upload-images.jianshu.io/upload_images/1808957-abd6e2a3c3a77a5f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 队列方法(FIFO--先进先出)
   3 .`shift()`移除数组第一项,返回`插入的项`--对立`pop()`
   4 .`unshift()`插入元素在数组前,返回`新数组长度`--对立`push()`
![image.png](https://upload-images.jianshu.io/upload_images/1808957-6d2cc456c8595fa6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 重排序方法
  5 .`reverse()`反转数组顺序
  6 . `sort()`升序排序
*注意:sort排序有时会出错,例如[0,1,5,10,15]排序后[0,1,10,15,5],原因是sort会把数组每一项转成字符串后比较=>`为啥"10" < "5"???`*
排序推荐用
```
function compare(value1,value2) {
  if (value1 < value2){
    return -1;
 } else if (value1 > value2) {
    return 1;
} else {
  return 0;
}
```
```
reverse()和sort()返回进过排序的数组,会改变原数组
```
* 操作方法
  7 .`concat()`如果传递的值是一或多个数组,该方法会将数组中每一项添加到结果数组中.如果传递的不是数组,则添加到结果数组的结尾`返回新数组,不改变原数组 `.
![image.png](https://upload-images.jianshu.io/upload_images/1808957-a2bba032d5130992.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
8 .`slice()`接受`一或两个参数`,表示起始位置,如果为1个则末尾为最后一个`返回新数组,不改变原数组,可传入负数 `.
![image.png](https://upload-images.jianshu.io/upload_images/1808957-aad16e56df282c26.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
9 .`splice()`用于向数组中插入项,有三种用法`返回从原始数组中删除的项,如果没删除返回空数组,改变了原数组`
`删除`:两个参数--(第一项的位置 , 删除的个数);
`插入`:三个参数--(起始位置 ,0(要删除的项), 要插入的项(如有多个可添加四五及多个项))
`替换`:三个参数--(起始位置 ,1(要删除的项数), 要插入的项(如有多个可添加四五及多个项))
![image.png](https://upload-images.jianshu.io/upload_images/1808957-53cda8a392eb2652.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 位置方法
10 .`indexOf()`
11 .`lastIndexOf()``返回所查元素下标,查不到返回-1,不改变原数组`
都两个参数--(要查找的内容,查找的起始位置(可选,默认0))
![image.png](https://upload-images.jianshu.io/upload_images/1808957-ca1d66abbf362bec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/1808957-b22ebc327538813c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*由上图知不包含当前位置元素*
* 迭代方法
12 .`every()`对数组中的每一项给定函数,如果函数的每一项都返回true,则返回true.
![image.png](https://upload-images.jianshu.io/upload_images/1808957-3f0297bad2224f46.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
13 .`filter()`对数组中的每一项运行给定函数,返回该函数返回true项组成的数组.
![image.png](https://upload-images.jianshu.io/upload_images/1808957-0588dd5787b18b6a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
14 .`forEach()`对数组中的每一项运行给定函数,无返回值.
`本质上与for循环迭代一样`
15 .`map`对数组中的每一项运行给定函数,返回函数调用结果组成的数组.
![image.png](https://upload-images.jianshu.io/upload_images/1808957-ea2aae223fd492c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
16 .`some`对数组中的每一项运行给定函数,若任一项返回true则返回true
![image.png](https://upload-images.jianshu.io/upload_images/1808957-8be516199e57100b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*以上方法都不修改数组的值*
* 归并方法
17 .`reduce()`
18 .`reduceRight()`迭代数组所有项,`返回最终值`
两个参数--(一个函数(该函数接受四个参数pre,cur,index,array),初次迭代的项(可选));
![image.png](https://upload-images.jianshu.io/upload_images/1808957-3e3153f06b4b6862.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/1808957-31be692ddabdc901.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/1808957-eb5010ad7c72a622.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


*两个的不同就是从哪头开始遍历,其余完全相同*
#### 改变原数组的有 push,pop,shift,unshift,reverse,sort,splice七个
#### 不改变的有concat,slice,indexOf,lastIndexOf,every,filter,some,forEach,map,reduce,reduceRight 十一个



