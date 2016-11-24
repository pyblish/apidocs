## Plugin.order

Control the order of execution.

> Since 1.4.3

<br>
<br>
<br>

### Introduction

The way instances are associated with plug-ins are via their `families`.

A plug-in may support one or more families, and instances matching one or more of these families are said to be associated with it.

An instance may be associated via a plug-in in 1 of 3 ways.

1. Intersection
2. Subset
3. Exact

By default, an instance of any family within the supported families of a plug-in is a match. This is called **Intersection** and stems from basic set theory.

```python
assert set(["a", "b"]).intersection(["b", "c"])
```

This is useful in the most general case, of one plug-in supporting many different - possibly unrelated - families. Such as one plug-in supporting both models and rigs, say for an established naming convention across both families.

**Subset** on the other hand means the families of an Instance must be a *subset* of the supported families of any plug-in.

Again the concept is borrowed from set theory.

```python
assert set(["a", "b"]).issubset(["a", "b", "c"])
```

This can be useful when instances are specialised, such as being a `lowpoly` family of a `model`, or `animation`  family of a `rig`.

Finally, there is **Exact** which captures edge-cases or otherwise highly context sensitive instances, such as an `animation` `rig` in `shot05`.

The algorithm is as follows.

```python
assert set(["a", "b"]) == set(["b", "a"])
```

<br>
<br>
<br>

### Usage

Decide whether your plug-in targets many unrelated families, or specialises in a few, then associate an algorithm with this plug-in.

**Example**

In this example, `SpecificPlugin` is associated to instances whose family(ies) are a ubset of the supported families model and low. If the instance does not have at least both of these, it is not a match.

This is different from `GenericPlugin`, where only one of the families of an instance need to match any of the supported families of a plug-in.

```python
from pyblish import api

class GenericPlugin(api.InstancePlugin):

  # Support both models and rigs
  families = ["model", "rig"]

  def process(self, instance):
    # Applies to both models and rigs
    assert "parent_GRP" in instance

class SpecificPlugin(api.InstancePlugin):

  # Support models, but only low-poly models
  families = ["model", "low"]
  match = api.Subset

  def process(self, instance):
    # Safe to assume it has a `polyCount` due
    # to only capturing models.
    assert instance.data["polyCount"] < 500
```

The last possible value is `Exact` which means an instance only matches when families of both instance and plug-ins match exactly.

```python
class EdgeCasePlugin(api.InstancePlugin):
  families = ["model", "low", "level21"]
  match = api.Exact

  def process(self, instance):
    assert "specialMember" in instance
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
