## Plugin.label

Provide an alternative, human-readable name of a plug-in.

<br>
<br>
<br>

### Introduction

Graphical user interfaces use the label as an alternative name for better readability. For example, you can use spaces and preserve case of a label.

<br>
<br>
<br>

### Example

```python
import pyblish.api

class MyCollector(pyblish.api.ContextPlugin):
    label = "My Collector"
```

<div class="modified-date">{{ file.mtime }}</div>