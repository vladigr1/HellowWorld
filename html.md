# HTML 

HTML is hyper text markup language:
* A markup language is a computer language that defines the structure and presentation of raw text.
* HyperText is text displayed on a computer or device that provides access to other text through links, also known as hyperlinks.

html element is `<text>`\
an openning tag `<p>`\
a closing tag `</p>`

## Body Element
The body element only content inside the opening and closing body tags can be displayed to the screen.
```html
<body>

</body>
```

### HTML Structure

When an element is contained inside another element, it is considered the child of the element. the chile lement is said to be nested inside of the parent element.
Understanding HTML hierarchy is important because child elements can inherit behavior and styling form their parnet element.

## Divs

`<div>` element is shor for "division", vert useful for grouping elemnts in your HTML together.\
`<div>` don't inherntly have visual representation, but they are very usefull when we want to aplly custom style to our HTML.
`<div>` can contain any text or other HTML elements, such as links,images, or videos.

**note**: add two space of indentation when you nest elements inside of `<div>` for better readability.

## Attributes

expand an element's tag, we can do so using _attribute_.\
_Attribute_ are content added to the opening tag of element.

```html
<div id = "intro">
  <h1>Introduction</h1>
</div>
```

## Display Text

* `<p>` == Paragraphs (`<p>`) contain a block of plain text.
* `<span>` == short pieces of text or other HTML. They are used to separate small pieces of content that are on the same line as other content.

```html
<div>
  <p><span>Self-driving cars</span> are anticipated to replace up to 2 million jobs over the next two decades.</p>
</div>
```

### Styling Text

`<em>` tag emphasizes text(italic).\
`<strong>` highlights important text(bold).\
`<br>` line break.

### Lists

same format :
```html
<ul>
  <li>Limes</li>
  <li>Tortillas</li>
  <li>Chicken</li>
</ul>
```

`<ul>` unordered list\
`<ol>` ordered list

## Table

* `<table border = "1">` == create table with border
* `table, td { border: 1px solid black; }` == css border version
* `<tr> </tr>` == rows
* `<td> </td>` == in row wirte column
* `<td colspan="2">` == span to two columns 
* ` <td rowspan="2">` == span to two rows
* `<th> scope="col> ..</th>` == table heading element, just like table data element
* `<tbody> <\/tbody>` == this element should contain all of the table’s data, excluding the table headings 
* `<thead>` ==  The table headings are contained inside of this element.\
  Note that the table’s head still requires a row in order to contain the table headings.
* `<tfoot>` == footer contains the totals of the data in the table.\
  Footers are often used to contain sums, differences, and other data results.

## Form

`<form>` == element which  is a great tool for collecting information, but then we need to send that information somewhere else for processing.\
`<form action="/example.html" method="POST">`

* `<input type="text" name="username" value="already pre-filled">` == input field
* `<label for="username">What do you want to eat?</label>` == label

```html
<!-- input password -->
<form>
  <label for="user-password">Password: </label>
  <input type="password" id="user-password" name="user-password">
</form>

```

* `<input id="years" name="years" type="number" step="1">` == number input
* `<input id="volume" name="volume" type="range" min="0" max="100" step="1">` == range input (slider)

```html

<!-- input checkbox -->

<form>
  <p>Choose your pizza toppings:</p>
  <label for="cheese">Extra cheese</label>
  <input id="cheese" name="topping" type="checkbox" value="cheese">
  <br>
  <label for="pepperoni">Pepperoni</label>
  <input id="pepperoni" name="topping" type="checkbox" value="pepperoni">
  <br>
  <label for="anchovy">Anchovy</label>
  <input id="anchovy" name="topping" type="checkbox" value="anchovy">
</form>

```

```html

<!-- radio-box -->

<form>
  <p>What is sum of 1 + 1?</p>
  <input type="radio" id="two" name="answer" value="2">
  <label for="two">2</label>
  <br>
  <input type="radio" id="eleven" name="answer" value="11">
  <label for="eleven">11</label>
</form>

```

```html

<!-- drop-down -->
<form>
  <label for="lunch">What's for lunch?</label>
  <select id="lunch" name="lunch">
    <option value="pizza">Pizza</option>
    <option value="curry">Curry</option>
    <option value="salad">Salad</option>
    <option value="ramen">Ramen</option>
    <option value="tacos">Tacos</option>
  </select>
</form>

```
**note**: data-list is list of option you must choose from them 

```html

<!-- data-list -->
<form>
  <label for="city">Ideal city to visit?</label>
  <input type="text" list="cities" id="city" name="city">

<!-- data-list element -->

  <datalist id="cities">
    <option value="New York City"></option>
    <option value="Tokyo"></option>
    <option value="Barcelona"></option>
    <option value="Mexico City"></option>
    <option value="Melbourne"></option>
    <option value="Other"></option>  
  </datalist>
</form>

```

```html

<!-- text-area -->

<form>
  <label for="blog">New Blog Post: </label>
  <br>
  <textarea id="blog" name="blog" rows="5" cols="30">
  </textarea>
</form>

```

```html

<!-- submit -->
<form>
  <input type="submit" value="Send">
</form>
```

### Form Validation

`required` enforce this rule

```html
<!-- required input -->
<form action="/example.html" method="POST">
  <label for="allergies">Do you have any dietary restrictions?</label>
  <br>
  <input id="allergies" name="allergies" type="text" required>
  <br>
  <input type="submit" value="Submit">
</form>
```

