---
description: Making tiny, fast functions
---

Python is real, real easy to define a function in, but sometimes... too slow!  Now let's make it _Faster_.

```python
add_two = lambda my_input: my_input + 2
```

That's... kinda it.

Here's another syntax example with an if statement:

```python
check_if_A_grade = lambda grade: 'Got an A!' if grade >= 90 else 'Did not get an A...'
```

Basic checklist:
* You don't need to use a `return` function, everything after the `:` is the return value.
