<!-- YAML
added: v0.5.3
changes:
  - version: v8.4.0
    pr-url: https://github.com/nodejs/node/pull/14558
    description: The `%o` and `%O` specifiers are supported now.
-->

* `format` {string} A `printf`-like format string.

The `util.format()` method returns a formatted string using the first argument
as a `printf`-like format.

The first argument is a string containing zero or more *placeholder* tokens.
Each placeholder token is replaced with the converted value from the
corresponding argument. Supported placeholders are:

* `%s` - String.
* `%d` - Number (integer or floating point value).
* `%i` - Integer.
* `%f` - Floating point value.
* `%j` - JSON.  Replaced with the string `'[Circular]'` if the argument
contains circular references.
* `%o` - Object. A string representation of an object
  with generic JavaScript object formatting.
  Similar to `util.inspect()` with options `{ showHidden: true, depth: 4, showProxy: true }`.
  This will show the full object including non-enumerable symbols and properties.
* `%O` - Object. A string representation of an object
  with generic JavaScript object formatting.
  Similar to `util.inspect()` without options.
  This will show the full object not including non-enumerable symbols and properties.
* `%%` - single percent sign (`'%'`). This does not consume an argument.

If the placeholder does not have a corresponding argument, the placeholder is
not replaced.

```js
util.format('%s:%s', 'foo');
// Returns: 'foo:%s'
```

If there are more arguments passed to the `util.format()` method than the number
of placeholders, the extra arguments are coerced into strings then concatenated
to the returned string, each delimited by a space. Excessive arguments whose
`typeof` is `'object'` or `'symbol'` (except `null`) will be transformed by
`util.inspect()`.

```js
util.format('%s:%s', 'foo', 'bar', 'baz'); // 'foo:bar baz'
```

If the first argument is not a string then `util.format()` returns
a string that is the concatenation of all arguments separated by spaces.
Each argument is converted to a string using `util.inspect()`.

```js
util.format(1, 2, 3); // '1 2 3'
```

If only one argument is passed to `util.format()`, it is returned as it is
without any formatting.

```js
util.format('%% %s'); // '%% %s'
```

