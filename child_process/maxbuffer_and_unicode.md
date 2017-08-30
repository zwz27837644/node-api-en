
The `maxBuffer` option specifies the largest number of bytes allowed on `stdout`
or `stderr`. If this value is exceeded, then the child process is terminated.
This impacts output that includes multibyte character encodings such as UTF-8 or
UTF-16. For instance, `console.log('中文测试')` will send 13 UTF-8 encoded bytes
to `stdout` although there are only 4 characters.

