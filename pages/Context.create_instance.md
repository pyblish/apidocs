Create [[Instances|Instance]] for a given [[Context]].

<br>
<br>
<br>

### Introduction

Create an instance and automatically make it a child of the calling context, returns the newly created [[Instance]].

```python
import pyblish.api
context = pyblish.api.Context()
instance = context.create_instance(name="MyInstance")
```