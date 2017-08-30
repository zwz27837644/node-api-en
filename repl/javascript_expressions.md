
The default evaluator supports direct evaluation of JavaScript expressions:

<!-- eslint-skip -->
```js
> 1 + 1
2
> const m = 2
undefined
> m + 1
3
```

Unless otherwise scoped within blocks or functions, variables declared
either implicitly or using the `const`, `let`, or `var` keywords
are declared at the global scope.

