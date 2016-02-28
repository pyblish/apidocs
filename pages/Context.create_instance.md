Create [Instances](pages/Instance.md) for a given [Context](pages/Context.md).

<br>
<br>
<br>

### Introduction

Create an instance and automatically make it a child of the calling context, returns the newly created [Instance](pages/Instance.md).

```python
import pyblish.api
context = pyblish.api.Context()
instance = context.create_instance(name="MyInstance")
```