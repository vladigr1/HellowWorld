# CSS - Cascading Style Sheets

Although CSS is a different language than HTML, it’s possible to write CSS code directly within HTML code using inline styles.

```html

<p style="color: red;">I'm learning to code!</p>

```

HTML allows you to write CSS code in its own dedicated section with the \<style\> element.\
To use the \<style\> element, it must be placed inside of the \<head\> element.

```html
<head>
  <style>
    p {
      color: red;
      font-size: 20px;
    }
  </style>
</head>
```

**note**: Developers avoid mixing code by storing HTML and CSS code in separate files (HTML files contain only HTML code, and CSS files contain only CSS code). 

style.css
```html
p {
  font-family: Arial;
}
```

When HTML and CSS code are in separate files, the files must be linked. Otherwise, the HTML file won’t be able to locate the CSS code, and the styling will not be applied.

```html
<link href="https://www.codecademy.com/stylesheets/style.css" type="text/css" rel="stylesheet">
```

## Naming - Tag names & Class Selcetor & ID Name

A tag name is the word (or character) between HTML angle brackets.

HTML elements can have more than just a tag name; they can also have attributes. One common attribute is the class attribute. It’s also possible to select an element by its class attribute.\
To select an HTML element by its class using CSS, a period (.) must be prepended to the class’s name.\
It’s possible to add more than one class name to an HTML element’s class attribute.

