## `extract`

Run extraction-only via Python.

| Source     | Added
|------------|---------
|[Link][]    | 1.0.16

[Link]: https://github.com/pyblish/pyblish-base/commit/68ded825ea07b6de3bd5a791628815a9394d6156

<br>
<br>
<br>

### Description

This function runs plug-ins of [ExtractionOrder](ExtractionOrder.md) and then stops. This is useful for getting hold of an extracted [Context](Context.md), bypassing validation, with [results](result.md).

<br>
<br>
<br>

### Argument Signature

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
| [Context](Context.md)    | extract([context](Context.md)=None, [plugins](Plugin.md)=None)

<br>
<br>
<br>

### Example

```python
import pyblish.util
context = pyblish.util.collect()
pyblish.util.extract(context)
```

<div class="modified-date">{{ file.mtime }}</div>