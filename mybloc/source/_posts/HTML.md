---
title: HTML5
date: 2017-10-19 14:57:25
tags:
---

# HTML5与HTML4的区别
## 推出的理由及目标
过去存在的问题：
-  web浏览器之间的兼容性很低
-  文档结构不够明确，如`<div></div>`
-  web应用程序的功能受到了限制

世界知名浏览器厂商对HTML5的支持：微软、Google、苹果、Opera、Mozilla

## 语法的改变
-  内容类型`text.html`
-  DOCTYPE声明

```html
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>

</body>
</html>
```

-  指定字符编码
-
```html
<meta charset="UTF-8">
```

-  可以省略标记的元素


-  具有boolean值的属性

```html
#true
<input type="checkbox" checked>
<input type="checkbox" checked="checked">
<input type="checkbox" checked="">
#false
<input type="checkbox">
```

-  省略引号

```html
<input type="checkbox" checked=checked>
```



## 新增的元素

### 新增的结构元素
- section 内容块
- article 独立内容
- aside 辅助信息
- header	标题
- hgroup 内容块
- footer 底部
- nav 导航
- figure 独立的单元

### 新增的其他元素
- video 视频
- audio 音频
- canvas 图形、画布
![](https://ws1.sinaimg.cn/large/006tNc79gy1fkl9klyw84j30xy0diady.jpg)


## 废除的元素
-  能使用CSS替代的元素：basefont、big、center、font、s、tt、u
-  不再使用frame框架
-  只有部分浏览器支持的元素
-  其他被废除的元素

## 新增的属性
-  表单相关
-  链接相关
-  其他

## 废除的属性


## 全局属性
-  contenEditable (true/false)

```
<h2>可编辑列表</h2>
<ul contenteditable>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>
```

-  designMode——只能在js脚本里被编辑
-  hidden (true/false)——所有都可应用
-  spellcheck——语法检查

```
<input type="text" spellcheck="">
```
-  tabindex——tab顺序

```
<a href="#" tabindex="1">hello1</a>
<a href="#" tabindex="3">hello3</a>
<a href="#" tabindex="2">hello2</a>
<ul tabindex="-1">
  <li>1</li>
  <li>1</li>
  <li>1</li>
  <li>1</li>
</ul>
```

# HTML5新增的主体结构元素

## article元素

代表文档、页面或应用程序中独立的、完整的、可以独自被外部引用的内容。它可以是一篇博客或者报刊中的文章，一篇论坛帖子、一段用户评论或独立的插件，或其他人和独立的内容。

-  可以嵌套使用
-  可以用来表示插件

```html
  <article>
    <header>
      <h1>极客学院</h1>
      <p>Hello,欢迎来到极客学院</p>
    </header>
    <article>
      <header>
        作者
      </header>
      <p>评论</p>
      <footer>
        <p>time</p>
      </footer>
    </article>
    <p>Hello</p>
    <footer>
      <p>这是底部</p>
    </footer>
  </article>
  <article>
    <h1>这是一个内嵌页面</h1>
    <object type="">
      <embed src="#" width="600" height="400"type="">
    </object>
  </article>
```

**note: 强调独立性**

## section元素

-  用于对网站或应用程序中页面上的内容进行分块。
-  一个section元素通常由内容及其标题组成。
-  但section元素并非一个普通的容器元素；
-  当一个容器需要被直接定义样式或通过脚本定义行为时，推荐使用div而非section元素。
-  如果aside、nav、article元素更符合使用条件，不要使用section
-  不要为没有标题的区域块使用section元素

**note: 强调分段或分块**

```
  <section>
    <h1>苹果</h1>
    <p>这是一个水果，可以吃，而且很好吃。</p>
  </section>
  <article>
    <h1>苹果</h1>
    <p>这是一个水果，可以吃，而且很好吃。</p>
    <section>
      <h2>红富士</h2>
      <p>这是一种外表很红的苹果，吃起来也不错。</p>
    </section>
    <section>
      <h2>国光</h2>
      <p>这是一种外表很红的苹果，吃起来也不错。</p>
    </section>
  </article>

  <section>
    <h1>水果</h1>
    <article>
      <h2>苹果</h2>
      <p>内容</p>
    </article>
    <article>
      <h2>苹果</h2>
      <p>内容</p>
    </article>
    <article>
      <h2>苹果</h2>
      <p>内容</p>
    </article>        
  </section>
```



## nav元素

-  一个可以用作页面导航的链接组，其中的导航元素连接到其他页面或当前页面的其他部分。
-  并不是所有的链接族都要被放进nav元素，只需要将主要的、基本的链接组放进nav元素即可。
-  nav元素应用场景：
   -  传统导航条
   -  侧边栏导航
   -  页内导航
   -  翻页操作

note:不要用menu元素代替nav元素，menu元素是交互性元素。

```
  <nav>
    <ul>
      <li><a href="#">主页</a></li>
      <li><a href="#">开发文档</a></li>
    </ul>
  </nav>
  <article>
    <header>
      <h1>HTML5</h1>
      <nav>
        <ul>
          <li><a href="#">HTML5</a></li>
          <li><a href="#">CSS3</a></li>
        </ul>
      </nav>
    </header>
    <section>
      <h1>HTML5</h1>
      <p>。。。</p>
    </section>
    <section>
      <h1>CSS3</h1>
      <p>。。。</p>
    </section>
    <footer>
      <a href="#">删除</a>
      <a href="#">修改</a>
    </footer>
  </article>
  <footer>
    <p><small>版权声明：</small></p>
  </footer>
```



## aside元素

-  表示当前页面或文章的附属信息部分
-  它可以包含与当前页面或主要内容相关的引用、侧边栏、广告、导航条，以及其他类似的有区别于主要内容的部分

```
  <header>
    <h1>JS入门</h1>
  </header>
  <article>
    <h1>语法</h1>
    <p>文章的正文。。。</p>
  </article>
  <aside>
    <h1>名词解释</h1>
    <p>语法：这是一个对语言来说很重要的内容体。</p>
  </aside>

  <aside>
    <nav>
      <h2>
        <ul>
          <li><a href="#">2015-3-10</a></li>
          <li><a href="#">
            大牛：真希望能好好的学一下
          </a></li>
        </ul>
      </h2>
    </nav>
  </aside>
```

## time元素和微格式

```
  <time datetime="2013-13-13">2013-13-13</time>
  <time datetime="2013-13-13T20:00">2013-13-13</time>
  <time datetime="2013-13-13T20:00Z">2013-13-13</time>
  <time datetime="2013-13-13T20:00+09:00">2013-13-13</time>
```

## pubdate属性

```
  <article>
    <header>
      <h1>苹果</h1>
      <p>发布日期<time datetime="2015-10-10" pubdate>1015-10-10</time></p>
      <p>舞会时间<time datetime="2015-10-12">2015-10-12</time></p>
    </header>
  </article>
```



# HTML5的非主体构元素

## header元素

-  一种具有引导和导航作用的结构元素
-  通常用来放置整个页面或页面内的一个内容区块的标题，但是也可以包含其他内容，例如数据表格、搜索表单或相关的logo图片。
-  可以出现多次

```
  <header>
    <h1>IT最新技术</h1>
    <a href="http://www.baidu.com">百度</a>
    <nav>
      <ul>
        <li><a href="#">学习</a></li>
        <li><a href="#">技术</a></li>
        <li><a href="#">极客</a></li>
      </ul>
    </nav>
  </header>
```

## footer元素

-  可作为其上层父级内容区块或是一个根区块的脚注。
-  通常包括其相关区块的脚注信息，如作者、相关阅读链接及版权信息等

```
  <!-- <div class="footer"> -->
  <footer>
    <ul>
      <li><a href="#">版权信息</a></li>
      <li><a href="#">版权信息</a></li>
      <li><a href="#">版权信息</a></li>
    </ul>
  </footer>
  <!-- </div> -->

  <article>
    <footer>
      这是一个文章的底部.
    </footer>
  </article>

  <section>
    <footer>

    </footer>
  </section>
```



## hgroup元素

-  将标题及其子标题进行分组的元素
-  通常会将h1~h6元素进行分组，譬如一个内容区块的标题及其子元素算一组。

```
  <article>
    <header>
      <hgroup>
      <h1>这是文章标题</h1>
      <h2>这是一个子标题</h2>
      </hgroup>
      <p><time datetime="2015-10-10">2015-10-10</time></p>
    </header>
    <div>
      这是内容
    </div>
    <footer>
      这是底部
    </footer>
  </article>
```

## address元素

-  用来在文档中呈现联系信息，包括文档作者或文档维护者的名字、他们的网站链接、电子邮箱、真实地址、电话号码等。
-  还用来展现根文档相关的联系人的所有联系信息。

```
  <address>
    <a href="#">Mary</a>
    <a href="#">Kay</a>
  </address>
  <footer>
    <div>
      <address>
        <a href="#">Kathy</a>
        Halo,world
      </address>
      <time datetime="2015-10-10">2015-10-10</time>
    </div>
  </footer>
```



## 网页编排规则

-  显示编排内容区域块
-  根据需求
-  标题分级
-  不同区域块可以写相同的标签

```
  <header>
    <h1>网页标题</h1>
    <nav>
      <ul>
        <li><a href="#">首页</a></li>
        <li><a href="#">帮助</a></li>
      </ul>
    </nav>
  </header>
  <article>
    <hgroup>
      <h1>文章主标题</h1>
      <h2>文章子标题</h2>
    </hgroup>
    <p>文章正文</p>
    <section>
      <div>
        <article>
          <h1>评论标题</h1>
          <p>评论正文</p>
        </article>
      </div>
    </section>
  </article>

  <footer>
    版权所有。。。
  </footer>
```



# HTML5表单新增元素与属性

## form属性

-  表单内的从属元素可以卸载页面上任何地方，然后为该元素指定一个form属性
-  属性值为该表单的id，这样就可以声明该元素从属于指定表单了。

```
  <form id="textform">
    <input type="text">
  </form>
    <textarea form="textform"></textarea>
```

## formaction属性

-  可以为所有的提交按钮，增加不同的formaction属性，使单击不同的按钮时可以将表单提交到不同的页面

```
    <form id="testform">
      <input type="submit" name="s1" value="v1" formaction="xx.jsp">提交到 xx.jsp 页面
      <input type="submit" name="s2" value="v2" formaction="xx.jsp">提交到 xx.jsp 页面
      <input type="submit" name="s3" value="v3" formaction="xx.jsp">提交到 xx.jsp 页面
    </form>
```

## formmethod

-  HTML4：一个表单内只能有一个action属性用来对表单内所有元素统一指定提交页面，所以每个表单内页只有一个method属性来统一制定提交方法
-  HTML5：可使用formmethod属性来对每一个表单元素分别制定不同的提交方法

```
  <form id="testform">
    <input type="submit" name="s1" value="v1" formmethod="post" formaction="xx.jsp">提交到 xx.jsp 页面
    <input type="submit" name="s2" value="v2" formmethod="get" formaction="xx.jsp">提交到 xx.jsp 页面
  </form>
```



## formenctype属性

-  HTML4：表单元素具有一个`enctype`属性，该属性用于指定在表单发送到服务器之前应该如何对表单内的数据进行编码
-  HTML5：可以使用`formenctype`属性对表单元素**分别**制定不同的编码方式。

```
  <form>
    <input type="text" formenctype="text/plain">
    <input type="text" formenctype="multipart/form-data">
    <input type="text" formenctype="application/x-www-form-urlencoded">
  </form>
```



## formtarget属性

-  HTML4：表单元素具有一个target属性，该属性用于指定在何处打开表单提交后所需要加载的页面
-  HTML5：可以对多个提交按钮**分别**使用formtarget属性来指定提交后在何处打开所需加载的页面。

```
  <form id="testform">
    <input type="submit" name="s1" value="v1" formtarget="_blank" formaction="xx.jsp">提交到 xx.jsp 页面
    <input type="submit" name="s2" value="v2" formtarget="_self" formaction="xx.jsp">提交到 xx.jsp 页面
    <input type="submit" name="s3" value="v3" formtarget="_parent" formaction="xx.jsp">提交到 xx.jsp 页面
    <input type="submit" name="s3" value="v3" formtarget="_top" formaction="xx.jsp">提交到 xx.jsp 页面
    <input type="submit" name="s3" value="v3" formtarget="_framename" formaction="xx.jsp">提交到 xx.jsp 页面
  </form>
```



## autofocus属性

为文本框、选择框或按钮控件加上autofocus属性，当画面打开时，该控件自动获得光标焦点

```
  <form>
    <input type="text">
    <input type="text" autofocus>
  </form>
```



## required属性

可以应用在大多数输入元素上，在提交时，如果元素中内容为空白，则不允许提交，同时在浏览器中显示信息提示文字。

```
  <form action="http://www.baidu.com">
    <input type="text" required="required">
    <button type="submit">提交1</button>
    <input type="text" required="">
    <button type="submit">提交2</button>
  </form>
```



## labels属性

为所有可使用标签的表单元素、button、select元素等，定义一个labels属性，属性值为一个NodeList对象，代表该元素所绑定的标签元素所构成的集合。

```
  <script>
  function Validate(){
    var txtName = document.getElementById("txt_name");
    var button = document.getElementById("btnValidate");
    var form = document.getElementById("testform");
    if(txtName.value.trim()==""){
      var label = document.createElement("label");
      label.setAttribute("for","txt_name");
      form.insertBefore(label,button);
      txtName.labels[1].innerHTML = "请输入姓名";
      txtName.labels[1].setAttribute("style", "font-size:9px;color:red")
    }
  }</script>
  <form id="testform">
    <label for="txt_name" id="label">姓名：</label>
    <input id="txt_name">
    <input type="button" id="btnValidate" value="验证" onclick="Validate()">
  </form>
```





## 标签的control属性

可以在标签内部放置一个表单元素，并且通过该标签的control属性来访问该表单元素。

```
  <script>
  function setValue(){
    var label = document.getElementById("label");
    var textbox = label.control;
    textbox.value = "010010";
  }
  </script>
  <form action="">
    <label id="label">
      邮编：
      <input id="txt_zip" maxlength="6">
      <small>请输入六位数字</small>
    </label>
    <input type="button" value="设置默认值" onclick="setValue()">
  </form>
```



## 文本框的placeholder属性

-  当文本框处于未输入状态时显示的输入提示。
-  当文本框处于未输入状态且未获取光标焦点时，模糊显示输入提示文字。

```
  <input type="text" placeholder="请输入用户名">
```



## 文本框的list属性

-  该属性的值为某个datalist元素的id。datalist元素也是HTML5种新增的元素。


-  该元素类似于选择框，但是当用户想要设定的值不在选择列表之内时，允许自行输入。
-  datalist元素本身并不显示，而是当文本框获得焦点是以提示输入的方式显示。

```
  <form>
    <input type="text" name="greeting" list="greetings">
    <datalist id="greetings" style="display: none">
        <option value="HTML5学习">HTML5学习</option>
        <option value="Android学习">Android学习</option>
        <option value="IOS学习">IOS学习</option>
    </datalist>
  </form>
```

## 文本框的AutoComplete属性

-  帮助输入所用的自动完成功能，是一个既节省输入时间又十分方便的功能。
-  在HTML5之前，安全方面欠缺，因输入的内容都可见。
-  用autocomplement属性，安全性方面可以得到很好的控制。

```
  <input type="text" name="greeting" autocomplete="" list="greetings">
  <input type="text" name="greeting" autocomplete="on">
  <input type="text" name="greeting" autocomplete="off">
```

有点懵



## 文本框的pattern属性

-  在HTML5中，对Input元素使用pattern属性，并且将属性值设为某个格式的正则表达式，在提交时会针对这些进行检查，检查其内容是否符合给定格式。
-  当输入的内容不符合给定格式是，则不允许提交，同时在浏览器中显示信心提示文字，提示输入的内容必须符合给定格式。

```
  <form action="http://www.baidu.com">
    请输入内容
    <input pattern="[A-Z]{3}" name="part">
    <input type="submit">
  </form>
```



## 文本框的SelectionDirection属性

-  对input元素与textarea元素，HTML5增加了selectionDirection属性。
-  当用户在这两个元素中用鼠标选取部分文字时，可以使用该属性来获取选区方向
-  当用户正向选取文字时，该属性值为“forward"
-  当用户反向选取文字时，该属性值为"backward"
-  当用户没有选取任何文字时，该属性值为"forward"

```
  <script>
  function AD(){
    var control = document.forms[0]['text'];
    var Direction = control.selectionDirection;
    alert(Direction);
  }
  </script>
  <form action="http://www.baidu.com">
    <input type="text" name="text">
    <input type="button" value="点击我" onclick="AD()">
  </form>
```



## 复选框的indeterminate属性

-  过去：只有选取和费选取这两种状态
-  HTML5：可在Javascript脚本代码中对该元素使用indeterminate属性，以说明复选框处于“尚未明确是否选取“状态，共三种状态。

```
  <input type="checkbox" indeterminate id="cb">属性测试
  <script>
      var cb = document.getElementById("cb");
      cb.indeterminate = true;
  </script>
```



## image提交按钮的height属性与width属性

-  针对类型为image的input元素，HTML5新增了两个属性，height、width分别用来指定图片按钮的高度和宽度。

```
  <form action="test.jsp" method="post">
    姓名：<input type="text" name="name">
    <input type="image" src="#" alt="编辑" width="100" height="100">
  </form>
```



# 改良的input元素的种类

## 增加和改良的input元素的种类
-  url
-  email
-  date
-  time
-  datetime
-  datetime-local
-  month
-  weed
-  number
-  range
-  search
-  Tel
-  color

```
  <!-- url -->
  <form>
    <input type="url" name="url" value="http://www.baidu.com">
    <input type="submit" value="提交">
  </form>
  <!-- email -->
  <form>
    <input type="email" name="name" value="yo7588@126.com">
    <input type="submit" value="提交">
  </form>
  <!-- date -->
    <input type="date" name="date" value="">
  <!-- time -->
    <input type="time" name="time" value="10:00">
  <!-- datetime -->
    <input type="datetime" name=" datetime" value="">
  <!-- datetime-local -->
    <input type="datetime-local" name="datetimelocal">
  <!-- month -->
    <input type="month" name="month" value="2010-10-10">
  <!-- week -->
    <input type="week" name="week">
  <!-- number -->
    <input type="number" name="number" value="15" min="10" max="100" step="5">
  <!-- 计算器 -->
  <br>
  <script>
    function sum(){
      var n1 = document.getElementById("num1").valueAsNumber;
      var n2 = document.getElementById("num2").valueAsNumber;
      document.getElementById("result").valueAsNumber = n1 + n2;
    }
  </script>
    <form>
      <input type="number" id="num1">
      +
      <input type="number" id="num2">
      =
      <input type="number" id="result" readonly>
      <input type="button" value="计算" onclick="sum()">
    </form>
  <!-- range -->
    <input type="range" name="range" min="10" max="100" step="5" value="25">
  <!-- search -->
    <input type="search">
  <!-- tel -->
    <input type="tel">
  <!-- color -->
    <input type="color" onchange="document.body.style.backgroundColor = document.getElementById('currentColor').textContent = this.value;">
    <span id="currentColor"></span>
  <!-- output -->
  <script>
    function value_change(){
      var number = document.getElementById("range").value;
      document.getElementById("output").value = number;
    }
  </script>
    <form id="testform">
      <input type="range" id="range" min="0" max="100" step="5" onchange="value_change()">
      <output id="output">10</output>
    </form>
```



## 表单验证

```
  <script>
    function check(){
      var email = document.getElementById("email");
      if(email.value==""){
        alert("请输入email");
        return false;
      }else if(!email.checkValidity()){
        alert("请输入正确的email地址");
        return false;
      }
    }
  </script>
  <form id="testform" onsubmit="check()" novalidate="true">
    <label for="email">Email</label>
    <input type="email" name="email" id="email"><br>
    <input type="submit">
  </form>
```





# HTML5增强的页面元素

## figure、figcaption、details、summary和mark元素

```
  <!-- figure以及figcaption -->
  <figure>
    <img src="https://ws1.sinaimg.cn/large/006tNc79gy1fkl9klyw84j30xy0diady.jpg" alt="HMTL5">
    <img src="https://ws1.sinaimg.cn/large/006tNc79gy1fkl9klyw84j30xy0diady.jpg" alt="HMTL5">
    <img src="https://ws1.sinaimg.cn/large/006tNc79gy1fkl9klyw84j30xy0diady.jpg" alt="HMTL5">
    <figcaption>HTML5</figcaption>
  </figure>
  <br>
```

```
  <!-- details以及summary -->
  <script>
    function detail_onclick(detail){
      var p = document.getElementById("p");
      if(detail.open){
        p.style.visibility = "hidden";
      }else{
        p.style.visibility = "visible";
      }
    }
  </script>
  <details id="detail" onclick="detail_onclick(this)">
    <summary>速度与激情7</summary>
    <p id="p" style="visibility: hidden">你好吗？</p>
  </details>
```

```
  <!-- mark -->
  <p>这是一段文字。用来<mark>测试</mark>mark元素</p>
```

## progress和meter元素

```
#失败
  <script>
    function btn(){
      for(var i=0;i<=100;i++){
        // updateprogress(i);
        setTimeout(function(){
          updateprogress(i);
        },1200));
      }
    }

    function updateprogress(newValue){
      alert(newValue);
      var progressBar = document.getElmentById("p");
      progressBar.value = newValue;
      progressBar.getElementsByTagName("span")[0].textContent = newValue;
    }
  </script>
  <section>
    <h2>pregress元素的使用</h2>
    <p>完成的百分比<progress style="background-color: #ededed" id="p" max="100"><span>0</span>%</progress></p>
    <input type="button" onclick="btn()" value="点击">
  </section>
```



```
    <!-- meter -->
  <meter value="40" min="0" max="100" low="10" high="90" optimum="80"></meter>
  <meter>40%</meter>
```



## ol、dl、cite和small元素

```
  <!-- ol -->
  <ol start="5" reversed>
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
    <li>列表4</li>
    <li>列表5</li>
    <li>列表6</li>
  </ol>

  <!-- dl -->
  <dl>
    <dt>Hello</dt>
    <dd>你好就是hello</dd>
    <dt>博客</dt>
    <dd>你喜欢看博客吗</dd>
  </dl>

  <!-- cite -->
  <h3>cite元素</h3>
  <p>我最喜欢的电影是<cite>速度与激情</cite></p>


```



# HTML5编辑API之Range对象

## Range对象基本概念

一个Range对象代表页面上的一段连续区域。通过Range对象，可以获取或修改网页上的任何区域。

```
  <script>
    function rangeTest(){
      var html;
      showRangeDiv = document.getElementById("showRange");
      selection = document.getSelection();
      if(selection.rangeCount>0){
        html = "你选取了>"+selection.rangeCount+"<内容<br/>";
        for(var i=0; i<selection.rangeCount;i++){
          var range = selection.getRangeAt(i);
          html += "第"+(i+1)+"段内容为："+range+"<br>";
        }
        showRangeDiv.innerHTML = html;
      }
    }
  </script>
  Range对象基本概念
  <input type="button" value="点击我" onclick="rangeTest()">
  <div id="showRange"></div>
```



## Range方法

### SelectNode/SelectNodeContents/deleteContents

```
  <script>
    function deleteRangeContent(onlyContent){
        var div = document.getElementById("div");
        var rangeObj = document.createRange();
        if(onlyContent){
          rangeObj.selectNodeContents(div);
          rangeObj.deleteContents();
        }else{
          rangeObj.selectNode(div);
          rangeObj.deleteContents();
        }
    }
  </script>
  <div id="div" style="background-color: #e0a0b0; width:300px;height:50px">
    元素中的内容
  </div>
  <button onclick="deleteRangeContent(true)">删除内容</button>
  <button onclick="deleteRangeContent(false)">删除元素</button>
```



### setStart/setEnd

```
  <script>
    function deleteChar(){
      var div = document.getElementById("myDiv");
      var textNode = div.firstChild;
      var rangeObj = document.createRange();
      rangeObj.setStart(textNode,1);
      rangeObj.setEnd(textNode,4);
      rangeObj.deleteContents();
    }
  </script>
  <div id="myDiv" style="color:red">
    这段文字是用来删除的
  </div>
  <button onclick="deleteChar()">删除文字</button>
```

### setStartBefore/setStartAfter/setEndBefore/setEndAfter

```
  <script>
    function deleteRow(){
      var table = document.getElementById("myTable");
      if(table.rows.length > 0){
        var row = table.rows[0];
        var rangeObj = document.createRange();
        rangeObj.setStartBefore(row);
        rangeObj.setEndAfter(row);
        rangeObj.deleteContents();
      }
    }
  </script>
  <table id="myTable" border="1" cellsapcing="0" cellpadding="0">
    <tr>
      <td>内容1</td>
      <td>内容2</td>
    </tr>
    <tr>
      <td>内容3</td>
      <td>内容4</td>
    </tr>
  </table>
  <button onclick="deleteRow()">删除第一行</button>
```





## Range对象方法

### cloneRange方法、cloneContents方法、extractContents方法与createContextual-Fragment方法

```
  <script>
    function cloneRnge(){
      var rangeObj = document.createRange();
      rangeObj.selectNodeContents(document.getElementById("p"));
      var rangeClone = rangeObj.cloneRange();
      alert(rangeClone.toString());
    }
  </script>
  <p id="p">这里是随便书写的内容</p>
  <button onclick="cloneRnge()">克隆</button>
```

```
  <script>
    function cloneContent(){
      var div = document.getElementById("div");
      var rangeObj = document.createRange();
      rangeObj.selectNodeContents(div);
      var docFrangMent = rangeObj.cloneContents();
      div.appendChild(docFrangMent)
    }
  </script>
    <div id="div">
      你好吗？
      <br>
      <button onclick="cloneContent()">克隆</button>
      <br>
    </div>
```

```
  <script>
    function moveContent(){
      var srcDiv = document.getElementById("srcDiv");
      var disDiv = document.getElementById("disDiv");
      var rangeObj = document.createRange();
      rangeObj.selectNodeContents(srcDiv);
      var docFragment = rangeObj.extractContents();
      disDiv.appendChild(docFragment)
    }
  </script>
  <div id="srcDiv" style="background-color: aquamarine;width: 300px; height: 50px">你好吗？</div>
  <div id="disDiv" style="background-color: bisque;width: 300px; height: 50px">你好吗？</div>
  <button onclick="moveContent()">移动元素</button>
```



### insertNode、compareBoundaryPoints方法

```
  <script>
    function moveButton(){
      var btn = document.getElementById("button");
      var selection = document.getSelection();
      if(selection.rangeCount > 0) {
        var range = selection.getRangeAt(0);
        range.insertNode(btn)

      }
    }
  </script>
  <div onmouseup="moveButton()" style="width: 400px; background-color:#ededed;">
    这里是我随便书写的一些文字。这里是我随便书写的一些文字。这里是我随便书写的一些文字。这里是我随便书写的一些文字。这里是我随便书写的一些文字。这里是我随便书写的一些文字。这里是我随便书写的一些文字。这里是我随便书写的一些文字。这里是我随便书写的一些文字。
  </div>
  <button id="button">按钮</button>
```

```
  <script>
    function testPlace(){
    var boldText = document.getElementById("boldTest");
    var boldRange = document.createRange();
    boldRange.selectNodeContents(boldText.firstChild);
    var selection = document.getSelection();
    if(selection.rangeCount>0){
      var selRange = selection.getRangeAt(0);
      if(selRange.compareBoundaryPoints(Range.START_TO_END,boldRange)<=0){
        alert("选取的文字在粗体前面");
      }else{
        if(selRange.compareBoundaryPoints(Range.END_TO_START,boldRange)>=0){
          alert("选择的文字在粗体后面");
        }
      }
    }
  }
  </script>
  这是一段文字,我也<b id="boldTest">不知道</b>写什么，随便吧。
  <br>
  <button onclick="testPlace()">位置比较</button>
```



### collapse、detach方法

```
  <script>
    var rangeObj = document.createRange();
    function selectRangeConents(){
      var div = document.getElementById("div");
      rangeObj.selectNode(div);
      rangeObj.detach();
    }
      function unselect(){
        rangeObj.collapse(false);
      }
      function shwoRange(){
        alert(rangeObj.toString());
      }
  </script>
    <div id="div" style="background-color: bisque;width: 300px;height:50px;">元素中的内容</div>
    <button onclick="selectRangeConents()">选择元素</button>
    <button onclick="unselect()">取消元素</button>
    <button onclick="shwoRange()">显示Range内容</button>
```





# HTML5 Canvas 使用路径

## HTML5绘制圆形

```
<body onload="draw('canvas')">
  <script>
    function draw(id){
      var canvas = document.getElementById(id);
      if(canvas == null){
        return false;
      }
      var context = canvas.getContext("2d");
      context.fillStyle = "#eeeeef";
      context.fillRect(0,0,600,700);
      for(var i = 0; i<=10;i++){
        context.beginPath();
        context.arc(i*25,i*25,i*10,0,Math.PI*2,true);
        context.closePath();
        context.fillStyle = "rgba(255,0,0,0.25)";
        context.fill();
      }
    }
  </script>
  <canvas id="canvas" width="600px" height="700px"></canvas>
</body>
```

## HTML5 moveTo与lineTo

```
  <script>
    function draw(id){
      var canvas = document.getElementById(id);
      var context = canvas.getContext("2d");
      context.fillStyle = "#eeeeef";
      context.fillRect(0,0,300,400);
      var dx = 150;
      var dy = 150;
      var s = 100;
      context.beginPath();
      context.fillStyle = "rgb(100,255,100)";
      context.strokeStyle = "rgb(0,0,100)";
      var x = Math.sin(0);
      var y = Math.cos(0);
      var dig = Math.PI / 15*11;
      for(var i = 0; i<30; i++){
        var x = Math.sin(i*dig);
        var y = Math.cos(i*dig);
        context.lineTo(dx+x*s,dy+y*s);
      }
      context.closePath();
      context.fill();
      context.stroke();
    }
  </script>
</head>
  <body onload="draw('canvas')">

    <canvas id="canvas" width="300" height="400"></canvas>
  </body>
```

## 使用bezierCurveTo绘制贝塞尔曲线

-  `bezierCurveTo(cp1x,cp1y,cp2x,cp2y,x,y)`
-  控制点

```
  <script>
    function draw(id){
      var canvas = document.getElementById(id);
      if(canvas == null){
        return false;
      }
      var context = canvas.getContext("2d");
      context.fillStyle = "#eeeeef";
      context.fillRect(0,0,300,400);
      var dx = 150;
      var dy = 150;
      var s = 100;
      context.beginPath();
      context.fillStyle = "rgb(100,255,100)";
      var x = Math.sin(0);
      var y = Math.cos(0);
      var dig = Math.PI / 15*11;
      context.moveTo(dx,dy);
      for(var i = 0; i<30;i++){
          var x = Math.sin(i*dig);
          var y = Math.cos(i*dig);
          context.bezierCurveTo(dx+x*s,dy+y*s-100,dx+x*s+100,dy+y*s,dx+x*s,dy+y*s);
      }
      context.closePath();
      context.fill();
      context.stroke();
    }
  </script>
</head>
<body onload="draw('canvas')">
  <!-- bezierCurveTo(cp1x,cp1y,cp2x,cp2y,x,y) -->
  <canvas id="canvas" width="300px" height="400px"></canvas>
</body>
```



# Canvas 绘制渐变图形与绘制变形图形

## Canvas 绘制渐变图形(线性)

```
  LinerGradient
  context.createLinerGradient(xstart,ystart,xend,yend)
  addColorStop(offset,color)
  addColorStop(offset,color)
```

```
<script>
  function draw(id){
    var canvas = document.getElementById(id);
    var context = canvas.getContext("2d");
    var g1 = context.createLinearGradient(0,0,0,300);
    g1.addColorStop(0,"rgb(255,255,0)");
    g1.addColorStop(1,"rgb(0,255,255)");
    context.fillStyle = g1;
    context.fillRect(0,0,500,500);
    var g2 = context.createLinearGradient(0,0,300,0);
    g2.addColorStop(0,"rgba(0,0,255,0.5)");
    g2.addColorStop(1,"rgba(255,0,0,0.5)");
    for(var i = 0;i<10;i++){
      context.beginPath();
      context.fillStyle = g2;
      context.arc(i*25,i*25,i*10,0,Math.PI*2,true);
      context.closePath();
      context.fill();
    }
  }
</script>
<body onload="draw('canvas')">
  <canvas id="canvas" width=:"500" height="500"></canvas>
</body>
```



## Canvas 绘制径向渐变

```
 <head>
  <script>
    function draw(id){
      var canvas = document.getElementById(id);
      if(canvas == null){
        return false;
      }
      var context = canvas.getContext("2d");
      var g1 = context.createRadialGradient(400,50,50,400,50,400);
      g1.addColorStop(0.1,"rgb(255,255,0)");
      g1.addColorStop(0.3,"rgb(255,0,255)");
      g1.addColorStop(1,"rgb(0,255,255)");
      context.fillStyle = g1;
      context.fillRect(0,0,500,500);
    }
  </script>
</head>

<body onload="draw('canvas')">
  <canvas id="canvas" width="500" height="500"></canvas>
</body>
```



## Canvas 绘制变形图形

```
  translate(x,y)
  scale(x,y)
  rotate(deg)
```

```
 <head>
  <script>
    function draw(id){
      var canvas = document.getElementById(id);
      if(canvas == null){
        return false;
      }
      var context = canvas.getContext("2d");
      context.fillStyle = "#eeeeef";
      context.fillRect(0,0,500,500);
      context.translate(300,50);
      context.fillStyle = "rgba(255,0,0,0.25)";
      for(var i = 0;i<50;i++){
        context.translate(25,25);
        context.scale(0.95,0.95);
        context.rotate(Math.PI/10);
        context.fillRect(0,0,100,50);
      }
    }
  </script>
</head>
<body onload="draw('canvas')">
  <canvas id="canvas" width="500" height="500"></canvas>
</body>
```



# Canvas 图形绘制处理

## Canvas 图形组合

```
   <!--globalCompositeOperation = type 属性-->
   scource-atop
    source-in
    source-out
    source-over
    destination-atop
    destination-in
    destination-out
    destination-over
    lighter
    copy
    xor
```



```
 <head>
  <script>
    function draw(id){
      var canvas = document.getElementById(id);
      var context = canvas.getContext("2d");
      var oprtns = new Array(
        "scource-atop",
        "source-in",
        "source-out",
        "source-over",
        "destination-atop",
        "destination-in",
        "destination-out",
        "destination-over",
        "lighter",
        "copy",
        "xor"
      );
      i = 3;
      context.fillStyle = "blue";
      context.fillRect(10,10,60,60);
      context.globalCompositeOperation = oprtns[i];
      context.beginPath();
      context.fillStyle = "red";
      context.arc(60,60,30,Math.PI*2,false);
      context.fill();
    }
  </script>

</head>
<body onload="draw('canvas')">
  <canvas id="canvas" width="500" height="500"></canvas>
</body>
```



## Canvas 给图形绘制阴影

```
shadowOffsetX
shadowOffsetY
shadowColor
shadowBlur
```

```
<head>
 <script>
    function draw(id){
      var canvas = document.getElementById(id);
      var context = canvas.getContext("2d");
      context.fillStyle = "#eeeeef";
      context.fillRect(0,0,500,500);
      context.shadowOffsetX = 20;
      context.shadowOffsetY = 20;
      context.shadowColor = "rgba(100,100,100,0.5)";
      context.shadowBlur = 7.5;

      context.translate(0,50);
      for(var i=0;i<3;i++){
        context.translate(100,100);
        create5Star(context);
        context.fill();
      }
    }
    function create5Star(context){
      var n = 0;
      var dx = 100;
      var dy = 0;
      var s = 50;
      context.beginPath();
      context.fillStyle = "rgba(255,0,0,0.5)";
      var x = Math.sin(0);
      var y = Math.cos(0);
      var dig = Math.PI /5*4;
      for(var i=0;i<5;i++){
          var x = Math.sin(i*dig);
          var y = Math.cos(i*dig);
          context.lineTo(dx+x*s,dy+y*s)
      }
      context.closePath()
    }
  </script>

</head>
<body onload="draw('canvas')">
  <canvas id="canvas" width="500" height="500"></canvas>
</body>
```





## Canvas 使用图像

```
  context.drawImage(img,x,y);
  context.drawImage(img,x,y,w,h);
  context.drawImage(img,sx,sy,sw,sh,dx,dy,dw,dh);
```

```
<head>
 <script>
    function draw(id){
      var canvas = document.getElementById(id);
      var context = canvas.getContext("2d");
      context.tillStyle = "#eeeeef";
      context.fillRect(0,0,500,500);
      image = new Image();
      image.src = "https://ws4.sinaimg.cn/large/006tKfTcgy1fkkdfpuicxj30kw0ldgoy.jpg";
      image.onload = function(){
        drawImage(context,image);
      }
    }
    function drawImage(context,image){
      context.drawImage(image,0,0,200,200);
      context.drawImage(image,270,270,380,380,230,230,120,110);
    }
  </script>
</head>
<body onload="draw('canvas')">
  <canvas id="canvas" width="500" height="500"></canvas>
</body>
```



# Web Storage概述

## Web Storage概述

-  过去的问题：使用cookies在客户端保存诸如存储如用户名等简单用户信息，但用cookies储存永久数据存在几个问题：
   -  大小：ccookies的大小被限制在4kb
   -  宽带：cookies是随HTTP事务一起被发送的，因此会浪费一部分发送cookies时使用的宽带
   -  复杂性：要正确的操纵cookies是很困难的。
-  功能是在web上储存数据的功能。这里的储存是针对客户端本地而言的。
   -  sessionStorage：讲述徐保存在session对象中。session是指用户在浏览某个网站时，从进入网站到浏览器关闭所经过的这段时间，也就是用户浏览这个网络战所花费的时间。session对象可以用来保存在这段时间内所要求保存的任何数据。
   -  localStorage：将数据保存在客户端本地的硬件设备（硬盘）中，即使浏览器被关闭了，该数据仍然存在，下一次打开浏览器访问网站是仍然可以继续使用。通常用来保存用户名和密码。

```
  <head>
  <script>
  function saveStorage(id){
    var target = document.getElementById(id);
    var str = target.value;
  // 保存数据的方法: key value
    sessionStorage.setItem("message",str);
  }

  function loadStorage(id){
    var target = document.getElementById(id);
  // 读取数据
    var msg = sessionStorage.getItem("message");
    target.innerHTML = msg;
  }
  </script>
</head>
<body>
  <p id="msg"></p>
  <input type="text" id="input">
  <input type="button" value="保存数据" onclick="saveStorage('input')">
  <input type="button" value="读取数据" onclick="loadStorage('msg')">
</body>
```

```
<head>
  <script>
function saveStorage(id){
  var target = document.getElementById(id);
  var str = target.value;
  localStorage.setItem("message", str)
}

function loadStorage(id){
  var target = document.getElementById(id);
  var msg = localStorage.getItem("message");
  target.innerHTML = msg;
}
  </script>
</head>
<body>
  <p id="msg"></p>
  <input type="text" id="input">
  <input type="button" value="保存数据" onclick="saveStorage('input')">
  <input type="button" value="读取数据" onclick="loadStorage('msg')">
</body>
```



## 简单Web留言本

失败

```
function saveStorage(id){
  var data = document.getElementById(id).value;
  var time = new Date().getTime();
  localStorage.setItem(time,data);
  alert("数据已储存");
  localStorage('msg');
}

function loadStorage(id){
  var result = "<table border = '1'>";
  for(var = 0;i<localStorage.length;i++){
      var key = localStorage.key(i);
      var value = localStorage.getItem(key);
      var date = new Date();
      date.setTime(key);
      result += "<tr><td>"+value+"</td><td>"+date+"</td></tr>";
  }
  result += "</table>";
  var target = document.getElementById(id);
  target.innerHTML = result;
}

function clearStorage(){
  localStorage.clear();
  alert("数据已经删除");
  loadStorage('msg');
}
```

```
  <p id="msg"></p>
  <textarea id="memo" cols="60" rows="10"></textarea><br>
  <input type="button" value="追加数据" onclick="saveStorage('memo')">
  <input type="button" value="删除数据" onclick="clearStorage()">
```



## 作为简单数据库来利用

```javascript
function saveStorage(){
  var data = new Object;
  data.name = document.getElementById("name").value;
  data.email = document.getElementById("email").value;
  data.tel = document.getElementById("tel").value;
  data.memo = document.getElementById("memo").value;
  var str = JSON.stringify(data);
  localStorage.setItem(data.name,str);
  alert("数据已经保存");
}

function findStorage(id){
  var find = document.getElementById('find').value;
  var str = localStorage.getItem(find);
  var data = JSON.parse(str);
  var result = "姓名："+data.name + "<br>";
      result += "Email："+data.email + "<br>";
      result += "话号码："+data.tel + "<br>";
      result += "备注："+data.memo + "<br>";
  var target = document.getElementById(id);
  target.innerHTML = result;
}
```

```html
<body>
  <table>
    <tr>
      <td>姓名：</td><td><input type="text" id="name"></td>
      <td>Email：</td><td><input type="text" id="email"></td>
      <td>电话号码：</td><td><input type="text" id="tel"></td>
      <td>备注：</td><td><input type="text" id="memo"></td>
    </tr>
    <tr>
      <td></td>
      <td><input type="button" value="保存" onclick="saveStorage()">  </td>
    </tr>
  </table>
  <hr>
  <p>检索：
  <input type="text" id="find">
  <input type="button" value="检索" onclick="findStorage('msg')">
  </p>
  <p id="msg"></p>
</body>
```





# 本地数据库

## 本地数据库的基本概念

大大丰富了客户端本地可以存储的内容，添加了很多功能将原本必须要保存在富强武器上的数据转为保存在客户端本地，从而大大提高了WEB应用程序性能，减轻了服务器的负担，使用web时代重新回到了“客户端为重、服务端为轻”的时代。

-  可以像访问本地文件那样轻松地对内置数据库进行直接访问
-  内置了两种本地数据库：SQLLite、indexedDB

1. 创建访问数据库的对象
2. 使用事务处理

```
  <script>
    var db = openDatabase("mydb","1.0","test db",1024*100);
    db.transaction(function(tx){
      tx.executeSql("");
    });
  </script>
```



## 用executesql来执行查询

```
    transaction.excuteSqul(sqlquery,[],dataHandler,errorHandler);
    function dataHandler(transaction,results);
    function errorHandler(transaction,errmsg);
    rows.length获取记录的条数
    rows属性 rows.length rows[index]
```

```
  transaction.excuteSqul("",[],function(){},function(){});
```



## 使用数据库实现Web留言本

```
var datatable = null;
var db = openDatabase("MyData","","My Database",1024*100);
function init(){
  datatable = document.getElementById("datatable");
  showAllData();

}

function removeAllData(){
  for(var i = datatable.childNodes.length - 1;i >= 0;i--){
    datatable.removeChild(datatable.childNodes[i]);
  }
  var tr = document.createElement("tr");
  var th1 = document.createElement("th");
  var th2 = document.createElement("th");
  var th3 = document.createElement("th");
  th1.innerHTML = "姓名";
  th2.innerHTML = "留言";
  th3.innerHTML = "时间";
  tr.appendChild(th1);
  tr.appendChild(th2);
  tr.appendChild(th3);
  datatable.appendChild(tr);
}

function showData(row){
  var tr = document.createElement("tr");
  var td1 = document.createElement("td");
  td1.innerHTML = row.name;
  var td2 = document.createElement("td");
  td2.innerHTML = row.message;
  var td3 = document.createElement("td");
  var t = new Date();
  t.setTime(row.time);
  td3.innerHTML = t.toLocaleDateString()+""+ t.toLocaleTimeString();
  tr.appendChild(td1);
  tr.appendChild(td2);
  tr.appendChild(td3);
  datatable.appendChild(tr);
}

function showAllData(){
  db.transaction(function(tx){
    tx.executeSql("CREATE TABLE IF NOT EXISTS MsgData(name TEXT,message TEXT,time INTEGER)",[]);
    tx.executeSql("SELECT * FROM MsgData", [], function(tx,rs){
      removeAllData();
      for(var i = 0;i<rs.rows.length;i++){
        showData(rs.rows.item(i));
      }
    })
  })
}
function addData(name,message,time){
  db.transaction(function(tx){
    tx.executeSql("INSERT INTO MsgData VALUES(?,?,?)",[name,message,time],function(tx,rs){
      alert("成功");
    },
    function(tx,error){
      alert(error.source+"::"+error.message);
    }
  )
  })
}

function saveData(){
  var name = document.getElementById("name").value;
  var memo = document.getElementById("memo").value;
  var time = new Date().getTime();
  addData(name,memo,time);
  showAllData();
}
```



```
<body onload="init()">
  <table>
    <tr><td>姓名：</td><td><input type="text" id="name"></td></tr>
    <tr><td>留言：</td><td><input type="text" id="memo"></td></tr>
    <tr>
      <td></td>
      <td><input type="button" value="保存" onclick="saveData()"></td>
    </tr>
  </table>
  <hr>
  <table id="datatable" border="1">
  </table>
    <p id="msg"></p>
</body>
```



# indexedDB数据库

## 链接数据库

-  该数据库是一种存储在客户端本地的NoSQL数据库

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fkmmsigd4vj30oh041q6j.jpg)

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fkmmsim1daj30pl03eadi.jpg)



