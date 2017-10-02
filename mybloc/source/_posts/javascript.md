---
title: javascript
date: 2017-09-29 12:27:37
tags:
---


# Introction to JavaScript
> **JavaScript** is a widely used web-based programming language that powers the dynamic behavior on most websites, including this one.

## Console
> a tool that developers use to record the output of their JavaScript programs.

The `console.log()` command is used to print, or log, text to the console.
```javascript
console.log("Hello!");
```

## Data Types
```javascript
console.log('New York City');
console.log(40.7);
console.log(true);
console.log(null);
```
-  **Strings** — Any grouping of keyboard characters (letters, spaces, numbers, or symbols) surrounded by single quotes (`'Hello'`) or double quotes (`"World!"`).
-  **Numbers** — Any number, including numbers with decimals: `4`, `1516`, `.002`, `23.42`.
-  **Booleans** — Either `true` or `false`, with no quotations.
-  **Null** — Can only be `null`. It represents the absence of value.
- **undefined**

## Math Operators
1. Add: `+`
2. Subtract: `-`
3. Multiply: `*`
4. Divide: `/`

## Properties
```javascript
console.log('Hello'.length);       // => 5
```

## [Built-in Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/prototype)
 > an instance + `.` + the name of the method + `()`

```javascript
console.log('Hello'.toUpperCase());                     // => 'HELLO'
console.log('Hey'.startsWith('H'));                     // => true
console.log('    Remove whitespace   '.trim());         // =>  Remove whitespace
```

-  `.toUpperCase()` — returns a string in all capital letters: `'HELLO'`.
-  `.startsWith()` — accepts the character `'H'` as an input between the opening and closing parentheses.
-  `' Remove whitespace '` — trims the whitespace at the beginning and end of a string.


## Libraries
> Call a method without an instance.
the library name + `.` +  the name of the method + `()`

 `Math` library——One such collection contains mathematical methods

```javascript
Math.floor(Math.random() * 50);
console.log(Math.ceil	Math.floor((Math.random() * 100)))
```

1. `Math.random` generates a random number between 0 and 1.
2. multiply that number by `50`, so now we have a number between 0 and 50.
3.  `Math.floor()`——Takes a decimal number, and rounds down to the nearest whole number.
4. `.ceil()`  —— returns the smallest integer greater than or equal to a decimal number.

```javascript
console.log(Number.isInteger(34.2));
```
 `isInteger()`  —— checks if a number is an integer.

## Comments

1. A *single line comment*
   ```javascript
   // The first 5 decimals of pi
   console.log('Pi is equal to ' + 3.14159);
   ```

2. A *multi-line comment*
   ```javascript
   /*
   console.log('All of this code');
   console.log('Is commented out');
   console.log('And will not be executed);
   */
   ```


## Review Types and Operators

-  4 essential data types in JavaScript include strings, numbers, booleans, and null.
-  Data is printed, or logged, to the console with `console.log()`.
-  Four built-in mathematical operators include `+`, `-`, `*`, and `/`.
-  JavaScript associates certain properties with different data types.
-  JavaScript has built-in methods for different data types.
-  Libraries are collections of methods that can be called without an instance.
-  You can write single-line comments with `//` and multi-line comments between `/*` and `*/`.


---


# Variables
> 变量是表示值得一个符号名字。

## Create a Variable: const
> In general, only use `const` if the value saved to a variable does not change in your program.

```javascript
const myName = 'Arya';
console.log(myName);                            // ==> Arya
```
1. `const`  —— constant, creates a new variable with a value that cannot change.
2. `myName` —— the variable's name. no spaces, and we capitalized the `N`. Capitalizing in this way is a standard convention in JavaScript called *camelCasing*
3. `=` —— the *assignment operator*. It assigns the value (`'Arya'`) to the variable (`myName`).
4. `'Arya'` is the *value* assigned (`=`) to the variable `myName`.


## Create a Variable: let
> `Let`  can be reassigned.

```javascript
let meal = 'Enchiladas';
console.log(meal);                              // ==> Enchiladas
meal = 'Tacos';
console.log(meal);                              // ==> Tacos
```

## Undefined
> JavaScript creates space for this variable in memory and sets it to `undefined`.

```javascript
let whatAmI;
```

## Mathematical Assignment Operators

```javascript
let x = 4;
x = x + 1;                  // ==> 5

let x = 4;
x += 2;                     // ==> 6

let y = 4;
y -= 2;                     // ==> 2

let z = 4;
z *= 2;                     // ==> 8

let r = 4;
r++;                        // ==> 5

let t = 4;
t--;                        // ==> 3
```

1. `+=`, `-=`, and `*=` perform the mathematical operation of the first operator (`+`, `-`, or `*`) using the number on the right, then assign the new value to the variable.
2. The increment (`++`) and decrement (`--`) operators are responsible for increasing and decreasing a number variable by one, respectively.


## String Interpolation
> inserting the data saved to a variable into a string

 1. `+` (the addition operator) —— is used to interpolate (insert) a string variable into a string.
 2.  `${myVariable}` —— for ES6, we can insert variables into strings with ease.


```javascript
let myPet = 'armadillo';
console.log('I own a pet ' + myPet + '.');  // ==>  'I own a pet armadillo.'

let myPet = 'armadillo'
console.log(`I own a pet ${myPet}.`)        // ==>  'I own a pet armadillo.'
```

## Review Variables

-  Variables hold reusable data in a program.
-  JavaScript will throw an error if you try to reassign `const` variables.
-  You can reassign variables that you create with the `let`keyword.
-  Unset variables store the primitive data type `undefined`.
-  Mathematical assignment operators make it easy to calculate a new value and assign it to the same variable.
-  The `+` operator is used to interpolate (combine) multiple strings.
-  In JavaScript ES6, backticks and `${}` are used to interpolate values into a string.

---

# Control Flow

## if/else Statements
> if/else statements are how programs can process yes/no questions programmatically.

