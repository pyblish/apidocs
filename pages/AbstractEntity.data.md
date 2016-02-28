Available to [[Instance]] and [[Context]] objects and used to pass data between library and plug-ins.

<br>
<br>
<br>

### Introduction

Data is primarily gathered during [[Collector|Collector]] and used during subsequent plug-ins, such as [[Validation|Validator]] and [[Extraction|Extractor]]. Data can also be used as a means of messaging across plug-ins.

- See [Tale of Three APIs](https://github.com/pyblish/pyblish/wiki/Tale-of-Three-APIs) for more information.

<br>
<br>
<br>

### Naming Convention

Data members are using mixedCase.

**Wrong**

```bash
instance.data["snake_case_is_for_python"] = True
instance.data["CamelCaseIsForClasses"] = False
```

**Right**
```bash
instance.data["myVariable"] = True
instance.data["longName"] = 42
instance.data["veryLongVariable"] = 5
```

The motivation is to separate between what is Python and what is Pyblish data.

<br>
<br>
<br>

### Examples

```python
import pyblish.api as pyblish
context = pyblish.Context()
context.data["myData"] = "myValue"

instance = pyblish.Instance(name="MyInstance", parent=context)
instance.data["range"] = [0, 120]
instance.data["active"] = False
```

Data of any type may be added, including complex objects.

```python
# Custom objects

import pyblish.api

class MyCustomChild(object):
   def __init__(self, name):
      self.name = name

instance = pyblish.api.Instance(name="Car")
instance.append(MyCustomChild("wheels"))
instance.append(MyCustomChild("engine"))

MyCustomType = type("MyCustomType", (object,), {})

owner = MyCustomType()
owner.value = "John Doe"
make = MyCustomType()
make.value = "Ford"

instance.data["owner"] = owner
instance.data["make"] = make
instance.data["miles"] = "123"
```