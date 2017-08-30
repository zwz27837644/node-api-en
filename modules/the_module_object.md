<!-- YAML
added: v0.1.16
-->

<!-- type=var -->
<!-- name=module -->

* {Object}

In each module, the `module` free variable is a reference to the object
representing the current module.  For convenience, `module.exports` is
also accessible via the `exports` module-global. `module` is not actually
a global but rather local to each module.

