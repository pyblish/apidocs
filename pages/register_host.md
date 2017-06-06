### register_host

Register supported host.

| Source     | Added
|------------|---------
|            | 1.1.3

<br>
<br>
<br>

### Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|            | [register_host](register_gui)(str)
|            | [deregister_host](deregister_host)(str)
|            | [registered_hosts](registered_hosts)()


<br>
<br>
<br>

### Description

Limit availability of plug-ins by host, such as Maya.

Integrations, such as `pyblish-maya` and `pyblish-nuke` register their own corresponding host automatically. Additional hosts may be registered by the end-user to customise the available plug-ins at time of publish.

<br>
<br>
<br>

### Example

```python
from pyblish import api

class CollectObjectSets(api.ContextPlugin):
    """Collect things only Maya would know"""
    order = api.CollectorOrder
    hosts = ["maya"]
    def process(self, context):
        from maya import cmds
        for objset in cmds.ls(type="objectSet"):
        context.create_instance(objset)
```

<div class="modified-date">{{ file.mtime }}</div>