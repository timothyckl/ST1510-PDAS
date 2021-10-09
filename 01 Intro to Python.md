# 01 Introduction to Python

## Table of Contents

3. [Importing Modules](##Importing-Modules)
    - Built-in Modules
4. [Data Types](##Data-Types)
5. [Operators](##Operators)
6. [If-else](##If-else)
7. [Loops](##Loops)
    - for loop
    - while loop


## Importing Modules

The ```import``` keyword used when functions not in the default Python library are needed.

#### __Built-in Modules__
Examples: 
```python
import random 
import datetime
import dateutil
import time
import ZipFile
```

## Data Types

Python has 3 numeric types: 

```python
a = 2 # int
b = 3.459 # float
c =  1+2j # complex
```

Integers are whole numbers while floating point numbers have decimal points.

### Working w/ Numeric Data Types

```python
import math

x = 349.4378

print(math.isnan(x)) # returns True if x is NOT a number
print(math.trunc(x)) # truncate decimal portion of x  output: 349
print(math.ceil(x)) # round x upwards  output: 350
print(math.floor(x)) # round x downwards  output: 349
print(math.sqrt(x)) # square root of x  output: 18.693255468216336

```

### Working w/ strings
Python has a built-in string class with many handy features. \
String literals can be enclosed by either double or single quotes.

```python
s1 = 'hi how are you'
s2 = "I am fine, thank you"
```

Characters in a string can be accessed by index \
Indexing starts with zero in Python strings.

![](https://i.imgur.com/YBH9bXj.png)

```python
s = 'hi how are you'

print(s[0]) # h
print(s[1]) # i
print(s[3:6]) # how 
```

Length of a string can be retrieved with ```len()```

```python
print(len(s)) #14
```

Repetition and Concatenation

```python
print(s + 'today') # hi how are you today
print(s * 2) # hi how are youhi how are you
```

String concatenation does not work with numeric data types.

```python
pi = 3.14

text = 'The value of pi is ' + pi      ## This does NOT work
text = 'The value of pi is '  + str(pi)  ## This is ok

print(text)
```

Since ```str()``` are classes in Python, they have their own methods.

```python
s = 'hi how are you'

print(s.upper()) # HI HOW ARE YOU
print(s.lower()) # hi how are you
print(s.isnumeric()) # returns boolean value
print(s.find('ar')) # finds 'ar' in string and return index 7

words = s.split(sep=' ') # splits s into an array, using space as separator
print(words[2]) # returns `are` at index 2
```

## Operators

```python
num1 = 10
num2 = 5
num3 = 3
```

### Arithmetic Operators

| Operator | Description | Operation |
| ----------- | ----------- | ----------- |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; + | Add num1 and num2 | num1 + num2 = 15 |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - | Subtract num2 from num1 | num1 - num2 = 5 |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; * | Multiply num1 by num2 | num1 * num2 = 50 |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; / | Divide num1 by num2 | num1 / num2 = 2 |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; % | Get the remainder after dividing num1 by num2 | num1 % num2 = 0 |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ** | num1 to the power of num2 |num1 ** num2 = 10^5  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // | Divide num1 by num3 and discard any decimal points from the answer | num1 // num3 =  3 |

### Assignment Operators

Python allows you to assign single or multiple variables at one go using the ```=``` operator

```python
a, b, c, d, e, x = 1, 10, 3, 100, 23, 5 

a += x # a = a + x
b -= x # b = b - x
c *= x # c = c * x
d /= x # d = d / x
e %= x # e = e % x
```

### Comparison Operators

Comparison operations return boolean values.

```python
num1 = 10
num2 = 20

print(num1 == num2) # False
print(num1 != num2) # True
```

| Operator | Operation | Values |
| ----------- | ----------- | ----------- |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; == | num1 == num2 | False |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; != | num1 != num2 | True |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; > | num1 > num2 | False |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; < | num1 < num2 | True |
|&nbsp;&nbsp;&nbsp;&nbsp; >= | num1 >= num2 | False |
|&nbsp;&nbsp;&nbsp;&nbsp; <= | num1 <= num2 | True |


### Logical Operators

```python
num1 = 10
num2 = 20
name1 = 'Dora'
name2 = 'Bryan'

print(num1 == num2) # False
print(num1 != num2) # True
```

| Operator | Operation | Values |
| ----------- | ----------- | ----------- |
|&nbsp;&nbsp;&nbsp;&nbsp; and | num1>=10 and num2>=10 | True |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; or | len(name1)>=5 or len(name2)>=5| True |
|&nbsp;&nbsp;&nbsp;&nbsp; not | not num1==num2 | True |


### Membership Operators

Membership operators validate membership in a sequence, such as strings, lists, or tuples.

```python
a = 5
b = 10

list = [1, 2, 3, 4, 5 ]

print(a in list) # True
print(b in list) # False
print(b not in list) # True
```

### Identity Operators

Identity operators compare the memory locations of two objects. 

```python
a = 20
b = 20
c = a
d= 30

print( a is b)  # True
print(a is not b) # False
print(a is c)  # True
print(b is c) # True
print(a is d) # False
```

## if-else

if-else statements allow for conditional programming. \
When a condition is truthy, only that code block will be executed.

```python
a = 2
if (1 + 2 == a):
    # do something
elif (1 + 1 == a):  # only this block will run
    # do something
else:
    #do something else
```

### Nested if-else

```python
number = input("Enter your choice (1-2): ")
staff = input("Are you a staff (Y/N)? ")

if number=="1":
   if staff.upper() == "Y":
        price = 5*0.9
   else:
        price = 5*0.95
elif number=="2":
    if staff.upper() == "Y":
        price = 10*0.8
    else:
        price = 10
else:
   print("You did not enter a valid input")
   #exit()   

print(f"Price is ${price}")

```

## Loops

Loops are structures that enable repetition of code which is also called iteeration. There are 2 types of loops.

#### __for loop__

Syntax:

```python
for stepper_variable in sequence_variable:
   # code
```

Example:

```python
for i in range(5):
    print(i)
 
# Output:
#         0
#         1
#         2
#         3
#         4
```

```python
my_list = ['a', 'b', 'c']

for i in my_list:
    print(i)
    
# Output:
#         a
#         b
#         c
```

##### for-else


Python also allows the use of else condition with for loops. 
An else block after for/while is executed when the loop is NOT terminated by a break statement. 

Syntax:

```python
for item in container:
    if search_something(item):
        # Found it!
        process(item)
        break
else:
    # Didn't find anything..
    not_found_in_container()
```

#### __while loop__

A while loop repeatedly executes as long as a given condition is true.

Syntax:
```python
count = 1

while count <= 10:
   print(f'The count is: {count}')
   count += 1

print("Good bye!")
```
