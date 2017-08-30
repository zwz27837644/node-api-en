<!-- YAML
added: v0.9.4
changes:
  - version: v6.8.0
    pr-url: https://github.com/nodejs/node/pull/8834
    description: Instances of `Duplex` now return `true` when
                 checking `instanceof stream.Writable`.
-->

<!--type=class-->

Duplex streams are streams that implement both the [Readable][] and
[Writable][] interfaces.

Examples of Duplex streams include:

* [TCP sockets][]
* [zlib streams][zlib]
* [crypto streams][crypto]

