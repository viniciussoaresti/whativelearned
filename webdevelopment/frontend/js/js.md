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

"Currying is an advanced technique of working with functions. It’s used not only in JavaScript, but in other languages as well. It's a transformation of functions that translates a function from callable as f(a, b, c) into callable as f(a)(b)(c).", [Javascript.info](https://javascript.info/currying-partials).



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

- Array' shift and unshift methods:

Didn't know about these either.

```javascript
array.shift();
//Example
let a = [1,2,3];
a.shift(); //returns the removed element (1)
console.log(a); //result == [2, 3]
```

```javascript
array.unshift('item');
//Example
let a = [1,2,3];
a.unshift(4); //returns the array's new size (4)
console.log(a); //result == [4, 1, 2, 3]
```

- Array.from():

Receives an array-like or an iterable object, and transforms it into an object.

```javascript
let divs = document.querySelectorAll('div'); //returns a NodeList
let divsArray = Array.from(divs); //returns an array with 'divs' content
```

- Conditional Operator:

Basically, a very nice way to summarize short if-else expressions.

```javascript
condition ? value-if-true : value-if-false;
//Example
let a = 1;
a === 1 ? console.log('equals 1') : console.log('different');
```
- toFixed():
"The toFixed() method formats a number using fixed-point notation", [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed).

```javascript
function financial(x) {
  return Number.parseFloat(x).toFixed(2);
}

console.log(financial(123.456));
// expected output: "123.46"

console.log(financial(0.004));
// expected output: "0.00"

console.log(financial('1.23e+5'));
// expected output: "123000.00"
```

- Spread and Rest Operators:

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

The same syntax can also be interpreted as a rest operator, that, does the opposite: transform many arguments into a single array, passing many function arguments, for example.

```javascript
function sum(...args){
  return args.reduce((acc, value) => acc + value);
}

sum(5, 5, 5, 2, 3); //20
```

- Destructuring Assignment:

"Destructuring assignment is a special syntax that allows us to “unpack” arrays or objects into a bunch of variables, as sometimes that’s more convenient", [Javascript.info](https://javascript.info/destructuring-assignment).

```javascript
let arr = ["John", "Smith"]

// destructuring assignment
// sets firstName = arr[0]
// and surname = arr[1]
let [firstName, surname] = arr;

alert(firstName); // John
alert(surname);  // Smith

//Works with any iterable on the right-side

let [a, b, c] = "abc"; // ["a", "b", "c"]
let [one, two, three] = new Set([1, 2, 3]);
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

Arrow functions have the same context as the upper context.
Examples for a better understanding:

```javascript
//Arrow function does not have the object scope
var obj = {
  a: 10
};

Object.defineProperty(obj, 'b', {
  get: () => {
    console.log(this.a, typeof this.a, this); // undefined 'undefined' Window {...} (or the global object)
    return this.a + 10; // represents global object 'Window', therefore 'this.a' returns 'undefined'
  }
});

//Arrow function has the function scope, as seen on on DIO's Bootcamp

let obj = {
  showContext: function showContext(){
    setTimeout(() => {
      this.log('after 1000ms');
    }, 1000);
  }

  log: function log(value){
    console.log(value);
  }
}

obj.showContext(); //returns 'after 1000ms', after 1000ms

```

- For of:

Interesting concept, going only through enumerable values, not properties as does for in.

```javascript
let arr = [3,5,7];
arr.foo = "hello";

for(let i in arr){
  console.log(i); // logs "0", "1", "2", "foo"
}

for(let i of arr){
  console.log(i); // logs "3", "5", "7"
}

/* As seen on DIO'S Avanade Angular Developer Bootcamp*/
```

- Object.freeze and Object.seal:

"The Object.freeze() method freezes an object. A frozen object can no longer be changed; freezing an object prevents new properties from being added to it, existing properties from being removed, prevents changing the enumerability, configurability, or writability of existing properties, and prevents the values of existing properties from being changed. In addition, freezing an object also prevents its prototype from being changed. freeze() returns the same object that was passed in", [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze).

```javascript
const obj = {
  prop: 42
};

Object.freeze(obj);

obj.prop = 33;
// Throws an error in strict mode

console.log(obj.prop);
// expected output: 42
```

"The Object.seal() method seals an object, preventing new properties from being added to it and marking all existing properties as non-configurable. Values of present properties can still be changed as long as they are writable", [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/seal).

```javascript
const object1 = {
  property1: 42
};

Object.seal(object1);
object1.property1 = 33;
console.log(object1.property1);
// expected output: 33

delete object1.property1; // cannot delete when sealed
console.log(object1.property1);
// expected output: 33
```

- Default Function Arguments (ES6+):

If an argument is not passed through the function call, you can pass an default value (or default values) through the function declaration, including another function's return, for example.

``` javascript
function multiply(a, b = 1){
  return a*b;
}

multiply(2); //Returns 2
multiply(5, undefined); //Returns 5
```

- Enhanced Object Literals (ES6+):

Pass an argument to an object, that's also the name of the property. Functions included.

``` javascript
let text = "I'm a text!";
let aSimpleFunction = function(){
  console.log("I'm a function!");
};

let object = {
  text,
  aSimpleFunction,
  otherFunction(){
    console.log("I'm a function also!");
  },
  [text]: "what?"
};

console.log(object); /*{text: "I'm a text!", aSimpleFunction: (the function's description),
otherFunction: (the function's description), I'm a text!: "what?"}*/
```

## Object-Oriented JS:

Every variable in JS has a 'hidden' inheritance, based on prototypes (variables that store the object's definitions). For example, a:

```javascript
let a = "abcd";
a.split('');
``` 

Is, actually:

```javascript
let a = String("abcd");
a.__proto__.split('');
``` 

There's some interesting concepts we can identify here:

- Every variable is actually an instantiation of a global object, such as [String](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String) or [Number](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Number);
- For that reason, they have a ```__proto__``` reference inside of them, and we're able to access all the inherited functions using it;
- There's two hidden parts of the first code: the constructor (```String()```) and the ```__proto__``` when we're calling the split function;
- For comparison:

```javascript
a.__proto__.split === String.prototype.split;
a.constructor === String;
```

An example of a constructor function, and a object instantiation:

```javascript
function Animal(){
  this.paws = 4;
}

let dog = new Animal();
console.log(dog.paws); //4
```

There's also a very simple way to make some kind of inheritance in JS:

```javascript
function Animal(){
  this.paws = 4;
}

function Dog(bites){}
  Animal.call(this, 4);
  this.bites = bites;
}

let rex = new Dog(false);
console.log(rex); //Dog {paws: 4, bites: false}
```

A way to override methods and properties:

```javascript
function Animal(paws){
  this.paws = paws;
  this.movement = function();
}

function Dog(bites){}
  Animal.call(this, 4);
  this.bites = bites;
  this.bark = function(){
    console.log('Woof! Woof!');
  }
}
```

How to define methods and properties standards:

```javascript
function Animal(){}
Animal.prototype.paws = 0;
Animal.prototype.movement = function();

function Dog(bites){}
  this.paws = 4;
  this.bites = bites;
}
Dog.prototype = Object.create(Animal);
Dog.prototype.bark = function(){
  console.log('Woof! Woof!');
}
```

That was before ES6, where official Classes where introduced. Now we have a more 'classy' sintax, close to Java, that's an official Object-Oriented language, for example.

```javascript
class Animal{
  constructor(paws){
    this.paws = paws;
  }

  movement(){}
}

class Dog extends Animal(){
  constructor(bites){
    super(4);
    this.bites = bites;
  }

  bark(){
    console.log('Woof! Woof!');
  }
}

const poodle = new Dog(false);
```

There was no support for native private fields and methods until recent updates, so there is something called the underscore convention (```_variableName```), that doesn't prevent someone from accessingg the property (adapted from [Bitscr](https://blog.bitsrc.io/javascript-finally-has-support-for-native-private-fields-and-methods-d758fdcfd320)). Now, we can define a private property, and access/modify them through getters/setters, and if we try to access them directly, we get an undefined.

Defining an private static field:

```javascript
class Class{
  static #privateField;
}

let a = new Class();
condole.log(a.privateField); //undefined
```