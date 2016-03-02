## Action

Process once, with [Context](context.md) and [Plugin](plugin.md) as input.

| Source     | Added
|------------|---------
|[Link][]    | 1.2.0

Inherits [Plugin](Plugin.md)

[Link]: https://github.com/pyblish/pyblish-base/commit/ac83f2a94bbde95bc2f6c4000d7c50e36a3d3b5f

<br>
<br>
<br>

### Public Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|               | [process](ContextPlugin.process.md)([context](Context.md), [plugin](plugin.md))

<br>
<br>
<br>

### Properties

| property                                       | type
|:-----------------------------------------------|:-----
| [icon](Action.icon.md)                   | str
| [on](Action.on.md)                       | str

<br>
<br>
<br>

### Usage

Attach any functionality to a plug-in and tailor it to a particular state; like an action only available via a failed validator, or a successful extraction, or just all-round functionality associated with a particular plug-in.

![image](https://cloud.githubusercontent.com/assets/2152766/13439097/da8cf9da-dfe3-11e5-8db1-7c33f31046fd.png)

Each action have access to both the Context and it's parent plug-in via dependency injection, along with any other custom dependencies already available to plug-ins in general.

Actions in QML are arranged in a menu with optional customisable groups and separators. Actions with any kind of implementation error show up as well, including a helpful error message for simplified debugging. 

**Dependency Injected**

These objects are available via dependency injection by default.

- `context`: The global context
- `plugin`: The parent plug-in

**Full list of features**

- Per-plugin actions
- Action API ~= Plug-in API, it is more or less a 1-1 match between their interfaces, including `process()` and `label`.
- Standard logging and exception reporting, identical to plug-ins
- Standard dependency injection still applies; can still inject custom functionality
- Customisable icon per action, from [Awesome Icon][1]
- Customisable availability
 - `all`: Always
 - `processed`: After plug-in has been processed
 - `failed`: After plug-in has been processed, and failed
 - `succeeded`: After plug-in has been processed, and succeeded

<br>
<br>
<br>

### Example

```python
class OpenInExplorer(pyblish.api.Action):
    label = "Open in Explorer"
    on = "failed"  # This action is only available on a failed plug-in
    icon = "hand-o-up"  # Icon from Awesome Icon
    
    def process(self, context):
        import subprocess
        subprocess.call("start .", shell=True)  # Launch explorer at the cwd


class Validate(pyblish.api.Validator):
    actions = [
        # Order of items is preserved
        pyblish.api.Category("My Actions"),
        MyAction,
        pyblish.api.Separator,
    ]

    def process(self, context, plugin):
        """The Context and parent Plug-in are available via dependency injection"""
        self.log.info("Standard log messages apply here.")
        raise Exception("Exceptions too.")
```

### Extended Example

Every possible combination of an action.

```python
class ContextAction(pyblish.api.Action):
    label = "Context action"

    def process(self, context):
        self.log.info("I have access to the context")
        self.log.info("Context.instances: %s" % str(list(context)))


class FailingAction(pyblish.api.Action):
    label = "Failing action"

    def process(self):
        self.log.info("About to fail..")
        raise Exception("I failed")


class LongRunningAction(pyblish.api.Action):
    label = "Long-running action"

    def process(self):
        self.log.info("Sleeping for 2 seconds..")
        time.sleep(2)
        self.log.info("Ah, that's better")


class IconAction(pyblish.api.Action):
    label = "Icon action"
    icon = "crop"

    def process(self):
        self.log.info("I have an icon")


class PluginAction(pyblish.api.Action):
    label = "Plugin action"

    def process(self, plugin):
        self.log.info("I have access to my parent plug-in")
        self.log.info("Which is %s" % plugin.id)


class LaunchExplorerAction(pyblish.api.Action):
    label = "Open in Explorer"
    icon = "folder-open"

    def process(self, context):
        import os
        import subprocess

        cwd = context.data["cwd"]
        self.log.info("Opening %s in Explorer" % cwd)
        result = subprocess.call("start .", cwd=cwd, shell=True)
        self.log.debug(result)


class ProcessedAction(pyblish.api.Action):
    label = "Success action"
    icon = "check"
    on = "processed"

    def process(self):
        self.log.info("I am only available on a successful plug-in")


class FailedAction(pyblish.api.Action):
    label = "Failure action"
    icon = "close"
    on = "failed"


class SucceededAction(pyblish.api.Action):
    label = "Success action"
    icon = "check"
    on = "succeeded"

    def process(self):
        self.log.info("I am only available on a successful plug-in")


class BadEventAction(pyblish.api.Action):
    label = "Bad event action"
    on = "not exist"


class InactiveAction(pyblish.api.Action):
    active = False


class PluginWithActions(pyblish.api.Validator):
    optional = True
    actions = [
        pyblish.api.Category("General"),
        ContextAction,
        FailingAction,
        LongRunningAction,
        IconAction,
        PluginAction,
        pyblish.api.Category("OS"),
        LaunchExplorerAction,
        pyblish.api.Separator,
        FailedAction,
        SucceededAction,
        pyblish.api.Category("Debug"),
        BadEventAction,
        InactiveAction,
    ]

    def process(self):
        self.log.info("Ran PluginWithActions")
```

### Maya Example

```python
import time
import pyblish.api
import pyblish_qml


class Collect(pyblish.api.Collector):
    def process(self, context):
        i = context.create_instance("MyInstance")
        i.data["family"] = "default"
        i.append("pCube1")


class SelectInvalidNodes(pyblish.api.Action):
    label = "Select broken nodes"
    on = "failed"
    icon = "hand-o-up"
    
    def process(self, context):
        self.log.info("Finding bad nodes..")
        nodes = []
        for result in context.data["results"]:
            if result["error"]:
                instance = result["instance"]
                nodes.extend(instance)
        
        self.log.info("Selecting bad nodes: %s" % ", ".join(nodes))
        cmds.select(deselect=True)
        cmds.select(nodes)


class Validate(pyblish.api.Validator):
    actions = [
        pyblish.api.Category("Scene"),
        SelectInvalidNodes
    ]

    def process(self, instance):
        raise Exception("I failed")


pyblish.api.register_plugin(Collect)
pyblish.api.register_plugin(Validate)

import pyblish_maya
pyblish_maya.show()
```

<div class="modified-date">{{ file.mtime }}</div>

[1]: http://fortawesome.github.io/Font-Awesome/icons/