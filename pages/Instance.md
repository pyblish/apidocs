## Instance

An instance is a *unit* of data.

| Source     | Added
|------------|---------
|[Link][]    | 0.1.6

Inherits [AbstractEntity](AbstractEntity.md)

[Link]: https://github.com/pyblish/pyblish/blob/6e9bfce6254ea56411af857afa49423a57f7b425/pyblish/plugin.py#L572

<br>
<br>
<br>

### Properties

| Output                           | Property                                       |
|---------------------------------:|:-----------------------------------------------|
| [Context](Context.md) | [context](Instance.context.md)

<br>
<br>
<br>

### Public Functions

| Output        | Method                                                      |
|--------------:|:------------------------------------------------------------|
|               | [append](Instance.append.md)(object)
|               | [remove](Instance.remove.md)(object)

4 functions inherited from [AbstractEntity](AbstractEntity.md)

<br>
<br>
<br>

### Description

Instances are a core component of Pyblish. To get a sense of what they are, think of **instances** as the inverse of **files**; i.e. when you load a file into an application, you get an *instance* of that file.

Thus, when constructing an `Instance`, simply ask yourself:

- *"What am I looking to store on disk?"*

<br>
<br>
<br>

### Content and Metacontent

An instance may contain both *content* and *metacontent*.

You can think of the contents of an instance like how bytes are the contents of a file, whereas metacontent represents additional information about an instance, such as author and time last modified.

```
 Instance
 _______________________________
|  content         metacontent  |
|  __   __         _        _   |
| |       |       /          \  |
| | child |      | key: value | |
| | child |      < key: value > |
| | child |      | key: value | |
| |__   __|       \_        _/  |
|______________________________ |

  .append(child)    .data[key] = value
```

<br>
<br>
<br>

### Examples

```python
import pyblish.api

instance = pyblish.api.Instance(name="MyInstance")
instance.data["name"] = "My instance."
instance.append("NodeName1")
instance.append(custom_object)
```

```python
# Creating an instance from a context automatically
# makes it a child of that context.

import pyblish.api

context = pyblish.api.Context()
instance_a = pyblish.api.Instance(name="MyInstanceA", parent=context)
instance_b = context.create_instance(name="MyInstanceB")
```

<br>
<br>
<br>

### Origin

The word "instance" generally refers to "an occurence" of something. This *something* may occur multiple times, but it still refers to the same *something*.

Let's take an example.

```python
# Copy & Paste                     |            # Hard Link
 _______        _______            |             _______        _______   
|      |\      |      |\           |            |      |\      |      |\  
|       |      |       |           |            |       |      |       |  
|   A   |      |   B   |           |            |   A   |      |   B   |  
|       |      |       |           |            |       |      |       |  
|_______|      |_______|           |            |_______|      |_______|  
    |              |               |                 \           /
    |              |               |                  \         / 
 ___|___        ___|___            |                   \_______/
|       |      |       |           |                   |       |
|   A   |      |   B   |           |                   |   A   |
|_______|      |_______|           |                   |_______|
```

Each file on your file-system refers to data in your disk. If you copy a file and paste it somewhere else, you end up with two files that refer to *two different sets of data*. This is because the copy you made of the file is also made of the data on disk.

You can confirm this by keeping an eye on the disk usage before and after you make the copy. It increases.

On the other hand, if you create what is known as a "hard link"* to this file, you will also end up with two files. But this time, the two different files will refer to *the same set of data*.

Thus, no matter how many hard links you make, you will never spend any more disk space that what is required to store the handle to the file (a few bytes at most).

In Pyblish, this concept is very much the same.

In fact, you can think of an `Instance` as the *inverse* of a file. When loading a file into an application, what you end up with is the *instance* of that file. No matter how many times you load the file, each *instance* will refer to the same file on disk.

* [Hard link](http://en.wikipedia.org/wiki/Hard_link)