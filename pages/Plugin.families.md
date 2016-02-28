Supported families.

<br>
<br>
<br>

### Introduction

Read about the architecture of plug-ins for a better understanding of the `families` attribute.

- [[Plug-in System|Plugin System]]

<br>
<br>
<br>

### Implementation

A plug-in may support one or more families by appending it's absolute name to the `families` attribute.

```python
class MyPlugin(...):
   families = ["myFamily"]
```