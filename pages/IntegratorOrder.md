## IntegratorOrder

A integrator integrates [instances](instance.md) with a pipeline.

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish

class MyIntegrator(pyblish.InstancePlugin):
    """Integrate to disk"""
    
    order = pyblish.IntegratorOrder

    def process(self, instance):
        import shutil
        shutil.copytree(
            src=instance.data["sourceDir"],
            dst="/server/{name}/{fname}".format(
                **instance.data)
        )
```