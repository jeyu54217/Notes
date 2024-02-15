**CONTENTS**
- [1. Magic Methods](#1-magic-methods)
- [2. Decorators](#2-decorators)
- [3. List comprehension](#3-list-comprehension)
- [4. Dict comprehension (PEP 274)](#4-dict-comprehension-pep-274)
- [5. Ternary](#5-ternary)
- [6. Underscores in Numeric Literals](#6-underscores-in-numeric-literals)
- [7. assign](#7-assign)
- [8. 1 \< x \< 10](#8-1--x--10)


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
- [See here](https://github.com/jeyu54217/Study_Note/blob/main/Python/decorator.md)


## 3. [List comprehension](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)
- List comprehension \
    ```
    [<item_expression> for <item> in <iterable>]
    ```

- Nested list comprehension
    ```
    [[<item_expression> for <item> in <iterable>] for <item> in <iterable>]
    ```

```python
# List comprehension
list_0 = []
for n in range(10):
    list_0.append(n)

list_1 = [n for n in range(10)]


[[_d[h] for h in _disp_header] for _d in _data]

# Nested list comprehension

```
## 4. Dict comprehension [(PEP 274)](https://peps.python.org/pep-0274/)
- Basic
    ``` 
    {<new_key> : <new_value> for <item> in <iterable>}
    ```
    ```python
    numbers = [1, 2, 3, 4, 5]
    squared_dict = {x: x**2 for x in numbers}
    print(squared_dict)
    # Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
    ```
- Conditional
    ```
    {<new_key> : <new_value> for <item> in <iterable> if <expression_condition>}
    ```
    ```python
    numbers = [1, 2, 3, 4, 5]
    even_squares = {x: x**2 for x in numbers if x % 2 == 0}
    print(even_squares)
    # Output: {2: 4, 4: 16}
    ```
- Value Condition
    ```
    {<new_key> : <new_value> if <Value_condition> else <Value_condition> for <item> in <iterable>}
    ```
    ```python
    numbers = [1, 2, 3, 4, 5]
    even_odd = {x: 'even' if x % 2 == 0 else 'odd' for x in numbers}
    print(even_odd)
    # Output: {1: 'odd', 2: 'even', 3: 'odd', 4: 'even', 5: 'odd'}
    ```
- Nested
    ```
    {<new_key> : <other_dict_comprehension> for <item> in <iterable>}
    ```
    ```python
    nested_dict = {x: {y: x*y for y in range(1, 4)} for x in range(1, 4)}
    print(nested_dict)
    # Output: {1: {1: 1, 2: 2, 3: 3}, 2: {1: 2, 2: 4, 3: 6}, 3: {1: 3, 2: 6, 3: 9}}
    ```
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

