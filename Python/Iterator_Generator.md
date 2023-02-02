**CONTENTS**
- [Iterator](#iterator)
- [Generatoriter](#generatoriter)

# Iterator
  - ```iter()``` : the ```for``` statement
  - ```next()``` : accesses elements in the container one at a time
      - ```StopIteration``` : When there are no more elements, __next__() raises a StopIteration exception which tells the for loop to terminate.

    ```python
    # Iterator

    s = 'abc'
    it = iter(s)

    it  # <str_iterator object at 0x10c90e650>
    next(it) # 'a'
    next(it) # 'b'
    next(it) # 'c'
    next(it) 
    
    #
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
        next(it)
    StopIteration

    ```
- Add iterator behavior to classes.
    1. Define an```__ iter__()``` method which returns an object with a ```__ next__()``` method. 
    2. If the class defines ```__ next__()```, then ```__ iter__()``` can just return self
    ```python
    # Define iterator in class

    class Reverse:
        """Iterator for looping over a sequence backwards."""
        def __init__(self, data):
            self.data = data
            self.index = len(data)

        def __iter__(self):
            return self

        def __next__(self):
            if self.index == 0:
                raise StopIteration
            self.index = self.index - 1
            return self.data[self.index]
        
    rev = Reverse('spam')
    iter(rev)        # <__main__.Reverse object at 0x00A1DB50>
    for char in rev: print(char)
    
    #
    m
    a
    p
    s
    
    ```


# Generatoriter

