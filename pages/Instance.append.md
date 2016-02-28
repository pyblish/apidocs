## Instance.append

Append *content* to an [Instance](pages/Instance.md).

<br>
<br>
<br>

### Introduction

The content of an [Instance](pages/Instance.md) is a reflection of the content in the resulting file(s) on disk.

An instance may contain both content and metacontent, added via `.append()` and `.data[]` respectively. You can think of the contents of an instance as the bytes for a file, whereas metacontent represents additional information about an instance, such as author and date modified.

When used within a host, the content typically refers to the part of a workspace that is to be published, such as a the physical nodes making up a character model or rig.

<br>
<br>
<br>

### Examples

```python
import pyblish.api

instance = pyblish.api.Instance(name="Car")
instance.append("wheels")
instance.append("engine")
instance[:] = ["wheels", "engine"]
instance[0] = "feet"
```