```
  <script>
  window.indexedDB = window.indexedDB || window.webkitIndexedDB || window.mozIndexedDB || window.msIndexedDB;
    window.IDBTransaction = window.IDBTransaction || window.webkitIDBTransaction || window.msIDBTransaction;
    window.IDBKeyRange = window.IDBKeyRange ||window.webkitIDBKeyRange || window.msIDBKeyRange;
    window.IDBCursor = window.IDBCursor || window.webkitIDBCursor || window.webkitIDBCursor || window.msIDBCursor;
    function connectDatabase(){
      var dbName = "indexedDBtest";
      var dbVersion = 1;
      var idb;
      var dbConnect = indexedDB.open(dbName,dbVersion);
      dbConnect.onsuccess = function(e){
        idb = e.target.result;
        alert("数据库链接成功");
      };
      dbConnect.onerror = function(){
        alert("链接数据库失败")
      }
    }

  </script>
<body>
  <input type="button" value="链接数据库" onclick="connectDatabase()">
</body>
```

## 数据库的版本更新

```
<head>
<script>
    window.indexedDB = window.indexedDB || window.webkitIndexedDB || window.mozIndexedDB || window.msIndexedDB;
    window.IDBTransaction = window.IDBTransaction || window.webkitIDBTransaction || window.msIDBTransaction;
    window.IDBKeyRange = window.IDBKeyRange ||window.webkitIDBKeyRange || window.msIDBKeyRange;
    window.IDBCursor = window.IDBCursor || window.webkitIDBCursor || window.webkitIDBCursor || window.msIDBCursor;

    function VersionUpDate(){
      var dbName = "indexDBtest";
      var dbVersion = 2;
      var idb;
      var dbConnect = indexedDB.open(dbName,dbVersion);
      dbConnect.onsuccess = function(e){
        idb = e.target.result;
        alert("数据库链接成功");
      }
      dbConnect.onerror = function(){
        alert("数据库链接成功");
      }
      dbConnect.onupgradeneeded = function(e){
        idb = e.target.result;
        var tx = e.target.transaction;
        var oldVersion = e.oldVersion;
        var newVersion = e.newVersion;
        alert("数据库更新成功"+oldVersion+"---"+newVersion);
      }
    }
  </script>
</head>
<body>
  <input type="button" value="数据库更新" onclick="VersionUpDate()">
</body>
```



