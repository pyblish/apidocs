## Events

This is a listing of default events in Pyblish.

<br>
<br>
<br>

**Pyblish**

| Event            | Arguments                            | Description
|:-----------------|:-------------------------------------|:------------
| `published`      | `context`                            | Emitted upon finished publish, regardless of failure
| `validated`      | `context`                            | Emitted upon finished validation

<br>

**Pyblish QML**

| Event              | Arguments                            | Description
|:-------------------|:-------------------------------------|:------------
| `instanceToggled`  | `instance, new_value, old_value` | An Instance was toggled in the GUI
| `pluginToggled`    | `plugin, new_value, old_value` | A Plug-in was toggled in the GUI

<br>
<br>
<br>

### Examples

```python
import pyblish.api

def on_published(context):
  has_error = any(result["error"] is not None for result in context.data["results"])
  print("Publishing %s" % ("finished" if has_error else "failed"))

pyblish.api.register_callback("published", on_published)
```
```python
import pyblish.api

def on_instance_toggled(instance, new_value, old_value):
  print("%s was toggled from %s to %s" % (instance, new_value, old_value))

pyblish.api.register_callback("instanceToggled", on_instance_toggled)
```
