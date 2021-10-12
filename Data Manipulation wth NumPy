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


```python=
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
