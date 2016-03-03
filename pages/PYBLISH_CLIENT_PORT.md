## PYBLISH_CLIENT_PORT

This contains the currently used port number to communicate with [pyblish-qml](https://github.com/pyblish/pyblish-qml).

<br>
<br>
<br>

### Usage

You typically won't have to use this, but can be helpful during debugging sessions. It is written upon starting the server but never read, so changing it will not have any effect.

<br>
<br>
<br>

### Example

From [Communicating with the host](https://pyblish.gitbooks.io/developer-guide/content/communicating_with_the_host.html) in the Developer Guide.

```python
import os
import xmlrpclib
proxy = xmlrpclib.ServerProxy("http://127.0.0.1:9001/pyblish")
proxy.discover()
# {...}
```

<div class="modified-date">{{ file.mtime }}</div>