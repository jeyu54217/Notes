# Parameters
  - The variables in the declaration of function.
###  1. Default Parameters
  - Should always follow the **non-default** parameters
```python
## Default Parameters

def fun_0(p1, p2, p3, p4=10): print(p1,p2,p3,p4)
fun_0(1,2,3) # 1 2 3 10
fun_0(1,2)   # TypeError: fun_1() missing 1 required positional argument: 'p3'

def fun_1(p1, p2=10, p3=10, p4=10): print(p1,p2,p3,p4)
fun_1(1,2,3) # 1 2 3 10
fun_1(1,2)   # 1 2 10 10

def fun_2(p1=10, p2, p3, p4): print(p1,p2,p3,p4) # SyntaxError: non-default argument follows default argument
def fun_3(p1, p2=10, p3, p4=10): print(p1,p2,p3,p4) # SyntaxError: non-default argument follows default argument
```

###  2. *args
###  3. *kwargs

## Arguments
  - the arguments are the data you pass into the method's parameters.
  - Argument is the actual value of this variable that gets passed to function.
### Keyword Arguments

# Scope
  - local -> nonlocal -> global -> built-in
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

## Lambda function