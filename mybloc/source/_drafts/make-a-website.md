---
title: make-a-website
date: 2017-09-29 12:24:57
tags:
---


**HTML**

Hyper Text Markup Language.

It is used to give websites structure with text, links, images, and other fundamental elements.

**CSS**

Cascading Style Sheets.

It is used to change the appearance of HTML elements.



## Anatomy of an HTML Element

```
<h1>You're Building a Website!</h1>
```

1. All HTML elements begin with an *opening tag*. In this case, the opening tag is `<h1>`.
2. Most elements require a *closing tag*, denoted by a `/`. In this case, the closing tag is `</h1>`.
3. The website user only sees the content between the opening and closing tags.

###### Add a Heading

###### Add a Paragraph

###### Anchor Elements

```
<a href="http://google.com"> Click here for Google!</a>
Here is a <a href="cities.html">list</a> of cities where you can find us.
```

 `http://google.com`, have a technical name: *URL*





## A Closer Look

1. Any valid URL can be used for the value of the `href` attribute.
2. The URL must be enclosed with quotation marks.
3. Text between the `<a>` and `</a>` tags can be as few or as many words as you would like.

![屏幕快照 2017-09-24 11.53.58](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-24 11.53.58.png)



## Adding Images

```
<img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-1/bikes1.jpg"/>
```

 Image URLs typically end with the .jpg or .png file extension.

The `src`attribute sets the *source* for an image element.

Image elements are *self-closing*,



## Add a Video

```
<video width="320" height="240" controls>
  <source src="video-url.mp4" type="video/mp4">
</video>
```

1. `width` and `height`: Set the size of the screen that displays the video.
2. `controls`: Adds play, pause and volume control.
3. `source src`: Sets the URL of the video to play.
4. `type`: Specifies different video formats.

## Create an Unordered List

*unordered list*. Items in an unordered list are referred to as *list items*.

 Each item is bulleted, not numbered.

-  A list item
-  A second list item
-  A third list item

```
<ul>
  <li>A list item</li>
  <li>A second list item</li>
  <li>A third list item</li>
</ul>
```

About unordered lists:

1. `ul` tags create the unordered list.
2. `li` tags contain each list item.

## Parent and Child Elements

these HTML elements had other HTML elements *nested* inside of them.

in unordered lists, `li` elements are nested inside the `ul`.

Web developers refer to the enclosing element as the *parent* element and the enclosed elements as *children*.

Referring to HTML elements as parents and children may sound funny, but it's a core web development concept.

The web browser also knows about these parent/child relationships

In the diagram to the right, notice the following:

1. The `ul` element is the parent of each `li`.
2. The `li` elements are children of the `ul`.
3. Code indentation signifies the relationship between parent and child elements.

![屏幕快照 2017-09-24 12.04.06](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-24 12.04.06.png)



## Add a Div

these concepts are applied on a real-life webpage.

*Div* elements divide your page by enclosing other elements.

These enclosed groups of elements can then be organized, moved and styled independently from one another.

Div elements are often used with the *class* attribute. Here's an example:

```
<div class="main">
 ...
</div>
```

**Note**: The `...` indicates where other HTML elements would normally be enclosed by the `div`.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Ollie Bike Sharing</title>
  <meta charset="utf-8"/>
  <link rel="stylesheet" type="text/css" href="main.css">
</head>

<body>
  <div class="container">
    <div class="nav">
  <h2>Ollie</h2>
  <ul>
  <li>sign up</li>
  <li>search bikes</li>
  <li>reserve a bike</li>
  <li>about us</li>
</ul>
    </div>>
<div class="main">
  <h1>Ollie Bike Sharing</h1>
  <h3>Share Your Pedals with the World.</h3>
  <p>Easy-to-use, free bike sharing now available in 27 cities.</p>
  <video width="320px" height="240" controls>
    <source src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-1/ollie.mp4" type="video/mp4">
  </video>
</div>
  </div>

