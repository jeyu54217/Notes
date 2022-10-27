## 1. Magic Methods
- dir() function to see the number of magic methods inherited by a class
- '__str__()'
```python
# override __str__
class Employee:
    def __init__(self):
        self.name='Swati'
        self.salary=10000
    def __str__(self):
        return 'name='+self.name+' salary=$'+str(self.salary)
```
https://www.tutorialsteacher.com/python/magic-methods-in-python

## 2. Decorators

## 3. List comprehension
[x for x in range(10)]
nested list comprehension
## 4. Dict comprehension
{key: value for key, value in d.items()}
## 5. Ternary

x = something if condition else otherthing

## 6. Underscores in Numeric Literals
big_number = 1_000_000_000
 equivalent to big_number = 1000000000

## 7. assign
a += 1
a = a + 1

## 8. 1 < x < 10
1 < x and x < 10