## 创建对象仓库

失败

```
  <script>
  window.indexedDB = window.indexedDB || window.webkitIndexedDB || window.mozIndexedDB || window.msIndexedDB;
window.IDBTransaction = window.IDBTransaction || window.webkitIDBTransaction || window.msIDBTransaction;
window.IDBKeyRange = window.IDBKeyRange ||window.webkitIDBKeyRange || window.msIDBKeyRange;
window.IDBCursor = window.IDBCursor || window.webkitIDBCursor || window.webkitIDBCursor || window.msIDBCursor;

  function createObjectStore(){
    var dbName = "indexDBTest";
    var dbVersion = 3;
    var idb;
    var dbConnect = indexedDB.open(dbName,dbVersion);
    dbConnect.onsuccess = function(e){
      idb = e.target.result;
      alert("数据库链接成功");
    }
    dbConnect.onerror = function(){
      alert("数据库链接失败");
    }
    dbConnect.onupgradeneeded = function(e){
      idb = e.target.reslut;
      var name = "user";
      var optionalParameters = {
        keyPath:"userid",
        autoIncrement:false
      };
      var store = idb.createObjectStore(name, optionalParameters);
      alert("对象仓库创建成功")
    }
  }
  </script>
</head>
<body>
  <input type="button" value="创建仓库" onclick="createObjectStore()">
</body>
```