</body>
</html>
```

![屏幕快照 2017-09-24 12.16.07](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-24 12.16.07.png)





## Metadata: The Brains

*metadata* processes.  the "brains" of a webpage because they communicate vital information to the web browser, but are not visible to a webpage visitor.

1. `<!DOCTYPE html>`: Tells the web browser to expect an HTML document.
2. `<html>...</html>`: The root of the HTML document and parent of all other HTML elements on the webpage.
3. `<head>...</head>`: Enclose other metadata about the site, such as its title.
4. `<title>...</title>`: Contains the site's title, which is one way users can find your site through a search engine, like Google.
5. `<meta charset="utf-8"/>`: Tells the web browser which character set to use. In this case, the character set is "utf-8".

## HTML Review

#### HTML ELEMENTS

-  *h1 - h6*: indicate text headings on a webpage. h1 is the largest heading; h6 is the smallest.

   ```
   <h1>Heading</h1>
   ```

-  *p*: used for non-heading text, such as the bodies of articles or company descriptions.

   ```
   <p>Description of company here.</p>
   ```

-  *a*: short for anchor and used to add links to other webpages. Anchor elements typically have an href attribute:

   ```
   <a href="http://codecademy.com">Click here</a> to learn how to make a website!
   ```

-  *img*: used to add an image to a webpage. Image elements are *self-closing* and do not require a closing tag:

   ```
   <img src="https://images.com/favorite.png">
   ```

-  *video*: used to add videos to a webpage, and uses multiple attributes and a nested source element:

   ```
   <video width="320" height="240" controls>
     <source src="https://movies.io/great-clip.mp4" type="video/mp4">
   </video>
   ```

-  *unordered list*: used to create lists on a webpage and requires li elements inside a ul:

   ```
   <ul>
     <li>list item</li>
     <li>another item</li>
     <li>yet another</li>
   </ul>
   ```

-  *div*: used to organize HTML elements into different groups, which can be given a class attribute:

   ```
   <div class="main">
     <h2>Subheading!</h2>
   </div>
   ```

-  *metadata tags*: provide metadata about a webpage.

#### WEB CONCEPTS

-  **parent/child elements**: used to describe HTML elements that enclose or are enclosed by other elements. For example, below the ul is the parent and the li items are children:

   ```
   <ul>
     <li>...</li>
     <li>...</li>
     <li>...</li>
   </ul>
   ```



`<head>...</head>`

The head element contains website metadata such as title and link elements, and is not visible to site visitors.



Div elements are commonly used for organize groups of HTML elements

Divs can be used to create logical divisions of HTML elements, such as "nav" or "main".



HTML  

It provides the structure for websites

HTML gives a website essential structure. Take for example, headings, paragraphs, divs and lists.



src, href and class are all...Attributes



Which HTML element is like the headline in a newspaper?

Headings, such as h1 and h3, display large and bold text.



# Link to a Stylesheet

The HTML *link* element links a CSS file to an HTML file so that CSS styling can be applied. Here's an example of the link element:

```
<link rel="stylesheet" type="text/css" href="main.css"/>
```

1. The link element uses three attributes:
   -`rel`:  the *relationship* between the current file and the file being linked to: in this case, the `rel` attribute is "stylesheet".
   -`type`:  the type of file linked to.
   -`href`: Provides the URL of the file being linked to.
2. Like the HTML image element, link is self-closing. It does not need a closing tag.





# Anatomy of a CSS Rule

1. *rule*: a list of CSS instructions for how to style a specific HTML element or group of HTML elements.
2. *selector*: specifies exactly which HTML elements to style. Here `h1` is the selector.
3. *properties* and *values*: located inside the `{ }` brackets, properties and values specify what aspect of the selector to style. In the diagram's example, the `color` property is set to `red`, which will display all `h1` elements in red.

![屏幕快照 2017-09-24 12.43.20](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-24 12.43.20.png)





###### font-family

###### color

*Hexadecimal color (#RRGGBB)*

###### CSS Class Selectors

```
<div class="header">
  <h2>Heading</h2>
  <p>Paragraph</p>
