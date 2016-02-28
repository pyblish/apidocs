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
| [[hosts|Plugin.hosts]]                         | list
| [[families|Plugin.families]]                   | list
| [[label|Plugin.label]]                         | str
| [[active|Plugin.active]]                       | bool
| [[version|Plugin.version]]                     | tuple
| [[actions|Plugin.actions]]                     | list
| [[order|Plugin.order]]                         | float
| [[optional|Plugin.optional]]                   | bool
| [[requires|Plugin.requires]]                   | str

<br>
<br>
<br>

### Public Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|               | [[process|Plugin.process]]([[Instance]])

<br>
<br>
<br>

### Introduction

A plug-in represents an action to be performed on [[Instances|Instance]] supported by any of it's [[families|Plugin.families]].