```javascript
let needsCoffee = true;
if (needsCoffee === true) {
    console.log('Finding coffee');
} else {
    console.log('Keep on keeping on!');
}
```



## else if Statements
> If we have a question that has multiple yes conditions, or multiple no conditions...

```javascript
let stopLight = 'green';

if (stopLight === 'red') {
  console.log('Stop');
} else if (stopLight === 'yellow') {
  console.log('Slow down');
} else if (stopLight === 'green') {
  console.log('Go!');
} else {
  console.log('Caution, unknown!');
}
```


## True and False Values
> In JavaScript, all variables and conditions have a *truthy* or *falsy* value.

All variables that have been created and set are truthy (and will evaluate to true if they are the condition of a control flow statement) unless they contain one of the seven values listed below:
-  `false`
-  `0` and `-0`
-  `""` and `''` (empty strings)
-  `null`
-  `undefined`
-  `NaN` (Not a Number)
-  `document.all` (something you will rarely encounter)


```javascript
let variableOne = 'I Exist!';
if (variableOne) {
// This code will run because variableOne contains a truthy value.
} else {
// This code will not run because the first block ran.
}
```

In programming, we often evaluate whether or not an expression is true or truthy.

```javascript
let isRaining = true;
if (isRaining) {
   console.log('Carry an umbrella!');
} else {
  console.log('Enjoy the sun!');
}
```

 `!`  —— an operator for swapping the truthiness and falsiness of values

```javascript
let isPhoneCharged = true;
if (!isPhoneCharged) {
  console.log('Plug in your phone!');
} else {
  console.log('No need to charge!');
}
```

## Comparison Operators

-  Less than: `<`
-  Greater than: `>`
-  Less than or equal to: `<=`
-  Greater than or equal to: `>=`
-   if two things equal each other, we write `===`
-  if two things *do not* equal each other, we write `!==`

## Logical Operators

- `&&` ——both must be true
- `||`——either can be true

```javascript
if (stopLight === 'green' && pedestrians === false) {
  console.log('Go!');
} else {
  console.log('Stop');
}
```

## switch Statements
> switch statement to write more concise and readable code.

```javascript
let groceryItem = 'papaya';

switch (groceryItem) {
  case 'tomato':
    console.log('Tomatoes are $0.49');
    break;
  case 'lime':
    console.log('Limes are $1.49');
    break;
  case 'papaya':
    console.log('Papayas are $1.29');
    break;
  default:
    console.log('Invalid item');
    break;
}
```

1. The `switch` keyword initiates the statement and is followed by `( ... )`, which contains the condition that each `case` will compare to.In the example, the condition is groceryItem.
2. `case` —— is like the `else if` part of an `if`/`else if`/`else`statement.
3. `break` —— prevent the `switch` statement from executing any more of its code. Without adding `break`at the end of each case, the program will execute the code for all matching cases and the default code as well. This behavior is different from `if`/`else` conditional statements which execute only one block of code.
4. At the end of each `switch` statement, there is a `default` condition. If none of the `case`s are true, then this code will run.


## Ternary Operator

```javascript
let isNightTime = true;

if (isNightTime) {
  console.log('Turn on the lights!');
} else {
  console.log('Turn off the lights!');
}
```

```javascript
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```

1. `isNightTime ?` —This checks if `isNightTime` is truthy.
2. `console.log ('Turn on the lights!')` — this code will be executed if the condition is truthy.
3. `:` — a colon separates the two different blocks of code that can be executed.
4. `console.log('Turn off the lights!');` — this code will be executed if the condition is falsy.


## Review: Control Flow

-  `if`/`else` statements make binary decisions and execute different code based on conditions.
-  All conditions are evaluated to be truthy or falsy.
-  We can add more conditional statements to `if`/`else`statements with `else if`.
-  `switch` statements make complicated `if`/`else`statements easier to read and achieve the same result.
-  The ternary operator (`?`) and a colon (`:`) allow us to refactor simple `if`/`else` statements.
-  Comparison operators, including `<`, `>`, `<=`, and `>=`can compare two variables or values.
-  After two values are compared, the conditional statement evaluates to `true` or `false`.
-  The logical operator `&&` checks if both sides of a condition are truthy.
-  The logical operator `||` checks if either side is truthy.
-  The logical operator `!==` checks if the two sides are not equal.
-  An exclamation mark (`!`) switches the truthiness / falsiness of the value of a variable.
-  One equals symbol (`=`) is used to assign a value to a variable.
-  Three equals symbols (`===`) are used to check if two variables are equal to each other.

---

# Functions
## Functions
> A function is a block of code designed to perform a task. Any code between curly braces is also known as a *block*.
> Functions are like recipes. They accept data, perform actions on that data, and return a result.

```javascript
let calculatorIsOn = false;

const pressPowerButton = () => {
  if (calculatorIsOn) {
    console.log('Calculator turning off.');
    calculatorIsOn = false;
  } else {
    console.log('Calculator turning on.');
    calculatorIsOn = true;
  }
};

pressPowerButton();               // ==> Calculator turning on.
pressPowerButton();               // ==> Calculator turning off.
```

1. We created a function named `pressPowerButton`.
-  `const pressPowerButton` creates a variable with a given name written in *camelCase*.
-   **arrow function** syntax：The variable is then set equal `=` to a set of parentheses followed by an arrow token `() =>`, indicating the variable stores a function.
-   between the curly braces `{}` is the *function body*, or the JavaScript statements that define the function. This is followed by a semi-colon `;`.
2. Inside the function body is an `if`/`else` statement.
3.  call the function —— `pressPowerButton();`. This executes the function, running all code within the function body.

## Parameters
> Parameters are variables in a function definition that represent data we can input into the function.

```javascript
const multiplyByThirteen = (inputNumber) => {
  console.log(inputNumber * 13);
};

multiplyByThirteen(9);                    // ==> 117
```

`inputNumber` is a parameter, but when we call `multiplyByThirteen(9)`, the `9` is called an *argument*. In other words, arguments are provided when you call a function, and parameters receive arguments as their value.

