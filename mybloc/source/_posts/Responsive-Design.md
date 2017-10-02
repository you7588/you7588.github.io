---
title: 响应设计（Responsive Design）
date: 2017-09-29 11:32:45
categories: 前端
tags: [前端]
---




# Sizing Elements

## Relative Measurements
Responsive design refers to the ability of a website to resize and reorganize its content based on:
1. The size of other content on the website.
2. The size of the screen the website is being viewed on.

## Em
> Historically, the em represented the width of a capital letter M in the typeface and size being used.   
> Today, the em represents the size of the base font being used.

```css
.heading {
  font-size: 2em;
}
```
if the base font of a browser is 16 pixels (which is normally the default size of text in a browser), then 1 em is equal to 16 pixels. 2 ems would equal 32 pixels, and so on.
```css
.splash-section {
  font-size: 18px;
}

.splash-section h1 {
  font-size: 1.5em;
}
```
If you're interested in sizing elements in comparison to other elements nearby, then the em unit would be better suited for the job.


## Rem

> **root em**. it checks the *root element*. The root element is the `<html>` tag.

Most browsers set the font size of `<html>` to 16 pixels, so by default rem measurements will be compared to that value. To set a different font size for the root element, you can add a CSS rule.

```css
html {
  font-size: 20px;
}

h1 {
  font-size: 2rem;
}
```

the font size of the root element, `<html>`, is set to 20 pixels. All subsequent rem measurements will now be compared to that value and the size of `h1` elements in the example will be 40 pixels.
If you are interested in sizing elements consistently across an entire website, the rem measurement is the best unit for the job.



## Percentages: Height & Width
> Percentages are often used to size box-model values, like width and height, padding, border, and margins. They can also be used to set positioning properties (top, bottom, left, right).

```css
.main {
  height: 300px;
  width: 500px;
}

.main .subsection {
  height: 50%;
  width: 50%;
}
```
Be careful, a child element's dimensions may be set erroneously if the dimensions of its parent element aren't set first.
**Note:** Because the box model includes padding, borders, and margins, setting an element's `width` to `100%` may cause content to overflow its parent container. While tempting, `100%` should only be used when content will not have padding, border, or margin.



## Percentages: Padding & Margin
> Vertical padding and margin are also calculated based on the width of the parent:

