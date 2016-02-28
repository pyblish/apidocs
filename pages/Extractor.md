An extractor writes [instances](pages/instance.md) to disk.

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish

class MyExtractor(pyblish.Extractor):
    """Documentation goes here"""

    families = ["myFamily"]
    hosts = ["python"]

    def process(self, instance):
        ...
```