If an HTML element needs to be styled uniquely (no matter what classes are applied to the element), we can add an ID to the element.\
CSS can select HTML elements by their id attribute. To select an id element, CSS prepends the id name with a hashtag (#).\
 **note**: ID is meant to style only one element. IDs override the styles of tags and classes. 

### Specificity

IDs are the most specific selector in CSS, followed by classes, and finally, tags.\
More specific CSS selector (.description h5), the more general selector of h5 will not take hold.

### Chaining Selectors

When writing CSS rules, it’s possible to require an HTML element to have two or more CSS selectors at the same time.\
Something like ` <div class="description"> ... `

## Nested Elements

In addition to chaining selectors to select elements, CSS also supports selecting elements that are nested within other HTML elements.\
Something like \<ul class='main-list'\>
  \<li\> ... \</li\>

## Multiple Selectors 

```css
h1, 
.menu {
  font-family: Georgia;
}
```

## Examples 

```css
p {
  font-family: Arial;
}
h1 {
  color: maroon;
}
.title{
  color:teal;
}
.uppercase{
  text-transform: uppercase;
}
.publish-time{
  color: gray;
}
.cursive{
  font-family: cursive;
}
.capitalize{
  text-transform: capitalize;
}
h2.destination{
  font-family: cursive;
}
.description h5{
  color: teal;
}
h5{
  color: rebeccapurple;
}
p,h5{
  font-family: Georgia;
}
```

## Properties

* font-family: Garamond;
* font-size: 18px;
* font-weight: bold;
* text-align: right; ( left, center, right ) 

* color: red;
* background-color: blue;
* opacity: 0.5;
* background-image: url("images/mountains.jpg");

`!important` can be applied to specific attributes instead of full rules. It will override any style no matter how specific it is. As a result, it should almost never be used.

## Box Model

All elements on a web page are interpreted by the browser as “living” inside of a box. This is what is meant by the box model.
![box modle](https://content.codecademy.com/courses/updated_images/diagram-boxmodel_Updated_1-01.svg)

The model includes the content area’s size (width and height) and the element’s padding, border, and margin. The properties include:

Element properties:
1. Width and height — specifies the width and height of the content area.
2. Padding — specifies the amount of space between the content area and the border.
3. Border — specifies the thickness and style of the border surrounding the content area and padding.
4. Margin — specifies the amount of space between the border and the outside edge of the element.

A border is a line that surrounds an element, like a frame around a painting. Borders can be set with a specific width, style, and color.\
You can modify the corners of an element’s border box with the border-radius property.\
Padding - The space between the contents of a box and the borders of a box is known as padding. Padding is like the space between a picture and the frame surrounding it.\
`padding: 6px 11px 4px 9px` correspond to the amount of padding in a clockwise rotation. In order, it specifies the amount of padding on the top (6 pixels), right (11 pixels), bottom (4 pixels), and left (9 pixels) sides of the content.\
Margin refers to the space directly outside of the box. The margin property is used to specify the size of this space.\
margin: 0 auto; will center the divs in their containing elements. The 0 sets the top and bottom margins to 0 pixels. The auto value instructs the browser to adjust the left and right margins until the element is centered within its containing element.\
**note**: vertical margins do not add. Instead, the larger of the two vertical margins sets the distance between adjacent elements.

Part of the Padding:
1. padding-top
2. padding-right
3. padding-bottom
4. padding-left

### min-max
1. min-width — this property ensures a minimum width of an element’s box.
2. max-width — this property ensures a maximum width of an element’s box.

### overflow

1. hidden - when set to this value, any content that overflows will be hidden from view.
2. scroll - when set to this value, a scrollbar will be added to the element’s box so that the rest of the content can be viewed by scrolling.
3. visible - when set to this value, the overflow content will be displayed outside of the containing element. Note, this is the default value.

### Resetting Defaults

All major web browsers have a default stylesheet they use in the absence of an external stylesheet.\
This affects how the browser displays HTML elements, which can make it difficult for a developer to design or style a web page.\
Many developers choose to reset these default values so that they can truly work with a clean slate.\
The code in the example above resets the default margin and padding values of all HTML elements. It is often the first CSS rule in an external stylesheet. 

```html
* {
  margin: 0;
  padding: 0;
}
```

## Visibility

Elements can be hidden from view with the visibility property.

The visibility property can be set to one of the following values:

1. hidden — hides an element.
2. visible — displays an element.

```css
p {
  height: 80px;
  width: 240px;
  border: solid coral;
  border-radius: 5px;
  border: 3px solid rgb(22, 77, 100);
  border-radius: 100%;
  padding: 10px;
  padding-bottom: 10px;
  padding: 6px 11px 4px 9px;
  padding: 6px 11px;
  margin-right: 15px;
  margin: 0 auto;
  overflow: scroll; 
  visibility: hidden;
}

```

## Changing the Box Model

The same can be said about the box model that browsers assume. In CSS, the box-sizing property controls the type of box model the browser should use when interpreting a web page.

The default value of this property is `content-box`. This is the same box model that is affected by border thickness and padding.
Box Model: Border-Box

Fortunately, we can reset the entire box model and specify a new one: border-box.

`border-box` for all HTML elements. This new box model avoids the dimensional issues that exist in the former box model you learned about.
```css
* {
  box-sizing: border-box;
}
```

## Display and Psitionging

The default position of an element can be changed by setting its position property. The position property can take one of four values:

1. static - the default value (it does not need to be specified)
2. relative
3. absolute
4. fixed

```css
.box-bottom {
  background-color: DeepSkyBlue;
  position: relative;
  top: 20px;
  left: 50px;
}
```

In the example above, the \<div\> has been positioned using two of the four offset properties. The valid offset properties are:

1. top - moves the element down.
2. bottom - moves the element up.
3. left - moves the element right.
4. right - moves the element left.

In the example above, the \<div\> will be moved down 20 pixels and to the right 50 pixels from its default static position.

When an element’s position is set to absolute all other elements on the page will ignore the element and act like it is not present on the page. The element will be positioned relative to its closest positioned parent element.

```css
.box-bottom {
  background-color: DeepSkyBlue;
  position: absolute;
  top: 20px;
  left: 50px;
}
```

In the example above, the .box-bottom \<div\> will be moved down and right from the top left corner of the view. If offset properties weren’t specified, the top box would be entirely covered by the bottom box.

When an element’s position is set to absolute, as in the last exercise, the element will scroll with the rest of the document when a user scrolls.

We can fix an element to a specific position on the page (regardless of user scrolling) by setting its position to fixed.

```css
.box-bottom {
  background-color: DeepSkyBlue;
  position: fixed;
  top: 20px;
  left: 50px;
}
```

In the example above, the .box-bottom \<div\> will remain fixed to its position no matter where the user scrolls on the page,

when boxes on a web page have a combination of different positions, the boxes (and therefore, their content) can overlap with each other, making the content difficult to read or consume.

```css
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

In the example above, the .box-bottom \<div\> ignores the .box-top \<div\> and overlaps it as a user scrolls.
The z-index property controls how far “back” or how far “forward” an element should appear on the web page when elements overlap. This can be thought of the depth of elements, with deeper elements appearing behind shallower elements.

The z-index property accepts integer values. Depending on their values, the integers instruct the browser on the order in which elements should be displayed on the web page.

```css
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

In the example above, we set the .box-top position to relative and the z-index to 2. We changed position to relative, because the z-index property does not work on static elements. The z-index of 2 moves the .box-top element forward, because it is greater than the .box-bottom z-index, 1. 

ome elements are not displayed in the same line as the content around them. These are called block-level elements. These elements fill the entire width of the page by default, but their width property can also be set. Unless otherwise specified, they are the height necessary to accommodate their content.

Elements that are block-level by default include all levels of heading elements (\<h1\> through \<h6\>), \<p\>, \<div\> and \<footer\>. For a complete list of block level elements, visit the MDN documentation.

strong {
  display: block;
}

In the example above, all \<strong\> elements will be displayed on their own line, with no content directly on either side of them even though their contents may not fill the width of most computer screens.

Inline-block display combines features of both inline and block elements. Inline-block elements can appear next to each other and we can specify their dimensions using the width and height properties. Images are the best example of default inline-block elements.

```css
.rectangle {
  display: inline-block;
  width: 200px;
  height: 300px;
}
```


If you’re simply interested in moving an element as far left or as far right as possible on the page, you can use the float property.

The float property can be set to one of two values:

1. left - this value will move, or float, elements as far left as possible.
2. right - this value will move elements as far right as possible.

```css
.box-bottom {
  background-color: DeepSkyBlue;
  float: right;
}
```

when multiple floated elements have different heights, it can affect their layout on the page. Specifically, elements can “bump” into each other and not allow other elements to properly move to the left or right.

The clear property specifies how elements should behave when they bump into each other on the page. It can take on one of the following values:

    left — the left side of the element will not touch any other element within the same containing element.
    right — the right side of the element will not touch any other element within the same containing element.
    both — neither side of the element will touch any other element within the same containing element.
    none — the element can touch either side.

```css
div {
  width: 200px;
  float: left;
}

div.special {
  clear: left;
}
```


### Let’s review what you’ve learned so far:

1. The position property allows you to specify the position of an element in three different ways.
2. When set to relative, an element’s position is relative to its default position on the page.
3. When set to absolute, an element’s position is relative to its closest positioned parent element. It can be pinned to any part of the web page, but the element will still move with the rest of the document when the page is scrolled.
4. When set to fixed, an element’s position can be pinned to any part of the web page. The element will remain in view no matter what.
5. The z-index of an element specifies how far back or how far forward an element appears on the page when it overlaps other elements.
6. The display property allows you control how an element flows vertically and horizontally a document.
7. inline elements take up as little space as possible, and they cannot have manually-adjusted width or height.
8. block elements take up the width of their container and can have manually-adjusted heights.
9. inline-block elements can have set width and height, but they can also appear next to each other and do not take up their entire container width.
10. The float property can move elements as far left or as far right as possible on a web page.
11. You can clear an element’s left or right side (or both) using the clear property.

## Color


Colors in CSS can be described in three different ways:

1. Named colors — English words that describe colors, also called keyword colors
2. RGB — numeric values that describe a mix of red, green, and blue
3. HSL — numeric values that describe a mix of hue, saturation, and lightness

1. color - this property styles an element’s foreground color.
2. background-color - this property styles an element’s background color.

```css
h1 {
  color: Red;
  background-color: Blue;
}
```

Hex color begins with a hash character (#) which is followed by three or six characters. The characters represent values for red, blue and green.

There is another syntax for representing RGB values that uses decimal numbers. It looks like this:

```css
h1 {
  color: rgb(23, 45, 23);
}
```
The syntax for HSL is similar to the decimal form of RGB, though it differs in important ways. The first number represents the degree of the hue, and can be between 0 and 360. The second and third numbers are percentages representing saturation and lightness respectively. Here is an example:

```css
color: hsl(120, 60%, 70%);
```

Hue is the first number. It refers to an angle on a color wheel. Red is 0 degrees, Green is 120 degrees, Blue is 240 degrees, and then back to Red at 360. You can see an example of a color wheel below:
color wheel

![Hue wheel](https://content.codecademy.com/courses/learn-css-color/color_wheel_4_background.svg)

Saturation refers to the intensity or purity of the color. If you imagine a line segment drawn from the center of the color wheel to the perimeter, the saturation is a point on that line segment. If you spin that line segment to different angles, you’ll see how that saturation looks for different hues. The saturation increases towards 100% as the point gets closer to the edge (the color becomes more rich). The saturation decreases towards 0% as the point gets closer to the center (the color becomes more gray).

Lightness refers to how light or dark the color is. Halfway, or 50%, is normal lightness. Imagine a sliding dimmer on a light switch that starts halfway. Sliding the dimmer up towards 100% makes the color lighter, closer to white. Sliding the dimmer down towards 0% makes the color darker, closer to black.

HSL is convenient for adjusting colors. In RGB, making the color a little darker may affect all three color components. In HSL, that’s as easy as changing the lightness value. HSL is also useful for making a set of colors that work well together by selecting various colors that have the same lightness and saturation but different hues.

To use opacity in the HSL color scheme, use hsla instead of hsl, and four values instead of three. For example:

```css
color: hsla(34, 100%, 50%, 0.1);
```

There is, however, a named color keyword for zero opacity, transparent. It’s equivalent to rgba(0, 0, 0, 0). It’s used like any other color keyword:

```css
color: transparent;
```
