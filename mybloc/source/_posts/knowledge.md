---
title: Javascript 知识点
date: 2017-10-05 09:50:51
tags: JS
---


## 什么是函数？

函数可以认为是一段JavaScript代码片段，也可以认为是一个代码黑盒，也可以认为是一台代码机器。
重要的特征：你告诉它干活，它就能给你相应结果。至于能干什么活，那就是函数设计者的事情。
函数就是一个可以执行固定任务的代码段，函数只需要定义一次，但能被执行任意次。

```javascript
// 定义一个函数print
function print() {
  console.log('hello, JS');
}

// 多次调用print函数
print();
print();
print();
```



## 定义一个函数的语法

定义函数最少最少需要三个元素：

-  关键字`function`
-  函数名`funcname()`
-  一对挂括号`{}`



**示例：**

```
function print() {
  console.log('hello, JS');
}
```



**错误示范：**

```javascript
print() {
  console.log('hello, JS');       //缺function 编译器完全不认识，在执行编译的时候直接就报错。
}


function () {
  console.log('hello, JS');		  //没有函数名，无法被调用。
}

function print() {
  console.log('hello, JS');		  //缺挂括号，编译器就认为print()就是函数print的函数体内容
print();
}
```



## 函数三要素

假如你要请一个人帮忙做某事，你必须要明确到底请谁（函数名）？告诉他你的要求（参数）是什么，他处理完事情后就会给你一个结果。



**当你要定义（设计）一个函数的时候，你就要站在设计函数的角度去思考。**

1. 我设计这个函数到底是为了完成什么功能？
2. 我设计这个函数需不需要调用者给我一些数据？
3. 我设计这个函数有没有必要返回一个结果数据？
4. 我设计这个函数应该用什么方式返回数据？



**当你要调用一个函数的时候，你就要站在使用者的角度去思考。**

1. 我调用的这个函数能否完成我想要的功能。
2. 我调用的这个函数都需要一些什么数据才能完成功能。
3. 我调用的这个函数会不会给一个结果数据。
4. 我调用的这个函数用的是什么方式返回数据。



**从设计函数的角度和从使用一个函数的角度，都反映出几个重要的要素。**

1. 函数名。一个函数名对应了一个函数执行体，这个执行体会完成一个具体的功能。
2. 参数。一个函数在执行的时候可能需要参数，也可能不需要。
3. 返回值。一个函数执行完后，可能返回一个结果，也可能不返回。





## 函数名(像使用变量一样使用函数名)
>  像使用变量一样使用函数名，函数名从某种意义上可以理解为变量名。
> **变量名**和**函数名**的使用方式的明显差异就是：函数名在调用时要带上一对括号`()`。

**一个变量要先定义后使用：**

```javascript
// 定义一个变量name，并赋值字符串'xiaoming'
var name = 'xiaoming';

// 因为字符串xiaoming被赋值给了变量name，我们才得已通过name来操作字符串xiaoming
var fullname = 'xu' + name;

// 把变量name的值传递给console的log函数进行打印
console.log(name);
```



**函数也应该要先定义再使用：**

```
// 先定义函数
function print() {
  console.log('hello, JS');
}
// 再使用（使用函数一般称为调用）
print();
```

先定义后使用之间的关联就是函数名起到联系。


**但，函数定义即使放在调用的下面也没问题：**

```
// 调用print函数
print();

// 定义函数print
function print() {
  console.log('hello, JS');
}
```

其实上面两种形式是等价的，原因就是代码在执行之前，编译器会把通过函数语法定义的函数提前定义。从而保证可以在任意处调用函数。



## 参数

>  在函数执行过程中，完成某些逻辑处理时需要的一些必要的数据。
>
>  参数就是函数设计者向调用者要求的数据来源方式。



**无设置参数时：**

```javascript
function print() {
  console.log('hello, JS');
}

//正确：
print();						// ==> hello, JS

//错误：
var content = 'hello, world';
print(content);					// ==> hello, JS(直接无视参数)
```



**有设置参数时：**

