
> Stability: 2 - Stable

<!--name=module-->

Node.js has a simple module loading system.  In Node.js, files and modules
are in one-to-one correspondence (each file is treated as a separate module).

As an example, consider a file named `foo.js`:

```js
const circle = require('./circle.js');
console.log(`The area of a circle of radius 4 is ${circle.area(4)}`);
```

On the first line, `foo.js` loads the module `circle.js` that is in the same
directory as `foo.js`.

Here are the contents of `circle.js`:

```js
const { PI } = Math;

exports.area = (r) => PI * r ** 2;

exports.circumference = (r) => 2 * PI * r;
```

The module `circle.js` has exported the functions `area()` and
`circumference()`. Functions and objects are added to the root of a module
by specifying additional properties on the special `exports` object.

Variables local to the module will be private, because the module is wrapped
in a function by Node.js (see [module wrapper](#modules_the_module_wrapper)).
In this example, the variable `PI` is private to `circle.js`.

The `module.exports` property can be assigned a new value (such as a function
or object).

Below, `bar.js` makes use of the `square` module, which exports a constructor:

```js
const square = require('./square.js');
const mySquare = square(2);
console.log(`The area of my square is ${mySquare.area()}`);
```

The `square` module is defined in `square.js`:

```js
// assigning to exports will not modify module, must use module.exports
module.exports = (width) => {
  return {
    area: () => width ** 2
  };
};
```

The module system is implemented in the `require('module')` module.

