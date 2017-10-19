---
title: javscript-exercise
date: 2017-10-07 19:38:21
tags: JS
---

## 判断对象
用`typeof obj ===‘object’ `判断`obj`是否是一个`object`：

```javascript
var obj = {
  name: 'xiaoming'
}

function output(obj) {
  if (typeof obj.name === 'object') {
    console.log(obj.name);
  } else {
    console.log('obj is not a object');
  }
}

output(obj);
```
[以上代码有缺陷吗？如果有，该如何改进？](https://github.com/xugy0926/getting-started-with-javascript/issues/640)


有缺陷。

1. 因为`typeof null`的结果也是`object`，但在js中`null`实际上并不是对象，为保证`obj = null`时也能正确判断，所以需要加上对`null`的判断`if (typeof obj === 'object' && obj !== null) `;
2. 如果该函数是用于判断任意变量或直接量是否是对象的，那么使用`obj.name`就不合逻辑了。因为不是所有对象都有`name`的属性的。为了和`else`的结果对应，为对象时输出`console.log(‘obj is an object')`比较符合写函数的目的。
3. `output`函数在接收参数传入时，如果参数正好是`null`，`null`也是object类型，而`null.name`会导致代码运行报错。因此一定要排除特殊情况`null`。
4. 至于传入的`obj`是否有无`name`，这个最少不会导致代码运行出错，`obj.name`即使没有也会默认输出一个`undefined`。是否必要判断`obj`中存不存在`name`，可以依据具体的业务情况来定夺。

**修正后的代码：**
```javascript
var obj = {
  name: 'xiaoming'
}

function output(obj) {
  if (!obj && typeof obj === 'object') {
    console.log('obj is an object');
  } else {
    console.log('obj is NOT a object');
  }
}

output(obj);
```

**参考：**
【null和undefined】犀牛书3.4章节
【逻辑与（&&）】犀牛书4.10.1章节
【typeof 运算符】犀牛书4.13.2章节

---

## 对象的属性差异
对象是JS中最重要的概念之一。在定义对象时，有以下两种方法：

**”属性定义“** 大法（常用）：
```javascript
var obj = {
  name: 'xiaoming',
  age: 18,
  isStudent: true  
}
```
上面`obj`有3个属性，分别是`name`、`age`、`isStudent`。

 **”键值定义“** 大法：
```javascript
var obj = {
  "name": 'xiaoming',
  "age": 18,
  "isStudent": true  
}
```
”键值定义“对象方式和json对象格式一样，这也是为什么在js中，所谓的json对象和普通对象经常混为一谈。

[这两种方式的共同点是什么？差异又是什么？](https://github.com/xugy0926/getting-started-with-javascript/issues/642)

### 使用时的差异点

定义对象时可以混搭
```javascript
var obj = {
  'name': 'xiaoming',           // 键值
  age: 18,                      // 属性
  isStudent: true               // 属性
}
```

正常访问属性
```javascript
// 通过键访问name
console.log(obj['name'])        // ==> xiaoming

// 通过属性访问age
console.log(obj.age)            // ==> 18
```

也可以反过来
```javascript
// 通过属性访问name
console.log(obj.name)          // ==> xiaoming

// 通过键值访问age  
console.log(obj['age'])        // ==> 18
```
通过以上事例，可以认为不管是属性还是键值，都可以随意用属性访问方式或键值访问方式来访问内容。但真的是这样吗？

下面的定义做点变化：
```javascript
var obj = {
  'my name': 'xiaoming',      // 键是‘my name’，有一个空格
  age: 18,                    // 属性
  isStudent: true             // 属性
}

console.log(obj['my name']);    // ==> xiaoming
console.log(obj.my name);       // ==> error!!!!
```
此时，`'my name'`只能通过键值访问方式来访问内容，而不能用属性方式

键值方式可以采用任意字符，哪怕是中文也可以。
```javascript
var obj = {
  '姓名': 'xiaoming',             // 键是‘my name’，有一个空格
  age: 18,                        // 属性
  isStudent: true                 // 属性
}
console.log(obj['姓名']);         // ==> xiaoming
```

**总结**
**1. 键可以用任意字符，不满足js的变量命名方式也可以。**
**2. 属性必须满足js的变量命名方式才可以。**

### 键是可以是一个表达式的值
当键是一个表达式值时，设置和访问时都是可以动态计算的。

```javascript
var list = ['xiaoming', 'xiaohua'];
var obj = {};
for (var i = 0; i < list.length; i++) {
  obj['name=' + list[i]] = list[i];
}

console.log(obj);  // ==> { 'name=xiaoming': 'xiaoming', 'name=xiaohua': 'xiaohua' }
```

**总结**

1. 键可以是表达式，动态构建，访问时也可以动态构建键。
2. 属性不具备这个特性。

### 不管是键值还是属性，都适用于值为函数时

```javascript
var obj = {
  '姓名': function () {
    console.log('xiaoming');
  },
  age: function () {
    console.log(18)
  },
}

obj['姓名']();
obj.age();
```

**总结: 用键值还是属性，主要考虑键和属性的命名差异点，至于后面的值是什么类型无所谓。**

### 构建动态的键，有什么应用场景

比如前端会按照分页的方式从服务端获取数据，那么每一页的数据都可以通过动态构建键的方式存储在obj对象中。

```javascript
var obj = {};

getData(page) {
  axios.get('url', params: {page}).then(function (response) {
    obj['page=' + page] = response.data;
  });
}

getData(1);
getData(2);
getData(3);

以上obj感觉像是一个键值对的数据库对象，再使用内容时操作起来很方便。
```
**参考：**
[第一次使用JSON](https://github.com/xugy0926/getting-started-with-javascript/blob/master/topics/%E7%AC%AC%E4%B8%80%E6%AC%A1%E4%BD%BF%E7%94%A8JSON.md)

---


## [对象的浅拷贝](https://github.com/xugy0926/getting-started-with-javascript/issues/643)
```javascript
var obj = {
  count: 1
}

function output(obj) {
  obj.count = obj.count + 1;
  console.log(obj.count);
}

output(obj);
console.log(obj.count);
```
在上面代码之后，执行下面代码分别输出什么？

1. 假如两个值不一样，为什么？
2. 假如两个值一样，为什么？有没有办法保证output函数内的obj.cout的改变不影响外面的obj.count？

**解答：**
```javascript
var obj = {
  count: 1
}

var anotherObj = {
  count: 1
}

console.log(anotherObj == obj);       // ==> false
```
分别定义了`obj`和`anotherOjb`，他们的对象实体内容虽然都一样，但还是不同的对象。
对象赋值并不是等于复制对象，而是引用。

```javascript
var obj = {
  count: 1
}

var anotherObj = obj;

console.log(anotherObj === obj);        // ==> true
```
此时`anotherObj`和`obj`是指向同一个对象实体。anotherObj此时是obj的引用，引用就像别名一样。
通过以上判断，可以认为两者是同一个对象。

```javascript
function output(obj) {
  obj.count = obj.count + 1;
  console.log(obj.count);
}
```
基于以上分析，`output`函数的形参对象变量其实就是实参变量的引用，所有他们是同一个。
在output函数内为了不影响真正的obj实体，有两种方式。

```javascript
function output(obj) {
  obj = Object.assign({}, obj);
  obj.count = obj.count + 1;
  console.log(obj.count);
}

function output(obj) {
  obj = JSON.parse(JSON.stringify(obj));
  obj.count = obj.count + 1;
  console.log(obj.count);
}
```
以上两种方式都是对形参obj对象重新“复制”一份新的对象。


## 数组元素和数组对象属性
```javascript
var obj = {
  count: 1
}

var myArray = ['red', 'white', 'black'];
console.log(myArray.length);        // ==> 3

myArray.obj = obj;
console.log(myArray.length);        // ==> 3
```
两次打印myArray的length是多少？为什么？

**解答：**
1. js中一切都是对象。包括函数也是对象。对象可以动态添加属性值。
2. 数组也是对象，只不过这个对象恰好有一个别的数据类型不具备的特点，可以通过索引来访问。

因为数组是对象的特殊形式，它同样有着属性名的概念，但和对象不同的是它使用0~2^32-2之间的整数属性名作为数组的索引，当不指定属性名时默认使用索引作为属性名。而length属性值，即数组的方法.length的值始终等于当前最大索引+1。

本例里初始赋值自动为三个元素建立了索引，最大索引为2。第一次myArray.length = 2 + 1，所以是3。而后加入的obj由于属性名obj不是索引，自然不影响索引号和length的值，所以第二次输出myArray.length还是3。

如果把obj在myArray中属性名改成符合索引格式的值，那么myArray.length的值就会改变了，而且不一定要接着索引2。代码如下：
```javascript
var obj = {
  count: 1
}

var myArray = ['red', 'white', 'black'];
console.log(myArray.length);

myArray["5"] = obj;
console.log(myArray.length);
```

---

## 闭包函数认知
```javascript
function main() {
  var name = 'xiaoming';
  return function () {
    console.log(name);
  }
}

var output = main();
output();
```
`main()`函数执行会返回一个函数，并赋值给了`output`。这说明output的定义时再`main()`外部，但为啥我在`main()`外部执行`output()`却可以使用name并正常输出`name`的值呢？

**解答：**

在js中函数的变量作用域是通过作用域链定义的，它在函数定义的时候就已经创建了，而不是在调用函数时决定的。由于闭包的特性，当函数定义了嵌套的函数，并将它作为返回值返回或者存储在某处的属性里时，就会有一个外部引用指向这个嵌套的函数，同时将它的作用域链保存下来，而这条作用域链就包含了嵌套函数的局部变量以及定义他们的外部函数的局部变量。

本例中，执行main()并将嵌套函数返回给output时，output()生成的变量作用域链里，就包含了main()里的name及值。所以，可以正常输出name的值。

闭包的特点就是能把原始作用域的内容带出去（事实上是同作用于下的变量可以访问），这里要重点记住一个特点：如果在某个作用域下但凡还有一个变量（包括函数变量）还在使用，那么这个作用域下的所有其他变量都不会销毁。
![](https://ws4.sinaimg.cn/large/006tNc79gy1fka3vr2tv1j31kw12fjw1.jpg)

---

## 解释setTimeout的回调执行的原理
```javascript
function output() {
  var name = 'xiaoming';
  setTimeout(function () {
    console.log(name);
  }, 1000);
}

output();
```
能解释一下为啥setTimeout中的回到函数为啥能访问output的变量name吗？





















---

## 参考

[新生大学小社群](http://code.7xinsheng.com/)
[老师的github](https://github.com/xugy0926/getting-started-with-javascript/)
