**CONTENTS**
- [Arguments](#arguments)
  - [1. Positional Arguments](#1-positional-arguments)
  - [2. Keyword Arguments](#2-keyword-arguments)
  - [Argument/Keyword Argument Unpacking](#argumentkeyword-argument-unpacking)
    - [Argument Unpacking](#argument-unpacking)
    - [Keyword Argument Unpacking](#keyword-argument-unpacking)
- [Parameters](#parameters)
  - [1. Default Parameters](#1-default-parameters)
  - [2. *args](#2-args)
  - [3. *kwargs](#3-kwargs)
  - [Param Order](#param-order)
- [Scope](#scope)
    - [local](#local)
    - [global](#global)
    - [nonlocal](#nonlocal)
- [Lambda](#lambda)
- [Documenting](#documenting)

# Arguments
  - Arguments are the data(actual value) which passed into the func's parameters.
## 1. Positional Arguments
- values that are passed into a function based on the order in which the parameters were listed during the function definition.
```python
# Positional Arguments
def func_posi_0(p1, p2): print(p1, p2)
func_posi_0("A", "B") # A B
func_posi_0("B", "A") # B A

```
## 2. Keyword Arguments
-  values which passed into a function are identifiable by specific parameter names and the assignment operator ```=```
-  Keyword arguments can be likened to dictionaries in that they map a value to a keyword.
-  the positions of the arguments do not matter.
-  have to come after positional arguments and before default arguments in a function call.
```python
# Keyword Arguments
def func_kw_0(p1, p2): print(p1, p2)
func_kw_0(p1="A", p2="B") # A B
func_kw_0(p2="A", p1="B") # B A


# come after positional arguments and before default arguments
def func_kw_1(p1, p2, p3=100): print(p1, p2, p3)
func_kw_1(p2="A", 100) # SyntaxError: positional argument follows keyword argument
func_kw_1(100, 200) # 100 200 100
```
## Argument/Keyword Argument Unpacking
- Using ```*``` , ```**``` as an Argument / Keyword Arguments
### Argument Unpacking
```python
# *Argument Unpacking
def func_args_0(*args): print(sum(args))

array_l = [1, 2, 3, 4]
array_t = (1, 2, 3, 4)
# error
func_args_0(array_l) # TypeError: unsupported operand type(s) for +: 'int' and 'tuple'
func_args_0(array_t) # TypeError: unsupported operand type(s) for +: 'int' and 'tuple'
# ok!
func_args_0(1, 2, 3, 4) # 10
func_args_0(*array_l, *array_t) # 20
```
### Keyword Argument Unpacking
```python

# **Keyword Argument Unpacking
def func_kwargs_0(A, B): print( f"{A} & {B}")
dict_1 = {"A": 123, "B": 321}
# error
func_kwargs_0(dict_1) # TypeError: func_kwargs_0() missing 1 required positional argument: 'B'
# ok!
func_kwargs_0(**dict_1) # 123 & 321
```
# Parameters
  - The variables in the declaration of function.

##  1. Default Parameters
  - Should always follow the **non-default** parameters
```python
## Default Parameters

def fun_0(p1, p2, p3, p4=10): print(p1,p2,p3,p4)
fun_0(1,2,3) # 1 2 3 10
fun_0(1,2)   # TypeError: fun_1() missing 1 required positional argument: 'p3'

def fun_1(p1, p2=10, p3=10, p4=10): print(p1,p2,p3,p4)
fun_1(1,2,3) # 1 2 3 10
fun_1(1,2)   # 1 2 10 10

# error
def fun_2(p1=10, p2, p3, p4): print(p1,p2,p3,p4) # SyntaxError: non-default argument follows default argument
# error
def fun_3(p1, p2=10, p3, p4=10): print(p1,p2,p3,p4) # SyntaxError: non-default argument follows default argument
```

##  2. *args
- Gathers all remaining ```arguments``` as a ```tuple```
- The order of arguments doesn't matter!
```python
# *args

def arg_fun_0(*args): print(args,type(args))
arg_fun_0(1, 2, 3) # (1, 2, 3) <class 'tuple'>

def arg_fun_1(*args):
    total = 0
    for val in args:
        total += val
    return total
arg_fun_1(1, 2, 3) # 6
```

##  3. *kwargs
- Gathers remaining ```keyword arguments``` as a ```dict```
```python
# *kwargs

def func_kwargs_0(**kwargs):
    print(kwargs, type(kwargs)) # {'A': 123, 'B': 321} <class 'dict'>
    for k,v in kwargs.items(): print(k,v)
# error
func_kwargs_0(A:'123', B=321)   # SyntaxError: invalid syntax
func_kwargs_0(A='123', "B"=321) # SyntaxError: expression cannot contain assignment, perhaps you meant "=="?

# ok!
func_kwargs_0(A='123', B=321)   # A 123 B 321
# Keyword Argument Unpacking
dict_0 = {'A':123,'B':321}
func_kwargs_0(**dict_0)         # A 123 B 321
```
## Param Order 
- ```param -> (*args = default_param) -> **kwargs```
```python
# Param Order
def arg_fun_position(a, b=10 ,*args, c=20): 
    print(a, args, b, type(args), c)
arg_fun_position(1, 2, 3, 4) # 1 (3, 4) 2 <class 'tuple'> 20
def fun_order(a, b, c=123, *args, d=321, **kwargs):
    print(a, b, c, args, d, kwargs)
fun_order(1, 2, 3, 4, 5, e=3333, f=999) # 1 2 3 (4, 5) 321 {'e': 3333, 'f': 999}
```
# Scope
  - local -> nonlocal -> global -> built-in
  - You will not find yourself using the global or nonlocal keyword frequently - but it's essential to understand for scope!
### local
```python
## Local Scope

glo_var = 0

def fun_loco_0():
    glo_var += 10
    return glo_var
print(fun_loco_0(), glo_var)  
# UnboundLocalError local variable 'glo_var' referenced before assignment

def fun_loco_1():
    local_var = glo_var # create new local obj but not point to the original glob_obj.
    local_var += 10
    return local_var,id(local_var), id(glo_var)
print(fun_loco_1(), glo_var) # (10, 140625991289024, 140625991288704) 0
```
### global
```python
## Global Scope

glo_var = 0

def fun_glo():
    global glo_var # point to the original glob_obj.
    glo_var += 10
    return glo_var
print(fun_glo(), glo_var)  # 10,10
```
### nonlocal
- for nested function
```python
def outer():
    count = 0
    def inner():
        nonlocal count
        count += 1
        return count
    return inner()
```


# Lambda
- ```(lambda parameter: expression)(argument)```
1. No need to define function **Name**.
2. Only one line.
3. Automatically ```return``` (No need to type the return keyword)
```python
# Map

# Filter

# Any
# All

# Sorted

# Min
# Max

# Reversed

```
# Documenting
```python
def fun_0():
    """The Doc
    1. This is the doc.
    2. The Doc The Doc.
    """
    return "Hello!"

print(fun_0.__doc__)
'''
The Doc
    1. This is the doc.
    2. The Doc The Doc.
'''
```