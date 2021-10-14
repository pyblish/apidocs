## Plug-in System

Learn about how things happen in Pyblish.

<br>
<br>
<br>


### Introduction

There are three ways in which a plug-in is associated with a particular set of data.

1. By availability
1. By host
1. By family

Availability is determined by registering a given plug-in to Pyblish, for example by calling [register_plugin_path()](register_plugin_path.md). Once a plug-in is made available, it must also match the currently running host.

```python
class MyPlugin(...):
  hosts = ["maya"]
```

If the host matches, a plug-in is put to the final test; it's supported families.

```python
class MyPlugin(...):
  families = ["myFamily"]
```

**See also**

- [Plugin.hosts](Plugin.hosts.md)


<br>
<br>
<br>

### Data

These data members are included.

| Data                  | Description
|-----------------------|-------------------------------------------
| currentFile          | Current working file
| workspaceDir         | Higher-level directory of current file
| user                  | Currently logged on user
| cwd                   | Current working directory (of Python interpreter)

**Example**

```python
import pyblish.util
context = pyblish.util.collect()
print context.data["currentFile"]
```

[1]: https://github.com/pyblish/pyblish.api/wiki/register_plugin_path
[2]: https://api.pyblish.com/pyblish.api/plugin/plugin.hosts
