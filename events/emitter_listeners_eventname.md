<!-- YAML
added: v0.1.26
changes:
  - version: v7.0.0
    pr-url: https://github.com/nodejs/node/pull/6881
    description: For listeners attached using `.once()` this returns the
                 original listeners instead of wrapper functions now.
-->
- `eventName` {any}

Returns a copy of the array of listeners for the event named `eventName`.

```js
server.on('connection', (stream) => {
  console.log('someone connected!');
});
console.log(util.inspect(server.listeners('connection')));
// Prints: [ [Function] ]
```