```javascript
const getAverage = (numberOne, numberTwo) => {
  const average = (numberOne + numberTwo) / 2 ;
  console.log(average);
};

getAverage(365, 27);                    // ==> 196
```

## Return
> The purpose of a function is to take some input, perform some task on that input, then return a result.

```javascript
const getAverage = (numberOne, numberTwo) => {
  const average = (numberOne + numberTwo) / 2;
  return average;
}

console.log(getAverage(365, 27));         // ==> 196
```

When functions `return` their value, we can use them together and inside one another.
If our calculator needed to have a Celsius to Fahrenheit operation, we could write it with two functions like so:

```javascript
const multiplyByNineFifths = (celsius) => {
  return celsius * (9/5);
};

const getFahrenheit = (celsius) => {
  return multiplyByNineFifths(celsius) + 32;
};

console.log('The temperature is ' + getFahrenheit(15) + '°F');
// Output: The temperature is 59°F
```

Take a look at the `getFahrenheit()` function.
Inside of its block, we called `multiplyByNineFifths()` and passed it the degrees in `celsius`.
The `multiplyByNineFifths()`function multiplied the `celsius` by `(9/5)`.
Then it returned its value so the `getFahrenheit()` function could continue on to add `32` to it.
Finally, on the last line, we interpolated the function call within a `console.log()` statement.
This works because `getFahrenheit()` returns its value.

## Function Declarations
> a function that is bound to an identifier or name.
> `function` + a name + a function body

```javascript
function square (number) {
  return number * number;
}

console.log(square(5));                   // ==> 25
```
Function declarations do not end in a semi-colon.

## Function Expressions
identifier can be omitted, creating an anonymous function.
Function expressions are often stored in a variable.
You can identify a function expression by the absence of a function name immediately trailing the function keyword.

```javascript
const square = function (number) {
  return number * number;
};

console.log(square(5));                   // ==> 25
```
Note: function expressions end with a semi-colon since they are stored in a variable.


## Arrow Functions
> A shorter syntax for a function expression. You can identify arrow functions through the use of parentheses and the arrow token `() =>`.

```javascript
const square = (number) => {
  return number * number;
};

console.log(square(5));                   // ==> 25
```
We can refactor this function in three ways. The most condensed form of the function is known as **concise body**.

1. Functions that take a single parameter should not use parentheses. However, if a function takes zero or multiple parameters, parentheses are required.
2. A function composed of a sole single-line block is automatically returned.
The contents of the block should immediately follow the arrow `=>` and the `return`keyword can be removed.
This is referred to as **implicit return**
3. A function composed of a sole single-line block does not need brackets.

```javascript
const square = number => number * number;

console.log(square(5));                   // ==> 25
```

1. The parentheses around `number` have been removed, since it is a single parameter.
2. The `return` keyword has been removed since the function consists of a single-line block.
3. The `{}` have been removed, again, since the function consists of a single-line block.



## Review Functions
-  *Functions* are written to perform a task.
-  Functions take data, perform a set of tasks on the data, and then return the result.
-  We can define parameters to be used when calling the function.
-  When calling a function, we can pass in *arguments*, which will set the function's parameters.
-  We can use `return` to return the result of a function which allows us to call functions anywhere, even inside other functions.

---

# Scope
> Scope refers to where a variable can be accessed in a program.
> While some variables can be accessed from anywhere within a program, other variables may only be available in a specific context.

## Global Scope
> Variables defined in the global scope are declared outside of a set of curly braces `{}`, referred to as a *block*, and are thus available throughout a program.
> Global variables make data accessible from any place within a program.

```javascript
const color = 'blue'

const colorOfSky = () => {
  return color;                             // ==> blue
};

console.log(colorOfSky());                  // ==> blue
```
1. Here the variable `color` is declared **outside** of the function block, giving it global scope.
2. In turn, `color` can be accessed within the `colorOfSky` function.

**Note:** It's better to avoid defining variables in the global scope. Globally scoped variables can collide with variables that are more locally scoped, causing unexpected behavior in our code.

```javascript
const satellite = 'The Moon';
const galaxy = 'The Milky Way';

let stars = 'North Star';


const myNightSky = () => {
  stars = 'Sirius';
  return 'Night Sky: ' + satellite + ',' + stars + ',' + galaxy;
}

console.log(myNightSky());       // ==> Night Sky: The Moon,Sirius,The Milky Way

console.log(myNightSky(stars));  // ==> Night Sky: The Moon,Sirius,The Milky Way
```
the global variable `stars` was reassigned to `'Sirius'`.

## Block Scope
> A variable defined in the block is only accessible within the curly braces.

```javascript
const colorOfSky = () => {
  let color = 'blue';
  console.log(color);          
};

colorOfSky();                       // ==> blue
console.log(color);                 // ==> ReferenceError
```
defined within an if block:
```javascript
const colorOfSky = () => {
  const dusk = true;
  let color = 'blue';
  if (dusk) {
    let color = 'pink';
    console.log(color);
  }
  console.log(color);
};

colorOfSky();                       // ==> pink, blue
console.log(color);                 // ==> undefined
```
defined within a for loop:
```javascript
const cloudCount = () => {
  let i = 2;
  console.log(i);
  for (let i = 0; i < 10; i++) {
    console.log(i);
  }
};

cloudCount();                           // ==> 2, All numbers from 0 to 9
console.log(i);                         // ==> Reference Error
```

## Review: Scope

-  *Scope* is the idea in programming that some variables are accessible/inaccessible from other parts of the program.
-  *Global Scope* refers to variables that are accessible to every part of the program.
-  *Block Scope* refers to variables that are accessible only within the block they are defined.

---

# Arrays
> Arrays are JavaScript's way of making lists.

A foundational concept of programming is how to organize and store data.
One way we organize data in real life is to make lists.

```word
New Year's Resolutions:
1. Rappel into a cave
2. Take a falconry class
3. Learn to juggle
```

