---
title: Variable Declaration Keywords
date: 2017-10-09 22:19:44
tags: JS
---



# var
> We use the *var* keyword to declare variables.The scope of a variable declared using this keyword is within the context wherever it was declared. It defines a variable globally or locally to an entire function regardless of block scope.

- 如果在顶层代码中使用`var`语句，它声明的是全局变量，在整个JavaScript中都是可见的。
For variables declared outside any function, this means they are globally available throughout the program.
- 如果`var`语句出现在函数体内，那么它定义的是一个局部变量，其作用域就是这个函数。
For variables declared within a function, this means they are only available within the function itself.


```javascript
function main(input) {
    var a = input;

    // If 'a' is odd:
    if (a % 2 == 1) {
        var a = input + 1;
        console.log("if(a): " + a);
    }

    console.log("main(a): " + a);
}

//input   11
//output  ==> if(a): 12  /  main(a): 12
```
1. Variable  is declared in the *main* function using the *var* keyword and initialized with the given value, `11`.
2. `a% 1` evaluates to *true* because `11` is odd, so we enter the *if* block.
3. Variable `a` is declared a second time inside the *if* block (still using the *var* keyword) and initialized with a value of ` 11 + 1 = 12`. We print the value of `a = 12`.
4. We exit the *if* block and print the value of `a` in *main*. This value is `12` because the scope of the initial declaration of  in *main* includes the *if* block.


## 使用一个变量之前应当先声明
```javascript
//声明1个变量
var i;
var sum;

//声明多个变量
var i,sum;

//将变量的初始赋值和变量声明合写在一起（即带有初始化表达式，用于指定它的初始值）
var message = "hello";
var i = 0, j = 0, k = 0;
var x = 2, y = x * x;                //第二个变量使用了第一个变量

//更多变量
var x = 2,
    f = function(x) {return x * x},
    y = f(x);                         //每个变量都独占一行

//循环变量
for(var i = 0;i < 10; i++,j--) console.log(i);

//声明后，再赋值
var i = 10;
i = "ten";
```
- 如果未在`var`声明语句中给变量指定初始值，那么虽然声明了这个变量，但在给它存入一个值之前，它的初始值就是`undefinded`。
- 若试图读取一个没有声明的变量的值，会报错。EM5规定，一个没有声明的变量赋值也会报错。
- `var`声明的变量是无法通过`delete`删除的。
- 多次声明一个变量是无所谓的。
- 变量在声明它们的脚本或函数中都是有定义的，变量声明语句会被“提前”至脚本或者函数的顶部。
---

# let
> Declare variables that are limited in scope to the block, statement, or expression in which they are used.


```javascript
function main(input) {
    let a = input;

    if (a % 2 == 1) {
        let a = input + 1;
        console.log("if(a): " + a);
    }
    console.log("main(a): " + a);
}
//input    <== 11
//output   ==>  if(a): 12  /  main(a): 11
```

## Solution
1. Variable  is declared in the *main* function using the *let* keyword and initialized with the given value, `11`.
2. `a % 1` evaluates to *true* because `a = 11` is odd, so we enter the *if* block.
3. Variable  is declared a second time inside the *if* block (again using the *let* keyword) and initialized with a value of `11 + 1 = 12`. We print the value of `a = 12`.
4. We exit the *if* block and print the value of  in *main*. Because we used the *let* keyword for both declarations and the scope of the second declaration of  was limited to the *if* block, the value of  in *main* is still `11`.

It's important to note that you cannot redeclare a variable declared using the *let* keyword within the same scope as the original variable. An attempt to do this raises an *Error*, as demonstrated by the code below.

```javascript
function main(input) {
    let a = input;

    // This will throw "SyntaxError: Identifier 'a' has already been declared"
    let a = input + 1;
    console.log(a);
}

//input   <== 11
//output  ==> SyntaxError: Identifier 'a' has already been declared
```

---

# const
> To create a *read-only* reference to a value, meaning the value referenced by this variable cannot be reassigned.
Because the value referenced by a constant variable cannot be reassigned, JavaScript *requires* that constant variables always be initialized.

```javascript
function main(input) {
    const a = input;

    // This will throw "SyntaxError: Missing initializer in const declaration"
    const b;

    console.log(a);
}

//input   <== 11
//output  ==> SyntaxError: Identifier 'a' has already been declared
```

---
# Task——变量提前声明的特点

```javascript
console.log(name);
var name = 'xiaoming';
console.log(name);
```
以上两个输出分别是什么？为什么？


```javascript
console.log(name);
let name = 'xiaoming';
console.log(name);
```
以上两个输出分别是什么？为什么？

