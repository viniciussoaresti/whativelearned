# Js:
The client-sided loved language.

JS's a multi-paradigm language, and as such, has the ability to be coded on object-oriented programming, functional programming, and so on.

## Concepts:
- First-class functions:

Javascript's a language that has first-class functions.

That is, functions can be treated as any other variable, as described on MDN [here](https://developer.mozilla.org/pt-BR/docs/Glossary/First-class_Function). Thus, beign able to be manipulated as an argument, returned by other funtions, and assigned to another variable.

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

## Tips:

- Conditional Operator:
Basically, a very nice way to summarize short if-else expressions.
```javascript
condition ? value-if-true : value-if-false;
//Example
let a = 1;
a === 1 ? console.log('equals 1') : console.log('different');
```
- Array reverse method:
Didn't know about this function.
```javascript
array.reverse();
//Example
let a = [1,2,3];
console.log(a.reverse()); //result == [3, 2, 1]
```