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

- [result.json](https://github.com/pyblish/pyblish-qml/blob/master/pyblish_qml/ipc/schema/result.json)
- [All schemas](https://github.com/pyblish/pyblish-qml/blob/master/pyblish_qml/ipc/schema)

**Snapshot from [1a350](https://github.com/pyblish/pyblish-qml/blob/1a35024c7aeccae858146cce62202d2b43b8c826/pyblish_qml/ipc/schema/result.json)**

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
