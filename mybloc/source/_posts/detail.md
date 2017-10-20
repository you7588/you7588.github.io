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

   ```javascript
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

   ​
