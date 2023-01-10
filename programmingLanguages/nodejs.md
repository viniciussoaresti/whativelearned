# Node.js:

"Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine", [NodeJS](https://nodejs.org/en/).

# Table of contents:

- [Node.js:](#nodejs)
- [Table of contents:](#table-of-contents)
  - [Hello World:](#hello-world)
  - [Concepts:](#concepts)
    - [Node base:](#node-base)
    - [Globals:](#globals)
    - [Modules:](#modules)
      - [Path:](#path)
      - [Creating modules:](#creating-modules)
      - [Process:](#process)
    - [EventEmitter:](#eventemitter)

## Hello World:

```js
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

## Concepts:

### Node base:

Node.js is single-threaded, non-blocking and asynchronous.

### Globals:

Node has a lot of globals for us to use on our work, listed
[here](https://nodejs.org/dist/latest-v18.x/docs/api/globals.html).

### Modules:

It also provides us with a lot of modules, which we can use with the 
`require` keyword, for example:

#### Path:

```js
const path = require('path');
console.log(path.basename(__filename));
```
#### Creating modules:

We can also create modules:

```js
//main file
const myModule = require('./moduleFile.js');
console.log(myModule);
```

```js
//module file
module.exports = "exported module";
```

#### Process:

The process module returns a lot of data around the process, and also captures
the data passed through the terminal as arguments on the `argv` array.

```js
console.log(process.argv);
```

### EventEmitter:

It's a class that allow us to emit and 'subscribe' to events, thus permitting us to handle the events that are happening and do something when it does.

```javascript
const EventEmitter = require('events');
const emitter = new EventEmitter();
emitter.on('User logged', data => { 
    console.log(data);
});
emitter.emit('User logged', {user: 'Vinícius Soares'});

/*
On the emit, the 'User logged' event is emitted, and since the
emitter is 'subscribed' to this event, we get 
{user: 'Vinícius Soares'} on our console.
*/
```