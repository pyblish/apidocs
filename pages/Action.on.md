## Action.on

Tailor the circumstance upon which a particular action should be made available.

<br>
<br>
<br>

### Description

Sometimes an Action is not relevant until a certain precondition has been met. For example, if an action is meant to repair broken validation, then it makes the most sense to provide this functionality until validation has actually failed.

<br>
<br>
<br>

### Example

```python
import pyblish.api

class FailedAction(pyblish.api.Action):
    label = "Failure action"
    icon = "close"
    on = "failed"
```