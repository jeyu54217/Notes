- [Operation](#operation)
- [Operands](#operands)
  - [Types of Operands](#types-of-operands)
    - [1. **Literal Operands**](#1-literal-operands)
    - [2. **Variable Operands**](#2-variable-operands)
    - [3. **Expression Operands**](#3-expression-operands)
    - [4. **Object Operands**](#4-object-operands)
  - [Operand Evaluation](#operand-evaluation)
  - [Implicit Type Conversion](#implicit-type-conversion)
- [Operators](#operators)
  - [1. Arithmetic Operators](#1-arithmetic-operators)
  - [2. Relational Operators](#2-relational-operators)
  - [3. Logical Operators](#3-logical-operators)
  - [4. Assignment Operators](#4-assignment-operators)
  - [5. Bitwise Operators](#5-bitwise-operators)
  - [6. Unary Operators](#6-unary-operators)
  - [7. Ternary Operator](#7-ternary-operator)
    - [Usage Example](#usage-example)

# Operation
- Python follows a precedence rule to determine the order of operations.
# Operands

In Java, operands are the values that operators act upon. When performing operations, such as arithmetic, logical, or comparison operations, operands are the entities required to complete the operation. Java supports various types of operands, including primitive data types (like int, float, double, char), objects, and expressions that evaluate to a value.

## Types of Operands

Java categorizes operands based on the types of operations they are involved in. Here are the main types:

### 1. **Literal Operands**
Literal operands are constant values explicitly stated in the code. They represent fixed values and can be of various data types, such as integers, floating-point numbers, characters, and strings.

```java
int number = 10; // 10 is a literal operand
```

### 2. **Variable Operands**
Variables are memory locations that store values. In operations, the value contained in a variable is used as an operand.

```java
int a = 5;
int b = a + 10; // a is a variable operand
```

### 3. **Expression Operands**
Expressions that evaluate to a single value can also serve as operands. These expressions can involve variables, literals, method calls, and operators.

```java
int result = (a + b) * 2; // (a + b) * 2 is an expression operand
```

### 4. **Object Operands**
In object-oriented operations, objects themselves can be operands. This is common in methods that operate on objects, such as comparing two objects.

```java
String str1 = "Hello";
String str2 = "World";
boolean isEqual = str1.equals(str2); // str1 and str2 are object operands
```

## Operand Evaluation

Java evaluates operands based on the context of the operation. The type of operation determines how operands are interpreted and what operations are permissible. For example, in arithmetic operations, operands are expected to be numeric types (byte, short, int, long, float, double), while logical operations expect boolean operands.

## Implicit Type Conversion

Java may perform implicit type conversion (also known as type promotion) on operands to match the data types expected by an operation. This is common in expressions involving multiple data types.

```java
int integer = 10;
double floatingPoint = 5.5;
double result = integer + floatingPoint; // integer is promoted to double
```



# Operators

## 1. Arithmetic Operators
- `+` (Addition): Adds two values.
- `-` (Subtraction): Subtracts one value from another.
- `*` (Multiplication): Multiplies two values.
- `/` (Division): Divides one value by another.
- `%` (Modulus): Returns the remainder of a division.

## 2. Relational Operators
- `==` (Equal to): Checks if two values are equal.
- `!=` (Not Equal to): Checks if two values are not equal.
- `>` (Greater than): Checks if a value is greater than the other.
- `<` (Less than): Checks if a value is less than the other.
- `>=` (Greater than or equal to): Checks if a value is greater than or equal to the other.
- `<=` (Less than or equal to): Checks if a value is less than or equal to the other.

## 3. Logical Operators
- `&&` (Logical AND): Returns true if both operands are true.
- `||` (Logical OR): Returns true if at least one of the operands is true.
- `!` (Logical NOT): Reverses the logical state of its operand.

## 4. Assignment Operators
- `=` (Assignment): Assigns a value to a variable.
- `+=` (Add and assign): Adds and assigns the value.
- `-=` (Subtract and assign): Subtracts and assigns the value.
- `*=` (Multiply and assign): Multiplies and assigns the value.
- `/=` (Divide and assign): Divides and assigns the value.
- `%=` (Modulus and assign): Applies modulus and assigns the value.

## 5. Bitwise Operators
- `&` (Bitwise AND): Applies AND on binary representations of the operands.
- `|` (Bitwise OR): Applies OR on binary representations of the operands.
- `^` (Bitwise XOR): Applies XOR on binary representations of the operands.
- `~` (Bitwise Complement): Inverts all the bits of the operand.
- `<<` (Left shift): Shifts bits to the left.
- `>>` (Right shift): Shifts bits to the right.
- `>>>` (Unsigned right shift): Shifts bits to the right without sign extension.

## 6. Unary Operators
- `+` (Unary plus): Indicates a positive value.
- `-` (Unary minus): Negates an expression.
- `++` (Increment): Increases a value by 1.
- `--` (Decrement): Decreases a value by 1.

## 7. Ternary Operator
- `? :` (Conditional): Returns one of two values based on a condition.

### Usage Example

Here's a simple example to demonstrate the use of operators in Java:

```java
public class OperatorsExample {
    public static void main(String[] args) {
        int a = 10, b = 5;
        int sum = a + b; // Arithmetic + operator
        System.out.println("Sum = " + sum);
        boolean isEqual = (a == b); // Relational == operator
        System.out.println("Is Equal? " + isEqual);
    }
}
```
