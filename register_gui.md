### register_gui

Register interest in a graphical user interface.

| Source     | Added
|------------|---------
|            | 1.4.1

<br>
<br>
<br>

### Description

Register one or more Python packages with the following interface, and surrounding Pyblish projects may utilise them where needed. Such as in file menu of the Autodesk Maya integration.

**Interface**

```python
def show():
  """Create or unhide the most desireable GUI."""
```

<br>
<br>
<br>

### Example

Here is the basic structure expected by the `register_gui` function.

```yaml
my_package/
  __init__.py
```

**\_\_init\_\_.py**

```python
"""My package description"""

from PySide import QtGui

def show():
    my_gui = QtGui.QMessageBox()
    my_gui.show()
```

Once the package is on your `PYTHONPATH`, you may register it like so.

```python
pyblish.api.register_gui("my_package")
```

<div class="modified-date">{{ file.mtime }}</div>