# indexedDB数据库索引

## 创建索引

-  createindex 索引名称、索引属性字段名、索引属性值是否唯

未成功

```
<script>
  var myDB = {
    name: "helloindexDB",
    version:1,
    db:null,
  }
  function openDB(name,version){
    var version = version||1;
    var request = window.indexedDB.open(name,version);
    request.onerror = function(e){
    }
    request.onsuccess = function(e){
      myDB.db = e.target.result;
    }
    request.onupgradeneeded = function(e){
      var db = e.target.result;
      if(!db.objectStoreNames.contains("students")){
        var store = db.createObjectStore("students",{keyPath:"id"});
        store.createIndex("nameIndex","name",{unique:true});
        store.createIndex("ageIndex","age",{unique:false});
      }
    }
  }

  var students = [{
    id:101,
    name:"aa",
    age:10
  },{
    id:102,
    name:"bb",
    age:11
  },{
    id:103,
    name:"cc",
    age:15
  },{
    id:104,
    name:"tt",
    age:18
  },{
    id:106,
    name:"mm",
    age:20
  }]

  function addData(db,storeName){
    var transaction = db.transaction(storeName,"readwrite");
    var store = transaction.objectStore(storeName);
    for(var i = 0;i<students.length;i++){
      store.add(students[1]);
    }
  }

  openDB(myDB.name,myDB.version);
  setTimeout(function(){
    addData(myDB.db,"students");
  },1000);
  </script>
```



