## Action.on

Tailor the circumstance upon which a particular action should be made available.

 - `all`: Always
 - `processed`: After plug-in has been processed
 - `failed`: After plug-in has been processed, and failed
 - `succeeded`: After plug-in has been processed, and succeeded

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

class MyAction(pyblish.api.Action):
    on = "failed"
```
