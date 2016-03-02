## Context.create_instance

Create [Instances](Instance.md) for a given [Context](Context.md).

<br>
<br>
<br>

### Introduction

Create an instance and automatically make it a child of the calling context, returns the newly created [Instance](Instance.md).

```python
import pyblish.api
context = pyblish.api.Context()
instance = context.create_instance(name="MyInstance")
```

<div class="modified-date">{{ file.mtime }}</div>