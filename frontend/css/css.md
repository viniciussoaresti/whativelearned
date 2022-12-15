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

We can check this with some tools like [CanIUse]().

## Tips:

### Project done on base DIO's class:
[Html and CSS Intro](https://github.com/viniciussoaresti/viniciussoaresti.github.io)

### a11y:

A11y stands for accessibility (a - 11 characters - y), which is an important concept for web developers to keep in mind.

For example, on CSS font-sizes, you can define them on "REM's", which is 'x' times the root font size.