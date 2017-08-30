
> Stability: 2 - Stable

The `console` module provides a simple debugging console that is similar to the
JavaScript console mechanism provided by web browsers.

The module exports two specific components:

* A `Console` class with methods such as `console.log()`, `console.error()` and
  `console.warn()` that can be used to write to any Node.js stream.
* A global `console` instance configured to write to [`process.stdout`][] and
  [`process.stderr`][].  The global `console` can be used without calling
  `require('console')`.

***Warning***: The global console object's methods are neither consistently
synchronous like the browser APIs they resemble, nor are they consistently
asynchronous like all other Node.js streams. See the [note on process I/O][] for
more information.

Example using the global `console`:

```js
console.log('hello world');
// Prints: hello world, to stdout
console.log('hello %s', 'world');
// Prints: hello world, to stdout
console.error(new Error('Whoops, something bad happened'));
// Prints: [Error: Whoops, something bad happened], to stderr

const name = 'Will Robinson';
console.warn(`Danger ${name}! Danger!`);
// Prints: Danger Will Robinson! Danger!, to stderr
```

Example using the `Console` class:

```js
const out = getStreamSomehow();
const err = getStreamSomehow();
const myConsole = new console.Console(out, err);

myConsole.log('hello world');
// Prints: hello world, to out
myConsole.log('hello %s', 'world');
// Prints: hello world, to out
myConsole.error(new Error('Whoops, something bad happened'));
// Prints: [Error: Whoops, something bad happened], to err

const name = 'Will Robinson';
myConsole.warn(`Danger ${name}! Danger!`);
// Prints: Danger Will Robinson! Danger!, to err
```

