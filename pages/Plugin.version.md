Plug-in version.

<br>
<br>
<br>

### Description

This attribute, containing a semantic version in the form of a tuple, is used in to determine which out of multiple plug-ins of identical names are to be used. For example, `MyPlugin.version == (1.0.0)` is assumed to be newer than `MyPlugin.version == (0.9.0)` and is therefore favoured, whereas the older version is discarded.