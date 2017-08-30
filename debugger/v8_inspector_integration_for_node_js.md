
V8 Inspector integration allows attaching Chrome DevTools to Node.js
instances for debugging and profiling. It uses the [Chrome Debugging Protocol][].

V8 Inspector can be enabled by passing the `--inspect` flag when starting a
Node.js application. It is also possible to supply a custom port with that flag,
e.g. `--inspect=9222` will accept DevTools connections on port 9222.

To break on the first line of the application code, pass the `--inspect-brk`
flag instead of `--inspect`.

```txt
$ node --inspect index.js
Debugger listening on 127.0.0.1:9229.
To start debugging, open the following URL in Chrome:
    chrome-devtools://devtools/bundled/inspector.html?experiments=true&v8only=true&ws=127.0.0.1:9229/dc9010dd-f8b8-4ac5-a510-c1a114ec7d29
```

(In the example above, the UUID dc9010dd-f8b8-4ac5-a510-c1a114ec7d29
at the end of the URL is generated on the fly, it varies in different
debugging sessions.)

[Chrome Debugging Protocol]: https://chromedevtools.github.io/debugger-protocol-viewer/
[TCP-based protocol]: #debugger_tcp_based_protocol
