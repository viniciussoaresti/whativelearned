# React:

Open-source front-end javascript library, developed initially by Facebook, with focus on dynamic components.


## Concepts:

### Introduction:

React, as most modern front-end frameworks, renders the application's content through javascript. Example:

Index.html:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>React App</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```

Index.js:

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

App.js:

```javascript
function App() {
  return (
    <h1>Hello World</h1>
  );
}

export default App;
```

There, we can see that the ReactDOM (React's Document Object Model) renders the component App (components are functions that return html, as we can see), on `Index.js`, inside the 'root' html element. Thus, the `App.js` content, that is, `<h1>Hello World</h1>`, renders through this structure.

### Fragment:

Fragments are a fun concept, on which a 'blank' html tag is created inside a component, to encapsulate other components/html tags (components/tags cannot be inserted multiple times if not inside another element, such as a div).

```javascript
function App(){
    return(
        <>
        <SomeComponent />
        <SomeComponent />
        <SomeComponent />
        <SomeComponent />
        </>
    );
}
```

### Props:

React uses proprieties as another name for attributes, on a rough explanation. Then, we're able to use them inside a component.

```javascript
function App(){
    return(
        <>
        <SomeComponent property1="prop1" />
        <SomeComponent property1="prop2" />
        <SomeComponent property1="prop3" />
        <SomeComponent property1="prop4" />
        </>
    );
}
```


```javascript
export default function SomeComponent(props){
    return(
        <someTag>{props.property1}</someTag>
    );
}
```

We're also able to pass information inside component tags, and access them using props.children:

```javascript
function App(){
    return(
        <>
        <SomeComponent>prop1</>
        <SomeComponent>prop2</>
        <SomeComponent>prop3</>
        <SomeComponent>prop4</>
        </>
    );
}
```


```javascript
export default function SomeComponent(props){
    return(
        <someTag>{props.children}</someTag>
    );
}
```

### State:

React uses the useState method for dynamic variable changes, for example, in contrast with Angular, that uses the famous two-way data bind concept. Adding this with the previous example, we've got:

```javascript
function App(){
    return(
        <>
        <SomeComponent>prop1</>
        <SomeComponent>prop2</>
        <SomeComponent>prop3</>
        <SomeComponent>prop4</>
        </>
    );
}
```


```javascript
import {useState} from 'react';

export default function SomeComponent(props){
    const [counter, setCounter] = useState(1);

    function increment(){
        setCounter(counter + 1);
    }

    return(
        <>
        <span>{counter}</span>
        <someTag>{props.children}</someTag>
        </>
    );
}
```

## Starting:

There's two easy ways to create a new React application. [Create React App](https://create-react-app.dev/) (template) and [Next.js](https://nextjs.org/) (framework).

When you install node, it comes with npx, the package executor, so you can simply use:

```npx create-react-app podcastr```

And then, for starting your app, after installing yarn:

```yarn start```

If you want to create a react app with next:

```npx create-next-app podcastr```

Adding typescript:

```yarn add typescript @types/react @types/node -D```

Adding SASS:

```yarn add sass```

## Next.js

Gatsby and Next.js are frameworks that enable SSR (server-side rendering) and SSG (static-site generation). This is required for SEO (Search Engine Optimization), for Google, Bing, DuckDuckGo and other search engines to be able to index pages, for social media apps to generate some info cards, and so on.

### SSR (server-side rendering)

As the name implies, the HTML is rendered by the server. In this case, not by the same server that deals with business rules, but in this case, a Node.js server that runs the Next.js framework.

### SSG (static-site generation)

A static-site is basically a render that was cached, with a predefined time, to avoid rendering the application again, having many benefits, such as lower server usage.

### Tips:

- _document.tsx:

In this file you can define the base configuration for your app, that is not reloaded every time, different from a situation in which you've had put it on the _app.tsx file. For example:

```typescript
import Document, { Html, Head, Main, NextScript } from 'next/document'

export default class MyDocument extends Document {
    render(){
        return(
            <Html>
                <Head>
                <link rel="preconnect" href="https://fonts.gstatic.com" />
                <link href="https://fonts.googleapis.com/css2?family=Inter&family=Lexend:wght@500;600&display=swap" rel="stylesheet" />
                </Head>
                <body>
                    <Main />
                    <NextScript />
                </body>
            </Html>
        );
    }
}
```