# CSS
The standard Cascading Style Sheet for web pages.

# Contents

- [CSS](#css)
- [Contents](#contents)
  - [Example CSS:](#example-css)
  - [Adding CSS to HTML (on the html file):](#adding-css-to-html-on-the-html-file)
  - [The import tag:](#the-import-tag)
  - [Why cascading?:](#why-cascading)
  - [Ensuring mobile consistency:](#ensuring-mobile-consistency)
  - [Specificity:](#specificity)
  - [!Important:](#important)
  - [At rules:](#at-rules)
  - [Shorthand:](#shorthand)
  - [Vendor prefixes:](#vendor-prefixes)
  - [Relative units:](#relative-units)
  - [Accessing the root element:](#accessing-the-root-element)
  - [Cool thing about the percentage:](#cool-thing-about-the-percentage)
  - [Box model:](#box-model)
    - [Box sizing:](#box-sizing)
    - [Inline vs Block display:](#inline-vs-block-display)
  - [Margin:](#margin)
  - [Padding:](#padding)
  - [Border:](#border)
  - [Outline:](#outline)
  - [Background image:](#background-image)
    - [Gradient](#gradient)
    - [Video, audio, iframe, images, figures and SVG:](#video-audio-iframe-images-figures-and-svg)
      - [Video:](#video)
      - [Audio:](#audio)
      - [Iframe:](#iframe)
      - [Images:](#images)
      - [Figures:](#figures)
      - [SVG:](#svg)
  - [Positioning:](#positioning)
    - [Position attribute:](#position-attribute)
      - [Static:](#static)
      - [Relative:](#relative)
      - [Absolute:](#absolute)
      - [Fixed:](#fixed)
      - [Element stacking:](#element-stacking)
  - [Texts:](#texts)
    - [More styles:](#more-styles)
      - [Font-variant:](#font-variant)
      - [Font-stretch:](#font-stretch)
      - [Letter-spacing and Word-spacing:](#letter-spacing-and-word-spacing)
      - [Line height:](#line-height)
      - [Text transform:](#text-transform)
      - [Text-decoration:](#text-decoration)
      - [Text-align:](#text-align)
      - [Text-shadow:](#text-shadow)
      - [Shorthand:](#shorthand-1)
  - [CSS selectors:](#css-selectors)
    - [Grouping Selectors:](#grouping-selectors)
    - [Combinators:](#combinators)
      - [Descendant combinator:](#descendant-combinator)
      - [Child combinator:](#child-combinator)
      - [Adjacent sibling combinator:](#adjacent-sibling-combinator)
      - [General sibling combinator:](#general-sibling-combinator)
    - [Pseudo-class selector:](#pseudo-class-selector)
      - [First child:](#first-child)
      - [Nth of type:](#nth-of-type)
      - [Nth child:](#nth-child)
      - [Nth child odd and even:](#nth-child-odd-and-even)
      - [Hover, focus, disabled and required:](#hover-focus-disabled-and-required)
    - [Pseudo-element selector:](#pseudo-element-selector)
      - [Before:](#before)
      - [After:](#after)
      - [First-line:](#first-line)
  - [Flexbox:](#flexbox)
    - [Flex direction:](#flex-direction)
    - [Flex sizing:](#flex-sizing)
    - [Flex container:](#flex-container)
      - [Flex-direction:](#flex-direction-1)
      - [Flex-wrap:](#flex-wrap)
      - [Flex-flow:](#flex-flow)
      - [Justify content:](#justify-content)
      - [Align items:](#align-items)
      - [Gap:](#gap)
    - [Flex item:](#flex-item)
      - [Flex-basis:](#flex-basis)
      - [Flex-grow:](#flex-grow)
      - [Flex-shrink:](#flex-shrink)
      - [Flex:](#flex)
      - [Order:](#order)
  - [Grid:](#grid)
  - [Tips:](#tips)
    - [Base css for all projects:](#base-css-for-all-projects)
    - [a11y:](#a11y)

## Example CSS:

```css 
/* i'm a comment */
h1  {
    color: blue;
    font-size: 60px;
    background: gray;
}
```

## Adding CSS to HTML (on the html file):

Inline:

``` html
<h1 style="color: red">Text</h1>
```

Style Tag:

``` html
<head>
    <style>
        h1{
            color: red;
        }
    </style>
</head>
```

Link to CSS file:

``` html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

## The import tag:

We can use the `@Import` tag to import something like fonts on css,
but it's not very indicated, and is advised to import things on the html head 
file for optimization purposes:

``` css
@import 'https://fonts.googleapis.com/css?family=Tangerine'
```

## Why cascading?:

It's read on a top-down approach, also considering style origin (inline > style tag > style link), specificity and importance. For example:

``` css
h1 {
    font-size: 12px;
}

h1 {
    color: red;
}
/* applies both declarations to the h1 element */
```

```css
h1 {
    color: blue;
}

h1 {
    color: red;
}
/* since red is the last property value, its applied */
```
## Ensuring mobile consistency:

We can ensure mobile consistency first with a specific head tag in the HTML:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

## Specificity:

"Specificity is the algorithm used by browsers to determine the CSS declaration
that is the most relevant to an element, which in turn, determines the property
value to apply to the element", [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity).

For example:

0 - Universal selector (*), combinators and negation pseudo-class (:not());
1 - Element type selector and pseudo-elements (::before, ::after);
10 - Classes and attribute selectors ([type="radio"]);
100 - Id selector;
1000 - Inline.

``` css
h1 {
    color: blue;
}

* {
    color: red;
}
/* since element type (1) is stronger than the universal selector (0),
the color is defined to blue */
```

``` css
* h1.title#my-title {
    color: orange;
}
/* we can also get selectors together to increase specificity value */
```

## !Important:

It's not recommended to use this, because it is not considered a good practice, and it breaks the natural cascading flow.
It goes over everything to define a property.

``` css
/* example */
h1 h2 {
    color: orange !important;
}
```
## At rules:

"At-rules are CSS statements that instruct CSS how to behave", [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule).

Some of them:
``` css
/* includes an external css */
@import url("http://local.com/style.css");

/* conditional rules to devices */
@media (min-width: 500px){
    /* rules here */
};

/* external fonts */
@font-face{
    /* rules here */
};

/* animation */
@keyframes nameOfAnimation{
    /* rules here */
};
```

## Shorthand:

Legible, short way of defining css.

``` css
/* example */
h1 {
    background-color: #000;
    background-image: url(images/bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
}
/* would be */
h1 {
    background: #000 url(images/bg.gif) no-repeat left top;
}
/* font example */
h2  {
    font: italic bold .8em/1.2 Arial, sans-serif;
}
```

See more on [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties#see_also).

## Vendor prefixes:

Sometimes some properties are not available on some browsers or are with a flag enabled:

```css
h1  {
    -webkit-transition: all 4s ease; /* basically, any WebKit or Chromium-based browser */
    -moz-transition: all 4s ease; /* Firefox */
    -ms-transition: all 4s ease; /* Old pre-WebKit versions of Opera */
    -o-transition: all 4s ease; /* Internet Explorer and Microsoft Edge, before Chromium */
}
```

We can check this with some tools like [CanIUse](https://caniuse.com/).

## Relative units:

"% (percentage): relative to the size of the parent element;
em (font size): relative to the size of the font;
rem (root em): relative to the font size of the root element;
vw (viewport width): relative to the width of the viewport;
vh (viewport height): relative to the height of the viewport", [FreeCodeCamp](https://www.freecodecamp.org/news/absolute-and-relative-css-units/).

## Accessing the root element:

```css
:root{

}

/* or */

html {

}
```

## Cool thing about the percentage:

```html
<!-- html -->
<ul>
    <li>One</li>
    <li>Two</li>
    <li>Three
        <ul>
            <li>Three A</li>
            <li>Three B
                <ul>
                    <li>Three B 1</li>
                    <li>Three B 2</li>
                </ul>
            </li>
        </ul>
    </li>
</ul>
```

```css
/* css */
li {
    font-size: 80%;
}
/* so every <li/> will be inheriting 80% from its parent */
```

## Box model:

The boxes that compose the html, on which we can work by using css, have the following properties:

- Width/Height;
- Content;
- Border;
- Padding;
- Margin.

<img src="https://media.gcflearnfree.org/content/5ef2084faaf0ac46dc9c10be_06_23_2020/box_model.png" alt="drawing" width="600"/>

### Box sizing:

The boxes usually add padding for example adding to the width, on content-box mode, but we can define it to border-box
mode for it to always respect the sizing defined.

```css
div {
    width: 100px;
    height: 100px;
    border: 1px solid red;
    margin: 10%;
    padding: 0 20px;
    box-sizing: border-box;
}
```

### Inline vs Block display:

Most of html tags have a block display, which means that they occupy all the line and push the other elements down,
they have width and height respected and padding, margin and border work normally, whereas inline puts elements one
alongside the other, width and height doesn't work and only horizontal margin, padding and border values work.

We can define the way a tag behaves like that:

```css
div {
    display: inline;
}

span {
    display: block;
}
```

## Margin:

We can define it in numbers, percentages and with the automatic value (tries to divide horizontally into the middle).

```css
div {
    margin: 12px 16px 10px 4px; /* top, right, bottom, left */
    margin: 12px 16px 0; /* top, sides, bottom */
    margin: 8px 16px; /* top and bottom, sides */
    margin: 8px; /* all 4 sides */
}
```

Careful with margin collapsing, which happens when for example two display-blocked divs have the same bottom and top
values.

## Padding:

The same margin rules, but careful as it can change elements width.

## Border:

"The border shorthand CSS property sets an element's border", [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/border).

## Outline:

The outline differs to a border because:

1. It doesn't modify the box size;
2. Can be different than rectangular;
3. Doesn't allow for individual adjustments;
4. It's mostly used by the user agent for accessibility.

## Background image:

Instead of using just a `background-color`, some properties used to set background
images are:  `background-image`, `background-image-repeat`, `background-position`, `background-size`, `background-origin`, `background-clip` and `background-attachment`.
It's nice to pay around with them.

### Gradient

We can apply a gradient to the background:

```css
main {
    background: linear-gradient(18deg, red, yellow);
    /* or */
    background: radial-gradient(red, yellow);
}
```

And even put multiple background values divided by commas on the background tag.

### Video, audio, iframe, images, figures and SVG:

#### Video:

We can define video tags on our html, with controls enabled or not (with just a 
flag), fallback content (if the video doesn't work), and with many other
configuration attributes, example:

```html
<video controls 
    width="200"
    height="400"
    autoplay
    preload="auto"
    loop
    muted
    poster="./icon.jpg">
    <source src="/media/cc0-videos/flower.webm"
            type="video/webm">
    <source src="/media/cc0-videos/flower.mp4"
            type="video/mp4">
    Download the
    <a href="/media/cc0-videos/flower.webm">WEBM</a>
    or
    <a href="/media/cc0-videos/flower.mp4">MP4</a>
    video.
</video>
```

#### Audio:

We can define audio tags on our html, something like the video tag, example:

```html
<audio controls autoplay muted loop>
    <source src="./audio.mp3" type="audio/mp3">
    <source src="./audio.ogg" type="audio/ogg">
    <p>Your browser doesn't support audio</p>
</audio>
```

#### Iframe:

We can define inline frame elements on our html, bringing external content to
our html:

```html
<iframe 
width="560"
height="315"
src="https://www.youtube.com/embed/3heO9XZpp2E"
title="Tim Bernardes being wonderful"
frameborder="0"
allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
allowfullscreen>
</iframe>
```

#### Images:

We can define images on our html, and even make them behave as a link:

```html
<a href="google.com">
    <img 
    src="./img.jpg"
    alt="Image alternative text when not loaded"
    title="Hold the mouse!"
    height="250px"
    width="200px">
</a>
```

#### Figures:

Figures are semantic ways of defining images with captions on our html:

```html
<a href="google.com">
    <figure>
        <img 
        src="./img.jpg"
        alt="Image alternative text when not loaded"
        title="Hold the mouse!"
        height="250px"
        width="200px">
        <figcaption>Image, by someone</figcaption>
    </figure>
</a>
```

#### SVG:

Scalable Vector Graphics are images rendered via algorithms, thus having some
benefits over standard images on some use cases. We don't usually code it by
hand on the html, but here's an example:

```html
<svg width="100px" height="100px">
    <circle cx="50" cy="50" rw="40" stroke="green"
    stroke-width="4" fill="yellow"/>
</svg>
```

Using a file is much more convenient:

```html
<img src="./ball.svg" alt="">
```

```html
<svg
version="1.1"
baseProfile="full" 
width="100px" 
height="100px"
xmlns="https://w3.org/2000/svg">
    <circle cx="50" cy="50" r="40" stroke="green"
    stroke-width="4" fill="yellow"/>
</svg>
```

## Positioning:

### Position attribute:

#### Static:

For default, all elements have the `static` property, staying all on top of the other.

#### Relative:

For the relative property, it allows us to use 5 other properties to set up our elements:

- Left;
- Right;
- Top;
- Bottom;
- Z-index.

But what would be the actual space element remains used.

#### Absolute:

The same as the relative property, but putting the element on another level,
removing the space it would use otherwise. Absolute means on all the page, but if
for example the element has a parent with a relative positioning, it stays attached
to the parent element. Example:

```html
<!-- html !-->
<body>
    <main>
        <div class="box box1"></div>
        <div class="box box2"></div>
        <div class="box box3"></div>
    </main>
</body>
```

```css
/* css */
.box {
    width: 50px;
    height: 50px;
    margin-bottom: 8px;
}

main {
    margin-top: 100px;
    position: relative;
}

.box1 {
    background-color: red;
    position: absolute;
    top: 0px;
    left: 0px;
}

.box2 {
    background-color: green;
}

.box3 {
    background-color: blue;
}
```

#### Fixed:

The element stays put even when scrolling the page, and it allows the other positioning
properties as well.

#### Element stacking:

Z-index usage.

## Texts:

Basic font attributes:
- Family: lists fonts in priority order, having a fallback font:
  - ```font-family: "Times New Roman", Times, sans-serif```.
- Weight: normal, bold, bolder, etc.;
- Style: normal, italic or oblique;
- Size: size in px, rem, em, etc;

Remembering we can use external fonts via @font-face, @import and links for example.
Links being the most common usage.

### More styles:

#### Font-variant:

```css
p {
	font-variant: small-caps;
}
```

[Font Variants](https://developer.mozilla.org/en-US/docs/Web/CSS/font-variant).

#### Font-stretch:

```css
p {
	font-stretch: expanded;
}
```

[Font Stretch](https://developer.mozilla.org/en-US/docs/Web/CSS/font-stretch).

#### Letter-spacing and Word-spacing:

```css
p {
	letter-spacing: 4px;
    word-spacing: 1em;
}
```

#### Line height:

```css
p {
	line-height: 1.5;
}
```

#### Text transform:

```css
p {
	text-transform: uppercase;
    /* none | capitalize | uppercase | lowercase | full-width | full-size-kana*/
}
```

#### Text-decoration:

Accepts multiple values.

```css
p {
  text-decoration: wavy overline blue; 
  /* line: underline | overline | line-through */
  /* style: wavy | dotted | double | dashed | solid */
  /* color: (color) */
}
```

#### Text-align:

```css
p {
	text-align: center;
    /* start | end | left | right | center | justify | match-parent */
}
```

#### Text-shadow:

Accepts multiple values.

```css
p {
  text-shadow: 1px 1px 1px red,
	       2px 2px 1px green; /* offset-x | offset-y | blur-radius | color */
}
```

#### Shorthand:

The order for defining font properties.

```css
p {
  font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif;
  /* font-style, font-variant, font-weight, font-stretch, font-size, line-height
   and font-family */
}
```

## CSS selectors:

- `*` (Global);
- `h1, div, p` (Element selector);
- `#div-01` (Id selector);
- `.textDivs` (Class selector);
- `['attribute']` (Attribute selector);
- `p:hover` (Pseudo-class selector);
- `p::first-line` (Pseudo-element selector);
- and many more selectors;

### Grouping Selectors:

```css 
/* applies the same declaration (properties and 
property values) to all listed elements */
h1, h2, div  {
    color: blue;
    font-size: 60px;
    background: gray;
}
```

### Combinators:

#### Descendant combinator:

Searches for an element inside another, even if there are other elements on the
way.

```css
body article h2{

}
```

#### Child combinator:

Searches for an element that is direct child of another, not considering any 
other elements after the direct child.

```css
body > ul > li{

}
```

#### Adjacent sibling combinator:

Selects only the element on the right side that is a direct element on the 
hierarchy (selects the first sibling occurrence).

```css
h1 + p{

}
```

#### General sibling combinator:

Selects all the element siblings specified.

```css
h1 ~ p{

}
```

### Pseudo-class selector:

#### First child:

Selects the first child of an element group:

```css
ul li :first-child {
  font-weight: bold;
}
```

#### Nth of type:

Selects the 'n'th element of an element group:

```css
ul li :nth-of-type(1) {
  font-weight: bold;
}
```

#### Nth child:

Selects the 'n'th child element of an element:

```css
ul li :nth-child(2) {
  font-weight: bold;
}
```

#### Nth child odd and even:

Selects the odd or even child elements of an element:

```css
ul li :nth-child(odd) { /*ul li:nth-child(even)*/
  font-weight: bold;
}
```

#### Hover, focus, disabled and required:

Selects elements when having hover or focus, or when having disabled or required
attributes:

```css
input :focus {
  border-color: red;
}
```

### Pseudo-element selector:

We can add html elements via css:

#### Before:

```css
li ::before {
  content: "> "
}
```

#### After:

```css
li ::after{
  content: ";"
}
```

And we also have:

#### First-line:

```css
p ::first-line {
	font-weight: bold;
}
```

## Flexbox:

Many things changed with the flexbox introduction, with the parent element being 
able to manipulate their children positioning, with the default being horizontal.

```css
/* css */
div.parent {
    display: flex;
}
/* we can use flex-direction, justify-content, align-items... */
```

### Flex direction:

Changes the child items positioning, with such as with `column`.

### Flex sizing:

Alters dynamically the height and width of the flex elements:

```css
.item {
    flex: 1;
}
```

### Flex container:

#### Flex-direction:

```css
.container {
    flex-direction: row; /*row-reverse, column, column-reverse*/
}
```

#### Flex-wrap:

Adapt content to multiple lines if needed:

```css
.container {
    flex-wrap: wrap; /*wrap-reverse*/
}
```

#### Flex-flow:

Enables shorthand for `direction` and `wrap`:

```css
.container {
    flex-flow: column wrap;
}
```

#### Justify content:

Element distribution inside the container, on the main axis:

```css
.container {
    display: flex;
    justify-content: flex-start; /*flex-end, center, space-around, 
    space-between, space-evenly*/
}
```

#### Align items:

Element distribution inside the container, on the other axis:

```css
.container {
    display: flex;
    justify-content: stretch; /*flex-start, flex-end, center*/
}
```

#### Gap:

Space between elements:

```css
.container {
    display: flex;
    gap: 10px; /*%, em, others*/
}
```

### Flex item:

#### Flex-basis:

Base width for flex elements.

```css
.container .item {
    display: flex;
    flex-basis: 10px; /*%, em, others*/
}
```

#### Flex-grow:

Item growth related to blank spaces. Each value represents a fraction of the
blank space.

```css
.container .item :nth-child(1){
    display: flex;
    flex-grow: 1;
}

.container .item :nth-child(2){
    display: flex;
    flex-grow: 2;
}
```

#### Flex-shrink:

Item shrink property. 0 makes the item occupy all the space it should, 1 is the
default making it shrink proportionally, and 2+ further shrinks the element. 

```css
.container .item :nth-child(1){
    display: flex;
    flex-shrink: 0;
}

.container .item :nth-child(2){
    display: flex;
    flex-shrink: 2;
}
```

#### Flex:

Shorthand for flex grow, shrink and basis:

```css
.container .item {
    display: flex;
    flex: 1 1 0; /*grow, shrink and basis*/
}
```

#### Order:

Defines order, from negative values to positive ones.

```css
.container .item :nth-child(1){
    order: 2; /*default*/
}
```

## Grid:

"CSS Grid Layout is a two-dimensional layout system for the web. It lets you lay content out in rows and columns. It has many features that make building complex layouts straightforward", [MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids).

```html
<!-- html !-->
<body>
    <header>Header</header>
    <main>Main</main>
    <aside>Aside</aside>
    <footer>Footer</footer>
</body>
```

```css
/* css */
body {
    margin: 0;
    height: 100vh;
    display: grid;
    grid-template-areas: 
    "header header"
    "main aside"
    "footer footer";
    grid-template-rows: 30px 1fr 40px;
    grid-template-columns: 1fr 80px;
}

header {
    grid-area: header;
    background-color: red;
}

main {
    grid-area: main;
    background-color: green;
}

aside {
    grid-area: aside;
    background-color: blue;
}

footer {
    grid-area: footer;
    background-color: yellow;
}
```

## Tips:

### Base css for all projects:
```css
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  text-decoration: none;
  /*
  font-family: sans-serif;
  font-size: 14px;
  transition: ease-in-out 1s; 
  */
}
```

### a11y:

A11y stands for accessibility (a - 11 characters - y), which is an important concept for web developers to keep in mind.

For example, on CSS font-sizes, you can define them on "REM's", which is 'x' times the root font size.