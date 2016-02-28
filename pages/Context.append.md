Append [[Instances|Instance]] to a [[Context]].

<br>
<br>
<br>

### Introduction

A context may contain both content and metacontent, added via `.append()` and `.data[]` respectively.

The contents of a Context is the instances, and it's data global information about the environment in which publishing occurs, such as time of day or currently logged on user.

<br>
<br>
<br>

### Examples

```python
import pyblish.api as pyblish

context = pyblish.Context()
instance = pyblish.Instance(name="MyInstance")
context.append(instance)
```