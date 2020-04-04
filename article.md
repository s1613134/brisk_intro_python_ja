# Brisk introduction to Python
This is an introduction designed for those of us who already know a dynamic programming language fairly well. MATLAB and the R language are examples of dynamic programming languages.

## How to read this page
Read this page in one shot from beginning to end. We go through all the basic Python data types, stopping from time to time to talk about relevant features of the Python language.

While you are reading, I suggest you open an IPython console, and type or copy / paste the code fragments, to run them. To copy / paste, click the >>> symbol at the right of each code cell to remove the leading characters and output, before selecting the cell contents.

By the end of the page you should have an idea of the Python landscape to orient you, as you start to learn the language.

## Numbers
There are two types of numbers in Python: integer and floating point. In Python, an integer is an object of type int, and a float is an object of type float.

```
>>> a = 99
>>> type(a)
<class 'int'>
>>> b = 99.0
>>> type(b)
<class 'float'>
```

You can create ints and floats by using int and float like this:

```
>>> float('1')
1.0
>>> float(1)
1.0
>>> int('1')
1
>>> int(1)
1
```

+, -, * or / on a mix of floats and ints, give floats:

```
>>> a + b
198.0
>>> a * b
9801.0
```

Dividing an int by an int also gives a float — but this is only true by default for Python >= 3 (see [1]):

```
>>> 1 / 2
0.5
```

If you only want the integer part of the division, use //

```
>>> 1 // 2
0
>>> 1.0 // 2.0
0.0
```

Python has built-in function called round:

```
>>> round(5.0 / 2.0)
2
```

The % operator on numbers gives you the remainder of integer division (also known as the modulus):

```
>>> 5 % 2
1
>>> 5.0 % 2.0
1.0
```

##True and False
True and False are special objects in Python. They are of type bool (for Boolean).

```
>>> type(True)
<class 'bool'>
>>> type(False)
<class 'bool'>
>>> True == False
False
>>> True == True
True
>>> False == False
True
```

You can use the logical operators and, or and not to express logic about Boolean values:

```
>>> True and True
True
>>> True and False
False
>>> True or False
True
>>> False or False
False
>>> not True
False
>>> True and not False
True
```

## None
None is also a special object in Python. By convention, Python often uses None to mean that no valid value resulted from an operation, or to signal that we don’t have a value for a parameter.

```
>>> type(None)
<class 'NoneType'>
```

Unlike most other values in Python, the default display output from None, is nothing:

```
>>> None
```

## Equals
As for MATLAB and R, = is for assignment, == is for testing equality.

```
>>> a = 1
>>> a
1
>>> a == 1
True
```

Like R, Python uses != for testing that objects are not equal. This is different from MATLAB, which uses ~=:

```
>>> a != 1
False
```

## “If” statements, blocks and indention
A conditional statement in Python looks like this:

```
>>> my_var = 10
>>> if my_var == 10:
...     print("The conditional is True!")
...     print("my_var does equal 10")
...
The conditional is True!
my_var does equal 10
```

The first line of the conditional statement, that contains the conditional test, ends in a colon. Call this the if test. There follow some lines indented relative to the if test. Call these indented lines the if block. Python executes the statements in the if block only when the if test evaluates to True. For example, in this case, the if test evaluates to False, and the block does not execute:

```
>>> my_var = 11
>>> # This time the conditional evaluates to False
>>> if my_var == 10:  # the "if test"
...     # The indented lines are the "if block"
...     print("The conditional is True!")
...     print("my_var does equal 10")
...
```

The first line that returns to the same level of indentation as the if test line, closes the if block.

Unless the if block has a further indented block (for example, another if block), then all the lines in the block must have the same indentation.

See note [2] for equivalent if statements in R and MATLAB.

The if block may be followed by another block where the conditional is else:. This block will only run if the initial conditional test evaluates to False.

```
>>> my_var = 11
>>> if my_var == 10:
...     print("The conditional is True!")
...     print("my_var does equal 10")
... else:
...     print("The conditional is False!")
...     print("my_var does not equal 10")
...
The conditional is False!
my_var does not equal 10
```

There may be other conditional tests, with associated conditional blocks. These tests use the contraction elif conditional_test, where elif is a contraction for else if:

```
>>> my_var = 12
>>> if my_var == 10:
...     print("The conditional is True!")
...     print("my_var does equal 10")
... elif my_var == 11:
...     print("The second conditional is True!")
...     print("my_var does equal 11")
... elif my_var == 12:
...     print("The third conditional is True!")
...     print("my_var does equal 12")
... else:
...     print("All conditionals are False!")
...     print("my_var does not equal 10, 11 or 12")
...
The third conditional is True!
my_var does equal 12
```
