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

## “While” statements
while statements are another example with an initial test followed by an indented block. Here’s an example where we find the largest Fibonacci number less than 1000:

```
>>> last_but_1 = 0
>>> fibonacci = 1
>>> while fibonacci < 1000:
...     last_but_2 = last_but_1
...     last_but_1 = fibonacci
...     fibonacci = last_but_2 + last_but_1
...
>>> print("Largest Fibonacci < 1000 is", last_but_1)
Largest Fibonacci < 1000 is 987
```

Notice the initial while test: while fibonacci < 1000:, followed by the indented while block. Unlike the if statement, Python will continue to run the statements in the while block until the conditional in the while test evaluates to False.

## Lists
Make a list like this:

```
>>> my_list = [9, 4, 7, 0, 8]
>>> my_list
[9, 4, 7, 0, 8]
>>> type(my_list)
<class 'list'>
```

A list element can be any type of object, including another list:

```
>>> mixed_list = [9, 3.0, True, my_list]
>>> mixed_list
[9, 3.0, True, [9, 4, 7, 0, 8]]
>>> type(mixed_list)
<class 'list'>
```

A Python list is like a cell array in MATLAB, or a list in R.

### “for” loops and iteration
We can iterate over a list. To iterate, means to fetch one element after another from some container, such as a list. We can use a for loop to iterate over a list:

```
>>> for e in my_list:
...     print(e)
...
9
4
7
0
8
```

The for loop has the same form as if statements and while loops, with a first line ending in a colon, followed by an indented block.

The first line in the for loop is of form: for loop_variable in container:. The container is the container from which we will fetch the elements. At each iteration of the for loop, Python gets a new element from the container to put into the loop variable. For each element in the container, Python executes the for block.

Note [3] shows equivalent for loops in Python, R and MATLAB.

See Range for a common way of writing a for loop that iterates over a sequence of integers.

### Lists are sequences
A sequence is a category of Python objects that have a defined element order, have a length, are iterable, can be indexed with integers, and sliced (see below). If object s is a sequence, then:

- s has a length that can be found with len(s);
- we can iterate over the elements in s with for element in s: # do something with element;
- we can return the element at position n with s[n];
- we can get another sequence by slicing s. For example, s[0:n] will give a new sequence containing the first n elements of s.

```
>>> # Has a length
>>> len(my_list)
5
```

```
>>> # Is iterable
>>> for e in my_list:
...     print(e)
9
4
7
0
8
```

```
>>> # Can be indexed
>>> my_list[1]
4
>>> # Can be sliced
>>> my_list[0:2]
[9, 4]
```

### Python indices are 0-based
Indices for Python sequences start at 0. For Python, the first element is at index 0, the second element is at index 1, and so on:

```
>>> my_list[0]
9
>>> my_list[1]
4
```

### Negative indices
Negative numbers as indices count back from the end of the list. For example, use index -1 to return the last element in the list:

```
>>> my_list
[9, 4, 7, 0, 8]
>>> my_list[-1]
8
```

The -1 index above is therefore equivalent to:

```
>>> my_list[len(my_list) - 1]
8
```

Here is the third from last element:

```
>>> my_list[-3]
7
```

### Every Python variable is a pointer
In Python, variable names point to the memory location of an object. Therefore, Python variables can be called pointers.

If you are running standard Python, you can see the memory location that a variable points to with the id() function. The following will give some long integer giving the memory location on your computer:

```
>>> id(my_list) 
4467820488
```

When you do another_variable = a_variable, you are telling the name another_variable to point to the same object as the name a_variable. The variable therefore points to the same memory location:

```
>>> another_list = my_list
>>> another_list
[9, 4, 7, 0, 8]
>>> id(another_list) # doctest: +SKIP
4467820488
>>> id(another_list) == id(my_list)
True
```

### Lists are mutable
A list is a mutable object. Mutable means, that we can change the elements in the list, without creating a new list.

```
>>> my_list[1] = 99
>>> my_list
[9, 99, 7, 0, 8]
```

Because lists are mutable, you need to keep in mind that Every Python variable is a pointer:

```
>>> another_list = my_list
>>> another_list
[9, 99, 7, 0, 8]
>>> id(another_list) == id(my_list)
True
```

Because my_list points to the same object as another_list, when you modify (the object pointed to by) my_list, we also modify the value of another_list, because my_list and another_list point at the same list:

```
>>> my_list[1] = 101
>>> another_list
[9, 101, 7, 0, 8]
```

### Adding lists
Adding two lists with + returns a new list that is the concatenation of the two lists:

```
>>> new_list = my_list + [False, 1, 2]
>>> new_list
[9, 101, 7, 0, 8, False, 1, 2]
```

### Appending and removing elements
You can append elements with the append method.

A method is a function attached to the object. See Functions for more on functions in Python.

