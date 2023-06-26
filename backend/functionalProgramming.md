# Functional Programming

"Functional programming is a programming paradigm in which we try to bind
everything in pure mathematical functions style. It is a declarative type of
programming style. Its main focus is on “what to solve” in contrast to an
imperative style where the main focus is “how to solve”. It uses expressions
instead of statements. An expression is evaluated to produce a value whereas a
statement is executed to assign variables", [G4G](https://www.geeksforgeeks.org/functional-programming-paradigm/).

# Contents:

- [Functional Programming](#functional-programming)
- [Contents:](#contents)
  - [1. Concepts:](#1-concepts)
    - [1.1: Imperative vs Declarative Functions:](#11-imperative-vs-declarative-functions)
    - [1.2: Immutability:](#12-immutability)
    - [1.3: Stateless:](#13-stateless)
    - [1.4: Function Characteristics:](#14-function-characteristics)
      - [1.4.1: Independent functions:](#141-independent-functions)
      - [1.4.2: Pure functions:](#142-pure-functions)
      - [1.4.3: First-class functions:](#143-first-class-functions)
      - [1.4.4: Higher-order functions:](#144-higher-order-functions)
      - [1.4.5: Function composition:](#145-function-composition)

## 1. Concepts:

### 1.1: Imperative vs Declarative Functions:

"The easiest way to explain the difference between declarative and imperative
code, would be that imperative code focuses on writing an explicit sequence
of commands to describe how you want the computer to do things, and declarative
code focuses on specifying the result of what you want", [Yehuda](https://www.linkedin.com/pulse/imperative-vs-declarative-programming-javascript-yehuda-margolis/).

```js
//IMPERATIVE
const doubleMapImperative = numbers => {
    const doubled = [];
    for (let i=0; i < numbers.length; i++) {
        doubled.push(numbers[i] * 2);
    }   
    return doubled;
};

//DECLARATIVE
const doubleMapDeclarative = numbers => numbers.map(n => n ⋆ 2);


console.log(doubleMapImperative (numbers: [2, 3, 4])); // [4, 6, 8]
console.log(doubleMapDeclarative (numbers: [2, 3, 4])); // [4, 6, 8]
/*https://www.linkedin.com/pulse/imperative-vs-declarative-programming-
javascript-yehuda-margolis/*/
```

### 1.2: Immutability:

Variables shouldn't be changed, when the state changes another variable should
be created.

```js
const cart = {
    quantity: 2,
    total: 200
}

// bad:
cart.quantity = 3;

//good:
const newCart = {...cart, quantity: 3};

//rocketseat
```

### 1.3: Stateless:

Functions don't save state, only know the data given to it, and the function
response should always be the same.

```js
//stateful
let number = 2;
function square(){
    return number * number;
}
number = square();

//stateless
const square = n => n * n;

//rocketseat
```

### 1.4: Function Characteristics:

#### 1.4.1: Independent functions:

All functions should have at least one argument, return something, nothing that
happens inside of it should interfere with the outside of itself, and shouldn't
use loops (for, while, etc.), but instead resort to recursion.

#### 1.4.2: Pure functions:

Functions shouldn't depend of any outside data apart from what is passed to
them, have interference from any external code, return different results based
on the same given parameters, or have any collateral effects (modify states or
save state).

#### 1.4.3: First-class functions:

Functions can can be treated as any other variable, as described on [MDN](https://developer.mozilla.org/pt-BR/docs/Glossary/First-class_Function). Thus,
being able to be manipulated as an argument, returned by other functions, and
assigned to another variable.

#### 1.4.4: Higher-order functions:

Functions that receive other functions as arguments or that could return other
functions.

Together with currying (which is advanced technique of working with functions,
(not only used in JavaScript, but in other languages as well) a
transformation of functions that translates a function from callable as
f(a, b, c) into callable as f(a)(b)(c)", [Javascript.info](https://javascript.info/currying-partials)).

Example:

```js
const pause = wait => fn => setTimeout(fn, wait);

pause(600)( () => console.log('waiting 600ms'));

const wait200 = pause(200);
const wait1000 = pause(1000);

wait200(() => console.log('waiting 200ms'));
wait1000(() => console.log('waiting 1s'));
//rocketseat
```

#### 1.4.5: Function composition:

Function chaining. Example:

```js
const people = ['Rafa', 'Diego', 'Dani', 'Rod'];

const upperCasePeopleThatStartsWithD = people
.filter(person => person.startsWith('D'))
.map(dPerson => dPerson.toUpperCase());
//rocketseat
```