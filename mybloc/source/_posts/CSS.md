---
title: CSS
date: 2017-09-23 22:49:52
tags: [CSS]
---


# CSS Setup and Selectors

## CSS （层叠样式表）
> Cascading Style Sheets


- 和HTML一样都是标记语言，可以直接由浏览器执行，属于浏览器解释型语言。
- 能够对网页中的元素进行精确的控制
- 能够真正做到网页表现与内容分离的一种样式设计语言
- 最新版本为CSS3

## CSS和HTML的关系
- HTML是标记，是把文字、图片等内容放在HTML标签中让浏览器去解释，并把内容显示在浏览器中，供用户阅读
- CSS是为HTML标签添加各种样式，用来告诉浏览器，应该如何显示这些标签里面的内容，起到局部与美化页面的作用
  a language that web developers use to **style** the HTML content on a web page.


## CSS样式的写法格式  
### Inline Styles（行内样式）
> a quick way of directly styling an HTML element.
> 在HTML标签内部，以属性的方式写CSS样式，该CSS样式只会对本标签起到作用。

``` html
<p style="color: red;">I'm learning to code!</p>
<p style="color: red; font-size: 20px;">I'm learning to code!</p>
<p style="font-family: Arial;">
```

### The style Tag（页内样式）
> To use the `<style>` element, it must be placed inside of the `<head>` element.
> 直接在本页面写CSS样式，所写的样式只会影响本页面，其他页面不会受到影响。

``` html
<head>
  <style>
    p {
      color: red;
      font-size: 20px;
    }
  </style>
</head>
```

### The .css file（外链样式）
> Developers avoid mixing code by storing HTML and CSS code in separate files (HTML files contain only HTML code, and CSS files contain only CSS code).

You can create a CSS file by using the `.css` file name extension, like so: `style.css`
通过载入的方式加载CSS样式，文件后缀名为`.css`，只要页面加载本CSS文件，那么这些页面都会受到影响。

```html
<head>
  <title>CSS样式</title>
  <link rel="stylesheet" type="text/css" href="style.css">
</head>
```

### Linking the CSS File
> When HTML and CSS code are in separate files, the files must be linked.
> `<link>`  a self-closing tag , to link HTML and CSS files together.placed within the head of the HTML file.  

``` html
<link href="https://www.codecademy.com/stylesheets/style.css" type="text/css" rel="stylesheet">
<link href="./style.css" type="text/css" rel="stylesheet">
<link href="style.css" type="text/css" rel="stylesheet">
```
- `href` — like the anchor element, the value of this attribute must be the address, or path, to the CSS file.
- `type` — describes the type of document that you are linking to (in this case, a CSS file). The value of this attribute should be set to `text/css`.
- `rel` — describes the relationship between the HTML file and the CSS file. Because you are linking to a stylesheet, the value should be set to `stylesheet`.


# CSS基础选择器

## 4种CSS基础选择器
### Tag Name（标签选择器）
> CSS can select HTML elements by using an element's tag name. A tag name is the word (or character) between HTML angle brackets.

```html
<style>
  p {  }
</style>

<body>
  <p>...</p>
</body>
```


### Class Name（class选择器）
> To select an HTML element by its class using CSS, a period (.) must be prepended to the class's name.

```html
<style>
.brand {
  text-transform: capitalize;
}
.green {
  color: green;
}

.bold {
  font-weight: bold;
}

.uppercase {
  text-transform: uppercase;
  font-family: cursive;
}
</style>


<body>
  <p class="brand">Sole Shoe Company</p>

  <!-- Multiple Classes -->
  <h1 class="green bold uppercase"> ... </h1>
</body>
```

### ID Name（ID选择器）
>If an HTML element needs to be styled uniquely (no matter what classes are applied to the element), we can add an ID to the element.

``` html
<style>
  #large-title { }
</style>

<body>
  <h1 id="large-title"> ... </h1>

<!-- 错误示范 -->
  <div id="kaka text">...</div>  
</body>
```

### 通用选择器
```html
<!-- 所有 -->
*{ font-size:40px; color:red; }
```

## 2种复合选择器
### Chaining Selectors
> Require an HTML element to have two or more CSS selectors at the same time.

``` HTML
  <h1 class="special coco">...</h1>
```

``` css
h1.special {

}
```

### Nested Elements
>  selecting elements that are nested within other HTML elements.

``` html
<ul class='main-list'>
  <li> ... </li>
  <li> ... </li>
  <li> ... </li>
</ul>
```
``` css
.main-list li {

}
```

## Chaining and Specificity

```css
p {
  color: blue;
}

.main p {
  color: red;
}
```
Both of these CSS rules define what a `p` element should look like. Since `.main p` has a class and a `p` tag as its selector, only the `p` elements inside the `.main` element will appear red.
This occurs despite there being another more general rule that states `p` elements should be blue.

## Important

```css
p {
  color: blue !important;
}

.main p {
  color: red;
}
```
The `!important` flag is only useful when an element appears the same way 100% of the time.
Since it's almost impossible to guarantee that this will be true throughout a project and over time,
it's best to avoid `!important`altogether.