</div>
```

Here, the `div` is the parent element and the `h2` and `p` are children. CSS styles applied to the `header` *class selector* will automatically apply to the `h2` and the `p`.

[Here's a refresher](https://www.codecademy.com/en/courses/make-a-website/lessons/site-structure/exercises/parent-child) on **parent and child elements.**

```
.header {
  color: #ffffff;
}
```

###### font-size

```
h1 {
  font-size: 60px;
}
```

size can be assigned in *pixels* (px), *rems*, or *ems*.

-  *pixel (px)*: Standard unit of measurement for sizing fonts and other HTML elements.
-  *rem*: Represents the default font size for the web browser. Rems can be used to ensure that HTML elements scale in proportion to each other on various web browsers and screen sizes. On most web browsers, `1rem` is equivalent to `16px`, `2rem` is equivalent to `32px` (a doubling), 3rem is equivalent to `48px` (a tripling) and so on.
-  *em*: A relative value that changes in proportion to the size of the parent element. For example, if a parent element has `font-size: 20px;`, child elements with `font-size: 1em;` would be equivalent to `20px`. Child elements with `font-size: 0.5em;` would be equivalent to `10px` (a halving) and so on.

#### A Background Image

```
.hero {
  background-image: url("https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-2/bg.jpg");
  background-size: cover;
}
```



# css-review



#### WEB CONCEPTS

-  *CSS*: Language used to style websites. Colors, fonts, and page layouts for a site are managed using CSS.
-  *CSS Selectors*: specifies exactly which HTML elements to style
   -  *class selectors*: used to target classes of HTML elements
   -  *id selectors*: used to style an HTML element which has an id attribute.
-  *External Stylesheet*: CSS file that styles an HTML file externally via the HTML `link`element.

#### CSS PROPERTIES

-  *font-family*: sets font for a CSS selector.
-  *color*: sets font color for the CSS selector.
-  *font-size*: sets font size for text.
-  *background-image*: sets a background image of your choosing for a given selector.

# BOUNDARIES AND SPACE

#### Create a Border

*border* ——visually define a page element's outer edge.

1. *thickness*: using pixels, ems, or rems.
2. *type*: Common options are `solid`, `dotted`, and `dashed`.
3. *color*: using named colors, HEX, or RGB values.

#### Working with Padding

*padding* ——controls the empty space between the page element's content and its border.

```
p {
  padding: 20px;
}
```



#### Working with Margin

*margin* —— controls the space between different HTML elements on a webpage.

```
.answer {
  margin: 2rem;
} d
```



#### DISPLAY

*Display types*  determine how HTML elements will be arranged in relation to each other.

1. The two dotted rectangles represent webpages.
2. HTML heading, paragraph, and unordered list elements are block level: each appears on its own line on the webpage.
3. HTML image and anchor elements are displayed inline: they appear on the same line as their neighboring elements on the webpage.

![屏幕快照 2017-09-24 14.55.09](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-24 14.55.09.png)





# Keep It Inline

Display types can be overwritten in CSS by using the *display* property.For example, we can make list items appear on the same line by setting display to `inline`:

```
li {
  display: inline;
}
```

 Navs are used to organize site navigation menus on a webpage.



# Using Float

The class selector, `.logo`, floats `left`, and the id selector `#search-bar` floats `right`:

```
.logo {
  float: left;
}

#search-bar {
  float: right;
}
```



## Display: Flex

flex can be used to easily align multiple page elements horizontally.

```
<div class="parent">
   ...
</div>
```

To make children of the div align horizontally on the webpage,

```
.parent {
  display: flex;
}
```

We can make sure no child element moves off the page by using `flex-wrap: wrap;`:

```
.parent {
  display: flex;
  flex-wrap: wrap;
}
```

 to center rows of children elements, we can use `justify-content: center;`:

```
.parent {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
```



## Working with Position

 *position* ——to position HTML elements in exact locations on a webpage.

 *relative*—— relative to where they would normally appear.