```javascript
let newYearsResolutions = ['Rappel into a cave', 'Take a falconry class', 'Learn to juggle'];
```



These lists can store any data types (including strings, numbers, and booleans) and they are ordered, meaning each item has a numbered position.



## Property Access

JavaScript starts counting from `0` rather than `1`, This is because JavaScript is **zero-indexed**.
```javascript
let newYearsResolutions = ['Rappel into a cave', 'Take a falconry class', 'Learn to juggle'];

console.log(newYearsResolutions[0]);           // ==> 'Rappel into a cave'
```

You can also access individual characters in a string.
```javascript
let hello = 'Hello World';
console.log(hello[6]);                         // ==> W
```

## Update Elements
```javascript
let seasons = ["Winter", "Spring", "Summer", "Fall"];

seasons[3] = "Autumn";
console.log(seasons)                 // ==> Winter   Spring    Summer    Autumn
```

## length property
```javascript
let newYearsResolutions = ['Rappel into a cave', 'Take a falconry class'];

console.log(newYearsResolutions.length);                // ==>  2
```

## Array Methods
> [Mozilla Developer Network (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

`.push()` —— add items to the end of an array.

```javascript
let n = ['i0', 'i1', 'i2'];
n.push('i3', 'i4');                    // ==> ['i0', 'i1', 'i2', 'i3', 'i4'];
```

 `.pop()` —— removes the last item of an array.

```javascript
let n = ['i0', 'i1', 'i2'];
n.pop();                               // ==> [ 'i0', 'i1' ]
```
`.join()` ——  joins all elements of an array (or an array-like object) into a string.
```javascript
let a = ['Wind', 'Rain', 'Fire'];
a.join();                               // ==> 'Wind,Rain,Fire'
a.join(', ');                           // ==> 'Wind, Rain, Fire'
a.join(' + ');                          // ==> 'Wind + Rain + Fire'
a.join('');                             // ==> 'WindRainFire'
```


`.slice()` —— extracts a section of a string and returns it as a new string.
```javascript
let a = ['zero', 'one', 'two', 'three'];
let sliced = a.slice(1, 3);

console.log(a);                         // ==> ['zero', 'one', 'two', 'three']
console.log(sliced);                    // ==> ['one', 'two']
```

`.splice()` —— changes the contents of an array by removing existing elements and/or adding new elements.
```javascript
let myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];

myFish.splice(2, 0, 'drum');            // insert 'drum' at 2-index position
// myFish is ["angel", "clown", "drum", "mandarin", "sturgeon"]

myFish.splice(2, 1);    // remove 1 item at 2-index position (that is, "drum")
// myFish is ["angel", "clown", "mandarin", "sturgeon"]
```


`.shift()` —— removes the first element from an array and returns that element. This method changes the length of the array.
```javascript
let a = [1, 2, 3];
let b = a.shift();

console.log(a);                             // ==> [2, 3]
console.log(b);                             // ==> 1
```


`.unshift()` ——  adds one or more elements to the beginning of an array and returns the new length of the array.
```javascript
let a = [1, 2, 3];
a.unshift(4, 5);

console.log(a);                               // ==> [4, 5, 1, 2, 3]
```

`.concat()` —— merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

```javascript

let arr1 = ['a', 'b', 'c'];
let arr2 = ['d', 'e', 'f'];

let arr3 = arr1.concat(arr2);           // ==> [ "a", "b", "c", "d", "e", "f" ]
```



## Arrays with let and const

Variables declared with `let`can be reassigned.
Variables that are assigned with `const` cannot be reassigned.
However, arrays that are declared with `const`remain *mutable*, or changeable.
This means that we can change the contents of an array, but cannot reassign the variable name to a new array or other data type.



## Review Arrays

-  Arrays are lists and are a way to store data in JavaScript.
-  Arrays are created with brackets `[]`.
-  Each item inside of an array is at a numbered position, starting at `0`.
-  We can access one item in an array using its numbered position, with syntax like: `myArray[0]`.
-  We can also change an item in an array using its numbered position, with syntax like `myArray[0] = "new string"`;
-  Arrays have a `length` property, which allows you to see how many items are in an array.
-  Arrays have their own methods, including `.push()` and `.pop()`, which add and remove items from an array, respectively.
-  Arrays have many other methods that perform different functions, such as `.slice()` and `.shift()`. You can read the documentation for any array method on the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) website.
-  Variables that contain arrays can be declared with `let`or `const`. Even when declared with `const`, arrays are still mutable; they can be changed. However, a variable declared with `const` cannot be reassigned.


---


# Loops
`for` —— let us loop a block of code a known amount of times.
`while` —— let us loop a block of code an unknown amount of times.

## for Loops

```javascript
let animals = ["Grizzly Bear", "Sloth", "Sea Lion"];

for (let animalIndex = 0; animalIndex < animals.length; animalIndex++) {
  console.log(animals[animalIndex]);
}

// => Grizzly Bear  Sloth  Sea Lion
```
We can make a for loop run forwards through an array, and make it run backward through one.

```javascript
let animals = ["Grizzly Bear", "Sloth", "Sea Lion"];

for (let animalsIndex=animals.length-1; animalsIndex >= 0;animalsIndex-- ) {
  console.log('I would love to visit ' + animals[animalsIndex]);
}

// => Sea Lion  Sloth  Grizzly Bear
```

## Nested for Loops
> run a `for` loop inside another `for` loop to compare the items in two arrays.
> Every time the outer `for` loop runs once, the inner `for`loop will run completely.

```javascript
for (let i = 0; i < myArray.length; i++) {
  for (let j = 0; j < yourArray.length; j++) {
    //Code To Run
   }
 }
```

```javascript
let myPlaces = ['Houston', 'Sioux Falls', 'Phoenix'];
let friendPlaces = ['Sioux Falls', 'Missoula', 'Buffalo'];

for (let myPlacesIndex = 0; myPlacesIndex < myPlaces.length; myPlacesIndex++) {
  for (let friendPlacesIndex = 0; friendPlacesIndex < friendPlaces.length; friendPlacesIndex++) {
		if (myPlaces[myPlacesIndex] === friendPlaces[friendPlacesIndex]) {
      console.log(friendPlaces[friendPlacesIndex]);
    }
  }
}
```

## while Loops

```javascript
while (condition) {
  // code block that loops until condition is false
}
```

1. The loop begins with the keyword `while`.
2. Inside the parentheses, we write a condition. As long as the condition evaluates to `true`, the block of code will loop.

```javascript
let cards = ['Diamond', 'Spade', 'Heart', 'Club'];

let currentCard = 'Heart';

while (currentCard !== 'Spade') {
  console.log(currentCard);
  currentCard = cards[Math.floor(Math.random() * 4)];
}

console.log('You found a spade!');
```

`currentCard = cards[Math.floor(Math.random() * 4)];`

This code will generate a random number between `0`and `3`, the range of indices of the `cards` array, and reassign `currentCard` to a new card from that array.



## Infinite Loops

Both `for` loops and `while` loops need explicit instructions on when to terminate.

Infinite loops are more common in `while` loops because they don't have an iterator built into their syntax. `while` loop, be sure to write the code that will guarantee the condition will eventually be met.

`for` loops require a start condition, a stop condition, and an iterator.

## Review: Loops

-  `for` loops allow us to repeat a block of code a known amount of times.
-  We can use a `for` loop inside another `for` loop to compare two lists.
-  `while` loops are for looping over a code block an unknown amount of times.
-  Infinite loops occur when stop conditions are never met.

---

# Iterators
> These methods are called on arrays and complete such tasks as altering each element and selecting elements that fit certain criteria.

```javascript
let artists = ['Picasso', 'Kahlo', 'Matisse', 'Utamaro'];

artists.forEach(function(artist) {
  console.log(artist + ' is one of my favorite artists.');
});

let numbers = [1, 2, 3, 4, 5];

let squareNumbers = numbers.map(function(number) {
  return number * number;
});

console.log(squareNumbers);

let things = ['desk', 'chair', 5, 'backpack', 3.14, 100];

let onlyNumbers = things.filter(function(thing) {
  return typeof thing === 'number';
});

console.log(onlyNumbers);

```



## .forEach()
> execute the same code on each element of an array.

```javascript
let groceries = ['whole wheat flour', 'brown sugar', 'salt', 'cranberries', 'walnuts'];

groceries.forEach(function(groceryItem) {
  console.log(' - ' + groceryItem);
});

> // ==> - whole wheat flour
> // ==> - brown sugar
> // ==> - salt
> // ==> - cranberries
> // ==> - walnuts
```

1. `groceries.forEach` calls the `.forEach()` method on the groceries array.
2. `(function(groceryItem) {` creates a function that takes a single parameter, `groceryItem` and opens the block of code for that function. Because `.forEach()` is an iterator method, every element in the `groceries`array will be passed to this function as an argument in place of `groceryItem`.
3. `});` closes the function code block and `.forEach()`method in that order.

```javascript
groceries.forEach(groceryItem => console.log(' - ' + groceryItem));
```
There are three important things to know about the `.forEach()` method.
1. It is an array method. It must be called upon an array.
2. Any changes to the iterated array value won't be updated in the original array.
3. The return value is `undefined`.



## .map()
> change the contents of the array

```javascript
let numbers = [1, 2, 3, 4, 5];

let bigNumbers = numbers.map(function(number) {
  return number * 10;
});
// ==> [ 10, 20, 30, 40, 50 ]
```

1. `let bigNumbers = numbers.map` creates a new array, `bigNumbers`, in which the returned values of the `.map()` method will be saved and calls the `.map()`method on the `numbers` array.
2. `(function(number) {` creates a function that takes a single parameter, `number`, and opens the block of code for that function.
3. `return number * 10;` is the code we wish to execute upon each element in the array. This will save each value from the `numbers` array, multiplied by `10`, to the `bigNumbers` array.
4. `});` closes the function code block and `.map()`method in that order.

```javascript
let numbers = [1, 2, 3, 4, 5];
let bigNumbers = numbers.map(numbers => numbers * 10);  
```

```javascript
let animals = ['Hen', 'elephant', 'llama', 'leopard', 'ostrich', 'Whale', 'octopus', 'rabbit', 'lion', 'dog'];
let secretMessage = animals.map(animal => animal.charAt(0));

console.log(secretMessage.join(''));                        // ==> HelloWorld
```

## .filter()
> returns certain elements from the original array that evaluate to truthy based on conditions written in the block of the method.

```javascript
let words = ['chair', 'music', 'pillow', 'brick', 'pen', 'door'];

let shortWords = words.filter(function(word) {
  return word.length < 6;
});
// ==> [ 'chair', 'music', 'brick', 'pen', 'door' ]
```

1. `let shortWords =` declares a new array that will contain the returned elements of the `.filter()`method.
2. `words.filter(function(word) {` calls the `.filter()` method on the `words` array and creates a function that will take a single parameter, `word`. Each element in the `words` array will be passed to this function as an argument.
3. `return word.length < 6;` is the condition to filter for all elements in the `words` array that have fewer than `6` characters will be added to the `shortWords` array.
4. `});` closes the code block and `.filter()` method in that order.

```javascript
let shortWords = words.filter(word => word.length < 6);
```

## Iterator Documentation
- [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)   
- [A list of iterator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods)

The documentation for each method contains several sections:
1. A short definition
2. A block with the correct syntax for using the method
3. A list of parameters the method accepts or requires
4. The return value of the function
5. An extended description
6. Examples of the method's use
7. Polyfill, Specifications, Browser Compatibility

``` javascript
let words = ['unique', 'uncanny', 'pique', 'oxymoron', 'guise'];

console.log(words.some(function(word) {
  return word.length < 6;                                       // ==> true
}));

let interestingWords = words.filter(word => word.length > 5);

console.log(interestingWords.every(word => word.length > 5));   // ==> true
```

## Choose the Right Iterator
```javascript
let cities = ['Nashville', 'Charlotte', 'Asheville', 'Austin', 'Boulder'];

let nums = [1, 50, 75, 200, 350, 525, 1000];

//  Choose a method that will return undefined
cities.forEach(city => console.log('Have you visited ' + city + '?'));

// Choose a method that will return a new array
let longCities = cities.filter(city => city.length > 7);

// Choose a method that will return a new array
let smallerNums = nums.map(num => num - 5);

// Choose a method that will return a boolean value
nums.some(num => num < 0);
```

## Review: Iterators

-  `.forEach()` is used to execute the same code on every element in an array but does not change the array and returns `undefined`.
-  `.map()` executes the same code on every element in an array and returns a new array with the updated elements.
-  `.filter()` checks every element in an array to see if it meets certain criteria and returns a new array with the elements that return truthy for the criteria.
-  All iterator methods can be written using arrow function syntax. In fact, given the succinctness and the implicit return of arrow function syntax, this is quickly becoming the preferred way to write these types of method calls.
-  You can visit the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) to learn more about iterator methods (and all other parts of JavaScript!).
-  Additional iterator methods such as `.some()`, `.every()`, `.reduce()`perform different functions.

