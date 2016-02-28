## InstancePlugin

Process once per [Instance](instance.md).

| Source     | Added
|------------|---------
|[Link][]    | 1.3.0

Inherits [Plugin](Plugin.md)

[Link]: https://github.com/pyblish/pyblish-base/blob/f695fad94b995915495b4123c503f24d3419429a/pyblish/plugin.py#L350

<br>
<br>
<br>

### Usage

The `InstancePlugin` is used for processing each individual instance. It is typically used on [Instances](instance.md) created during [Collection](CollectorOrder), either to validate or extract, but can be thought of as just a general process on each available [Instance](instance.md).

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish

class MyValidator(pyblish.InstancePlugin):
    order = pyblish.ValidatorOrder
   
    def process(self, instance):
        assert instance.data["name"] == "MyInstance"
```