```javascript
console.log(name);
const name = 'xiaoming';
console.log(name);
```
以上两个输出分别是什么？为什么？


```javascript
console.log(name);      //undefined;
var name = 'xiaoming';
console.log(name);      //xiaoming;


console.log(name);      //ReferenceError: name is not defined;
let name = 'xiaoming';
console.log(name);      //xiaoming (it will not console.log when run line1);


console.log(name);      //ReferenceError: name is not defined;
const name = 'xiaoming';
console.log(name);      //xiaoming (it will not console.log when run line1);
```

**解答：**
[首先，var是js的大大坑，为了填补var的坑，es6引入了let。
想要了解var，就要先掌握代码在处理过程是对变量的查找过程。

```javascript
    console.log(name);
    var name = 'xiaoming';
    console.log(name);
```
从上面的代码，很直观的看出第一行输出name时，name这个变量并没有声明。如果变量没有声明，代码肯定执行会抛出异常。但上面代码并没有抛出异常，反而输出了一个‘undefined’。这是为什么？

事实上，上面的代码等价于

```javascript
    var name;
    console.log(name);
    name = 'xiaoming';
    console.log(name);
```
通过等价代码能看出，最先声明了一个变量name，并没有赋值，没有赋值的变量默认值是'undefined'。
通过这样的等价转换是不是就明白了结果。
JS编译器在处理代码分为两个过程：编译期和执行期。
再来看源代码

```javascript
    console.log(name);
    var name = 'xiaoming';
    console.log(name);
```

重点看第一行代码，在编译期中，第一行需要输出name，name在哪里呢？后面有一个var name，所以编译会把var name提前，紧接着是执行期，name只是声明提前了，但并没有赋值，所以输出了默认的undefined。
所以，是编译器在编译期做了一些手脚，把var变量的声明提前了。
从上面这件事我们可以引申到函数表达式定义的理解。

```javascript
    fun();
    var fun = function() {
      console.log('hello, js');
    }
    fun();
```
以上代码在执行第一行fun()时会抛出一个错误。

```javascript
    TypeError: fun is not a function
        at Object.<anonymous> (/Users/youngxu/Desktop/sample.js:1:63)
        at Module._compile (module.js:569:30)
        at Object.Module._extensions..js (module.js:580:10)
        at Module.load (module.js:503:32)
        at tryModuleLoad (module.js:466:12)
        at Function.Module._load (module.js:458:3)
        at Function.Module.runMain (module.js:605:10)
        at startup (bootstrap_node.js:158:16)
        at bootstrap_node.js:575:3
```
虽然fun声明被提前了，但fun的定义并没有提前，fun只是被默认赋值了一个undefined值。这又不是一个函数，此时执行fun()时就会抛出错误，编译器很明白发生了什么。为什么？因为编译器抛出的是TypeError错误呀，好好体会一些。
事实上，js对var在编译器的处理过程会带来很多问题，最好的处理原则就是先明确声明，再明确定义。所以，js在后面引入了let，let的变量并不会提前声明，没有声明的变量会明确抛出(ReferenceError: name is not defined)。所以建议以后在写js代码时，能用let就不要用var。
至于const，const是用来定义不能修改的常量的，只能有一次赋值，不能提前声明。

---

## Task —— 计算圆的面积和周长

1. Declare a *constant variable*,`PI` , and assign it the value *Math.PI*. You will not pass this challenge unless the variable is declared as a constant and named `PI` (uppercase).
2. Read a number, `r`, denoting the radius of a circle from stdin.
3. Use `PI` and `r` to calculate the  `area` and  `perimeter`of a circle having radius`r` .
4. Print `area` as the first line of output and print `perimeter` as the second line of output.


```javascript
   function main() {
    // Write your code here. Read input using 'readLine()' and print output using 'console.log()'.

    // Print the area of the circle:

    // Print the perimeter of the circle:

   try {    
        // Attempt to redefine the value of constant variable PI
        PI = 0;
        // Attempt to print the value of PI
        console.log(PI);
    } catch(error) {
        console.error("You correctly declared 'PI' as a constant.");
    }
}
```

**Input**
```javascript
2.6
```

**Output**
```javascript
21.237166338267002
16.336281798666924
```

**answer**
```javascript
   function main() {

    const PI = Math.PI;
    let r = readLine()

    let area = PI * r * r
    console.log(area)

    let perimeter = 2* PI * r
    console.log(perimeter)
```


# 参考

[hackerrank](https://www.hackerrank.com/challenges/js10-let-and-const/problem)
