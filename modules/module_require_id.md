<!-- YAML
added: v0.5.1
-->

* `id` {string}
* Returns: {Object} `module.exports` from the resolved module

The `module.require` method provides a way to load a module as if
`require()` was called from the original module.

*Note*: In order to do this, it is necessary to get a reference to the
`module` object.  Since `require()` returns the `module.exports`, and the
`module` is typically *only* available within a specific module's code, it must
be explicitly exported in order to be used.

[`__dirname`]: #modules_dirname
[`__filename`]: #modules_filename
[`Error`]: errors.html#errors_class_error
[`module` object]: #modules_the_module_object
[`path.dirname()`]: path.html#path_path_dirname_path
[exports shortcut]: #modules_exports_shortcut
[module resolution]: #modules_all_together
[native addons]: addons.html
