---
title: JavaScript编程技巧与实战
date: 2017-10-20 10:28:33
tags: JS
---

# JavaScript 编程技巧与实战概要

-  正则表达式RegExp对象
-  作用域与闭包
-  this的使用
-  值传递和引用传递
-  H5的标准属性
-  H5的事件属性
-  Web Worker
-  jQuery
-  Ajax/Http知识
-  Commen JS规范
-  Seajs
-  RequireJs

![](https://ws3.sinaimg.cn/large/006tKfTcgy1fknlgwv01kj31kw0w0jye.jpg)
![](https://ws1.sinaimg.cn/large/006tKfTcgy1fknlgw04h8j31kw0w00zl.jpg)
![](https://ws1.sinaimg.cn/large/006tKfTcgy1fknlgvb00xj31kw0w0gsy.jpg)
![](https://ws3.sinaimg.cn/large/006tKfTcgy1fknlguiiocj31kw0w0qjw.jpg)
![](https://ws4.sinaimg.cn/large/006tKfTcgy1fknlgsqhmrj31kw0w0aic.jpg)

# JavaScript高级编程技巧

## 正则表达式RegExp对象

### 创建RegExp对象：

-  `var test = new RegExp("jikexueyuan")`
-  `var test = /jikexueyuan/`

```javascript
var str = "abc123"
var regExp=/[a-z]+/
console.log(regExp.exec(str))
["abc", index: 0, input: "abc123"]
```



### RegExp对象方法:

-  exec —— 检索字符串中指定的值。返回找到的值，并确定其位置
-  compile —— 编译正则表达式，把正则表达式编译为内部格式
-  test —— 检索字符串是否存在模式，返回true或false



#### exec

```javascript
   var str = "abc123"   
   var regExp=/[0-9]+/
   console.log(regExp.exec(str))
   ["123", index: 3, input: "abc123"]
```



#### compile

```javascript
   var str = "abc123"      
   var regExp=/[a-z]+/
   regExp.compile("[0-9]+")
   regExp
   /[0-9]+/
   console.log(regExp.exec(str))
   ["123", index: 3, input: "abc123"]
```



#### test

```javascript
   var str = "abc123"
   var regExp=/[a-z]+/   
   regExp.test(str)
   true

   var str = "你好极客学院"
   regExp.test(str)
   false
```



### RegExp修饰符

-  `i` —— 设置匹配对大小写不敏感
-  `g` —— 设置匹配为全局，类似于查找所有，持续到结束
-  `m` —— 设置匹配为多行



#### i

```javascript
var str = "ABCabc"
var regExp=/[a-z]/
regExp.exec(str)
["a", index: 3, input: "ABCabc"]

regExp=/[a-z]/i
regExp.exec(str)
["A", index: 0, input: "ABCabc"]

regExp=new RegExp("[a-z]","i")
/[a-z]/i
```



#### g

```javascript
var str = "ABCabc"
var regExp=/[a-z]/g
str.replace(regExp,"HI")
"ABCHIHIHI"

var regExp=/[a-z]/
str.replace(regExp,"HI")
"ABCHIbc"
```



#### 特殊符号^和$

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fknmzq9lf3j30sj0dvtb6.jpg)



```javascript
var str = "hello jikexueyuan"
var regExp=/^jike/
regExp.test(str)
false

str="jikexueyuan hello"
regExp.test(str)
var regExp=/xueyuan$/
regExp.test(str)
false

var str = "hello jikexueyuan"
regExp.test(str)
true

var regExp=/^hello xueyuan$/
regExp.test(str)
false

var regExp=/^hello jikexueyuan$/
regExp.test(str)
true
```

#### m

```javascript
var str="jike123\njike456"
regExp=/^jike/
str.replace(regExp,"")
"123
jike456"

regExp=/^jike/mg
str.replace(regExp,"")
"123
456"

regExp=/^jike/g
/^jike/g
str.replace(regExp,"")
"123
jike456"
```

#### 方括号`[]`

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fknnj7uvacj30ou0fewgo.jpg)

```javascript
var str="abcdabcdabcd"
regExp=/[^a-c]/
/[^a-c]/
str.replace(regExp,"")
"abcabcdabcd"

regExp=/[^a-c]/g
/[^a-c]/g
str.replace(regExp,"")
"abcabcabc"

var str="abcd123abcd123abcd123"
regExp=/[a-c0-3]/g
/[a-c0-3]/g
str.replace(regExp,"")
"ddd"

regExp=/[a-c0-3]/
/[a-c0-3]/
str.replace(regExp,"")
"bcd123abcd123abcd123"
regExp=/[^a-c0-3]/
/[^a-c0-3]/
str.replace(regExp,"")
"abc123abcd123abcd123"
```

```html
    <input type="text"
    onkeyup="regExp=/[^a-z]/g;this.value=this.value.replace(regExp,'')">

    <input type="text"
    onkeyup="regExp=/[^0-9]/g;this.value=this.value.replace(regExp,'')">

    <input type="text"
    onkeyup="regExp=/[^a-zA-Z0-9]/g;this.value=this.value.replace(regExp,'')">
```

#### 预定义类

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fknoirvyfdj30ul0d6grn.jpg)

```javascript
var d = "abc123ABZ_."

var regExp=/\w/g
d.replace(regExp,"")
"."

regExp=/\W/g
d.replace(regExp,"")
"abc123ABZ_"

regExp=/\d/g
d.replace(regExp,"")
"abcABZ_."

regExp=/\D/g
d.replace(regExp,"")
"123"

```

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fknoq4klfgj30rk0h27bc.jpg)

```javascript
var s="abc456 bc"
regExp=/b\b/g
s.replace(regExp,"")
"abc456 bc"

regExp=/bc\b/g
s.replace(regExp,"")
"abc456 "

regExp=/bbc\b/g
s.replace(regExp,"")
"abc456 bc"

regExp=/\bbc\b/g
s.replace(regExp,"")
"abc456 "

regExp=/\bbc/g
s.replace(regExp,"")
"abc456 "

regExp=/\babc/g
s.replace(regExp,"")
"456 bc"
```

[unicode编码转换器](http://tool.chinaz.com/Tools/Unicode.aspx)

```javascript
var s="极客学院"
regExp=/\u6781\u5ba2/g
s.replace(regExp,"")
"学院"

var s="abc123._;'p,.123你好 sad\n123\rcsa"
s
"abc123._;'p,.123你好 sad
123
csa"

regExp=/./g
s.replace(regExp,"")
"

"
```

#### 量词

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fknp3twngtj30t809wtc0.jpg)

```javascript bash
var s="abc123._;'p,.123你好 sad\n123\rcsa"
regExp=/.+/
s.replace(regExp,"")
"
123
csa"

regExp=/.+/m
s.replace(regExp,"")
"
123
csa"

regExp=/.?/
s.replace(regExp,"")
"bc123._;'p,.123你好 sad
123
csa"

regExp=/.{4,10}/
s.replace(regExp,"")
"p,.123你好 sad
123
csa"

regExp=/.{4}/
s.replace(regExp,"")
"23._;'p,.123你好 sad
123
csa"

regExp=/.{4,}/
s.replace(regExp,"")
"
```

#### 其他

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fknpcbgygqj30xx0d1dmr.jpg)

```javascript
var s="abc123"
regExp=/bc(?=1)/g
s.replace(regExp,"")
"a123"

regExp=/bc(?!1)/g
s.replace(regExp,"")
"abc123"

regExp=/bc(?!2)/g
s.replace(regExp,"")
"a123"

var s="jike xueyuan nihao"
regExp=/jike|nihao/g
s.replace(regExp,"")
" xueyuan "

var s="abcac"
regExp=/ab(.*)c/
s.replace(regExp,"")
""

regExp=/ab(.*?)c/
s.replace(regExp,"")
"ac"
```

