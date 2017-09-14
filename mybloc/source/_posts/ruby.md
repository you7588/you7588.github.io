---
title: ruby
date: 2017-09-13 11:53:00
categories: Ruby
tags: [ruby, 常用]

---


## Ruby

Ruby 是用于快捷易用物件导向程式设计的直译式脚本语言

*直译式脚本语言(interpreted scripting language)：*

-  能够直接产生作业系统呼叫
-  强大的字串处理(string operations) 及正规表示式(regular expressions)
-  在开发时提供即时回馈

*快捷易用：*

-  不需要变数宣告(variable declarations)
-  变数不需要型别(typed)
-  语法简单一致
-  自动管理记忆体

*物件导向程式设计：*

-  任何东西都是物件
-  类别、方法、继承等
-  单件方法(singleton methods)
-  模组提供「混入」(mixin) 功能
-  迭代器(iterators) 及闭包(closures)

*以及：*

-  多精确度整数(multiple precision integers)
-  方便的例外处理(exception processing)
-  动态载入(dynamic loading)
-  执行绪支援(threading support)


## 程式语言分类
**Ruby是个动态强分型的直译式程式语言。**

**根据需不需要事先宣告变数型别：**

-  静态分型(Static typing when possible)：Java、C、C++

  >  编译期间做检查数据类型的语言，即写程序时要声明所有变量的数据类型，是固定的。使用数据之前，必须先声明数据类型（int ,float,double等）。相当于使用之前，首先要为它们分配好内存空间。

    优点：结构非常规范，便于调试，方便类型安全
    缺点：为此需要写更多类型相关代码，不便于阅读、不清晰明了


-  动态分型(Dynamic typing when needed)：Ruby、Perl、Python和PHP

    >  运行期间才做数据类型检查的语言，即动态类型语言编程时，永远不用给任何变量指定数据类型。该语言会在第一次赋值给变量时，在内部将数据类型记录下来。

      优点：方便阅读，不需要写非常多的类型相关的代码；
      缺点：不方便调试，命名不规范时会造成读不懂，不利于理解等

**根据会不会隐性自动转换型别：**

-  强分型(Strong typing)：Ruby、Perl、Python、Java

    >  一旦变量被指定某个数据类型，如果不经强制转换，即永远是此数据类型。

    优点：强类型定义语言带来的严谨性能够有效的避免许多错误。

-  弱分型(Weak typing)：PHP、C、C++

    >  数据类型可以被忽略的语言。它与强类型定义语言相反, 一个变量可以赋不同数据类型的值。

    优点：在速度上可能较快于强类型定义语言

**通常动态分型的程式语言多半也是**

- 直译式(interpreted)程式语言:不需要事先编译，透过直译器(interpreter)执行即可
- 解释型语言（英语：Interpreted language），又称解释型语言，是一种编程语言。这种类型的编程语言，会将代码一句一句直接运行，不需要像编译语言（Compiled language）一样，经过编译器先行编译为机器码，之后再运行。这种编程语言需要利用解释器，在运行期，动态将代码逐句解释（interpret）为机器码，或是已经预先编译为机器码的的子程序，之后再运行。
- 理论上，任何编程语言都可以是编译式，或解释型的。它们之间的区别，仅与程序的应用有关。许多编程语言同时采用编译器与解释器来实现，其中包括Lisp，Pascal，C，BASIC 与 Python。JAVA及C#采用混合方式，先将代码编译为bytecode，在运行时再进行解释。
- 编译式(compiled)程式语言:事先编译成执行档才行执行。是一种以编译器来实现的编程语言。它不像直译语言一样，由解释器将代码一句一句运行，而是以编译器，先将代码编译为机器码，再加以运行。理论上，任何编程语言都可以是编译式，或直译式的。它们之间的区别，仅与程序的应用有关。
- 一般而言，用编译语言写成的程序，在运行期的运行速度，通常比用直译语言写的程序快。因为程序在编译期，已经被预先编译成机器码，可以直接运行，不用像直译语言一样，还要多一道直译程序。

但是要先进行编译，之后才能运行程序，这也造成了编译语言的缺点。一般而言，编译语言的程序开发速度，以及除错时间，都是比较长的。因为它不像直译语言可以写完一行，或一小段程序之后，马上运行，马上除错。直译语言通常让程序开发的整体时间变少，在开发过程中，程序师也可以更弹性、快速的测试自己的想法。

为了改善直译语言的效率而发展出的即时编译技术，已经缩小了这两种语言间的差距。这种技术混合了编译语言与直译语言的优点，它像编译语言一样，先把程序源代码编译成字节码。到运行期时，再将字节码直译，之后运行。Java与LLVM是这种技术的代表产物。

优点：在运行期的运行速度，通常比用直译语言写的程序快。

```
/* PHP */会隐形地自动转型
$i = 1;
echo "Value is " . $i ;
# Value is 1                      

/* C */会隐形地自动转型
int a = 5;
float b = a;

# Ruby 会检查型别不相配而发生错误
i = 1
puts "Value is " + i

# TypeError: can't convert Fixnum into String
#   from (irb):2:in `+'
#   from (irb):2
```









## 参考

+ [ihower](https://ihower.tw/rails/ruby.html)
+ [弱类型、强类型、动态类型、静态类型语言的区别是什么？](https://www.zhihu.com/question/19918532)
+ Ruby中文官方網站：[Ruby簡介](http://www.ruby-lang.org/zh_TW/about/)  / [二十分鐘Ruby體驗](http://www.ruby-lang.org/zh_TW/documentation/quickstart/)  /  [從其他程式語言到Ruby](http://www.ruby-lang.org/zh_TW/documentation/ruby-from-other-languages/)
+ [Ruby使用手冊](http://guides.ruby.tw/ruby/)

免费的英语资源教学网站：
+ [CodeCademy](https://www.codecademy.com/learn/learn-ruby) 从做中学习线上的互动教学
+ [Learn Ruby the Hard Way](http://ruby.learncodethehardway.org/book/) 以习题为主的教材
+ LaunchSchool 除了入门的内容，还包括完整练习题和解答：
  - [Introduction to Programming with Ruby by Tealeaf Academy](https://launchschool.com/books/ruby/)
  - [Object Oriented Programming with Ruby](https://launchschool.com/books/oo_ruby)
