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


### Overlap with Pandas

Lambda is hella useful to play with Pandas.  You can write a tiny lambda function to execute clean-up code really nicely.

```python
# Pull just someone's last name out of a list
# Note, this assumes no suffixes -- more complex than that and you want a _real_ function

get_last_name = lambda x: x.split(" ")[-1]
df['last_name'] = df.name.apply(get_last_name)

```

This gets tricky for row by row lambdas -- frankly, past a certain point, just write a function.  But if you really, really want to make a lambda...

```python
total_earned = lambda row: (row.hourly_wage * 40) + ((row.hourly_wage * 1.5) * (row.hours_worked - 40)) \
	if row.hours_worked > 40 \
  else row.hourly_wage * row.hours_worked
  
df['total_earned'] = df.apply(total_earned, axis = 1)
```