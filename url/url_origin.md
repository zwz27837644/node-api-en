
* {string}

Gets the read-only serialization of the URL's origin.

```js
const { URL } = require('url');
const myURL = new URL('https://example.org/foo/bar?baz');
console.log(myURL.origin);
// Prints https://example.org
```

```js
const { URL } = require('url');
const idnURL = new URL('https://你好你好');
console.log(idnURL.origin);
// Prints https://xn--6qqa088eba

console.log(idnURL.hostname);
// Prints xn--6qqa088eba
```

