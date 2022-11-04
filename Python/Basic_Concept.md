**CONTENTS**
- [Variables](#variables)
  - [Naming Conventions (EPE8)](#naming-conventions-epe8)
  - [Dynamic Typing](#dynamic-typing)
  - [Static Typing](#static-typing)
  - [Inferred Type](#inferred-type)
- [Mutable & Immutable](#mutable--immutable)
  - [Mutable](#mutable)
  - [Immutable](#immutable)
- [Tuple & Set](#tuple--set)
  - [Tuple](#tuple)
  - [Set](#set)
    - [Set Comprehension](#set-comprehension)
  - [Memory Management](#memory-management)
  - [Is Python call by reference or call by value](#is-python-call-by-reference-or-call-by-value)

# Variables

## Naming Conventions [(EPE8)](https://peps.python.org/pep-0008/#naming-conventions)
1. UPPER_CASE
2. CapitalizedWords : CapWords, for Class names
3. mixedCase
4. **_var** : 
   - weak “internal use” indicator.
   - ```import *```does not import objects whose names start with an ```_```.
5. [**__var**](https://stackoverflow.com/questions/1301346/what-is-the-meaning-of-single-and-double-underscore-before-an-object-name) : This has real meaning. The interpreter replaces this name with _classname__foo as a way to ensure that the name will not overlap with a similar name in another class.
(See also : [__private-variables](https://github.com/jeyu54217/study_notes/blob/main/Python/OOP.md#__private-variables))
7. **__ var__** : “magic” objects or attributes that live in user-controlled namespaces.
8. var_ : avoid conflicts with Python keyword. e.g. Class -> class_

## Dynamic Typing
- variables can change types readily
- Ruby, Python, PHP, JavaScript, Erlang
```python
var = True
print(var) # True

var = "a dog"
print(var) # a dog

var = None
print(var) # None

var = 22 / 7
print(var) # 3.142857142857143
```
## Static Typing
- Java, C, C++
## Inferred Type
- Go 、Kotlin、Swift
# Mutable & Immutable
## Mutable
  - the **values** of **object** can be changed.
  - stored by value
   ['list'], {'set'}, {'dict':'dict'}, User-Defined Classes
## Immutable
  - the **values** of  **object** **cannot** be changed.
  - stored by reference
  - Numbers, "Strings", (Tuples), Frozen Sets, User-Defined Classes 
    ```python
    x = (1,2,3)
    3 in x # True
    x[0] = "change me!" # TypeError: 'tuple' object does not support item assignment
    ```
- https://ithelp.ithome.com.tw/m/articles/10278722
# Tuple & Set 
## Tuple
1. light-weight lists (ordered) : faster than lists
2. Immutable : safer than list
3. Valid keys in a dictionary ex .items() 
4. Only 2 Methods : 
```python
# (1) .count() : Returns the number of times a value appears in a tuple
x = (1,2,3,3,3)
x.count(1) # 1
x.count(3) # 3

# (2) .index() : Returns the index at which a value is found in a tuple.
tupl = (1,2,3,3,3)
tupl.index(1) # 0
tupl.index(5) # ValueError: tuple.index(x): x not in tuple
tupl.index(3) # 2 - only the first matching index is returned
```

## Set 

1. Sets do not have duplicate values
2. Unordered
3. You cannot access items in a set by index.
### Set Comprehension
-  useful when converting other data types to a set
```python
{x**2 for x in range(10)}

# {0, 1, 64, 4, 36, 9, 16, 49, 81, 25}

def are_all_vowels_in_string(string):
    return len({char for char in string if char in 'aeiou'}) == 5
```

## Memory Management
https://docs.python.org/3.10/c-api/memory.html#memory-management

## Is Python call by reference or call by value
