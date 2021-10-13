03 Data Manipulation w/ NumPy

## Table of Contents

1. Creating Arrays
2. NumPy Data Dypes
3. Array Inspection
4. Subsetting & Indexing
5. Copying & Sorting
6. Dimension Manipulation
7. Combining, Splitting & Converting
8. Array Mathematics
    - Operators
    - Math/Stat Methods
9. File I/O w/ Arrays

## Creating Arrays

NumPy provides N-dimensional arrays, which describe a collection of items __of the same type__

### Structure of ndarry

Example of a 3x3 ndarry with a size of 9:

![](https://i.imgur.com/8L3pg04.png)

### array() method

Syntax:

```python
import numpy as np

# Create a 1-d array of integers
a = np.array([1,2,3]) 

# Create a 2-d array (2x3)
b = np.array([(1,2,3), (4,5,6)]) 

# Create a 2-d array (2x4) of type float
c = np.array([(1.5,2.5,3.5,4.5),(5.5,6.5,7.5,8.5)], dtype=float)

# Create a 3-d array (2x2x4)
d = np.array([[(1,2,3,4), (5,6,7,8)], [(9,10,11,12), (13,14,15,16)]])

# Create a 1-d array of strings
e = np.array(['Apple', 'Orange', 'Pear', 'Durian'])
```

### zeros() and ones()

Syntax:

```python
import numpy as np

# Create a 3x4 2-d array, with initial value zero 
a = np.zeros((3,4))
print(a) # prints [[0. 0. 0. 0.]
         #         [0. 0. 0. 0.]
         #         [0. 0. 0. 0.]]


# Create a 2x3x4 3-d array with initial value one
b = np.ones((2,3,4))
print(b) # prints [[[1. 1. 1. 1.]
         #          [1. 1. 1. 1.]
         #          [1. 1. 1. 1.]]
         #                     
         #         [[1. 1. 1. 1.]
         #          [1. 1. 1. 1.]
         #          [1. 1. 1. 1.]]]
```

### arange()

Syntax:

```python
import numpy as np

# numpy.arange(start,stop,step)

# Create an array that starts from zero and ends at 8
a = np.arange(0,9)  
print(a) # prints [0 1 2 3 4 5 6 7 8]

# Create array that starts from 10 and ends at 19 with interval 2
c = np.arange(10,20,2)
print(c) # prints [10 12 14 16 18]

# Create an array that contains the dates in month of Aug 2017
d = np.arange('2020-10-10','2020-11-11',dtype='datetime64')
print('Countdown to 11/11 sales: \n',d)
```

### linspace()

Syntax:

```python    
import numpy as np

# numpy.linspace(start,stop,num)

# Create array that starts with 0 and ends at 2
# with 9 samples in between
d = np.linspace(0,2,9)
print(d) # prints [0. 0.25 0.5 0.75 1. 1.25 1.5 1.75 2.]
```

### linspace()

Syntax:

```python    
import numpy as np

# Create a constant array with a specified value
# numpy.full(shape, fill_value)
h = 7.0
e = np.full((2,2),h)
print(e) # prints [[7. 7.]
         #         [7. 7.]]

# Create a 2x2 identity matrix
f = np.eye(2)
print(f) # prints [[1. 0.]
         #         [0. 1.]]
```

### random() and randint()

Syntax:

```python    
import numpy as np

# Create a 2x2 array with random floats in the interval 0.0 to 1.0 
g = np.random.random((2,2))
print(g) # prints [[0.2535411 0.46228199]
         #         [0.54930425 0.65506307]]
         
         
# Create a 3x2x4 array with random numbers
# between 10 and 50 (not including 50)
h = np.random.randint(10,50,(3,2,4))
print(h) # prints [[[21 15 21 37]
         #          [47 14 16 45]]
         #        
         #         [[27 20 48 18]
         #          [45 36 43 17]]
         #         
         #         [[33 43 17 24]
         #          [35 10 11 18]]]
```

### empty()

Syntax:

```python
import numpy as np

# Create a 3x2  empty array
h = np.empty((3,2))
print(h) # prints [[0 0]
         #         [0 0]
         #         [0 0]]
```

### reshape()

Syntax

```python    
import numpy as np

# Create 20 numbers from 1 to 10 as a 1-d array
# then reshape this to a 2d array of shape 2x5
a = np.arange(1, 11).reshape(2,5)
print(a) # prints [[ 1  2  3  4  5]
         #         [ 6  7  8  9 10]]
```

## NumPy Data Dypes

| Built-in dtype | Code | Data Type |
| -------------- | ---- | --------- |
| np.int32 | i4 | 32-bit integer |
| np.int64 | i8 | 64-bit integer |
| np.float64 | f8 | 64-bit decimal number |
| np.bool | ? | Boolean type storing TRUE and FALSE values |
| np.object | O | Python object type |
| np.datetime64 | datetime64 | NumPy data for dates |
| np.unicode | U8 (length is 8) | Fixed-length Unicode string type |


```python
import numpy as np
import math

a = np.array([math.pi],dtype=np.int32)
b = np.array([math.pi],dtype=np.float64)
c = np.array([math.pi],dtype=np.bool)
d = np.array([math.pi],dtype=np.object)
e = np.array([math.pi],dtype=np.unicode)

print(a,b,c,d,e)
print(a.dtype,b.dtype,c.dtype,d.dtype,e.dtype)

# prints [3] [3.14159265] [True] [3.141592653589793] ['3.141592653589793']
#        int32 float54 bool object <U17
```

## Array Inspection

### shape

Syntax: 

```python    
import numpy as np

# Create 3 arrays with different shapes
a = np.array([1,2,3])
b = np.array([(1,2,3),(4,5,6)])
c = np.array([[(1,2,3,4),(5,6,7,8)], [(9,10,11,12),(13,14,15,16)]])

print(a.shape) # prints (3,)

print(b.shape) # prints (2, 3)

print(c.shape) # prints (2, 2, 4)
```

### len, ndim, size 

Syntax:

```python    
import numpy as np
# Create 3 arrays with different shapes and sizes
a = np.array([1,2,3,4,5,6])
b = np.array([(1,2,3),(4,5,6)])
c = np.array([[(1,2,3,4),(5,6,7,8)],       
              [(9,10,11,12),(13,14,15,16)]])

# Number of rows
print(len(a)) # prints 6
print(len(b)) # prints 2
print(len(c)) # prints 2

# Number of dimensions
print(a.ndim) # prints 1
print(b.ndim) # prints 2
print(c.ndim) # prints 3

# Total number of elements across dimensions
print(a.size) # prints 6
print(b.size) # prints 6
print(c.size) # prints 16
```

## Subsetting & Indexing

### One-dimensional Slicing & Indexing

```python    
import numpy as np

a = np.arange(9) # a = [0,1,2,3,4,5,6,7,8]
b = np.array # creates empty array

# Select the element at index 2
print(a[2]) # prints 2

# You can slice NumPy arrays like you do with Python Lists
# Select elements from index 0 to 7 with step 2
print(a[:7:2]) # prints 0 2 4 6

# Select and reverse elements from index 0 to the end
print(a[::-1]) # prints 8 7 6 5 4 3 2 1
```

### Multi-dimensional Slicing & Indexing

```python    
import numpy as np

# Create an array with 0 to 23 and reshape it into a 2x3x4 array
# Think of it as an Excel workbook with 2 worksheets
# Each worksheet has 3 rows,4 columns
b = np.arange(24).reshape(2,3,4)

print(b) # prints [[[0 1 2 3]
         #          [4 5 6 7]
         #          [8 8 10 11]]
         #
         #         [[12 13 14 15]
         #          [16 17 18 19]
         #          [20 21 22 23]]
         
# Select first worksheet, second row, all columns
print(b[0,1])    # [4 5 6 7]

# Select first worksheet, all rows, second column
print(b[0,:,1])   # [1 5 9]

# Select first worksheet, 2nd row, alternate column
print(b[0,1,::2])  # [4 6]

# Select first worksheet, all rows, last col, but in reverse
print(b[0,::-1, -1])  # 11 7 3

# Select 1st worksheet, last col, every 2 rows
print(b[0,::2,-1])  # 3 11

# Select all worksheets but reverse, all rows, all col, 
print(b[::-1])  
```

### Boolean Indexing

Boolean indexing lets you indicate if an element should be included
In the example below, we want to create an array with only the even numbers

```python
import numpy as np

a = np.arange(6).reshape(2,3)
print(a) # prints [[0 1 2]
         #         [3 4 5]]

# create filter array
b = a % 2 == 0
print(b) # prints [[True False True]
         #         [False True False]]

c = a[b] # same as c = a[a % 2 == 0]
print(c) # prints [0 2 4]
```

### np.where()

np.where can be used to retrieve the index where the Boolean expression is fulfilled 

```python    
import numpy as np

a = np.arange(6).reshape(2,3)
print(a)

# using np.where
even = np.where(a % 2 == 0)
print('rows  where boolean is met: \t', even[0])
print('columns where boolean is met: \t', even[1])

print(a[even]) # same as a[np.where(a%2==0)]
```

See [How to work with numpy.where()](https://kanoki.org/2020/01/03/how-to-work-with-numpy-where/)

### Subsetting & Slicing Arrays

```python    
a = np.arange(1,10)
arr = a.reshape(3,3)

print(arr) # prints [[1 2 3]
           #         [4 5 6]
           #         [7 8 9]]
           
# rows 0-1, col 1-2
print(arr[:2,1:]) # prints [[2 3]
                  #         [5 6]]
                  
print(arr[2], arr[2,:], arr[2:,:]) # prints [7 8 9] [7 8 9] [7 8 9]
```

## Copying & Sorting

### np.copy()

Syntax:

```python    
import numpy as np

# Create 2 arrays with different data types, shapes and sizes
a = np.array([5, 4, 3, 2, 1])
b = np.copy(a)



print(a) # prints [5, 4, 3, 2, 1]
print(b) # prints [5, 4, 3, 2, 1]
```

### np.sort()

Syntax:

```python    
colors = np.array([("Red","Blue","Yellow"),
		           ("Green","Cyan","Magenta")])   
colors = np.sort(axis=1) # sort along rows

print(colors) # ptints [['Blue' 'Red' 'Yellow']
              #         ['Cyan' 'Green' 'Magenta']]
```

See [A quick guide to np.sort()](https://www.sharpsightlabs.com/blog/numpy-sort/)

## Dimension Manipulation

### flatten()

```flatten()``` converts a multi-dimensional array to a 1-D array.

```python
import numpy as np

b = np.arange(24).reshape(2,3,4) # b= [[[0, 1, 2, 3], [4, 5, 6, 7], [8..],[20, 21, 22, 23]]]
c = b.flatten()

print(b) 
print(c) # [ 0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23]

c[0] = 100;  # change the first value in the copy

print(b) # no change 
print(c) # [ 100  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23]
```

### reshape()

```reshape()``` creates a new array with new dimensions. \
This does not change the array data or the original array itself.

```python
import numpy

my_array = numpy.arange(6)

print(my_array) # prints  [0 1 2 3 4 5]
print(numpy.reshape(my_array,(3, 2))) # prints [[0 1]
                                      #         [2 3]
                                      #         [4 5]]
                                      
print(numpy.reshape(my_array,(2, 3))) # prints [[0 1 2]
                                      #         [3 4 5]]
```

### shape()

```shape()``` can retrieve array dimensions or change array dimensions.

```python
import numpy as np

a= np.array([1, 2, 3, 4, 5])
print(a.shape)     # (5,) -> 5 rows and 0 columns

b = np.array([[1, 2],[3, 4],[6,5]])
print(b.shape) # (3, 2) -> 3 rows and 2 columns 

# Change the shape of the array
c = np.array([1,2,3,4,5,6])
c.shape = (3, 2)
print(c) # prints [[1 2]
         #         [3 4]
         #         [5 6]]
```

### transpose()

```transpose()``` is both a library level function and an instance method. \
This means it can be called as ```numpy.transpose(ndarray)``` or ```numpy.ndarray.transpose()```. \
ndarray has an attribute named ‘T’, which returns the transpose of the array.

```python
import numpy as np

x = np.array(([10,20,30,40], [50,60,70,80], [90, 85, 75, 45]))

print(x) # prints [[10 20 30 40]
         #         [50 60 70 80]
         #         [90 85 75 45]]

# All return the transpose of x [[10 50 90]
print(x.transpose())       #     [20 60 85]
print(np.transpose(x))     #     [30 70 75]
print(x.T)                 #     [40 80 45]]
```

### resize()

```resize()``` is similar to ```reshape()``` but does not enforce dimension restrictions. \
Values in an array will repeat if there are not enough values.

```python    
import numpy as np

a = np.array([[0,1],[2,3]]) # 2x2 array

print(a)
print(np.resize(a, (4, 1)))
print(np.resize(a, (2, 3))) # values will repeat

print(np.reshape(a, (2, 3))) # error
```

## Combining

### concatenate()

```concatenate()``` concatenates two or more arrays along an axis.

Concatenating 1-D Arrays:

```python
import numpy as np

x = np.arange(5)
y = np.arange(6,10)
z = np.arange(11,15) 

print(x) # prints [0 1 2 3 4]
print(y) # prints [6 7 8 9]
print(z) # prints [11 12 13 14]
print(np.concatenate((x,y,z))) # prints [0 1 2 3 4 6 7 8 9 11 12 13 14]
```

Concatenating 2-D Arrays:

By default ```concatenate()``` concatencates along axis 0. \
Dimensions for the concatenated axis __MUST__ match.

Concatenation along axis 0: 
```python    
import numpy as np

# Reshaped to 2-D
x = np.arange(1,5).reshape (2,2)
y = np.arange(6,12).reshape(3,2)

print(x)
print(y)
print(np.concatenate((x,y))) # prints [[1 2]
                               #       [3 4]
                               #       [6 7]
                               #       [8 9]
                               #       [10 11]
```

Concatenation along axis 1: 
```python    
import numpy as np

# Reshaped to 2-D
x = np.arange(1,5).reshape (2,2)
y = np.arange(6,12).reshape(2,3)

print(x)
print(y)
print(np.concatenate((x,y), axis = 1)) # prints [[1 2 6 7 8]
                                       #         [3 4 9 10 11]]
```

### append() 

Values appened must be of the correct shape (the same shape as arr, excluding axis) \
If axis is not specified, values can be any shape and will be flattened before use.

```python    
import numpy as np

x = np.array([(1,2,3), 
	          (4,5,6)])

x1 = np.append(x, np.array([(7,8,9)]), axis = 0)
x2 = np.append(x, np.array([(7,8), 
                            (9,10)]), axis = 1)

print(x1) # prints [[1 2 3]
          #         [4 5 6]
          #         [7 8 9]]
          
print(x2) # prints [[1 2 3 7 8]
          #         [4 5 6 9 10]]
```

## Splitting Arrays

### split()

```split()``` splits an array into multiple sub-arrays.

```python
import numpy as np

x = np.arange(12.0)
y = np.split(x, 3)

print(x) # prints [0. 1. 2. 3. 4. 5. 6. 7. 8. 9. 10. 11.]
print(y) # prints [0. 1. 2. 3.], [4. 5. 6. 7.], [8. 9. 10. 11.]
```

### vsplit()

```vsplit()``` splits an array into multiple sub-arrays vertically.  \
Same as ```split()``` with axis = 0, the array is always split along the first axis regardless of the array dimension.

```python    
import numpy as np

x = np.arange(12.0).reshape(4, 3)
y = np.vsplit(x, 2)

print(x) # prints [[0.  1.  2.]
         #         [3.  4.  5.]
         #         [6.  7.  8.]
         #         [9. 10. 11.]]
         
print(y[0]) # prints [[0. 1. 2.]
            #         [3. 4. 5.]]
            
print(y[1]) # prints [[6.  7.  8.]
            #         [9. 10. 11.]]
```

### hsplit()

```hsplit()``` splits an array intp multiple sub arrays horizontally.  \
Same as ```split()``` with axis = 1, the array is always split along the first axis regardless of the array dimension.

```python    
import numpy as np

x = np.arange(12.0).reshape(3, 4)
y = np.hsplit(x, 2)

print(x) # prints [[0. 1. 2. 3.]
         #         [4. 5. 6. 7.]
         #         [8. 9. 10. 11.]]
         
print(y[0]) # prints [[0. 1.]
            #         [4. 5.]
            #         [8. 9.]]
            
print(y[1]) # prints [[2. 3.]
            #         [6. 7.]
            #         [10. 11.]]
```

## Converting Arrays

### tolist()

```tolist()``` returns a copy of array as a nested list. \
Data items are converted to the nearest compatible Python type.

```python    
a = np.array([1, 2])
b = np.array([[1, 2], [3, 4]])

print(a.tolist()) # prints [1, 2]
print(b.tolist()) # prints [[1, 2], [3, 4]]
```

### astype()

```astype()``` returns a copy of an array cast to a specified dtype.

```python    
a = np.array([1, 2])

print(a.astype(int)) # prints [1 2]
print(a.astype(float)) # prints [1. 2.]
```

## Array Mathematics

### Arithmetic Operators

The standard arithmetic operators such as: ```+, -, *, /, **, %```  are applied on individual elements, so, arrays have to conformable.

```python    
x = np.array(([10,20,30],
              [40,50,60]))
y = np.array(([1,2,3], 
              [4,5,6]))

print(x + y)
print(x - y)
print(x * y)
print(x / y)
print(x % y)
```

### Logical Operators

Similarly, logical operators ```>, < , ==``` are applied on individual elements, so arrays have to be of same size.

```python    
import numpy as np

x = np.array(([10,20,30],
              [40,50,60]))
y = np.array(([1,2,3], 
              [4,5,6]))

print(x > y)
print(x < y)
print(x == y)
```

### Math/Stat Methods

![](https://i.imgur.com/UJ1GFhP.png)

### sum()

```sum()``` returns the sum of all elements in an array or along an axis.

> __Parameters__: ```numpy.sum(a, axis=None, dtype=None, out=None, keepdims=<class numpy._globals._NoValue>)```

```python 
b = np.arange(24).reshape(6,4)

print(b.sum()) # prints 276
print(f'sum of cols {b.sum(axis = 0)}'') # prints sum of cols [60 66 72 78]
print(f'sum of rows{b.sum(axis = 1)}') # prints sum of rows [6 22 38 54 70 86]
```

### mean()

```mean()``` returns the mean of elements in an array or along an axis.

> __Parameters__: ```numpy.mean(a, axis=None, dtype=None, out=None)```

```python
b = np.arange(24).reshape(6,4)

print('Mean ', b.mean()) # prints Mean 11.5
print('Mean of columns ', b.mean(axis=0)) # prints Mean of columns [10. 11. 12. 13.] 
print('Mean of rows ', b.mean(axis=1))  # prints Mean of rows [1.5 5.5 9.5 13.5 17.5 21.5]
```

### median()

```median()``` returns the median of an arry elements along an axis.

> __Parameters__: ```numpy.median(a, axis=None, out=None, overwrite_input=False, keepdims=False)```

```python    
a = np.array([[10, 7, 4], 
              [3, 2, 1]])

median = np.median(a)

print(median) # prints 3.5
```

### min(), max()

```min()``` and  ```max()``` returns the min/max of an array, or along an axis.

> __Parameters__:&nbsp;```ndarray.min(axis=None, out=None, keepdims=False)```
\
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;``` ndarray.max(axis=None, out=None, keepdims=False)```

```python
import numpy as np

b = np.arange(24).reshape(8,3)

print(b.min()) # prints 0
print(b.min(axis = 0)) # prints [0 1 2]
print(b.min(axis = 1)) # prints [0 3 6 9 12 15 18 21]

print(b.max()) # prints 23
print(b.max(axis = 0)) # prints [21 22 23]
print(b.max(axis = 1)) # prints [2 5 8 11 14 17 20 23]
```

### argmin(), argmax()

```argmin()``` and ```argmax()``` return arrays containing the indices of the smallest/largest elements.

> __Parameters__:&nbsp;```numpy.argmin(a, axis=None, out=None)```
\
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;``` numpy.argmax(a,axis=None, out=None)```

```python    
b = np.arange(24).reshape(8,3)

print(b.argmin()) # prints 0
print(b.argmin(axis = 0)) # prints [0 0 0]
print(b.argmin(axis = 1)) # prints [0 0 0 0 0 0 0 0]

print(b.argmax()) # prints 23
print(b.argmax(axis = 0)) # prints [7 7 7]
print(b.argmax(axis = 1)) # prints [2 2 2 2 2 2 2 2]
```

### cumsum()

```cumsum()``` returns the cumulative sum of array elements along an axis.

> __Parameters__: ```numpy.cumsum(a, axis=None, dtype=None, out=None)```

```python
a = np.array([[1,2,3],
              [4,5,6]])

b = np.cumsum(a)
print(b) # prints [1 3 6 10 15 21]
```

### cumprod()

```cumprod()``` returns the cumulative product of array elements along an axis.

> __Parameters__: ```numpy.cumprod(a, axis=None, dtype=None, out=None)```

```python    
a = np.array([[1,2,3], 
              [4,5,6]])

b = np.cumprod(a)
print(b)  # prints [1 2 6 24 120 720]
```

### std()

```std()``` returns the standard deviation along an axis.

> __Parameters__: ```numpy.std(a, axis=None, dtype=None, out=None)``` 

```python    
import numpy as np

a = np.array([[1,2,3], 
              [4,5,6]])

print(np.std(a)) # prints 1.707825127659933
```

### var()

```var()``` returns the variance along an axis

> __Parameters__: ```numpy.var(a, axis=None, dtype=None, out=None, ddof=0)``` 

```python    
import numpy as np

a = np.array([[1,2,3], [4,5,6]])

print(np.var(a)) # prints 2.9166666666666665
print(np.var(a, axis = 0, dtype = np.float32)) # prints [2.25 2.25 2.25]
print(np.var(a, axis = 1, dtype = np.float64)) # prints [0.66666667 0.66666667]
```