1. A container div is defined, but its height is not set (meaning it's flat).
2. The container then has a child element added within. The child element *does* have a set height. This causes the height of its parent container to stretch to that height.
3. The child element requires a change, and its height is modified. This causes the parent container's height to also stretch to the new height. This cycle occurs endlessly whenever the child element's height is changed!

For example, when a property like `margin-left` is set using a percentage (say `50%`), the element will be moved halfway to the right in the parent container (as opposed to the child element receiving a margin half of its parent's margin).
**Note:** When using relative sizing, ems and rems should be used to size text and dimensions on the page related to text size (i.e. padding around text). This creates a consistent layout based on text size. Otherwise, percentages should be used.



## Width&Height: Minimum & Maximum

1. `min-width` — ensures a minimum width for an element.
2. `max-width` — ensures a maximum width for an element.
3. `min-height` — ensures a minimum height for an element's box.
4. `max-height` — ensures a maximum height for an element's box.

```css
p {
  min-width: 300px;
  max-width: 600px;
  min-height: 150px;
  max-height: 300px;
}
```

**Note**: The unit of pixels is used to ensure hard limits on the dimensions of the element(s).


## Scaling Images and Videos

```css
.container {
  width: 50%;
  height: 200px;
  overflow: hidden;
}

.container img {
  max-width: 100%;
  height: auto;
  display: block;
}
```

## Scaling Background Images

```css
body {
  background-image: url('#');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```

by default, images will repeat


## Review: Relative Measurements
-  Content on a website can be sized relative to other elements on the page using *relative measurements*.
-  The unit of `em` sizes font relative to the font size of a parent element.
-  The unit of `rem` sizes font relative to the font size of a root element. That root element is the `<html>` element.
-  Percentages are commonly used to size box-model features, like the width, height, borders, padding, or margin of an element.
-  When percentages are used to size width and height, child elements will be sized relative to the dimensions of their parent (remember that parent dimensions must first be set).
-  Percentages can be used to set padding and margin. Horizontal and vertical padding and margin are set relative to the width of a parent element.
-  The minimum and maximum width of elements can be set using `min-width` and `max-width`.
-  The minimum and maximum height of elements can be set using `min-height` and `max-height`.
-  When the height of an image or video is set, then its width can be set to `auto` so that the media scales proportionally. Reversing these two properties and values will also achieve the same result.
-  A background image of an HTML element will scale proportionally when its `background-size` property is set to `cover`.


# Media Queries
## Media Queries
```css
@media only screen and (max-width: 480px) {
  body {
    font-size: 12px;
  }
}
```

1. `@media` — This keyword begins a media query rule and instructs the CSS compiler on how to parse the rest of the rule.
2. `only screen` — Indicates what types of devices should use this rule. In early attempts to target different devices, CSS incorporated different media types (screen, print, handheld). The rationale was that by knowing the media type, the proper CSS rules could be applied. However, “handheld” and “screen” devices began to occupy a much wider range of sizes and having only one CSS rule per media device was not sufficient. `screen` is the media type always used for displaying content, no matter the type of device. The `only` keyword is added to indicate that this rule only applies to one media type (`screen`).
3. `and (max-width : 480px)` — This part of the rule is called a *media feature*, and instructs the CSS compiler to apply the CSS styles to devices with a width of 480 pixels or smaller. Media features are the conditions that must be met in order to render the CSS within a media query.
4. CSS rules are nested inside of the media query's curly braces. The rules will be applied when the media query is met. In the example above, the text in the `body` element is set to a `font-size` of `12px` when the user's screen is less than 480px.



## Range

By using multiple widths and heights, a range can be set for a media query.

```
@media only screen and (min-width: 320px) and (max-width: 480px) {
    /* ruleset for 320px - 480px */
}
```

```
@media only screen and (min-width: 320px) {
    /* ruleset for 320px - 479px */
}


@media only screen and (min-width: 480px) {
    /* ruleset for > 480px */
}
```



## Dots Per Inch (DPI)

Another media feature we can target is screen resolution.

To target by resolution, we can use the `min-resolution` and `max-resolution` media features. These media features accept a resolution value in either [dots per inch (dpi)](https://en.wikipedia.org/wiki/Dots_per_inch) or dots per centimeter (dpc).

```
@media only screen and (min-resolution: 300dpi) {
    /* CSS for high resolution screens */
}
```

The media query in the example above targets high resolution screens by making sure the screen resolution is at least 300 dots per inch. If the screen resolution query is met, then we can use CSS to display high resolution images and other media.



## And Operator

The `and` operator can be used to require multiple media features.

```
@media only screen and (max-width: 480px) and (min-resolution: 300dpi) {
    /* CSS ruleset */
}
```

By placing the `and` operator between the two media features, the browser will require both media features to be true before it renders the CSS within the media query. The `and` operator can be used to chain as many media features as necessary.



## Comma Separated List

If only one of multiple media features in a media query must be met, media features can be separated in a comma separated list.

```css
@media only screen and (min-width: 480px), (orientation: landscape) {
    /* CSS ruleset */
}
```

we used a comma (`,`) to separate multiple rules. The example above requires only one of the media features to be true for its CSS to apply.

The `orientation` media feature detects if the page has more width than height. If a page is wider, it's considered `landscape`, and if a page is taller, it's considered `portrait`.



## Breakpoints

We know how to use media queries to apply CSS rules based on screen size and resolution, but how do we determine what queries to set?

The points at which media queries are set are called *breakpoints*. Breakpoints are the screen sizes at which your web page does not appear properly. For example, if we want to target tablets that are in landscape orientation, we can create the following breakpoint:

```css
@media only screen and (min-width: 768px) and (max-width: 1024px) and (orientation: landscape) {
    /* CSS ruleset */
}
```

The example above creates a screen size range the size of a tablet in landscape mode and also identifies the orientation.

Rather than set breakpoints based on specific devices, the best practice is to resize your browser to view where the website naturally breaks based on its content. The dimensions at which the layout breaks or looks odd become your media query breakpoints. Within those breakpoints, we can adjust the CSS to make the page resize and reorganize.

By observing the dimensions at which a website naturally breaks, you can set media query breakpoints that create the best possible user experience on a project by project basis, rather than forcing every project to fit a certain screen size. Different projects have different needs, and creating a responsive design should be no different.

Check out [this](https://s3.amazonaws.com/codecademy-content/courses/freelance-1/unit-5/screen-sizes.png) list of breakpoints by device widths. Use it as a reference of screen widths to test your website to make certain it looks great across a variety of devices.



## Review: Media Queries
-  When a website responds to the size of the screen it's viewed on, it’s called a *responsive* website.
-  You can write *media queries* to help with different screen sizes.
-  Media queries require *media features*. Media features are the conditions that must be met to render the CSS within a media query.
-  Media features can detect many aspects of a user's browser, including the screen's width, height, resolution, orientation, and more.
-  The `and` operator requires multiple media features to be true at once.
-  A comma separated list of media features only requires one media feature to be true for the code within to be applied.
-  The best practice for identifying where media queries should be set is by resizing the browser to determine where the content naturally breaks. Natural breakpoints are found by resizing the browser.

# Reference

[codecademy](https://www.codecademy.com)
