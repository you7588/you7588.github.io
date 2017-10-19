---
title: Functions in JavaScript（函数）
date: 2017-10-09 21:36:11
tags: JS
---


# Functions（函数）

关键字`function`用来定义函数。
A function declaration creates a function that's a *Function* object having all the properties, methods, and behaviors of Function objects.

By default, functions return the value `undefined`; to return any other value, the function must have a return statement that consists of the `return` keyword followed by the value to be returned (this can be a literal value, a variable, or even a call to a function).


```javascript
// The first line contains a string denoting .
function greetings(name) {
    console.log("Hello, " + name);
}

// The second line contains two space-separated integers,  and , to be summed.
function sum(a, b) {
    return a + b;
}

function main(name, a, b) {
    greetings(name);
    console.log(sum(a, b));
}

//input  <== Julia
//input  <== 8 2
//output ==> Hello, Julia
//output ==> 10
```

# The Function Expression （函数表达式）
A function expression is very similar to (and has almost the same syntax as) a function statement.
The main difference between a **function expression** and a **function statement** is the function **name**, which can be omitted from a function expression to create an [anonymous function](https://en.wikipedia.org/wiki/Anonymous_function). Function expressions are often used as [Immediately Invoked Function Expressions](https://en.wikipedia.org/wiki/Immediately-invoked_function_expression) (IIFEs), which run as soon as they're defined.

## Unnamed Function Expression （未命名的函数表达式）
A single integer denoting .

```javascript
function main(input) {
    var square = function(x) {
        return x * x;
    };

    console.log(square(input));
}

//input    <== 4
//output   ==> 16
```

## Named Function Expression （命名函数表达式）
Two space-separated integers describing the respective values of  and .
```javascript
function main(factN, fibN) {
    var math = {
        factorial:
            function factorial(n) {
                if (n > 1) {
                    return n * factorial(n - 1);
                }
                return 1;
            }
    };

    var fib = function fibonacci(n){
        if (n > 2) {
            return fibonacci(n - 1) + fibonacci(n - 2);
        }
        else if (n < 1) {
            return 0;
        }
        return 1;
    }

    console.log(math.factorial(factN));
    console.log(fib(fibN));

}
//input    <== 5     11
//output   ==> 120   89
```

# Recursion（递归）

This is an extremely important algorithmic concept that involves splitting a problem into two parts: a *base case*and a *recursive case*. The problem is divided into smaller subproblems which are then solved recursively until such time as they are small enough and meet some base case; once the base case is met, the solutions for each subproblem are combined and their result is the answer to the entire problem.

If the base case is not met, the function's recursive case calls the function again with modified values. The code must be structured in such a way that the base case is reachable after some number of iterations, meaning that each subsequent modified value should bring you closer and closer to the base case; otherwise, you'll be stuck in the dreaded [infinite loop](https://en.wikipedia.org/wiki/Infinite_loop)!

It's important to note that any task that can be accomplished recursively can also be performed [iteratively](https://en.wikipedia.org/wiki/Iteration#Computing) (i.e., through a sequence of repeatable steps). Recursive solutions tend to be easier to read and understand than iterative ones, but there are often performance drawbacks associated with recursive solutions that you're going to want to evaluate on a case-by-case basis. Typically, we use recursion when each recursive call significantly reduces the size of the problem (e.g., if we can halve the dataset during each recursive call). Regardless of the advisability of recursively solving a problem, it's extremely important to practice and understand *how* to recursively solve problems.

## Example (Java)

**Input Format**
Two space-separated integers to be multiplied.


```javascript
import java.util.*;

class Solution {
    // Multiply 'n' by 'k' using addition:
    private static int nTimesK(int n, int k) {
        // Print current value of n
        System.out.println("n: " + n);

        // Recursive Case
        if(n > 1) {
            return k + nTimesK(n - 1, k);
        }
        // Base Case n = 1
        else {
            return k;
        }
    }
    public static void main(String[] args) {
    	Scanner scanner = new Scanner(System.in);
        int result = nTimesK(scanner.nextInt(), scanner.nextInt());
        scanner.close();
        System.out.println("Result: " + result);
    }
}
```

```
// <== 4 4
// ==>
n: 4
n: 3
n: 2
n: 1
Result: 16
```



The diagram below depicts the execution of the code above using the default input (`4 4`). Each call to *nTimesK* is represented by a bubble, and each new recursive call bubble is stacked inside and on top of the bubble that was responsible for calling it. The function recursively calls itself using reduced values until it reaches the base case (). Once it reaches the base case, it passes back the base case's return value () to the bubble that called it and continues passing back `k +` the previously returned value until the final result (i.e.: the multiplication by addition result of ) is returned.

![Recursion 2.png](https://s3.amazonaws.com/hr-challenge-images/17162/1456174849-459a4048f8-Recursion2.png)

Once the code hits the base case in the  bubble, it returns  (which is ) to the  bubble.
Then the  bubble returns , which is , to the  bubble.
Then the  bubble returns , which is , to the  bubble.
Then the  bubble returns , which is , to the first line in *main* as the result for , which assigns  to the  variable.
