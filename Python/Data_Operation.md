- [Operation](#operation)
- [Operands](#operands)
  - [Any Object](#any-object)
    - [Numeric](#numeric)
    - [String](#string)
    - [List,Tuple,Set,Dict](#listtuplesetdict)
    - [Boolean:](#boolean)
    - [None:](#none)
    - [File](#file)
  - [Operand Compatibility \& Type Conversion](#operand-compatibility--type-conversion)
- [Operators](#operators)
  - [Type](#type)
    - [1. Arithmetic](#1-arithmetic)
    - [2. Comparison](#2-comparison)
    - [3. Logical](#3-logical)
    - [4. Assignment Operators](#4-assignment-operators)
    - [5. Membership](#5-membership)
    - [6. Identity](#6-identity)
    - [7. Bitwise](#7-bitwise)
    - [8. Unary](#8-unary)
    - [9. Binary](#9-binary)
    - [10. Ternary operators (or conditional operators)](#10-ternary-operators-or-conditional-operators)

# Operation
- Python follows a precedence rule to determine the order of operations.
# Operands
## Any Object
### Numeric
- `int`
- `float`
- `complex`
### String
### List,Tuple,Set,Dict
### Boolean:
   - `bool`: Represents boolean values `True` and `False`.
### None:
   - `None`: Represents the absence of a value or a null value.

### File
## Operand Compatibility & Type Conversion
- int(), str(), float().


# Operators
## Type
### 1. Arithmetic
Used for performing mathematical calculations like addition, subtraction, multiplication, etc.

- `+` Addition: Adds two operands.
- `-` Subtraction: Subtracts right operand from the left.
- `*` Multiplication: Multiplies two operands.
- `/` Division: Divides left operand by the right one (result is always a float).
- `%` Modulus: Returns remainder of division.
- `**` Exponentiation: Raises the left operand to the power of the right.
- `//` Floor Division: Division that results into whole number adjusted to the left in the number line.

### 2. Comparison
Used for comparing values. It either returns True or False according to the condition.

- `==` Equal to: True if both operands are equal.
- `!=` Not equal to: True if operands are not equal.
- `>` Greater than: True if left operand is greater than the right.
- `<` Less than: True if left operand is less than the right.
- `>=` Greater than or equal to: True if left operand is greater than or equal to the right.
- `<=` Less than or equal to: True if left operand is less than or equal to the right.

### 3. Logical
Used to combine conditional statements.

- `and` True if both operands are true.
- `or` True if either of the operands is true.
- `not` True if operand is false (complements the operand).

### 4. Assignment Operators
Used to assign values to variables.

- `=` Assigns value from right side operands to left side operand.
- `+=` Adds right operand to the left operand and assign the result to left operand.
- `-=` Subtracts right operand from the left operand and assign the result to left operand.
- Other variations include `*=`, `/=`, `%=`, `**=`, `//=`, etc., each applying the operation and assigning the result.

### 5. Membership
Used to test whether a value or variable is found in a sequence (string, list, tuple, set, and dictionary).

- `in` True if value is found in the sequence.
- `not in` True if value is not found in the sequence.

### 6. Identity
Used to compare the memory locations of two objects.

- `is` True if the operands are identical (refer to the same object).
- `is not` True if the operands are not identical (do not refer to the same object).

### 7. Bitwise
Operate on bits and perform bit-by-bit operations.

- `&` Bitwise AND
- `|` Bitwise OR
- `^` Bitwise XOR
- `~` Bitwise NOT
- `<<` Bitwise left shift
- `>>` Bitwise right shift


### 8. Unary  
  - require a single operand (e.g.,  -x).
### 9. Binary  
  - require two operands (e.g.,  x + y).
### 10. Ternary operators (or conditional operators) 
  - require three operands (e.g., x if condition else y ).
