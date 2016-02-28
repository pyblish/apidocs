## Plugins

Plug-ins are snippets of code, discovered at run-time and defines the behaviour of Pyblish.

| Source     | Added
|------------|---------
|[Link][]    | 0.1.6

[Link]: https://github.com/pyblish/pyblish/blob/6e9bfce6254ea56411af857afa49423a57f7b425/pyblish/plugin.py#L119

<br>
<br>
<br>

### Properties

| property                                       | type
|:-----------------------------------------------|:-----
| [hosts](pages/Plugin.hosts.md)                 | list
| [families](pages/Plugin.families.md)           | list
| [label](pages/Plugin.label.md)                 | str
| [active](pages/Plugin.active.md)               | bool
| [version](pages/Plugin.version.md)             | tuple
| [actions](pages/Plugin.actions.md)             | list
| [order](pages/Plugin.order.md)                 | float
| [optional](pages/Plugin.optional.md)           | bool
| [requires](pages/Plugin.requires.md)           | str

<br>
<br>
<br>

### Public Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|               | [process](pages/Plugin.process.md)([Instance](pages/Instance.md))

<br>
<br>
<br>

### Introduction

A plug-in represents an action to be performed on [Instances](pages/Instance.md) supported by any of it's [families](pages/Plugin.families.md).
