<!-- YAML
added: v0.1.100
-->
* `data` {any}
* `...args` {any}

Prints to `stdout` with newline. Multiple arguments can be passed, with the
first used as the primary message and all additional used as substitution
values similar to printf(3) (the arguments are all passed to
[`util.format()`][]).

```js
const count = 5;
console.log('count: %d', count);
// Prints: count: 5, to stdout
console.log('count:', count);
// Prints: count: 5, to stdout
```

See [`util.format()`][] for more information.

