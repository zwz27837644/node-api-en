<!-- YAML
added: v0.1.16
-->

The `exports` variable is available within a module's file-level scope, and is
assigned the value of `module.exports` before the module is evaluated.

It allows a shortcut, so that `module.exports.f = ...` can be written more
succinctly as `exports.f = ...`. However, be aware that like any variable, if a
new value is assigned to `exports`, it is no longer bound to `module.exports`:

```js
module.exports.hello = true; // Exported from require of module
exports = { hello: false };  // Not exported, only available in the module
```

When the `module.exports` property is being completely replaced by a new
object, it is common to also reassign `exports`, for example:

<!-- eslint-disable func-name-matching -->
```js
module.exports = exports = function Constructor() {
  // ... etc.
};
```

To illustrate the behavior, imagine this hypothetical implementation of
`require()`, which is quite similar to what is actually done by `require()`:

```js
function require(/* ... */) {
  const module = { exports: {} };
  ((module, exports) => {
    // Module code here. In this example, define a function.
    function someFunc() {}
    exports = someFunc;
    // At this point, exports is no longer a shortcut to module.exports, and
    // this module will still export an empty default object.
    module.exports = someFunc;
    // At this point, the module will now export someFunc, instead of the
    // default object.
  })(module, module.exports);
  return module.exports;
}
```

