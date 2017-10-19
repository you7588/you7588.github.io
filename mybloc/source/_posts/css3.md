---
title: css3
date: 2017-10-19 14:57:58
tags:
---
# CSS3选择器

## CSS3属性选择器

使属性选择器有了通配符的概念：

-  `[att*=val]`

-  `[att^=val]`

-  `[att$=val]`

   ```
   <head>
   <style>
       [id*=div]{
         color: lime;
       }
       /*首字符*/
       [id^=div]{
         color: red;
       }
       /*结束字符*/
       [id$=div]{
         color:blue;
       }
       /*数字的写法，但是没有任何显示*/
       [id$=/3]{
         color:yellow;
       }
     </style>
   </head>
   <body>
     <div id="mydiv1">示例文本1</div>
     <div id="div2">示例文本2</div>
     <div id="div3">示例文本3</div>
     <div id="div4">示例文本4</div>
     <div id="div">示例文本5</div>
     <div id="my">my示例文本</div>
   </body>
   ```

   ​

## CSS3结构性伪类选择器

-  伪类选择器
-  **伪元素选择器**:

```
<head>
<style>
  /*first-line*/
    p:first-line{
      color: red;
    }
    /*first-letter*/
    p:first-letter{
      color:darkblue;
    }
    /*before*/
    li:before{
      content: "--";
    }
    /*after*/
    li:after{
      content: "哈哈";
      font-size: 20px;
      color: red;
    }
  </style>
</head>
<body>
  <p>这是第一行的内容<br>这里则是第二行的内容</p>
  <ul>
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
    <li>列表4</li>
    <li>列表5</li>
    <li>列表6</li>
    <li>列表7</li>
  </ul>
</body>
```



## 选择器root、not、empty和target

结构性伪类选择器的共同特征是允许开发者根据文档中的结构来指定元素的样式。

```
<head>
<style>
    /*root*/
    :root{
      background-color: #666;
    }
    /*root 与 body的区别*/
    body{       
      background-color: #ededed;
    }
    /*not*/
    div *:not(h1){
      color: red;
    }
    /*empty*/
    :empty{
      background-color: blue;
    }
    /*target*/
    :target{
      background-color: darksalmon;
    }

  </style>

</head>
<body>
  <div>
    <h2>你好吗？</h2>
    <h1>这里是标题</h1>
    <p>这里是P标签</p>
  </div>

  <table border="1">
    <tr>
      <td>内容1</td>
      <td>内容2</td>
    </tr>
    <tr>
      <td>内容3</td>
      <td></td>
    </tr>    
    <tr>
      <td></td>
      <td>内容4</td>
    </tr>       
  </table>
  <br>
  <a href="#a1">菜单1</a>
  <a href="#a2">菜单2</a>
  <a href="#a31">菜单3</a>
  <a href="#a4">菜单4</a>

  <div id="a1">
    <h1>菜单1</h1>
    <p>菜单内容1</p>
  </div>
  <div id="a2">
    <h1>菜单2</h1>
    <p>菜单内容2</p>
  </div>
  <div id="a3">
    <h1>菜单3</h1>
    <p>菜单内容3</p>
  </div>    
```





## 选择器：first-child、last-child、nth-child和nth-last-child

特别针对一个父元素中的第一个子元素、最后一个元素、指定序号的子元素，第偶数个或奇数个子元素进行样式的指定。

```
<head>
<style>
    li:first-child{
      background-color: yellow;
    }
    li:last-child{
      background-color: blue;
    }
    /*nth-child(position)*/
    li:nth-child(3){
      background-color: grey;
    }
    li:nth-last-child(2){
      background-color: red;
    }
    li:nth-child(odd){
      background-color: pink;
    }
    li:nth-child(even){
      background-color: green;
    }
  </style>

</head>
<body>
  <h2>列表</h2>
  <ul>
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
    <li>列表4</li>
    <li>列表5</li>
    <li>列表6</li>
    <li>列表7</li>
  </ul>

</body>
```





## 选择器：nth-of-type和nth-last-of-type

-  避免这类问题的发生。
-  计算子元素是第奇数个子元素还是第偶数个子元素时，就只针对同类型的子元素进行计算

```
<head>
<style>
    /*把父元素和子元素计算在内*/
    h2:nth-child(odd){
      background-color: red;
    }
    h2:nth-last-of-type(odd){
      background-color: red;
    }
    /*只算父元素*/
    h2:nth-of-type(odd){
      background-color: red;
    }
    h2:nth-of-type(even){
      background-color: red;
    }

  </style>

</head>
<body>
  <h2>文章标题</h2>
  <p>文章正文</p>
  <h2>文章标题</h2>
  <p>文章正文</p>
  <h2>文章标题</h2>
  <p>文章正文</p>
  <h2>文章标题</h2>
  <p>文章正文</p>
  <h2>文章标题</h2>
  <p>文章正文</p>
  <h2>文章标题</h2>
  <p>文章正文</p>
</body>
```

