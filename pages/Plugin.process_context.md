Override this in a plug-in to process the [[Context]]

<br>
<br>
<br>

### Introduction

This method may be overridden in your plug-in subclasses to process the current [[Context]]. If overridden, Pyblish will execute this method at the opportune time.

<br>
<br>
<br>

### Implementation

The implementation of your sub-class is dependent on the task you would like it to perform, read more about best-practices and use-cases in the [Strategies](https://github.com/pyblish/pyblish/wiki/Strategies) section.

**Example**

```python
import pyblish.api. as pyblish

class SelectInstances(pyblish.Selector):
  hosts = ["python"]
  def process_context(self, context):
    instance = context.create_instance(name="MyInstance")
    instance.set_data("family", "myFamily")
```