We can see that append is a method by displaying the value of my_list.append:

```
>>> my_list.append
<built-in method append of list object at 0x...>
```

To call the method, we add parentheses, surrounding any arguments we want to pass into the method. In this case we want to pass in the element to append:

```
>>> my_list.append(20)
>>> my_list
[9, 101, 7, 0, 8, 20]
```

Note that the append method does not return the list, it just changes the list in-place. Python returns None from the append method:

```
>>> result = my_list.append(42)
>>> result == None
True
```

This is also true for some other methods that modify the list in-place, such as the sort method:

```
>>> new_list = [10, 1, 3]
>>> result = new_list.sort()
>>> # Return value is None
>>> result == None
True
>>> # But the original list now in ascending order from sort
>>> new_list
[1, 3, 10]
```

You can remove elements from the list with the pop method:

```
>>> # Remove and return the last element of the list
>>> my_list.pop()
42
>>> my_list
[9, 101, 7, 0, 8, 20]
>>> # Remove and return the third element of the list
>>> my_list.pop(2)
7
>>> my_list
[9, 101, 0, 8, 20]
```

### Slicing
You can return slices from any sequence, including lists, by putting a slice specifier in square brackets. For example, this returns the first 3 elements of the list:

```
>>> my_list[0:3]
[9, 101, 0]
The first number after the square bracket and before the colon is the start index. In this case we start at the first element (element at index 0). The second number, after the colon, is the stop index. This is the end index plus one. So we return elements at index 0, 1 and 2. That is, elements up to, but not including 3.
```

If you omit the first number (the start index) Python assumes 0:

```
>>> my_list[:3]
[9, 101, 0]
```

If you omit the second number, Python assumes the length of the list as the stop index.

```
>>> my_list[2:]
[0, 8, 20]
>>> my_list[2:len(my_list)]
[0, 8, 20]
```

You can omit both numbers, in which case you return all the elements of the list. This can be useful if you want to make a new list that contains the same elements as the first:

```
>>> another_list = my_list[:]
>>> another_list
[9, 101, 0, 8, 20]
```

Because this is a new list object, you can change the original list without changing the new list:

```
>>> my_list[1] = 999
>>> another_list
[9, 101, 0, 8, 20]
```

You can also specify a second colon, and a third number. This third number is the step size. For example, to get every second element of the list:

```
>>> my_list[0:len(my_list):2]
[9, 0, 20]
>>> # Length of list assumed as stop index if omitted
>>> my_list[0::2]
[9, 0, 20]
```

You can use negative numbers for the start and stop indices. As for indexing, negative start and stop values count back from the end of the list:

```
>>> my_list
[9, 999, 0, 8, 20]
>>> my_list[-4:-2]
[999, 0]
```

Negative numbers for the step count backwards from the start to the stop index:

```
>>> my_list[4:1:-1]
[20, 8, 0]
```

If you have a negative step size, and you don’t specify the start index, then the start index defaults to the last element in the list. If you don’t specify the stop index, it defaults to one prior to index 0:

```
>>> my_list
[9, 999, 0, 8, 20]
>>> my_list[-1:1:-1]
[20, 8, 0]
>>> my_list[:1:-1]
[20, 8, 0]
>>> my_list[-2::-1]
[8, 0, 999, 9]
```

One consequence that is worth remembering is that the following idiom gives you a reversed copy of the list:

```
>>> my_list[::-1]
[20, 8, 0, 999, 9]
```

## Tuples
Tuples are almost the same as lists, except they are not mutable. That is, you cannot change the elements of a tuple, or change the number of elements.

```
>>> my_tuple = (9, 4, 7, 0, 8)
>>> my_tuple
(9, 4, 7, 0, 8)
```

```
>>> my_tuple[1] = 99
Traceback (most recent call last):
   ...
TypeError: 'tuple' object does not support item assignment
```

```
>>> # This raises an AttributeError, because tuples have no append method
>>> my_tuple.append(20)
Traceback (most recent call last):
   ...
AttributeError: 'tuple' object has no attribute 'append'
```

Here’s an empty tuple:

```
>>> empty_tuple = ()
>>> empty_tuple
()
```

A tuple with two elements:

```
>>> two_tuple = (1, 5)
>>> two_tuple
(1, 5)
```

There is a little complication when making a tuple with one element:

```
>>> not_a_tuple = (1)
>>> not_a_tuple
1
```

This is because Python can’t tell that you meant this to be a tuple, rather than an expression with parentheses round it:

```
>>> not_a_tuple = (1 + 5 + 3)
>>> not_a_tuple
9
```

To tell Python that you mean this to be a length-one tuple, add a comma after the element, and before the closing parenthesis:

```
>>> one_tuple = (1,)
>>> one_tuple
(1,)
```
