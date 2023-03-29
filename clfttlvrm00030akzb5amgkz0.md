---
title: "Understanding data types in Python."
datePublished: Wed Mar 29 2023 15:07:09 GMT+0000 (Coordinated Universal Time)
cuid: clfttlvrm00030akzb5amgkz0
slug: understanding-data-types-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/lzh3hPtJz9c/upload/8217be49ddb1c45852e7c50b9e20d422.jpeg
tags: python, web-development, python3, coding, python-beginner

---

Variables in Python belong to a data type. A data type is a classification that shows which value a variable has. It ensures that correct operations are done to the variable without causing errors.

Data types in python fall into two categories: primitive and non-primitive types.

**Primitive data types**

Primitive data types contain simple values of data and are building blocks. They are:

* Integer

* Float

* String

* Boolean

Let’s look into each and their properties.

**Integer**

An integer is numerical data type that represents a whole number, both negative and positive.

```python

num = 6

print(type(num))

```

```

<class 'int'>

```

We can do arithmetic operations to them.

```python

x = -6

y = 5

print( "-6 + 5 is" , x + y )#addition

print( "-6 - 5 is" ,x - y )#subtraction

print( "-6 *5 is" ,x* y )#multiplication

print( "-6 / 5 is" ,x / y )#division

print( "-6 % 5 is" ,x % y )#modulus

```

```

-6 + 5 is -1

-6 - 5 is -11

-6 * 5 is -30

-6 / 5 is -1.2

-6 % 5 is 4

```

**Float**

A float is a numeric data type used to represent decimal numbers.

```python

num = 6.0

print(type(num))

```

```

<class 'float'>

```

We can also do arithmetic operations, just like the integers.

```python

x = -6.0

y = 5

print( "-6 + 5 is" , x + y )#addition

print( "-6 - 5 is" ,x - y )#subtraction

print( "-6 *5 is" ,x* y )#multiplication

print( "-6 / 5 is" ,x / y )#division

print( "-6 % 5 is" ,x % y )#modulus

```

```

-6 + 5 is -1.0

-6 - 5 is -11.0

-6 * 5 is -30.0

-6 / 5 is -1.2

-6 % 5 is 4.0

```

**Strings**

A string is a collection on characters. An example is a name - like Aron. Aron is made up of four characters, ‘a’,’r’, ‘o’, ‘n’. They are enclosed with either single quotes or double quotes.

```python

name = 'Aron'

surname = "Koech"

print(type(name))

print(name)

print(type(surname))

print(surname)

```

```

<class 'str'>
Aron
<class 'str'>
Koech

```

We can concatenate the variables to be one word.

```python

print(name +' '+ surname)

print(name , surname)

```

```

Aron Koech

Aron Koech

```

We have combined the name and surname using string concatenation in the first line, with a space in between.

The second line of code uses comma-separated values to give the same output.

**Boolean**

Boolean is a data type that represents a binary value, either True or False. It is commonly used to evaluate conditions in decision making processes.

```python

x = -6

y = 5

print(x == y)

```

```

False

```

==(equality operator) is used to check if x and y variables are equal. If they are equal, it prints True, otherwise False.

**Non-primitive data types**

They are complex data types, that can store collection of values in different formats. They are:

* Lists

* Tuples

* Sets

* Dictionaries

**Lists**

Lists are data types that store a collection of values, such as integers and strings. They are stored inside [ ] brackets. Lists are ordered, meaning the order will not change. They are also mutable, meaning the elements can be modified after they have been created.

```python

x = [1, 2, 3, 4, 5] # creates a list of integers

colors = ['blue', 'pink', 'yellow', 'brown'] # creates a list of strings

list = [5, 10.4, 'Purple', False] # creates a list of mixed data types

print(x)

print(colors)

print(list)

```

```

[1, 2, 3, 4, 5]

['blue', 'pink', 'yellow', 'brown']

[5, 10.4, 'Purple', False]

```

To access an element in the list:

```python

print(colors[2])

```

This prints the color element at index 2, which is yellow.

Lists can also be sliced.

```python

print(colors[2:])

print(x[1:3])

print(list[:2])

```

```

['yellow', 'brown']

[2, 3]

[5, 10.4]

```

We can change an element in a list. Suppose we want to replace the second color to purple.

```python

colors[1] = 'purple'

print(colors)

```

```

['blue', 'purple', 'yellow', 'brown']

```

Tuples

Tuples are data types that contain ordered, immutable elements. The elements are enclosed in

( ) brackets.

```python

x = (1, 2, 3, 4, 5)

print(x)

```

```

(1, 2, 3, 4, 5)

```

We can access individual elements in a tuple by indexing, just like lists.

```python

print(x[2])

```

This prints the element in index 2, which is 3.

We can also access the range of elements using slicing.

```python

print(x[2:])

```

```

(3, 4, 5)

```

This prints the elements from index 2 to the last element.

**Sets**

Sets are collection of unique elements. They are unordered and mutable.

```python

x = (1,2,1,3,2,3,2,4,4,5)

print(set(x))

```

```

{1, 2, 3, 4, 5}

```

Only the unique elements are printed.

**Dictionaries**

Dictionaries are data types that are made up of key-value elements in pairs.

They are stored using curly {} brackets.

```python

dict = {'Eliud':1, 'Peter':2, 'Andrew':3, 'Mike':4}

print(dict)

```

```

{'Eliud': 1, 'Peter': 2, 'Andrew': 3, 'Mike': 4}

```

You can access individual values by referring to their keys.

```python

print(dict['Eliud'])

```

This will return 1, which is its key.

You can also change the value of the keys.

```python

dict['Eliud']=10

print(dict)

```

```

{'Eliud': 10, 'Peter': 2, 'Andrew': 3, 'Mike': 4}

```

**Conclusion**

Data types are categorized into primitive and non-primitive. There is still more to cover on data types. Check out [python data types](https://docs.python.org/3/library/datatypes.html) to learn more. 

