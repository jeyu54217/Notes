
- [Code Execution](#code-execution)
  - [1. Interprete](#1-interprete)
  - [2. Compile](#2-compile)
  - [3. Just In Time (JIT)](#3-just-in-time-jit)
- [Data Typing](#data-typing)
  - [1. Dynamic \& Static Typing](#1-dynamic--static-typing)
  - [2. Strong \& Weak Typing](#2-strong--weak-typing)
- [Programming Paradigms](#programming-paradigms)
  - [1. Imperative Programming](#1-imperative-programming)
    - [a. **Procedural**](#a-procedural)
    - [b. **Object-Oriented Programming (OOP)**](#b-object-oriented-programming-oop)
  - [2. Declarative](#2-declarative)
    - [a. **Functional Programming (FP)**](#a-functional-programming-fp)
    - [b. **Database Query Languages**](#b-database-query-languages)
    - [c. **Logic Programming**](#c-logic-programming)
  - [3. Structured](#3-structured)
  - [4. Event-Driven](#4-event-driven)
  - [5. Concurrent](#5-concurrent)
  - [6. Generic](#6-generic)
  - [7. Reflective](#7-reflective)
  - [8. Symbolic](#8-symbolic)
  - [9. Metaprogramming](#9-metaprogramming)
- [Text \& Bytes](#text--bytes)



# Code Execution
  
  |              | Interpreter                                        | Compiler                                                                   | JIT Compiler                                                                |
  |---------------------|----------------------------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
  | **Execution**       | Executes source code directly, line by line.       | Translates entire source code to machine code before execution.            | Compiles bytecode to machine code at runtime.                               |
  | **Speed**           | **Slow**, due to **on-the-fly interpretation**.    | **Fast**, as code is run by the CPU directly.                              | Can be faster than interpretation, optimizes at runtime.                    |
  | **Development**     | **Easier** to **debug** and **test** due to **immediate feedback**. | Requires **compilation step**, making testing/debugging a **slower** process. | Offers a balance, with some optimization possible at runtime.               |
  | **Portability**     | **High**, code can run anywhere the interpreter exists. | **Low**, compiled code is often **platform-specific**. (Different OS have their own Compiler.) | **High**, **bytecode** is **portable** and compiled on-the-fly to native machine code. |
  | **Use Case**        | Scripting, small programs, rapid development.       | Large applications, systems programming, **performance-critical** applications. | Environments where **performance** and **portability** are both concerns. |
  | **Examples**        | Python, Ruby, JavaScript                           | C, C++, Rust                                                               | Java (JVM), .NET (CLR)                                                      |


## 1. Interprete 
- **Source Code (Line/Chunk) → Interpreter → Machine Code → Execution → Source Code (Line/Chunk)...**
<img width="389" alt="Screenshot 2024-02-19 at 01 06 05" src="https://github.com/jeyu54217/Notes/assets/73396926/f74326e3-7a4d-40da-898c-3727e174f8df">

## 2. Compile
- **Source Code → Compiler →  Machine Code → Execution**
<img width="389" alt="Screenshot 2024-02-19 at 01 05 56" src="https://github.com/jeyu54217/Notes/assets/73396926/bb19c5bb-7108-4a95-aa09-837ea147ac48">

## 3. Just In Time (JIT)

- **Source Code → Compiler → a Byte Code file →**
    **Byte Code Line/Chunk → JIT Interpreter → Machine Code → Execution → Byte Code Line/Chunk...**
- **Java**
  <img width="1028" alt="Screenshot 2024-02-19 at 00 57 31" src="https://github.com/jeyu54217/Notes/assets/73396926/64d6495b-8375-4bc6-a013-d06115e95d15">

# Data Typing

- **Language Comparison**

| Language   | Typing System              | Type Strength     | Notes                                                                                      |
|------------|----------------------------|-------------------|--------------------------------------------------------------------------------------------|
| Python     | Dynamic Typing             | Strong Typing     | Python enforces type rules at runtime but does not allow implicit type conversion.         |
| JavaScript | Dynamic Typing             | Weak Typing       | JavaScript allows considerable flexibility with types, including implicit type conversion. |
| PHP        | Dynamic Typing             | Weak Typing       | PHP features implicit type conversion, fitting both dynamic and weak typing.               |
| Ruby       | Dynamic Typing             | Strong Typing     | Similar to Python, Ruby is dynamically and strongly typed without implicit conversions.    |
| Java       | Static Typing              | Strong Typing     | Java requires explicit type declaration and does not allow implicit type conversion.       |
| C          | Static Typing              | Weak Typing       | C allows for implicit type conversion, fitting the criteria for static but weak typing.    |
| C++        | Static Typing              | Strong Typing     | C++ is statically typed and generally considered strongly typed but allows type casting.   |
| C#         | Static Typing              | Strong Typing     | C# enforces type rules at compile time with minimal implicit type conversion.              |
| Go         | Static Typing              | Strong Typing     | Go is statically typed with a strong emphasis on type safety and minimal conversion.  

## 1. Dynamic & Static Typing
  
  |               | Dynamic Typing                                                                                                                                                                                                                        | Static Typing                                                                                                                                                                                                                           |
  |-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | **Type Checking**     | Type checks are performed at runtime, allowing variable types to change over execution. Offers flexibility in variable use.                                                                                                           | Type checks are performed at compile-time, ensuring types are correct before the program runs. Catches type-related errors early.                                                                                                        |
  | **Flexibility**       | High, with easy reassignment of variables to different types. Beneficial for rapid development and evolving requirements.                                                                                                              | Lower, as variables are bound to a specific type once declared. Makes code more predictable but requires more upfront design.                                                                                                           |
  | **Performance**       | May have performance overhead due to runtime type checking and interpretation.                                                                                                                                                         | Typically results in faster execution times due to compile-time optimizations.                                                                                                                                                          |
  | **Error Detection**   | Errors related to type found at runtime, leading to potential runtime errors and increased debugging time.                                                                                                                             | Caught at compile-time, reducing runtime errors and saving debugging time.                                                                                                                                                               |
  | **Code Verbosity**    | Less verbose, as types do not need to be explicitly declared.                                                                                                                                                                          | More verbose due to explicit type declarations, which can make code more explicit and potentially increase readability.                                                                                                                 |
  | **Use Cases**         | Suited for scripting, rapid prototyping, and applications where flexibility is key.                                                                                                                                                    | Ideal for large-scale applications, systems programming, where performance and type safety are critical.                                                                                                                                |
  | **Language Examples** | Python, Ruby, JavaScript | C, C++, Java |

## 2. Strong & Weak Typing
  
  |               | Strong Typing                                                                                                                                                      | Weak Typing                                                                                                                                                    |
  |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | **Type Coercion**     | Minimal to no implicit type coercion. Operations between incompatible types require explicit conversion, enhancing type safety and predictability.                     | Implicit type coercion is common, allowing operations between different types without explicit conversion, which can lead to flexibility but also unpredictability. |
  | **Type Safety**       | High. The language enforces strict type rules, reducing the chances of runtime errors due to type mismatches.                                                         | Lower. The flexibility in types can increase the risk of type-related runtime errors.                                                                             |
  | **Error Detection**   | Errors related to type mismatches are more likely to be caught early, either at compile-time (for statically typed languages) or at runtime before they cause issues. | Type-related errors might only become apparent at runtime, potentially leading to bugs that are harder to trace and fix.                                          |
  | **Runtime Behavior**  | Predictable. The strict type system ensures that operations behave as expected, without implicit changes in type.                                                     | Less predictable. Implicit type conversions can lead to unexpected behavior, making the code harder to understand and debug.                                      |
  | **Flexibility**       | Lower. The need for explicit type conversions can make the code more verbose and potentially slow down rapid development.                                             | Higher. Allows for quicker prototyping and development due to the ease of mixing types, but at the cost of potential runtime issues.                               |
  | **Use Cases**         | Preferred in applications where reliability and maintainability are critical, such as large-scale or complex systems.                                                  | Suited for scripting, rapid prototyping, or environments where the ease of development is prioritized over strict type safety.                                    |
  | **Examples** | Python, Java           | JavaScript, PHP|

- **Strong**
    
  | Advantages                            | Disadvantages                                                      |
  |---------------------------------------|--------------------------------------------------------------------|
  | **Type Safety:** Reduces the likelihood of type-related runtime errors, increasing the reliability of the code. | **Less Flexibility:** Can limit rapid development due to the need for explicit conversions and declarations. |
  | **Error Detection:** Type mismatches are often caught early, improving code quality and maintainability.       | **Verbosity:** Code might be more verbose due to explicit type conversions and declarations.                   |
  | **Predictability:** Operations behave as expected without implicit type changes, making the code easier to understand and debug. | **Slower Prototyping:** The strict type system can slow down initial development and prototyping. |

- **Weak**
    
  | Advantages                            | Disadvantages                                                         |
  |---------------------------------------|-----------------------------------------------------------------------|
  | **Flexibility:** Allows for easy mixing of types, facilitating rapid development and prototyping. | **Type Safety:** Increased risk of type-related errors at runtime, which can affect the reliability of the code. |
  | **Ease of Development:** Can speed up development by reducing the need for explicit type conversions. | **Unpredictability:** Implicit type conversions can lead to unexpected behavior and make the code harder to debug. |
  | **Rapid Prototyping:** Ideal for scenarios where speed of development is prioritized over strict type safety. | **Error Detection:** Type-related errors may only become apparent at runtime, potentially leading to more complex debugging. |


# Programming Paradigms
## 1. Imperative Programming
- Imperative programming is characterized by a series of commands for the computer to perform. It's one of the oldest programming paradigms and forms the basis of many other paradigms.

### a. **Procedural** 
- A subtype of imperative programming, it structures code into procedures or functions, facilitating code reuse and modularization. Languages like C and Pascal are well-known examples.
  
### b. **Object-Oriented Programming (OOP)** 
- Focuses on defining data structures as objects and the operations that can be performed on them, promoting data encapsulation, inheritance, and polymorphism. Java, C++, and Python are languages that support OOP.
- Supported Languages
  
  | Language | OOP Support | Notes |
  |----------|-------------|-------|
  | Go       | Partial     | Go does not support OOP in the traditional sense (e.g., no inheritance), but it allows methods on struct types and interfaces for polymorphism. |
  | Java     | Full        | Java is a purely object-oriented language, supporting inheritance, encapsulation, and polymorphism. |
  | C#       | Full        | C# is a modern, object-oriented, and type-safe programming language, providing full support for OOP concepts. |
  | Python   | Full        | Python is a dynamically typed language that supports OOP fully, including multiple inheritance and polymorphism. |
  | C++      | Full        | C++ supports OOP and allows for low-level memory manipulation, combining both high-level OOP features and low-level capabilities. |
  | Ruby     | Full        | Ruby is a purely object-oriented language, where everything is an object, fully supporting OOP paradigms. |
  | Swift    | Full        | Swift supports OOP and is designed to work with Apple's Cocoa and Cocoa Touch frameworks, offering a modern approach to OOP. |
  | Kotlin   | Full        | Kotlin is a statically typed programming language that runs on the JVM and fully supports OOP, designed to interoperate fully with Java. |



- example: python
  ```python
  class Dog:
      def __init__(self, name, age):
          self.name = name  # instance variable for the dog's name
          self.age = age  # instance variable for the dog's age
  
      def bark(self):
          print(f"{self.name} says woof!")
  
      def birthday(self):
          self.age += 1
          print(f"Happy Birthday {self.name}! You are now {self.age} years old.")
  
  # Creating instances of the Dog class
  dog1 = Dog("Buddy", 5)
  dog2 = Dog("Lucy", 3)
  
  # Calling methods on those instances
  dog1.bark()  # Output: Buddy says woof!
  dog2.birthday()  # Output: Happy Birthday Lucy! You are now 4 years old.

  ```
  
## 2. Declarative 
- Declarative programming expresses the logic of a computation without describing its control flow. It abstracts the flow control process, letting developers focus on "what" a program should accomplish rather than "how."

### a. **Functional Programming (FP)** 
- Emphasizes pure functions and immutable data. FP supports higher-order functions, function composition, and recursion, aiming for side-effect-free code.
- example: python
  ```python
  from functools import reduce
  
  # Pure function to square a number
  def square(x):
      return x * x
  
  # Pure function to sum two numbers
  def add(x, y):
      return x + y
  
  # Function to compute the sum of squares of a list of numbers
  def sum_of_squares(lst):
      return reduce(add, map(square, lst))
  
  numbers = [1, 2, 3, 4, 5]
  result = sum_of_squares(numbers)
  print(result)  # Output: 55

  ```
### b. **Database Query Languages** 
- SQL (Structured Query Language) is a prime example, enabling the definition, manipulation, and query of data in relational databases.
- example: sql
  ```sql
  SELECT * FROM users WHERE age > 18;

  ```
### c. **Logic Programming** 
- Uses formal logic to express computations. Prolog is a notable example, where programs are written as a set of facts and rules within a logical framework.
- [In Detail](https://chat.openai.com/share/f1c5386d-6dd2-4a2a-b7a1-fe0da4774bb8)
  
  
## 3. Structured 
- It's a fundamental concept that virtually **all modern programming languages** supported
- The paradigm's emphasis on straightforward control flow (e.g., using loops and conditionals) without the use of GOTO statements makes it a foundational concept in software development.
- example: python
  ```python
  def sum_even_numbers(limit):
      sum = 0
      for number in range(1, limit + 1):
          if number % 2 == 0:
              sum += number
      return sum
  
  # Calculate the sum of even numbers up to 10
  result = sum_even_numbers(10)
  print("Sum of even numbers from 1 to 10 is:", result)

  ```
  
## 4. Event-Driven 
- Centers around the generation and handling of events. In this paradigm, the flow of the program is determined by events such as **'user actions'**, **'sensor outputs'**, or **' messages passing'** from other programs or threads. JavaScript, used in web development, is a well-known example.
  
- Supported Languages
  
  | Language       | Application Domain               | Notes                                                |
  |----------------|----------------------------------|------------------------------------------------------|
  | JavaScript     | Web development                  | Widely used for client-side and server-side events   |
  | Python         | General-purpose, Web development | Supports event-driven programming via frameworks ( [Django](https://chat.openai.com/share/d2eee468-87a0-4774-8a7f-07c85eb15e1e) )     |
  | Java           | Enterprise, Android apps         | Utilizes event listeners in GUI and web applications |
  | C#             | .NET applications                | Used in desktop, web, and game development           |
  | Go             | Concurrent systems               | Goroutines facilitate event-driven concurrency       |
  | PHP            | Web development                  | Commonly used with AJAX for dynamic web content      |
  | Ruby           | Web development                  | Ruby on Rails supports event-driven web applications |
  | Swift          | iOS and macOS apps               | Supports event-driven programming in Apple ecosystem |
  | TypeScript     | Web development                  | Superset of JavaScript, enhancing its capabilities   |

- example: javascript DOM
  ```javascript
  // HTML markup for the button
  <button id="clickMeButton">Click Me!</button>
  
  // JavaScript code to add an event listener to the button
  document.getElementById("clickMeButton").addEventListener("click", function() {
      alert("The button was clicked!");
  });

  // In this example, the addEventListener method is used to listen for the "click" event on the button with the id clickMeButton. When the button is clicked, the anonymous function passed as the second argument to addEventListener is executed, causing the alert box to appear with the message "The button was clicked!". This illustrates the essence of event-driven programming in JavaScript: reacting to events by executing specified code blocks.
  ```


## 5. Concurrent 
- Involves writing programs that can execute operations simultaneously, either through multiple threads or processes. This paradigm is essential for exploiting multi-core processors and for developing applications that require concurrent operations, such as web servers.
- Supported Languages
  
  | Language       |  Support                        |
  |----------------|--------------------------------------------|
  | Java           | Threads, Executor Framework, Fork/Join     |
  | C#             | async/await, Task Parallel Library (TPL)   |
  | Python         | threading, asyncio, multiprocessing        |
  | Go             | Goroutines, Channels                       |
  | JavaScript     | Callbacks, Promises, async/await           |
  | Rust           | Ownership, Borrowing, Threads, async/await |
  | C++            | Threads, async/await (with C++20)          |
  | Kotlin         | Coroutines, async/await                    |
  | Swift          | Grand Central Dispatch (GCD), async/await  |

  
## 6. Generic 
- Focuses on algorithms that can be written in a way that allows types to be specified later.
- The main benefit is the ability to write code that is agnostic to particular data types, enhancing reusability.
- Supported Languages
  
  | Language    | Support           |
  |-------------|-------------------------------------------|
  | C++         | Templates                                 |
  | Java        | Generics                                  |
  | C#          | Generics                                  |
  | Swift       | Generics                                  |
  | TypeScript  | Generics                                  |
  | Kotlin      | Generics                                  |
  | Rust        | Generics, Traits                          |
  | Go          | Generics (introduced in Go 1.18)          |
  | Python      | Duck typing, Type Hints (PEP 484)         |

- example: python
  ```python
  from typing import TypeVar, Generic, List
  
  T = TypeVar('T')  # Declare type variable
  
  class Stack(Generic[T]):
      def __init__(self) -> None:
          self.items: List[T] = []
  
      def push(self, item: T) -> None:
          self.items.append(item)
  
      def pop(self) -> T:
          return self.items.pop()
  
      def peek(self) -> T:
          return self.items[-1]
  
  # Using the generic Stack class
  stack_int = Stack[int]()
  stack_int.push(1)
  print(stack_int.pop())  # Output: 1
  
  stack_str = Stack[str]()
  stack_str.push("hello")
  print(stack_str.pop())  # Output: "hello"


  # In this example, Stack is a generic class that can be parameterized with different types (int, str, etc.). This allows the Stack class to be used in a type-safe manner, with type checking tools like Mypy able to detect type mismatches at static analysis time.
  ```

  
## 7. Reflective 
- Enables a program to inspect and modify its structure and behavior at **runtime**.
- The inspect module for getting more detailed information about objects, such as the source code, the list of arguments a function takes, etc.
- Supported Languages
  
  | Language         | Support                                        |
  |------------------|------------------------------------------------------------------|
  | Java             | Full (via the `java.lang.reflect` package)                       |
  | C#               | Full (through Reflection namespace)                              |
  | Python           | Full (using types and functions in the `reflect` and `inspect` modules) |
  | JavaScript       | Partial (via prototype inspection and property enumeration)      |
  | Ruby             | Full (with methods like `send`, `method`, and introspection capabilities) |
  | PHP              | Full (through its Reflection classes)                            |
  | Swift            | Limited (runtime type information and dynamic features)          |
  | Go               | Limited (via the `reflect` package, though not as dynamic as in other languages) |

- example: python
  
  ```python
  '''
  Python offers various built-in functions and modules for reflective operations, such as:
    1. The type() and isinstance() functions for inspecting object types.
    2. The getattr(), setattr(), hasattr(), and delattr() functions for interacting with object attributes dynamically.
    3. The dir() function for listing the attributes and methods of an object.
  '''
  
  class MyClass:
    def __init__(self, value):
        self.value = value

    def show(self):
        print(f"Value: {self.value}")

  obj = MyClass(10)
  
  # Inspect the object's attributes
  print(dir(obj))
  
  # Dynamically get an attribute value
  print(getattr(obj, "value"))
  
  # Dynamically set an attribute value
  setattr(obj, "value", 20)
  obj.show()
  
  # Check if the object has a specific attribute
  print(hasattr(obj, "show"))
  
  # Dynamically call a method
  method = getattr(obj, "show")
  method()
  ```

## 8. Symbolic 
- Symbolic programming is a paradigm primarily associated with AI, focusing on the manipulation of symbols and symbolic expressions, allowing for the manipulation of these symbols mathematically rather than just performing numeric computations.
- Supported Languages
  
  | Language    | Support                | Notes                                                        |
  |-------------|------------------------|--------------------------------------------------------------|
  | Lisp        | Native                 | Historically significant for symbolic AI.                    |
  | Prolog      | Native                 | Logic programming with symbolic reasoning.                    |
  | Julia       | Through Libraries      | High-performance, with symbolic packages like SymPy.jl.      |
  | Python      | Through Libraries      | Popular libraries like SymPy for symbolic math.              |
  | MATLAB      | Through Symbolic Toolbox | Used for mathematical computations including symbolic.     |
  | R           | Through Libraries      | Symbolic computing via Ryacas and other packages.            |

- example: lisp
  ```lisp
  (define (square x) (* x x))
  
  (square 5)
  ; Evaluates to 25, demonstrating a simple symbolic manipulation of squaring a number.
  ```
## 9. Metaprogramming 
- Allows programs to treat other programs as their data 
- This means a program can be designed to read, generate, analyze, or transform other programs, and even modify itself while running.
- Supported Languages
  
  | Language | Support | Notes |
  |----------|-----------|------|
  | Ruby     | Extensive | Dynamic metaprogramming through open classes, reflection, and the ability to evaluate strings as code. |
  | Lisp     | Extensive | Macros and symbolic computation, allowing programs to manipulate and generate code. |
  | Python   | Yes       | Reflection, decorators, and metaclasses for runtime and compile-time metaprogramming. |
  | C++      | Yes       | Templates for compile-time metaprogramming, and RTTI (Run-Time Type Information) for runtime type identification. |
  | Java     | Yes       | Reflection API for inspecting and modifying code at runtime, annotation processors for compile-time metaprogramming. |
  | Go       | Limited   | Limited support through interfaces and reflection, but lacks generics in its traditional form (generics added in Go 1.18). |
  | C#       | Yes       | Attributes, reflection, expression trees, and source generators for runtime and compile-time metaprogramming. |



- example: python
  ```python
  def log_function_call(func):
      def wrapper(*args, **kwargs):
          print(f"Calling function '{func.__name__}' with arguments {args} and keyword arguments {kwargs}")
          result = func(*args, **kwargs)
          print(f"'{func.__name__}' returned {result}")
          return result
      return wrapper
  
  @log_function_call
  def add(a, b):
      return a + b
  
  # When you call add, it's now wrapped by log_function_call, which logs its execution.
  add(10, 5)

  ```
# Text & Bytes

  |          | Text                                          | Bytes                                         |
  |------------------|--------------------------------------------------|--------------------------------------------------|
  | Definition       | A sequence of characters representing linguistic expressions. | A sequence of bytes representing binary data.    |
  | Data Type        | Character data (e.g., Unicode in Python).        | Binary data (e.g., byte literals in Python).     |
  | Encoding         | Requires an encoding standard (e.g., UTF-8) to be converted into bytes. | Raw format that can be interpreted into text or other data types using specific encoding. |
  | Usage            | Used for text processing, manipulation, and storage in a readable format for humans. | Used for low-level data manipulation and storage, including binary files, images, and serialized objects. |
  | Mutability       | Immutable in some languages (e.g., Python strings). | Immutable if defined as a bytes literal in some languages (e.g., Python). |
  | Storage Efficiency | Less efficient compared to bytes for non-ASCII characters due to encoding (e.g., UTF-8 uses more bytes for characters outside the ASCII range). | More efficient for storing binary data and ASCII characters. |
  | Operations       | Supports operations like concatenation, slicing, and case conversion. | Supports operations like concatenation, slicing, but not text-specific operations like case conversion. |
  | Compatibility    | Directly readable and manipulable by humans and text-processing tools. | Requires decoding to be human-readable. Compatible with binary data processing tools. |

- Text
  | Advantages                                                                                         | Disadvantages                                                                                       |
  |----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
  | Human-readable, without needing decoding.                                   | More storage space for non-ASCII characters due to the nature of encoding standards.    |
  | Widely supported across programming languages with extensive functions for manipulation (e.g., search, replace). | Potential for confusion and errors due to multiple encoding standards (e.g., UTF-8 vs. ISO 8859-1). |
  | Can represent a vast range of characters from various languages using encoding standards like UTF-8. |                                                                                                     |
- Bites
  | Advantages                                                                                                         | Disadvantages                                                                                                |
  |--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
  | More storage-efficient for binary data, can be more efficient for ASCII characters.                             | Not directly readable without decoding, which can add a layer of complexity for text manipulation.           |
  | Can handle any binary data, including images, audio, and video files, making it versatile for different applications. | Primarily useful for binary data manipulation, which can be limiting for applications that primarily deal with text. |
  | Suitable for operations that require direct manipulation of memory contents.                                       | Requires explicit encoding and decoding for text representation, introducing potential for errors if not handled correctly. |


# Library & Framework
