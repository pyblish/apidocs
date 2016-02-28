## InstancePlugin.process

The primary processing mechanism of the [Instnace](Instance.md).

<br>
<br>
<br>

### Introduction

This method may be overridden in your plug-in subclasses to process the current [Instance](Instance.md).

<br>
<br>
<br>

## Example

```python
import pyblish.api

class ValidateInstances(pyblish.api.InstancePlugin):
    order = pyblish.api.ValidatorOrder

    def process(self, instance):
        assert instance.data["name"] == "MyInstance"
```