```javascript
function print(content) {
  console.log(content);
}

//正确：
print('hello, JS'); 			// ==> hello, JS

//错误：
print(); 						// ==> undefined(没有内置内容给参数变量content)
```

**逻辑问题（牛头不对马嘴）：**

```javascript
function print(name, content) {
  console.log('i am ' + name);
  console.log('i am learning ' + content);
}

//正确：
print('xiaoming', 'JS'); 		
// ==> i am xiaoming
// ==> i am learning JS

//错误：
print('JS', 'xiaoming');
// ==> i am JS
// ==> i am learning xiaoming
```

## 返回值
>  一个函数要不要明确返回结果取决设计者的自我判断。

**没有返回值：**

```javascript
function print(content) {
  console.log(content);
}

print('hello, JS');
```
`print`这个函数的功能就是打印调用者传进来的内容，打印就结束，没有必要返回某个值。


**尴尬示范（强硬加上的返回值）：**

```javascript
function print(content) {
  console.log(content);
  return true;					 // 给一个返回值，返回true表示打印完了。
}

var result = print('hello, JS');
```

**有返回值：**

```javascript
function sum(x, y) {
  var result = x + y;
  return result;
}

var result = sum(1, 2);
console.log(result);
```

-  sum这个函数被设计成做两个数的相加，加完的结果明确了返回（return result）。这个返回值就很必要，如果加完不给结果这个函数就没有多大意义。
-  一个函数在定义的时候明确了返回值，调用者就要明确用一个变量来接收返回值。`var result = sum(1, 2);`就很明确接收了返回值。当sum函数体内执行完后，return出来的result给到了调用者定义的result变量（注意：sum函数内部的result变量和sum函数外面的result变量不是一个作用域下的，它们是不同的两个变量）。
-  只有用result变量接收了sum的返回值，我才有机会打印结果

**注：** 不被使用的变量都是垃圾代码



## 两种定义函数方式的差异
-  函数语法定义方式
```javascript
function print(content) {
  console.log(content);
}
```

-  函数表达式定义方式
```javascript
var print = function (content) {
  console.log(content);
}
```

 **差异：**
-  调用函数时，函数语法定义法能提前，函数表达式定义法就能不提前
-  ​



## 函数语法定义方式
>  用函数语法定义一个函数，能获得定义提前的优待。

**先定义后使用：**
```javascript
function print(content) {
  console.log(content);
}

print('Hello, JS');
```

**函数定义即使放在调用的下面也没问题：**
```javascript
print('Hello, JS');

function print(content) {
  console.log(content);
}
```
其实上面两种形式是等价的，原因就是代码在执行之前，编译器会把通过函数语法定义的函数提前定义。从而保证可以在任意处调用函数。


## 表达式定义方式
>  表达式定义方式和普通定义变量是一个道理（一样理解）

**定义一个变量：**

```javascript
var name = 'xiaoming';
var name = 'xu' + name；
```

-  `xiaoming`是一个字符串表达式


-  `'xu' + name`是一个表达式，表示计算出结果`xuxiaoming`后，把结果赋值给了变量`fullname`。



**定义函数表达式：**

```javascript
var print = function (content) {
  console.log(content);
}

print('Hello，JS');
```

-  `function(content) { console.log(content )} `就是一个表达式。
-  把表达式赋值给变量`print`后，变量`print`是一个函数变量。有了这个函数变量print，我们就可以通过print变量执行该函数了。

**错误示范：**

```javascript
print('Hello，JS');				 // 喔喔。。没定义怎么能使用？

var print = function (content) {
  console.log(content);
}
```

上面的代码肯定出错。既然print是一个函数变量，一个变量没有定义之前肯定是不能使用的啦。
有人就问，函数语法定义法能提前，为啥函数表达式定义法就不提前呢？
那我提个问题，如果函数表达式定义法能提前，那定义变量是不是意味着都提前了呢。那就乱套了。


## 深入表达式定义法

** 直接使用表达式**