1. `position: relative;`
2. `top`, `left`, `bottom`, and `right` to shift an element away from where it would have normally appeared on the page.

```
.container {
  position: relative;
  top: 10px;
  left: 20px;
}
```



# Review



#### WEB CONCEPTS

-  *CSS Box Model*: illustrates the space and boundary properties of an HTML element that can be controlled using CSS.

#### CSS SKILLS

-  *border*: sets the outline of an HTML page element, like a picture frame that contains the element.
-  *padding*: sets the amount of space between an element's content and its border.
-  *margin*: sets the amount of space between an HTML element and the next nearest element(s).
-  *display*: property that determines how the selected element will be arranged in relation to other HTML elements on the page.
-  *inline*: display value used to arrange HTML elements on the same line as neighboring elements.
-  *flex*: display value that allows us to easily align multiple page elements vertically or horizontally.
-  *float*: property used to float HTML elements left or right of neighboring elements.
-  *position*: property used to position HTML elements in exact locations on a webpage.



# CSS Frameworks

*Bootstrap* is a popular CSS framework with *prewritten* CSS rules designed to help you build webpages faster.



# Bootstrap

The HTML link element makes Bootstrap available to us.

```
<head>
  ...
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css"/>
  ...
</head>
```



# On the Grid

One of the reasons Bootstrap and frameworks like it are so popular is because they offer *grids*.

A *grid* makes it possible to organize HTML elements using preconfigured columns. Using a grid, you can customize responsive page layouts quickly and reliably.

The Bootstrap grid contains *12 equal-sized columns*, as seen in the diagram on the right. HTML elements are arranged to span different numbers of columns in order to create custom page layouts.



In the diagram, observe the following:

1. Bootstrap's grid columns are represented by 12 vertical bars. The boxes represent HTML elements.
2. The words "container", "jumbotron", "col-sm-6" and "col-sm-3" refer to Bootstrap classes.
3. The element with class "jumbotron" spans the entire width of the webpage, beyond the borders of the grid.
4. Elements inside the second "container", such as "col-sm-6" and "col-sm-3" are contained within the grid columns.
5. Elements labeled "col-sm-3" take up three grid columns; elements labeled "col-sm-6" take up six grid columns.

![屏幕快照 2017-09-24 16.45.49](/Users/chenxiaomin/Desktop/屏幕快照 2017-09-24 16.45.49.png)



# Header/Navigation

an HTML *header* element with Bootstrap's predefined `container` class is used:

Inside the header, a row is created by using a div with Bootstrap's `row`class:

Finally, the row is cut into two parts:

```
<header class="container">
  <div class="row">
   <h1 class="col-sm-4">Heading</h1>
   <nav class="col-sm-8 text-right">
    <p>nav item 1</p>
    <p>nav item 2</p>
    <p>nav item 3</p>
   </nav>
 </div>
</header>
```



# The Jumbotron

`jumbotron`  ——  a large showcase area featuring important content.

Bootstrap refers to this as a *jumbotron*. Below is an example implementation of a jumbotron.

```
<section class="jumbotron">
  <div class="container">
    <div class="row text-center">
      <h2>Homemade Goods</h2>
      <h3>This Year's Best</h3>
      <a class="btn btn-primary" href="#" role="button">See all</a>
    </div>
  </div>
</section>
```

The `...` is a placeholder for where text elements will go next.

The anchor element's `href` attribute, `#`, is a placeholder for an actual URL.



# Supporting Content

 Supporting content can be arranged using Bootstrap's grid.

First, an HTML section element with the `container`class is used:

Next, div elements with the `row` class are added:

Finally, the rows are divided by using divs with Bootstrap's `col-sm-...` class.

```
<section class="container">
  <div class="row">
    <div class="col-sm-6">
     ...
    </div>
    <div class="col-sm-6">
     ...
    </div>
  </div>
  <div class="row">
    <div class="col-sm-6">
     ...
    </div>
    <div class="col-sm-6">
     ...
    </div>
  </div>
</section>
```

