## Context

The context represents the world.

| Source     | Added
|------------|---------
|[Link][]    | 0.1.6

Inherits [AbstractEntity](AbstractEntity.md)

[Link]: https://github.com/pyblish/pyblish/blob/6e9bfce6254ea56411af857afa49423a57f7b425/pyblish/plugin.py#L542

<br>
<br>
<br>

### Public Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|       Instance| [.create_instance](Context.create_instance.md)(str, **kwargs)

4 functions inherited from [AbstractEntity](AbstractEntity.md)

<br>
<br>
<br>

### Description

The context encapsulates one or more [Instance](Instance.md)'s along with information about the current execution environment, such as the current user and time of day. Publishing is performed by iterating over the members of a context.

```python
# Psuedo-code
for plugin in plugins:
  for instance in context:
     plugin.process(instance)
```

<br>
<br>
<br>

### Examples

```python
# Creating a context
#
# The context is normally created for you by a user interface or
# through convenience functions, but can be helpful to manually
# create for debugging purposes.

import pyblish.api as pyblish
context = pyblish.Context()
```

```python
# Creating instances from a context
#
# Instances can be created directly or through a context. When
# created through a context, the context is automatically set
# as the parent of the newly created instance.

import pyblish.api as pyblish
context = pyblish.Context()
instanceA = context.create_instance(name="MyInstanceA")
instanceB = pyblish.Instance(name="MyInstanceB", parent=context)

print("The context contains these instances:")
for instance in context:
    print(instance)
# MyInstanceA
# MyInstanceB
```

```python
# Setting data on a context
# 
# Both Instance and Context inherit from AbstractEntity which
# provides the mechanism for modifying data.

import pyblish.api as pyblish
context = pyblish.Context()
data = context.data
context.data["hostname"] = "localhost"
assert "hostname" in context.data is True
context.data.pop("hostname")
assert "hostname" in context.data is False
```

<div class="modified-date">{{ file.mtime }}</div>