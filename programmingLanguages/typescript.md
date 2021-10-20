# Typescript

## Introduction:

"TypeScript is an open-source language which builds on JavaScript, one of the world’s most used tools, by adding static type definitions", [Typescript Lang](https://www.typescriptlang.org/).

The main goal of TypeScript is to add better type definitions and checking, and object-orientation to javascript, making code more readable and upgradable for developers, avoiding errors.

Of course, since it is built on top of javascript, if you use the TypeScript compiler (for example, `tsc index.ts`), a JS file is generated, 'translating' the TypeScript code to native JS code.

### Code example:

```typescript
type User = { //type = a definition of a type of data
    name: string; //specifies the parameter type, in this case a string
    address: {
        city: string;
        state: string;
    }
}

function createWelcomeMessage(user: User){ //specifies which type the received parameters should be
    return `Welcome, ${user.name}. City: ${user.address} - ${user.address.state}`; //string template literal
}

const welcomeMessage = createWelcomeMessage({
    name: 'Diego Fernandes',
    address: {
        city: 'Rio do Sul',
        state: 'SC'
    }
}); //Go Rocketseat!
```

## Concepts:

### Interfaces vs Types:

"The difference between types and interfaces in TypeScript used to be more clear, but with the latest versions of TypeScript, they’re becoming more similar.

Interfaces are basically a way to describe data shapes, for example, an object.

Type is a definition of a type of data, for example, a union, primitive, intersection, tuple, or any other type", [Logrocket](https://blog.logrocket.com/types-vs-interfaces-in-typescript/).

As on most object-oriented languages, interfaces can be extended:

```typescript
interface IUser = {
    name: string;
    address: {
        city: string;
        state: string;
    }
}

interface IAdmin extends IUser = {
    sudo: true | false; //you can also specify the values
}
```

And types are commonly used to specify intersections between interfaces:

```typescript
interface IAnimal = {
    name: string;
}

interface IDog extends IAnimal = {
    meow: true | false; //you can also specify the values
}

interface ICat extends IUser = {
    woof: true | false; //you can also specify the values
}

type IDomesticAnimal =  IDog | ICat;
// IDomesticAnimal =  IDog & ICat definition is also possible
```

You can read about an example of that [here](https://stackoverflow.com/questions/37688318/typescript-interface-possible-to-make-one-or-the-other-properties-required).

### Type Assertions:

"Type assertions are a way to tell the compiler “trust me, I know what I’m doing.” A type assertion is like a type cast in other languages, but it performs no special checking or restructuring of data. It has no runtime impact and is used purely by the compiler. TypeScript assumes that you, the programmer, have performed any special checks that you need", [Typescript](https://www.typescriptlang.org/docs/handbook/basic-types.html#type-assertions).

Type assertions have two forms.

One is the as-syntax:
```typescript
let someValue: unknown = "this is a string";
let strLength: number = (someValue as string).length;
```

The other version is the “angle-bracket” syntax:
```typescript
let someValue: unknown = "this is a string"; 
let strLength: number = (<string>someValue).length;
```

### (HTML) Web APIs and Interfaces:

"When writing code for the Web, there are a large number of Web APIs available. Below is a list of all the APIs and interfaces (object types) that you may be able to use while developing your Web app or site. Web APIs are typically used with JavaScript, although this doesn't always have to be the case", [MDN](https://developer.mozilla.org/en-US/docs/Web/API).

#### HTMLInputElement:

"The HTMLInputElement interface provides special properties and methods for manipulating the options, layout, and presentation of <input> elements", [MDN](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement).

Practical example:
```typescript
const input = document.getElementById('input') as HTMLInputElement;

input.addEventListener('input', (event) => {
    console.log((event.currentTarget as HTMLInputElement).value);
});
```

### Generic Types:

"A major part of software engineering is building components that not only have well-defined and consistent APIs, but are also reusable. Components that are capable of working on the data of today as well as the data of tomorrow will give you the most flexible capabilities for building up large software systems.

In languages like C# and Java, one of the main tools in the toolbox for creating reusable components is generics, that is, being able to create a component that can work over a variety of types rather than a single one. This allows users to consume these components and use their own types", [TypeScript](https://www.typescriptlang.org/docs/handbook/2/generics.html).

```typescript
function addValueToAllList<T>(array: any[], value: T) {
    return array.map(item => item + value);
}

addValueToAllList([1, 2, 3], 1);
```

## Tips:

### Question mark:

"Question marks on TypeScript variable are used to mark that variable as an optional variable. If we put the question mark when declaring a variable that variable becomes optional. The optional parameters will have value as undefined when unused", [Geeks for Geeks](https://www.geeksforgeeks.org/why-use-question-mark-in-typescript-variable/#:~:text=Why%20use%20Question%20mark%20in%20TypeScript%20variable%20%3F,-Difficulty%20Level%20%3A%20Hard&text=Question%20marks%20on%20TypeScript%20variable,value%20as%20undefined%20when%20unused.).

```typescript
function point(x?: number, y?: number){
    if(x) 
        console.log('X : ' + x);
    else 
        console.log('Value of X coordinate not given');
    if(y) 
        console.log('Y : ' + y);
    else 
        console.log('Value of Y coordinate not given');
}
```

### Handling read only and multiple keys manipulation with types using keyof:

```typescript
interface Dog {
    name: string;
    age: number;
    favoritePark?: string;
}

type ReadOnlyDog = {
    readonly [K in keyof Dog]: Dog[K];
    /*We can remove the optional keys with the following syntax:
    readonly [K in keyof Dog]-?: Dog[K];
    And improve readability with the following one:
    +readonly [K in keyof Dog]: Dog[K];*/
}

class Dog implements ReadOnlyDog {
    name: string;
    age: number;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }
}

const myDog = new Dog('Doggy', 6);
```