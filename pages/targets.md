## Targets

Filter plug-ins by an arbitrary "target", such as `Global Assets`, `Local User`, `Animators`, `Everyone with Read Hair` etc.

This differs from `families` in that the caller provides the data, as opposed to the DCC. Useful for special-purpose GUIs or publishing tasks.

<br>
<br>
<br>

### Targets Workflow

This release enables assigning targets to plugins. Targets are registered globally so you can enable and disable plugins based on targets.
This workflow helps when needing to run plugins from the same host but with different sets of plugins. Possible use cases could be submitting to a render farm, or publishing to a different location.

Targets work the same way as families, so a wildcard of ```*``` enables the plugin for all targets. Since all plugins are registered with ```*``` as targets, this workflow is backwards compatible with existing plugins that has not overwritten the targets attribute.

**Targets with `publish.util`**


```python
from pyblish import api, util


class plugin(api.ContextPlugin):
targets = ["custom"]

def process(self, context):
self.log.info("Custom target publishing.")


api.register_plugin(plugin)

util.publish(targets=["custom"])
```

<br>
<br>
<br>

#### Example

```python
import pyblish.api
import pyblish.util

class StudioPlugin(pyblish.api.ContextPlugin):

    targets = ["studio"]

    def process(self, context):
        self.log.info("Publishing to studio library.")

class ProjectPlugin(pyblish.api.ContextPlugin):

    def process(self, context):
        self.log.info("Publishing to project library.")


pyblish.api.register_plugin(StudioPlugin)
pyblish.api.register_plugin(ProjectPlugin)

# Publishing with ProjectPlugin only.
pyblish.util.publish()

# Publishing with ProjectPlugin and StudioPlugin.
pyblish.api.register_target("studio")
pyblish.util.publish()
```

<div class="modified-date">{{ file.mtime }}</div>
