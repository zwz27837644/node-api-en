
The default evaluator will, by default, assign the result of the most recently
evaluated expression to the special variable `_` (underscore).
Explicitly setting `_` to a value will disable this behavior.

<!-- eslint-skip -->
```js
> [ 'a', 'b', 'c' ]
[ 'a', 'b', 'c' ]
> _.length
3
> _ += 1
Expression assignment to _ now disabled.
4
> 1 + 1
2
> _
4
```

