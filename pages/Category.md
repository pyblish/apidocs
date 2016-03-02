## Category

A visual separator for the parent menu of [Actions](Action.md).

<br>
<br>
<br>

### Public Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|               | \_\_init\_\_(name)

<br>
<br>
<br>

### Example

```python
import pyblish.api


class OpenInExplorer(pyblish.api.Action):
    label = "Open in Explorer"
    on = "failed" plug-in
    icon = "hand-o-up"
    
    def process(self, context):
        import subprocess
        subprocess.call("start .", shell=True)


class Validate(pyblish.api.Validator):
    actions = [
        # Order of items is preserved
        pyblish.api.Category("My Actions"),
        MyAction,
        pyblish.api.Separator,
    ]

    def process(self, context, plugin):
        raise Exception("Failed")
```