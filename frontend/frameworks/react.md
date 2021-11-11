# React:

Open-source front-end javascript library, developed initially by Facebook, with focus on dynamic components. I've put it on frameworks because with its ecosystem integration, and many libraries being almost 'mandatory' on an actual project, it basically turns it into a framework.

## Starting:

There's two easy ways to create a new React application. [Create React App](https://create-react-app.dev/) (template) and [Next.js](https://nextjs.org/) (framework).

Create-react-app:

```npx create-react-app app-name```

And then, for starting your app:

```npm start```

If you want to create a react app with next (note that the project will have some different configurations, including the index.html not necessarily existing, and yarn usage by default):

```npx create-next-app podcastr```

Adding typescript with yarn:

```yarn add typescript @types/react @types/node -D```

Adding SASS with yarn:

```yarn add sass```

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

### JSX:

"JSX is a syntax extension to JavaScript. React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages", [React](https://reactjs.org/docs/introducing-jsx.html).

```jsx
const element = <h1>Hello, world!</h1>;
```

### React DOM:

"The virtual DOM (VDOM) is a programming concept where an ideal, or “virtual”, representation of a UI is kept in memory and synced with the “real” DOM by a library such as ReactDOM. This process is called reconciliation.

This approach enables the declarative API of React: You tell React what state you want the UI to be in, and it makes sure the DOM matches that state. This abstracts out the attribute manipulation, event handling, and manual DOM updating that you would otherwise have to use to build your app", [React](https://reactjs.org/docs/faq-internals.html).

### Components (Function and Class Components):

"Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.

The simplest way to define a component is to write a JavaScript function:

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

This function is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element. We call such components “function components” because they are literally JavaScript functions.

You can also use an ES6 class to define a component:

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

The above two components are equivalent from React’s point of view", [React](https://reactjs.org/docs/components-and-props.html).

They can also compose, and be rendered as many times as we want, but React puts as a good practice to have a component be as small as we possibly can, so they become more reusable.

Also, react recommends that all React components must act like pure functions with respect to their props. Example of an impure function (changes its input):

```jsx
function withdraw(account, amount) {
  account.total -= amount;
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

### State and Lifecycle:



### State and Effect Hook:

React uses the useState method for dynamic variable changes, for example, in contrast with Angular, that uses the famous two-way data bind concept. Adding this with the previous example, we've got:

```javascript
//index.js
import React from "react";
import ReactDOM from "react-dom";

import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```


```javascript
//App.js
import React, { useState } from 'react';

export default function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);
  if (count % 2 === 0) {
    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
          Click me (we have an even number)
        </button>
      </div>
    );
  } else {
    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
          Click me (we have an odd number)
        </button>
      </div>
    );
  }
}
```

### Context API:

When developing a react application, there's often the need to share information between components, for example on the podcastr project, between a 'play' action on the episode description component, and the player component. This can be solved using the context API:

```javascript
//src.pages._app.tsx
import '../styles/global.scss'
import { Header } from '../components/Header';
import { Player } from '../components/Player';
import { PlayerContext } from '../contexts/PlayerContext';
import styles from '../styles/app.module.scss'

function MyApp({ Component, pageProps }) {
  return (
    <PlayerContext.Provider value={'Diego'}>
      <div className={styles.wrapper}>
        <main>
          <Header />
          <Component {...pageProps} />
        </main>
        <Player />
      </div>
    </PlayerContext.Provider>
  );
}

export default MyApp

//src.contexts.PlayerContext
import { createContext } from 'react';

