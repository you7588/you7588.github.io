---
title: Arithmetic Operators（算术运算符）
date: 2017-10-09 15:34:42
tags: JS
---

# Operator Types

## Unary（一元）
> A *unary* operator requires a single operand, either before or after the operator, following this format:

`a++`, `++`,`+`,`-`,`--`

```javascript
operand operator
operator operand
```
- 作用于一个单独的操作数，并产生一个新值
- 有很高的优先级，而且都是右结合（right-associative）

=

## Binary（二进制）

> A *binary* operator requires two operands, one before the operator and one after the operator, following this format:

`+`,`-`,
```
operand1 operator operand2
```

For example, in the expression `a + b = c`, `+` is a binary operator.

## Ternary（三元）

There is one *ternary* operator, the conditional operator. For example, in the expression `a ? b : c`, the use of `?` and `:` in this manner constitutes the ternary operator. We'll discuss this operator more in the *Conditional Statements* tutorial.

---

# Arithmetic Operators（算术运算符）
> An arithmetic operator takes numeric values (either literals or variables) as its operands and returns a single numeric value.

给定 `y=5`，下面的表格解释了这些算术运算符：

| 运算符  | 描述         | 例子    | 结果    |
| ---- | ---------- | ----- | ----- |
| +    | 加          | x=y+2 | x=7   |
| -    | 减          | x=y-2 | x=3   |
| *    | 乘          | x=y*2 | x=10  |
| /    | 除          | x=y/2 | x=2.5 |
| %    | 求余数 (保留整数) | x=y%2 | x=1   |
| ++   | 累加         | x=++y | x=6   |
| - -   | 递减         | x=- -y | x=4   |


- 所有无法转换为数字的操作数都转换为`NaN`值。如果操作数（或转换结果）是`NaN`值，算术运算的结果也是`NaN`。
- 运算符的行为依赖于类型转换的结果。

## 1. Addition (`+`)
> `operand1 + operand2`

```javascript
2 + 3                     // ==> 5
"hello" + " " + "there"   // ==> "hello there"
1 + 2                     // ==> 3
"1" + "2"                 // ==> 12   都是字符串
"1" + 2                   // ==> 12   优先考虑字符串连接
1 + {}                    // ==> "1[object Object]"
true + true               // ==> 2
2 + null                  // ==> 2
2 + undefined             // ==> NaN

1 + 2 + "blind mice";      // ==> "3 blind mice"
1 + (2 + "blind mice");    // ==> "12 blind mice"
```



## 用于字符串的 + 运算符

\+ 运算符用于把文本值或字符串变量加起来（连接起来）。

```javasctipt
txt1="What a very ";
txt2="nice day";
txt3=txt1+txt2;

// 或者把空格插入表达式中：
txt1="What a very";
txt2="nice day";
txt3=txt1+" "+txt2;
// ==> "What a very nice day"
```
要想在两个字符串之间增加空格，需要把空格插入一个字符串之中：

## 对字符串和数字进行加法运算：

```javasctipt
x=5+5;
document.write(x);

x="5"+"5";
document.write(x);

x=5+"5";
document.write(x);

x="5"+5;
document.write(x);
```

加号的转换规则：优先考虑字符串连接
- 若其中一个操作数是字符串或者转换为字符串的对象，另外一个操作数将会转换为字符串。
- 若两个操作数都不是类字符串，那么都将进行算术加法运算。
- 如果把数字与字符串相加，结果将成为字符串。


## 2. Subtraction (`-`)
> `operand1 - operand2`

```javascript
3 - 2 // ==> 1
4 - 10 // ==> -6
```

## 3. Multiplication (`*`)
> `operand1 * operand2`

```javascript
3 * 2 // ==> 6
4 * 10 // ==> 40
```

## 4. Division (`/`)
> `operand1 / operand2`

```javascript
6 / 3 // ==> 2
3 / 2 // ==> 1.5
4 / 10 // ==> 0.4
0 / 0  // ==> NaN
```

