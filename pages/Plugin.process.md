The primary processing mechanism of Pyblish.

<br>
<br>
<br>

### Introduction

This method may be overridden in your plug-in subclasses to process the current [Context](pages/Context.md).

<br>
<br>
<br>

### Implementation

The implementation of your sub-class is dependent on the task you would like it to perform, read more about best-practices and use-cases in the [Strategies](https://github.com/pyblish/pyblish/wiki/Strategies) section.

**Example**

```python
import pyblish.api

class SelectInstances(pyblish.api.Selector):
  def process(self, context):
    context.create_instance(name="MyInstance", family="myFamily")
```