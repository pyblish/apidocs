## Plugin.actions

Associate [actions](Action.md) with a plug-in.

| Source     | Added
|------------|---------
|[Link][]    | 1.2.0

[Link]: https://github.com/pyblish/pyblish-base/blob/ac83f2a94bbde95bc2f6c4000d7c50e36a3d3b5f/pyblish/plugin.py#L346

<br>
<br>
<br>

### Example

```python
import pyblish.api

class MyAction(pyblish.api.Action):
    def process(self, context, plugin):
        self.log.info("I'm an action")

class MyCollector(pyblish.api.ContextPlugin):
    actions = [MyAction]
```

<div class="modified-date">{{ file.mtime }}</div>