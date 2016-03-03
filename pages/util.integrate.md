## `integrate`

Run integration-only via Python.

This function runs plug-ins of [IntegrationOrder](IntegrationOrder.md) and then stops. This is useful for getting hold of an integrated [Context](Context.md), bypassing validation and extraction, with [results](result.md).

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
| [Context](Context.md)    | integrate([context](Context.md)=None, [plugins](Plugin.md)=None)

<br>
<br>
<br>

### Example

```python
import pyblish.util
context = pyblish.util.collect()
pyblish.util.extract(context)
```