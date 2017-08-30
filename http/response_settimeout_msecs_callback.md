<!-- YAML
added: v0.9.12
-->

* `msecs` {number}
* `callback` {Function}

Sets the Socket's timeout value to `msecs`.  If a callback is
provided, then it is added as a listener on the `'timeout'` event on
the response object.

If no `'timeout'` listener is added to the request, the response, or
the server, then sockets are destroyed when they time out.  If a handler is
assigned to the request, the response, or the server's `'timeout'` events,
timed out sockets must be handled explicitly.

Returns `response`.

