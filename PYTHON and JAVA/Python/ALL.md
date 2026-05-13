## 1. Key Characteristics

What sets Python apart from languages like C++ or Java?

- **Interpreted:** Python code is executed line-by-line. This makes debugging easier but generally means it runs slower than compiled languages.
    
- **Dynamically Typed:** You don't need to declare variable types (like `int` or `string`). Python figures it out at runtime.
    
- **Batteries Included:** Python comes with a massive standard library that supports everything from file I/O to web servers right out of the box.

|**Method**|**Syntax Style**|**Python Version**|**Performance**|
|---|---|---|---|
|**f-strings**|`f"Val: {x}"`|3.6+|**Fastest**|
|**.format()**|`"Val: {}".format(x)`|2.6+|Medium|
|**% Operator**|`"Val: %s" % x`|Legacy|Fast|
|**Concatenation**|`"Val: " + str(x)`|All|Slowest|

## Built-in Data Types

In programming, data type is an important concept.

Variables can store data of different types, and different types can do different things.

Python has the following data types built-in by default, in these categories:

|   |   |
|---|---|
|Text Type:|`str`|
|Numeric Types:|`int`, `float`, `complex`|
|Sequence Types:|`list`, `tuple`, `range`|
|Mapping Type:|`dict`|
|Set Types:|`set`, `frozenset`|
|Boolean Type:|`bool`|
|Binary Types:|`bytes`, `bytearray`, `memoryview`|
|None Type:|`NoneType`|

| Example                                      | Data Type  | Try it |
| -------------------------------------------- | ---------- | ------ |
| x = "Hello World"                            | str        |        |
| x = 20                                       | int        |        |
| x = 20.5                                     | float      |        |
| x = 1j                                       | complex    |        |
| x = ["apple", "banana", "cherry"]            | list       |        |
| x = ("apple", "banana", "cherry")            | tuple      |        |
| x = range(6)                                 | range      |        |
| x = {"name" : "John", "age" : 36}            | dict       |        |
| x = {"apple", "banana", "cherry"}            | set        |        |
| x = frozenset({"apple", "banana", "cherry"}) | frozenset  |        |
| x = True                                     | bool       |        |
| x = b"Hello"                                 | bytes      |        |
| x = bytearray(5)                             | bytearray  |        |
| x = memoryview(bytes(5))                     | memoryview |        |
| x = None                                     | NoneType   |        |

| Code | Result          | Try it |
| ---- | --------------- | ------ |
| \'   | Single Quote    |        |
| \\   | Backslash       |        |
| \n   | New Line        |        |
| \r   | Carriage Return |        |
| \t   | Tab             |        |
| \b   | Backspace       |        |
| \f   | Form Feed       |        |
| \ooo | Octal value     |        |
| \xhh | Hex value       |        |
## Arithmetic Operators

Arithmetic operators are used with numeric values to perform common mathematical operations:

| Operator | Name           | Example | Try it |
| -------- | -------------- | ------- | ------ |
| +        | Addition       | x + y   |        |
| -        | Subtraction    | x - y   |        |
| *        | Multiplication | x * y   |        |
| /        | Division       | x / y   |        |
| %        | Modulus        | x % y   |        |
| **       | Exponentiation | x ** y  |        |
| //       | Floor division | x // y  |        |

| perator | Name                 | Description                                                                                             | Example | Try it |
| ------- | -------------------- | ------------------------------------------------------------------------------------------------------- | ------- | ------ |
| &       | AND                  | Sets each bit to 1 if both bits are 1                                                                   | x & y   |        |
| \|      | OR                   | Sets each bit to 1 if one of two bits is 1                                                              | x \| y  |        |
| ^       | XOR                  | Sets each bit to 1 if only one of two bits is 1                                                         | x ^ y   |        |
| ~       | NOT                  | Inverts all the bits                                                                                    | ~x      |        |
| <<      | Zero fill left shift | Shift left by pushing zeros in from the right and let the leftmost bits fall off                        | x << 2  |        |
| >>      | Signed right shift   | Shift right by pushing copies of the leftmost bit in from the left, and let the rightmost bits fall off | x >> 2  |        |