---

# Objects
> JavaScript *objects* are containers that can store data and functions.
The data we store in an object is not ordered — we can only access it by calling its associated *key*.
对象是名/值对的集合，或字符串到值射映的集合。

```javascript
let restaurant = {
  name: 'Italian Bistro',
  seatingCapacity: 120,
  hasDineInSpecial: true,
  entrees: ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine Pesto']
};
```

1. `let restaurant` creates a variable named `restaurant` that stores the object.
2. We create the object between curly braces: `{}`.
3. key `:` value
4. Every key-value pair is separated by a comma `,`.

An objects keys point to values that can be any data type, including other objects.

## Accessing Object Properties
> 通过`.`或`·[]`来访问对象属性。

```javascript
let restaurant = {
  name: 'Italian Bistro',
  seatingCapacity: 120,
  hasDineInSpecial: true,
  entrees: ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine pesto']
};

console.log(restaurant.entrees);
// ==> ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine pesto']

console.log(restaurant['entrees']);

// ==> ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine pesto']
```

Bracket notation is required to use variables to look up keys within an object. It's not possible to use variables like this with dot notation.

For example, a restaurant may have different specials based on the time of day. We could put each special in the `restaurantSpecials`object, then select the one we need later in our program based on the current time.

```javascript
let meal = 'none';
let time = 12;

const restaurantSpecials = {
 breakfast: 'The breakfast special is 20% off freshly squeezed orange juice',
 lunch: 'The lunch special is 10% off appetizers',
 none: 'There are no specials currently'
};

if (time < 11) {
  meal = 'breakfast';
} else if (time < 5) {
  meal = 'lunch';
}

console.log(restaurantSpecials[meal]);
// ==> The lunch special is 10% off appetizers
```

