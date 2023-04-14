# DOM

# Contents:

- [DOM](#dom)
- [Contents:](#contents)
  - [Introduction:](#introduction)
  - [Selecting elements:](#selecting-elements)
    - [getElementById:](#getelementbyid)
    - [getElementsByClassName (returns a HTMLCollection):](#getelementsbyclassname-returns-a-htmlcollection)
    - [getElementsByTagName:](#getelementsbytagname)
    - [querySelector:](#queryselector)
    - [querySelectorAll (returns a NodeList):](#queryselectorall-returns-a-nodelist)
  - [Manipulating content:](#manipulating-content)
    - [textContent:](#textcontent)
    - [innerText:](#innertext)
    - [innerHTML:](#innerhtml)
    - [Manipulating attributes:](#manipulating-attributes)
    - [Manipulating styles:](#manipulating-styles)
    - [Manipulating classes:](#manipulating-classes)
  - [Navigating through elements:](#navigating-through-elements)
    - [parentElement and parentNode:](#parentelement-and-parentnode)
    - [childNodes, children, firstChild, firstElementChild, lastElement and lastElementChild:](#childnodes-children-firstchild-firstelementchild-lastelement-and-lastelementchild)
    - [nextSibling, nextElementSibling, previousSibling and previousElementSibling:](#nextsibling-nextelementsibling-previoussibling-and-previouselementsibling)
  - [Creating and adding elements to the page:](#creating-and-adding-elements-to-the-page)
    - [createElement:](#createelement)
    - [append and prepend:](#append-and-prepend)
    - [insertBefore (inserts before a specific element):](#insertbefore-inserts-before-a-specific-element)
  - [Events:](#events)
    - [Adding events on the html:](#adding-events-on-the-html)
    - [Adding events on the js:](#adding-events-on-the-js)
    - [Event argument (returns many types of events):](#event-argument-returns-many-types-of-events)

## Introduction:

The Document Object Model (DOM) is the Javascript representation of the HTML.
It provides us with an API to interact with it.

## Selecting elements:

### getElementById:

```js
document.getElementById('blog-title');
```

### getElementsByClassName (returns a HTMLCollection):

```js
document.getElementsByClassName('one');
```

### getElementsByTagName:

```js
document.getElementsByTagName('h1');
```

### querySelector:

Selects the first element that matches the query.

```js
document.querySelector('.one');
```

### querySelectorAll (returns a NodeList):

Selects all the elements that match the query.

```js
document.querySelector('[src]');
```

## Manipulating content:

### textContent:

```js
let element = document.getElementById('my-id');
element.textContent = "Hello!";
```

### innerText:

```js
let element = document.getElementById('my-id');
element.innerText = "Hello!";
```

### innerHTML:

```js
let element = document.getElementById('my-id');
element.innerHTML = "Hello!<small>!</small>";
```

### Manipulating attributes:

Adding:

```js
const header = document.querySelector('header');
header.setAttribute('id', 'header')

const headerId = document.querySelector('#header');
console.log(headerId)
```

Getting:

```js
const headerId = document.querySelector('#header');
console.log(headerId.getAttribute('id'));
```

Removing:

```js
const headerId = document.querySelector('#header');
headerId.removeAttribute('id');
console.log(headerId.getAttribute('id'));
```

### Manipulating styles:

```js
const element = document.querySelector('body');
element.style.backgroundColor = '#f9f3d2';
console.log(element.style.backgroundColor);
```

### Manipulating classes:

```js
const element = document.querySelector('body');
element.classList.add('active', 'green');
console.log(element.classList);
element.classList.remove('active');
element.classList.toggle('green');
```

## Navigating through elements:

### parentElement and parentNode:

```js
const element = document.querySelector('body');
console.log(element.parentElement); //same as parentNode
```

### childNodes, children, firstChild, firstElementChild, lastElement and lastElementChild:

```js
const element = document.querySelector('body');
console.log(element.childNodes); // returns a NodeList, considers blank spaces and comments
console.log(element.children); //returns a HTMLCollection
console.log(element.firstChild); //considers blank spaces and comments
console.log(element.firstElementChild);
console.log(element.lastElement); //considers blank spaces and comments
console.log(element.lastElementChild);
```

### nextSibling, nextElementSibling, previousSibling and previousElementSibling:

```js
const element = document.querySelector('body');
console.log(element.nextSibling); //considers blank spaces and comments
console.log(element.nextElementSibling);
console.log(element.previousSibling); //considers blank spaces and comments
console.log(element.previousElementSibling);
```

## Creating and adding elements to the page:

### createElement:

```js
const div = document.createElement('div');
div.innerText = "Hello!";
```

### append and prepend:

```js
const element = document.querySelector('body');
const div = document.createElement('div');
div.innerText = "Hello!";
body.append(div); //puts at the last index inside the body
body.prepend(div); //puts at the first index inside the body
```

### insertBefore (inserts before a specific element):

```js
const element = document.querySelector('body');
const div = document.createElement('div');
div.innerText = "Hello!";
const h1 = element.querySelector('h1');
element.insertBefore(div, h1);
element.insertBefore(div, h1.nextElementSibling); //simulating an insertAfter
```

## Events:

### Adding events on the html:

```html
<!-- html !-->
<h1 onClick="print()"></h1>
```

```js
function print(){
  console.log('clicked');
}
```

### Adding events on the js:

Adding via htmlEvent:

```js
const input = document.querySelector('input');

input.onKeyDown = function() {
  console.log('input');
}

input.onKeyUp = function() {
  console.log('input');
}
```

Adding an event listener (enables multiple functions at the same time):

```js
const input = document.querySelector('input');

input.addEventListener('click', () => {console.log('hey')});
```

### Event argument (returns many types of events):

```js
const input = document.querySelector('input');

input.addEventListener('click', (event) => {console.log(event)});
```