## 利用索引获取数据

失败

```
 <head>
  <script>
  var myDB = {
    name: "helloindexDB",
    version:1,
    db:null,
  }
  function openDB(name,version){
    var version = version||1;
    var request = window.indexedDB.open(name,version);
    request.onerror = function(e){
    }
    request.onsuccess = function(e){
      myDB.db = e.target.result;
    }
    request.onupgradeneeded = function(e){
      var db = e.target.result;
      if(!db.objectStoreNames.contains("students")){
        var store = db.createObjectStore("students",{keyPath:"id"});
        store.createIndex("nameIndex","name",{unique:true});
        store.createIndex("ageIndex","age",{unique:false});
      }
    }
  }

  var students = [{
    id:101,
    name:"aa",
    age:10
  },{
    id:102,
    name:"bb",
    age:11
  },{
    id:103,
    name:"cc",
    age:15
  },{
    id:104,
    name:"tt",
    age:18
  },{
    id:106,
    name:"mm",
    age:20
  }]

  function addData(db,storeName){
    var transaction = db.transaction(storeName,"readwrite");
    var store = transaction.objectStore(storeName);
    for(var i = 0;i<students.length;i++){
      store.add(students[1]);
    }
  }

  openDB(myDB.name,myDB.version);
  setTimeout(function(){
    addData(myDB.db,"students");
  },1000);

  function getDataByIndexName(db,storeName){
    var transaction = db.transaction(storeName);
    var store = transaction.objectStore(storeName);
    var index = store.index("nameIndex");
    index.get("aa").onsuccess = function(e){
      var student = e.target.result;
      console.log(student.name+"---"+student.age+"---"+student.id)
    }
  }

  setTimeout(function(){
    getDataByIndexName(myDB.db,"students");
  },1000);

  function getDataByIndexAge(db,storeName){
    var transaction = db.transaction(storeName);
    var store = transaction.objectStore(storeName);
    var index = store.index("ageIndex");
    index.get(11).onsuccess = function(e){
      var student = e.target.result;
      console.log(student.name+"---"+student.age+"---"+student.id)
    }
  }

  setTimeout(function(){
    getDataByIndexAge(myDB.db,"students");
  },1000);
  </script>
```





