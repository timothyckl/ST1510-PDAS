02 Data Structures

## Table of Contents

1. List
    - Indexing Elements
    - List Iteration
    - Update List
    - List Operations
    - List Functions & Methods
    - List Comprehension
2. Tuples & Sets
    - Tuples vs Lists
    - Sets
3. Dictionary
    - Iteration
    - Dictionary Comprehension
    - Update Items
    - Dictiony Functions & Methods
4. Functions
    - Parameters
    - Methods or Functions
    - Lambda Functions
5. Error handling

## Python Lists
- Lists are used to reporesent arrays.
- They store collections of similar or dissimilar items.

Example:

```python
list1 = ['red', 'green', 'blue']
list2 = ['chonk', 10, 0.9]
```

### Indexing List Elements
- List indices start at 0, and can be sliced, concatenated etc.

![](https://i.imgur.com/WdYJqzw.png)

```python
words = ['hi', 'how', 'are', 'you']

print(len(words)) # returns 4
print(words[0]) # returns ‘hi’
print(words[-2:]) # returnss 'are', 'you'
```

### List Iteration

- for loops can be used to iterate throught lists.

```python
words = ['hi', 'how', 'are', 'you']

for item in words:
    print(item, end='\t') # returns hi    how    are    you
```

### Updating Lists

- To add elements in a list, use append() or insert() methods.

```python
os = ['Windows10', 'Ubuntu', 'Redhat']

os.append(“Kali") # add new item at the back
os.insert(1, “Debby") # insert new item at the index 1
os[1] = "Debian" # update value at index 1

# os = ['Windows10', 'Debian', 'Ubuntu', 'Redhat', 'Kali']
```

- To remove elements in a list, use del() or pop() methods

```python
del(os[1]) # removes ‘Debian’ at index 1
os.pop() # returns the last object ‘Kali’

# os = ['Windows10', 'Ubuntu', 'Redhat'] 
```

- Lists respond to the + and * operators much like strings, equating to concatenation (+) and repetition (*) as well

```python
os = ['Windows10', 'Ubuntu', 'Redhat']

print(os*2) # ['Windows10', 'Ubuntu', 'Redhat', 'Windows10', 'Ubuntu', 'Redhat']

tcp = [21,23,443]
udp = [53,135]

open_ports = tcp + udp
print(open_ports) # [21, 23, 443, 53, 135]
```

### Built-in List Functions

![](https://i.imgur.com/Jt9tjE4.png)

### Built-in List Methods

![](https://i.imgur.com/d0X41n8.png)

### List Comprehensions

- List comprehensions are a common way to create lists

```python
# normal list creation
numbers = [1, 2, 3, 4]
squares = []

for n in numbers:
  squares.append(n**2)

print(squares)  # [1, 4, 9, 16]

# using list comprehension
numbers2 = [1, 2, 3, 4]
squares2 = [n**2 for n in numbers2]

print(squares2)  # [1, 4, 9, 16]
```

- Can include conditional statements

```python
# using list comprehension
numbers = [1, 2, 3, 4]
squares = [n**2 for n in numbers if n%2==0] #only even numbers

print(squares)  # [4, 16]
```

## Tuples

- A tuple is like a list that can store different types of data 
- Tuples use round brackets instead of square brackets

```python
names = ('joe', 'mama', 420)
cube = (4,) # single element tuples end with a comma
```

### Tuples vs Lists

- Tuples are immutable
- Reassigning and appending tuple values will return an error

```python
student = ('p42069690', 'Mike Cox', 3.5)
student[2] = 4.0
# TypeError: 'tuple' object does not support item assigment

student.append('ST6969')
# AttributeError: 'tuple' object has no attribute 'append'
```

### Sets
- Sets are list without duplicate elements
- Frozen sets are immutable

```python
list1 = [1, 2, 3]
list2 = [2, 3, 4]
list3 = list1 + list2

print(list3) # returns [1, 2, 3, 2, 3, 4]
print(set(list3)) # returns {1, 2, 3, 4}

fset = frozenset(list3)
fset.add(4)
# AttributeError: 'frozenset' object has no attribute 'add'
```
### Built-in Set Methods

![](https://i.imgur.com/B9IcPio.png)

## Dictionaries

- Dictionaries are data types that work with key-value pairs
- Each value can be access by indexing with its key
```python
phonebook = {   
   #  key : value
   "John" : 938477566,    
   "Jack" : 938377264,    
    "Jill" : 947662781
}

print(phonebook["John"]) # returns 938477566
```

### Dictionary Iteration

```python
phonebook = {   
   #  key : value
   "John" : 938477566,    
   "Jack" : 938377264,    
    "Jill" : 947662781
}

print(phonebook.keys()) # returns dict_keys(['John', 'Jack', 'Jill'])

for i in phonebook:
    print(i) # prints keys
    print(phonebook[i]) # prints corresponding values
    
phonebook = {
    "John" : 938477566, 
    "Jack" : 938377264,  
    "Jill" : 947662781
}

for name, number in phonebook.items():
    print(f"{name}:{number}")
    
for i, j in enumerate(phonebook, 1): # optional start index
    print(i, j)
```

### Dictionary Comprehension
e.g. Reverseing key-value pairs

```python
phonebook = {
    "John" : 938477566, 
    "Jack" : 938377264,  
    "Jill" : 947662781
}

phonebook_reversed = {y:x for x,y in phonebook.items()}
```

### Adding New Items to Dictionaries

- Adding key value to the dictionary is similar to list

```python
phonebook = {
    "John" : 938477566, 
    "Jack" : 938377264,  
    "Jill" : 947662781
}

phonebook['Tom'] = 987654321

# after adding
# {'Jack': 93837726, 
# 'John': 94762781, 
# 'Jill': 93847755, 
# 'Jane': 91289900,
# 'Tom': 987654321}
```


- Add multiple values using update()

```python
phonebook = { 
    "Jack" : 93837726, 
    "John" : 94762781
}
phonebook2 = {
    "Jill" : 93847755,  
    "Jane": 91289900
}

phonebook.update(phonebook2)

# after update
# {'Jack': 93837726, 
# 'John': 94762781, 
# 'Jill': 93847755, 
# 'Jane': 91289900}
```

### Removing Dictionary Items

- del() function - Removes a key value pair using the key

```python
del(phonebook['Jill'])
print(phonebook) # prints {'Jack': 93837726, 'John': 94762781, 'Jane': 91289900}
```

- pop() method – Returns and removes using the key

```python
phonebook.pop('Jack')
print(phonebook) # prints {'John': 94762781, 'Jane': 91289900}
```

### Comparing Two Dictionaries

```python
importers = {'El Salvador' : 1234,'Nicaragua' : 152,'Spain' : 252}
exporters = {'Spain' : 252, 'Germany' : 251, 'Italy' : 1563}

# Find the intersection of importers and exporters i.e. duplicate keys
print(importers.keys() & exporters.keys()) 

# Find the difference between importers and exporters
print(importers.keys() - exporters.keys())

# Find countries where amount of exports matches amount of imports
print(importers.items() & exporters.items())
```

## Python Functions

- A function is a block of organized, reusable code that is used to perform a single, related action
- Functions provide better modularity for your application and a high degree of code reusing
- Optional parameters can pe specified with ```=```

### Defining a Function
```python
def printme(num, str='Hi',):
    for i in range(num):
        print(str, end='\t')
        
printme(3, 'Hello') # prints Hello    Hello    Hello
printme(4) # prints Hi    Hi    Hi    Hi
```

### Methods or Functions?

- Methods are functions tied to objects while normal functions are not

### Lambda Functions

- Lambda functions are nameless anonymous functions
- They can take any number of parameters, but can only have one expression

```python
print((lambda x, y: x+y)(2,3)) # prints 5
```

Example:

```python
num = [i for i in range(1,11)]
is_even =[]

for i in num:
    is_check.append((lambda x: True if x % 2 == 0 else False)(i))
```

### Why Use Lambda?

- We use lambda functions when we require a nameless function for a short period of time.
- In Python, we generally use it as an argument to a higher-order function (a function that takes in other functions as arguments). 
- Lambda functions are used along with built-in functions like filter(), map(), reduce() etc.

### filter()

- filter() in Python takes in a function and a list as arguments.
- The function is called with all the items in the list and a new list is returned which contains items for which the function evaluates to True.

```python
my_list = [5, 22, 4, 97, 54, 62, 8, 77, 28, 73, 61]
even = list(filter(lambda x: (x % 2 == 0 and x > 10), my_list))

print(even) # prints [22, 54, 62, 28]
```

### map()

- The map() function also takes in a function and a list.
- The function is called with all the items in the list and a new list is returned which contains items returned by that function for each item.

```python
lengths = [5, 7, 22, 9, 14, 6]
areas = list(map(lambda x: x*x, lengths))

print(areas) # prints [25, 49, 484, 81, 196, 36]
```

### reduce()

- The reduce() function is a part of functools module and again takes in both a function and a list 
- The function is called repeatedly across all the items in the list and a new reduced result is returned. 

```python
from functools import reduce

list1 = [5, 8, 10, 20, 50, 100]
sum = reduce((lambda x, y: x + y), list1)

print(sum) #  prints 193
```

## Python Exceptions

### try-except

- Programs should handle exceptions
- When exceptions occur, current process stops, passes exception to the caller process. If not handled, program will crash
- Exceptions can be handled with try, except
- Multiple exceptions can be caught

```python
try:
    x = int(input(“Enter a number: "))
except ValueError:
    print("Not a number")
except ZeroDivisionError:
    print("Pls enter a number bigger than 0!")
```

### try-except-finally

- Finally clause will always execute. Good for closing files

```python
 try:
    x=int(input("Enter a number: "))
    print(1/x) #print inverse
 except ValueError: #optional
    print("Pls enter a valid number!")
 except ZeroDivisionError: #optional
    print("Pls enter a number bigger than 0!")
 except:
    print("Any other exceptions will print this")
 finally:
    print("This line will always be printed")
```
