---
title: Javascript Basics （语言核心）
date: 2017-10-09 12:35:37
tags: JS
---


# JavaScript的主要内容
1. 写入HTML输出
2. 对事件作出反应
3. 改变HTML内容
4. 改变HTML图像
5. 改变HTML样式
6. 验证输入


# JavaScript 使用
1. HTML 中的脚本必须位于 `<script>` 与 `</script>` 标签之间。
2. 脚本可被放置在 HTML 页面的 `<body>` 和 `<head>` 部分中。
3. 那些老旧的实例可能会在 `<script>` 标签中使用 `type="text/javascript"`。现在已经不必这样做了。JavaScript 是所有现代浏览器以及 HTML5 中的默认脚本语言。
4. 可以在 HTML 文档中放入不限数量的脚本。
5. 脚本可位于 HTML 的 `<body>` 或 `<head>` 部分中，或者同时存在于两个部分中。通常的做法是把函数放入 `<head>` 部分中，或者放在页面底部。这样就可以把它们安置到同一处位置，不会干扰页面的内容。
6.  把脚本保存到外部文件中。外部文件通常包含被多个网页使用的代码，其扩展名是 `.js`。如需使用外部文件，请在 `<script>` 标签的 `"src"` 属性中设置该 `.js` 文件：
7.  在 `<head>` 或 `<body>` 中引用脚本文件都是可以的。实际运行效果与您在 `<script>` 标签中编写脚本完全一致。
8.  外部脚本不能包含` <script>` 标签。

---

# JavaScript 输出

## 操作 HTML 元素
从 JavaScript 访问某个 HTML 元素，可以使用 `document.getElementById(*id*) `方法。
（`"id"` 属性来标识 HTML 元素）通过指定的 `id` 来访问 HTML 元素，并改变其内容：

```html
<body>
<h1>我的第一张网页</h1>
<p id="demo">我的第一个段落</p>

<script>
document.getElementById("demo").innerHTML="我的第一段 JavaScript";
</script>
</body>
```

## 写到文档输出
下面的例子直接把 `<p>` 元素写到 HTML 文档输出中：

```javascript
<body>
<h1>我的第一张网页</h1>

<script>
document.write("<p>我的第一段 JavaScript</p>");
</script>

</body>
```

## 警告
请使用 `document.write()` 仅仅向文档输出写内容。
如果在文档已完成加载后执行 `document.write`，整个 HTML 页面将被覆盖：

```html
<body>

<h1>我的第一张网页</h1>

<p>我的第一个段落。</p>

<button onclick="myFunction()">点击这里</button>

<script>
function myFunction()
{
document.write("糟糕！文档消失了。");
}
</script>
</body>
```

---

# Character Set（字符集）

-  JavaScript程序使用*Unicode*字符集编写。Unicode是*ASCII*和*Latin-1*的超集，并支持地球上几乎所有在用的语言。
-  JavaScript是区分大小写的语言（case-sensitive language）。HTML并不区分大小写（尽管XHTML区分大小写）。
-  JavaScript忽略程序中标记之间出现的空格。在大多数情况下，JavaScript也会忽略换行符。
-  对代码行进行折行。可在文本字符串中使用反斜杠（“\”)对代码行进行换行。

---

# Printing Output
> We use the *console.log* method to write data to [standard output](https://en.wikipedia.org/wiki/Standard_streams#Standard_output_.28stdout.29) in JavaScript.

```javascript
function main() {
    console.log("You entered the following text in the Input box:");

    const input = readLine();
    console.log(input);
}
```

```bash
#input
I'm using JavaScript to print to stdout.

#output
You entered the following text in the Input box:
I'm using JavaScript to print to stdout.
```

---

# JavaScript 语句

JavaScript 语句向浏览器发出的命令。语句的作用是告诉浏览器该做什么。

下面的 JavaScript 语句向 id="demo" 的 HTML 元素输出文本 "Hello World"：

```javascript
document.getElementById("demo").innerHTML="Hello World";
```

1. Optional Semicolon（可选的分号）—— 像许多编程语言一样，JavaScript使用分号（`;`）来分隔语句。
2. JavaScript 代码（或者只有 JavaScript）是 JavaScript 语句的序列。浏览器会按照编写顺序来执行每条语句。
3. JavaScript 代码块

组合JavaScript 语句，{起始和结束}，作用：使语句序列一起执行。
JavaScript 函数是将语句组合在块中的典型例子。

```javascript
function myFunction()
{
document.getElementById("demo").innerHTML="Hello World";
document.getElementById("myDIV").innerHTML="How are you?";
}
```
---

# Literals（直接量）
>  程序中直接使用的数据值。

```javascript
// The integer number twelve:
12

// The floating-point number one-point-two:
1.2

// A string of text:
"Hello, World."

// Another string:
'Hi!'

// A boolean value:
true

// The absence of an object:
null

//正则表达式直接量（用作模式匹配）
/javascript/gi

// An object initializer:
{x: 1, y: 2}

// An array initializer:
[1, 2, 3, 4, 5]
```

---


# Identifiers（标识符和保留字）

**标识符**

标识符只是一个名称，用来对变量和函数进行命名，以及为某些代码循环语句中的跳转位置的标记。

-  JavaScript标识符必须以字母、下划线（`_`）或美元符号（`$`）开头。
-  后续字符可以是字母，下划线，美元符号或数字。
-  JavaScript不允许将数字作为标识符的第一个字符。

```javascript
// Some valid identifiers are:
x
variable_name
sum13
_variable
$variable
```

**保留字 reserved words 和 关键字 keywords**
许多标识符是*保留字*或*关键字*，这意味着它们是一组在语言本身具有特殊意义的预定义单词的一部分。您不能在程序中使用这些单词作为标识符。

**关键字**

```javascript
break
delete function
return
typeof
case
og
if
switch
var
catch
else
in
this
void
continue
false
instanceof
throw
while
debugger
finally
new
true
with
default
for
null
try
```

**保留的关键字**
```javascript
class
const
enum
export
extends
import
super
implements
let
private
public
yield
interface
package
protected
static
```

**不完全的保留字**
```javascript
arguments
eval
```

**全局变量和函数**
```javascript
arguments
encodeURI
Infinity
Number
RegExp
Array
encodeURIComponent
isFinite
Object
String
Boolean
Error
isNaN
parseFloat
SyntaxError
Date
eval
JSON
parseInt
TypeError
decodeURI
EvalError
Math
RangeError
undefined
decodeURIComponent
Function
NaN
ReferenceError
URIError
```
---

# Task——Hello, World!
```javascript
function greeting(parameterVariable) {
    // This line prints 'Hello, World!' to the console:

    // Write a line of code that prints parameterVariable to stdout using console.log:
}

function main() {
    const parameterVariable = readLine();
    greeting(parameterVariable);
}
```

**Input**
```
Welcome to 10 Days of JavaScript!
```

**Output**
```
Hello, World!
Welcome to 10 Days of JavaScript!
```

**answer**
```javascript
function greeting(parameterVariable) {
    console.log('Hello, World!');
    console.log(parameterVariable)
}
```

# Reference
[Hackerrank](https://www.hackerrank.com/challenges/js10-hello-world/problem)
《JavaScript权威指南》
[w3schools](http://www.w3schools.com/)
