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

