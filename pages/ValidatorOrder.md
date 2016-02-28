## ValidatorOrder

A validator determines whether or not an [instance](pages/instance.md) is valid.

<br>
<br>
<br>

**Illustration**

```
  _______                                  _____
         |                                |
input    |------ is valid? ----- yes ---->|  output
  _______|           |                    |_____
     ^               |
     |               no
     |               |
     |_______________|
```

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish

class MyValidator(pyblish.InstancePlugin):
    """Documentation goes here"""

    order = pyblish.ValidatorOrder

    def process(self, instance):
        self.log.info("something")
```