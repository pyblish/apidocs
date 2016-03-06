## Plugin.order

Control the order of execution.

<br>
<br>
<br>

### Introduction

Plug-ins are sorted by this attribute. By altering the order of a subclass, you effectively have control over the order in which a particular plug-in is set to execute.

```yaml
# Default order per plug-in superclass
Selector: 0
Validator: 1
Extractor: 2
Conform: 3
```

Sorting is performed via the [sort](sort.md) function and works similar to this.

```python
plugins.sort(key=lambda p: p.order)
```

<br>
<br>
<br>

### Usage

By incrementing the order, you can offset how they are sorted and executed.

```python
class ValidateAfter(pyblish.api.InstancePlugin):
   order = 1.5
```

As the default order for a [Validator](Validator.md) is `1`, setting it to `1.5` means that this particular subclass will run once all validators still at the default order have finished.

To protect yourself against changes to the inherited order, it is recommended that you *offset* the order as opposed to setting it to an absolute value.

```python
class ValidateFirst(pyblish.api.InstancePlugin):
   order = pyblish.api.ValidatorOrder + 0.5
```

**Example**

Here's an example of three plug-ins of the same superclass, set to run one after the other.

```python
class ValidateFirst(pyblish.api.InstancePlugin):
   order = pyblish.api.ValidatorOrder + 0

class ValidateSecond(pyblish.api.InstancePlugin):
   order = pyblish.api.ValidatorOrder + 0.1

class ValidateThird(pyblish.api.InstancePlugin):
   order = pyblish.api.ValidatorOrder + 0.2
```

<br>
<br>
<br>

### Behavior

Each order have a special meaning to Pyblish.

> 0-1

Implies [Collector](Collector.md). It is run first, sometimes automatically, such as when launching the Pyblish QML graphical user interface.

> 1-2

Implies [Validation](validator.md).

> 2-3

Implies [Extraction](Extractor.md). It *does not* run if any plug-in within range `1-2` has produced an error.

> 3+

Implies [Integration](Integration.md). Like [Extraction](Extractor.md), it only runs if validation was successful.

<br>
<br>
<br>

### Caution

Keep in mind that if you offset an order too far, you effectively alter it's role in the Pyblish ecosystem which may cause undefined behaviour.

```python
class ValidateSecond(pyblish.api.InstancePlugin):
   # When does this plug-in run?
   order = 6
```

If you find yourself working with a large number of interdependent plug-ins, it is recommended that you subclass the super-classes and make ordering explicit.

**pipeline/pyblish.py**

```python
import pyblish.api as pyblish

class DefaultValidator(pyblish.InstancePlugin):
     order = pyblish.ValidatorOrder

class PreValidator(pyblish.InstancePlugin):
     order = pyblish.ValidatorOrder - 0.1

class PostValidator(pyblish.InstancePlugin):
     order = pyblish.ValidatorOrder + 0.1
```

You can then replace the provided classes with your with your own.

**/my_plugins/validate_something.py**

```python
import pipeline.pyblish

class ValidateSomething(pipeline.pyblish.PostValidator):
    ...
```
