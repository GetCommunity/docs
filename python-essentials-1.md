# Python Essentials 1 - PCAP-30-02 Certification

- [Python Essentials 1 - PCAP-30-02 Certification](#python-essentials-1---pcap-30-02-certification)
  - [Module 1](#module-1)
    - [Introduction to Computer Programming](#introduction-to-computer-programming)
    - [Compilation vs. Interpretation](#compilation-vs-interpretation)
      - [Compilation](#compilation)
        - [Advantages of Compilation](#advantages-of-compilation)
        - [Disadvantages of Compilation](#disadvantages-of-compilation)
      - [Interpretation](#interpretation)
        - [The Interpreter Order Of Operations](#the-interpreter-order-of-operations)
        - [Advantages of Interpretation](#advantages-of-interpretation)
        - [Disadvantages of Interpretation](#disadvantages-of-interpretation)
    - [Python](#python)
      - [Core Features of Python](#core-features-of-python)
      - [Python Use Cases](#python-use-cases)
      - [Python Versions](#python-versions)
  - [Module 2](#module-2)
    - [Functions()](#functions)
      - [Example Built-In Python Functions](#example-built-in-python-functions)
      - [Functions vs. Methods](#functions-vs-methods)
    - [Literals](#literals)
    - [Operators + Expressions](#operators--expressions)
    - [Variables](#variables)
      - [Reserved Python Keywords](#reserved-python-keywords)
      - [Variable Types, Typing, and Type Casting](#variable-types-typing-and-type-casting)
  - [Module 3](#module-3)
    - [Comparison Operations](#comparison-operations)
    - [Conditional Instruction / Conditional Statement](#conditional-instruction--conditional-statement)
    - [Loops](#loops)
    - [Logic Operations and Expressions](#logic-operations-and-expressions)
    - [Bitwise Operations](#bitwise-operations)
    - [Lists](#lists)
      - [List Operations](#list-operations)
      - [Sorting Lists](#sorting-lists)
      - [Processing Lists](#processing-lists)
      - [List Comprehension \& Multidimensional Arrays](#list-comprehension--multidimensional-arrays)
  - [Module 4](#module-4)
    - [Functions](#functions-1)
      - [Functions come from](#functions-come-from)
      - [Function Invocation](#function-invocation)
      - [Function Parameters and Argument Passing](#function-parameters-and-argument-passing)
      - [Example Parameterized Functions](#example-parameterized-functions)
      - [`return` the Results of a Function](#return-the-results-of-a-function)
      - [The `None` Keyword](#the-none-keyword)
      - [Exercises Using Functions](#exercises-using-functions)
        - [Calculate the number of days in a given year](#calculate-the-number-of-days-in-a-given-year)
        - [Calculate all the Prime Numbers between 2 and any number](#calculate-all-the-prime-numbers-between-2-and-any-number)
      - [Functions and Scopes](#functions-and-scopes)
      - [Exercises Using Function Scopes](#exercises-using-function-scopes)
        - [Converting BMI in Metric/Imperial Units](#converting-bmi-in-metricimperial-units)
        - [Making Functions More Pythonic](#making-functions-more-pythonic)
        - [Finding a `Factorial!`](#finding-a-factorial)
        - [`Factorial!` Function Implemented Recursively](#factorial-function-implemented-recursively)
    - [Tuples](#tuples)
    - [Dictionaries](#dictionaries)
      - [Creating a Dictionary](#creating-a-dictionary)
      - [Sorting a Dictionary (or List)](#sorting-a-dictionary-or-list)
      - [Accessing Dictionary Values](#accessing-dictionary-values)
      - [Modifying \& Adding Dictionary Items](#modifying--adding-dictionary-items)
    - [Errors and The `exception` Keyword](#errors-and-the-exception-keyword)
      - [Useful Exceptions](#useful-exceptions)
      - [Testing for Exceptions](#testing-for-exceptions)
      - [Debugging Tips](#debugging-tips)
      - [Unit Testing](#unit-testing)
    - [Additional Notes](#additional-notes)
      - [Python Built-in Functions](#python-built-in-functions)
      - [Priority of Operations](#priority-of-operations)

---

## Module 1

Introduction to Computer Programming.

### Introduction to Computer Programming

- A **Program** is a set of instructions for the computer to execute that completes a series of tasks or operations on the system.
- **Natural Languages** and **Programming Languages** contain four key aspects in order to be understood widely:

1. alphabet
2. lexis
3. syntax
4. semantics

- An **Instruction List** is a complete set of known commands by the _Machine Language_.
- In **Machine Language**, the _Instruction List (IL)_ is the alphabet.
- A **High-Level Programming Language** is written using symbols, words, and conventions easily read by humans.
- **Source Code** is a program written in a high-level programming language.
- A **Script** is a text file that contains instructions written in a high-level programming language.
- In contrast, a **Low-Level Programming Language** is the actual **Machine Code** executed by the computer's _Instruction List_.
- Low-level languages are extremely difficult for humans to read and understand at face value, but are the fastest for a computer to complete.

### Compilation vs. Interpretation

**Computer Programming** is the act of writing a programming language in an order that achieves the desired effect or output. Once a program is written in a programming language it needs to be translated so the computer can execute it. There are two different ways of transforming a program from a high-level programming language into (low-level) machine language.

#### Compilation

- source code translated once down to machine code
- the translation must be re-completed if the source code is modified
- the machine code executable file (ie. app.exe) is distributed to users
- users run the executable machine code directly on their machine systems

##### Advantages of Compilation

- usually executes code faster
- only the programmer needs the compiler
- machine code is difficult for end users to decipher, but easy to execute

##### Disadvantages of Compilation

- compilation can be very time-consuming
- programmer needs as many compilers as hardware platforms the code is to be run on (Linux, Mac, Microsoft)

#### Interpretation

- the _Interpreter_ translates the code every time it is executed
- the source code cannot distribute as-is
- the user's machine needs the interpreter to be able to translate the source code into machine code to execute it

##### The Interpreter Order Of Operations

1. reads a raw source code file text
2. checks the text lines for language errors

- finds an error, the program stops, shows an error message... OR
- no errors found, continue

1. interpreter executes the line and continues to the next line

- read-check-execute can be repeated many times
- some code may execute before an error is even found

##### Advantages of Interpretation

- code can run as soon as it's written, as code is translated at runtime
- code can be run on computers using different machine languages (no separate compilation for each hardware platform)

##### Disadvantages of Interpretation

- code executes not as fast as machine code because the interpreter shares power with the computer
- end-users need to have the correct interpreter on their system to run the code

### Python

- an interpreted, object-oriented, high-level programming language
- named after Monty Python's Flying Circus (BBC TV Comedy sketch series)
- created by **Guido van Rossum** (b. 1956, Netherlands) between 1989-1999

#### Core Features of Python

**Guido van Rossum** presented in 1999 "Computer Programming for Everybody" proposal to DARPA:

- an easy and intuitive language just as powerful as those of the major competitors;
- open source, so anyone can contribute to its development;
- code that is as understandable as plain English;
- suitable for everyday tasks, allowing for short development times.
- Direct Competitors: Perl, Ruby

#### Python Use Cases

- web development
- scientific and numeric computing
- education
- desktop GUIs
- software development
- business operations

#### Python Versions

- **CPython** is the default implementation of the Python programming language (Python Software Foundation)
- **Cython** is a superset of Python that compiles Python and C code
- **Jython** is a superset of Python written in integration with Java apps
- **PyPy & RPython** are a subset of Python within python
  Tools Needed for _IDLE: Integrated Development and Learning Environment_
- a **code editor** is a tool used to write Python code
- a **console** is a command-line interpreter which lets you interact with your OS and execute Python commands and scripts
- a **debugger** is a tool that launches code step-by-step and inspects it at each moment of execution

---

## Module 2

Data types, variables, basic input-output operations, and basic operators.

```python
# comment like this
print("some action")
```

### Functions()

- A **function** may cause **an effect** or result in **a value** and are provided with **arguments**.
- They are _built-in_ to the Python language, _provided by a Python module_, or _custom written_ by a Python programmer.
- Function arguments can be anonymous or provided by name, but all functions must be invoked by wrapping arguments in parentheses after the function name (**function invocation**).

```python
print()
>
print("hello world")
> hello world
```

Functions **must be declared prior to the where said function is invoked**.

```python
# INVALID: invoking the function before the definition
customPrint(message="hello world")
> NameError

# defining the function
def customPrint(message=""):
 print("custom print said:", message)

# invoking the function
customPrint(message="hello world")
> custom print said: hello world

NameError: name 'customPrint' is not defined
```

The print() function below:

- arguments: takes 0 or more
- in func: converts arguments into a human readable format
- effect: sends the resulting data to the output device (ie. the console)
  Unlike most programming languages, Python requires that _there cannot be more than one instruction in a line_.

```python
# INVALID
print("hello")print("world")
> SyntaxError
```

Functions with keyword arguments follow two specific rules:

1. a keyword argument consists of three elements:
   - a **keyword** identifying the argument
   - an **equal sign**
   - a **value** assigned to that argument
2. any **keyword arguments must be put after the last positional argument**

#### Example Built-In Python Functions

```python
# INVALID
print(end="end.", "This is the ")
> Error

# OK!
print("This is the ", end="end.")
> This is the end.
print("This is the", "end.", sep=" ")
> This is the end.

print("Hello arg...", end=" this is the end.", sep="-")
> Hello arg... this is the end.

print("My", "name", "is", "Monty", "Python.", sep="-")
> My-name-is-Monty-Python.

print("My", "name", "is", sep="_", end="*")
print("Monty", "Python.", sep="*", end="*\n")
> My_name_is*Monty*Python.*
```

#### Functions vs. Methods

**Functions do not belong to any data**: it gets data, may create new data*, and*it may return data.

```python
result = function(arg)
```

A **method is owned by the data it works for**, while a _function is owned by the whole code_; methods behave as functions but can change the internal state of the data from which it was invoked.

```python
result = data.method(arg)
```

### Literals

**Literals** are notations for representing some fixed value in code.
**Numeric Literals** express different number systems:

- **Binary numbers** use a base 2 system; binary 1010 is 10 in decimal.
- **Octal numbers** use base 8.

```python
print(0o123)
```

- **Hexadecimal numbers** use base 16

```python
print(0x123)
```

- **Scientific numbers** use base 10

```python
# 300000000
print(3E8, 3e8)
```

- **Integers** (int) numbers without a fractional component

```python
print(256, -1)
```

- **Floating-point numbers** (float) numbers express a fraction

```python
print(2.546, 2.5, -0.4, .4, 4.)
```

- **Boolean Literals** (bool) express truthfulness (True, False).

```python
print(True)
print(False)
print(True > False) # True
print(True < False) # False
```

**String Literals** (string) express text values:

- can be empty ""
- The **backslash `\`** is a unique literal that affects the way the subsequent character is treated by the program:

```python
# w/o backslash INVALID
print("I like "Monty Python"")
> SyntaxError

# w/ backslash OK!
print("I like \"Monty Python\"")
# or
print('I like "Monty Python"')
print('', "")
```

**None Literal or NoneType** (none) object represents the absence of a value.

### Operators + Expressions

**Operators** are symbols that act on values and perform mathematical operations. An **Expression** is a combination of values, variables, operators, or calls to functions that evaluate a value. The **Binding** of the operator determines the order of computations performed. Most operators follow left-sided binding, but some cases use right-side binding (e.g. exponentiation).
**The integer vs. float rule:**

```python
# if both args are int, the result is an int
2 ** 3 = 8

# if at least one arg is float, the result is a float
2 ** 3. = 8.0
2. ** 3 = 8.0
2. ** 3. = 8.0
```

**Unary Operators** take one operand, to negate or make a value positive.

```python
+2 is 2
+(-2) is 2
2 vs -2
```

**Addition** follows _int v. float rule_.

```python
2 + 3 = 5
2 + 3. = 5.0
```

**Subtraction** follows _int v. float rule_.

```python
2 - 3 = -1
2 - 3. = -1.0
```

**Exponentiation or Exponents** follow _int v. float rule_; uses right-sided binding.

```python
2 ** 3 = 8
2 ** 3. = 8.0
2 ** 3 ** 2
= 2 ** (3 ** 2)
= 2 ** 9
= 512
```

**Multiplication Operator** follows _int v. float rule_.

```python
6 * 2 = 12
6 * 2. = 12.0
1. * 3 = 3.0
2. * 3. = 6.0
```

**Division operator** _always produces a float_.

```python
6 / 3 = 2.0
6 / 3. = 2.0
1. / 3 = 2.0
2. / 3. = 2.0
```

**Integer Division** uses **Floor Division** to conform the result to _the integer vs. float rule_ by always rounding the result to the lesser integer value.

```python
# round int
6 // 3 = 2

# round float
6 // 3. = 2.0
1. // 3 = 0.0
2. // 3. = 0.0

# int rounded down
6 // 4 = 1 1.5 -> 1
-6 // 4 = -2 -1.5 -> -2

# float rounded down
1. // 4 = 1.0      0.25 -> -0.0
2. // -4 = -2.0    -0.5 -> -1.0
```

The **Remainder (Modulo)** returns the remaining values after the division operation, follows the _int v. float rule_.
**ZeroDivisionError** applies to division, integer division, and the remainder operations.
The **Concatenation** operator uses the + symbol to join strings together ("string" + "string").

```python
print("hello" + " " + "world")
> hello world
```

The **Replication** operator uses the `*` symbol to repeat a string some integer number of times; cannot replicate a string using a floating point value.

```python
string * integer
integer * string
```

```python
# INVALID
string * float
> TypeError
```

**Priorities of Operators** perform higher priority operations before lower ones. Python generally follows the _PEMDAS Rule_ from mathematics.

| priority | operator     | note                 |
| :------- | :----------- | :------------------- |
| 1        | +, -         | unary                |
| 2        | \*\*         | right-sided bindings |
| 3        | \*, /, //, % | n/a                  |
| 4        | +, -         | binary               |

**Shortcut Operators**:

| Expression   | Shortcut  |
| :----------- | :-------- |
| x = x / 2    | x /= 2    |
| x = x // 2   | x //= 2   |
| z = z % z    | z %= z    |
| a = a - 1    | a -= 1    |
| a = a + 1    | a += 1    |
| x = x \* 2   | x \*= 2   |
| y = y \*\* 3 | y \*\*= 3 |

### Variables

A **Variable** is a named location reserved to store values in memory. Auto-initialized when you assign a variable a value.
Each variable must have a unique name, an **Identifier**, a non-empty sequence of characters, _must begin with an underscore or letter_ and cannot be a Python keyword.

```python
a_string = "hello world"
times_int = 2
rand_float = 29.
repeat_string = a_string * times_int
print(repeat_string)
> hello worldhello world
```

#### Reserved Python Keywords

```python
False, None, True, and, as, assert, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
```

A **Compound Assignment Operator (Shortcut Operator)** modify the values assigned to variables

```python
var += 1
var /= 2
```

#### Variable Types, Typing, and Type Casting

**Type Casting** is used to coerce a value to be interpreted as a certain type

```python
int(5.)
int("5")
# 5

float("2.5")
# 2.5

str(45)
# "45"
```

## Module 3

Logical and comparison operators, conditional statements, loops, and bitwise operations.

### Comparison Operations

**Comparison Operators** are used to check the truthiness between two values.

| Operator | Description                                                                                                 | Example                                                    |
| :------- | :---------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------- |
| \==      | returns if operands' values are equal, and False otherwise                                                  | `x == y # False`<br />`x == z # True`                      |
| !=       | returns True if operands' values are not equal, and False otherwise                                         | `x != y # True`<br />`x != z # False`                      |
| \>       | True if the left operand's value is greater than the right operand's value, and False otherwise             | `x > y # False`<br />`y > z # True`                        |
| <        | True if the left operand's value is less than the right operand's value, and False otherwise                | `x < y # True`<br />`y < z # False`                        |
| \>= (≥)  | True if the left operand's value is greater than or equal to the right operand's value, and False otherwise | `x >= y # False`<br />`x >= z # True`<br />`y >= z # True` |
| <= (≤)   | True if the left operand's value is less than or equal to the right operand's value, and False otherwise    | `x <= y # True`<br />`x <= z # True`<br />`y <= z # False` |

### Conditional Instruction / Conditional Statement

A **Conditional Statement** uses a variable or expression that evaluates to a boolean, then executes the conditional statement body.

- do not mix tab and space indentation
- conditions are nestable, and indentation improves readability
- `if-elif-else` is also known as a **cascade**
- `else` is always the last branch of the cascade
- `else` must precede an `if` statement
- `else` is an optional part of the cascade
- if the `else` branch is in cascade, only one branch executed
- if no `else` branch is possible no branch is executed
  Example Code:

```python
# IF (single)
if this_is_true:
 do_this_if_true()
always_do_this()

# IF-ELSE
if this_is_true:
 do_this_if_true()
else:
 do_this_otherwise()
always_do_this()

# IF-ELIF-ELSE is also known as a cascade
if the_weather_is_good:
 go_for_a_walk()
elif tickets_are_available:
 go_to_the_theater()
elif table_is_available:
 go_for_lunch()
else:
 play_chess_at_home()
always_drink_water()
```

### Loops

**Loops** repeat actions in the **Loop Body**
**Infinite Loops** aka **endless loops**: press **Ctrl-C (or Ctrl-Break)** in the console to cause a **KeyboardInterrupt** and exit an endless loop from continuing.
**`while` loops** repeat indented code in the loop's body, as long as the condition evaluates to `True`. If the condition is `False` the body is not executed at all. The body should be able to change the condition's value to avoid infinite loops.

```python
# Example 1
while True:
print("Stuck in an infinite loop.")

# Example 2
counter = 5
while counter > 2:
print(counter)
counter -= 1
```

**`for` loops** iterate over a collection of data item by item.

```python
# Example 1
word = "Python"
for letter in word:
 print(letter, end="*")
```

```python
# Example 2
for i in range(1, 10):
 if i % 2 == 0:
  print(i)
```

The **`break` keyword** exits the loop immediately and unconditionally ends the loop body operations. The program begins at the next instruction after the loop's body.
The **`continue` keyword** will proceed to the next loop in the sequence and immediately recheck the loop's conditional expression.

---

### Logic Operations and Expressions

**Logical operators** connect conditional statements together forming the basis of computer logic.
**`not` Logical Negations** inverts boolean values, high priority

| A     | not A |
| :---- | :---- |
| False | True  |
| True  | False |

**`and` Logical Conjunction** both must be true, for statement to be true

| A     | B     | A and B |
| :---- | :---- | :------ |
| False | False | False   |
| False | True  | False   |
| True  | False | False   |
| True  | True  | True    |

**`or` Logical Disjunction** one must be true, for statement to be false

| A     | B     | A or B |
| :---- | :---- | :----- |
| False | False | False  |
| False | True  | True   |
| True  | False | True   |
| True  | True  | True   |

### Bitwise Operations

**Bitwise Operators** manipulate single bits of data (must be integers 0/1, no floats)

- `&` (ampersand) bitwise conjunction
- `|` (bar) bitwise disjunction
- `~` (tilde) bitwise negation
- `^` (caret) bitwise exclusive or (xor)

|  A  |  B  | A & B | A \| B | A ^ B |
| :-: | :-: | :---: | :----: | :---: |
|  0  |  0  |   0   |   0    |   0   |
|  0  |  1  |   0   |   1    |   1   |
|  1  |  0  |   0   |   1    |   1   |
|  1  |  1  |   1   |   1    |   0   |

|  A  | ~ A |
| :-: | :-: |
|  0  |  1  |
|  1  |  0  |

**Bitwise operators** to manipulate single bits of data. **Logical operators** do not penetrate into the bit level of its argument.

Python Bitwise Examples:

| Bitwise Operator         |    Bitwise Examples    | In Binary                    |
| :----------------------- | :--------------------: | :--------------------------- |
| Example:                 | `x = 15`<br />`y = 16` | `0000 1111`<br />`0001 0000` |
| `&` bitwise `and`        |      `x & y = 0`       | `0000 0000`                  |
| `\|` bitwise `or`        |     `x \| y = 31`      | `0001 1111`                  |
| `~` bitwise `not`        |      `~ x = 240*`      | `1111 0000`                  |
| `^` bitwise `xor`        |      `x ^ y = 31`      | `0001 1111`                  |
| `>>` bitwise right shift |      `y >> 1 = 8`      | `0000 1000`                  |
| `<<` bitwise left shift  |       `y << 3 =`       | `1000 0000`                  |

### Lists

**Lists** is a type of data that stores multiple objects, it is _an ordered and mutable collection_ of comma-separated items between square brackets. Lists can be indexed and updated.

**List Indexing** is the operation of selecting an element from the list, but any expression can be the index

```python
# create a list
numbers = [10, 5, 7, 2, 1]

# indexing the list
numbers[4]

# indexing the list using an expression
i = 2
numbers[i * 2]
= numbers[4]

# list can be nested
my_list = [1, "a", ["list", 2], False]
```

#### List Operations

The **length of a list** may vary (dynamic entity).
**`len()` function** returns the number of elements currently stored inside the list.
**`del` keyword** removes the given item from the list, (note: cannot access or remove an element that does not exist).

A **Negative Indexing** gets the item starting from the end of the list.

```python
numbers = [0,1,2,3,4,5]
print(numbers[-2])
> 4
```

The **`list.append()` method** adds a new element to the end of the list. ```

```python
numbers = []
for i in range(1,5):
 numbers.append(i)
print(numbers)
> [1, 2, 3, 4]
```

The **`list.insert(location, value)` method** adds a new element at any location in the list, shifting the existing location elements to the right.

```python
numbers = []
for i in range(1,5):
 numbers.insert(0, i)
print(numbers)
> [4, 3, 2, 1]

numbers = []
for i in range(1,5):
 numbers.insert(-1, i)
print(numbers)
> [2, 3, 4, 1]
```

The **`in` keyword** is used to loop through the elements in a list.

```python
my_list = ["hello", "world"]
for i in my_list:
print(i, end="")
> helloworld
```

#### Sorting Lists

The **`list.sort()` method** reorders the elements in non-decreasing order.
The **`list.reverse()` method** reverses the order of the elements in the list.

```python
numbers = []
for i in range(1,5):
 numbers.insert(-2, i)

print(numbers)
> [3, 4, 2, 1]

numbers.sort()
print(numbers)
> [1, 2, 3, 4]

numbers.reverse()
print(numbers)
> [4, 3, 2, 1]
```

#### Processing Lists

Lists differ from ordinary variables because the name of a list references the **name of a memory location where the list is stored**.

```python
list_1 = [1]
list_2 = list_1
list_1[0] = 2
print(list_2)
> [2]
# not 1, because updating list_1,
# updates the single memory location
# that both lists reference
```

A **`list slice`** makes a new copy of a list, or part of a list.

```python
# copies the entire list
list_1 = [1]
list_2 = list_1[:]
list_1[0] = 2
print(list_2)
> [1]

# slice part of a list
# list_slice[start:stop]
list_1 = [10, 8, 6, 4, 2]
list_2 = list_1[1:3]
print(list_2)
> [8, 6]

# negative indices are valid
my_list = [10, 8, 6, 4, 2]
new_list = my_list[2:-1]
print(new_list)
> [6, 4, 2]

# make empty list if start index is negative
my_list = [10, 8, 6, 4, 2]
new_list = my_list[-1:1]
print(new_list)
> []

# excluding start will begin from 0 index
# my_list[:end] => my_list[0:end]
my_list = [10, 8, 6, 4, 2]
new_list = my_list[:3]
print(new_list)
> [10, 8, 6]

# excluding end will end on an index equal to the len of the list
# my_list[start:] => my_list[start:len(my_list)]
my_list = [10, 8, 6, 4, 2]
new_list = my_list[3:]
print(new_list)
> [4, 2]
```

Use the **`del` keyword** to delete a slice from a list:

```python
# note: this does not produce any new list
my_list = [10, 8, 6, 4, 2]
del my_list[1:3]
print(my_list)
> [10, 4, 2]

# delete all the elements inside the list
my_list = [10, 8, 6, 4, 2]
del my_list[:]
print(my_list)
> []

# or delete the list entirely
del my_list
print(my_list)
> NameError: name 'my_list' is not defined
```

The **`in` and `not in` keywords** are able to determine if a value is store inside a list or not.

```python
my_list = [0, 3, 12, 8, 2]
print(5 in my_list)
> False
print(5 not in my_list)
> True
print(12 in my_list)
> True
```

#### List Comprehension & Multidimensional Arrays

**List Comprehension** is used to create list data on-the-fly during program execution (is not described statically).

```python
# shorthand list comprehensive
list = [expression for element in list if conditional]

# if equivalent to
for element in list:
 if conditional:
  expression

twos = [2 ** i for i in range(8)]
print(twos)
> [1, 2, 4, 8, 16, 32, 64, 128]

odds = [x for x in squares if x % 2 != 0 ]
print(odds)
> [1, 9, 25, 49, 81]
```

**Multi-Dimensional Arrays** are equivalent to _a matrix in mathematics_:

```python
row = []
for x in range(8):
 for y in range(8):
  row.append(y)

# make a chessboard
board = [[i for i in range(8)] for j in range(8)]
print(board)
> [[0, 1, 2, 3, 4, 5, 6, 7],
   [0, 1, 2, 3, 4, 5, 6, 7],
   [0, 1, 2, 3, 4, 5, 6, 7],
   [0, 1, 2, 3, 4, 5, 6, 7],
   [0, 1, 2, 3, 4, 5, 6, 7],
   [0, 1, 2, 3, 4, 5, 6, 7],
   [0, 1, 2, 3, 4, 5, 6, 7],
   [0, 1, 2, 3, 4, 5, 6, 7]]
```

---

## Module 4

Functions, tuples, dictionaries, and data processing.

### Functions

A **Function** is a block of code that performs a specific task when the function is called _(invoked)_. Use functions to make your code reusable, better organized, and more readable; _The DRY Principle_ Don't Repeat Yourself.

- functions can **have parameters**
- function may **return values** or **cause an effect**
- functions are invoked by passing **arguments** between the parenthesis after the function_name()
- positional arguments
- keyword arguments

**Decomposition / Decomposing Code** is the process of dividing the source code (or problem) into well-isolated pieces, each encoded into a function form; Decomposition allows us to share the work and the responsibility among many developers.

**Define** the function using the `def` _keyword_, followed by the indented function body.

```python
def my_function(): # define a function
 print("Do stuff...") # function body
```

#### Functions come from

- Python built-in functions
- Python modules
- custom coded functions
- (functions connected with _classes_)

---

#### Function Invocation

When **Invoking** a function:

1. Python recalls the function by its name from memory and _jumps_ into the function body
2. the body of the function is then _executed_
3. the end of the function returns to the place
   Example Call:

```python
# define function
def message():
 print("Message")

# function returns None by default
# do stuff
print("Start)

# invoke the message() function
message()
> Message

# after function executes
# returns to this next line
print("Stop)

> Start
> Message
> Stop
```

#### Function Parameters and Argument Passing

**Parameterized Functions** declare parameter variables in the function parenthesis

- **function parameters** live _inside functions_, and can be only be defined between the pair of parentheses in the `def` statement
- **function arguments** exist _outside functions_, and carry the value passed to corresponding function parameters
- You must provide as many arguments as there are defined parameters, _unless the function parameter has a default value declared_

#### Example Parameterized Functions

```python
# define a function
def my_function(a, b, c):
 # function body
 print(a, b, c)

# function invocation
my_function(1, 2, 3)

# a more practical example
def hello(name):
 print("Hello", name, "!")

# pass an argument the the "name" parameter
username = input("Enter your name:")
hello(username)
```

**Positional Parameter Passing**:

```python
def introduction(first_name, last_name):
 print("Hello, my name is", first_name, last_name)

introduction("Jessie", "Owens")
> Hello, my name is Jessie Owens

introduction("James", "Bond", "007")
> TypeError: introduction() takes 2 positional arguments but 3 were given
```

**Keyword Argument Passing**:

```python
def introduction(first_name, last_name):
 print("Hello, my name is", first_name, last_name)

introduction(first_name = "James", last_name = "Bond")
> Hello, my name is James Bond

introduction(last_name = "Skywalker", first_name = "Luke")
> Hello, my name is Luke Skywalker

introduction(surname="Skywalker", first_name="Luke")
> TypeError: unexpected keyword argument 'surname'
```

Defining **Default (Predefined) Values**:

```python
def introduction(first_name, last_name="Trump"):
 print("Hello, my name is", first_name, last_name)

introduction("Donald")
introduction(first_name="Donald")
> Hello, my name is Donald Trump
```

**Note:** _positional arguments_ must not follow _keyword arguments_.

```python
def subtract(a, b):
 print(a - b)

subtract(5, b=2)
> 3

subtract(a=5, 2)
> Syntax Error
```

#### `return` the Results of a Function

Functions can home some kind of effect (printing text to the console), but functions also can `return` a value using the `return` keyword in two variants:

1. `return` **without an expression** _causes the immediate termination of execution_
2. `return` **with an expression** causes the immediate termination of the function's execution AND will _evaluate the expression's value and return the result_
   Example Function `return`:

```python
def boring_function():
 return 123

x = boring_function()
print("The boring_function has returned the value:", x)
> The boring_function has returned the value: 123
```

#### The `None` Keyword

There are only two kinds of circumstances when None can be safely used:

```python
# 1. assigning it to a variable (or return it as a function's result)
value = None
value = nothing_but_func() = None

# 2. comparing it with a variable to diagnose an internal state
if value is None:
 print("Sorry, you don't carry any value")
> Sorry, you don't carry any value
```

Functions implicitly return `None` if it doesn't return a value using a `return` expression.

```python
def strange_function(n):
 if(n % 2 == 0):
  return True

output = strange_function(1)
print(output)
> None

output = strange_function(2)
print(output)
> True
```

#### Exercises Using Functions

##### Calculate the number of days in a given year

```python
# return T/F if it is a leap year
def is_year_leap(year):
 if year % 400 == 0:
  return True
 elif year % 100 == 0:
  return False
 elif year % 4 == 0:
  return True
 else:
  return False

# return number of days in a given year, month
def days_in_month(year, month):
 if month in [1,3,5,7,8,10,12]:
  return 31
 elif month in [9,4,6,11]:
  return 30
 elif month == 2:
  if is_year_leap(year):
   return 29
  else:
   return 28

# calculate the number of days in a year, month, day
def day_of_year(year, month, day):
 count = 0
 for i in range(1, month+1):
  count += days_in_month(year, i)
 return count

# Testing
print(day_of_year(2000, 12, 31))
> 366
```

##### Calculate all the Prime Numbers between 2 and any number

```python
# calculate if a value is prime
def is_prime(num):
 for i in range(2, num):
  if num % i == 0:
   return False
 return True

# loop a range & print all prime numbers
for i in range(1, 20):
 if is_prime(i + 1):
  print(i + 1, end=" ")
 print()

> 2 3 5 7 11 13 17 19
```

#### Functions and Scopes

The **Scope** of a name (e.g., a variable name) is part of the code where the name is properly recognizable.
**Function Scope Example 1:** A variable that exists outside a function has a scope inside the function body.

```python
# example 1
var = 2
def multiply_by_var(x):
 return x * var

print(multiply_by_var(7))
> 14
```

**Function Scope Example 2 & 3:** unless the function defines a variable of the same name.

```python
# example 2
def multiply(x):
 var = 5
 return x * var

print(multiply(7))
> 35

# example 3
def multiply(x):
 var = 7
 return x * var

var = 3
print(multiply(7))
> 49
```

**Function Scope Example 4:** A variable that exists inside a function has a scope inside the function body.

```python
# example 4
def adding(x):
 var = 7
 return x + var

print(adding(4))
print(var)
> 11
> NameError
```

**Function Scope Example 5:** Use the **`global`** keyword followed by a variable name to make the variable's scope global.

```python
# example 5
var = 2
print(var)
> 2

def return_var():
 global var
 var = 5
 return var

print(return_var())
print(var)
> 5
> 5
```

#### Exercises Using Function Scopes

##### Converting BMI in Metric/Imperial Units

```python
def ft_and_inch_to_m(ft, inch = 0.0):
 return ft * 0.3048 + inch * 0.0254

def lb_to_kg(lb):
 return lb * 0.45359237

def bmi(weight, height):
 if height < 1.0 or height > 2.5 or weight < 20 or weight > 200
  return None
 return weight / height ** 2

print(bmi(52.5, 1.65))
> 19.283746556473833

print( bmi( weight=lb_to_kg(176), height=ft_and_inch_to_m(5, 7) ) )
> 27.565214082533313
```

##### Making Functions More Pythonic

```python
# The sum of any two sides of a triangle
# must be greater than the third side.

# long-form (inefficient)
def is_a_triangle(a, b, c):
 if a + b <= c:
  return False
 if b + c <= a:
  return False
 if c + a <= b:
  return False
 return True

# shortened (better...)
def is_a_triangle(a, b, c):
 if a + b <= c or b + c <= a or c + a <= b:
  return False
 return True

# condensed (now that's Pythonic!)
def is_a_triangle(a, b, c):
 return a + b > c and b + c > a and c + a > b

# testing
print(is_a_triangle(1, 1, 1))
> True
print(is_a_triangle(1, 1, 3))
> False

# checking for right triangles
def is_a_right_triangle(a, b, c):
 if not is_a_triangle(a, b, c):
  return False
 if c > a and c > b:
  return c ** 2 == a ** 2 + b ** 2
 if a > b and a > c:
  return a ** 2 == b ** 2 + c ** 2

# testing
print(is_a_right_triangle(5, 3, 4))
> True
print(is_a_right_triangle(1, 3, 4))
> False
```

##### Finding a `Factorial!`

```python
def factorial_function(n):
 if n < 0:
  return None
 if n < 2:
  return 1
 product = 1
 for i in range(2, n + 1):
  product *= i
  return product

# testing
for n in range(1, 6):
print(n, factorial_function(n))

> 1 1
> 2 2
> 3 6
> 4 24
> 5 120
```

##### `Factorial!` Function Implemented Recursively

```python
def factorial(n):
if n == 1:
# base case (termination condition)
return 1
else:
# recursive function invocation
return n * factorial(n - 1)
##### The Fibonacci Sequence
def fib(n):
if n < 1:
return None
if n < 3:
return 1

elem_1 = elem_2 = 1
the_sum = 0
# pay attention to the var movements in loop
for i in range(3, n + 1):
the_sum = elem_1 + elem_2
elem_1, elem_2 = elem_2, the_sum
return the_sum

# testing
for n in range(1, 10):
 print(n, "->", fib(n))

> 1 -> 1
> 2 -> 1
> 3 -> 2
> 4 -> 3
> 5 -> 5
> 6 -> 8
> 7 -> 13
> 8 -> 21
> 9 -> 34
```

---

### Tuples

**Tuples** are ordered and unchangeable (immutable) collections of data.
**Sequence Types** may store one or more values (or be empty) and are browsed/scanned element by element (sequentially) using a `for` loop.
**Mutability** is a property of data that _describes its ability to change during program execution_.
Python has two kinds of data: **mutable** and **immutable** data.
**Mutable data** can be freely updated at any time or _In Situ_ (in Latin translates literally _in position_).

```python
# ALLOWED, lists are mutable data types
list.append(1) # container of items
```

**Immutable data** cannot be modified during program execution

```python
# NOT ALLOWED, tuples are immutable sequence types

tuple.append(1) # AttributeError: 'tuple' object has no attribute 'append'
# sequence of items cannot be changed at execution
```

**Tuples** are _Immutable Sequence Types_ where each element may be a different type, including literals and variables.

```python
tuple_1 = (1, 2, 4, 8)
tuple_2 = 1., .5, .25, .125
empty_tuple = ()
one_element_tuple_a = (1, )
one_element_tuple_b = 1.,

list = [1, 2, 3]
a_tuple = tuple(list)
print(a_tuple)
> (1, 2, 3)
```

**Index a tuple** to access its values.

```python
my_tuple = (1, 2.0, "string", [3, 4], (5, ), True)
print(my_tuple[3]) # outputs: [3, 4]

# tuple items cannot be deleted or changed
my_tuple = (1, 2.0, "string", [3, 4], (5, ), True)
my_tuple[2] = "guitar" # TypeError exception

# but tuples can be deleted entirely
del my_tuple
```

Use the **`tuple.count()`** method to count the number of times a specified element occurs in a tuple.

```python
tup = 1, 2, 3, 2, 4, 5, 6, 2, 7, 2, 8, 9
duplicates = tup.count(2)
print(duplicates)
> 4
```

---

### Dictionaries

A **Dictionary** is a _mutable data structure_ defined by a set of **key-value pairs** using a pair of curly braces `{}`.
**Dictionaries** are _not a sequence_ and each key must be unique.
**Dictionaries are not Lists**: Dicts hold _pairs of values_ compared to Lists which contain a _set of numbered values_.

#### Creating a Dictionary

```python
# dict instantiation
empty_dictionary = {}
empty_dictionary = dict()
dictionary = {
 "horse": "caballo",
 "cat": "gato",
 "dog": "perro"
}
phone_numbers = dict('boss': 0987654321, 'Suzy': 1234567890)

# example
words = ['cat', 'lion', 'horse']
for word in words:
 if word in dictionary:
  print(word, "->", dictionary[word])
 else:
  print(word, "is not in dictionary")

# output
> cat -> gato
> lion is not in dictionary
> horse -> caballo
```

#### Sorting a Dictionary (or List)

The **`sorted()` function** sorts dictionaries

```python
dictionary = {"cat": "gato", "dog": "perro", "horse": "caballo"}
for key in sorted(dictionary.keys()):
 print(key, "->", dictionary[key])

> cat -> gato
> dog -> perro
> horse -> caballo
```

#### Accessing Dictionary Values

The **`dict.get()`** method will return the value of the given dictionary key-name.

```python
dictionary = {"cat": "gato", "dog": "perro", "horse": "caballo"}
print(dictionary.get("horse"))
> caballo
```

Use **`dict.keys()`** to access values by _referencing a certain key by its name_:

```python
dictionary = {"cat": "gato", "dog": "perro", "horse": "caballo"}
for key in dictionary.keys():
 print(key, "->", dictionary[key])
> horse -> caballo
> cat -> gato
> dog -> perro
```

The **`dict.values()`** method works similarly to .keys(), but _returns values_.

```python
dictionary = {"cat": "gato", "dog": "perro", "horse": "caballo"}
for spanish in dictionary.values():
 print(spanish)

> gato
> perro
> caballo
```

The **`dict.items()`** method returns each key-value pair as a tuple.

```python
dictionary = {"cat": "gato", "dog": "perro", "horse": "caballo"}
for english, spanish in dictionary.items():
 print(english, "->", spanish)

> cat -> gato
> dog -> perro
> horse -> caballo
```

#### Modifying & Adding Dictionary Items

Adding/Inserting a dictionary item by declaring its **`dict[key] = value`**

```python
span_eng = {"cat": "gato", "dog": "perro", "horse": "caballo"}
# update a dict key-value
span_eng['cat'] = 'león'

# adding non-existent key
span_eng['swan'] = 'cisne'
```

Use the **`dict.update()`** method to insert/update items in a dictionary:

```python
span_eng = {"flor": "flower"}
span_eng.update({"suelo": "soil"})
print(span_eng)
> {"flor": "flower", "suelo": "soil"}
```

The **`dict.popitem()`** method will remove and return the last item in a dictionary:

```python
span_eng = {"flor": "flower", "suelo": "soil"}
last_item = span_eng.popitem()
print(last_item)
> {"suelo": "soil"}

print(span_eng)
> {"flor": "flower"}
```

Use the **`del`** keyword to delete a specific dictionary item or the **`dict.clear()`** method to _remove all dictionary items_.

```python
dictionary = {"cat": "gato", "dog": "perro", "horse": "caballo"}
del dictionary["cat"]
print(dictionary)
> {"dog": "perro", "horse": "caballo"}

dictionary.clear()
print(dictionary)
> {}
```

The **`dict()` function** will convert a list or tuple to a dictionary:

```python
# a tuple of tuples
colors = (("green", "#008000"), ("blue", "#0000FF"))
# a list of tuples
colors = [("green", "#008000"), ("blue", "#0000FF")]
# convert to `dict()`
colors_dictionary = dict(colors)
print(colors_dictionary)
> {'green': '#008000', 'blue': '#0000FF'}
```

---

### Errors and The `exception` Keyword

Errors arise when:

- when code is fed bad data
- _you_ write bad code with mistakes causing "bug"

It is better to beg for forgiveness than to ask for permission... In Python it is _better to handle an error when it happens than to try to avoid it_.

```python
try:
 # run this block first, forgive later
 value = int(input('Enter a natural number: '))
 print('The reciprocal of', value, 'is', 1/value)
except ValueError:
 # catch value error
 print('I do not know what to do.')
except ZeroDivisionError:
 # catch operational error
 print('Division by zero is not allowed.')
except:
 # catch default error
 print('Something strange has happen... Sorry!')
```

Or you can consolidate exception handling using a `tuple`

```python
try:
 value = int(input('Enter a natural number: '))
 print('The reciprocal of', value, 'is', 1/value)
except (ValueError, ZeroDivisionError):
 # catch value or operational error
 print('I cannot use that value.')
except:
 # catch default error
 print('Something strange has happened... Sorry!')
```

#### Useful Exceptions

**ZeroDivisionError** occurs because you cannot divide any value by `0`.

```python
n / 0 -> ZeroDivisionError
n // 0 -> ZeroDivisionError
n % 0 -> ZeroDivisionError
```

**ValueError** arises when dealing with values that are not allowed in come context

```python
# each of these have their own ways of handling values
string()
int()
float()
list()
dict()
tuple()
```

**TypeError** arises when applying data whose type cannot be accepted in the current context

```python
short_list = [1]
one_value = short_list[0.5]
> TypeError: cannot use float as the list index
```

**AttributeError** arises when activating a method that does not exist on the item you are dealing with

```python
short_list = [1]
short_list.append(2)
short_list.depend(3)
AttributeError: 'list' has no attribute 'depend'

short_tup = (1,)
short_tup.append(2)
AttributeError: 'tuple' has no attribute 'append'
```

**SyntaxError** arises when the interpreter reaches a line of code that violates the Python language grammar/syntax

```python
x = 92
if x > 90
print("You got an 'A'!")
> error, line #
> if x > 90:
> ^
> SyntaxError: expected ':'
```

---

#### Testing for Exceptions

Every novelist needs an editor and _each programmer needs a tester_. Since Python is an **interpreted** language, the source code is parsed and executed at the same time. Consequentially, the program may not reach a block of code with an error.

**Print Debugging** sometimes called **Interactive Debugging** because it requires a developer to interact with the program to find the bug. Other forms of debugging involve pragmatically running your functions through systematic tests that automate the testing process to a degree.

#### Debugging Tips

1. Try to tell someone
   - explain what your code is expected to do and how it actually behaves
   - be concrete and answer any questions the listener has
   - you'll likely realize the cause of the problem telling your story
2. Try to _isolate the problem_
   - extract the part of the code that seems to be throwing an error
   - comment out parts of the code that obscure the problem
   - assign concrete values instead of reading from an `input()`
   - test functions using predictable argument values
   - analyze the code, read it aloud
3. _Analyze all the changes you introduce into your code_, in particular, if a bug appears that didn't show up earlier
4. Taking a break\*, taking walks, and drinking coffee helps the blood flow
5. Being optimistic\*, solving problems equals brain power over time, patience and persistence are great skills to build

#### Unit Testing

**Unit Testing** is about testing the software and how the code itself is written

> Writing/running tests are inseparable parts of the code and preparing the test data is an inseparable part of coding.

We will go into Unit Testing more deeply in the Associate and Professional Certification Modules!

---

### Additional Notes

#### Python Built-in Functions

```python
print("", sep="", end="\n")
max(10, 50, 33)  # 50
min(2, -5, 10)   # -5
range(start=0, stop=100, step=1)

# [0,1,2,...98,99]
numbers = [0, 1, 2]
len(numbers)     # 3
numbers[] = 3
len(numbers)     # 4
```

#### Priority of Operations

| Priority | Operator                                                             | Description                                       |
| :------- | :------------------------------------------------------------------- | :------------------------------------------------ |
| 0        | `()`                                                                 | Parentheses                                       |
| 1        | `f(args…)`                                                           | Function call                                     |
| 2        | `(expressions…), [expressions…], {expressions…}`<br/>`{key: value…}` | Displaying Sequences<br>Dictionaries              |
| 3        | `x[index], x[index:index], x(arguments), x.attribute`                | Indexing, slicing, calling, attribute referencing |
| 4        | `await x`                                                            | Await expression                                  |
| 5        | `**`                                                                 | Exponent                                          |
| 6        | `+x, –x, ~x`                                                         | (unary) Positive, Negative, Bitwise NOT           |
| 7        | `*, /, //, %`                                                        | Multiplication, Division, Remainder               |
| 8        | `+, –`                                                               | (binary)Addition, subtraction                     |
| 9        | `<<, >>`                                                             | Bitwise left and right shifts                     |
| 10       | `&`                                                                  | Bitwise AND                                       |
| 11       | `^`                                                                  | Bitwise XOR                                       |
| 12       | `\|`                                                                 | Bitwise OR                                        |
| 13       | `in, not in, is, is not, <, >,<=, >=, !=, ==, <>`                    | Comparisons, identity, and membership operators   |
| 14       | `not`                                                                | Boolean NOT                                       |
| 15       | `and`                                                                | Boolean AND                                       |
| 16       | `or`                                                                 | Boolean OR                                        |
| 17       | `if-else`                                                            | Conditional Expression                            |
| 18       | `lambda`                                                             | Lambda expression                                 |