1. The `restaurantSpecials` object has three key-value pairs for different specials throughout the day: `breakfast`, `lunch`, and `none`.
2. The `if`/`else` statement sets the `meal`variable to `'breakfast'` or `'lunch'`based on the the `time`. For purposes of this example, we can imagine the `time` variable getting updated every hour.
3. On the last line, we wrote `restaurantSpecials[meal]`. The `meal`variable is not a key in the `restaurantSpecials` object. Because we are using bracket notation, JavaScript looks at the `meal` variable's value. In this case, `meal` is set to `'lunch'` within the `if`/`else` statement because `time` is equal to `12`. Since `special` equals `'lunch'`, writing `restaurantSpecials[meal]` is the same as writing `restaurantSpecials['lunch']` — the code outputs the lunch special.



```javascript
let person = {
  name: 'kaka',
  age: 12,
  weekendAlarm: 'No alarms needed',
  weekAlarm: 'Alarm set at 7AM',
}

let day = ['Monday', 'Tuesday', 'Wednesday', 'Saturday', 'Sunday'];
let alarm;

if (day==='Sunday' || day==='Saturday') {
  alarm = 'weekendAlarm';
} else {
  alarm = 'weekAlarm';
};

console.log(person[alarm])
// ==> Alarm set at 7AM
```

## Adding a Property
> Objects are considered *mutable*, which means you can change them after they're created. Even if you save an object to a `const` variable

```javascript
const restaurant = {
  name: 'Italian Bistro',
  seatingCapacity: 120,
  hasDineInSpecial: true,
  entrees: ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine pesto']
}

restaurant['appetizers'] = ['Fried Calamari', 'Bruschetta'];
restaurant.desserts = ['Homemade Tiramisu', 'Cannoli'];
```

## Editing a Property
```javascript
restaurant['appetizers'] = ['Fried Calamari', 'Bruschetta', 'Caprese Salad'];
restaurant.desserts = ['Homemade Tiramisu', 'Canolli', 'Cheesecake'];
```

## Methods
```javascript
const restaurant = {
  name: 'Italian Bistro',
  openRestaurant: () => {
    return 'Unlock the door, flip the open sign. We are open for business!';
  },
  closeRestaurant: () => {
    return 'Lock the door, flip the open sign. We are closed.'
  }
};

console.log(restaurant.openRestaurant());
// ==> Unlock the door, flip the open sign. We are open for business!
console.log(restaurant.closeRestaurant());
// ==> Lock the door, flip the open sign. We are closed.
```

## Methods: ES6

```javascript
const restaurant = {
  name: 'Italian Bistro',
  openRestaurant() {
    return 'Unlock the door, flip the open sign. We are open for business!';
  },
  closeRestaurant() {
    return 'Lock the door, flip the open sign. We are closed.'
  }
};
```

## The this Keyword

