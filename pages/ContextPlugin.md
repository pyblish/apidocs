## ContextPlugin

Process once, with [Context](context.md) as input.

<br>
<br>
<br>

### Public Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|               | [process](Plugin.process.md)([Instance](Instance.md))


<br>
<br>
<br>

### Usage

The `ContextPlugin` is used for processing an entire scene or workspace. It is typically used during the collection portion of publishing, where data is identified and encapsulated in one or more [Instances](instance.md), but can in general be used for any processing that doesn't require access to any particular [Instance](instance.md).

<br>
<br>
<br>

### Example

```python
import pyblish.api as pyblish

class MyCollector(pyblish.ContextPlugin):
    order = pyblish.CollectorOrder
   
    def process(self, context):
        context.create_instance("MyInstance")
```