# CSS
The standard Cascading Style Sheet for web pages.

# Contents

- [CSS](#css)
- [Contents](#contents)
  - [Example code on CSS:](#example-code-on-css)
  - [CSS selectors:](#css-selectors)
  - [Grouping Selectors:](#grouping-selectors)
  - [Adding CSS to HTML (on the html file):](#adding-css-to-html-on-the-html-file)
  - [The import tag:](#the-import-tag)
  - [Why cascading?:](#why-cascading)
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
  - [Tips:](#tips)
    - [Project done on base DIO's class:](#project-done-on-base-dios-class)
    - [a11y:](#a11y)

## Example code on CSS:

```css 
/* i'm a comment */
h1  {
    color: blue;
    font-size: 60px;
    background: gray;
}
```

## CSS selectors:

- `*` (Global);
- `h1, div, p` (Element selector);
- `#div-01` (Id selector);
- `.textDivs` (Class selector);
- Attribute, pseudo-class, pseudo-element, and many more selectors;

## Grouping Selectors:

```css 
/* applies the same declaration (properties and 
property values) to all listed elements */
h1, h2, div  {
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

We can use the `@Import` tag to import something like fonts on css, but it's not very indicated, and is advised to import things on the html head file for optimization purposes:

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

``` css
h1 {
    color: blue;
}

h1 {
    color: red;
}
/* since red is the last property value, its applied */
```

### Specificity:

"Specificity is the algorithm used by browsers to determine the CSS declaration that is the most relevant to an element, which in turn, determines the property value to apply to the element", [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity).

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

```css
div {
    margin: 12px 16px 10px 4px; /* top, right, bottom, left */
    margin: 12px 16px 0; /* top, sides, bottom */
    margin: 8px 16px; /* top and bottom, sides */
    margin: 8px; /* all 4 sides */
}
```

## Tips:

### Project done on base DIO's class:
[Html and CSS Intro](https://github.com/viniciussoaresti/htmlCssIntro)

### a11y:

A11y stands for accessibility (a - 11 characters - y), which is an important concept for web developers to keep in mind.

For example, on CSS font-sizes, you can define them on "REM's", which is 'x' times the root font size.