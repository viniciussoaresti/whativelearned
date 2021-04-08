# Js:
The client-sided loved language.

JS's a multi-paradigm language, and as such, has the ability to be coded on object-oriented programming, functional programming, and so on.

## Concepts:
- First-class functions:

Javascript's a language that has first-class functions.

That is, functions can be treated as any other variable, as described on [MDN](https://developer.mozilla.org/pt-BR/docs/Glossary/First-class_Function). Thus, beign able to be manipulated as an argument, returned by other funtions, and assigned to another variable.

- Closure:

"A closure gives you access to an outer function’s scope from an inner function", [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures).

For example:
```javascript
function init() {
  var name = 'Mozilla'; // name is a local variable created by init
  function displayName() { // displayName() is the inner function, a closure
    alert(name); // use variable declared in the parent function
  }
  displayName();
}
init();
```

- Currying

"Currying is an advanced technique of working with functions. It’s used not only in JavaScript, but in other languages as well.

Currying is a transformation of functions that translates a function from callable as f(a, b, c) into callable as f(a)(b)(c).", [Javascript.info](https://javascript.info/currying-partials).



```javascript
function soma(a){
  return function(b){
    return a+b;
  }
}

const soma2 = soma(2);

soma2(2); //or soma(2)(2), depending on what your use case is
soma2(3);
soma2(4);
soma2(5);
/* As seen on DIO's bootcamp 'Avanade Angular Developer' */
```
- Hoisting

"[...] a strict definition of hoisting suggests that variable and function declarations are physically moved to the top of your code, but this is not in fact what happens. Instead, the variable and function declarations are put into memory during the compile phase, but stay exactly where you typed them in your code.", [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting).

The key points to it, is that the declared functions (and its return) are hoisted, var declarations (not initialization a.k.a. value attribution) and let and const are not.

```javascript
catName("Chloe");

function catName(name) {
  console.log("My cat's name is " + name);
}
/*
The result of the code above is: "My cat's name is Chloe"
"Even though we call the function in our code first,
before the function is written,
the code still works. This is because of how context
execution works in JavaScript."
As seen on MDN.
*/

//More examples:
console.log(num); // Returns an error
let num; // Declaration
num = 6; // Initialization

console.log(num); // Returns an error
const num; // Declaration
num = 6; // Initialization

console.log(num); // Returns undefined, as only declaration was hoisted
var num; // Declaration
num = 6; // Initialization
```
## Tips:

- Array reverse method:

Didn't know about this function.

```javascript
array.reverse();
//Example
let a = [1,2,3];
console.log(a.reverse()); //result == [3, 2, 1]
```
- Conditional Operator:

Basically, a very nice way to summarize short if-else expressions.

```javascript
condition ? value-if-true : value-if-false;
//Example
let a = 1;
a === 1 ? console.log('equals 1') : console.log('different');
```

- Spread Operator:

"Spread syntax (...) allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.", [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax).

```javascript
myFunction(...iterableObj); // pass all elements of iterableObj as arguments to function myFunction

[...iterableObj, '4', 'five', 6]; // combine two arrays by inserting all elements from iterableObj

let objClone = { ...obj }; // pass all key:value pairs from an object 

function myFunction(x, y, z) { }
let args = [0, 1, 2];
myFunction(...args);
/*
Any argument in the argument list can use spread syntax,
and the spread syntax can be used multiple times.
*/
```

- Template Strings:

"Template literals are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them.", [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals). 

```javascript
let a = 5;
let b = 10;
console.log(`Fifteen is ${a + b} and
not ${2 * a + b}.`);
// "Fifteen is 15 and
// not 20."
```

- Symbols:

"Symbol is a built-in object whose constructor returns a symbol primitive — also called a Symbol value or just a Symbol — that’s guaranteed to be unique. Symbols are often used to add unique property keys to an object that won’t collide with keys any other code might add to the object, and which are hidden from any mechanisms other code will typically use to access the object. That enables a form of weak encapsulation, or a weak form of information hiding.",  [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals).

Key points: Symbol-keyed properties will be completely ignored when using JSON.stringify(), or for-in loops.

To be able to get a symbol property, there's ```Object.getOwnPropertySymbols(object)``` and ```Reflect.ownKeys(object)```.

- Arrow Functions:

Just a note: Arrow functions do not have their own this.
``` javascript
var obj = {
  a: 10
};

Object.defineProperty(obj, 'b', {
  get: () => {
    console.log(this.a, typeof this.a, this); // undefined 'undefined' Window {...} (or the global object)
    return this.a + 10; // represents global object 'Window', therefore 'this.a' returns 'undefined'
  }
});
```