## 游标与index和游标结合

跳过

# 文件API

## FileList对象与File对象

```
<head>
<script>
    function showFileName(){
      var file;
      for(var i = 0;i<document.getElementById("file").files.length;i++){
        file = document.getElementById("file").files[i];
        console.log(file.name);
      }

    }
  </script>
</head>
<body>
  <input type="file" id="file" multiple>
  <input type="button" onclick="showFileName()" value="文件上传">
</body>
```



## 文件API之Blo b对象

File<blob:size type（继承）

-  size长度
-  type类型

```
 <head>
  <script>
    function showFileInfo(){
      var file;
      file = document.getElementById("file").files[0];
      var size = document.getElementById("size");
      size.innerHTML = file.size;
      var type = document.getElementById("type");
      type.innerHTML = file.type;

    }
  </script>
</head>
<body>
  选择文件：
  <input type="file" id="file" multiple>
  <input type="button" onclick="showFileInfo()" value="显示文件信息"><br>

  文件大小：<span id="size"></span><br>
  文件类型：<span id="type"></span>
</body>
```

```
 <head>
  <script>
    function FileUpload(){
      var file;
      for(var i = 0; i<document.getElementById("file").files.length;i++){
        file = document.getElementById("file").files[i];
        if(!/image\/\w+/.test(file.type)){
          alert("请上传身份证图片");
        }else{
        console.log("ok")
        }
      }
    }
  </script>
</head>
<body>
  <input type="file" id="file" multiple>
  <input type="button" onclick="FileUpload()" value="显示文件信息"><br>
```



