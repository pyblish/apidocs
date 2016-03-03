## `collect`

Run collection via Python.

This function runs plug-ins of [CollectionOrder](CollectionOrder.md) and then stops. This is useful for getting hold of a populated [Context](Context.md)

| Source     | Added
|------------|---------
|[Link][]    | 1.0.16

[Link]: https://github.com/pyblish/pyblish-base/commit/68ded825ea07b6de3bd5a791628815a9394d6156

<br>
<br>
<br>

### Argument Signature

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
| [Context](Context.md)    | collect([context](Context.md)=None, [plugins](Plugin.md)=None)

<br>
<br>
<br>

### Example

```python
import pyblish.util
context = pyblish.util.collect()
```