```hyml
<!-- max min numbers -->
<form action="/example.html" method="POST">
  <label for="guests">Enter # of guests:</label>
  <input id="guests" name="guests" type="number" min="1" max="4">
  <input type="submit" value="Submit">
</form>
```

```html
<!-- text length check -->
<form action="/example.html" method="POST">
  <label for="summary">Summarize your feelings in less than 250 characters</label>
  <input id="summary" name="summary" type="text" minlength="5" maxlength="250" required>
  <input type="submit" value="Submit">
</form>
```

#### Matching a pattern using reggex

```html
<!-- matching a pattern -->
<form action="/example.html" method="POST">
  <label for="payment">Credit Card Number (no spaces):</label>
  <br>
  <input id="payment" name="payment" type="text" required pattern="[0-9]{14,16}">
  <input type="submit" value="Submit">
</form>
```

## HTML Files

using the tag `<!DOCTYPE html>` will declare the file HTML file. along with what verison is being used (HTML5).\
The `<html> </html>` tags create HTML structure and content.

### Metadata of the file

the `<head> </head>` element contains the metadata for the web page.\
the data which can enter in the metadata section:

* `<title>` == a browser's tab displays the title.

## Semantic HTML

The word semantic means “relating to meaning,” so semantic elements provide information about the content between the opening and closing tags.
![sematic web](https://content.codecademy.com/courses/updated_images/SemanticVSNonSemantic_Diagram_Updated_1.svg)

* `<header>` is a container usually for either navigational links or introductory content containing `<h1>` to `<h6>` headings.

```html
<header>
  <h1>
     Everything you need to know about pizza!
  </h1>
</header>
```

This can be compared to the code below which uses a <div> tag instead of a <header> tag:

```html
<div id="header">
  <h1>
    Everything you need to know about pizza!
  </h1>
</div>
```

 * `<nav>` is used to define a block of navigation links such as menus and tables of contents. It is important to note that `<nav>` can be used inside of the `<header>` element but can also be used on its own.\
Let’s take a look at the example below:

```html
<header> 
  <nav>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>      
    </ul>
  </nav>
</header>
```

* The element <main> is used to encapsulate the dominant content within a webpage.
* The content at the bottom of the subject information is known as the footer, indicated by the <footer> element. The footer contains information such as:
  1. Contact information
  2. Copyright information
  3. Terms of use
  4. Site Map
  5. Reference to top of page links
  For example:
  ```html
  <footer>
    <p>Email me at Codey@Codecademy.com</p>
  </footer>
  ```

let’s focus on what can go in the body. The two elements we’re going to focus on now are `<section>` and `<article>`.
* `<section>` defines elements in a document, such as chapters, headings, or any other area of the document with the same theme. For example, content with the same theme such as articles about cricket can go under a single `<section>`. A website’s home page could be split into sections for the introduction, news items, and contact information.\
  Here is an example of how to use `<section>`:

```html
<section>
  <h2>Fun Facts About Cricket</h2> 
</section>
```
* The <article> element holds content that makes sense on its own. <article> can hold content such as articles, blogs, comments, magazines, etc. An <article> tag would help someone using a screen reader understand where the article content (that might contain a combination of text, images, audio, etc.) begins and ends.\
  Used along with othe elments like `<section>` and `<article>`.\
  Here is an example of how to use <article>:

```html
<section>
  <h2>Fun Facts About Cricket</h2>
  <article>
    <p>A single match of cricket can last up to 5 days.</p>
  </article>
</section>
```

* The `<aside>` element is used to mark additional information that can enhance another element but isn’t required in order to understand the main content.\
  Some common uses of the `<aside>` element are for:
  1. Bibliographies
  2. Endnotes
  3. Comments
  4. Pull quotes
  5. Editorial sidebars
  6. Additional information
  Here’s an example of `<aside>` being used alongside `<article>`:

```html
<article>
  <p>The first World Series was played between Pittsburgh and Boston in 1903 and was a nine-game series.</p>
</article>
<aside>
  <p>
   Babe Ruth once stated, “Heroes get remembered, but legends never die.” 
  </p>
</aside>
```

* `<figure>` is an element used to encapsulate media such as an image, illustration, diagram, code snippet, etc, which is referenced in the main flow of the document.\
  It’s possible to add a caption to the image by using `<figcaption>`.\
  Here is an example:

```html
<figure>
  <img src="overwatch.jpg">
  <figcaption>This picture shows characters from Overwatch.</figcaption>
</figure>
```

* The `<audio>` element is used to embed audio content into a document. Like `<video>`, `<audio>` uses src to link the audio source.

```html
<audio>
  <source src="iAmAnAudioFile.mp3" type="audio/mp3" autoplay controls>
</audio>
```

Video example:

```html
<video src="coding.mp4" controls>Video not supported</video>
```

Embeded example:
```html
<embed src="download.gif"/>
```
### Linking


* `<a href= "https://..">link txt </a>` == anchor element (how link a page).
* `<a href= ".." target="_blank">` ==  opening in new tab
* `<a href="..">` <img> == wrapping the `<img>` elemnt with `<a>` element
* `<p id="top">` == linking a target
* `<a href="#top">` == jump to target
  
## Tags

* `<h1>` == headers 1 - 5
* `<p>` == paraghraph
* `<div>` == division 
* `<em>` == italic
* `<strong>` == bold
* `<br>` == break line
* `<ul>` unordered list
* `<ol>` ordered list
* `<img src="location.jpg" alt="info"/>` == tag allows you to add an image to a web page, alt is info incase the image not rander
* `<video src="myVideo.mp4" width="320" height="240" controls>
   Video not supported
   </video>` == video
* `<!-- txt -->` = comment
