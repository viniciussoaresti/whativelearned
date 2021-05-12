# Node.js:

"Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine", [NodeJS](https://nodejs.org/en/).

## Concepts:

- EventEmitter:

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