## 文件API之FileReader对象

5个对象：

-  readAsBinaryString:
-  readAsText:
-  readAsDataURL:
-  readArrayBuffer:
-  abort:

6个事件：

-  onabort:
-  onerror:
-  onloadstart:
-  onprogress:
-  onload:
-  onloadend:

```
<header>
<script>
      var result = document.getElementById("result");
      var file = document.getElementById("file");
      function readAsDataURL(){
        var file = document.getElementById("file").files[0];
        var reader = new FileReader();
        reader.readAsDataURL(file);
        reader.onload = function(e){
          var resultimg = document.getElementById("result");
          resultimg.innerHTML = '<img src="'+this.result+'" alt="" />';
        }
      }

      function readAsText(){
        var file = document.getElementById("file").files[0];
        var reader = new FileReader();
        reader.readAsText(file);
        reader.onload = function(e){
          var resulttxt = document.getElementById("result");
          resulttxt.innerHTML = this.result;
        }
        reader.onprogress = function(){

        }
      }


  </script>
</head>
<body>
  <p>
    <label>请选择一个文件</label>
    <input type="file" id="file">
    <input type="button" value="读取图像" onclick="readAsDataURL()">
    <input type="button" value="读取二进制数据" onclick="">
    <input type="button" value="读取文本文件" onclick="readAsText()">
  </p>
  <div name="result" id="result">

  </div>
</body>
```



