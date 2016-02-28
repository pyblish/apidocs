The primary mechanism with which plug-ins are read from disk.

<br>
<br>
<br>

### Introduction

Pyblish is a plug-in driven framework, everything it does it does through plug-ins. A plug-in can either come in the form of a declaration in the currently active Python session, or as a file. This discovery mechanism is how plug-ins are located and loaded dynamically into Pyblish at run-time.

<br>
<br>
<br>

### Mechanism

For Pyblish to locate plug-ins, you either (1) register a plug-in directly via [[register_plugin]], (2) register a path via [[PYBLISHPLUGINPATH]] or (3) [[register_plugin_path]].

Registering a plug-in directly (1) is useful during initial prototyping and for sharing your plug-in with others in a quick and effortless manner. You can simply post your plug-in on a forum, one could copy-paste it into his running session of Python and off we go. Registering directories (2)(3) makes for a power method of persisting plug-ins and to dynamically expose plug-in based on project, task and/or artist.