## 1. Built-in Functions

These are the "out-of-the-box" functions that are always available in Python. You don't need to import any libraries or define them yourself.

- **Examples:** `print()`, `len()`, `type()`, `range()`, and `input()`.
    
- **Use Case:** Performing common, foundational tasks instantly.
    

## 2. User-Defined Functions (UDFs)

These are functions you create yourself using the `def` keyword to perform a specific task that isn't covered by built-in options.

Python

```
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
```

- **Key Components:** The function name, parameters (optional), and the `return` statement.
    
- **Benefit:** They make your code modular, readable, and reusable.
    

## 3. Lambda Functions (Anonymous Functions)

Sometimes you need a quick, one-line function but don't want to go through the trouble of a formal definition. These are defined using the `lambda` keyword.

- **Syntax:** `lambda arguments : expression`
    
- **Example:** `add = lambda x, y : x + y`
    
- **Limitation:** They can only contain a single expression and are typically used as arguments for higher-order functions like `map()` or `filter()`.
    

## 4. Recursive Functions

A recursive function is a function that calls itself within its own definition. This is a powerful tool for tasks that can be broken down into smaller, identical sub-problems.

- **Classic Example:** Calculating a factorial.
    
- **Rule of Thumb:** Every recursive function **must** have a "base case" to prevent it from running forever and causing a stack overflow.
    

Python

```
def factorial(n):
    if n == 1: # Base case
        return 1
    else:
        return n * factorial(n-1)
```





Regular Expressions (commonly known as **regex**) are powerful patterns used to match, search, and manipulate text. In Python, you access regex through the built-in `re` module.

---

## 1. The Core Functions

To use regex, you must first `import re`. Here are the four most common functions you'll use:

|**Function**|**Purpose**|
|---|---|
|**`re.search()`**|Scans a string for a match and returns a Match object (first occurrence only).|
|**`re.findall()`**|Returns a list containing all matches found in the string.|
|**`re.sub()`**|Replaces one or many matches with a specific string.|
|**`re.split()`**|Splits the string into a list at every match.|

---

## 2. Basic Syntax & Meta-characters

Regex uses special characters to define patterns rather than looking for literal text.

- **`.` (Dot):** Matches any single character except a newline.
    
- **`^` / `$`:** Matches the **start** or the **end** of a string.
    
- **`*` / `+` / `?`:** Quantifiers (Zero or more / One or more / Zero or one).
    
- **`\d` / `\w` / `\s`:** Matches a **digit**, **word character** (letters/numbers/underscore), or **whitespace**.
    
- **`[]` (Character Set):** Matches any character inside the brackets (e.g., `[a-z]` for lowercase letters).
    

---

## 3. Practical Examples

### A. Searching for a Pattern

Python

```
import re

text = "The price is 42 dollars"
match = re.search(r"\d+", text) # Looking for one or more digits

if match:
    print(f"Found: {match.group()}") # Output: 42
```

_Note: The `r` before the string marks it as a **raw string**, which prevents Python from misinterpreting backslashes (like `\n`)._

### B. Finding All Occurrences

Python

```
text = "Contact us at support@example.com or sales@biz.org"
emails = re.findall(r"[\w\.-]+@[\w\.-]+", text)

print(emails) 
# Output: ['support@example.com', 'sales@biz.org']
```

### C. Replacing Text

Python

```
text = "The rain in Spain"
# Replace all spaces with underscores
new_text = re.sub(r"\s", "_", text)

print(new_text) # Output: The_rain_in_Spain
```

---

## 4. Compiled Objects for Performance

If you plan to use the same regex pattern multiple times throughout your code, it is more efficient to **compile** it into a pattern object.