```javascript
//ignoreCase
var s="abcac"
regExp=/ab(.*?)c/
regExp.ignoreCase
false

regExp
/ab(.*?)c/

regExp=/xx/i
regExp.ignoreCase
true

regExp=/xx/ig
regExp.global
true

regExp.multiline
false

//lastIndex
var s = "hello world,hello jike";
var regExp = /hello/g
var result;

while ((result = regExp.exec(s)) != null){
   console.log(result);
   console.log("");
   console.log(regExp.lastIndex);
}

["hello", index: 0, input: "hello world,hello jike"]
5
["hello", index: 12, input: "hello world,hello jike"]
17


//search
s="hello jike"
regExp=/jike/
s.search(regExp)
6

regExp=/xjike/
s.search(regExp)
-1

//split
s="abc 123"
s.split("")
["a", "b", "c", " ", "1", "2", "3"]

s.split("",4)
["a", "b", "c", " "]

s.split("b")
["a", "c 123"]


s="abc 1b23"
s.split("b")
["a", "c 1", "23"]
regExp=/[a-z]/
s.split(regExp)
["", "", "", " 1", "23"]


s="abc 123"
regExp=/[a-z]/
s.match(regExp)
["a", index: 0, input: "abc 123"]

regExp=/[a-z]/g
s.match(regExp)
["a", "b", "c"]

s = "abc213ab"
regExp=/(bc)(.*)(ab)/g
s.replace(regExp,"")
"a"
s.replace(regExp,"__$1__$2__$3")
"a__bc__213__ab"
```

#### 实例
验证手机号码：

```javascript
var s=13300001111

regExp=/^133[0-9]{8}$/
regExp.test(s)
true
```

```javascript
 var patt = new RegExp(pattern,modifiers);
   var patt = /pattern/modifiers;

   //eg
   var patt = new RegExp("\\w+","i");
   var patt = /\w+i/

   var reg = new RegExp("hello","gi");
   var str = "Hi, hello wakakawakaka, hello world!"
   document.write(reg.test(str))                    // ==> true

   var reg = /hello/
   var str = "Hi, hello wakakawakaka, hello world!"
   document.write(reg.test(str))                    // ==> true


   var reg = /Hello/i;								// 不区分大小写
   var str = "Hi, hello wakakawakaka, hello world!"
   document.write(reg.test(str))                    // ==> true

   var reg = /Hello/gi;							// 不区分大小写,全局查找
   var str = "Hi, hello wakakawakaka, hello world!"
   document.write(reg.test(str))                    // ==> true

   var reg = /Hello/gi;							// 不区分大小写,全局查找
   var str = "Hi, hello wakakawakaka, hello world!"
   document.write(reg.exec(str))                    // ==> hello
```

```javascript
   var username = "2123";
   var regex = /^[A-Za-z0-9_]{4,20}$/
   // or
   var regex = /^\w{4,20}$/
   var regex = /^\d{4,20}$/

   if(regex.test(username)){
   	alert("您的用户名可用");
   }else{
   	alert("您的用户名不不不可用");
   }

   //xxx@qq.com  xxxx@163.com

   var email = "jacke@126.com"
   var regex2 = /^\w+@\w+\.\w+$/

   if(regex2.test(email)){
   	alert("您的邮箱可用");
   }else{
   	alert("您的邮箱不不不可用");
   }
```

## 作用域（scope）
-  作用域就是变量和函数的可访问范围
-  影响变量和函数的可见性与生命周期
-  JavaScript包括全局作用域和局部作用域
-  JavaScript没有块级作用域
-  JavaScript会预编译变量和函数


### 作用域的描述
#### 全局作用域：

```javascript
    var a="123";
    function test(){
      console.log("test内调用外部变量a:"+a);  //可以作用到任何地方
    }
    test();
// ==>  test内调用外部变量a:123
```

```
var s = "123";
window.s
// ==> "123"
```

#### 局部作用域：

```javascript
    function test(){
      function inner(){
        console.log("inner");
      }
      inner();
    }
    test();
    inner();

// ==> inner
// ==> Uncaught ReferenceError: inner is not defined
```

#### 函数内变量作用域：

```javascript
    function test(){
      var b ="123";
        console.log("test内部变量b："+b);
    }
    test();
    console.log("test内部变量b："+b);
// ==>  test外部变量b：123
// ==>  Uncaught ReferenceError: b is not defined
```

#### 函数内变量作用域（特殊情况）：

```javascript
    function test(){
      b ="123";
        console.log("test内部变量b："+b);
    }
    test();
    console.log("test外部变量b："+b);
    window.b;

// ==>  test内部变量b：123
// ==>  test外部变量b：123
// ==> "123"
```

#### 块语句（块等级代码）

```javascript
if(){};

for(){};

switch(){}
```

```javascript
for(var b=1; b<5;b++){
}
console.log(b);
// ==> 5
```

#### 预编译变量与函数

```javascript
var c = "123";
function test(){
  console.log(c);
  var c = "456";
  console.log(c);
}
test();
// ==> undefined
// ==> 456
```

```javascript
var c = "123";
function test(){
  console.log(d);
  console.log(c);
  var c = "456";
  console.log(c);
}
test();
// ==> ReferenceError: d is not defined
```

### 执行上下文（execution context）
-  全局执行上下文为window
-  每个函数都有自己的执行上下文
-  全局的执行上下文在当前窗口关闭后被销毁
-  执行上下文有一个与之相对应的变量对象

