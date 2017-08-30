
* {string|number}

The `error.errno` property is a number or a string.
The number is a **negative** value which corresponds to the error code defined
in [`libuv Error handling`]. See uv-errno.h header file
(`deps/uv/include/uv-errno.h` in the Node.js source tree) for details. In case
of a string, it is the same as `error.code`.

