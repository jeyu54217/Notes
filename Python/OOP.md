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
  - [Inheritance & Polymorphism](#inheritance--polymorphism)
    - [Inheritance](#inheritance)
    - [Multiple Inheritance](#multiple-inheritance)
    - [Polymorphism](#polymorphism)

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
## Inheritance & Polymorphism
### Inheritance
- A key feature of OOP is the ability to define a class which inherits from another class (a "base" or "parent" class).
- In Python, inheritance works by passing the parent class as an argument to the definition of a child class
- The super() keyword allows us to call the __ init__ function of a parent class
```python
class Animal:
    def __init__(self, species):
        self.species = species
    def make_sound(self, sound):
        print(sound)

    cool = True
#  initialize the child with both its own __init__ method and its parent's __init__ method:
class Dog(Animal):
    def __init__(self, name):
        super().__init__("canine")
        self.name = name
bro = Dog("Bro")
COPY
bro.name  # Bro
bro.species  # canine
```
### Multiple Inheritance
- Penguin inherits from both Aquatic and Ambulatory, therefore instances of Penguin can call both the walk and swim methods.
- What about the greet method for our instance of Penguin? It is calling the Aquatic.greet() instead of Ambulatory.greet().
```python
class Aquatic:
  def __init__(self,name):
    self.name = name

  def swim(self):
    return f"{self.name} is swimming"

  def greet(self):
    return f"I am {self.name} of the sea!"

class Ambulatory:
  def __init__(self,name):
    self.name = name

  def walk(self):
    return f"{self.name} is walking"

  def greet(self):
    return f"I am {self.name} of the land!"

class Penguin(Aquatic, Ambulatory):
  def __init__(self,name):
    super().__init__(name=name)
jaws = Aquatic("Jaws")
lassie = Ambulatory("Lassie")
captain_cook = Penguin("Captain Cook")
jaws.swim() # 'Jaws is swimming'
jaws.walk() # AttributeError: 'Aquatic' object has no attribute 'walk'
jaws.greet() # 'I am Jaws of the sea!'

lassie.swim() # AttributeError: 'Ambulatory' object has no attribute 'swim'
lassie.walk() # 'Lassie is walking'
lassie.greet() # 'I am Lassie of the land!'

captain_cook.swim() # 'Captain Cook is swimming'
captain_cook.walk() # 'Captain Cook is walking'
captain_cook.greet() # 'I am Captain Cook of the sea!'
```
### Polymorphism
- Classes can inherit from other classes and use the same methods to do different things (polymorphism)
- We can enhance our custom classes with special/magic/dunder methods
- an object can take on many (poly) forms (morph).
  1. The same class method works in a similar way for different classes
   ```python
   Cat.speak()  # meow
   Dog.speak()  # woof
   Human.speak()  # yo
   ```
    - method overriding
        - Each subclass will have a different implementation of the method.
        - If the method is not implemented in the subclass, the version in the parent class is called instead.
```python
class Animal():
    def speak(self):
        raise NotImplementedError("Subclass needs to implement this method")

class Dog(Animal):
    def speak(self):
        return "woof"

class Cat(Animal):
    def speak(self):
        return "meow"
```
  2.  The same operation works for different kinds of objects (Polymorphism)
   ```python
  sample_list = [1,2,3]
  sample_tuple = (1,2,3)
  sample_string = "awesome"

  len(sample_list)
  len(sample_tuple)
  len(sample_string)

  8 + 2  # 10
  "8" + "2"  # 82
  # Python classes have special (also known as "magic") methods, that are dunders (i.e. double underscore-named). 
  # hese are methods with special names that give instructions to Python for how to deal with objects.
  # The + operator is shorthand for a special method called __add__() that gets called on the first operand.
  # If the first (left) operand is an instance of int, __add__() does mathematical addition. If it's a string, it does string concatenation.
  # Therefore, you can declare special methods on your own classes to mimic the behavior of builtin objects, like so using __len__:
  class Human:
    def __init__(self, height):
        self.height = height  # in inches

    def __len__(self):
        return self.height
   ```

