---
description: 
---

Basic way to zip together two lists into a dictionary:

```python
songs = ["Like a Rolling Stone", "Satisfaction", "Imagine", "What's Going On", "Respect", "Good Vibrations"]
playcounts = [78, 29, 44, 21, 89, 5]

plays = {key:value for key, value in zip(songs, playcounts)}
```

Looping through a dictionary:

```python
pct_women_in_occupation = {"CEO": 28, "Engineering Manager": 9, "Pharmacist": 58, "Physician": 40, "Lawyer": 37, "Aerospace Engineer": 9}

for job, value in pct_women_in_occupation.items():
  print("Women make up {} percent of {}s".format(value, job))
```

Also, you can call all keys with `dict.keys()` and all values with `dict.values()`