```
    nth-child(n)
    n=αn+β
```

```
  <style>
    li:nth-child(4n+1){
      background-color: red;
    }
    li:nth-child(4n+2){
      background-color: green;
    }
    li:nth-child(4n+3){
      background-color: blue;
    }
    li:nth-child(4n){
      background-color: yellow;
    }
  </style>
</head>
<body>
  <h2>列表</h2>
  <ul>
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
    <li>列表4</li>
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
    <li>列表4</li>
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
    <li>列表4</li>
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
    <li>列表4</li>
  </ul>
</body>
```

## only-child选择器

-  可以来代替使用`nth-child`和`nth-last-child`的实现方法。

```
<head>
  <style>
    li:nth-child(1){
      background-color: red;
    }
    /*只有一个列表项的时候*/
    li:only-child{
      background-color: yellow;
    }
  </style>
</head>
<body>
  <h2>列表</h2>
  <ul>
    <li>列表1</li>
  </ul>
  <ul>
    <li>列表1</li>
  </ul>  
  <ul>
    <li>列表1</li>
    <li>列表1</li>
    <li>列表1</li>
    <li>列表1</li>
  </ul>
</body>
```





## 选择器种类
-  UI元素状态伪类选择器（17种）
   -  E:hover
   -  E:active
   -  E:focus
   -  E:disabled
   -  E:read-only
   -  E:checked
   -  E:default
   -  E:indeterminate
   -  E::selection
   -  E:invalid
   -  E:valid
   -  E:required
   -  E:optional
   -  E:in-range
-  通用兄弟元素选择器

共同特征是：指定的样式只有当元素处于某种状态下时才起作用，在默认状态下不起作用。



## hover、focus、active 和 checked

```
<head>
<style>
    input[type="text"]:hover{
      background-color: yellow;
    }
    input[type="text"]:focus{
      background-color: aqua;
    }
    input[type="text"]:active{
      background-color: red;
    }
  </style>
</head>
<body>
  <input type="text"name="name">
  <input type="text" name="age">
</body>
```

```
  <style>
    input[type="checkbox"]:checked{
      outline: 2px solid red;
    }
  </style>
</head>
<body>
  <input type="checkbox">阅读
  <input type="checkbox">旅游
  <input type="checkbox">看电影
  <input type="checkbox">上网
</body>
```



## enabled和disabled

```
<head>
  <style>
    input[type="text"]:enabled{
      background-color: yellow;
    }
    input[type="text"]:disabled{
      background-color: grey;
    }
  </style>
</head>
<body>
  <script>
    function radio_change(){
      var radio1 = document.getElementById("radio1");
      var radio2 = document.getElementById("radio2");
      var text = document.getElementById("text");
      if(radio1.checked){
        text.disabled="";
      }else{
        text.value = "";
        text.disabled = "disabled";
      }
    }
  </script>
  <input type="radio" id="radio1" name="radio" onchange="radio_change()">可用
  <input type="radio" id="radio2" name="radio" onchange="radio_change()">不可用
  <input type="text" id="text" disabled>
</body>
```



## 通用兄弟元素选择器

-  用来指定位于同一个父元素之中的某个元素之后的所有其他某个种类的兄弟元素所使用样式。

```
  <style>
    div ~ p{
      background-color: yellow;
    }
  </style>
</head>
<body>
  <div>
    <div>
      <p>P元素为div的子元素</p>
      <p>P元素为div的子元素</p>
    </div>
    <p>P元素为div的子元素</p>
    <p>P元素为div的子元素</p>
    <p>P元素为div的子元素</p>
  </div>
</body>
```



# CSS3 文字与字体相关样式

## 给文字添加阴影

`text-shadow:length length length color`

```
  <style>
    div{
      text-shadow: -5px -5px 5px red,
                   5px 5px 10px blue,
                   10px 10px 15px green;
      font-size: 40px;
      color: yellow;
      font-weight: bold;
      background-color: grey;
      height:200px;
      width:100px;
      padding: 30px 0;
      text-align: center;
    }
  </style>
</head>
<body>
  <div>
    你好
  </div>
```



## 使用服务器端字体

`word-break:normal,keep-all,break `

```
<head>
<style>
    @font-face{
      font-family: WebFont;
      /*ttf:o otf:t*/
      src: url('')format("truetype");
      font-weight: nromal;
    }
    div{
      font-family: WebFont;
    }
  </style>
</head>
<body>
  <div>
    This is my page web;
  </div>
</body>
```

