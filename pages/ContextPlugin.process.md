## ContextPlugin.process

The primary processing mechanism of the [Context](Context.md).

<br>
<br>
<br>

### Introduction

This method may be overridden in your plug-in subclasses to process the current [Context](Context.md).

<br>
<br>
<br>

## Example

```python
import pyblish.api

class CollectInstances(pyblish.api.ContextPlugin):
    order = pyblish.api.CollectorOrder

    def process(self, context):
        context.create_instance("MyInstance")
```