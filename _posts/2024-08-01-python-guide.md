---
layout: post
tags: [work]
---

# Python Guide

## Bookmarks

- Python Docs
  - [Tutorial](https://docs.python.org/3/tutorial/index.html)
  - [Built-in Functions](https://docs.python.org/3/library/functions.html)
- W3Schools
  - [Tutorial](https://www.w3schools.com/python/)
  - [Exercises](https://www.w3schools.com/python/exercise.asp)
  - [Glossary](https://www.w3schools.com/python/python_ref_glossary.asp)
- Setup & Styling
  - [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python) for text editor and extension setup
  - [PEP8 Style guide](https://peps.python.org/pep-0008/) for formatting code
  - [Black Formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter)
- Package Management
  - [Python Package Index (`PyPI`)](https://pypi.org/) for finding non-standard library packages
  - [Preferred Installer Program(`pip`)](https://pypi.org/project/pip/) for installing packages

## Standard

### Functions

The Python interpreter has a number of functions and types built into it that are always available. They are listed [here](https://docs.python.org/3/library/functions.html) in alphabetical order.

Some commonly used beginner functions are:

- Data types: `bool()`, `dict()`, `float()`, `int()`, `list()`, `str()`, `tuple()`
- Data analysis: `abs()`, `max()`, `min()`, `range()`
- Data validation: `all()`, `any()`, `id()`, `len()`, **`print()`**, `type()`

#### Returns

A [return statement](https://www.geeksforgeeks.org/python-return-statement/) is used to end the execution of the function call and “returns” the result (value of the expression following the return keyword) to the caller. The statements after the return statements are not executed. If the return statement is without any expression, then the special value None is returned.

A return statement always returns one value. This means that if you concatenate return values, they will be aggregated into a collection of some sort, and you will need to index that return value for the specific value you need in another function of test.

### Comments & Docstrings

- Use `#` for in-line comments:
- Use (3) apostrophes before and after block comments:

``` py
# in-line comment
'''
block comment
'''
```

Write [docstrings](https://peps.python.org/pep-0008/#documentation-strings) for all public modules, functions, classes, and methods.

A docstring is a string literal that occurs as the first statement in a module, function, class, or method definition. Such a docstring becomes the __doc__ special attribute of that object.

All modules should normally have docstrings, and all functions and classes exported by a module should also have docstrings. Public methods (including the __init__ constructor) should also have docstrings. A package may be documented in the module docstring of the __init__.py file in the package directory.

``` py
def sample_function():
    """Return a value of 5.""" # This is a docstring
    return 5
```

### Variables

#### Guidelines

- A variable name must start with a letter or the underscore character
- A variable name cannot start with a number
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )
- Variable names are case-sensitive (age, Age and AGE are three different variables)
- A variable name cannot be any of the [Python keywords](https://www.w3schools.com/python/python_ref_keywords.asp).

#### How To

- Declared as `var = value`
- Can be cast to specific data type as `var = type(value)`
- Type of variable can also be retrieved with `print(type(var))`
- Global variables can be used (and set) inside or outside of functions
    - They can be set outside of a function the same way a normal function is declared
    - They can be set inside of a function using the `global` keyword (`global x`)

### Data Types

#### Reference Table

Variables can store data of different types, and different types can do different things. Python has the following data types built-in by default, in these categories:

| Type | Examples |
| - | - |
| Text | `str` |
| Numeric | `int`, `float`, `complex` | 
| Sequence | `list`, `tuple`, `range` | 
| Mapping | `dict` | 
| Set | `set`, `frozenset` | 
| Boolean | `bool` | 
| Binary Types | `bytes`, `bytearray`, `memoryview` |
| None | `NoneType` |

#### Identification & Casting

The built-in `type()` function can be used to identify data types of values: `print(type(x))`.

In Python, the data type is set when you assign a value to a variable, but you can further specify the data type using constructor functions (this is referred to as casting):

``` py
a = 4 # type of z is integer by default
b = int(4.5) # value of a is cast/specified as integer, and it will print/return without the decimal point
```

#### Numbers

- Int, or integer, is a whole number, positive or negative, without decimals, of unlimited length.
- Float, or "floating point number" is a number, positive or negative, containing one or more decimals.
    - Float can also be scientific numbers with an "e" to indicate the power of 10.
- Complex numbers deal with imaginary numbers and are not really relevant to most users.

``` py
a = 1 # int
b = -3255522 # int
c = -35.59 # float
d = 12E4 # float
```

##### Random

Python does not have a `random()` function to make a random number, but Python has a built-in module called `random` that can be used to make random numbers:

``` py
import random
print(random.randrange(1, 10)) 
```

#### Strings

Strings in python are surrounded by either single quotation marks, or double quotation marks. You can use quotes inside a string, as long as they don't match the quotes surrounding the string. You can assign a multiline string to a variable by using three quotes (again, single or double).

You can display a string literal with the `print()` function.

``` py
a = "Hello"
b = 'world'
c = "Hello 'world'"
d = """Hello
world"""
e = " " # this is just an empty space
print(a + e + b + e + c + e + d)
> Hello World Hello 'world' Hello
> world
```

##### Arrays & Slicing

Like many other popular programming languages, strings in Python are arrays of bytes representing unicode characters. However, Python does not have a character data type, a single character is simply a string with a length of 1. Square brackets can be used to access elements of the string.

``` py
a = "Hello, World!"
print(a[1])
> e
```

> Note: Indexes start at `[0]` for the first character.

You can return a range of characters by using the slice syntax. There are various ways to use this method:
- Specify the start index and the end index, separated by a colon, to return a part of the string: `print(x[1:5])`
- By leaving out the start index, the range will start at the first character: `print(x[:5])`
- By leaving out the end index, the range will go to the end: `print(x[1:])`
- Use negative indexes to start the slice from the end of the string: `print(x[-5:-1])`

``` py
x = "Hello world"
print(x[1:5]) # start and end indices
> ello
print(x[:5]) # start at first index (0) and go to index 5
> Hello
print(x[1:]) # start at 1 and go to last index
> ello world
print(x[-5:-1]) # start 5 indexes from the last character and return up to the second-to-last index
> worl
```

##### Looping

Since strings are arrays, we can loop through the characters in a string, with a `for` loop.

``` py
for x in "hat":
  print(x)
> h
> a
> t
```

##### Checks

To check if a certain phrase or character is present in a string, we can use the keyword `in` or an `if` statement. Conversely, the keyword `not in` and an alternative `if` statement can be used to check if a value if NOT present.

``` py
# Using `in` to check for present value
txt = "The best things in life are free!"
print("free" in txt)
> True
# Using `if` to check for present value
txt = "The best things in life are free!"
if "free" in txt:
  print("Yes, 'free' is present.")
> Yes, 'free' is present.
# Using `not in` to check for non-present value
txt = "The best things in life are free!"
print("dog" not in txt)
> True
# Using `if` to check for non-present value
txt = "The best things in life are free!"
if "expensive" not in txt:
  print("No, 'expensive' is NOT present.")
> No, 'expensive' is NOT present.
```

##### Modify

There are several built-in methods for modifying strings.

- `capitalize()`: Convert the first character of a string to uppercase
- `lower()`: Converts all uppercase characters in a string into lowercase
- `replace()`: replace with another string
- `split()`: returns a list of substrings, separated by common separator (ex. commas)
- `strip()`: remove whitespace
- `upper()`: Converts all lowercase characters in a string into uppercase

##### Combine/Concatenate

You can concatenate (or combine) strings using the `+` operator, and you can space them out using whitespace inside of strings (`" "`)

``` py
a = "Hello"
b = "World"
c = a + " " + b
```

##### Format

Formatted string literals (aka F-strings) let you include the value of Python expressions inside a string by prefixing the string with `f` or `F` and writing expressions as {expression}.

``` py
price = 59
txt = f"The price is {price} dollars"
> The price is 59 dollars
txt = f"The price is {price:.2f} dollars"
> The price is 59.00 dollars
txt = f"The price is {price:.2f} dollars"
The price is 1180 dollars
```

##### Escape

To insert characters that are illegal in a string, use an escape character. An escape character is a backslash `\` followed by the character you want to insert.

> Some escape sequences must be terminated, specifically when using single and double quotes to add illegal strings. Terminate with an additional backslash at the end of the string, before closing quotes."

``` py
txt = "We are the so-called \"Vikings\" from the north."
> We are the so-called "Vikings" from the north."
```

| Character | Output |
| - | - |
| `\'` | Single Quote |
| `\"` | Double Quote |
| `\\` | Backslash |
| `\n` | New Line |
| `\r` | Carriage Return |
| `\t` | Tab |
| `\b` | Backspace |
| `\f` | Form Feed |
| `\ooo` | Octal value |
| `\xhh` | Hex value |

##### Built-in Methods

There are various built-in methods for strings. All methods return a new value rather than modifying the string.

See [full list here](https://docs.python.org/3/library/stdtypes.html#string-methods).

#### Booleans

Boolean values express whether an expression is true or false. This in fundamental to Python, programming, and machine code, and it relates back to binary notation (`0` and `1`). 

You can evaluate any expression in Python, and get one of two answers: `True` or `False`. Common examples of this occuring are within comparisons (ex. greater than, less than) and conditions (ex. `if`, `while`).

The `bool()` function allows you to evaluate any value, and give you `True` or `False` in return. Almost any value is evaluated to `True` if it has some sort of content:
- Any number is `True`, except `0`.
- Any string is `True`, except empty strings (`""`).
- Any `list`, `tuple`, `set`, and `dictionary` are `True`, except empty ones.

There are not many values that evaluate to `False`, except empty values, such as `()`, `[]`, `{}`, `""`, the number `0`, `None`, and `False`.

``` py
a = 9
b = 10
c = ""
# Operator comparisons
print(a > b)
> False
print(a < b) 
> True
# Conditional comparisons
if b > a:
    print(b is greater than a)
else:
    print(b is not greater than a)
> b is greater than a
# Boolean evaluation
print(bool(a))
> True
print(bool(b))
> True
print(bool(c))
> False
```

You can use functions to `return` boolean values, and then use those values as conditions in other functions. This extends to built-in functions (ex. `isinstance()`) or functions or external libraries.

``` py
def myFunction() :
  return True

if myFunction():
  print("YES!")
else:
  print("NO!")

x = 200
print(isinstance(x, int))
> True
```

### Operators

Operators are used to perform operations on variables and values. [W3Schools](https://www.w3schools.com/python/python_operators.asp) does a good job of breaking down how these operators can be used, as the official [Python docs](https://docs.python.org/3/reference/lexical_analysis.html#operators) are pretty brief. The following are commonly used operators and some applications for them.

Arithmetic operators perform common mathematical operations:

```
+       -       *       **      /       //      %
```

Assignment operators (aka delimiters) are used to assign values to variables, often based on underlying mathemtical operations. A common usage of these is iterating a value up or down based on a condition (`if {condition}: x += 1`, which adds `1` to the value of `x` if the statement is `True`).

```
=       +=      -=      *=      **=      /=      //=
%=      &=      |=      ^=      >>=     <<=      :=
```

Comparison operators compare values:

```
==      !=      <       >       <=      >=      
```

Logical operators combine conditional statements:

```
and     or     not
```

Identity operators compare objects based on memory addresses. This is different than equality comparison as it's evaluating whether the values are stored in the same address (`=`) and not just whether the values evaluate similarly (`==`).

```
is      is not
```

There are many other operators and many different ways in which they can be used. Refer to the documentation links above, and try to find real examples of how they can be used elsewhere to learn more.

### Collections & Arrays

Of the built-in data types available in Python, there are 4 that store collections of data: `dictionary`, `list`, `set`, and `tuple`. The usage and function of these data types differ, and each has its own advantages, capabilities, and guidelines:

1. `Dictionary` is a collection which is ordered and changeable. *No duplicate members (keys).*
    - Stored inside `{}`
2. `List` is a collection which is ordered and changeable. Allows duplicate members.
    - Stored inside `[]`
3. `Set` is a collection which is *unordered* and *unchangeable* (can add/remove, as needed). *No duplicate members.*
    - Stored inside `{}`
4. `Tuple` is a collection which is ordered and *unchangeable*. Allows duplicate members.
    - Stored inside `()`

> Python does not have built-in support for Arrays, but [`lists` can be used instead](https://www.w3schools.com/python/python_arrays.asp).

> Ordered types can be referred to using indices because the order of items within the data type is fixed.

> Dictionaries are considered ordered as of Python 3.7, though there is still no dedicated method for index querying/manipulation.

#### Dictionaries

[Dictionaries](https://www.w3schools.com/python/python_dictionaries.asp) are written using curly brackets: `{}`. They are used to store data values in `key:value` pairs inside of "items".

Dictionary items are accessed via key and value references, either directly or through supplemental functions. This can be done in several ways:

- Items (key/value pairs)
  - `items()` function
- Keys
  - Direct reference
  - `keys()` function
  - `get()` function to access values via keys
- Values
  - `values()` function

Looping through dictionaries is often required when parsing [JSON](https://www.json.org/json-en.html) responses from API calls. You can loop through a dictionary by using a `for` loop. [Nested dictionaries](https://www.w3schools.com/python/python_dictionaries_nested.asp) are not detailed below, but beginners should consider delving into these constructs to handle more complex queries, when ready.

``` py
# Create a dictionary and set key/value pairs
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964,
  "year": 2020
}
print(thisdict)
> {'brand': 'Ford', 'model': 'Mustang', 'year': 2020} # Newest duplicate entry overwrote older entry

# Access items
x = thisdict.items()
> dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 2020)]) # returned as Tuples

# Access keys
y1 = thisdict["model"]
> Mustang
y2 = thisdict.get("model")
> Mustang
y3 = thisdict.keys()
> dict_keys(['brand', 'model', 'year'])

# Access values
z = thisdict.values()
> dict_values(['Ford', 'Mustang', 2020])

# Looping
thisdict = {}
for x in thisdict:
  print(x)  # Returns all KEYS as unique responses (due to the iteration occuring)
> brand
> model
> year

for x in thisdict:
  print(thisdict[x]) # Returns all VALUES as unique responses (due to the iteration occuring)
> Ford
> Mustang
> 2020
``` 

#### Lists

[Lists](https://www.w3schools.com/python/python_lists.asp) are created using square brackets: `[]`. They can contain different data types.

> While normally considered to be an ordered, indexable data type, there are some methods that can change the order of lists, though these can be considered edge cases for the purpose of learning about them.

There are several functions for access, changing, sorting, copying, joining, adding to, and removing from lists. See [W3Schools](https://www.w3schools.com/python/python_lists.asp) for details.

Similar to dictionaries, you can [loop through lists](https://www.w3schools.com/python/python_lists_loop.asp) using `for` and `while` statements. One unique advantage to lists is the native index methods that can be used to add additional conditions for loops, such as `len()` and `range()`:

``` py
thislist = ["apple", "banana", "cherry"]
for i in range(len(thislist)): # The iterable created is [0, 1, 2]
  print(thislist[i])
> apple # thislist[0]
> banana # thislist[1]
> cherry # thislist[2]
i = 0
while i < len(thislist):
  print(thislist[i])
  i = i + 1
> apple # thislist[0]
> banana # thislist[1]
> cherry # thislist[2]
```

List comprehension can be used to shorten expressions related to list queries and modifications. The example below contrasts the syntax between standard syntax and list comprehansion, but it can be combined with various [list methods](https://www.w3schools.com/python/python_lists_methods.asp), as well.

``` py
# Standard syntax
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = []

for x in fruits:
  if "a" in x:
    newlist.append(x)

print(newlist) 

# List comprehension
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]

newlist = [x for x in fruits if "a" in x]

print(newlist) 
```

#### Sets

[Sets](https://www.w3schools.com/python/python_sets.asp) are written with curly brackets:`{}`. Once a set is created, you cannot change its items, but you can remove items and add new items. In addition to now allowing duplicate values, `True` and `1` are evaluated as duplicate, as well as `False` and `0`.

The same looping mechanics apply to sets as dictionaries and lists, minus the index capabilities. The `for` loop is the best way to loop through them.

``` py
thisset = {"apple", "banana", "cherry"}

for x in thisset:
  print(x)
> apple
> banana
> cherry
```

Sets can be joined using various methods described [here](https://www.w3schools.com/python/python_sets_join.asp).

#### Tuples

[Tuples](https://www.w3schools.com/python/python_tuples.asp) are written with round brackets:`()`. While they are ordered and indexable, they cannot be changed.

Tuples must contain commas; otherwise they will just be recognized as the data type being stored inside the parenthesis. So for a Tuple with a single value, it would look like `thistuple = (value1,)`.

Tuples can store any data type, and they can store multiple data types at once. When values are assigned, this is referred to as "packing", and when values are extracted, this is referred to as "unpacking. If the number of variables is less than the number of values, you can add an * to the variable name and the values will be assigned to the variable as a list.

``` py
fruits = ("apple", "banana", "cherry", "dog", "cat") # values are packed into Tuple called `fruits`
(green, yellow, *red) = fruits # values are extracted/unpacked into variables

print(green) # `green` variable was assigned to `apple` value
print(yellow)
print(red) # the asterisk assigns any remaining values to this variable as a list
> apple
> banana
> ['cherry', 'dog', 'cat']
```

Looping can be accomplished in the same manner as lists, with the ability reference indices via the `len()` and `range()` functions as part of `for` and `while` loops.

### Conditions & Loops

[Conditional statements](https://www.w3schools.com/python/python_conditions.asp) (aka [compound statements](https://docs.python.org/3/reference/compound_stmts.html) or loops) contain (groups of) other statements; they affect or control the execution of those other statements in some way.

The `if`, `while`, and `for` statements are commonly used to loop, iterate, and/or repeat through expressions based on certain conditions.

Python supports the usual logical conditions from mathematics:

- Equals: `a == b`
- Not Equals: `a != b`
- Less than: `a < b`
- Less than or equal to: `a <= b`
- Greater than: `a > b`
- Greater than or equal to: `a >= b`

#### If/Elif/Else

An "if statement" is written by using the `if` keyword and setting a condition using operators (ex. `==`, `>`, `or`, etc.). You can have `if` statements inside `if` statements (this is called nested `if` statements). The `elif` and `else` keywords are used to provide alternative actions if the initial condition does not evaluate to `True`.

- The `elif` keyword is Python's way of saying "if the previous conditions were not true, then try this condition".
- The `else` keyword catches anything which isn't caught by the preceding conditions.
- The `and` keyword is a logical operator, and is used to combine conditional statements.
- The `or` keyword is a logical operator, and is used to combine conditional statements.
- The `not` keyword is a logical operator, and is used to reverse the result of the conditional statement.
- The `pass` statement can be used inside of an `if` statement with no other content to prevent throwing an error following evaluation.

``` py
a = 1
b = 2
c = 3

if a > b:
    print("a is greater than b")
    if a > b and a > c:
        print("a is greater than b AND c")
elif a == b or a == c:
    print("a is equal to b OR c")
elif a < b or a < c:
    print ("a is less than b OR c")
else:
    print("a does not meet any of the expected conditions")
    pass
```

#### While

The `while` loop is used to execute statements as long as a condition is `True`. The `break`, `continue` and `else` statements are used to control the flow of the loop based on additional or alternative conditions.

``` py
i = 0
while i < 6:
  i += 1
  print(i)
  if i == 1:
    print("i is equal to 1")
    continue
  elif i < 6:
    print("i is less than 6")
  else:
    print("i is no longer less than 6")
    break
```

#### For

A `for` loop is used for iterating over a sequence of items inside of a `list`, a `tuple`, a `dictionary`, a `set`, or a `string` and executing a set of statements for each item. The `break`, `continue` and `else` statements are used to control the flow of the loop based on additional or alternative conditions. The `for` loop does not require an indexing variable to set beforehand.

``` py
fruits = ["apple", "banana", "cherry", "dog"]
for x in fruits:
  print(x)
  if x == "apple":
    print("Yum")
    continue
  elif x == "banana":
    print("Yum!")
    continue
  else:
    print("Gross!")
    break
```

### Functions

A function is a block of code which only runs when it is called. You can pass data, known as parameters, into a function. A function can return data as a result.

A function must be defined and called in order to execute:

``` py
def my_function(): # definition
  print("Hello world")

my_function() # call
```

To let a function return a value, use the `return` statement. This value can then be used by other functions.

``` py
def my_function(x):
  return 5 * x

print(my_function(3))
> 15
```

#### Parameters & Arguments

Information can be passed into functions as arguments. Arguments are specified after the function name, inside the parentheses. You can add as many arguments as you want, just separate them with a comma. By default, a function must be called with the correct number of arguments. Meaning that if your function expects 2 arguments, you have to call the function with 2 arguments, not more, and not less. 

The terms parameter and argument can be used for the same thing: information that are passed into a function. From a function's perspective:

- A parameter is the variable listed inside the parentheses in the function definition.
- An argument is the value that is sent to the function when it is called.

Arbitrary arguments (`*args`) can be used if you do not know how many arguments will be passed into your function. This way the function will receive a `tuple` of arguments, and can access the items accordingly.

``` py
def my_function(*kids):
  print("The youngest child is " + kids[2])

my_function("Emil", "Tobias", "Linus") 
> The youngest child is Linus
```

Keyword arguments can be sent with the `key = value` syntax so that the order of arguments no longer matters. Arbitrary keyword arguments (`**kwargs`) can be passed if you do not know how many keyword arguments will be passed in your function. This way the function will receive a `dictionary` of arguments, and can access the items accordingly.

``` py
def my_children(child3, child2, child1):
  print("The youngest child is " + child3)

my_children(child1 = "Emil", child2 = "Tobias", child3 = "Linus") # Keyword arguments passed
> The youngest child is Linus

def my_function(**kid): # Arbitrary keyword argument
  print("His last name is " + kid["lname"])

my_function(fname = "Tobias", lname = "Refsnes")
```

### Classes & Methods

Python is an object oriented programming language. Almost everything in Python is an `object`, with its properties and methods. A `Class` is like an object constructor, or a "blueprint" for creating objects. Objects can also contain methods. Methods in objects are functions that belong to the object.

All classes have a function called `__init__()`, which is always executed when the class is being initiated. Use the `__init__()` function to assign values to object properties, or other operations that are necessary to do when the object is being created

The `self` parameter is a reference to the current instance of the class, and is used to access variables that belongs to the class. It does not have to be named `self` , you can call it whatever you like, but it has to be the first parameter of any function in the class.

``` py
class MyClass: # Create class
  x = "Jane"
  y = 25

p1 = MyClass() # Create object (p1) using class

class Person: # Create class with function
  def __init__(self, name, age):
    self.name = name
    self.age = age

  def myfunc(self): # Method created within class
    print(self.name + " is the oldest.")

p2 = Person("John", 36)

print(p1.x, p1.y)
print(p2.name, p2.age)
p2.myfunc() # Method executed on p2 object
```

#### Inheritance

[TODO](https://www.w3schools.com/python/python_inheritance.asp)

### Error & Exceptions

[TODO](https://docs.python.org/3/tutorial/errors.html)

[TODO](https://www.w3schools.com/python/gloss_python_error_handling.asp)

[TODO](https://www.w3schools.com/python/python_ref_exceptions.asp)

## Advanced

### Modules

While many capabilities exist within the Python standard library, there are also [built-in](https://docs.python.org/3/py-modindex.html) and [external](https://pypi.org/) [modules](https://docs.python.org/3/installing/index.html#) that can simplify, extend, and deepen the capabilities of Python.

- A `module` or `library` is a file containing a set of functions that can be imported into a Python script.
- A `package` is a collection of modules/files inside a common namespace that must be installed on the environment running Python.
- The [preferred installer program](https://pypi.org/project/pip/) (pip) is used to install packages.
- The [Python Package Index](https://pypi.org/) (PyPI) is a public repository of open source licensed packages made available for use by other Python users.

To create a module, just save the code you want in a file with the file extension `.py`. The `import` statement is used to reference the module file and leverage its functionality. You can create an alias when you import a module, by using the `as` keyword:

``` py
# Stored as mymodule.py (module name is mymodule)
def greeting(name):
  print("Hello, " + name) 

# Stored as main.py
import mymodule as mm # Module import and alias

mm.greeting("Jonathan")
> Hello, Jonathan
```

_**Note:** You can also import parts of a module using the `from` keyword (ex. `from {module} import {object}`) to reduce dependencies and help with performance._

#### Requests

[TODO](https://requests.readthedocs.io/en/latest/)

### Virtual Environments

[TODO](https://docs.python.org/3/library/venv.html)

### Tests

The most fundamental use of the `assert` statement in Pytest is to check if a condition is `True`. If the condition is `False`, Pytest raises an [`AssertionError` exception](https://www.w3schools.com/python/python_ref_exceptions.asp). The `assert` statement works with a wide range of Python objects and expressions.

Beyond simple assert statements, some more advanced use cases can be applied to PyTest:

1. Validate exceptions raised
1. Check truthiness and falsiness of an expression
1. Compare collections
1. Test strings
1. Floating point comparisons

``` py
# math_operations.py

def add(a, b):
    return a + b

# test_math_operations.py

from math_operations import add

def test_add():
    assert add(2, 3) == 5

# $ pytest test_math_operations.py
# > [100%] 1 passed
```

#### Anatomy of a Test

The [PyTest documentation](https://docs.pytest.org/en/stable/explanation/anatomy.html) breaks tests down into 4 parts:

1. Arrange
    - This is the setup to run a test.
    - This can mean preparing objects, starting/killing services, entering records into a database, or even things like defining a URL to query, generating some credentials for a user that doesn’t exist yet, or just waiting for some process to finish.
2. Act
    - This is the action that kicks off the behavior we want to test.
    - This typically takes the form of a function/method call.
3. Assert
    - Review the result of a test and evaluate whether it operated as expected.
    - The `assert` in our test is where we take that measurement/observation and apply our judgement to it. If something should be green, we’d say `assert thing == "green"`.
4. Cleanup
    - The test picks up after itself, so other tests aren’t being accidentally influenced by it.

#### Test-Driven Development

Test-Driven Development (TDD) is a way to develop software that relies on writing code tests before writing any actual code. This strategy aims at focusing the development on very specific functionalities.

TDD involves the following steps:

1. Write a Test: Start by writing a test for the new functionality.
1. Run the Test: Run the test, expecting it to fail since the functionality isn't implemented yet.
1. Write Code: Write the minimal amount of code required to pass the test.
1. Run Tests Again: Run tests to see if the new code passes.
1. Refactor: Clean up the code, maintaining its functionality.
1. Repeat: Continue this cycle for each new piece of functionality.

In TDD, the Red-Green Refactor cycle is a repetitive process consisting of three main steps:

1. Red: Write a failing test (the test fails because the functionality it tests does not exist yet).
1. Green: Write the minimal amount of code necessary to make the test pass.
1. Refactoring: Refine the code without changing its functionality.

### Parsing

[TODO](https://www.w3schools.com/python/gloss_python_json_parse.asp)

### Web Frameworks

[TODO](https://wiki.python.org/moin/WebFrameworks)

### Enhancement Proposals

[PEP](https://peps.python.org/pep-0001/) stands for Python Enhancement Proposal. A PEP is a design document providing information to the Python community, or describing a new feature for Python or its processes or environment. The PEP should provide a concise technical specification of the feature and a rationale for the feature.

There are 2 PEPs I've found particularly useful as a beginner:

- [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
    - Guidance on how Python code should be written, formatted, and presented. This can be largely handled through a VS Code extension like `black` or `auto-pep8`.
- [PEP 257 – Docstring Conventions](https://peps.python.org/pep-0257/)
    - Guidance on what Docstrings are and how/when to use them.