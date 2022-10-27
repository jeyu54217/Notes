**CONTENT**

- [OOP (Object oriented programming)](#oop-object-oriented-programming)
  - [Encapsulation & Abstraction](#encapsulation--abstraction)
    - [Encapsulation](#encapsulation)
    - [Abstraction](#abstraction)
  - [Classes & Instances](#classes--instances)
    - [Class](#class)
      - [Creating a Class](#creating-a-class)
      - [Class Attributes](#class-attributes)
      - [Class Methods](#class-methods)
    - [Instance](#instance)
      - [Instantiating a Class](#instantiating-a-class)
      - [Instance Attributes and Methods](#instance-attributes-and-methods)

# OOP (Object oriented programming)
  - programming paradigm

## Encapsulation & Abstraction
### Encapsulation
  -  the grouping of public and private attributes and methods into a programmatic class, making abstraction possible
### Abstraction
  - exposing only "relevant" data in a class interface, hiding private attributes and methods (aka the "inner workings") from users


## Classes & Instances
### Class
- blueprint for objects
- Classes can contain methods (functions) and attributes (similar to keys in a dict).
#### Creating a Class
- Classes in Python can have a special __init__ method, which gets called every time you create an instance of the class (instantiate).
- The self keyword refers to the current class instance.
- self must always be the first parameter to __init__ and any methods and properties on class instances.
- You never have to pass it directly when calling instance methods, including __init__.
```python
class Vehicle:

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
```

#### Class Attributes
- We can also define attributes directly on a class that are shared by all instances of a class and the class itself.
```python
class Pet():

    allowed = ("cat", "dog", "bird", "lizard", "rodent")

    def __init__(self, kind, name):

        if kind not in self.allowed:
            raise ValueError(f"You can't have a {kind} as a pet here!")

        self.kind = kind
        self.name = name

fluffy = Pet("cat", "Fluffy")
fluffy.allowed
("cat", "dog", "bird", "lizard", "rodent")
Bro = Pet("bear", "Bro")
ValueError: You can't have a bear as a pet here!
```
#### Class Methods
- Class methods are methods (with the @classmethod decorator) that are not concerned with instances, but the class itself.
- The first argument is cls (for class) instead of self. Like self, it does not need to be passed in explicitly.
- Class methods are available on the class itself and any instances of the class, and are mostly used for building new instances of classes.
```python
class Person():
    # ...

    @classmethod
    def from_csv(cls, filename):
        return cls(*params) # this is the same as calling Person(*params)

Person.from_csv(my_csv)
```
### Instance
- objects that are constructed from a class blueprint that contain their class's methods and properties.
#### Instantiating a Class
```python
v = Vehicle("Honda", "Civic", 2017)

v
<__main__.Vehicle at 0x10472f5c0>
v.make
'Honda'
v.model
'Civic'
v.year
2017
```
#### Instance Attributes and Methods
```python
class Person():

    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name

    def full_name(self):
        return f"My name is {self.first_name} {self.last_name}"

    def likes(self, thing):
        return f"{self.first_name} likes {thing}!" 

p = Person("Colt", "Steele")
```

properties
methods