Python

```
pattern = re.compile(r"ID-\d{4}")

# Now use the object to perform operations
print(pattern.findall("My IDs are ID-1024 and ID-9982"))
```

---

## 5. Summary Table of Special Sequences

|**Sequence**|**Matches**|
|---|---|
|`\D`|Anything **but** a digit|
|`\W`|Anything **but** a word character (symbols, etc.)|
|`\b`|A word boundary (the space between a word and a symbol)|
|`( )`|**Groups:** Allows you to extract specific parts of a match|

Are you trying to validate a specific type of input (like an email or phone number), or are you scraping data from a larger text file?



| **Context**                             | **Public (name)**          | **Private (__age)**                                     |
| --------------------------------------- | -------------------------- | ------------------------------------------------------- |
| **Inside the same class**               | Accessible via `self.name` | Accessible via `self.__age`                             |
| **Outside the class** (e.g., `p1.name`) | **Allowed**                | **Error** (`AttributeError`)                            |
| **In a Child Class** (Inheritance)      | **Allowed**                | **Error** (Child cannot see parent's private variables) |




Python uses **Exceptions** to handle errors that occur during the execution of a program. Instead of the program crashing, you "catch" the error and decide how to respond.

---

## 1. Exception Handling (The `try-except` Block)

The core of exception handling is the `try` block. You place the code that _might_ fail inside `try`, and the code to handle the error inside `except`.

Python

```
try:
    # Code that might raise an error
    result = 10 / 0
except ZeroDivisionError:
    # Code that runs if the specific error occurs
    print("Error: You cannot divide by zero!")
```

---

## 2. The `except` Clause

You can have multiple `except` blocks to handle different types of errors, or a "catch-all" block. You can also capture the error message using the `as` keyword.

Python

```
try:
    number = int(input("Enter a number: "))
    result = 10 / number
except ValueError:
    print("Invalid input! Please enter an integer.")
except ZeroDivisionError as e:
    print(f"Mathematical error: {e}")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

---

## 3. The `try-finally` Clause

The `finally` block is the "clean-up" crew. It **always** runs, regardless of whether an exception was raised or caught. This is crucial for closing files or releasing system resources.

Python

```
try:
    file = open("example.txt", "r")
    content = file.read()
    print(content)
except FileNotFoundError:
    print("The file was not found.")
finally:
    # This runs even if the file wasn't found or if an error occurred during reading
    print("Cleaning up: Closing resources.")
    # In a real scenario, you'd check if 'file' exists before closing
```

---

## 4. User-Defined Exceptions

Sometimes, built-in errors (like `ValueError`) aren't specific enough for your logic. You can create your own exception by creating a new **class** that inherits from the built-in `Exception` class.

### Step-by-Step implementation:

1. **Define** the class inheriting from `Exception`.
    
2. **Raise** it using the `raise` keyword when a specific condition is met.
    

Python

```
# 1. Define the custom exception
class AgeRestrictionError(Exception):
    """Exception raised for errors in the input age."""
    def __init__(self, age, message="Age must be 18 or older to enter."):
        self.age = age
        self.message = message
        super().__init__(self.message)

# 2. Use the custom exception
def check_entry(age):
    if age < 18:
        raise AgeRestrictionError(age)
    else:
        print("Access granted.")

try:
    check_entry(16)
except AgeRestrictionError as e:
    print(f"Access Denied: {e.message} (User age: {e.age})")
```

---

### Summary Table

| **Clause**    | **Purpose**                                               |
| ------------- | --------------------------------------------------------- |
| **`try`**     | Wraps the code that might cause an issue.                 |
| **`except`**  | Executes only if an error occurs in the try block.        |
| **`else`**    | Executes only if **no** errors occurred in the try block. |
| **`finally`** | Executes no matter what (used for cleanup).               |
| **`raise`**   | Manually triggers an exception.                           |