```javascript
const restaurant = {
  name: 'Italian Bistro',
  hasDineInSpecial: true,
  openRestaurant() {
    if (hasDineInSpecial) {
      return 'Unlock the door, post the special on the board, then flip the open sign.';
    } else {
      return 'Unlock the door, then flip the open sign.';
    }
  }
};

console.log(restaurant.openRestaurant());
// ==> ReferenceError: hasDineInSpecial is not defined
```

The error above doesn't work because `hasDineInSpecial` is out of the `.openRestaurant()` method's scope.

```javascript
const restaurant = {
  name: 'Italian Bistro',
  hasDineInSpecial: true,
  openRestaurant: function() {
    if (this.hasDineInSpecial) {
      return 'Unlock the door, post the special on the board, then flip the open sign.'
    } else {
      return 'Unlock the door, then flip the open sign.'
    }
  }
}

console.log(restaurant.openRestaurant());
// ==> Unlock the door, post the special on the board, then flip the open sign.
```

`this`keyword refers to the current object, which we use to grab the value saved to `hasDineInSpecial`.

`this.hasDineInSpecial` inside the object is the same as accessing `restaurant.hasDineInSpecial` outside the object.


```javascript
let myObj = {
  name: 'Miti',
  sayHello() {
    return `${this.name} says hello!`;
  }
};
```

If we call `myObj.sayHello()`, our method will return `'Miti says hello!'`. `this` in the example above is called inside the `myObj`object, which limits the scope to the properties inside of `myObj`.

Let's change that by switching the object calling `this`:

```javascript
let yourObj = {
  name: 'Timer'
};

yourObj.sayHello = myObj.sayHello;
// Sets the sayHello method on yourObj to be the sayHello method on yourObj
```

If you call `yourObj.sayHello()`, it will return `'Timer says hello!'`. `this` in the example above is called inside the `yourObj` object, which limits the scope to the properties inside of `yourObj`.


```javascript
let person = {
  name: 'Tyron',
  age: 40,
  weekendAlarm: 'No alarms needed',
  weekAlarm: 'Alarm set to 7AM',

  sayHello: function() {
    return `Hello, my name is ${this.name}`;
  },

  sayGoodbye() {
    return 'Goodbye!';
  }
};

let friend = {
  name: 'pingki',
}

friend.sayHello = person.sayHello;
console.log(friend.sayHello())                // ==> Hello, my name is pingki
console.log(person.sayHello());               // ==> Hello, my name is Tyron

let day = 'Tuesday';
let alarm;

if (day === 'Saturday' || day === 'Sunday' ) {
  alarm = 'weekendAlarm';
} else {
  alarm = 'weekAlarm';
}

console.log(person[alarm]);                      // ==> Alarm set to 7AM
```


## Getters and Setters
> A common object design paradigm is to include getter and setter methods as attributes.

Getter and setter methods get and set the properties inside of an object. There are a couple of advantages to using these methods for getting and setting properties directly:
-  You can check if new data is valid before setting a property.
-  You can perform an action on the data while you are getting or setting a property.
-  You can control which properties can be set and retrieved.

```javascript
let restaurant = {
  name: 'Italian Bistro',
  seatingCapacity: 120,
  hasDineInSpecial: true,
  entrees: ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine Pesto']
}
```

`Available seats = Capacity - Seats Taken`

```javascript
let restaurant = {
  _name: 'Italian Bistro',
  _seatingCapacity: 120,
  _hasDineInSpecial: true,
  _entrees: ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine pesto'],

  set seatingCapacity(newCapacity) {
      if (typeof newCapacity === 'number') {
        this._seatingCapacity = newCapacity;
      console.log(`${newCapacity} is valid input.`);
    } else {
        console.log(`Change ${newCapacity} to a number.`)
    }
  }
}
```

-  Developers use an underscore before a property name to indicate a property or value should not be modified directly by other code.
-  The `set seatingCapacity()` setter method accepts `newCapacity` as a variable. The `newCapacity` variable holds the new value that we will store in `_seatingCapacity`.
-  Inside of the `.seatingCapacity()` setter we use a conditional statement to check if the `newCapacity` variable (our new value) is a number.
-  If the input value is a number (valid input), then we use `this._seatingCapacity` to change the value assigned to `_seatingCapacity`. If it is not valid, then we output a message to the user.


**How to use?**
Now that you know how to create a setter method, you may be wondering how we use it.

```javascript
restaurant.seatingCapacity = 150;           // ==> 150 is valid input.
```
We set the `_seatingCapacity` value to `150`. We use the same syntax we would use to set a property that doesn't have a setter method. Since the input (`150`) is a number, our method will execute the first block in the conditional statement — it changes `_seatingCapacity` to `150` and logs `150 is a valid input.` to the console.


**A way to access them:**
Once you've set the properties, you need a way to access them. Getters are used to get the property values inside of an object. Like setters, getters are preferred to setters because you can do additional processing inside the method.

```javascript
let restaurant = {
  _name: 'Italian Bistro',
  _seatingCapacity: 120,
  _hasDineInSpecial: true,
  _entrees: ['Penne alla Bolognese', 'Chicken Cacciatore', 'Linguine pesto'],

  set seatingCapacity(seatingCapacity) {
      if (typeOf newCapacity === 'number') {
        this._seatingCapacity = newCapacity;
    } else {
        console.log(`Change ${newCapacity} to a number.`)
    }
  },

  get seatingCapacity() {
      console.log(`There are ${this._seatingCapacity} seats at Italian Bistro.`);
      return this._seatingCapacity;
  }
}
```

In the example above, the getter method (`get seatingCapacity()`) logs something to the console and returns the value saved to `_seatingCapacity`. We call the getter method the same way we would access a property without a method:

```javascript
restaurant.seatingCapacity = 150;
const seats = restaurant.seatingCapacity;
```

In this example we set the `seatingCapacity`to `150`, then call the getter method using `restaurant.seatingCapacity` and save the result to a variable called `seats`. The getter will also log the following line of code to the console:

```javascript
There are 150 seats at Italian Bistro.
```

