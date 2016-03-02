## CollectorOrder

Collectors create [instances](Instance.md).

<br>
<br>
<br>

### Example

```python
import os
import pyblish.api as pyblish

class MyCollector(pyblish.ContextPlugin):
    """This plug-in identifies content and creates instances"""

    order = pyblish.CollectorOrder

    def process(self, context):
        for folder in os.listdir("."):
            if not folder.endswith("_asset"):
                continue
            instance = context.create_instance(folder)
            instance.data["family"] = "asset"
```

<div class="modified-date">{{ file.mtime }}</div>