## Specificity
> Specificity is the order by which the browser decides which CSS styles will be displayed.

** `!important`   >> ID   >>    class   >>   tag**


## Multiple Selectors
> In order to make CSS more concise, it's possible to add CSS styles to multiple CSS selectors all at once.
This prevents writing repetitive code.

``` css
h1 {
  font-family: Georgia;
}

.menu {
  font-family: Georgia;
}

==>

h1,
.menu {
  font-family: Georgia;
}
```



## Review CSS Selectors

-  CSS can change the look of HTML elements. In order to do this, CSS must select HTML elements, then apply styles to them.
-  CSS can select HTML elements by tag, class, or ID.
-  Multiple CSS classes can be applied to one HTML element.
-  Classes can be reusable, while IDs can only be used once.
-  IDs are more specific than classes, and classes are more specific than tags. That means IDs will override any styles from a class, and classes will override any styles from a tag selector.
-  Multiple selectors can be chained together to select an element. This raises the specificity, but can be necessary.
-  Nested elements can be selected by separating selectors with a space.
-  The `!important` flag will override any style, however it should almost never be used, as it is extremely difficult to override.
-  Multiple unrelated selectors can receive the same styles by separating the selector names with commas.


# CSS VISUAL RULES

## CSS Structure
> CSS declarations consist of a property and a value.

``` CSS
h1 {
  color: blue;
}
```
Property — the style of that element (i.e., size, color, etc.).
Value — the value of the property (i.e., 18px for size, blue for color, etc.).

## Opacity
> the measure of how transparent an element is.

```css
.overlay {
  opacity: 0.5;
}
```
1 representing 100%, or fully visible and opaque,
0 representing 0%, or fully invisible.

## Background Image
> change the background of an element.

``` css
.main-banner {
  background-image: url("https://www.example.com/image.jpg");
}

.main-banner {
  background-image: url("images/mountains.jpg");
}
```
The url should be a url to an image. The url can be a file within your project, or it can be a link to an external site.
To link to an image inside an existing project, you must provide a relative file path.



## Review Visual Rules
-  CSS declarations are structured into property and value pairs.
-  CSS can make an element transparent with the `opacity` property.
-  CSS can also set the background of an element to an image with the `background-image` property.

# The Box Model
## the Box Model

All elements on a web page are interpreted by the browser as "living" inside of a box.

1. `height`and`width`——the width and height of the content area.
2. `padding`  —  the amount of space between the content area and the border.
3. `border`  —the thickness and style of the border surrounding the content area and padding.
4. `margin`  —  the amount of space between the border and the outside edge of the element.
5. `overflow`

![屏幕快照 2017-09-23 15.38.20](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-23 15.38.20.png)



## Height and Width

```
p {
  height: 80px;
  width: 240px;
}
```

 `px` —— *pixels*,allow you to set the exact size of an element's box (width and height).

When the width and height of an element are set in pixels, it will be the same size on all devices — an element that fills a laptop screen will overflow a mobile screen.



## Borders

A *border* is a line that surrounds an element, like a frame around a painting.

