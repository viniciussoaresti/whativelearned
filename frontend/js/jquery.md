# JQuery
## Introduction:
It's a JS library that enables you to select HTML elements and perform actions on them.
## Usage:
```
$("p").hide();
```

'$' invokes JQuery, which them receives a parameter, that could be one of the following: this (which is the current element), type (I mean, a tag, selecting all of them. e.g. if 'p' is passed, it works with all '<p>' elements), .class (the class of the items) or #id (the id of the item). More selectors: https://www.w3schools.com/jquery/jquery_selectors.asp.

Which then, can be updated with a bunch of methods, for example an event e.g. 'click', or an effect like 'hide', 'show', 'slide', 'animate', 'stop', 'callback' and 'chaining'.