## PYBLISH_STRICT_DATATYPES

Throw errors when assigning invalid data types.

<br>
<br>
<br>

### Usage

When enabled the values in both ```instance.data``` and ```context.data``` will be validated.

```python
data = {
  "publish": True  # Boolean for GUIs to function.
}
```

<br>
<br>
<br>

### Example

```python
import os
os.environ["PYBLISH_STRICT_DATATYPES"] = "True"
```

<div class="modified-date">{{ file.mtime }}</div>
