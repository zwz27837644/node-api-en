<!-- YAML
added: v1.6.0
-->

Flush the request headers.

For efficiency reasons, Node.js normally buffers the request headers until
`request.end()` is called or the first chunk of request data is written. It
then tries to pack the request headers and data into a single TCP packet.

That's usually desired (it saves a TCP round-trip), but not when the first
data is not sent until possibly much later.  `request.flushHeaders()` bypasses
the optimization and kickstarts the request.