函数语法定义法有提前优待，那也不能说表达式定义法就没有价值。价值可大了。

```javascript
// 这是函数语法定义方式
function print() {
  console.log('Hello, JS');
}

setTimeout(print, 5000);
```

```javascript
// 这是函数表达式定义方式
var print = function () {
  console.log('Hello, JS');
}

setTimeout(print, 5000);
```

定义了一个函数，然后调用setTimeout，5秒钟后回调print。



**改进的写法：**

-  变量的做法

```javascript
var name = 'xiaoming';
console.log(name);
```

可以省一个变量

```javascript
console.log('xiaoming');
```

-  函数的做法

```javascript
var print = function() {
  console.log('Hello, JS');
}

setTimeout(print, 5000);
```

可以省一个变量

```javascript
setTimeout(function() {
  console.log('Hello, JS');
}, 5000);
```



**在函数中定义函数**

```javascript
function printWelcome(name) {
  var addWelcome = function() {
    return '你好！' + name;
  }

  console.log(addWelcome());
}

printWelcome('xiaoming');
```

## 了不起的axios(http)
[axios](https://github.com/mzabriskie/axios)是一个在全后端通吃的HTTP客户端，解决所有在js学习过程中http相关的请求。
前端要访问服务端数据，服务端访问另一个服务端数据，这两种访问都需要用到http客户端。
前后端通吃是axios的优势，但更牛的是，它能把处理写成链式结构。

```javascript
axios.get().then().then().catch();
```

以上的处理流程解释如下:
`axios.get()`获得的结果给到第一个`then()`，处理完后给到第二个`then()`。如果中间过程发生错误，会直接跳到`catch()`里。

事实上`axios.get()`是一个异步函数，`axios.get()`的异步回来后才会调用后面的`then()`函数。以这样的推理，整个`axios.get().then().then().catch()`就是一个异步函数链条。

### Get请求

```javascript
axios.get('/api')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

### Post请求

```javascript
axios.post('/api', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

---

## 代码就是由这些组成的

在写JS代码时，似乎都是在操作下面4类语法。

-  一个数据集合(对象、json)。
-  两种函数（同步、异步）
-  三大结构（顺序语句、条件语句、循环语句）
-  多种数据格式（数字，字符串，数组，布尔，json，对象）的使用方式

下面详细剖析一个案例来说明代码的组成。

比如想通过 <https://js.xinshengdaxue.com/api> 提供的接口来获取心里话数据。

心里话接口信息请参考接口文档 <http://js.xinshengdaxue.com/api/>

```javascript
[GET] /api/v1/learnJS/course/:id/words
id: 第一期课程为1

结果：
{
  code, // 1: 处理正常，0：处理错误
  message, // code === 0 时返回
  words
}

```

以下代码使用了axios第三方库来发起http请求获取数据[点这里了解axios](https://github.com/xugy0926/getting-started-with-javascript/blob/master/topics/%E4%BA%86%E4%B8%8D%E8%B5%B7%E7%9A%84axios(http).md)

### 第一步：通过axios提供的异步函数get获取数据

```javascript
axios.get('https://js.xinshengdaxue.com/api/v1/learnJS/course/1/words')
  .then(function (response) {
    // response对象就是我们获取到的结果对象
  })
  .catch(function (error) {
    console.log(error);
  });
```

### 第二步：依据获取到的结果对象，并操纵对象来分析从服务端返回来的结果

```javascript
axios.get('https://js.xinshengdaxue.com/api/v1/learnJS/course/1/words')
  .then(function (response) {
    // 读取对象中的code属性值，如果值等于1，说明服务器的逻辑处理是正常
    if (response.data.code === 1) {
      alert('success');
    } else {
      alert('failed');
    }
  })
  .catch(function (error) {
    console.log(error);
  });
```

### 第三步：在code等于1的逻辑中把心里话数据拿出来并赋值给一个变量wordsList

```javascript
axios.get('https://js.xinshengdaxue.com/api/v1/learnJS/course/1/words')
  .then(function (response) {
    if (response.data.code === 1) {
      // 将response中的心里话数据拿出来并赋值给一个变量。
      // 这时我们拿着wordsList这个变量可以做你想要的任意操作。
      var wordsList = response.data.words;
    } else {
      alert('failed');
    }
  })
  .catch(function (error) {
    console.log(error);
  });
```

### 第四步：想要过滤掉名字为空的数据

```javascript
axios.get('https://js.xinshengdaxue.com/api/v1/learnJS/course/1/words')
  .then(function (response) {
    if (response..data.code === 1) {
      // 将response中的心里话数据拿出来并赋值给一个变量。
      // 这时我们拿着wordsList这个变量可以做你想要的任意操作。
      var wordsList = response.data.words;

      // 过滤名字内容为空的数据
      var filterWordsList = [];
      for (var i = 0; i < wordsList.length; i++) {
        // 当name，avatar，words三个属性都有内容时，加入到数组filterWordsList
        if (wordsList[i].name && !wordsList[i].avatar && wordsList[i].words) {
          filterWordsList.push(wordsList[i]);
        }
      }

    } else {
      alert('failed');
    }
  })
  .catch(function (error) {
    console.log(error);
  });
```

### 第五步：将最终的结果反映到vue的data变量中

```javascript
axios.get('https://js.xinshengdaxue.com/api/v1/learnJS/course/1/words')
  .then(function (response) {
    if (response.data.code === 1) {
      // 将response中的心里话数据拿出来并赋值给一个变量。
      // 这时我们拿着wordsList这个变量可以做你想要的任意操作。
      var wordsList = response.data.words;

      var filterWordsList = [];
      // 过滤内容为空的数据
      for (var i = 0; i < wordsList.length; i++) {
        // 当name，avatar，words三个属性都有内容时，加入到数组filterWordsList
        if (wordsList[i].name && !wordsList[i].avatar && wordsList[i].words) {
          filterWordsList.push(wordsList[i]);
        }
      }

      // 将filterWordsList赋值给Vue的data里的wordsList变量。
      // 倘若data里的wordsList变量和html中的节点绑定了，页面就会自动更新数据
      app.wordsList = filterWordsList;
    } else {
      alert('failed');
    }
  })
  .catch(function (error) {
    console.log(error);
  });
```

以上五步循序渐进的处理涉及到了语法重点的所有知识。

-  调用了异步函数`axios.get()`。
-  使用数据集合(response，wordsList, filterWordsList)。
-  运用了三大结构中的顺序语句、条件语句、循环语句。
-  操作了数据格式。
   -  运用点号来访问对象属性。response.code等。
   -  读取数组长度。wordsList.length。
   -  游标方式访问数据内容。wordsList[i]）。


   ## 立即执行函数

   ### 如何定义完函数就立即执行？

   一个函数定义完就执行，这种技巧在编程中经常用到。

   正常情况下，我们都是这样做的：

   ```javascript
   // 定义函数print
   function print(content) {
     console.log(content);
   }

   // 调用函数print
   print('Hello, JS');
   ```

   把函数明确定义出来的好处当然很多，功能清晰，可以重复调用。

   但有人就喜欢这样做：

   ```javascript
   (function(content){
     console.log(content);
   })('Hello, JS');
   ```

   上面这种写法让人非常难以理解。而且，这个函数定义出来就被执行了，并不能重复调用。

   这就好比你造了一台机器，这台机器只运行了一次就死了，从函数重复利用的角度来看，没有价值。

   先不管这个，我们先从技术的角度来拆解分析这件事情。

   ```javascript
   function (content) {
     console.log(content);
   }
   ```

   上面这个是函数表达式，单独存在的时候没有价值。

   前面说了，正常情况下直接用函数语法方式给定一个函数名：

   ```javascript
   function print(content) {
     console.log(content);
   }
   ```

   或者，是把函数表达式赋值给一个变量。

   ```javascript
   var print = function(content) {
     console.log(content)
   }

   ```

   只有这样，才能正常利用pint来调用函数。

   但是，一个函数表达式两侧直接加上括号，就能获得这个表达式的值：

   ```javascript
   (function (content) {
     console.log(content);
   })
   ```

   然后对这个值进行直接调用，调用函数时后面跟一对括号：

   ```javascript
   (function (content) {
     console.log(content);
   })('Hello, JS')
   ```

   这就完成了一次直接定义并且直接调用的动作，省去了一次函数命名的过程。看上去是不是没啥价值？但是真的没价值吗？



   ### 定义完就执行的价值

   在前端的技术中，无法像在nodejs一样通过require引用模块，所以第三方的模块都放在 `<head>` 里。

   比如：

   ```javascript
   <head lang="en">
       <script src="https://unpkg.com/vue"></script>
       <script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
   </head>
   ```

   上面引入了两个模块，vue和jquery。

   引入进来后，我们可以在js代码中直接调用他们来进行业务操作。比如：

   ```javascript
   <script>
     // 使用了Vue对象来初始化
     var app = new Vue({
       el: '#app',
       data: {
         title: 'learn JS'
       }
     });

     // 使用了$对象
     $.get(....);
   </script>
   ```

   事实上，有一件很奇怪的事情就是，为什么我引入了vue和jquery，就可以在js中直接使用Vue和$这两个对象呢？我并没有像nodejs的require一样明确的把模块指定给某个变量。

   ```javascript
   // nodejs引入模块，我们可以明确用一个变量来接收
   var fs = require('fs');
   ```

   这是因为，在前端引入第三方模块的过程中，一旦第三方的js文件被下载下来后，浏览器会立即去执行下载过来的js文件，并把执行过程中产生的对象加入到一个全局的对象中，以方便开发者调用。

   当vue.js文件下载过来之后，浏览器会立即执行vue.js，产生了Vue这个对象，并把Vue这个对象加入到了全局的对象中。从而，开发者就可以在自己的js代码中调用Vue这个对象。

   vue.js的代码为了保证自己能被立即执行，用的就是这种定义立即执行的技巧。

   ```javascript
   (function (global) {
     ....
     ....
     global.Vue = Vue
   })(this)
   ```

   如果你想定义一个js文件放在public中，也可以采用这个技巧。方式可以参考words-from-the-heart的测试代码。

   words-from-the-heart/index.html
   words-from-the-heart/public/js/index.js

---

   ## 匿名函数使用技巧

   以下例子是一个模拟异步处理的手法

   ```javascript
   // 定义一个函数，函数名为callback
   function callback () {
     console.log('我终于被调用了');
   }

   // 5秒钟后调用callback函数
   setTimeout(callback, 5000);
   ```

   1. 定义了一个函数callback。
   2. 然后调用setTimeout函数，5秒钟后调用callback函数。

   其实，我们可以采用匿名函数来简化流程。

   ```javascript
   setTimeout(function () {
     console.log('我终于被调用了');
     }, 5000);
   ```

   通过匿名函数的方式带来直接的好处就是，不用去考虑怎么定义函数的命名。提高了写代码的效率。


---

## 变量命名简明技巧

-  1. 完整代表了变量的含义吗？ -> 推到出更多信息
-  1. 以问题为导向了吗？ -> 反映了问题而非解决方案

```javascript
var start = 0; // bad。 开始什么？不明白
var startCount = 1; // good。  可以推到出是number类型
```

```javascript
var end = 100; // bad。 end什么？不明白
var endCount = 100; // good。可以推导出是结束数字，number类型。
```

```javascript
var file = './name_style.js'; // bad。 文件内容？不清楚
var jsFilePath = './name_style.js'; // good。可以推导出是js文件的路径，路径一定是字符串。
```

```javascript
var id = '1234567'; // bad 什么id？不明白
var nameId = '1234567'; // good。可以推到是名字的id。
```

// 表述一个人的基本信息

```javascript
var person = {   // bad。person可以表示一个人，但没办法知道是个人信息
  name: 'xiaoming',
  age: 18,
  sex: 'man'
};

var personInfoObj = {  // good。可以推到出这是个人信息，而且还是一个object类型。
  name: 'xiaoming',
  age: 18,
  sex: 'man'
}
​```

// 表示一个输入的雇员信息
​```javascript
var inputData = { // bad。只能表示是输入的数据。输入的什么数据？不清楚。只知道how，不知道what。
  name: 'xiaoming',
  age: 18,
  sex: 'man'
}

var employeeData = { // good。 这是个雇员的数据(很明确知道what是什么)，很清晰。
  name: 'xiaoming',
  age: 18,
  sex: 'man'
}
```

---

## 同步函数的两种返回结果的方式

同步函数既可以立即返回结果，也能通过间接返回(callback)结果。

### 立即返回结果
比如定义一个求和函数sum并调用一次求和动作。

```javascript
// 定义求和函数sum
function sum(a, b) {
  var c = a + b;
  return c;
}

// 调用sum函数，并传递两个值给sum的参数，当sum函数执行完并将结果赋值给变量value
var value = sum(1, 2);
// 打印value的值
console.log(value);
```

为了更好的看清楚整个流程，可以在代码中加入打印代码执行序列号。

```javascript
console.log('flow: 1');
// 定义求和函数sum
function sum(a, b) {
  console.log('flow: 2');
  var c = a + b;
  console.log('flow: 3');
  return c;
  console.log('flow: 4');
}

console.log('flow: 5');
// 调用sum函数，并传递两个值给sum的参数，当sum函数执行完并将结果赋值给变量value
var result = sum(1, 2);
console.log('flow: 6');
// 打印result的值
console.log(result);
console.log('flow: 7');
```

代码执行的序列是
```javascript
flow: 1
flow: 5
flow: 2
flow: 3
flow: 6
3
flow: 7
```
在函数sum内，`flow: 4`并不能被执行，因为前面一行`return c`会导致整个函数结束执行。


### callback返回结果
比如定义一个求和函数sum并调用一次求和动作。

```javascript
// 定义求和函数sum
function sum(a, b, callback) {
  var c = a + b;
  callback(c);
}

// 定义一个callback函数，用于接收sum函数返回的值
function resultCallback(value) {
  console.log(value);
}

// 调用sum函数，并传递两个值给sum的参数，同时把resultCallback传过去
var result = sum(1, 2, resultCallback);
// 打印value的值
console.log(result);
```

打印代码执行序列号

```javascript
console.log('flow: 1');
// 定义求和函数sum
function sum(a, b, callback) {
  console.log('flow: 2');
  var c = a + b;
  callback(c);
  console.log('flow: 3');
}

console.log('flow: 4');
// 定义一个callback函数，用于接收sum函数返回的值
function resultCallback(value) {
  console.log('flow: 5');
  console.log(value);
  console.log('flow: 6');
}

console.log('flow: 7');
// 调用sum函数，并传递两个值给sum的参数，同时把resultCallback传过去
var result = sum(1, 2, resultCallback);
console.log('flow: 8');
// 打印result的值
console.log(result);
console.log('flow: 9');
```

代码执行的序列是

```javascript
flow: 1
flow: 4
flow: 7
flow: 2
flow: 5
3
flow: 6
flow: 3
flow: 8
undefined
flow: 9
```
在函数sum内，没有明确return结果，而是通过callback函数返回的结果。所以console.log(result)的result是一个没有定义的值undefined。

虽然同步函数可以通过立即返回和间接返回得到函数的处理结果，但是间接返回在同步函数中的处理过于画蛇添足，还增加了代码的复杂度。同步函数处理的间接返回结果并不是一件好事。

---

## callback函数的设计学
JavaScript语言发展太快了，api文档跟不上语言的发展速度。
callback函数的设计理念，三个关键词：
-  异步处理
-  错误处理
-  开源社区

JavaScript的语言特性就是异步处理，一层套一层的异步调用，如果某个异步处理出了问题，该怎么告知调用者？
错误优先处理：所有的工程师定义的所有异步函数的回调的第一个参数默认为错误参数。
就这么一个简单的口号，解决了所有异步调用的错误处理问题。
有了一个原则：错误优先处理。我们写任何代码就很随性了。

```javascript
// 读取某个文件夹路径里的所有内容
fs.readdir('path', function(err) {
   if (err) {
       return;
   }
});

// 读取某个文件内容
fs.readFile('file_path', function(error) {
   if (error) {
       return;
   }
});

// 写入'hello, js'到某个文件中
fs.writeFile('file_path', 'Hello, JS', function(e) {
   if (e) {
       return;
   }
});
```

以上你不管是调用哪个异步函数，callback的第一个参数都是用来接收错误信息的。参数的名字？就显然不重要了，你随意的取。不过建议命名为err，这是所有优秀工程师的统一命名。

当错误问题解决了，那怎么知道该函数会不会返回结果内容呢？这当然是要查api文档啦。某一个异步函数是否返回结果内容，api文档都会清楚告知。但是！如果不差查api文档能不能知道是否返回结果呢？能！需要像福尔摩斯一样去推理。

-  `fs.readdir` —— 读取目录下的所有文件名，这么明确的异步处理函数，你说会不会返回内容呢？答案肯定是会的，而且一定是个数组。注意readdir的作用，是返回所有文件名。
-  `fs.readFile` —— 读取某个文件的内容，这么明确的异步处理函数，你说会不会返回内容呢？答案肯定是会的，而且一定是string。注意readFile的作用，是返回文件内容。
-  `fs.writeFile` —— 将内容写入到某个文件，这么明确的异步处理函数，你说会不会返回内容呢？答案肯定是不会的。

通过函数的作用，来推理callback函数的返回内容就是这么简简单单。
那如果推理得知会返回内容，内容应该怎么获得呢？
前面的错误优先返回中，错误变量err会占据callback函数的第一个位置，那结果就是第二个位置。

```javascript
// 读取某个文件夹路径里的所有内容
fs.readdir('path', function(err, files) {
   if (err) {
       return;
   }

  console.log(files);
});

// 读取某个文件内容
fs.readFile('file_path', function(err, file) {
   if (error) {
       return;
   }

  console.log(file);
});
```

谨记callback函数的设计理念：

1. 错误处理优先。
2. 依据函数作用推测是否有结果，如果有结果，结果参数在第二位。

不管是错误处理还是推理是否有结果返回，这样的设计理念体现出工程师与工程师之间的信任，javascript语言好像是更有人情味的编程语言。
如果你哪一天在使用一个第三方库发现回调函数没有遵从这个原则，我建议你赶紧把这个第三方库扔到大海里去，让它从你的生活中消失。这个作者不值得你信任。

---

## JavaScript的语法学习指引
JavaScript的基本语法特性的组合在一起成为：JavaScript标准库。其包含了语法和不同数据类型的使用方式。

### 途径一：[w3school](http://www.w3school.com.cn/js/index.asp)

在w3school里看语法要注意几个点。

1. 里面的JavaScript知识都是在浏览器环境下讲的。
2. 里面的JS HTML DOM是前端html的知识，教你如何运用js代码来处理html、css、事件。这个知识涉及到了浏览器运行环境里的某些内置库。
3. 里面的JS Window是浏览器知识，教你如何运用js代码来处理浏览器的一些属性。这个知识涉及到了浏览器运行环境里的某些内置库。
4. JS 库，这里讲解了浏览器运行环境下用的一些库。

所以，在w3school学JavaScript语法需要结合一些前端知识，要注重分辨哪些是JavaScript的语法知识，哪些又是浏览器内置库的知识，别搞混了。

### 途径二：JavaScript权威指南（犀牛书）

学习语法知识时，可以用浏览器环境或者nodejs运行环境去试验书中的代码。

#### 第一部分：

1. 第1章 - 第7章是JS的基础。（强烈要求掌握）
2. 第8章 - JS的重点重点重点。（强烈要求掌握）
3. 第9章- 在进阶过程时去掌握。（初学者学有余力时去了解）
4. 第10、第11可以暂时忽略。
5. 2.5可选分号 — 强烈忽略本小节。

#### 第二部分：

和前端开发有关的内容。

#### 第三部分和第四部分：

内置服务的api。当字典来查。



#### 途径三：mozilla JavaScript

-  [JavaScript](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript)
-  [HTML](https://developer.mozilla.org/zh-CN/docs/Web/HTML)
-  [CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS)

---

## 学习语法时的自问技巧
-  一个数据集合(对象、json)。
-  两种函数（同步、异步）
-  三大结构（顺序语句、条件语句、循环语句）
-  多种数据格式（数字，字符串，数组，布尔，json，对象）的使用方式
以上4大块语法是构建js代码流程的基础。

在平时的编码中，要实现想法就离不开这些基础知识。不信？请[点这里](https://github.com/xugy0926/getting-started-with-javascript/blob/master/topics/%E4%BB%A3%E7%A0%81%E5%B0%B1%E6%98%AF%E7%94%B1%E8%BF%99%E4%BA%9B%E7%BB%84%E6%88%90%E7%9A%84.md)

学习JS是要始终思考下面问题。

-  一个数据集合(对象)。
   -  如何定义一个对象？
   -  如何访问对象的属性？

-  两种函数（同步、异步）
   -  如何定义函数？（函数语法定义方式和表达式定义方式的区别）
   -  如何调用同步函数？同步函数怎么返回结果。
   -  如何调用异步函数？异步函数怎么返回结果。

-  三大结构（顺序语句、条件语句、循环语句）
   -  顺序语句的执行流程。
   -  条件语句的执行流程。什么内容才能成为条件，是语句？还是表达式？
   -  循环语句的执行流程。循环语句的三大特性：什么是初始化语句？什么是循环判断条件？什么是累加器？为什么需要三大特性才能保证循环正确执行。

-  多种数据格式（数字，字符串，数组，布尔，json，对象）的使用方式。
   -  字符串怎么相加来拼接字符串？
   -  数字和字符串可以相加吗？哪数组和字符串能相加吗？和对象呢？和其他格式呢？
   -  数组怎么用游标访问元素？数据可以删掉元素吗？可以增加吗？可以排序吗？
   -  什么样的表达式才能得到布尔值？将数字1和字符串1进行比较会得到true还是false？
   -  怎么访问对象的属性？可以给某个对象动态的添加属性吗？
 ​
学习JS语法基础知识时要把被动变为主动。如果你始终跟着书本走，你的思路就被牵制了。比如在学习数组格式时，你首先要想一个数组格式存在什么价值？会带来记录数据的便利性吗？便利性体现在哪？该怎么利用这些便利性？只有这样你才能真正掌握。



## 学习函数抓住这几个点
### [两种定义函数的方式](https://github.com/xugy0926/getting-started-with-javascript/blob/master/topics/%E4%B8%A4%E7%A7%8D%E5%AE%9A%E4%B9%89%E5%87%BD%E6%95%B0%E6%96%B9%E5%BC%8F%E7%9A%84%E5%B7%AE%E5%BC%82.md)
-  函数语法方式定义。
-  函数表达式定义。

### 两种使用函数的方式
-  同步函数。
-  异步函数。

### [两种函数返回结果的方式](https://github.com/xugy0926/getting-started-with-javascript/blob/master/topics/%E5%90%8C%E6%AD%A5%E5%87%BD%E6%95%B0%E7%9A%84%E4%B8%A4%E7%A7%8D%E8%BF%94%E5%9B%9E%E7%BB%93%E6%9E%9C%E7%9A%84%E6%96%B9%E5%BC%8F.md)
-  立即返回结果。
-  callback返回结果。

### 两个返回结果的注意点
-  同步函数可以采用callback返回结果，但不要这么做。
-  异步函数只能采用callback返回最终结果。但调用异步函数本身也有一个立即返回值。两个返回结果要区分。



















## Reference

[小白学编程](http://code.7xinsheng.com/)
