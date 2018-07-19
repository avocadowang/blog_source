---
title: '[转]5分钟学习js一些小技巧'
date: 2018-07-19 15:07:15
tags:
---
> 编者按：本文转载自 zhCN_超 的掘金专栏，原文链接 - Learn these neat JavaScript tricks in less than 5 minutes , 来一起学习吧！

##### 清空和截短数组
```
const arr = [11, 22, 33, 44, 55, 66];

// 截取
arr.length = 3;
console.log(arr); //=> [11, 22, 33];

// 清空
arr.length = 0;
console.log(arr); //=> []
console.log(arr[2]); //=> undefined
```
##### 使用对象结构模拟命名参数
以前，当我们希望向一个函数传递多个参数时，可能会采用配置对象的模式：
```
doSomething({ foo: 'Hello', bar: 'Hey!', baz: 42 });

function doSomething(config) {
  const foo = config.foo !== undefined ? config.foo : 'Hi';
  const bar = config.bar !== undefined ? config.bar : 'Yo!';
  const baz = config.baz !== undefined ? config.baz : 13;

  // ...

}
```
这是一个古老但是有效的模式，有了 ES2015 的对象结构，你可以这样使用：
```
function doSomething({ foo = 'Hi', bar = 'Yo!', baz = 13 }) { 
    // ...
}
```
如果你需要这个配置对象参数变成可选的，也很简单：
```
function doSomething({ foo = 'Hi', bar = 'Yo!', baz = 13 } = {}) {
    // ...
}
```
##### 数组的对象解构
使用对象解构将数组项赋值给变量：
```
const csvFileLine = '1997,John Doe,US,john@doe.com,New York';
const { 2: country, 4: state } = csvFileLine.split(',');
```
* 注：本例中，2 为 split 之后的数组下标，country 为指定的变量，值为 US
##### switch 语句中使用范围
这是一个在 switch 语句中使用范围的例子：
```
function getWaterState(tempInCelsius) {
  let state;

  switch (true) {
    case (tempInCelsius <= 0):
      state = 'Solid';
      break;
    case (tempInCelsius > 0 && tempInCelsius < 100):
      state = 'Liquid';
      break;
    default:
      state = 'Gas';
  }
  return state;
}
```
##### await 多个 async 函数
await 多个 async 函数并等待他们执行完成，我们可以使用 Promise.all：
```
await Promise.all([anAsyncCall(), thisIsAlsoAsync(), oneMore()])
```
##### 创建纯对象
你可以创建一个 100% 的纯对象，这个对象不会继承 Object 的任何属性和方法（比如 constructor，toString() 等）：
```
const pureObject = Object.create(null);
console.log(pureObject); //=> {}
console.log(pureObject.constructor); //=> undefined
console.log(pureObject.toString); //=> undefined
console.log(pureObject.hasOwnProperty); //=> undefined
```
##### 格式化 JSON 代码
JSON.stringify 不仅可以字符串化对象，它也可以格式化你的 JSON 输出：
```
const obj = {
  foo: {
    bar: [11, 22, 33, 44],
    baz: {
      bing: true,
      boom: 'Hello'
    }
  }
};

// 第三个参数为格式化需要的空格数目

JSON.stringify(obj, null, 4);

// =>"{
  // => "foo": {
    // => "bar": [
      // => 11,
      // => 22,
      // => 33,
      // => 44
    // => ],
    // => "baz": {
      // => "bing": true,
      // => "boom": "Hello"
    // => }
  // => }
// =>}"
```
##### 移除数组重复项
使用 ES2015 和扩展运算符，你可以轻松移除数组中的重复项：
```
const removeDuplicateItems = arr => [...new Set(arr)];
removeDuplicateItems([42, 'foo', 42, 'foo', true, true]);
//=> [42, "foo", true]
```
* 注：只适用于数组内容为基本数据类型
##### 扁平化多维数组
使用扩展运算符可以快速扁平化数组：
```
const arr = [11, [22, 33], [44, 55], 66];
const flatArr = [].concat(...arr); //=> [11, 22, 33, 44, 55, 66]
```
不幸的是，上面的技巧只能适用二维数组，但是使用递归，我们可以扁平化任意纬度数组：
```
function flattenArray(arr) {
  const flattened = [].concat(...arr);
  return flattened.some(item => Array.isArray(item)) ? flattenArray(flattened) : flattened;
}

const arr = [11, [22, 33],[44, [55, 66, [77, [88]], 99]]];
const flatArr = flattenArray(arr);
//=> [11, 22, 33, 44, 55, 66, 77, 88, 99]
```

