
<!--type=misc-->

Throughout the documentation are indications of a section's
stability. The Node.js API is still somewhat changing, and as it
matures, certain parts are more reliable than others. Some are so
proven, and so relied upon, that they are unlikely to ever change at
all. Others are brand new and experimental, or known to be hazardous
and in the process of being redesigned.

The stability indices are as follows:

```txt
Stability: 0 - Deprecated
This feature is known to be problematic, and changes may be planned. Do
not rely on it. Use of the feature may cause warnings to be emitted.
Backwards compatibility across major versions should not be expected.
```

```txt
Stability: 1 - Experimental
This feature is still under active development and subject to non-backwards
compatible changes, or even removal, in any future version. Use of the feature
is not recommended in production environments. Experimental features are not
subject to the Node.js Semantic Versioning model.
```

*Note*: Caution must be used when making use of `Experimental` features,
particularly within modules that may be used as dependencies (or dependencies
of dependencies) within a Node.js application. End users may not be aware that
experimental features are being used, and therefore may experience unexpected
failures or behavioral changes when changes occur. To help avoid such surprises,
`Experimental` features may require a command-line flag to explicitly enable
them, or may cause a process warning to be emitted. By default, such warnings
are printed to `stderr` and may be handled by attaching a listener to the
`process.on('warning')` event.

```txt
Stability: 2 - Stable
The API has proven satisfactory. Compatibility with the npm ecosystem
is a high priority, and will not be broken unless absolutely necessary.
```

