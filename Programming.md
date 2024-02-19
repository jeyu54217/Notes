

- [Code Execution](#code-execution)
  - [1. Interprete](#1-interprete)
  - [2. Compile](#2-compile)
  - [3. Just In Time (JIT)](#3-just-in-time-jit)
- [Dynamic \& Static Type](#dynamic--static-type)
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
| Feature             | Interpreter                                        | Compiler                                                                   | JIT Compiler                                                                |
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
- **Java**
 - **Source Code → Compiler → a Byte Code file →**
    **Byte Code Line/Chunk → JIT Interpreter → Machine Code → Execution → Byte Code Line/Chunk...**
  
  <img width="1028" alt="Screenshot 2024-02-19 at 00 57 31" src="https://github.com/jeyu54217/Notes/assets/73396926/64d6495b-8375-4bc6-a013-d06115e95d15">
## Data Type
# Dynamic & Static Typing
|               | Dynamic Typing                                                                                                                                                                                                                          | Static Typing                                                                                                                                                                                                                           |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Type Checking**     | Type checks are performed at runtime, allowing variable types to change over execution. Offers flexibility in variable use.                                                                                                               | Type checks are performed at compile-time, ensuring types are correct before program runs. Catches type-related errors early.                                                                                                                |
| **Flexibility**       | High, with easy reassignment of variables to different types. Beneficial for rapid development and evolving requirements.                                                                                                                  | Lower, as variables are bound to a specific type once declared. Makes code more predictable but requires more upfront design.                                                                                                               |
| **Performance**       | May have performance overhead due to runtime type checking and interpretation.                                                                                                                                                             | Typically results in faster execution times due to compile-time optimizations.                                                                                                                                                              |
| **Error Detection**   | Errors related to type found at runtime, leading to potential runtime errors and increased debugging time.                                                                                                                                 | Caught at compile-time, reducing runtime errors and saving debugging time.                                                                                                                                                                   |
| **Code Verbosity**    | Less verbose, as types do not need to be explicitly declared.                                                                                                                                                                              | More verbose due to explicit type declarations, which can make code more explicit and potentially increase readability.                                                                                                                     |
| **Tooling and IDE Support** | Some level of type inference and checking in IDEs, but limited compared to static typing due to runtime type checks.                                                                                                                      | Strong support for autocomplete, refactoring, and static analysis tools due to compile-time type information. Improves productivity and code quality.                                                                                       |
| **Use Cases**         | Suited for scripting, rapid prototyping, and applications where flexibility is key.                                                                                                                                                       | Ideal for large-scale applications, systems programming, where performance and type safety are critical.                                                                                                                                    |

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