![](https://ws3.sinaimg.cn/large/006tKfTcgy1fkntqa64a6j30ui0kkq7o.jpg)

#### 执行上下文建立阶段

   -  建立变量，函数，arguments对象，参数variable object
   -  建立作用域链
   -  确定this的值

#### 执行上下文代码执行阶段

   -  变量赋值
   -  函数引用
   -  执行其他代码

Variable Object变量对象 ==> Active Object活动对象

   ```javascript bash
   function foo(i){
     var a = 'hello';
     var b = function privateB(){

     };
     function c(){

     }
   }
   foo(22);

   //建立阶段
   fooExecutionContext = {
     variableObject:{
       arguments:{
         0:22,
         length:1
       },
       i:22,
       c:pointer to function c()
       a:undefined,
       b:undefined
     },
       scopeChain:{...},
       this:{...}
   };

   //代码执行阶段
   fooExecutionContext = {
     variableObject:{
       arguments:{
         0:22,
         length:1
       },
       i:22,
       c:pointer to function c()
       a:'hello',
       b:pointer to function privateB()
     }，
       scopeChain:{...},
       this:{...}

   };
   ```
---

## 闭包
指有权限访问另一个函数作用域的变量的函数
创建闭包的常见方式就是在一个函数内部创建另一个函数


### 闭包的转换
   ```javascript
   var elements=document.getElementsByTagName("span");

   for(var i=0;i<elements.length;i++){
     elements[i].onclick=function(){
       console.log(this);
       console.log(i);
     }
   }
   // ==>
   ƒ (){
       console.log(this);
       console.log(i);
     }

   // 按下1，2，3
   // ==> 3
   // ==> 3
   // ==> 3
   ```

   ```javascript
   var elements=document.getElementsByTagName("span");

   for(var i=0;i<elements.length;i++){
     (function (m){
       elements[i].onclick=function(){
         console.log(m);
       }
   })(i);
   }

   // ==> undefined
   // 按下1，2，3
   // ==> 0
   // ==> 1
   // ==> 2
   ```

   #### 创建闭包的实例

   ```javascript
   function Outter(){
     var InnerVar=0;

     var s=function Inner(){
       InnerVar++;
       console.log("InnerVar:"+InnerVar);
     }
     return s;
   }
   var test = Outter();
   test();
   // 输出会叠加，不会被销毁
   // ==> InnerVar:1
   // ==> InnerVar:2
   // ==> InnerVar:3
   ```

   ```javascript
   function searchTxT(){
     var alreadyState = new Array();
     var txtResult = new Array();
     var getResult = function(txt){
       if(alreadyState[txt]==1){
         console.log("已经有结果了，正在返回");
         return txtResult[txt];
       }else{
         console.log("正在为您搜索"+txt+"的结果");
         alreadyState[txt]=1;
         txtResult[txt]="这是"+txt+"的搜索结果！";
         return txtResult[txt];
       }
     }
     return getResult;
   }

   var mySearch=searchTxT();
   mySearch("JavaScript");
   mySearch("JavaScript");

   // ==> 正在为您搜索JavaSacript的结果
   // ==> 已经有结果了，正在返回
   ```

## this的使用

   -  函数运行时动态生成的对象
   -  只能在函数内部使用
   -  指的是调用函数的那个对象
   -  闭包的this指向window（不是绝对的）
   -  DOM元素执行绑定事件时，事件内部this为该DOM元素



### 全局中this为window对象

   ```
   console.log(this)
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   ```

### 函数中this也为window对象

   ```javascript
   var x = 1;
   function test(){
       console.log(this);
       console.log(this.x);
   }
   test();

   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> 1
   ```

   ```javascript
     var x = 1;
     function test(){
         console.log(this);
         console.log(this.x);
     }
     function changeX(){
       this.x=5;
     }
     changeX();
     test();

   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> 5  
   ```

   注：说明两个`this`指向的是同一个东西

### 函数内部函数N次嵌套this还是指向window

   ```javascript
   var x = 1;
   var s = function test(){
     console.log(this.x);
     inner();
     function inner(){
       console.log(this.x);
       innerInner();
       function innerInner(){
         console.log(this);
         console.log(this.x);
       }
     }
   }
   s();
   // ==> 1  
   // ==> 1  
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> 1
   ```

   ```javascript
   var x = 1;
   var s = function test(){
     var x = 3;
     console.log(x);
     console.log(this.x);
   }
   s();
   // ==> 3
   // ==> 1
   ```



### 构造函数中的`this`指向对象本身

   ```javascript
   var x = 1;
   function test(){
     console.log(this);
     this.x = 2;
   }
   var o = new test();
   console.log(o.x);
   console.log(x);

   // ==> 2
   // ==> 1
   ```

### 闭包

   ```javascript
   var x = 1;
   function test(){
     console.log(this.x);
     console.log(this);
     this.x = 2;
     var m=function (){
       this.x=4;
       console.log(this);
       console.log(this.x);
       console.log("m");
     }
     return m;
   }
   test();
   // ==> 1
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==>
   ƒ (){
       this.x=4;
       console.log(this);
       console.log(this.x);
       console.log("m");
     }
   ```

   ```javascript
   var x = 1;
   function test(){
     console.log(this.x);
     console.log(this);
     this.x = 2;
     var m=function (){
       this.x=4;
       console.log(this);
       console.log(this.x);
       console.log("m");
     }
     return m;
   }
   test();
   var o = new test();
   console.log(o.x);
   o();
   console.log("x:"+x);

   // ==> 1
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> test {}
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> 4
   // ==> m
   // ==> x:4

   ```

   ```javascript
   var x = 1;
   function test(){
     console.log(this.x);
     console.log(this);
     this.x = 2;
     var m=function (){
       this.x=4;
       console.log(this);
       console.log(this.x);
       console.log("m");
       var t={x:this.x};
       return t;
     }
     return m;
   }
   var o = new test();
   console.log(o.x);
   o();
   console.log("x:"+x);

   // ==> test {}
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> 4
   // ==> m
   // ==> x:4
   ```

### 对象中的this，this不变化后的值变化

   ```javascript
   function test(){
     console.log(this);
     console.log(this.x);
   }
   test();
   var o = {};
   o.x = 1;
   o.m = test;
   o.m();

   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> undefined
   // ==> {x: 1, m: ƒ}
   // ==>  1
   ```

### apply动态指定this

   ```javascript
   var x = 0;
   function test(){
     console.log(this);
     console.log(this.x);
   }
   test();
   var o={
     x:1,
     m:this.test
   };
   o.m.apply();
   o.m.apply(o);
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   // ==> {x: 1, m: ƒ}
   // ==>  1
   ```

   ```javascript
     <input type="text" onclick="test(this)">
     <script>
     function test(t){
       console.log(t);
     }
     // ==>   <input type="text" onclick="test(this)">
     <script>
     function test(t){
       console.log(t);
     }

   // <== t1=document.getElementById("t1")
   // == ><input type="text" onclick="test(this)" id="t1">

   // <== t1.ondlick=function(){console.log(this);}                     
   // ==> ƒ (){console.log(this);}
   ```


## 值传递和引用传递

### 原始值

   -  存储在栈（stack）中的简单数据段，也就是说，他们的值直接存储在变量访问的位置
   -  包括：Undefined、Null、Boolean、Number、String型

### 引用值

   -  存储在堆（heap）中的对象，也就是说，存储在变量处的值是一个指针（point），指向存储对象的内存处

   ![](https://ws2.sinaimg.cn/large/006tKfTcgy1fkopj69c0bj30f30ho3zn.jpg)



### 值传递和引用传递
   -  JavaScript的原始类型，是按值传递的
   -  JavaScript的对象类型，是按共享传递的
   -  原始类型是不可变的，只有对象是可变的
   -  对象的值是引用的，可变的



### 按值传递 call by value

   ```javascript
   var x=1;
   function test(){
       o=2;
   }
   text(x);
   console.log(x);
   // ==> 1
   ```

   ### 按引用传递 call by reference

   ```javascript
   var obj = {x:1}
   function test(o){
       o.x=2;
   }
   test(obj);
   console.log(obj.x)
   // ==> 2
   ```

### 按共享传递 call by sharing

   ```javascript
     var obj = {x:1}
     function test(o){
         o.x=2;
         o = 100;
         t = 200;
         console.log(o);
         return o;
     }
     var s = test(obj);
     console.log("s:"+s);
     console.log("t:"+t);
     console.log("obj.x:"+obj.x);
     console.log("o:"+o);

   // ==> 100
   // ==> s:100
   // ==> t:200
   // ==> obj.x:2
   // ==> Uncaught ReferenceError: o is not defined
   ```

   ```javascript
     function setName(obj){
       obj.name = 'aaa';
       var obj = new Object();						// obj = new Object();也一样
       obj.name = 'ccc';
       return obj;
     }
     var person = new Object();
     person.name = 'bbb';
     var newPerson = setName(person);
     console.log(person.name + ' | ' + newPerson.name);

   // ==> aaa | ccc
   ```

   注：如果`var obj = new Object();`是按引用传递的，此处传参进来obj应该被重新引用新的内存单元。

   ```javascript
     var a = {num:'1'};
     var b = {num:'2'};
     function change(obj){
       obj.num = '3';
       obj = b;
       return obj.num;
     }
     var result = change(a);
     console.log(result + '|' + a.num);
     // ==> 2|3
   ```



### 原始类型是不可变的，只有对象是可变的

   ```javascript
   var str = "abc";
   console.log(str[0]);
   str[0] = "d";
   console.log(str[0]);
   console.log(str);
   // ==> a
   // ==> a
   // ==> abc
   ```

### 对象的值是引用的，可变的

   ```javascript
   var obj = {x:1};
   obj.x = 100;
   var o = obj;
   o.x = 1;
   console.log("obj.x:"+obj.x);
   o = true;
   console.log("obj.x:"+obj.x)
   // ==> obj.x:1
   // ==> obj.x:1
   ```

   ![](https://ws3.sinaimg.cn/large/006tKfTcgy1fkoqlibil0j30h70b1wf8.jpg)

   ![](https://ws3.sinaimg.cn/large/006tKfTcgy1fkoqm36rykj30nx0b4jt1.jpg)


## H5新的标准属性

### form

   ```html
   <h1>form表单新增属性</h1>
   <form id="myform">
   	<fieldset name="userInfo" disabled>
           <legend>
               <label>
                   <input type="checkbox" name="inset" onchange="myform.userInfo.disabled = !checked"/>
               是否填写身份信息
               </label>
           </legend>
           <p><label>姓名: <input type="text" name="uname" required/></label><span>required：该项必填</span></p>
           <p><label>年龄: <input type="text" name="age" pattern="[0-9]{1,2}"/><span>只能输入1-2位数字，pattern：使用正则校验输入的内容</span></label></p>
           <p><label>学习目标: <input type="text" name="target" placeholder="这是placeholder提示的内容"><span>placeholder：设置提示信息</span></label></p>
           <p><label>入学年月： <input name="joinMonth" type="month"/></label></p>
       </fieldset>
       <p>
       <label><input type="text" autofocus>autofocus:元素默认获得焦点</label>
       </p>
       <p>
       <label>数字：<input name="number" type="number" min="5" max="10" step="3">min:设置最小值，max:设置最大值，step:设置当前值的间隔，当前要求必须输入5-10以内，且数字间隔为3</label>
       </p>
       <p>
       <label><input name="file" type="file" multiple/>multiple:允许上传时选择多个文件</label>
       </p>
       <p>
       <label>
       	<input type="text" name="autocomplete" autocomplete="on" list="mylist">
           datalist:设置提示选项
           <datalist id="mylist">
              <option value="Asmita"></option>
              <option value="Aspros"></option>
           </datalist>
       </label>
       </p>
       <p>
           <textarea name="textarea" id="" cols="40" rows="10" maxlength="200" wrap="hard">
           </textarea>
       </p>
       <p>
           <input type="submit" value="提交" formmethod="get"/>
           <input type="submit" value="POST提交" formmethod="post"/>
           <input type="submit" value="不验证提交" formnovalidate/>
       </p>

   </form>

   <!--允许表单在外部定义元素，通过form指向form-->
   <p>允许表单在外部定义元素，通过form属性指向其需要提交的form</p>
   <p><label>email<input name="email" type="email" form="myform" required/></label></p>
   <br/><br/><br/><br/><br/><br/>
   ```



### base

   ```html
   <head>  
   <meta charset="utf-8" />  
   <title>base新增属性</title>
   <base href="http://e.jikexueyuan.com/" />
   <base target="_blank" />
   </head>  

   <body>  
   <h1>base新增属性</h1>
   <img src="headerandfooter/images/logo.png" alt="">
   <br/>
   <h3>
   	&lt;img src="headerandfooter/images/logo.png" alt=""&gt;
   </h3>
   通过设置base href使图片自动在href指定的链接中查找资源
   <br/><br/>
   <hr>
   <br/>
   <a href="http://www.jikexueyuan.com">测试链接</a>
   <h3>
   	&lt;a href="http://www.jikexueyuan.com"&gt;测试链接&lt;/a&gt;
   </h3>
   <br/>
   虽然没有指定target="_blank"，但是受到base target的影响，依然会打开新窗口
   <br/><br/><br/><br/><br/><br/>
   </body>  
   ```



#### manifest

   ```html
   <h1>HTML新增manifest属性</h1>
   <img src="favicon.ico" alt="">
   <script type="text/javascript">
   if ("onoffline" in window) {
       console.log("该浏览器支持onoffline事件!");
   }
   console.log("当前浏览器在线状态："+navigator.onLine);
   window.ononline=function(){
   	console.log("当前浏览器在线");
   	}
   window.onoffline=function(){
   	console.error("当前浏览器离线");
   	}
   </script>
   ```



### `script`新增`async`属性

   ```javascript
   alert("ASMITA");
   ```

   ```javascript
   <head>
   <meta charset="utf-8" />
   <title>script新增async属性</title>
   //异步加载：先弹出窗口，再出现文字
   <script src="script_async.js"></script>
   //同步加载：文字和窗口同时弹出
   <script src="script_async.js" async="async"></script>
   </head>

   <body>
   <h1>script新增async属性</h1>
   </body>
   ```



### `table`新增`contenteditable`属性

   ```javascript
   <head>
   <style>
   table{ border:2px solid #000000; width:400px;}
   td{ border:1px solid #CCCCCC;}
   </style>
   </head>  

   <body>  
   <h1>table新增contenteditable属性</h1>
   <table>
   	<tr>
       	<td>ID</td>
           <td>内容</td>
           <td>备注</td>
       </tr>
       <tr>
       	<td>1</td>
           <td contenteditable="true">ASMITA</td>
           <td contenteditable="true">这行的内容是允许修改的</td>
       </tr>
       <tr>
       	<td>2</td>
           <td>极客学院</td>
           <td>这行的内容不允许修改</td>
       </tr>
   </table>
   </body>  
   ```



### `ol`新增`reversed`属性

   ```javascript
   <head>  
   <meta charset="utf-8" />  
   <title>ol新增reversed属性</title>
   <style>
   table{ border:2px solid #000000; width:400px;}
   td{ border:1px solid #CCCCCC;}
   </style>
   </head>  

   <body>  
   <h1>ol新增reversed属性</h1>
   <ol>
   	<li>我爱学习</li>
   	<li>极客学院</li>
   	<li>ASMITA</li>
   </ol>
   <h2>下面这个是倒序排列的 reversed</h2>
   <ol reversed>
   	<li>我爱学习</li>
   	<li>极客学院</li>
   	<li>ASMITA</li>
   </ol>
   </body>  
   ```


## H5新的事件属性

   ![](https://ws3.sinaimg.cn/large/006tKfTcgy1fkow7g5o9nj318e0kvwjo.jpg)



### `onbeforeunload`

   ```javascript
   <script>
   window.onbeforeunload=checkLeave;
   function checkLeave(){
   	console.log(event);
   	event.returnValue="确定离开当前页面吗？";
   	console.log("确定离开咯");
   	alert("确定离开吗？");			//不能alert
   　　　}
   </script>
   ```

### `onerror`

   ```html javascript
   <input type="button" value="测试" onclick="message()" />
   <script type="text/javascript">
   //window.onerror=handleErr;


   function handleErr(msg,url,line){
   	var txt="";
   	txt="本页中存在错误。\n\n"
   	txt+="错误：" + msg + "\n"
   	txt+="URL: " + url + "\n"
   	txt+="行：" + line + "\n\n"
   	txt+="点击“确定”继续。\n\n"
   	alert(txt)
   	return true;
   	}

   function message(){
   	adddlert("这行是错误的");
   	}
   ```

### `onhashchange`

   ```html
   <head>
   <meta charset="utf-8">
   <style>#hide{display:none; color:red;}</style>
   </head>

   <body>
      <a href="#hash1">Set Hash1</a>
      <a href="#hash2">Set Hash2</a>
      <div id="hide">网上的资料很多是错的，把hashchange写成了haschange</div>
   <script type="text/javascript">
   window.onhashchange=function(){
   	console.log("hash change to:"+location.hash);
   }
   window.onclick=function(){
   	document.getElementById("hide").style.display='block';
   	}
   </script>
   </body>
   ```



### `onoffline`和`ononline`

   这种方法明显不靠谱啊，建议使用ajax请求远程连接，如果错误则表示离线

   ```html
   <head>
   <meta charset="utf-8">
   <style>#hide{ display:none; color:red;}</style>
   </head>

   <body>
   onoffline事件演示，请打开console查看
   <br/>
   <div id="hide">这种方法明显不靠谱啊，建议使用ajax请求远程连接，如果错误则表示离线</div>
   <script type="text/javascript">
   if ("onoffline" in window) {
       console.log("该浏览器支持onoffline事件!");
   }
   console.log("当前浏览器在线状态："+navigator.onLine);
   window.ononline=function(){
   	console.log("当前浏览器在线");
   	}
   window.onoffline=function(){
   	console.error("当前浏览器离线");
   	}
   window.onclick=function(){
   	document.getElementById("hide").style.display='block';
   	}		
   </script>
   </body>
   ```


### `onpagehide`

   ```html
   发生在页面跳转时
   <a href="http://www.baidu.com/">百度</a>
   <script type="text/javascript">
   if ("onpagehide" in window) {
       console.log("该浏览器支持onpagehide事件!");
   }
   window.onpagehide =function(){
   	console.log("PageHide");
   	for(var i=0;i<1000;i++){
   		console.log(i);
   		}
   	}
   </script>
   ```

### `onpageshow`

   经过测试，当前版本浏览器两者都会触发，所以出于兼容考虑， 建议写2个吧

   ```html
   <head>
   <meta charset="utf-8">
   <style>#hide{display:none; color:red;}</style>
   </head>

   <body>
   onpageshow在页面每次加载时触发<br/>
   onload在页面首次加载时触发，如果页面已经被浏览器缓存了，则不触发
   <div id="hide">经过测试，当前版本浏览器两者都会触发，所以出于兼容考虑， 建议写2个吧</div>
   <script type="text/javascript">
   window.onload=function(){
   	console.log("onload");
   	}
   window.onpageshow=function(){
   	console.log("onpageshow");
   	}
   window.onclick=function(){
   	document.getElementById("hide").style.display='block';
   	}
   </script>
   </body>
   ```



### `onpopstate`

   ```html
   <input type="button" value="点我更换url中的页面地址为test1.html" onclick="changeUrl()">
   <br/>
   <input type="button" value="点我换回来" onclick="changeBack()">
   <br/>
   <input type="button" value="点我触发onpopstate事件" onclick="goBack()">
   <div id="testDisp">
   	当前显示页面初始化的内容
   </div>
   <script type="text/javascript">

   	function changeUrl(){
   		history.pushState({test: "s"}, "俺是假的", "test1.html");
   		testDisp.innerHTML="当前显示test1.html的内容";
   		}
   	function changeBack(){
   		history.pushState({page: 1}, "俺是真的", "onpopstate.html");
   		testDisp.innerHTML="当前显示onpopstate.html的内容";
   		}
   	function goBack(){
   		history.back();
   		}

       window.onpopstate = function(event) {
   		console.log("执行onpopstate");
   		console.log(event);
         	console.log("location: " + document.location + ", state: " + JSON.stringify(event.state));  
       };  

   </script>
   <!--实例demo参考页  http://www.zhangxinxu.com/wordpress/2013/06/html5-history-api-pushstate-replacestate-ajax/-->
   ```

### `onresize`

   ```
   <div>窗口大小改变时触发	</div>
   <script type="text/javascript">
       window.onresize = function() {
   		console.log("Hi man,窗口变了哦");
   		console.log("当前窗口【"+document.body.offsetWidth+"x"+document.body.offsetHeight+"】");
       };  

   </script>
   <!--实例demo参考页  http://www.zhangxinxu.com/wordpress/2013/06/html5-history-api-pushstate-replacestate-ajax/-->
   ```

## Web Worker

   -  为网页脚本提供了一种能在后台进程中运行的方法
   -  虽然在后台执行，但是依然会消耗CPU资源
   -  无法访问DOM资源
   -  无法访问全局变量或全局函数
   -  无法使用`alert()`或者`confirm`等浏览器互交类方法


**方法:**
   -  postMessage：发送请求
   -  onmessage：捕获请求
   -  terminate：终止worker，一旦terminate后，无法重新启用，只能另外创建

   ```html
   <div id="result">正在连接服务器</div>
   <script>
   if(typeof(Worker)!=="undefined"){
     console.log("当前浏览器支持web worker");
     }
   else{
     console.error("当前浏览器不支持web worker");
     }

   function pageExec(){
   	for(i=0;i<1000;i++){

   		}
   	return i;
   	}
   //var test=pageExec();
   //console.log(test);
   function doWorker(){ 		//运行轮循事件
   	var worker = new Worker('work.js');
   	worker.onmessage= function (event) {
   	 	document.getElementById("result").innerHTML = event.data+"<br/>";
   	 	console.log(event);
   		worker.terminate();
   		};
   	}
   function doWorker2(){ 		//向worker传递参数
   	var worker = new Worker('work2.js');
   	worker.onmessage= function (event) {
   	 	document.getElementById("result").innerHTML = event.data+"<br/>";
   		};
   	worker.postMessage("小明");
   	worker.onerror = function(e){
   		console.log(e.message+"   on:"+e.filename+" line:"+e.lineno);
   		worker.terminate();
   		};
   	}
   doWorker2();
   </script>

   ```

   ```javascript
   //work.js
   setInterval(returnNowServerConnect,2000);

   function returnNowServerConnect(){
   	postMessage("当前服务器连接人数:"+parseInt(Math.random(1,1000)*1000));
   	}
   ```

   ```javascript
   //work2.js
   alert(1);
   addEventListener("message", function(evt){
   	if(evt.data=="小明"){
   		postMessage(evt.data+"，男，22岁");
   	}
   	else if(evt.data=="李磊"){

   	}
   });
   ```

   ## jQuery

   ### jQuery简介

   -  jQuery是一个工具，一个比原生JavaScript更加高效的工具
   -  jQuery是使用JavaScript写的
   -  尺寸小、使用简单方便、屏蔽浏览器差异、跨浏览器兼容性好
   -  插件丰富、开源、免费
   -  优雅的代码
   -  快速实现动画
   -  更好的选择器



   ### 更好的选择器

   ```javascript
   //JavaScript
   getElementById(xxx)
   getElementsByClassName(xxx)

   //jQuery
   $(#xxx)
   $(.xxx)
   ```



   ### 更好的DOM操作

   ```javascript
   //JavaScript
   getElementById(xxx).style.color="#ccc"

   //jQuery
   $(#xxx).css(color:#ccc)
   ```



   ### 更好的事件处理方法

   ```javascript
   //JavaScript
   getElementById(xxx).onclick=function(){}

   //jQuery
   $(#xxx).on("click",function(){})
   ```



   ### 更好的Ajax

   ```

   ```



   ### 安装使用

   ```javascript
   <script src="jquery.js"></script>
   ```

   **版本：**

   `1.x`  —— 支持IE6/7/8

   `2.x`  ——  支持IE9+

   `3.x`  —— 支持IE9+



   ### 基础语法

   ```javascript
   $(selector).action()
   ```

   -  美元符号`$`定义jQuery
   -  选择符`(selector)`“查询“ 和 ”查找“ HTML元素
   -  `action()`执行对元素的操作



   ## jQuery选择器、事件



   ### id选择器

   ```javascript
   $("#test")
   ```



   ### class选择器

   ```javascript
   $(".test")
   ```



   ### 标签选择器

   ```javascript
   $("div")
   ```



   ### 全部选择器

   ```javascript
   $("*")
   ```

   选择页面中所有元素

   ### 层叠选择器

   ```javascript
   $("div span")
   $("form > input")
   ```

   -  选择`div`中的所有`span`元素
   -  选择`form`中的所有`input`元素，只包括第一层

   ### 常用事件

   ![](https://ws1.sinaimg.cn/large/006tKfTcgy1fkozg7pbvpj30w10bmgpv.jpg)



   -  `mouseenter` —— `mouseover`
   -  `mouseleave`—— `mouseout`



   ### 事件的绑定

   ```javascript
   .bind
   $(xxx).bind(type[,data],fn)

   .on
   $(xxx).on(events[,selector][,data],handler)
   ```

   ```html
   <head>
       <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
       <title>事件的绑定与解除</title>
       <script src="jquery.js"></script>
       <style>
       div {
           width: 300px;
           height: 200px;
           background: #CCCCCC;
       }
       </style>
   </head>

   <body>
       <div></div>
       <input type="button" value="点击绑定按钮事件" id="dobind">
       <input type="button" value="点击解除按钮事件" id="unbind">
       <script>
       $("#dobind").on("click", function() {
           $("div").on("click", function() {
               alert("hello");
           });
       });
       $("#unbind").on("click", function() {
           $("div").off("click");
       });
       </script>
   </body>
   ```



   ### 事件的解除

   ```javascript
   .unbind
   $(xxx).unbind(type[,data],fn)

   .off
   $(xxx).off([events[,selector][,handler]])
   ```



   ### 事件冒泡

   在一个对象上触发某类事件（比如单击onclick事件），如果此对象定义了此事件的处理程序，那么此事件就会调用这个处理程序，如果没有定义此事件处理程序或者事件返回true，那么这个事件会向这个对象的父级对象传播，从里到外，直至它被处理（父级对象所有同类事件都将被激活），或者它到达了对象层次的最顶层，即document对象（有些浏览器是window）

   ```javascript
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
   <title>冒泡和阻止冒泡</title>
   <script src="jquery.js"></script>
   </head>

   <body>
       <div id="out">
           <div id="middle">
           	<a href="#">测试</a>
           </div>
       </div>
   <script>
   $("#out").on("click",function(){console.log("out");});
   $("#middle").on("click",function(){console.log("middle");});
   $("a").on("click",function(event){
   	console.log("a");
   	//event.stopPropagation();		//阻止冒泡,但不阻止a标签的默认行为
   	//return false;					//阻止a标签跳转的默认行为
   	//event.preventDefault();			//只阻止默认行为，不阻止冒泡
   	//event.stopImmediatePropagation();	//阻止所有事件，包括平级的
   	});
   $("a").on("click",function(event){
   	console.log("b");
   	});
   </script>
   </body>

   // ==> a
   // ==> b
   // ==> middle
   // ==> out
   ```



   ### 自定义事件

   -  `on` —— 绑定事件
   -  `trigge ` —— 触发事件

   ```javascript
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
   <title>自定义事件</title>
   <script src="jquery.js"></script>
   </head>

   <body>
       <input type="button" id="myipt" value="开门">
       <p id="doorState"></p>
       <p id="tempState"></p>
   <script>
   var myipt=$("#myipt");
   myipt.on("click",function(){
   	if(this.value=="开门"){
   		doorState.trigger("openTheDoor");
   		tempState.trigger("openTheDoor");
   		this.value="关门";
   		}
   	else{
   		doorState.trigger("closeTheDoor");
   		tempState.trigger("closeTheDoor");
   		this.value="开门";
   		}
   	});
   var doorState=$("#doorState");
   doorState.on("openTheDoor",function(){
   	$(this).html("门是开着的");
   	});
   doorState.on("closeTheDoor",function(){
   	$(this).html("门是关着的");
   	});
   var tempState=$("#tempState");
   tempState.on({
   	openTheDoor:function(){
   		$(this).html("现在温度-1°");
   		},
   	closeTheDoor:function(){
   		$(this).html("现在温度3°");
   		}
   	});


   </script>
   </body>
   ```



   ## jQuery效果

   ### 显示与隐藏

   可设置速度和回调方法

   ```javascript
   $(selector).show(speed,callback)
   $(selector).hide(speed,callback)
   ```



   ```html
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
   <title>Jquery特效 - hide</title>
   <script src="jquery.js"></script>
   <style>
   div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}

   </style>
   </head>

   <body>
   <div id="hide">
       点击我消失hide()
   </div>
   <input type="button" value="点击显示消失的元素">
   <div id="hide2">
       点击我慢慢消失hide("slow",function(){alert("我是回调")});}
   </div>
   <div id="hide3">
       点击我快速消失hide("fast")
   </div>
   <div id="hide4">
       点击我10秒后消失hide(10000)
   </div>
   <script>
   $("#hide").on("click",function(){$(this).hide();});
   $("#hide2").on("click",function(){$(this).hide("slow",function(){alert("我是回调")});});
   $("#hide3").on("click",function(){$(this).hide("fast");});
   $("#hide4").on("click",function(){$(this).hide(10000);});

   $("input").on("click",function(){$("#hide").show();});
   </script>
   </body>
   ```



   ### 滑动

   设置滑动显示、滑动隐藏、滑动隐藏显示状态切换，可设置速度和回调方法

   ```javascript
   $(selector).slideDown(speed,callback)
   $(selector).slideUp(speed,callback)
   $(selector).slideToggle(speed,callback)
   ```

   ```html
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
   <title>Jquery特效 - slideToggle</title>
   <script src="jquery.js"></script>
   <style>
   div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}

   </style>
   </head>

   <body>
   <div id="test1">
       点击我消失slideUp()
   </div>
   <input type="button" value="点击显示消失的元素slideDown()">
   <div id="test2">
       下面的按钮一点击，我就会慢慢消失。<br/>再点击一次还会回来的<br/>slideToggle("slow",function(){alert("我是回调")});}
   </div>
   <input type="button" value="点击切换状态">
   <div id="test3">
       点击我快速消失slideUp("fast")
   </div>
   <div id="test4">
       点击我10秒后消失slideUp(10000)
   </div>
   <script>
   $("#test1").on("click",function(){$(this).slideUp();});
   $("#test3").on("click",function(){$(this).slideUp("fast");});
   $("#test4").on("click",function(){$(this).slideUp(10000);});

   $("input:nth-child(2)").on("click",function(){$("#test1").slideDown();});
   $("input:nth-child(4)").on("click",function(){$("#test2").slideToggle("slow",function(){alert("我是回调")});});
   </script>
   ```



   ### 淡入淡出

   设置淡入、淡出、到指定的透明度，可设置速度、（透明度）、和回调方法

   ```
   $(selector).fadeIn(speed,callback)
   $(selector).fadeOut(speed,callback)
   $(selector).fadeTo(speed,opacity,callback)
   ```

   ```html
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
   <title>Jquery特效 - fade</title>
   <script src="jquery.js"></script>
   <style>
   div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}

   </style>
   </head>

   <body>
   <div id="test1">
       被操作的元素
   </div>
   <input type="button" value="淡入">
   <input type="button" value="淡出">

   <div id="test2">
       点击设置透明度到30%
   </div>
   <script>
   $("input:nth-child(2)").on("click",function(){$("#test1").fadeIn();});
   $("input:nth-child(3)").on("click",function(){$("#test1").fadeOut();});
   $("#test2").on("click",function(){$(this).fadeTo(2000,0.3)})
   </script>
   </body>
   ```

### 自定义动画

```javascript
$(selector).animate({params},[duration],[easing],[callback])
```

-  `params` ——动画参数，比如`{width:"300px",opacity:0.3}`
-  `duration` —— 持续时间，比如`"slow" "fase" "normal"`或毫秒
-  `easing` —— 动画的执行方式，比如 `"liner" "swing"`
-  ``callback` —— 回调方法



```html javascript
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery特效 - animation</title>
<script src="jquery.js"></script>
<style>
div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}

</style>
</head>

<body>
<div id="test1">
    点击运行动画
    <br/>
    animate(
    	{width:"400px",opacity:0.3,height:"400px"},3000
        )

</div>
<script>
$("#test1").on("click",function(){
	$(this).animate({width:"400px",opacity:0.3,height:"400px"},3000,function(){alert("callback")});
	});
</script>
</body>
```

## jQuery属性操作

### 添加、删除元素

```
//添加元素
$(selector).addClass(class)
//删除元素
$(selector).removeClass(class)
//添加或删除元素，switch为布尔值，用来确定是否添加class
$(selector).toggleClass(class)
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery属性操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
</style>
</head>

<body>
<div id="test1">

</div>
<button>绿色</button>
<button>还原</button>
<button>切换</button>
<button>检查</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.addClass("green");
	});
$($("button").get(1)).on("click",function(){
	test1.removeClass("green");
	});
$("button").eq(2).on("click",function(){
	test1.toggleClass("green");
	});
$("button").eq(3).on("click",function(){
	alert(test1.hasClass("green"));
	});
</script>
</body>
```



### 判断元素是否有指定的class

```
$(selector).hasClass(class)
```



### 获取或设置元素内容

```
$(selector).html()
```

相当于`innerHTML`

### 获取或设置元素值

```
$(selector).val()
```

相当于`value`

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery属性操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
</style>
</head>

<body>
<div id="test1">
   这是test1的内容
</div>
<button>获取test1的内容</button>
<button>设置input的内容</button>
<br/>
<input type="text" id="ipt" value="极客学院">
<button>获取input的内容</button>
<button>获取input的值</button>
<button>设置input的值</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	console.log(test1.html());
	});
$($("button")[1]).on("click",function(){
	test1.html("这是设置过后的内容");
	});
var ipt=$("#ipt");
$($("button")[2]).on("click",function(){
	console.log(ipt.html());
	});
$($("button")[3]).on("click",function(){
	console.log(ipt.val());
	});
$($("button")[4]).on("click",function(){
	ipt.val("让学习更有效");
	});			
</script>
</body>
```



### `attr`

```javascript
//获取元素属性的值
$(selector).attr(attribute)
//设置(添加)圆度的属性和值
$(selector).attr(attribute,value)
//删除元素属性及值
$(selector).removeAttr(attribute)
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery属性操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
</style>
</head>

<body>
<div id="test1" uid="35">
   我是是test1，我的默认uid是35
</div>
<button>获取test1的uid</button>
<button>设置input的uid</button>
<button>移除uid属性</button>
<br/>
<input type="text" id="ipt" value="极客学院">
<button>获取input的值</button>
<button>设置input的值</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	console.log(test1.attr("uid"));
	});
$($("button")[1]).on("click",function(){
	test1.attr("uid","40");
	});
$($("button")[2]).on("click",function(){
	test1.removeAttr("uid");
	});
var ipt=$("#ipt");
$($("button")[3]).on("click",function(){
	console.log(ipt.attr("value"));
	});
$($("button")[4]).on("click",function(){
	ipt.attr("value","让学习更有效");
	});

</script>
</body>
```



## jQuery文档操作

### after和before插入指定的内容

```
//在被选元素后插入指定的内容
$(selector).after(content)
//在被选元素前插入指定的内容
$(selector).before(content)
//在被选元素前插入指定的内容
$(selector).before(function(index))
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery文档操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
</style>
</head>

<body>
<div id="test1">
   这是test1的内容
</div>
<button>使用after插入内容</button>
<button>使用before插入内容</button>
<br/><br/>
<span>ABC</span>
<br/>
<span>DEF</span>
<br/>
<button>使用before的第二种方法插入内容</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.after("<p>这是after新插入的内容</p>");
	});
$($("button")[1]).on("click",function(){
	test1.before("<p>这是before新插入的内容</p>");
	});
$($("button")[2]).on("click",function(){
	$("span").before(
		function(i){
			return "<p>这是before新插入的内容"+i+"</p>"
		});
	});
</script>
</body>
```



### insertAfter和insertBefore插入指定的内容

```
$(content).insertBefore(selector)
$(content).insertAfter(selector)
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery文档操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; min-height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
</style>
</head>

<body>
<div id="test1">
   这是test1的内容
</div>
<button>使用insertAfter插入内容</button>
<button>使用insertBefore插入内容</button>

<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	$("<p>这是insertAfter新插入的内容</p>").insertAfter("#test1");
	});
$($("button")[1]).on("click",function(){
	$("<p>这是insertBefore新插入的内容</p>").insertBefore("#test1");
	});
</script>
</body>
```



### `append`

在被选元素结尾(元素内)插入指定的内容

```
$(selector).append(content)

//如果content是页面内的元素，则会删除原有元素
$(content).appendTo(selector)
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery文档操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; min-height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
</style>
</head>

<body>
<div id="test1">
   这是test1的内容
</div>
<button>使用append 插入内容</button>
<button>使用appendTo插入内容</button>
<nav></nav>
<nav></nav>
<button>使用appendTo插入内容2</button>
<div id="test2">
	这是test2的内容
</div>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.append("<p>这是append新插入的内容</p>");
	});
$($("button")[1]).on("click",function(){
	test1.appendTo("nav");
	});
$($("button")[2]).on("click",function(){
	$("<p>这是append新插入的内容</p>").appendTo("#test2");
	});
</script>
</body>
```



### `prepend`

在被选元素开头(元素内)插入指定的内容

```
$(selector).prepend(content)

//如果content是页面内的元素，则会删除原有元素
$(content).prependTo(selector)
```



### `clone`/`detach`/`empty`

复制被选元素，包含它的子节点、文本和属性

`includeEvents`为可选项，布尔值，用于设定是否肤质元素的绑定事件

```
$(selector).clone(includeEvents)
```

移除被选元素，包含它的子节点、文本和属性

```
$(selector).detach()
```

清空被选元素的子节点、文本和属性

```
$(selector).empty()
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery文档操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; min-height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
</style>
</head>

<body>
<div id="test1">
   这是test1的内容
</div>
<p class="clone1">被克隆的对象1</p>
<p id="clone2">被克隆的对象2，点击我试试</p>
<button>使用clone插入内容</button>
<button>使用clone插入内容2,并复制其绑定事件</button>
<br/>
<button>detach移除clone1对象</button>
<button>detach移除clone2对象</button>
<br/>
<button>empty清空test1的内容</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.prepend($(".clone1").clone());
	});
$($("button")[1]).on("click",function(){
	test1.before($("#clone2").clone(true));
	});
$("#clone2").on("click",function(){alert("hello")});

$($("button")[2]).on("click",function(){
	$(".clone1").detach();
	});
$($("button")[3]).on("click",function(){
	$("#clone2").detach();
	});
$($("button")[4]).on("click",function(){
	$("#test1").empty();
	});
</script>
</body>
```



### `wrap`

将被选元素用`wrapper`内的参数进行包裹

```javascript
$(selector).wrap(wrapper)
```

`wrapper`的三种格式

1.  `("<div></div>")``
2. ``document.creatElement("div")`
3. `$("#test1")`

使用已经存在的元素包裹不会删除原来的元素



**移除被选元素的父元素**

```
$(selector)upwrap()
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery文档操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; min-height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
div#test1{ background:#C39738;}
</style>
</head>

<body>
<div id="test1">
   这是test1的内容
</div>
<span class="span1">被包裹的元素span1</span>
<br/>
<button>使用wrap包裹span1</button>
<br/><br/>

<span class="span2">被包裹的元素span2</span>
<br/>
<button>使用wrap包裹span2</button>
<br/><br/>

<span class="span3">被包裹的元素span3</span>
<br/>
<button>使用wrap包裹span3</button>
<button>使用unwrap移除span3的父元素</button>
<br/><br/>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	$(".span1").wrap("<div></div>");
	});
$($("button")[1]).on("click",function(){
	$(".span2").wrap(document.createElement("div"));
	});
$($("button")[2]).on("click",function(){
	$(".span3").wrap($("#test1"));
	});
$($("button")[3]).on("click",function(){
	$(".span3").unwrap();
	});
</script>
</body>
```



### `wrapAll`和`wrapInner`

```javascript
$(selector).wrapAll(wrapper)
```

被选元素移动到第一个元素的位置，并用wrapper内的参数进行包裹

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery文档操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; min-height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
div#test1{ background:#C39738;}
</style>
</head>

<body>
<span class="span1">被包裹的元素span1</span>
<br/><a href="#">这是一个捣乱的a标签</a><br/>
<span class="span2">被包裹的元素span2</span>
<br/>
<span class="span3">被包裹的元素span3</span>

<button>使用wrapAll包裹所有span元素</button>
<br/><br/>
<script>
$($("button")[0]).on("click",function(){
	$("span").wrapAll("<div></div>");
	});
</script>
</body>
```



```javascript
$(selector).wrapInner(wrapper)
```

将被选元素内的元素用wrapper内的参数进行包裹

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery文档操作</title>
<script src="jquery.js"></script>
<style>
div { width:300px; min-height:80px; background:#CCCCCC; margin:20px; text-align:center;}
div.green{ background:green;}
div#test1{ background:#C39738;}
</style>
</head>

<body>

<p>第一行</p>
<p>第二行</p>

<button>使用wrapInner包裹所有p元素</button>
<br/><br/>
<script>
$($("button")[0]).on("click",function(){
	$("p").wrapInner("<b></b>");
	});
</script>
</body>
```



## jQuery遍历

### 向下遍历

```javascript
$(selector).children()
```

获取子元素，但是只获取到第一层

```javascript
$(selector).find(selector)
```

查找子元素，并返回元素集合，可获取所有层级子元素

```
$(selector).eq(index)
```

获取子元素，可获取所有层级子元素

```
$(selector).contents()
```

获取子元素，包括文本和注释节点

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery遍历 向下遍历</title>
<script src="jquery.js"></script>
<style>
div { width:400px; height:200px; background:#CCCCCC; margin:20px; text-align:center; display:-webkit-box; -webkit-box-align:center; -webkit-box-pack:center;}
div#test1{ width:600px; height:150px; background:#E52225}
div.test2{ width:200px; height:100px; background:#E0D42A}
div.test3{ width:150px; height:50px;}
</style>
</head>

<body>
<div id="test1">
	<div class="test2">
    	<div class="test3">

        </div>
    </div>
    <!--这是一行注释-->
    <div class="test2">
    	<div class="test3">

        </div>
    </div>
    我是test1
</div>
<button>使用children设置子元素边框</button>
<button>使用find设置子元素为div的边框</button>
<button>使用find设置子元素class为test3的边框</button>
<button>使用eq设置子元素2的边框</button>
<button>使用contents获取注释内容</button>
<button>使用contents设置子元素5的边框</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.children().css({border:"3px solid green"});
	});
$($("button")[1]).on("click",function(){
	test1.find("div").css({border:"3px solid green"});
	});
$($("button")[2]).on("click",function(){
	test1.find(".test3").css({border:"3px solid green"});
	});
$($("button")[3]).on("click",function(){
	$("#test1 div").eq(2).css({border:"3px solid green"});
	});
$($("button")[4]).on("click",function(){
	console.log(test1.contents()[3]);
	});
$($("button")[5]).on("click",function(){
	$(test1.contents()[5]).css({border:"3px solid green"});;
	});
</script>
</body>
```



### 向上遍历

获取上一层父元素

```
$(selector).parent(selector)
```

获取所有父元素

```
$(selector).parents(selector)
```

获取所有父元素直到selector结束，filter为获取条件，非必填

```
$(selector).parentsUntil(selector,filter)
```



```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery遍历 向上遍历</title>
<script src="jquery.js"></script>
<style>
div { width:400px; height:200px; background:#CCCCCC; margin:20px; text-align:center; display:-webkit-box; -webkit-box-align:center; -webkit-box-pack:center;}
div.test{ width:800px; height:300px; background:#A6ED04;}
div.test1{ width:600px; height:200px; background:#E52225}
div.test2{ width:200px; height:150px; background:#E0D42A}
div.test3{ width:150px; height:50px;}
</style>
</head>

<body>
<div class="test">
    <div class="test1">
        <div class="test2">
            <div class="test3">
                我是test3
            </div><br/>
        </div>
        <!--这是一行注释-->
        <div class="test2">
            <div class="test3" id="test1">
                我是id:test1
            </div>
        </div>
        我是class:test1
    </div>
</div>
<button>使用parent设置父元素边框</button>
<button>使用parents设置父元素边框</button>
<button>使用parentsUntil设置父元素边框</button>
<br/>
<button>使用parentsUntil设置父元素边框直到class为test1结束</button>
<button>使用parentsUntil设置父元素为div的边框直到class为test结束</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.parent().css({border:"3px solid green"});
	});
$($("button")[1]).on("click",function(){
	test1.parents().css({border:"3px solid green"});
	});
$($("button")[2]).on("click",function(){
	test1.parentsUntil().css({border:"3px solid green"});
	});
$($("button")[3]).on("click",function(){
	test1.parentsUntil($(".test1")).css({border:"3px solid green"});
	});
$($("button")[4]).on("click",function(){
	test1.parentsUntil($(".test"),"div").css({border:"3px solid green"});
	});
</script>
</body>
```



### 同级遍历next

获取下一个同级元素

```
$(selector).next(selector)
```

获取后面所有同级元素

```
$(selector).nextAll(selector)
```

获取后面所有同级元素直到selector结束，filter为或许条件，非必填

```
$(selector).nextsUntil(selector,filter)
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery遍历 同级遍历</title>
<script src="jquery.js"></script>
<style>
div { width:400px; height:200px; background:#CCCCCC; margin:20px; text-align:center; display:-webkit-box; -webkit-box-align:center; -webkit-box-pack:center;}
div.test{ width:1000px; height:300px; background:#A6ED04;}
div.test1{ width:950px; height:200px; background:#E52225}
div#test1{width:300px;}
div.test2{ width:200px; height:150px; background:#E0D42A}
div.test3{ width:150px; height:50px;}
</style>
</head>

<body>
<div class="test">
    <div class="test1">
        <div class="test2" id="test1">
            <div class="test3">
                我是test3
            </div>
            <p>我是id：test1</p>
        </div>
        <!--这是一行注释-->
        <div class="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        <div class="test2" id="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        我是class:test1
    </div>
</div>
<button>使用next设置下一个元素边框</button>
<button>使用nextAll设置后面所有元素边框</button>
<button>使用nextUntil设置后面所有元素边框直到id为test2结束</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.next().css({border:"3px solid green"});
	});
$($("button")[1]).on("click",function(){
	test1.nextAll().css({border:"3px solid green"});
	});
$($("button")[2]).on("click",function(){
	test1.nextUntil($("#test2")).css({border:"3px solid green"});
	});
</script>
</body>
```

### 同级遍历prev

获取上一个同级元素

```
$(selector).prev(selector)
```

获取前面所有同级元素

```
$(selector).prevAll(selector)
```

获取前面所有同级元素直到selector结束，filter为或许条件，非必填

```
$(selector).prevUntil(selector,filter)
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery遍历 同级遍历</title>
<script src="jquery.js"></script>
<style>
div { width:400px; height:200px; background:#CCCCCC; margin:20px; text-align:center; display:-webkit-box; -webkit-box-align:center; -webkit-box-pack:center;}
div.test{ width:1000px; height:300px; background:#A6ED04;}
div.test1{ width:950px; height:200px; background:#E52225}
div#test1{width:300px;}
div.test2{ width:200px; height:150px; background:#E0D42A}
div.test3{ width:150px; height:50px;}
</style>
</head>

<body>
<div class="test">
    <div class="test1">
        <div class="test2" id="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        <!--这是一行注释-->
        <div class="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        <div class="test2" id="test1">
            <div class="test3">
                我是test3
            </div>
            <p>我是id：test1</p>
        </div>
        我是class:test1
    </div>
</div>
<button>使用prev设置上一个元素边框</button>
<button>使用prevAll设置后面所有元素边框</button>
<button>使用prevUntil设置后面所有元素边框直到id为test2结束</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.prev().css({border:"3px solid green"});
	});
$($("button")[1]).on("click",function(){
	test1.prevAll().css({border:"3px solid green"});
	});
$($("button")[2]).on("click",function(){
	test1.prevUntil($("#test2")).css({border:"3px solid green"});
	});
</script>
</body>
```



### 同级遍历siblings

获取同级的其他元素

```
$(selector).siblings(selector)
```

```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery遍历 同级遍历</title>
<script src="jquery.js"></script>
<style>
div { width:400px; height:200px; background:#CCCCCC; margin:20px; text-align:center; display:-webkit-box; -webkit-box-align:center; -webkit-box-pack:center;}
div.test{ width:1000px; height:300px; background:#A6ED04;}
div.test1{ width:950px; height:200px; background:#E52225}
div#test1{width:300px;}
div.test2{ width:200px; height:150px; background:#E0D42A}
div.test3{ width:150px; height:50px;}
</style>
</head>

<body>
<div class="test">
    <div class="test1">
        <div class="test2" id="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        <!--这是一行注释-->
        <div class="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        <div class="test2" id="test1">
            <div class="test3">
                我是test3
            </div>
            <p>我是id：test1</p>
        </div>
        我是class:test1
    </div>
</div>
<button>使用siblings设置同级元素边框</button>
<button>使用siblings设置同级id为test2的元素边框</button>
<script>
var test1=$("#test1");
$($("button")[0]).on("click",function(){
	test1.siblings().css({border:"3px solid green"});
	});
$($("button")[1]).on("click",function(){
	test1.siblings("#test2").css({border:"3px solid green"});
	});
</script>
</body>
```



### 过滤

获取被选中的首个元素

```
$(selector).first()
```

获取被选中的最后一个元素

```
$(selector).last()
```

获取被选中的元素中排除第二个selector设置的元素

```
$(selector).not(selector)
```

获取被选中的元素中保留第二个selector设置的元素

```
$(selector).filter(selector)
```



```html
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Jquery遍历 过滤</title>
<script src="jquery.js"></script>
<style>
div { width:400px; height:200px; background:#CCCCCC; margin:20px; text-align:center; display:-webkit-box; -webkit-box-align:center; -webkit-box-pack:center;}
div.test{ width:1000px; height:300px; background:#A6ED04;}
div.test1{ width:950px; height:200px; background:#E52225}
div#test1{width:300px;}
div.test2{ width:200px; height:150px; background:#E0D42A}
div.test3{ width:150px; height:50px;}
</style>
</head>

<body>
<div class="test">
    <div class="test1">
        <div class="test2" id="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        <!--这是一行注释-->
        <div class="test2">
            <div class="test3">
                我是test3
            </div>
        </div>
        <div class="test2" id="test1">
            <div class="test3">
                我是test3
            </div>
            <p>我是id：test1</p>
        </div>
        我是class:test1
    </div>
</div>
<button>使用first设置第一个元素边框</button>
<button>使用last设置最后一个元素边框</button>
<button>使用not设置class不等于test2的元素边框</button>
<button>使用filter设置class等于test2的元素边框</button>
<script>
$($("button")[0]).on("click",function(){
	$("div").first().css({border:"3px solid green"});
	});
$($("button")[1]).on("click",function(){
	$("div").last().css({border:"3px solid green"});
	});
$($("button")[2]).on("click",function(){
	$("div").not(".test2").css({border:"3px solid green"});
	});
$($("button")[3]).on("click",function(){
	$("div").filter(".test2").css({border:"3px solid green"});
	});		
</script>
</body>
```