Above, two rows are divided into two equal parts.

Each part takes up 6 of bootstrap's 12 columns.

Using the `col-sm-6` class ensures that this layout will appear when the user's screen is the width of a tablet device(768 pixels).

On narrower screens, such as an iPhone, only one image per row will appear.





# Footers

First, a footer element with Bootstrap's `container` class is used:

Inside the footer, a div with Bootstrap's `row` class is added to hold footer content:

Finally, the row is divided into parts using Bootstrap's grid.

```
<footer class="container">
  <div class="row">
    <p class="col-sm-4">&copy; 2016 Skillfair</p>

    <ul class="col-sm-8">
  <li class="col-sm-1">...</li>
  <li class="col-sm-1">...</li>
  <li class="col-sm-1">...</li>
  <li class="col-sm-1">...</li>

    </ul>
  </div>
</footer>
```

Above, the row is broken into three parts:

a `p` element that takes up four columns,

a `ul` which takes up 8 columns,

and `li` items which take up 1 column each.

The `li`s could hold navigation menu items or social media icons.

Again, because the `col-sm-...` class is used, this layout will appear on tablet-width screens and wider. Screen sizes smaller than tablet-width (768 pixels), will not maintain this layout.

`&copy` is a *character code*, which web browsers interpret as the copyright symbol: ©.





# Bootstrap Generalizations

#### WEB CONCEPTS

-  *CSS Framework*: Set of prewritten CSS rules designed to help you build webpages faster.
-  *Bootstrap Grid*: 12 equal-sized columns which can be utilized via Bootstrap classes to build responsive page layouts quickly and reliably.

#### BOOTSTRAP CLASSES

-  *row*: Arranges HTML elements in rows, and can be useful when building headers/navigation menus, main feature sections, supporting content sections and footers.
-  *jumbotron*: Used to create large showcase sections featuring important content.
-  *col-sm-\**: Used to span a specified number of columns on the Bootstrap grid. The "sm" is short for "small", and maintains desired CSS layouts on small screens (tablet-sized).
-  *text-right*: Bootstrap class used to orient text to the right side of the webpage.
-  *btn btn-primary*: Bootstrap class used to style page elements as buttons.





```
<!DOCTYPE html>
<html>
<head>
  <title>Skillfair</title>
  <meta charset="utf-8"/>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">
  <link href='https://fonts.googleapis.com/css?family=Roboto:300,400,700' rel='stylesheet' type='text/css'>
  <link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>
<header class="container">
  <div class="row">
    <h1 class="col-sm-4">Skillfair</h1>
    <nav class="col-sm-8 text-right">
      <p>newest</p>
      <p>catalogue</p>
      <p>contact</p>
    </nav>
 </div>
</header>
<section class="jumbotron">
  <div class="container">
    <div class="row text-center">
      <h2>Homemade Goods</h2>
      <h3>This Year's Best</h3>
      <a class="btn btn-primary" href="#" role="button">See all</a>
    </div>
  </div>
</section>
<section class="container">
  <div class="row">
    <figure class="col-sm-6">
    <p>kitchen</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/kitchen.jpg"/>
    </figure>
    <figure class="col-sm-6">
    <p>woodwork</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/woodwork.jpg"/>
    </figure>
  </div>
  <div class="row">
    <figure class="col-sm-6">
    <p>gifts</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/gifts.jpg"/>
    </figure>
    <figure class="col-sm-6">
    <p>antiques</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/antique.jpg"/>
    </figure>
  </div>
</section>
<footer class="container">
  <div class="row">
    <p class="col-sm-4">&copy; 2016 Skillfair</p>

    <ul class="col-sm-8">
  <li class="col-sm-1">...</li>
  <li class="col-sm-1">...</li>
  <li class="col-sm-1">...</li>
  <li class="col-sm-1">...</li>

    </ul>
  </div>
</footer>
</body>
</html>
```
