## Plugin.active

A hint about whether or not to trigger the plug-in.

<br>
<br>
<br>

### Introduction

This attribute provides the Pyblish run-time with hint meaning "don't run". Under normal circumstances, a plugin with `active = False` is not processed.

<br>
<br>
<br>

### Example

```python
import pyblish.api

class MyCollector(pyblish.api.ContextPlugin):
    active = False
```

<div class="modified-date">{{ file.mtime }}</div>