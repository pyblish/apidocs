Override this in a plug-in to process the [[Instance|API Instance]]

<br>
<br>
<br>

### Introduction

This method may be overridden in your plug-in subclasses to process the current [[Instance|API Instnace]]. If overridden, Pyblish will execute this method at the opportune time.

<br>
<br>
<br>

### Implementation

The implementation of your sub-class is dependent on the task you would like it to perform, read more about best-practices and use-cases in the [[Strategies]] section.

**Example**

```python
import pyblish.api. as pyblish

class ValidateInstance(pyblish.Validator):
  hosts = ["python"]
  families = ["myFamily"]
  def process_instance(self, instance):
    if instance.data("name") != "Marcus":
      raise pyblish.ValidationError("Invalid name")
```