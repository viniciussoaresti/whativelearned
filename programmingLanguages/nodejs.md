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
- [EJS:](#ejs)
  - [Install](#install)
  - [Using:](#using)
  - [Separating layout parts:](#separating-layout-parts)
    - [Folder organization:](#folder-organization)
  - [Live Reload](#live-reload)
  - [Passing objects to ejs:](#passing-objects-to-ejs)
    - [Omiting object:](#omiting-object)
    - [Foreach:](#foreach)

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

# EJS:

Embedded JavaScript (EJS) templates. Modelling language for HTML pages creation utilizing JS.

## Install

Install using `npm i ejs`.

We also need to have a server in place, which we can achieve with express (`npm i express`).

## Using:

To use it, we need to change any html file extensions to `.ejs`, put them on a `views` folder and specify a server to
render it:

```js
//server.js
const express = require('express');
const app = express();

app.set('view engine', 'ejs');

app.get('/', function (req, res) {
    res.render('index');
});

app.listen(8080);
```

I've found some problems when linking css files, and it seems like when adding static files (like JS, CSS or images),
we need to use a folder (most commonly the 'public' folder) to store them and define it on the express definitions:

```js
//server.js
app.use(express.static("public"));
```

And in the ejs file:

```html
<!-- index.ejs !-->
<link rel="stylesheet" href="css/style.css"> <!-- the style.css is located on /public/css/-->
```

## Separating layout parts:

We can separate layout parts and include them on other parts of html pages with ejs. For example:

```html
<!-- index.ejs !-->
<!DOCTYPE html>
<html lang="en">

<%- include('head'); %>

<body class='container'>


    <main>
        <div>
            <h1>Page title</h1>
            <p>Content</p>
        </div>
    </main>


</body>

</html>
```

```html
<!-- head.ejs !-->
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Rowdies:wght@300&display=swap" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <link rel="stylesheet" href="css/style.css">
</head>
```

### Folder organization:

Good practice in ejs:

Separate full pages and partials (like headers, footers, etc.) inside the views folder, within their own folders.

## Live Reload

Oh, did I forget to mention that all the edits you make are made to the server without having to restart the server? Neat.
It's not a **live** live reload, refreshing the browser automatically, but it's almost as good.

## Passing objects to ejs:

We're able to pass objects from one page to another, like the following example:

```html
<!-- index.ejs !-->
<!DOCTYPE html>
<html lang="en">

<%- include('../partials/head'); %>

<body class='container'>

    <%- include('../partials/header', {page: 'Home'}); %>

    <main>
        <div class='container-fluid text-sm-center p-5 bg-secondary'>
            <h1>Node com EJS</h1>
            <p>Vamos aprender a trabalhar com arquivos EJS</p>
        </div>
    </main>

    <%- include('../partials/footer'); %>

</body>

</html>
```

```html
<!-- header.ejs !-->
<header>
    <p>Page: <%- page %> </p>
    <nav class='navbar navbar-expand-lg navbar-light bg-light'>
        <a class='navbar-brand' href="/">EJS</a>
        <ul class='navbar-nav mr-auto'>
            <li class='nav-item'><a class='nav-link' href='/'>Home</a></li>
            <li class='nav-item'><a class='nav-link' href='/about'>About</a></li>
        </ul>
    </nav>
</header>
```

When using it, be sure to always send the object each page will receive, or else it'll error.

### Omiting object:

Sometimes on a page we won't need to send an object, so we can adapt the code to comply. Note the `=` change on the
`header.ejs` include declaration, specifying that this content will be received dynamically:

```html
<!-- header.ejs !-->
<header>
    <nav class='navbar navbar-expand-lg navbar-light bg-light'>
        <a class='navbar-brand' href="/">EJS</a>
        <ul class='navbar-nav mr-auto'>
            <li class='nav-item'><a class='nav-link' href='/'>Home</a></li>
            <li class='nav-item'><a class='nav-link' href='/about'>About</a></li>
        </ul>
    </nav>
    <p>Page: <%= typeof page != 'undefined' ? page : 'Home' %> </p>
</header>
```

### Foreach:

Foreach example consuming items from the backend:

```html
<!-- index.ejs !-->
<!DOCTYPE html>
<html lang="en">

<%- include('../partials/head'); %>

<body class='container'>

    <%- include('../partials/header', {page: 'Home'}); %>

    <main>
        <div class='container-fluid text-sm-center p-5 bg-secondary'>
            <h1>Node com EJS</h1>
            <p>Vamos aprender a trabalhar com arquivos EJS</p>
        </div>
        <ul>
            <% items.forEach((item)=>{ %>
            <li>
                <strong><%= item.title %>:</strong> <%= item.message %>
            </li>
            <% }) %>
        </ul>
    </main>

    <%- include('../partials/footer'); %>

</body>

</html>
```

```js
//server.js
const express = require('express');
const app = express();

app.use(express.static("public"));
app.set('view engine', 'ejs');

app.get('/', function (req, res) {
    const items = [
        {
            title: 'D',
            message: 'Develop'
        },
        {
            title: 'E',
            message: 'EJS'
        },
        {
            title: 'M',
            message: 'Mindfully'
        },
        {
            title: 'A',
            message: 'After'
        },
        {
            title: 'I',
            message: 'Initial'
        },
        {
            title: 'S',
            message: 'Studies'
        }
    ]
    res.render('pages/index', { items: items });
});

app.get('/about', function (req, res) {
    res.render('pages/about');
});

app.listen(8080);
```