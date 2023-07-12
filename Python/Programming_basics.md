**CONTENTS**
- [Variables](#variables)
  - [Naming Conventions (EPE8)](#naming-conventions-epe8)
  - [Dynamic Typing](#dynamic-typing)
  - [Static Typing](#static-typing)
  - [Inferred Type](#inferred-type)
- [Mutable \& Immutable](#mutable--immutable)
  - [Mutable](#mutable)
  - [Immutable](#immutable)
- [Tuple \& Set](#tuple--set)
  - [Tuple](#tuple)
  - [Set](#set)
    - [Set Comprehension](#set-comprehension)
- [Topics](#topics)
  - [- What's the maximum length of a list in Python?](#--whats-the-maximum-length-of-a-list-in-python)
  - [- Python Memory Management](#--python-memory-management)
  - [- Is Python call by reference or call by value](#--is-python-call-by-reference-or-call-by-value)
  - [- Dicts are now ordered](#--dicts-are-now-ordered)
  - [Unicode \& byte strings](#unicode--byte-strings)

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
# Topics
## - What's the maximum length of a list in Python?
In Python, the maximum length of a list is determined by the maximum value that can be represented by the sys.maxsize constant. sys.maxsize represents the largest positive integer that can be used as an index for a list or any other sequence in Python.

The value of sys.maxsize depends on the platform and the build of Python you are using. On most systems, sys.maxsize is equal to 2^31 - 1 or 2^63 - 1, depending on whether you're using a 32-bit or 64-bit version of Python.

In practical terms, this means that the maximum length of a list in Python can be approximately 2 billion elements (if using a 32-bit version of Python) or around 9 quintillion elements (if using a 64-bit version of Python). However, keep in mind that the actual limit may be lower due to memory constraints and other system limitations.

It's important to note that creating a list with such a large number of elements can consume a significant amount of memory and may impact the performance of your program. If you need to work with very large datasets or sequences of elements, consider using alternative data structures or techniques that allow for more memory-efficient operations, such as generators or streaming data processing.
## - Python Memory Management
https://docs.python.org/3.10/c-api/memory.html#memory-management
Certainly! Here are the key memory management features in Python:

1. Reference Counting:
   - Python uses reference counting as its primary memory management technique. Each object in Python has a reference count associated with it, which keeps track of the number of references to the object.
   - When a reference to an object is created, the reference count is incremented. When a reference is deleted or goes out of scope, the reference count is decremented.
   - When an object's reference count reaches zero, meaning there are no more references to it, the memory occupied by the object is automatically freed.

2. Garbage Collection:
   - In addition to reference counting, Python also employs a garbage collector to deal with situations where circular references occur. Circular references are references between objects that form a cycle and cannot be reached by the program.
   - Python's garbage collector periodically runs to identify and collect objects that are no longer reachable. It uses a combination of techniques, including reachability analysis, to determine which objects can be safely collected.
   - The garbage collector in Python is generational, meaning it divides objects into different generations based on their age. Younger objects are collected more frequently, while older objects are collected less frequently. This generational approach helps optimize the garbage collection process and minimize its impact on the program's performance.

3. Memory Allocation:
   - Python has its own memory manager responsible for allocating memory on the heap for objects. When an object is created, the memory manager allocates memory for it on the heap and initializes the object's data.
   - The memory manager uses various memory allocation strategies, such as pooling and caching, to improve the efficiency of memory allocation and deallocation.
   - Python's memory manager can request more memory from the operating system as needed and release memory that is no longer in use.

4. Memory Optimizations:
   - Python provides several techniques to optimize memory usage. For example, it uses interned strings to reduce memory consumption for frequently used string literals. It also employs a shared references mechanism to minimize the memory overhead of immutable objects that are referenced by multiple variables.
   - Python encourages the use of generators and iterators, which can save memory by lazily producing values instead of storing them all in memory at once.
   - Additionally, libraries and tools like `sys` and `pympler` offer functionalities for monitoring memory usage, profiling memory-intensive code, and identifying memory leaks.

Python's memory management is generally transparent to the programmer, as the interpreter handles most memory-related tasks. However, understanding these memory management features can help in writing efficient code, identifying memory-related issues, and optimizing memory usage when necessary.
## - Is Python call by reference or call by value
## - Dicts are now ordered
- Changed in version 3.7: Dictionary order is guaranteed to be insertion order. This behavior was an implementation detail of CPython from 3.6.
- https://softwaremaniacs.org/blog/2020/02/05/dicts-ordered/en/

## Unicode & byte strings 
Unicode and byte strings are two different concepts in Python that relate to handling character encodings and representing textual data.

1. Unicode:
Unicode is a universal character encoding standard that aims to represent every character from every writing system in the world. It assigns a unique code point (an integer value) to each character, including characters from different languages, symbols, punctuation marks, emojis, and more. The most commonly used encoding scheme for Unicode is UTF-8 (Unicode Transformation Format 8-bit).

In Python, strings are represented as Unicode by default starting from Python 3.x. This means that you can directly work with and manipulate text in various languages without worrying about different character encodings. Unicode strings in Python are prefixed with the `u` character.

Example:
```python
unicode_string = "Hello, 世界"
print(unicode_string)
# Output: Hello, 世界
```

2. Byte Strings:
Byte strings (or simply "bytes") in Python represent a sequence of raw bytes. Unlike Unicode strings, byte strings do not assume any specific character encoding. They are used when working with binary data or when it's necessary to interface with systems or protocols that expect specific byte-level representations.

In Python, byte strings are represented using the `bytes` type or by prefixing a string literal with `b`.

Example:
```python
byte_string = b"Hello, world!"
print(byte_string)
# Output: b'Hello, world!'
```

Byte strings can also be created by encoding Unicode strings using a specific character encoding scheme, such as UTF-8.

Example:
```python
unicode_string = "Hello, 世界"
byte_string = unicode_string.encode('utf-8')
print(byte_string)
# Output: b'Hello, \xe4\xb8\x96\xe7\x95\x8c'
```

Note that when working with byte strings, you may need to perform encoding and decoding operations to convert between byte strings and Unicode strings, depending on the context and requirements of your application.

It's important to understand the distinction between Unicode strings and byte strings in Python, as it affects how you handle and process textual data, especially when interacting with external systems or performing low-level operations on binary data.
