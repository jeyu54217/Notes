**CONTENTS**
- [1. Magic Methods](#1-magic-methods)
- [2. Decorators](#2-decorators)
- [3. List comprehension](#3-list-comprehension)
- [4. Dict comprehension (PEP 274)](#4-dict-comprehension-pep-274)
- [5. Ternary](#5-ternary)
- [6. Underscores in Numeric Literals](#6-underscores-in-numeric-literals)
- [7. assign](#7-assign)
- [8. 1 < x < 10](#8-1--x--10)


## 1. [Magic Methods](https://www.tutorialsteacher.com/python/magic-methods-in-python)
- dir() function to see the number of magic methods inherited by a class
- __ str__( )
```python
# override __str__()
class Employee:
    def __init__(self):
        self.name='Swati'
        self.salary=10000
    def __str__(self):
        return 'name='+self.name+' salary=$'+str(self.salary)
```


## 2. Decorators



## 3. [List comprehension](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)

[_expression_ for x in range(10)]
nested list comprehension
```python
# List comprehension
list_0 = []
for n in range(10):
    list_0.append(n)

list_1 = [n for n in range(10)]

# Nested list comprehension

```
## 4. Dict comprehension [(PEP 274)](https://peps.python.org/pep-0274/)
```{k: v for key, value in d.items()}```
## 5. Ternary

```x = something if condition else otherthing```

## 6. Underscores in Numeric Literals
```big_number = 1_000_000_000``` equivalent to ```big_number = 1000000000```

## 7. assign
```python
a += 1
a = a + 1
```
## 8. 1 < x < 10
```1 < x and x < 10```