```
<head>
  <style>
    @font-face{
      font-family: MyArial;
      src: local("Arial"),
            url("NotoSansCJKsc-Thin.otf");
    }
    div{
      font-family: MyArial;
    }
  </style>
</head>
<body>
  <div>
    This is my page web;
  </div>
```



## 修改字体种类而保持字体尺寸不变

`font-size-adjust:`

`x-height:58 font-size:100 px; aspect:0.58`

`c = (a/b)/s`

不成功：

```
  <style>
    #div1{
      font-family: Menlo;
      font-size: 16px;
      font-size-adjust: 0.60;
    }
    #div2{
      font-family: Cursive;
      font-size: 16px;
      font-size-adjust: 0.9;
    }
    #div3{
      font-family: "Lantinghei SC";
      font-size: 16px;
      font-size-adjust: 0.3;
    }
  </style>
</head>
<body>
  <div id="div1">Text sample</div>
  <div id="div2">Text sample</div>
  <div id="div3">Text sample</div>
</body>
```



# 盒子相关样式

## 盒子的类型

-  `block`
-  `inline-block` —— 可设置宽度
-  `inline`  —— 无法设置宽度

```
<head>
  <style>
    div{
      background-color: aqua;
      display: inline-block;
      width: 300px;
    }
    span{
      background-color: brown;
      display: inline;
      width: 300px;
    }
  </style>
</head>
<body>
  <div>div元素</div>
  <div>div元素</div>
  <br>
  <span>span元素</span>
  <span>span元素</span>
</body>
```

```
<head>
  <style>
    table{
      display: inline-table;
      border: solid 3px #00aaff;
    }
    td{
      border: solid 1px #ff00ff;
    }
  </style>
</head>
<body>
  你好上
  <table>
    <tr>
      <td>A</td><td>A</td><td>A</td><td>A</td>
    </tr>
    <tr>
      <td>A</td><td>A</td><td>A</td><td>A</td>
    </tr>
    <tr>
      <td>A</td><td>A</td><td>A</td><td>A</td>
    </tr>
    <tr>
      <td>A</td><td>A</td><td>A</td><td>A</td>
    </tr>
  </table>
  你好下
</body>
```



```
<head>
  <style>
    div{
      display: list-item;
      list-style-type: circle;
      margin-left: 30px;
    }
  </style>
</head>
<body>
  <div>示例1</div>
  <div>示例2</div>
  <div>示例3</div>
  <div>示例4</div>
</body>
```



## 对盒子中容纳不下的内容的显示

```
<head>
  <style>
    div{
      width: 300px;
      height: 150px;
      border: solid 1px orange;
      /*overflow: visible;*/
      overflow-y: hidden;
      overflow-x: scroll;
      white-space: nowrap;
    }
  </style>
</head>
<body>
  <div>
    <h1>标题文字</h1>
    <p>文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例</p>
    <p>文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例文字实例</p>
  </div>
</body>
```



## 盒子的阴影和大小计算方式

```
<head>
  <style>
    div{
      margin-left: 100px;
      margin-top: 100px;
      background-color: #ffaa00;
      box-shadow: 0px 0px 20px grey;
      width: 200px;
      height: 100px;
    }
  </style>
</head>
<body>
  <div></div>
</body>
```

```
<head>
  <style>

    #div1{
      box-sizing: border-box;
      width: 100px;
      height: 100px;
      padding: 10px;
      background-color: #00aaff;
    }

    #div2{
      box-sizing: content-box;
      width: 100px;
      height: 100px;
      padding: 10px;
      background-color: #00ffaa;
    }
  </style>
</head>
<body>
  <div id="div1"></div>
  <div id="div2"></div>
</body>
```



# 背景与边框相关样式

## 与背景相关的新增属性

```
<head>
  <style>
    div{
      background-color: black;
      border: dashed 15px green;
      padding: 30px;
      color: white;
      font-size: 30px;
      font-weight: bold;
      background-image: url("https://ws2.sinaimg.cn/large/006tNc79gy1fkjd7u3wvjj30lo0xlqax.jpg");
      background-repeat: no-repeat;
    }
    .div1{
      background-origin: border-box;
      background-clip: border-box;
    }
    .div2{
      background-origin: padding-box;
      background-clip: padding-box;
    }
    .div3{
      background-origin: content-box;
      background-clip: content-box;
    }
  </style>
</head>
<body>
  <div class="div1">示例1</div>
  <br>
  <div class="div2">示例2</div>
  <br>
  <div class="div3">示例3</div>
</body>
```



## 一个元素中显示多个背景图片

```
<head>
  <style>
    div{
      background-image: url("https://ws1.sinaimg.cn/large/006tKfTcgy1fkngt8dizwj308s05swf6.jpg"),url("https://ws2.sinaimg.cn/large/006tKfTcgy1fkngtawg3cj30cg08940j.jpg");
      background-repeat: repeat-x,no-repeat;
      background-position: 100%,100%,center,center;
      width: 1000px;
      height:800px;
    }
  </style>
</head>
<body>
  <div></div>
</body>
```



