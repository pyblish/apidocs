## InstancePlugin

Process once per [Instance](instance.md).

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