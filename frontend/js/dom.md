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