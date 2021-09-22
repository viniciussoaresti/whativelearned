# Typescript

## Introduction:

"TypeScript is an open-source language which builds on JavaScript, one of the world’s most used tools, by adding static type definitions", [Typescript Lang](https://www.typescriptlang.org/).

The main goal of TypeScript is to add better type definitions and checking, and object-orientation to javascript, making code more readable and upgradable for developers, avoiding errors.

### Code example:

```typescript
type User = {
    name: string;
    address: {
        city: string;
        state: string;
    }
}

function createWelcomeMessage(user: User){
    return `Welcome, ${user.name}. City: ${user.address} - ${user.address.state}`;
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