export const PlayerContext = createContext('Diego');
/*The createContext argument just defines how the data's
supposed to be like*/
```

### Refs:

"In the typical React dataflow, props are the only way that parent components interact with their children. To modify a child, you re-render it with new props. However, there are a few cases where you need to imperatively modify a child outside of the typical dataflow. The child to be modified could be an instance of a React component, or it could be a DOM element. For both of these cases, React provides an escape hatch", [React's Refs](https://reactjs.org/docs/refs-and-the-dom.html).

```javascript
//src.components.Player.index.tsx
export function Player() {
  const audioRef = useRef <HTMLAudioElement> (null);
  //...
  <audio
    src={episode.url}
    ref={audioRef}
    autoPlay
    onPlay={() => setPlayingState(true)}
    onPause={() => setPlayingState(false)}
  />
}
```

### Side Effects:

"The Effect Hook lets you perform side effects in function components. Data fetching, setting up a subscription, and manually changing the DOM in React components are all examples of side effects. Whether or not you’re used to calling these operations “side effects” (or just “effects”), you’ve likely performed them in your components before.

What does useEffect do? By using this Hook, you tell React that your component needs to do something after render. React will remember the function you passed (we’ll refer to it as our “effect”), and call it later after performing the DOM updates. In this effect, we set the document title, but we could also perform data fetching or call some other imperative API", [React's Effect Hook](https://reactjs.org/docs/hooks-effect.html).

Based on the previous example:

```javascript
//src.components.Player.index.tsx
export function Player() {
  const audioRef = useRef <HTMLAudioElement> (null);

  useEffect(() => {
        if (!audioRef.current) {
            return;
        }

        if (isPlaying) {
            audioRef.current.play();
        } else {
            audioRef.current.pause();
        }
    }, [isPlaying]);
  //...
  <audio
    src={episode.url}
    ref={audioRef}
    autoPlay 
  />
}
```

### React Node:

"The primary type or value that is created when using React is known as a React node. A React node is defined as a light, stateless, immutable, virtual representation of a DOM node", [React Enlightenment](https://www.reactenlightenment.com/react-nodes/4.1.html).

Basically a type you can refer to compare if an element is an React/Html element. Usage example:

```javascript
import { ReactNode } from 'react';

interface ComponentProps {
    children: ReactNode;
};

export function Component (ComponentProps: ComponentProps){
  //doSomething
}
```

## Tips:

Lorem ipsum dolor sit amet, consectetur adipis.

## Next.js

Gatsby and Next.js are frameworks that enable SSR (server-side rendering) and SSG (static-site generation). This is required for SEO (Search Engine Optimization), for Google, Bing, DuckDuckGo and other search engines to be able to index pages, for social media apps to generate some info cards, and so on.

### SSR (server-side rendering)

As the name implies, the HTML is rendered by the server. In this case, not by the same server that deals with business rules, but in this case, a Node.js server that runs the Next.js framework.

### SSG (static-site generation)

A static-site is basically a render that was cached, with a predefined time, to avoid rendering the application again, having many benefits, such as lower server usage.

### Tips:

#### _document.tsx:

In this file you can define the base configuration for your app, that is not reloaded every time, different from a situation in which you've had put it on the _app.tsx file. For example:

```javascript
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

#### css/scss modules:

When you define a css/scss module with next, for example: `styles.module.scss`, this specific css definition only applies to the specific component you're working on. That is, if you have other css classes named the same through your application, there's no problem.

Example importing the module's styles:

```javascript
//Header/styles.module.scss
.headerContainer {
    background: var(--white);
    height: 6.5rem;
    display: flex;
    align-items: center;
    padding: 2rem 4rem;
    border-bottom: 1px solid var(--gray-100);
}

//Header/index.tsx
import styles from './styles.module.scss';

export function Header() {
    return (
        <header className={styles.headerContainer}>
            <img src="/logo.svg" alt="Podcastr"></img>

            <p>O melhor para você ouvir, sempre</p>

            <span>Qui, 8 Abril</span>
        </header>
    );
}
```

#### Consuming API's:

There's three different ways to consume an API, using each "methodology": SPA, SSR and SSG.

SPA:

```javascript
import { useEffect } from "react"

export default function Home() {
  useEffect(() => {
    fetch('http://localhost:3333/episodes')
    .then(response => response.json())
    .then(data => console.log(data));
  }, []); 

  return (
    <h1>Index</h1>
  )
}

/*In this way, the fetch happens every time
the component is loaded. Problem? Crawlers will
not wait for the request to complete.*/
```

SSR:

```javascript
export default function Home(props) {
  return (
    <div>
      <h1>Index</h1>
      <p>{JSON.stringify(props.episodes)}</p>
    </div>
  )
}

export async function getServerSideProps() {
  const response = await fetch('http://localhost:3333/episodes')
  const data = await response.json()
  return {
    props: {
      episodes: data,
    }
  }
}

/*In this way, the fetch happens every time
a person accesses the app. Problem? Many server
requests, unnecessarily.*/
```

SSG:

```javascript
export default function Home(props) {
  return (
    <div>
      <h1>Index</h1>
      <p>{JSON.stringify(props.episodes)}</p>
    </div>
  )
}

export async function getStaticProps() {
  const response = await fetch('http://localhost:3333/episodes')
  const data = await response.json()
  return {
    props: {
      episodes: data,
    },
    revalidate: 28800 // 60 * 60 * 8 -- seconds in 8h
  }
}

/*Literally changing the method's name.
In this way, the fetch happens on the defined
revalidate specified time (on seconds).*/
```

#### Image:

Next's Image, doing all the magic:

```javascript
<Image width={192} height={192} src={episode.thumbnail} alt={episode.title} />
```

#### Routing:

The rest of the url, that is, the part that comes after the domain extension, is called slug. To avoid making the common query parameters routing, we're able to specify 'paths' on our application, with next. 

On the pages folder, just create a folder with the desired path, create the corresponding 'parameter' you wish to receive inside brackets ([]) and you're done. Example:

```javascript
/*
/pages/episodes/[slug].tsx
*/

import { useRouter } from 'next/router';

export default function Episode() {
    const router = useRouter();

    return (
        <h1>{router.query.slug}</h1>
    );
}

/*
Then, we're able to access it by the following url:
(application domain, for example localhost:3000)/episodes/slugText.

Then, the page should show exactly 'slugText', inside a h1.
Or some other text/'path';

For an easy routing, you could do something like:
*/

<a href={`/episodes/${episode.id}`}>{episode.title}</a>
```

But that is not a silver bullet, as it changes the page and reloads all necessary files. To be able to optimize this:

```javascript
/*
/pages/index.tsx
*/

import Link from 'next/link';

/*
Instead of <a href={`/episodes/${episode.id}`}>{episode.title}</a>:
*/

<Link href={`/episodes/${episode.id}`}>
  <a>{episode.title}</a>
</Link>
```

#### Incremental static regeneration:

Incremental static regeneration is, as Diego Fernandes' said (NLW #5), a 'dynamic static pages' technique that allow us to control how new static pages are generated with dynamic content.

"With getStaticProps you don't have to stop relying on dynamic content, as static content can also be dynamic. Incremental Static Regeneration allows you to update existing pages by re-rendering them in the background as traffic comes in.

Inspired by stale-while-revalidate, background regeneration ensures traffic is served uninterruptedly, always from static storage, and the newly built page is pushed only after it's done generating.", [Next.js](https://nextjs.org/docs/basic-features/data-fetching#incremental-static-regeneration).

For it to be also able to dynamically generate static routes, we're able to control it like that:

```javascript
export const getStaticPaths: GetStaticPaths = async () => {
    return ({
        paths: [
            {
                params: {
                    slug: 'a-importancia-da-contribuicao-em-open-source'
                    //it will only render this route/page
                }
            }
        ],
        fallback: 'false' // returns a 404 error
        /*
        fallback: 'true' -- tries to get the data required to render the page,
        making the request client-side

        fallback: 'blocking' -- tries to get the data required to render the page, making the request server-side (on next's server), and the user's
        only redirected after the page has rendered

        both fallback true and blocking are examples of incremental static regeneration
        */
    });
};
```

While using fallback true, we can be presented with an error, as Next tries to render the page with undefined values. This can be solved using the useRouter import, as seen below:

```javascript
import { useRouter } from 'next/router';

export default function Episode({ episode }: EpisodeProps) {
    const router = useRouter();

    if(router.isFallback){
      return (
        <p>Carregando...</p>
      );
    }

    return (
        <div className={styles.episode}>
            <div className={styles.thumbnailContainer}>
                <Link href="/">
                    <button type="button">
                        <img src="/arrow-left.svg" alt="Voltar" />
                    </button>
                </Link>
                <Image width={700} height={160} src={episode.thumbnail}
                    objectFit="cover"></Image>
                <button type="button">
                    <img src="/play.svg" alt="Tocar Episódio" />
                </button>
            </div>

            <header>
                <h1>{episode.title}</h1>
                <span>{episode.members}</span>
                <span>{episode.publishedAt}</span>
                <span>{episode.durationAsString}</span>
            </header>

            <div className={styles.description}
                dangerouslySetInnerHTML={{ __html: episode.description }} />
        </div>
    );
}
```

#### Using dynamic page titles:

"We expose a built-in component for appending elements to the head of the page", [Next.js](https://nextjs.org/docs/api-reference/next/head).

```javascript
import Head from 'next/head';

//on any function that returns html (React Node's)
<Head>
  <title>Home | Podcastr</title>
</Head>
```