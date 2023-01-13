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
      - [Output:](#output)
      - [Input:](#input)
      - [Exit:](#exit)
  - [NPM:](#npm)
    - [Creating a package:](#creating-a-package)
    - [Installing a package:](#installing-a-package)
    - [Installing a package only for the development environment:](#installing-a-package-only-for-the-development-environment)
    - [Update:](#update)
    - [Running scripts:](#running-scripts)
    - [Installing packages globally:](#installing-packages-globally)
    - [Semantic versioning:](#semantic-versioning)
  - [Timers:](#timers)
    - [setTimeout:](#settimeout)
    - [clearTimeout:](#cleartimeout)
    - [setInterval:](#setinterval)
    - [clearInterval:](#clearinterval)
  - [Events:](#events)
    - [Event Emmiter:](#event-emmiter)

# Hello World:

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

# Concepts:

## Node base:

Node.js is single-threaded, non-blocking and asynchronous.

## Globals:

Node has a lot of globals for us to use on our work, listed
[here](https://nodejs.org/dist/latest-v18.x/docs/api/globals.html).

## Modules:

It also provides us with a lot of modules, which we can use with the 
`require` keyword, for example:

### Path:

```js
const path = require('path');
console.log(path.basename(__filename));
```
### Creating modules:

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

### Process:

The process module returns a lot of data around the process, and also captures
the data passed through the terminal as arguments on the `argv` array.

```js
console.log(process.argv);
```
#### Output:

Meaning process.stardardOutput:

```js
process.stdout.write("Hey")
```

#### Input:

This time we have an asynchronous function, which receives data and processes
it on another function:

```js
process.stdin.on("data", data => {
    process.stdout.write(data.toString().trim() + "\n");
})
```

#### Exit:

```js
process.exit();
```

## NPM:

Stands for Node Package Manager.

### Creating a package:

`npm init` or `npm init -y` for a simple start.

### Installing a package:

`npm install (packageName)`.

### Installing a package only for the development environment:

`npm i (packageName) -g`.

### Update:

`npm update`.

### Running scripts:

When we have scripts defined on the package.json, we can run them by name:

`npm run scriptName`

### Installing packages globally:

`npm i (packageName) -g`

`npm uninstall (packageName) -g`

### Semantic versioning:

We have some notations for the dependencies update:

- * for major, minor and patch (the latest version);
- ^ for minor and patch (1.x.x for example);
- ~ for patch (1.1.x for example).

Which we can use, checking before with `npm outdated`, with `npm upgrade`.
This doesn't change the package.json, but the package-lock.json.

## Timers:

### setTimeout:

Runs a function after x milliseconds:

```js
const timeOut = 3000;
const finished = () => console.log("done");
setTimeout(finished, timeOut);
```

### clearTimeout:

Cancels a timeout:

```js
const timeOut = 3000;
const finished = () => console.log("done");
let timer = setTimeout(finished, timeOut);
clearTimeout(timer);
```

### setInterval:

Sets a function to be run in an interval of time:

```js
const timeOut = 1000;
const checking = () => console.log("checking!");
setInterval(checking, timeOut);
```

### clearInterval:

```js
const timeOut = 1000;
const checking = () => console.log("checking!");
let interval = setInterval(checking, timeOut);
clearInterval(interval);
```

## Events:

In node.js we have the event module, which we can use to fire and listen to 
events, and define an action when the event is triggered. It serves as a base to
other modules like http, stream, file system, etc.

### Event Emmiter:

Defining an event emitter, emitting an event and listening to it:

```js
const { EventEmitter } = require('events');
const ev = new EventEmitter();
ev.on("saySomething", (message) => {
    console.log("listened you: " + message);
})
ev.emit("saySomething", "message");
```

Listening only to the first event emmited:

```js
ev.once("saySomething", (message) => {
    console.log("listened you: " + message);
})
```