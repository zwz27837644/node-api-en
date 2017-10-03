
Under the hood, [`dns.lookup()`][] uses the same operating system facilities
as most other programs. For instance, [`dns.lookup()`][] will almost always
resolve a given name the same way as the `ping` command. On most POSIX-like
operating systems, the behavior of the [`dns.lookup()`][] function can be
modified by changing settings in nsswitch.conf(5) and/or resolv.conf(5),
but note that changing these files will change the behavior of _all other
programs running on the same operating system_.

Though the call to `dns.lookup()` will be asynchronous from JavaScript's
perspective, it is implemented as a synchronous call to getaddrinfo(3) that runs
on libuv's threadpool. This can have surprising negative performance
implications for some applications, see the [`UV_THREADPOOL_SIZE`][]
documentation for more information.

Note that various networking APIs will call `dns.lookup()` internally to resolve
host names. If that is an issue, consider resolving the hostname to and address
using `dns.resolve()` and using the address instead of a host name. Also, some
networking APIs (such as [`socket.connect()`][] and [`dgram.createSocket()`][])
allow the default resolver, `dns.lookup()`, to be replaced.