1. `width` — The thickness of the border: pixels,`thin`, `medium`,  `thick`
2. `style` — The design of the border: `none`, `dotted`,  `solid`, [10 different styles](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style##Values).
3. `color` — The color of the border.  [140 built-in color keywords](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value).

```
p {
  border: 3px solid coral;
}


p.content-header {
  height: 80px;
  width: 240px;
  border: solid coral;
}
```

The default border is `medium none color`, where `color` is the current color of the element.



## Border Radius

shape of an element's box: square.

 `border-radius`

```
div.container {
  border: 3px solid rgb(22, 77, 100);
  border-radius: 5px;
}


div.container {
  height: 60px;
  width: 60px;
  border: 3px solid rgb(22, 77, 100);
  border-radius: 100%;
}
```



## Padding

 Padding is like the space between a picture and the frame surrounding it.

```
p.content-header {
  padding: 10px;
}

p.content-header {
  padding-bottom: 10px;
}

p.content-header {
  padding: 6px 11px 4px 9px;
}

p.content-header {
  padding: 5px 10px;
}
```

1. `padding-top`
2. `padding-right`
3. `padding-bottom`
4. `padding-left`
5. in a clockwise rotation.  top (6 px), right (11 px), bottom (4 px), left (9 px)
6. `5px` for the top and bottom sides of the content. `10px`, for the left and right sides of the content.



## Margins

```
p {
  border: 1px solid aquamarine;
  margin: 20px;
}

p {
  border: 3px solid DarkSlateGrey;
  margin-right: 15px;
}


p {
  margin: 6px 10px 5px 12px;
}

p {
  margin: 6px 12px;
}
```

1. `margin-top`
2. `margin-right`
3. `margin-bottom`
4. `margin-left`
5. top (6 pixels), right (10 pixels), bottom (5 pixels), left (12 pixels) sides of the box.
6. `6px`, for the top and bottom of the box. `12px`, sfor the left and right sides of the box.

## Auto

The `margin` property also lets you center content.

```
div {
  margin: 0 auto;
}
```

 `margin: 0 auto;` will center the `div`s in their containing elements.

 `0` sets the top and bottom margins to 0 pixels.

 `auto` value instructs the browser to adjust the left and right margins until the element is centered within its containing element.

 `div` elements in the example above should center within an element that fills the page, but this doesn't occur. Why?

In order to center an element, a width must be set for that element. Otherwise, the width of the div will be automatically set to the full width of its containing element, like the `<body>`, for example. It's not possible to center an element that takes up the full width of the page.

```
div.headline {
  width: 400px;
  margin: 0 auto;
}
```

In the example above, the width of the div is set to 400 pixels, which is less than the width of most screens. This will cause the div to center within a containing element that is greater than 400 pixels wide.



## Margin Collapse

 top and bottom margins, vertical margins, *collapse*,

Horizontal margins (left and right), like padding, are always displayed and added together.

For example, if two divs with ids `##div-one` and `##div-two`, are next to each other, they will be as far apart as the sum of their adjacent margins.

```
##img-one {
  margin-right: 20px;
}

##img-two {
  margin-left: 20px;
}
```

In this example, the space between the `##img-one` and `##img-two`borders is 40 pixels. The right margin of `##img-one` (`20px`) and the left margin of `##img-two` (`20px`) add to make a total margin of 40 pixels.

Vertical margins do not add. Instead, the larger of the two vertical margins sets the distance between adjacent elements.

```
##img-one {
  margin-bottom: 30px;
}

##img-two {
  margin-top: 20px;
}
```

In this example, the vertical margin between the `##img-one` and `##img-two` elements is 30 pixels. Although the sum of the margins is 50 pixels, the margin collapses so the spacing is only dependent on the `##img-one`bottom margin.

Study the graphic display to the right. Elements A and B have 20 pixels of horizontal margin, the sum of each element's margin. Elements A and C have 30 pixels of vertical margin — the top margin of element C.

![屏幕快照 2017-09-23 16.29.50](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-23 16.29.50.png)





## Minimum and Maximum Height and Width

1. `min-width` — ensures a minimum width of an element's box.
2. `max-width` — ensures a maximum width of an element's box.
3. `min-height` — ensures a minimum height for an element's box.
4. `max-height` — ensures a maximum height of an element's box.

```
p {
  min-width: 300px;
  max-width: 600px;
}

p {
  min-height: 150px;
  max-height: 300px;
}
```



## Overflow

All of the components of the box model comprise an element’s size. For example, an image that has the following dimensions is 364 pixels wide and 244 pixels tall.

-  300 pixels wide
-  200 pixels tall
-  10 pixels padding on the left and right
-  10 pixels padding on the top and bottom
-  2 pixels border on the left and right
-  2 pixels border on the top and bottom
-  20 pixels margin on the left and right
-  10 pixels margin on the top and bottom

The total dimensions (364px by 244px) are calculated by adding all of the vertical dimensions together and all of the horizontal dimensions together. Sometimes, these components result in an element that is larger than the parent's containing area.

How can we ensure that we can view all of an element that is larger than its parent's containing area?

The `overflow` property controls what happens to content that spills, or overflows, outside its box. It can be set to one of the following values:

-  `hidden` - when set to this value, any content that overflows will be hidden from view.
-  `scroll` - when set to this value, a scrollbar will be added to the element's box so that the rest of the content can be viewed by scrolling.
-  `visible` - when set to this value, the overflow content will be displayed outside of the containing element. Note, this is the default value.

```
p {
  overflow: scroll;
}
```

In the example above, if any of the paragraph content overflows (perhaps a user resizes their browser window), a scrollbar will appear so that users can view the rest of the content.

The overflow property is set on a parent element to instruct a web browser how to render child elements. For example, if a div’s overflow property is set to `scroll`, all children of this div will display overflowing content with a scroll bar.



## Resetting Defaults

User agent stylesheets often have default CSS rules that set default values for padding and margin.

```
* {
  margin: 0;
  padding: 0;
}
```

 `0` do not require a unit of measurement.



## Visibility

Elements can be hidden from view with the `visibility` property.

1. `hidden` — hides an element.
2. `visible` — displays an element.

```
<ul>
  <li>Explore</li>
  <li>Connect</li>
  <li class="future">Donate</li>
<ul>

.future {
  visibility: hidden;
}
```

users can still view the contents of the list item (e.g., `Donate`) by viewing the source code in their browser. the web page will *only* hide the contents of the element. It will still leave an empty space where the element is intended to display.

**Note:** What's the difference between `display: none` and `visibility: hidden`?

 `display: none` will be completely removed from the web page.

`visibility: hidden`  will not be visible on the web page, but the space reserved for it will.



## Review

1. The box model comprises a set of properties used to create space around and between HTML elements.
2. The height and width of a content area can be set in pixels or percentage.
3. Borders surround the content area and padding of an element. The color, style, and thickness of a border can be set with CSS properties.
4. Padding is the space between the content area and the border. It can be set in pixels or percent.
5. Margin is the amount of spacing outside of an element's border.
6. Horizontal margins add, so the total space between the borders of adjacent elements is equal to the sum of the right margin of one element and the left margin of the adjacent element.
7. Vertical margins collapse, so the space between vertically adjacent elements is equal to the larger margin.
8. `margin: 0 auto` horizontally centers an element inside of its parent content area, if it has a width.
9. The `overflow` property can be set to `display`, `hide`, or `scroll`, and dictates how HTML will render content that overflows its parent's content area.
10. The `visibility` property can hide or show elements.



## Box Model: Content-Box

Many properties in CSS have a default value and don't have to be explicitly set in the stylesheet.

 the default `font-weight` of text is `normal`

`box-sizing` property controls the type of box model the browser should use when interpreting a web page.

The default value of this property is `content-box`. This is the same box model that is affected by border thickness and padding.

![屏幕快照 2017-09-23 17.25.53](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-23 17.25.53.png)



## Box Model: Border-Box

 reset the entire box model and specify a new one: `border-box`.

```
* {
  box-sizing: border-box;
}
```

the universal selector (`*`) targets all elements on the web page and sets their box model to the `border-box` model.

avoids the dimensional issues that exist in the former box model you learned about.

In this box model, the height and width of the box will remain fixed. The border thickness and padding will be included inside of the box, which means the overall dimensions of the box do not change.

```
<h1>Hello World</h1>
```

```
 * {
  box-sizing: border-box;
}

h1 {
  border: 1px solid black;
  height: 200px;
  width: 300px;
  padding: 10px;
}
```

In the example above, the height of the box would remain at 200 pixels and the width would remain at 300 pixels. The border thickness and padding would remain entirely *inside* of the box.

![屏幕快照 2017-09-23 17.31.45](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-23 17.31.45.png)





## Review: Changing the Box Model

1. In the default box model, box dimensions are affected by border thickness and padding.
2. The `box-sizing` property controls the box model used by the browser.
3. The default value of the `box-sizing` property is `content-box`.
4. The value for the new box model is `border-box`.
5. The `border-box` model is not affected by border thickness or padding.

## Flow of HTML

A browser will render the elements of an HTML document that has no CSS from left to right, top to bottom, in the same order as they exist in the document. This is called the *flow* of elements in HTML.

In addition to the properties tha t it provides to style HTML elements, CSS includes properties that change how a browser *positions* elements. These properties specify where an element is located on a page, if the element can share lines with other elements, and other related attributes.

In this lesson, you will learn five properties for adjusting the position of HTML elements in the browser:

-  `position`
-  `display`
-  `z-index`
-  `float`
-  `clear`

Each of these properties will allow us to position and view elements on a web page. They can be used in conjunction with any other styling properties you may know.





## Position

![img](https://s3.amazonaws.com/codecademy-content/courses/web-101/unit-7/alex-clark-experiment/static.png)

```
.boxes {
  width: 120px;
  height: 70px;
}
```

block-level elements in the image above take up their own line of space and therefore don't overlap each other.   the default *position* for block-level elements.

1. `static` - the default value (it does not need to be specified)
2. `relative`
3. `absolute`
4. `fixed`

## Position: Relative

```
.box-bottom {
  background-color: DeepSkyBlue;
  position: relative;
}
```

Note that offset properties will not work if the position of the element is not set to `relative`.

```
.box-bottom {
  background-color: DeepSkyBlue;
  position: relative;
  top: 20px;
  left: 50px;
}
```

1. `top` - moves the element down.
2. `bottom` - moves the element up.
3. `left` - moves the element right.
4. `right` - moves the element left.

the div will be moved down 20 pixels and to the right 50 pixels from its default static position. The image below displays the new position of the box. The dotted line represents where the statically positioned (default) box was positioned.

![img](https://s3.amazonaws.com/codecademy-content/courses/web-101/unit-7/alex-clark-experiment/relative.png)

pixels, ems, percentages.



## Position: Absolute

`absolute` all other elements on the page will *ignore* the element and act like it is not present on the page.

the element will scroll out of view when a user scrolls.

```
.box-bottom {
  background-color: DeepSkyBlue;
  position: absolute;
  top: 20px;
  left: 50px;
}
```

The bottom box in this image (colored blue) is displaced from the top left corner of its container. It is 20 pixels lower and 50 pixels to the right of the top box.

If offset properties weren't specified, the top box would be entirely covered by the bottom box.



![img](https://s3.amazonaws.com/codecademy-content/courses/web-101/unit-7/alex-clark-experiment/absolute.gif)





## Position: Fixed

We can *fix* an element to a specific position on the page (regardless of user scrolling) by setting its position to `fixed`.

```
.box-bottom {
  background-color: DeepSkyBlue;
  position: fixed;
  top: 20px;
  left: 50px;
}
```

![img](https://s3.amazonaws.com/codecademy-content/courses/web-101/unit-7/alex-clark-experiment/fixed.gif)



## Z-Index

```
.box-top {
  background-color: Aquamarine;
}

.box-bottom {
  background-color: DeepSkyBlue;
  position: absolute;
  top: 20px;
  left: 50px;
}
```

`z-index` controls how far "back" or how far "forward" an element should appear on the web page.

accepts integer values,that instruct the browser on the order in which elements should be displayed on the web page.

```
.box-top {
  background-color: Aquamarine;
  position: relative;
  z-index: 2;
}

.box-bottom {
  background-color: DeepSkyBlue;
  position: absolute;
  top: 20px;
  left: 50px;
  z-index: 1;
}
```

 `.box-top` position to relative and the z-index to 2. the z-index property does *not* work on static elements.

The z-index of `2` moves the `.box-top` element forward, because it is greater than the `.box-bottom` z-index, `1`

![img](https://s3.amazonaws.com/codecademy-content/courses/web-101/unit-7/alex-clark-experiment/z-index.png)



## Inline Display

Every HTML element has a default `display` value that dictates if it can share horizontal space with other elements.

 Some elements fill the entire browser from left to right regardless of the size of their content.

Other elements only take up as much horizontal space as their content requires and can be directly next to other elements.

 `display` property: `inline`, `block`, and `inline-block`.

The default `display` for some tags, such as `<em>`, `<strong>`, and `<a>`, is called *inline*.

Inline elements have a box that wraps tightly around their content, only taking up the amount of space necessary to display their content and not requiring a new line after each element.

The height and width of these elements cannot be specified in the CSS document.

For example, the text of an anchor tag will, by default, be displayed on the same line as the text inside of an emphasize element.

Each of these will only be as wide as necessary to contain their content.

```
To learn more about <em>inline</em> elements, click <a href="##">here</a>.
```

 the `<em>` element is `inline`, because it displays its content on the same line as the content surrounding it, including the anchor tag.

 [inline elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)

The CSS `display` property provides the ability to make any element an inline element. This includes elements that are not inline by default such as paragraphs, divs, and headings.

```
h1 {
  display: inline;
}
```

change the display of all `<h1>` elements to `inline`. The browser will render `<h1>` elements on the same line as other inline elements immediately before or after them (if there are any).



## Block Display

**block-level elements** are not displayed in the same line as the content around them.

These elements fill the entire width of the page and, unless specified, are the height necessary to accommodate the content inside of them.

**block-level elements**:

heading elements (`<h1>` ~ `<h6>`), `<p>`, `<div>` , `<footer>`,[the MDN documentation](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements).

```
strong {
  display: block;
}
```

In the example above, all `<strong>` elements will be displayed on their own line, with no content directly on either side of them even though their contents may not fill the width of most computer screens.



## Inline-Block Display

`inline-block`. Inline-block display combines features of both inline and block elements.

appear next to each other and we can specify their dimensions

`width` , `height`

Images are the best example of default inline-block elements.

`div`s in the CSS below will be displayed on the same line and with the specified dimensions:

```
<div class="rectangle">
  <p>I’m a rectangle!</p>
</div>
<div class="rectangle">
  <p>So am I!</p>
</div>
<div class="rectangle">
  <p>Me three!</p>
</div>
```

```
.rectangle {
  display: inline-block;
  width: 200px;
  height: 300px;
}
```

`.rectangle` `div`s will all appear inline with a width of 200 pixels and height of 300 pixels, even though the text inside of them may not require 200 pixels by 300 pixels of space.



## Float

1. `left` - this value will move, or float, elements as far left as possible.
2. `right` - this value will move elements as far right as possible.

```
.boxes {
    width: 120px;
    height: 70px;
}

.box-bottom {
  background-color: DeepSkyBlue;
  float: right;
}
```

This works for static and relative positioned elements.

![img](https://s3.amazonaws.com/codecademy-content/courses/web-101/unit-7/alex-clark-experiment/float-right.png)

Floated elements must have a width specified, as in the example above. Otherwise, the element will assume the full width of its containing element, and changing the float value will not yield any visible results.



## Clear

 when multiple floated elements have different heights, it can affect their layout on the page.

Specifically, elements can "bump" into each other and not allow other elements to properly move to the left or right.

`clear`: specifies how elements should behave when they bump into each other on the page.

1. `left` — the left side of the element will not touch any other element within the same containing element.
2. `right` — the right side of the element will not touch any other element within the same containing element.
3. `both` — neither side of the element will touch any other element within the same containing element.
4. `none` — the element can touch either side.

```
div {
  width: 200px;
  float: left;
}

div.special {
  clear: left;
}
```

all divs on the page are floated to the left side. The div with class `special`did not move all the way to the left because a taller div blocked its positioning. By setting its `clear` property to `left`, the `special` div will be moved all the way to the left side of the page.



## Review: Layout

1. The `position` property allows you to specify the position of an element in three different ways.
2. When set to `relative`, an element's position is relative to its default position on the page.
3. When set to `absolute`, an element's position can be pinned to any part of the web page, but the element will still move out of view when the page is scrolled.
4. When set to `fixed`, an element's position can be pinned to any part of the web page. The element will remain in view no matter what.
5. The `z-index` of an element specifies how far back or how far forward an element appears on the page.
6. The `float` property can move elements as far left or as far right as possible on a web page.
7. You can clear an element's left or right side (or both) using the `clear` property.



## Color

-  [**Named colors**](https://msdn.microsoft.com/en-us/library/aa358802(v=vs.85).aspx)

   -   English words, **keyword colors**: `blue`, `black`, and `LimeGreen`
   -  total 147 named colors

-  *RGB*

   -  `rgb(7, 210, 50)`  a mix of red, green, blue
   -   have a decimal number value from 0 to 255, Each can be one of 256 values.
   -  `256 * 256 * 256 = 16,777,216`

-   [*HSL* ](http://dba.med.sc.edu/price/irf/Adobe_tg/models/images/hsl_top.JPG)

   -   `hsl(200, 20%, 50%)`   

   -  hue (the color itself, ranges from 0 to 360 ),  Red: 0,360; Green:120, Blue:240

   -  saturation (the intensity of the color, percentages )

   -  lightness (how light or dark a color is, percentages )

      ​


-  [Hexadecimal or hex colors](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value)

   -  Hexadecimal is a number system with has sixteen digits, 0 to 9 followed by "A" to "F".
   -   Each can be one of 256 values.`256 * 256 * 256 = 16,777,216`
   -  Hex:  `##` +  three or six characters.(values for red, blue and green), using hexadecimal numbers

   ```
   DarkSeaGreen: ##8FBC8F
   Sienna:       ##A0522D
   SaddleBrown:  ##8B4513
   Brown:        ##A52A2A
   Black:        ##000000 or ##000
   White:        ##FFFFFF or ##FFF
   Aqua:         ##00FFFF or ##0FF
   ```

   ​

-  Opacity and Alpha

   -   `hsla`   alpha, a decimal number from 0 (completely transparent) to 1 (opaque,non-transparent)

   ```
   color: hsla(34, 100%, 50%, 0.1);
   ```

   -  `rgba`

   ```
   color: rgba(234, 45, 98, 0.33);
   ```

   -   `rgba(0, 0, 0, 0)`    `transparent`

   ```
   color: transparent;
   ```



1. `color` - this property styles an element's foreground color.
2. `background-color` - this property styles an element's background color.

```
h1 {
  color: Red;
  background-color: Blue;
}
```





## Typography

## Font Family

The phrase "type of font" refers to the technical term [typeface](https://en.wikipedia.org/wiki/Typeface), or *font family*.

```
h1 {
  font-family: Garamond;
}

h1 {
  font-family: "Courier New";
}
```

1. The font specified in a stylesheet must be installed on a user's computer in order for that font to display when a user visits the web page.
2. The default typeface for all HTML elements is `Times New Roman`.
3. It's a good practice to limit the number of typefaces used on a web page to 2 or 3.
4. When the name of a typeface consists of more than one word, it's a best practice to enclose the typeface's name in quotes

## Font Size

To change the size of text on your web page

```
p {
  font-size: 18px;
}
```

`px` means pixels , a way to measure font size.



## Font Weight

 controls how bold or thin text appears.

```
p {
  font-weight: bold;
}

header {
font-weight: 800;
}

footer {
font-weight: 200;
}
```

By default, the `font-weight` of most text elements is set to `normal`.

Some elements, like headers, have built-in bold styling.

a numeric scale ranging from 100 to 900.

Valid values are multiples of 100 within this range such as `200` or `500`.

1. `400` is the default `font-weight` of most text.
2. `700` signifies a bold `font-weight`.
3. `300` signifies a light `font-weight`.

not all fonts can be assigned a numeric `font-weight`.



## Font Style

```
h3 {
  font-style: italic;
}
```

 `italic`

the default: `normal`



## Word Spacing

```
h1 {
  word-spacing: 0.3em;
}
```

The default:`0.25em`

the preferred unit is ems.



## Letter Spacing

kerning: increasing the spacing between individual letters.

```
h1 {
  letter-spacing: 0.3em;
}
```



## Text Transformation

```
h1 {
  text-transform: uppercase;
}
```

 `uppercase`

 `lowercase`



## Text Alignment

the default:  appears on the left side of the browser.

 `text-align` To align text

```
h1 {
  text-align: right;
}
```

1. `left` — aligns text to the left hand side of its parent element
2. `center` — centers text inside of its parent element.
3. `right` — aligns text to the right hand side of its parent element.



## Line Height Anatomy

 `line-height`: modifies the *leading* of text.

![屏幕快照 2017-09-23 23.32.09](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-23 23.32.09.png)

1. A unites number, such as `1.2`. This number is an absolute value that will compute the line height as a ratio of the font size.
2. A number specified by unit, such as `12px`. This number can be any valid CSS unit, such as pixels, percents, ems, or rems.

```
p {
  line-height: 1.4;
}
```



## Serif and Sans Serif

1. Serif — fonts that have extra details on the ends of each letter. Examples include fonts like Times New Roman or Georgia, among others.
2. Sans-Serif — fonts that do not have extra details on the ends of each letter. Instead, letters have straight, flat edges, like Arial or Helvetica.

![屏幕快照 2017-09-23 23.37.06](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-23 23.37.06.png)



## Fallback Fonts

Most computers have a small set of typefaces pre-installed:

serif fonts like Times New Roman

sans-serif fonts like Arial.

These pre-installed fonts serve as *fallback fonts* if the stylesheet specifies a font which is not installed on a user's computer.

```
h1 {
  font-family: "Garamond", "Times", serif;
}
```

1. Use the Garamond font for all `<h1>` elements on the web page.
2. If Garamond is not available, use the Times font.
3. If Garamond and Times are not available, use any serif font pre-installed on the user's computer.

The fonts specified after Garamond are the fallback fonts (`Times`, `serif`).



*non-user fonts*:  New fonts are often centralized in directories made available for public use.  

[Google Fonts](https://fonts.google.com/)

\1. A single linked font, using `Droid Serif` as an example:

```
<head>
  <link href="https://fonts.googleapis.com/css?family=Droid+Serif" type="text/css" rel="stylesheet">
</head>

.space .sample .text {
  font-family: "Space Mono", monospace;
}
```

\2. Multiple linked fonts, using the `Droid Serif` and `Playfair Display` fonts as an example:

```
<head>
  <link href="https://fonts.googleapis.com/css?family=Droid+Serif|Playfair+Display" type="text/css" rel="stylesheet">
</head>
```

\3. Multiple linked fonts, along with weights and styles. Here `Droid Serif` has font weights of `400`, `700`, and `700i`, while `Playfair Display` has font weights of `400`, `700`, and `900i`:

```
<head>
  <link href="https://fonts.googleapis.com/css?family=Droid+Serif:400,700,700i|Playfair+Display:400,700,900i" rel="stylesheet">
</head>
```

Once a font is linked, we can create CSS selectors to target elements, just as we do with other fonts.





## Font-Face

`@font-face`

1. Instead of using the font's link in the HTML document, enter the link into the URL bar in the browser.
2. The browser will load the CSS rules. You will need to focus on the rules that are directly labeled as `/* latin */`. Some of the latin rules are on separate lines. You will need each of these.
3. Copy each of the CSS rules labeled latin, and paste the rules from the browser to the top of **style.css**.

It important to stress the need to copy the `@font-face` rules to the top of the stylesheet for the font to load correctly in the project. [here](https://fonts.googleapis.com/css?family=Space+Mono:400,700/)

```
/* latin */
@font-face {
  font-family: 'Space Mono';
  font-style: normal;
  font-weight: 400;
  src: local('Space Mono'), local('SpaceMono-Regular'), url(https://fonts.gstatic.com/s/spacemono/v1/adVweg3BJhE6r8jYmXseHQzyDMXhdD8sAj6OAJTFsBI.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2212, U+2215;
}
```



```
@font-face {
  font-family: "Roboto";
  src: url(fonts/Roboto.woff2) format('woff2'),
       url(fonts/Roboto.woff) format('woff'),
       url(fonts/Roboto.tff) format('truetype');
}
```

1. The main difference is the use of a relative file path instead of a web URL.
2. We add a format for each file to specify which font to use. Different browsers support different font types, so providing multiple font file options will support more browsers.

As of now `.woff2` appears to be the way of the future, due to greatly reduced file sizes and improved performance, but many browsers still don’t support it. There are lots of great sources to find fonts to use locally, such as [Font Squirrel](https://www.fontsquirrel.com/).



```
@font-face {
  font-family: "Glegoo";
  src: url(../fonts/Glegoo-Regular.ttf) format('truetype');
}

.banner p {
  border-top: 1px solid ##fff;
  border-bottom: 1px solid ##fff;
  padding: 10px;
  color: ##ffffff;
  font-weight: bold;
  line-height: 1.4;
  font-family: "Glegoo";
  font-size: 20px;
}
```

-  The `font-family` property defines the typeface of an element.
-  `font-size` controls the size of text displayed.
-  `font-weight` defines how thin or thick text is displayed.
-  The `text-align` property places text in the left, right, or center of its parent container.
-  Text can have two different color attributes: `color`and `background-color`. `color` defines the color of the text, while `background-color` defines the color behind the text.

## Review

-  *Typography* is the art of arranging text on a page.
-  Text can appear in any number of weights, with the `font-weight`property.
-  Text can appear in italics with the `font-style` property.
-  The vertical spacing between lines of text can be modified with the `line-height` property.
-  *Serif* fonts have extra details on the ends of each letter. *Sans-Serif*fonts do not.
-  *Fallback fonts* are used when a certain font is not installed on a user's computer.
-  Google Fonts provides free fonts that can be used in an HTML file with the `<link>` tag or the `@font-face` property.
-  Local fonts can be added to a document with the `@font-face`property and the path to the font's source.
-  The `word-spacing` property changes how far apart individual words are.
-  The `letter-spacing` property changes how far apart individual letters are.
-  The `text-align` property changes where text horizontally on a page.

---

# IE浏览器的兼容

所谓的浏览器兼容问题，是指因为不同的浏览器对同一段代码有不同的解析，造成页面显示效果不统一的情况。在大多数情况下，IE6-IE8浏览器在Web发展中起到很大阻力，Web前端工程师写好的页面在Firefox、Chrome、Opera等主流浏览器下测试，基本没有什么问题，而在IE6-IE8浏览器下预览，又是另一番景象，本来规整的页面全乱了。

幸好随着HTML5的盛行，IE低版本的浏览器也逐渐退出舞台，所以现在很多网站也不再去考虑IE6-IE8低版本的浏览器，不过有些特殊的网站不得不考虑低版本浏览器，比如政府网站、教育系统网站，网站性质也决定了不得不兼容低版本浏览器，那么下面我们就介绍一下常见的IE低版本的兼容方式，如果你的客户网站不考虑低版本浏览器，你就可以完全忽略该节课了。

## 1.IE6双倍边距

产生因素：当元素有float属性，又有margin属性时，在IE6下面显示的margin的值是设置值的两倍。

解决方法：将有float属性的元素添加display:inline属性。

## 2.伪类选择器hover

产生因素：IE6只支持a标签的CSS定义hover效果，其他标签添加hover效果没有任何作用。

解决方法：一方面可以使用JavaScript添加鼠标移入效果，另一方面只能将其他标签改变为a标签后再添加hover效果。

## 3.定义元素的不透明度

产生因素：opacity:0.5，可以改变元素的透明度，取值范围是0~1，但是IE6不支持这种透明度表现方式。

解决方法：IE6浏览器专属的透明度属性， filter：alpha（opacity=80），取值范围是0~100。

## 4.IE各个版本hack

```css
/*属性hack方式*/

.box {_width:100px;}             /* IE6专用*/

.box {*+width:100px;}          /* IE7专用*/

.box {*width:100px;}            /* IE6、IE7共用*/

.box {width:100px\0;}           /* IE8、IE9共用*/

.box {width:100px\9;}           /* IE6、IE7、IE8、IE9共用*/

.box {width:330px\9\0;}        /* IE9专用*/


/*选择器hack*/

*html .box{width:100px;}       /*IE6*/

*+html .box{width:100px;}     /*IE7*/

```
---

# CSS3与CSS2.1的区别

## 什么是CSS3

CSS3是CSS2的一个升级版本，CSS3提供了非常多新途径去改善您的设计工作，且做了不少重要的变化，大部分的CSS3规范都重复了CSS2.1的内容，但也在它的基础上进行了很多增补和修订。

## CSS3新特性

总的来说CSS3主要拥有以下几个新的亮点：高级选择器，圆角，多背景，自定义字体，动画与过渡，渐变色，box阴影，rgba颜色表示，文字阴影，图形化边界等。

### 网页细节更易操作

在CSS3之前，如果想要在页面上添加圆角或阴影，只能通过图片的方式才能实现想要表达的效果，但是CSS3添加了“背景和边框”模块，比如常见的圆角、阴影、边框、背景都是该模块的，还有一个模块是"色彩和图像"，比如新增的rgba(0,0,0,0.5)增加了透明色。

### 字体多样化   

CSS3之前，Web设计师必须使用已在用户计算机上安装好的字体。通过CSS3，Web设计师可以使用他们喜欢的任意字体。当您找到或购买到希望使用的字体时，可将该字体文件存放到Web服务器上，它会在需要时被自动下载到用户的计算机上。

### 种类多样的选择器

CSS3新增了非常多的高级选择器，可用它们选取HTML结构中的特定片段而无需增加特定的ID或类，在CSS3之前想要选择特定的区块只能通过JS来选择，CSS3增加的这些选择器，能够很好的满足我们的需求，并且使用CSS3选择器代码更加简洁且不容易出错。

### 2D-3D转换

在CSS3中可以为任意元素添加2D的变形，我们能够对元素进行移动、缩放、转动、拉长或拉伸。转换是使元素改变形状、尺寸和位置的一种效果。3D转换是基于二维变换的相同属性，如果熟悉二维变换，会发现3D变形的功能和2D变换的功能类似。CSS3中的3D变换主要包括以下几种，如： 3D位移、 3D旋转、3D缩放、3D矩阵。

### 过渡和动画

CSS3中的过渡（transition）和动画（animation），都可以让页面增加动效，提高页面的视觉效果，但是这两种是有区分的，过渡（transition）是一种简单的动画，可以理解为从一种状态到另一种状态具有非常平滑的过渡效果，但是过渡需要有某些事件进行触发才可以进行动画，动画（animation）是无需事件触发就能完成特定的动画，现在页面上常见的动态效果基本都是CSS3的animation动画可以完成的。

### 媒体查询

用户浏览网页的设备越来越复杂，大屏幕电脑、平板、智能手机，以前做设计只针对大屏幕电脑分辨率，现在已经不太适合，因为移动端智能设备的普及。我们应该让我们的设计在不同的设备做出不同的响应，让用户不管使用什么样的设备访问网站都有一个不错的用户体验，完成这种网站的制作就需要使用CSS3的媒体查询，适应不同的设备显示。