## 圆角边框

```
<head>
  <style>
  /*左上，右上、右下、左下。顺时针*/
    div{
      background-color: grey;
      border: 3px solid #000;
      width: 300px;
      height: 200px;
      padding: 20px;
      border-radius: 20px 30px 10px 50px;
    }
  </style>
</head>
<body>
  <div>
    示例文字示例文字示例文字示例文字示例文字示例文字示例文字示例文字
    示例文字示例文字
    示例文字示例文字示例文字示例文字示例文字示例文字示例文字示例文字
  示例文字示例文字示例文字示例文字示例文字示例文字示例文字示例文字
  示例文字示例文字
</div>
</body>
```



## 使用图像边框

```
<head>
  <style>
    div{
      -webkit-border-image: url("https://ws2.sinaimg.cn/large/006tKfTcgy1fknhb8z28aj306y062dgw.jpg") 50 70 50 40;
      /*background-image: url("https://ws2.sinaimg.cn/large/006tKfTcgy1fknhb8z28aj306y062dgw.jpg");*/
      width: 200px;
    }
  </style>
</head>
<body>
  <div>
    示例文字
  </div>
</body>
```

![](https://ws4.sinaimg.cn/large/006tKfTcgy1fknk57dn55j30fp0g5ae3.jpg)



# 变形处理

## transform 功能的基础知识

-  旋转
-  缩放
-  移动
-  倾斜

```
  <style>
    div{
      width: 300px;
      margin: 150px auto;
      background-color: aqua;
      text-align: center;
      transform: rotate(45deg);
      -webkit-transform:rotate(45deg);
      transform: scale(3.5);
      transform: skew(30deg,30deg);
      transform: translate(250px, 250px);
    }
  </style>
</head>
<body>
  <div>
    示例文字
  </div>
</body>
```



## 对一个元素使用多种变形的方法

-  前后顺序一定不要颠倒

```
<head>
  <style>
    div{
      width: 300px;
      margin: 150px auto;
      background-color: aqua;
      text-align: center;
      transform: translate(250px, 250px) rotate(45deg) scale(3.5);
    }
  </style>
</head>
<body>
  <div>
    示例文字
  </div>
</body>
```



## 指定变形的基准点

```
<head>
  <style>
    div{
      width: 300px;
      height: 200px;
      background-color: aqua;
    }
    .div2{
      transform-origin: top right;
      transform: rotate(45deg);
      transform: scale(1.5);
    }
  </style>
</head>
<body>
  <div class="div1">示例文字</div>
  <div class="div2">示例文字</div>
</body>
```



# 动画功能

## Transitions 功能

-  `progerty`
-  `dration`
-  `timing-function`

```
<head>
  <style>
    div{
      background-color: #ffff00;
      width: 100px;
      color: #000000;
      /*transition: background-color 5s linear;*/
      /*transition-property: background-color;
      transition-duration: 3s;
      transition-timing-function: linear;*/
      /*transition: background-color 1s linear, color 1s linear, width 1s linear;*/
      transition: transform 1s linear, color 1s linear, width 1s linear;

    }
    div:hover{
      background-color: #ff00ff;
      color: #ffffff;
      width: 200px;
      transform: rotate(360deg);
    }
  </style>
</head>
<body>
    <div>示例文字</div>
</body>
```



## Animations功能

```
<head>
  <style>
    div{
      background-color: red;
    }
    @-webkit-keyframes mycolor{
      /*开始帧*/
      0%{
        background-color: red;
      }
      /*背景颜色变化帧*/
      40%{
        background-color: #ffff00;
      }
      70%{
        background-color: aqua;
      }
      /*结束帧*/
      100%{
        background-color: red;
      }
    }
    div:hover{
      -webkit-animation: mycolor 5s linear;
    }

  </style>
</head>
<body>
    <div>示例文字</div>
</body>
```



## 实现动画的方法

-  `linear ease-in ease-out ease ease-in-out`

```
<head>
  <style>
    div{
      position: absolute;
      background-color: #ffff00;
      top: 100px;
      width: 500px;
    }
    @-webkit-keyframes mycolor{

      0%{
        background-color: red;
        transform: rotate(0deg);
      }
      30%{
        background-color: aqua;
        transform: rotate(30deg);
      }
      60%{
        background-color: lightskyblue;
        transform: rotate(-30deg);
      }
      100%{
        background-color: red;
        transform: rotate(0deg);
      }
    }
    div:hover{
      -webkit-animation-name: mycolor;
      -webkit-animation-duration: 5s;
      -webkit-animation-timing-function: linear;
    }

  </style>
</head>
<body>
    <div>示例文字</div>
</body>
```