## FileSystem概述及浏览器检测

失败的回调

![](https://ws3.sinaimg.cn/large/006tKfTcgy1fkmpvhgighj30y80fwwk5.jpg)

```
  window.requestFileSystem(type,size,successCallback,errorCallback)
```

失败：

```
  <script>
      window.requestFileSystem=window.requestFileSystem || window.webkitRequestFileSystem;
      var fs = null;
      var msg = "";
      if(window.requestFileSystem){
        initFs();
      }
      function initFs(){
        window.requestFileSystem(window.TEMPORARY,1024*10,function(filesystem){
          fs = filesystem;
          document.getElementById("result").innerHTML = "当前浏览器可以操作";
        },erroHandler);
      }
        function erroHandler(e){
          switch (e.code){
            case FileError.NOT_FOUND_ERR:
                msg = "未找到文件或目录";
                break;
            case FileError.SECURITY_ERR:
                msg = "操作不当引起的安全性错误";
                break;
        };
        document.getElementById("result").innerHTML="当前引发的错误"+msg;
      }

  </script>
</head>
<body>
    <output id="result"></output>
</body>
```



## 申请磁盘配额

```
  <script>

    function getSzie(){
      var size = document.getElementById("capacity").value;
      window.webkitStorageInfo.requestQuota(PERSISTENT,size,function(grantdBytes){
        var text = "申请磁盘成功";
        var strBtyes,intBytes;
        if(grantdBytes >= 1024*1024*1024){
          intBytes = Math.floor(grantdBytes/(1024*1024*1024));
          text+=intBytes+"GB";
          grantdBytes = grantdBytes*(1024*1024*1024);
        }
        if(grantdBytes >= 1024*1024){
          intBytes = Math.floor(grantdBytes/(1024*1024));
          text+=intBytes+"GB";
          grantdBytes = grantdBytes*(1024*1024);
        }
        if(grantdBytes >= 1024){
          intBytes = Math.floor(grantdBytes/(1024));
          text+=intBytes+"GB";
          grantdBytes = grantdBytes*(1024);
        }
        text+=grantdBytes+"bytes";
        document.getElementById("result").innerHTML =text;
      })
    }

  </script>
</head>
<body>
    <input type="text" id="capacity" value="1024">
    <input type="button" value="申请配额" onclick="getSzie()">
    <output id="result"></output>
</body>
```



## 创建文件

失败

```
  <script>
  function createFile(){
    var size= document.getElementById("FileName").value;
    window.webkitRequestFileSystem(PERSISTENT,size,function(fs){
      var fileName = document.getElementById("FileName").value;
      fs.root.getFile(fileName,{
        create:true
      },
        function(fileEntry){
          var text = "文件完整路径:"+fileEntry.fullPath+"<br />";
          text += "文件名"+fileEntry.name+"<br />";
          document.getElementById("result").innerHTML = text;
        })
    })
  }
  </script>
</head>
<body>
  <form>
    文件名：<input type="text" id="FileName" value="test.txt"><br>
    文件大小：<input type="text" id="FileSzie" value="2014"><br>
    <input type="button" value="创建文件" onclick="createFile()">
  </form>
</body>
```
