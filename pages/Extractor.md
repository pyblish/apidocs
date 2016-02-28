An extractor writes [[instances|Instance]] to disk.

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish


@pyblish.log
class MyExtractor(pyblish.Extractor):
    """Documentation goes here"""

    families = ["myFamily"]
    hosts = ["python"]

    def process(self, instance):
        ...
```