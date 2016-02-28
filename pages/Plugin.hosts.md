## Plugin.hosts

Supported hosts.

<br>
<br>
<br>

### Introduction

Read about the architecture of plug-ins for a better understanding of the `hosts` attribute.

- [Plug-in System](https://github.com/pyblish/pyblish/wiki/Plugin-system)

<br>
<br>
<br>

### Implementation

Each integration provides support for a given host, for detailed information about plug-ins in a particular host, see its corresponding documentation.

```python
class MyPlugin(...):
   hosts = ["maya"]
```

**See also**

- [Pyblish][p]

[p]: https://github.com/pyblish/pyblish/wiki/Modularisation#organisation