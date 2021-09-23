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

And types are commonly used to specify interfaces 'merging':

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
// IDomesticAnimal =  IDog & ICat is also possible
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