## `publish`

Publish via Python.

| Source     | Added
|------------|---------
|[Link][]    | 1.0.16

[Link]: https://github.com/pyblish/pyblish-base/commit/68ded825ea07b6de3bd5a791628815a9394d6156

<br>
<br>
<br>

### Description

This function runs all currently discoverable plug-ins and is especially useful when running without a GUI or to run remotely.

<br>
<br>
<br>

### Argument Signature

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
| [Context](Context.md)    | publish([context](Context.md)=None, [plugins](Plugin.md)=None)

<br>
<br>
<br>

### Example

```python
import pyblish.util
context = pyblish.util.publish()
```