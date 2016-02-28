## ExtractorOrder

An extractor writes [instances](pages/instance.md) to disk.

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish

class MyExtractor(pyblish.InstancePlugin):
    """Documentation goes here"""
    
    order = pyblish.ExtractorOrder

    def process(self, instance):
        ...
```