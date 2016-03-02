## result

The `result` dictionary is produced once per process and contains information about what happened, primarily intended for use in graphical user interfaces.

<br>
<br>
<br>

### Overview

These members are available in each result produced.

```json
{
    success: "Status of processing."
    instance: "Name of processed instance or null if no instance were processed."
    plugin: "Instance of current plug-in at the time."
    duration: "Time in milliseconds taken to process a pair."
    error: "Instance of exception thrown (if any)."
    records: "List of log messages made."
}
```

<br>
<br>
<br>

### Example

```python
import pyblish.util
context = pyblish.util.publish()

for result in context.data["results"]:
  print("Success!" if result["success"] else "Failed..")
  
  # All log messages are captured in `records`
  for record in result["records"]:
    print(record)
```

<br>
<br>
<br>

### Full schema

- https://github.com/pyblish/pyblish-rpc/blob/master/pyblish_rpc/schema/result.json

**Snapshot from [1e034](https://github.com/pyblish/pyblish-rpc/blob/6a075199c50c5c6a99e110505117c7d0d6d1e034/pyblish_rpc/schema/result.json)**

```json
{
    "$schema": "http://json-schema.org/schema#",

    "title": "Result",
    "description": "Result from processing a (plugin, instance) pair",

    "type": "object",

    "additionalProperties": false,

    "properties": {
        "success": {
            "description": "Status of processing",
            "type": "boolean"
        },
        "instance": {
            "description": "Name of processed instance or null if no instance were processed",
            "oneOf": [
                {"$ref": "instance.json"},
                {"type": "null"}
            ]
        },
        "plugin": {
            "oneOf": [
                {"$ref": "plugin.json"},
                {"type": "null"}
            ]
        },
        "duration": {
            "description": "Time in milliseconds taken to process a pair",
            "type": "number"
        },
        "error": {
            "oneOf": [
                {"$ref": "error.json"},
                {"type": "null"}
            ]
        },
        "records": {
            "type": "array",
            "items": {
                "$ref": "record.json"
            }
        }
    },

    "definitions": {}
}
```

<div class="modified-date">{{ file.mtime }}</div>