---
description: Things to Copy & Paste
---

## Lamba Syntax

```python
# Double every negative number
numbers = [2, -1, 79, 33, -45]
negative_doubled = [num * 2 for num in numbers if num < 0]
```

```python
# Double every negative number, triple every positive number
numbers = [2, -1, 79, 33, -45]
doubled = [num * 2 if num < 0 else num * 3 for num in numbers]
```

```python
# Create new subset matching logic condition
heights = [161, 164, 156, 144, 158, 170, 163, 163, 157]
can_ride_coaster = [dude for dude in heights if dude > 161]
```

```python
# Nested list comprehension, such as after a zip
xy = [[1, 3], [2, 4], [3, 3], [4, 2]]
z = [x * y for (x, y) in xy]
```