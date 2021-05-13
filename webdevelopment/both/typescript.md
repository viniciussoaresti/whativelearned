# Typescript

## Introduction:

Putting it on js because... it basically is JS, only with some special features.

"TypeScript is an open-source language which builds on JavaScript, one of the world’s most used tools, by adding static type definitions", [Typescript Lang](https://www.typescriptlang.org/).

```typescript
type User = {
    name: string;
    address: {
        city: string;
        state: string;
    }
}

function createWelcomeMessage(user: User){
    return `Boas-vindas, ${user.name}. Cidade: ${user.address} - ${user.address.state}`;
}

const welcomeMessage = createWelcomeMessage({
    name: 'Diego Fernandes',
    address: {
        city: 'Rio do Sul',
        state: 'SC'
    }
});
```

## Concepts:

### Interfaces vs Types:

"The difference between types and interfaces in TypeScript used to be more clear, but with the latest versions of TypeScript, they’re becoming more similar.

Interfaces are basically a way to describe data shapes, for example, an object.

Type is a definition of a type of data, for example, a union, primitive, intersection, tuple, or any other type", [Logrocket](https://blog.logrocket.com/types-vs-interfaces-in-typescript/).