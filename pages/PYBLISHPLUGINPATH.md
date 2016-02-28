## PYBLISHPLUGINPATH

One or more paths from which to discover Pyblish plug-ins.

<br>
<br>
<br>

### Usage

The environment variable is typically set prior to launching an application, such that the given application can be tailored for a given task or project, and then have access to these plug-ins at run-time.

<br>
<br>
<br>

### Example

```python
import os
os.environ["PYBLISHPLUGINPATH"] = r"c:\pyblish_plugins"
os.environ["PYBLISHPLUGINPATH"] = "/home/pyblish_plugins"
```