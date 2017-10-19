---
layout: data
title: JavaScript’s Data Types（数据类型）
date: 2017-10-08 21:26:29
tags:
---


# JavaScript's Data Types（数据类型）
> The latest [ECMAScript](http://www.ecma-international.org/ecma-262/7.0/index.html) standard defines seven data types:
> JavaScript 拥有动态类型,这意味着相同的变量可用作不同的类型：

- **primitive type（原始类型）**
>  A primitive value or data type is data that is not an object and has no methods. All primitives are immutable, meaning they cannot be changed. There are six primitive types:

   -  **String  字串符** —— 存储字符（比如 "Bill Gates"）的变量
   -  **Number 数字** —— JavaScript 只有一种数字类型
   -  **Boolean 布尔值** —— 布尔（逻辑）只能有两个值：true 或 false。
   -  **Symbol**
   -  **Null 空** -- 不包含任何属性和方法
   -  **Undefined 未定义** —— 表示变量不含有值，不包含任何属性和方法

-  **Object type（对象类型）**
> The seventh data type.

   -  **普通对象** —— 对象由花括号分隔
   -  **数组**
   -  **函数**
   -  **日期**
   -  **正则**
   -  **错误**​

---

# String Data Type（字符串）
> A string value is a chain of zero or more Unicode characters (i.e., letters, digits,  spaces, numbers, symbols or punctuation marks) that we use to represent text.

## 字符串直接量
```javascript
//字符串可以是引号中的任意文本。您可以使用单引号或双引号：
var carname="Bill Gates";
var carname='Bill Gates';

//您可以在字符串中使用引号，只要不匹配包围字符串的引号即可：
var answer="Nice to meet you!";
var answer="He is called 'Bill'";
var answer='He is called "Bill"';

var firstString = "Hello, There.";
var secondString = "How're you?";
var thirdString = "c";                                      // 单个字符
var fourthString = '"Wow!!!", she shouted.';
var fifthString = "You\'re right, it can\'t be a quote.";   // 转义字符
var sixString = ""                                          // 空字符串，长度为0
var sevenString = "two\nlines"                              // 两行
var EgithString = "one\ long \ line"                        // 不太懂

console.log(firstString);           // ==> Hello, There.
console.log(secondString);          // ==> How're you?
console.log(thirdString);           // ==> c
console.log(fourthString);          // ==> "Wow!!!", she shouted.
console.log(fifthString);          // ==> You're right, it can't be a quote.
```

## 字符串的使用
> Unlike in languages like C, JavaScript strings are immutable. This means that once a string is created, it is not possible to modify it.However, it is still possible to create another string based on an operation on the original string.

**Javascript的内置功能之一就是字符串连接：**
-  A substring of the original by picking individual letters or using `String.substr()`.
-  A concatenation of two strings using the concatenation operator (`+`) or `String.concat()`.
-  `${myVariable}` —— for ES6, we can insert variables into strings with ease.

```javascript
let myPet = 'armadillo';
console.log('I own a pet ' + myPet + '.');  // ==>  'I own a pet armadillo.'
let myPet = 'armadillo'
console.log(`I own a pet ${myPet}.`)        // ==>  'I own a pet armadillo.'
```

```javascript
s = "hello, world";             // 定义一个字符串
s[0]                            // ==>h  字符串可当作只读数组
s[s.length-1]                   // ==>d  
s.charAt(0)                     // ==>h   第一个字符
s.charAt(s.length-1)            // ==>d   最后一个字符
s.substring(1,4)                // ==>ell 第2~4个字符
s.slice(1,4)                    // ==>ell 同上
s.slice(-3)                     // ==>rld 最后三个字符
s.indexOf("l")                  // ==>2   字符l首次出现的位置
s.lastIndexOf("l")              // ==>10  字符l最后一次出现的位置
s.indexOf("l",3)                // ==>3   在位置3及之后首次出现字符了的位置
s.split(",")                    // ==>[ 'hello', ' world' ]  分割成字串
s.replace("h", "H")             // ==>Hello, world 全文字替换
s.toUpperCase()                 // ==>HELLO, WORLD
```

---

# Number Data Type（数字）
>  According to the ECMAScript standard, all numbers are [double-precision 64-bit binary format IEEE 754-2008](https://en.wikipedia.org/wiki/Double-precision_floating-point_format), meaning there is no specific type for integers.

Javascript 不区分整数值和浮点数值，Javascript中的所有数字均用浮点数值表示。

```javascript
var x1=34.00;      //浮点型直接量，使用小数点来写
var x2=34;         //整型直接量，不使用小数点来写

//极大或极小的数字可以通过科学（指数）计数法来书写：
var y=123e5;      // 12300000
var z=123e-5;     // 0.00123
```

## Symbolic Numbers
-  无穷大 `Infinity`
-  负无穷大`-Infinity`
-  非数字值 `NaN`:  "Not-a-Number", denotes an unrepresentable value.它和任何职都不相等，包括自身。

## The *isSafeInteger* Method
A *safe integer* is an integer that:
-  Can be exactly represented as an IEEE-754 double precision number, and
-  Whose IEEE-754 representation cannot be the result of rounding any other integer to fit the IEEE-754 representation.

The `Number.isSafeInteger()` method determines whether the provided value is a number that is a safe integer.

```javascript
var var1 = 1;
var var2 = 0;
var var3 = -0;

console.log("1 / 0 = " + var1 / var2);
console.log("1 / -0 = " + var1 / var3);
console.log("MAX_VALUE: " + Number.MAX_VALUE);
console.log("MAX_VALUE + 1 = " + Number.MAX_VALUE + 1);
console.log("MIN_VALUE = " + Number.MIN_VALUE);
console.log("MIN_VALUE - 1 = " + Number.MIN_VALUE - 1);
console.log("MAX_SAFE_INTEGER = " + Number.MAX_SAFE_INTEGER);
console.log("MIN_SAFE_INTEGER = " + Number.MIN_SAFE_INTEGER);
console.log("SquareRoot(-1) = " + Math.sqrt(-1));
console.log("isSafeInteger(100) = " + Number.isSafeInteger(100));
```

```bash
1 / 0 = Infinity
1 / -0 = -Infinity
MAX_VALUE: 1.7976931348623157e+308
MAX_VALUE + 1 = 1.7976931348623157e+3081
MIN_VALUE = 5e-324
NaN
MAX_SAFE_INTEGER = 9007199254740991
MIN_SAFE_INTEGER = -9007199254740991
SquareRoot(-1) = NaN
isSafeInteger(100) = true
```

---

# Boolean Data Type（布尔值）
>  A boolean represents a logical entity and can have one of two literal values: `true`, and `false`.
> 布尔值指代真或假、开或关、是或否。这个类型只有两个值，保留字`true`和`false`。

- Javascript 程序中的比较语句的结果通常都是布尔值。
- 布尔值通常用于Javascript中的控制结构中。     
- 任意JavaScript的值都可以转换为布尔值。


```javascript
var x=true
var y=false

// false
undefined
null
0
-0
NaN
""             // 空字符串
```

---

# Symbol Data Type
> Symbols are new to JavaScript in ECMAScript Edition 6. A Symbol is a unique and immutable primitive value and may be used as the key of an Object property.

---

# Null Data Type（空值）
>  The null data type is an internal type that has only one value: `null`. This is a primitive value that represents the absence of any object value. A variable that contains null contains no valid number, string, boolean, array, or object. You can erase the contents of a variable (without deleting the variable) by assigning it the null value.

- Null是Javascript语言的关键字，它表示一个特殊值，常用来描述“空值”。
- Null是一个特殊的对象值，含义是”非对象“。
- 但通常认为null是它自有类型的唯一一个成员，它可以表示数字、字符串和对象是”无值“的。
- 可通过将变量的值设置为` null `来清空变量。
- 不包含任何属性和方法，使用`.`和`[]`来存取值得成员或方法都会产生一个类型错误。

```javascript
null.typeof()          // ==> object

cars=null;
person=null;
```
---

# Undefined Data Type（未定义）
>  The undefined value is returned when you use an object property that does not exist, or a variable that has been declared, but has never had a value assigned to it.

- Undefined 表示值的空缺。
- 不包含任何属性和方法，使用`.`和`[]`来存取值得成员或方法都会产生一个类型错误。
- 它是变量的一种取值，表明变量没有初始化，如果要查询对象属性或数组元素的值时返回`undefined`则说明这个属性火元素不存在。
- `undefined`是预定义的全局变量（不是关键字），它的值就是”未定义”。

---

# The *typeof* Operator
>  As demonstrated in some of the code examples above, we can use the `typeof` operator to determine the type associated with a variable's current value:
`typeof` 是一元运算符，放在其单个操作数的前面，操作数可以是任意类型。返回值为表示操作数类型的一个字符串。

**任意值在`typeof`运算后的返回值：**

| type         | x         | typeof x                                 |
| ------------ | --------- | ---------------------------------------- |
| undefined    | undefined | "undefined"                              |
| null         | null      | "object"                                 |
| true / false |           | "boolean"                                |
| 任意数字或NaN     | 1.5e5     | "number"                                 |
| 任意字符串        | 'hello'   | "string"                                 |
| 任意函数         |           | "function"                               |
| 任意内置对象（非函数）  |           | "object"                                 |
| 任意宿主对象       |           | 由编译器各自实现的字串符，但不是"undefined"."boolean","number","string" |



常用写法

```javascript
(typeof value == "string")? "'" + value + "'" : value
typeof(i)
```

在switch语句中非常有用。


```javascript
// Number Data Type:
var firstVar = 1.5e5;

// String Data Type:
var secondVar = 'Hello';

// Boolean Data Type:
var thirdVar = true;

// Symbol Data Type:
var fourthVar = Symbol("some Symbol variable");

// Null Object:
var fifthVar = null;

// Undefined Data Type:
var sixthVar;

// Object:
var seventhVar = {a: 1, b: 2};

// NaN (It is a Number):
var eighthVar = Math.sqrt(-1);

console.log(firstVar + " is a " + typeof firstVar);		
console.log(secondVar + " is a " + typeof secondVar);		
console.log(thirdVar + " is a " + typeof thirdVar);
console.log(fourthVar.toString() + " is a " + typeof fourthVar);		
console.log(fifthVar + " is an " + typeof fifthVar);		
console.log(sixthVar + " is an " + typeof sixthVar);		
console.log(seventhVar + " is an " + typeof seventhVar);		
console.log(eighthVar + " is a " + typeof eighthVar);		
```

```bash
150000 is a number
Hello is a string
true is a boolean
Symbol(some Symbol variable) is a symbol
null is an object
undefined is an undefined
[object Object] is an object
NaN is a number
```

---

# 类型转换
```javascript
10 + "objects"
"7" * "4"
var n = 1 - "x";
n + "objects"
```

## 转换和相等性
```javascript
null == undefined
"0" == 0
0 == false
"0" == false
```

## 显式类型转换
```javascript
Number("3")
Stiring(false)
Boolean([])
Object(3)
```

```javascript
x + ""
+x
!!x
```

```javascript
var n = 17;
binary_string = n.toString(2);
octal_string = "0" + n.toString(8);
hex_string = "Ox" + n.toString(16);
```

```javascript
var n = 123456.789;
n.toFixed(0);
n.toFixed(2);
n.toFixed(5);
n.toExponential(1);
n.toExponential(3);
n.toPrecision(4);
n.toPrecision(7);
n.toPrecision(10);
```

```javascript
parseInt("3 blind mice")
parseFloat("3.14 meters")
parseInt("-12.34")
parseInt("OxFF")
parseInt("Oxff")
parseInt("-oXFF")
parseFloat(".1")
parseInt("0.1")
parseInt(".1")
parseFloat("$72.47")
```

```javascript
parseInt("11",2);
parseInt("ff",16);
parseInt("zz",36);
parseInt("077",8);
parseInt("077",10);
```

## 对象转换为原始值
```javascript
[1,2,3].toString()
(function(x) { f(x); }).toString()
/\d+/g.toString()
new Date(2010,0,1).toString()
```
```javascript
var d = new Date(2010, 0, 1);
d.valueOf()
```

```javascript
var now = new Date();
typeof (now + 1)
typeof (now - 1)
new == now.toString()
now > (now -1)
```
---

# 数组

```javascript
//下面的代码创建名为 cars 的数组：
var cars=new Array();
cars[0]="Audi";
cars[1]="BMW";
cars[2]="Volvo";
//或者 (condensed array):
var cars=new Array("Audi","BMW","Volvo");
//或者 (literal array):
var cars=["Audi","BMW","Volvo"];
```

---

# 对象
在括号内部，**对象的属性** 以名称和值对的形式 (name : value) 来定义。属性由逗号分隔：

```javascript
//以下对象 (person) 有三个属性：firstname、lastname 以及 id。
var person={firstname:"Bill", lastname:"Gates", id:5566};

//空格和折行无关紧要。声明可横跨多行：
var person={
firstname : "Bill",
lastname  : "Gates",
id        :  5566
};

//对象属性有两种寻址方式：
name=person.lastname;
name=person["lastname"];
```


# Variables（变量）

## Dynamic Typing
> JavaScript is a loosely typed or *dynamic* language, meaning you don't need to declare a variable's type ahead of time and the language automatically determines a variable's type while the program is being processed. That also means that you can reassign a single variable to reference different types. For example:

```javascript
function print() {
    console.log(
        "someVariable(" + someVariable
        + ") is a " + typeof someVariable
    );
    // Note: 'typeof' is explained later in this tutorial.
}

// Declare someVariable and initialize it to the number '5':
var someVariable = 5;
print(someVariable);        // ==> someVariable(5) is a number

// Assign the string "Hello" to someVariable:
var someVariable = "Hello";
print(someVariable);        // ==> someVariable(Hello) is a string

// Assign the boolean value 'true' to someVariable:
var someVariable = true;
print(someVariable);        // ==> someVariable(true) is a boolean
```

## Naming
> JavaScript is a case-sensitive language, meaning that a variable name such as `myVariable` is different from the variable name `myvariable`. Variable names can be of any length, and the rules for creating legal variable names are as follows:

-  The first character must be either an ASCII letter (uppercase or lowercase) or an underscore (`_`).
-  Note that a number *cannot* be used as the first character.
-  Subsequent characters can be ASCII letters, underscores, or digits (e.g., the numbers  through ).
-  The variable name must not be a [reserved word](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).

The code below declares :
```javascript
// some valid variable names
var _daysCount
var MinimumCost
var page10
var Total_elements

//invalid variable names and will not compile
var 10Students        // ==> "SyntaxError: Unexpected number"
var First&Second      // ==> "SyntaxError: Unexpected token &"
```

## Declaration and Initialization
The first time a variable appears in your script is considered its **declaration**.
The first mention of the variable sets it up in memory, and the name allows you to refer back to it in your subsequent lines of code.
You should declare variables using the `var` keyword before using them.
If you do not initialize a variable that was declared using the `var` keyword, it automatically takes on the value `undefined`.

```javascript
// Declare firstVar:
var firstVar;

// Initialize firstVar:
firstVar = 1;

// Declare and Initialize secondVar:
var secondVar = "String";

// Declare thirdVar and fourthVar:
var thirdVar,
    fourthVar;

// Initialize thirdVar:
thirdVar = true;

// Initialize fourthVar:
fourthVar = null;

// Declare and Initialize fifthVar and sixthVar:
var fifthVar = 1.01,
    sixthVar = "Sixth";

// Declare seventhVar:
var seventhVar;

console.log(firstVar);              // ==> 1
console.log(secondVar);             // ==> String
console.log(thirdVar);              // ==> true
console.log(fourthVar);             // ==> null
console.log(fifthVar);              // ==> 1.01
console.log(sixthVar);              // ==> Sixth
console.log(seventhVar);            // ==> undefined
```

## Coercion

In JavaScript, you can perform operations on values of different types without raising an exception. The JavaScript interpreter implicitly converts, or coerces, one of the data types to that of the other, then performs the operation. The rules for coercion of string, number, or boolean values are as follows:

-  If you add a number and a string, the number is coerced to a string.
-  If you add a boolean and a string, the boolean is coerced to a string.
-  If you add a number and a boolean, the boolean is coerced to a number.

```javascript
function print(name, variable) {
    console.log(
        name + "(" + variable
        + ") is a " + typeof variable
    );
}

var someNumber = 10;
var someString = "Ten";
var someBoolean = false;

var sumOfNumberAndString = someNumber + someString;
var sumOfBooleanAndString = someBoolean + someString;
var sumOfNumberAndBoolean = someNumber + someBoolean;

print("sumOfNumberAndString", sumOfNumberAndString);
print("sumOfBooleanAndString", sumOfBooleanAndString);
print("sumOfNumberAndBoolean", sumOfNumberAndBoolean);
```

```
sumOfNumberAndString(10Ten) is a string
sumOfBooleanAndString(falseTen) is a string
sumOfNumberAndBoolean(10) is a number
```


# 声明变量类型

当您声明新变量时，可以使用关键词 "new" 来声明其类型：

```
var carname=new String;
var x=      new Number;
var y=      new Boolean;
var cars=   new Array;
var person= new Object;
```

-  JavaScript 变量均为对象。当您声明一个变量时，就创建了一个新的对象。

---

# Task——Data Types
```JavaScript
function performOperation(secondInteger, secondDecimal, secondString) {
  const firstInteger = 4;
  const firstDecimal = 4.0;
  const firstString = 'HackerRank ';

// Write code that uses console.log to print the sum of the 'firstInteger' and 'secondInteger' (converted to a Number type) on a new line.


// Write code that uses console.log to print the sum of 'firstDecimal' and 'secondDecimal' (converted to a Number type) on a new line.


// Write code that uses console.log to print the concatenation of 'firstString' and 'secondString' on a new line. The variable 'firstString' must be printed first.

function main() {
    const secondInteger = readLine();
    const secondDecimal = readLine();
    const secondString = readLine();

    performOperation(secondInteger, secondDecimal, secondString);
}
```

**Input**
```
12
4.32
is the best place to learn and practice coding!
```

**Output**
```
16
8.32
HackerRank is the best place to learn and practice coding!
```

**answer**
```javascript
function performOperation(secondInteger, secondDecimal, secondString) {
    const firstInteger = 4;
    const firstDecimal = 4.0;
    const firstString = 'HackerRank ';
    console.log(firstInteger + parseInt(secondInteger));
    console.log(firstDecimal + parseFloat(secondDecimal));
    console.log(firstString + secondString);
}
```

[Hackerrank](https://www.hackerrank.com/challenges/js10-data-types/problem)
《JavaScript权威指南》
[w3schools](http://www.w3schools.com/)
