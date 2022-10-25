# Variables

## Naming
1. 
2. 
3. 
4. 

## Dynamic Typing

# Mutable & Immutable
## Mutable
## Immutable
```python
x = (1,2,3)
3 in x # True
x[0] = "change me!" # TypeError: 'tuple' object does not support item assignment
```
# Tuple
1. light-weight lists : faster and safer than lists
2. Valid keys in a dictionary ex .items() 
3. Only 2 Methods : 
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

# Set

1. Sets do not have duplicate values
2. Elements in sets aren't ordered.
3. You cannot access items in a set by index.
