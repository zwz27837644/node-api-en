<!-- YAML
added: v0.1.29
-->

* `chunk` {string|Buffer}
* `encoding` {string}
* `callback` {Function}

Sends a chunk of the body.  By calling this method
many times, a request body can be sent to a
server--in that case it is suggested to use the
`['Transfer-Encoding', 'chunked']` header line when
creating the request.

The `encoding` argument is optional and only applies when `chunk` is a string.
Defaults to `'utf8'`.

The `callback` argument is optional and will be called when this chunk of data
is flushed.

Returns `request`.