## 5. Remainder (`%`)
> `operand1 % operand2`

```javascript
6 % 3 // ==> 0
3 % 2 // ==> 1
4 % 10 // ==> 4
-5 % 2  // ==> -1
5 % 2  // ==> 1
6.5 % 2.1  // ==> 0.2
```

## 6. Exponentiation (`**`)
> `operand1 ** operand2`. This operator is a part of ECMAScript2016 feature set

```javascript
2 ** 3 // ==> 8
3 ** 2 // ==> 9
5 ** 4 // ==> 625
```

## 7. Unary Negation (`-`)
> `-operand`

```javascript
-4 // ==> -4
-(-5) // ==> 5 (not --5)
```

## 8. Unary Plus (`+`)
> `+operand`

```javascript
+4 // ==> 4
+(-4) // ==> -4
```

## 9. Increment 递增 (`++`)

We use this operator in the 前增量prefix and 后增量postfix forms, forms `++operand` and `operand++`.

-  `++operand`, increments the operand by  and then returns the value of the operand.
-  `operand++`, returns the value of the operand and *then* increments the operand's value by .

```javascirpt
function main(input) {
    var a = input;
    // Print the value of 'a' and the preincremented value of 'a':
    console.log("a(" + a + "), ++a(" + ++a + ")");
    // Assign the current value of 'a' to 'b' and then postincrement 'a':
    var b = a++;
    // Print the values of 'a' once and 'b' twice, then postincrement the 2nd 'b':
    console.log("a(" + a + "), b(" + b + "), b++(" + b++ + ")");
    // Print the final values of 'a' and 'b':
    console.log("a(" + a + "), b(" + b + ")");
}

// input  ==> 4
```

```javascript
a(4), ++a(5)
a(6), b(5), b++(5)
a(6), b(6)
```

## 10. Decrement 递减 (`--`)

We use this operator in the prefix and postfix forms, forms `--operand` and `operand--`.

-  `--operand`, decrements the operand by  and then returns the value of the operand.
-  `operand--`, returns the value of the operand and *then* decrements the operand's value by .

```javascript
function main(input) {
    var a = input;
    // Print the value of 'a' and the predecremented value of 'a':
    console.log("a(" + a + "), --a(" + --a + ")");
    // Assign the current value of 'a' to 'b' and then postdecrement 'a':
    var b = a--;
    // Print the values of 'a' once and 'b' twice, then postdecrement the 2nd 'b':
    console.log("a(" + a + "), b(" + b + "), b--(" + b-- + ")");
    // Print the final values of 'a' and 'b':
    console.log("a(" + a + "), b(" + b + ")");
}

// input  ==> 4
```

```javascript
a(4), --a(3)
a(2), b(3), b--(3)
a(2), b(2)
```

# Task——Area and perimeter of rectangle
```javascript
/**
*   Calculate the area of a rectangle.
*
*   length: The length of the rectangle.
*   width: The width of the rectangle.
*   
*	Return a number denoting the rectangle's area.
**/
function getArea(length, width) {
    let area;
    // Write your code here

    return area;
}

/**
*   Calculate the perimeter of a rectangle.
*
*	length: The length of the rectangle.
*   width: The width of the rectangle.
*   
*	Return a number denoting the perimeter of a rectangle.
**/
function getPerimeter(length, width) {
    let perimeter;
    // Write your code here

    return perimeter;
}

function main() {
    const length = +(readLine());
    const width = +(readLine());

    console.log(getArea(length, width));
    console.log(getPerimeter(length, width));
}
```


**Input**
```javascript
3
4.5
```

**Output**
```javascript
13.5
15
```
**answer**
```javascript

function getArea(length, width) {
    let area;
    area = length * width;
    return area;
}

function getPerimeter(length, width) {
    let perimeter;
    perimeter = (length + width) * 2;
    return perimeter;
}
```
