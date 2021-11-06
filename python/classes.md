---
description: The ~~Beauty~~ Weirditude of Object Oriented Programming in Python
---


##### Object-oriented programming has almost no place in Data Science.  This is the realm of monsters, interview questions, and overlap with Java.


### General Bits:

* `__main__` means "this current file we're running"
* Classes can have variables and functions (called methods) defined within them
* An Object is one instance of a Class
* The data held by an Object is called an Instance Variable, and can differ from different Objects of that Class
* `self` refers to the Object, not the Class
* *The Strength of Classes and Objects is not needing to repeat common variables and functions, making the code DRY*


### Differences Between Methods and Functions:

* A method must call `self` as a variable
* To call the method, first call the object the method is embedded within
* Methods can use variables defined elsewhere in the object


```python
class DistanceConverter:
  kms_in_a_mile = 1.609
  def how_many_kms(self, miles):
    return miles * self.kms_in_a_mile
 
converter = DistanceConverter()
kms_in_5_miles = converter.how_many_kms(5)

print(kms_in_5_miles)
# prints "8.045"
```


### The Magic of Dunder Methods

Sometimes it's a shitload easier to have code run when a new object is being created, instead of creating the object then running the object's method.  For this, dunder methods -- also called magic, also called constructors.  In Python, this is done with `__init__`, which can then have variables passed to it as the object is created.

```python
class Shouter:
  def __init__(self, phrase):
    # make sure phrase is a string
    if type(phrase) == str:
 
      # then shout it out
      print(phrase.upper())
 
shout1 = Shouter("shout")
# prints "SHOUT" as soon as the object is created
```

Related is `__repr__`, so that when an error pops up, a more useful string is returned.  This also gives the object a name, which is pretty handy.  Often this can be defined as part of the intialization, but nearly any object-unique attribute will work.

```python
class Example():
  def __init__(self, name):
    self.name = name
    # when the object is created, get a name
 
  def __repr__(self):
    return self.name
    # use that name to refer to this specific object
```


### Object Attributes

An object can both inherit an attribute from its class (called a _class attribute_), or by creating an attribute (called an _instance attribute_) through `object.instance_attr = "foo"`.

Both of these are considered attributes of the object.  To access object attributes:


```python
# note, the attribute to test must be passed as a string

hasattr(attributeless, "fake_attribute")
# returns False
 
getattr(attributeless, "other_fake_attribute", 800)
# returns 800, the default value

dir(my_obj)
# returns all attributes of the object
```

These attribute handlers can also be run on the default data types (`str`, `dict`) and functions (`count`, `slice`).  


### Putting It All Together


```python
class Circle:
  pi = 3.14
  def __init__(self, diameter):
    print("Creating circle with diameter {d}".format(d=diameter))
    # Add assignment for self.radius here:
    self.radius = diameter / 2

  def circumference(self):
    return 2 * self.pi * self.radius
    # you need to call self before each object variable 

medium_pizza = Circle(12)
print(medium_pizza.circumference())
# prints 37.68
```


```python
class Student():
  def __init__(self, name, year):
    self.name = name
    self.year = year 
    self.grades = []

  def add_grade(self, grade):
    if Grade == type(grade):
      self.grades.append(grade)

pieter = Student("Pieter Bruegel the Elder", 8)

class Grade():
  minimum_passing = 65
  def __init__(self, score):
    self.score = score

pieter.add_grade(Grade(100))
```