A collector creates [[instances|Instance]].

> Also known as [[Selector|Collector]]

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish


@pyblish.log
class MyCollector(pyblish.Collector):
    """Documentation goes here"""

    families = ["myFamily"]
    hosts = ["maya"]

    def process(self, context):
        instance = context.create_instance(name='MyInstance')
        instance.data['family'] = 'myFamily'
```