```javascript
let person = {
  _name: 'Lu Xun',
  _age: 137,

  set age(ageIn) {
    if (typeof ageIn === 'number') {
      this._age = ageIn;
    }
    else {
      console.log('Invalid input');
      return 'Invalid input';                   
    }
  },

  get age() {
    console.log(`${this._name} is ${this._age} years old.`);
    return this._age;
  }

};

person.age = 'Thirty-nine';                // ==> Invalid input
person.age = 39;                           // ==> Lu Xun is 39 years old.

console.log(person.age);                   // ==> 39
```

## Review:Objects
-  Objects store key-value pairs and let us represent real-world things in JavaScript.
-  Properties in objects are separated by commas. Key-value pairs are always separated by a colon.
-  You can add or edit a property within an object with dot notation.
-  A method is a function in an object.
-  `this` helps us with scope inside of object methods. `this` is a dynamic variable that can change depending on the object that is calling the method.
-  Getter and setter methods allow you to process data before accessing or setting property values.

---

# Classes
> A tool that developers use to quickly produce similar objects.
> A great way to reduce duplicate code and debugging time.

```javascript
let halley = {
  _name: 'Halley',
  _behavior: 0,

  get name() {
    return this._name;
  },

  get behavior() {
    return this._behavior;
  },

  incrementBehavior() {
    this._behavior++;
  }
}
```
Now, imagine you own a dog daycare and want to create a catalog of all the dogs who belong to the daycare. Instead of using the syntax above for every dog that joins the daycare, we can create a Dog class that serves as a template for creating new Dog objects. For each new dog, you can provide a value for their name.

**Created a class called Dog, and used it to produce a Dog object:**
```javascript
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }
  get behavior() {
    return this._behavior;
  }   

  incrementBehavior() {
    this._behavior ++;
  }
}

const halley = new Dog('Halley');
console.log(halley.name);                           // ==> Halley
console.log(halley.behavior);                       // ==> 0

halley.incrementBehavior();
console.log(halley.name);                           // ==> Halley
console.log(halley.behavior);                       // ==> 1
```

## Constructor
> `constructor()` method —— every time it creates a new instance of a class.
> Although you may see similarities between class and object syntax, there is the important method that sets them apart.

```javascript
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  }
}
```
-  `Dog` —— the name of our class. By convention, we capitalize and CamelCase class names.
-  `constructor()` —— creates a new **instance** of a class.
-  This `constructor()` method accepts one argument, `name`.
-  Inside of the `constructor()` method, we use the `this` keyword. In the context of a class, `this` refers to an instance of that class. In the `Dog` class, we use `this`to set the value of the Dog instance's `name` property to the `name` argument.
-  `behavior` ——keep track of the number of times a dog misbehaves. initialized to zero.

## Instance
> An object that contains the property names and methods of a class, but with unique property values.

```javascript
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  }
}

const halley = new Dog('Halley');
console.log(halley.name);                          // ==>  Output: 'Halley'
```

-   `new`  —— generate a new instance of the `Dog` class. The `new`keyword calls the `constructor()`, runs the code inside of it, and then returns the new instance.
-  We pass the `'Halley'` string to the Dog constructor, which sets the `name` property to `'Halley'`.
-  we log the value saved to the `name` key in our `halley` object, which logs `'Halley'` to the console.

## Methods
Class method and getter syntax is the same as it is for objects **except you can not include commas between methods**.


**Add getter methods for name and behavior:**

```javascript
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}
```
- `_name `and `_behavior` —— indicate these properties should not be accessed directly.
- ` .incrementBehavior()` —— When you call .incrementBehavior() on a Dog instance, it adds 1 to it.
**Note:** Between each of our methods, we did *not* include commas.

## Method Calls
**Use our new methods to access and manipulate data from Dog instances:**

```javascript
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }   

  incrementBehavior() {
    this._behavior++;
  }
}

const halley = new Dog('Halley');

let nikko = new Dog('Nikko');              // Create dog named Nikko
nikko.incrementBehavior();                 // Add 1 to nikko instance's behavior
let bradford = new Dog('Bradford');        // Create dog name Bradford
console.log(nikko.behavior);               // ==> 1
console.log(bradford.behavior);            // ==> 0
```

## Inheritance

![](https://ws3.sinaimg.cn/large/006tNc79gy1fk45z8cd6vj310j0t5tba.jpg)


Imagine our doggy daycare is so successful that we decide to expand the business and open a kitty daycare. Before the daycare opens, we need to create a `Cat` class so we can quickly generate `Cat` instances. We know that the properties in our `Cat` class (`name`, `behavior`) are similar to the properties in our `Dog` class, though, there will be some differences, because of course, cats are not dogs.

Let's say that our `Cat` class looks like this:

```javascript
class Cat {
  constructor(name, usesLitter) {
    this._name = name;
    this._usesLitter = usesLitter;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get usesLitter() {
    return this._usesLitter;
  }

  get behavior() {
    return this._behavior;
  }  

  incrementBehavior() {
    this._behavior++;
  }
}
```

In the example above, we create a `Cat` class. It shares a couple of properties (`_name` and `_behavior`) and a method (`.incrementBehavior()`) with the `Dog`class from earlier exercises. The `Cat` class also contains one additional property (`_usesLitter`), that holds a boolean value to indicate whether a cat can use their litter box.

When multiple classes share properties or methods, they become candidates for *inheritance* — a tool developers use to decrease the amount of code they need to write.

With inheritance, you can create a *parent* class (also known as a superclass) with properties and methods that multiple *child* classes (also known as subclasses) share. The child classes inherit the properties and methods from their parent class.

Let's abstract the shared properties and methods from our `Cat` and `Dog` classes into a parent class called `Animal`.

```javascript
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }   

  incrementBehavior() {
    this._behavior++;
  }
}
```

In the example above, the `Animal` class contains the properties and methods that the `Cat` and `Dog` classes share (`name`, `behavior`, `.incrementBehavior()`).

The diagram to the right shows the relationships we want to create between the Animal, Cat, and Dog classes.
