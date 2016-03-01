## Action.icon

Customisable icon to go with an Action.

<br>
<br>
<br>

### Description

Associate an [FontAwesome][ai] icon with an action. Choose from the library of available icons on from the main website.

- [FontAwesome Library][ai]

[ai]: http://fortawesome.github.io/Font-Awesome/icons

<br>
<br>
<br>

### Example

```python
class MyAction(pyblish.api.Action):
    icon = "close"
```