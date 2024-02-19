

- [Code Execution](#code-execution)
  - [1. Interprete](#1-interprete)
  - [2. Compile](#2-compile)
  - [3. Just In Time (JIT)](#3-just-in-time-jit)
- [Data Typing](#data-typing)
  - [1. Dynamic \& Static Typing](#1-dynamic--static-typing)
  - [2. Strong \& Weak Typing](#2-strong--weak-typing)
- [Programming Paradigms](#programming-paradigms)
  - [1. Imperative Programming](#1-imperative-programming)
    - [**Procedural Programming:**](#procedural-programming)
    - [**Object-Oriented Programming (OOP):**](#object-oriented-programming-oop)
  - [2. Declarative Programming](#2-declarative-programming)
    - [**Functional Programming (FP):**](#functional-programming-fp)
    - [**Logic Programming:**](#logic-programming)
    - [**Database Query Languages:**](#database-query-languages)
  - [3. Structured Programming](#3-structured-programming)
  - [4. Event-Driven Programming](#4-event-driven-programming)
  - [5. Concurrent Programming](#5-concurrent-programming)
  - [6. Aspect-Oriented Programming (AOP)](#6-aspect-oriented-programming-aop)
  - [7. Generic Programming](#7-generic-programming)
  - [8. Reflective Programming](#8-reflective-programming)
  - [9. Symbolic Programming](#9-symbolic-programming)
  - [10. Metaprogramming](#10-metaprogramming)
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

## 1. Dynamic & Static Typing

|               | Dynamic Typing                                                                                                                                                                                                                        | Static Typing                                                                                                                                                                                                                           |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Type Checking**     | Type checks are performed at runtime, allowing variable types to change over execution. Offers flexibility in variable use.                                                                                                           | Type checks are performed at compile-time, ensuring types are correct before the program runs. Catches type-related errors early.                                                                                                        |
| **Flexibility**       | High, with easy reassignment of variables to different types. Beneficial for rapid development and evolving requirements.                                                                                                              | Lower, as variables are bound to a specific type once declared. Makes code more predictable but requires more upfront design.                                                                                                           |
| **Performance**       | May have performance overhead due to runtime type checking and interpretation.                                                                                                                                                         | Typically results in faster execution times due to compile-time optimizations.                                                                                                                                                          |
| **Error Detection**   | Errors related to type found at runtime, leading to potential runtime errors and increased debugging time.                                                                                                                             | Caught at compile-time, reducing runtime errors and saving debugging time.                                                                                                                                                               |
| **Code Verbosity**    | Less verbose, as types do not need to be explicitly declared.                                                                                                                                                                          | More verbose due to explicit type declarations, which can make code more explicit and potentially increase readability.                                                                                                                 |
| **Use Cases**         | Suited for scripting, rapid prototyping, and applications where flexibility is key.                                                                                                                                                    | Ideal for large-scale applications, systems programming, where performance and type safety are critical.                                                                                                                                |

## 2. Strong & Weak Typing

|               | Strong Typing                                                                                                                                                      | Weak Typing                                                                                                                                                    |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Type Coercion**     | Minimal to no implicit type coercion. Operations between incompatible types require explicit conversion, enhancing type safety and predictability.                     | Implicit type coercion is common, allowing operations between different types without explicit conversion, which can lead to flexibility but also unpredictability. |
| **Type Safety**       | High. The language enforces strict type rules, reducing the chances of runtime errors due to type mismatches.                                                         | Lower. The flexibility in types can increase the risk of type-related runtime errors.                                                                             |
| **Error Detection**   | Errors related to type mismatches are more likely to be caught early, either at compile-time (for statically typed languages) or at runtime before they cause issues. | Type-related errors might only become apparent at runtime, potentially leading to bugs that are harder to trace and fix.                                          |
| **Runtime Behavior**  | Predictable. The strict type system ensures that operations behave as expected, without implicit changes in type.                                                     | Less predictable. Implicit type conversions can lead to unexpected behavior, making the code harder to understand and debug.                                      |
| **Flexibility**       | Lower. The need for explicit type conversions can make the code more verbose and potentially slow down rapid development.                                             | Higher. Allows for quicker prototyping and development due to the ease of mixing types, but at the cost of potential runtime issues.                               |
| **Use Cases**         | Preferred in applications where reliability and maintainability are critical, such as large-scale or complex systems.                                                  | Suited for scripting, rapid prototyping, or environments where the ease of development is prioritized over strict type safety.                                    |
- Strong Typing
  | Advantages                            | Disadvantages                                                      |
|---------------------------------------|--------------------------------------------------------------------|
| **Type Safety:** Reduces the likelihood of type-related runtime errors, increasing the reliability of the code. | **Less Flexibility:** Can limit rapid development due to the need for explicit conversions and declarations. |
| **Error Detection:** Type mismatches are often caught early, improving code quality and maintainability.       | **Verbosity:** Code might be more verbose due to explicit type conversions and declarations.                   |
| **Predictability:** Operations behave as expected without implicit type changes, making the code easier to understand and debug. | **Slower Prototyping:** The strict type system can slow down initial development and prototyping.
             |
- Weak Typing
| Advantages                            | Disadvantages                                                         |
|---------------------------------------|-----------------------------------------------------------------------|
| **Flexibility:** Allows for easy mixing of types, facilitating rapid development and prototyping. | **Type Safety:** Increased risk of type-related errors at runtime, which can affect the reliability of the code. |
| **Ease of Development:** Can speed up development by reducing the need for explicit type conversions. | **Unpredictability:** Implicit type conversions can lead to unexpected behavior and make the code harder to debug. |
| **Rapid Prototyping:** Ideal for scenarios where speed of development is prioritized over strict type safety. | **Error Detection:** Type-related errors may only become apparent at runtime, potentially leading to more complex debugging. |

# Programming Paradigms
## 1. Imperative Programming
- Imperative programming is characterized by a series of commands for the computer to perform. It's one of the oldest programming paradigms and forms the basis of many other paradigms.

### **Procedural Programming:** 
- A subtype of imperative programming, it structures code into procedures or functions, facilitating code reuse and modularization. Languages like C and Pascal are well-known examples.
### **Object-Oriented Programming (OOP):** 
- Focuses on defining data structures as objects and the operations that can be performed on them, promoting data encapsulation, inheritance, and polymorphism. Java, C++, and Python are languages that support OOP.

## 2. Declarative Programming
Declarative programming expresses the logic of a computation without describing its control flow. It abstracts the flow control process, letting developers focus on "what" a program should accomplish rather than "how."

### **Functional Programming (FP):** 
- Emphasizes pure functions and immutable data. Haskell and Clojure are prominent examples. FP supports higher-order functions, function composition, and recursion, aiming for side-effect-free code.
### **Logic Programming:** 
- Uses formal logic to express computations. Prolog is a notable example, where programs are written as a set of facts and rules within a logical framework.
### **Database Query Languages:** 
- SQL (Structured Query Language) is a prime example, enabling the definition, manipulation, and query of data in relational databases.

## 3. Structured Programming
- Aimed at improving the clarity, quality, and development time of a computer program by making extensive use of subroutines, block structures, for and while loops. It's a step away from the GOTO statement, promoting more logical and manageable code flow.

## 4. Event-Driven Programming
- Centers around the generation and handling of events. In this paradigm, the flow of the program is determined by events such as user actions, sensor outputs, or message passing from other programs or threads. JavaScript, used in web development, is a well-known example.

## 5. Concurrent Programming
- Involves writing programs that can execute operations simultaneously, either through multiple threads or processes. This paradigm is essential for exploiting multi-core processors and for developing applications that require concurrent operations, such as web servers. Languages that support concurrency include Java (via threads) and Go (with goroutines).

## 6. Aspect-Oriented Programming (AOP)
- Allows for the separation of concerns, especially those that cut across multiple modules of a program. It's useful for encapsulating cross-cutting concerns like logging, transaction management, or security features into separate modules. AspectJ is an example of an AOP language.

## 7. Generic Programming
- Focuses on algorithms that can be written in a way that allows types to be specified later. The main benefit is the ability to write code that is agnostic to particular data types, enhancing reusability. C++ templates and Java generics are implementations of this paradigm.

## 8. Reflective Programming
- Enables a program to inspect and modify its structure and behavior at runtime. This paradigm is powerful for developing frameworks and libraries that need to perform complex manipulations of their components. Java and .NET languages support reflection.

## 9. Symbolic Programming
- Used predominantly in artificial intelligence, it emphasizes the manipulation of symbols and symbolic expressions. Lisp, one of the oldest programming languages, is known for its capacity for symbolic computation.

## 10. Metaprogramming
- Involves writing programs that can treat programs as their data. It means that a program could be designed to read, generate, analyze, or transform other programs, and even modify itself while running. Languages that support metaprogramming include Ruby and Lisp.

# Text & Bytes
