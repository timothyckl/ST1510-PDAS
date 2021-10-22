04 Visualisation w/ Matplotlib

## Table of Contents

1. Plot Customisation
2. Multiple Plots
3. Bar Charts
4. Pie Charts
5. Histograms
6. Scatter Plots
7. Box Plots
8. Display Images
9. Interactive Charts

## Plot Customisation

### Specifying x, y axis range 

`axis()` allows for changes in the x, y ranges of a graph.

```python 
import matplotlib.pyplot as plt

plt.plot([10, 40, 60, 90], 
         [1, 4, 9, 16])
plt.axis([0, 100, 0, 20])
plt.show()
```

Similar to `axis()`, `xlim()` and `ylim()` changes the range values of x/y axis respectively.

```python
import matplotlib.pyplot as plt

plt.plot([10, 40, 60, 90], [1, 4, 9, 16])

#plt.axis([0, 100, 0, 20])

plt.xlim(0,100)
plt.ylim(0,20)

plt.show()
```

Both methods output:

![](https://i.imgur.com/odSiCpk.png)

### Titles and Labels

Titles and labels for plots can be added with the `title()`, `xlabel()` and `ylabel()` methods.

```python    
import matplotlib.pyplot as plt

plt.title('Grades vs Hours Studied')
plt.xlabel('Hours Studied')
plt.ylabel('Grades')

plt.plot([5, 10, 30, 40],
         [50, 60, 70, 90])
plt.show()
```

Output:

![](https://i.imgur.com/hnh1vhW.png)

### Colour & Patterns

You can specify a format string that indicates the color and line type of the plot. 

Supported color abbreviations are:

- full names (e.g. 'green')
- hex strings (e.g. '('#008000')
- RGB/RGBA tuples (e.g. (0,1,0,1))
- greyscale intensities (e.g. '0.8')

To plot with red circles, you would use `'ro'`

```python
import matplotlib.pyplot as plt

plt.plot([1,2,3,4], 
         [1,4,9,16], 'ro')
plt.axis([0, 6, 0, 20])
plt.show()
```

Output:

![](https://i.imgur.com/MdQs3h8.png)

Reference: [List of marker styles](https://matplotlib.org/stable/api/markers_api.html)


### Plot Method kwargs

Lines have attributes that can be set with keyword arguments:

- linewidth
- dash style
- antialiased

```python
import matplotlib.pyplot as plt
x,y = [1,2,3,4],
      [1,2,3,4]
plt.plot(x, y,
       linewidth=5,
       linestyle="dotted",
       color="red")

plt.show()
```

Output: 

![](https://i.imgur.com/HTazKDK.png)


### Ticks

Ticks are the values(number/string) used to show specific points on the coordinate axis. 

When a graph is plotted, the axes adjust and take the default ticks. 

Matplotlib’s default ticks are generally sufficient in common situations but are in no way optimal for every plot. 

`xticks()` and `yticks()` are used to add custom tick marks.

```python    
# using xticks()
import numpy as np
import matplotlib.pyplot as plt

y = [70,30,40,90,10]
xlabels = ('Tom', 'Dick', 'Harry', 'Sally', 'Sue')
plt.xticks(np.arange(5),xlabels)
plt.ylim(0,100)
plt.plot(y)

plt.show()
```

Output:

![](https://i.imgur.com/jWO5pke.png)

```python    
# using yticks()
import numpy as np
import matplotlib.pyplot as plt

x = [70,30,40,90,10]
ylabels = [0, 25, 50, 75, 100]
plt.yticks(np.arange(5),ylabels)
plt.xlim(0,100)
plt.scatter(x, np.arange(5))

plt.show()
```

Output:

![](https://i.imgur.com/ZnCi7pQ.png)

### Class Exercise

```python
import matplotlib.pyplot as plt 

x = [i for i in range(1, 10)]
y = [j**2 for j in x]

plt.title('The x**2 graph')
plt.xlabel('x-axis')
plt.ylabel('y-axis')
plt.plot(x, y, color='b', marker='o', linestyle='dashed')
plt.show()
```

Output:

![](https://i.imgur.com/Z3Q4Y5f.png)


## Multiple Plots

Matplotlib allows plotting multiple plots on a single figure or plot multiple plots on multiple figures using the subplot and figure commands.

```python    
import numpy as np
import matplotlib.pyplot as plt

# Create numpy array with values 
# between 0 and 5 in steps of 0.2
t = np.arange(0, 5, 0.2)

plt.plot(t, t, 'r--',   # red dash
         t, t**2, 'bs', # blue square
         t, t**3, 'g^') # green triangle
plt.show()
```

Output:

![](https://i.imgur.com/rng8uCn.png)

### Adding Legend to Plot

`legend()` method is used to add a legend on graphs with multiple lines.

```python
import numpy as np
import matplotlib.pyplot as plt

line_1 = np.random.randint(1,20,20)
line_2 = np.random.randint(1,20,20)

plt.figure(figsize=(10,5))

plt.plot(line_1,label="Line 1")
plt.plot(line_2,label="Line 2")

legend = plt.legend(loc='lower right')
plt.show()
```

Output:

![](https://i.imgur.com/NTihqsz.png)

Reference: [matplotlib.pyplot.legend()](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.legend.html)

### 2 Subplots, 1 Figure

Multi-plots are decalred with `figure()` that takes an integer as a reference number.

Subplot call signatures: `subplot(nrows, ncols, plot_number)`

```python    
import numpy as np
import matplotlib.pyplot as plt

t1 = np.arange(0.0, 5.0, 0.1)
t2 = np.arange(0.0, 5.0, 0.02)

plt.figure(1)
plt.subplot(2, 1, 1)  # 2 rows, 1 col, 1st row
plt.plot(t1, 'b*')

plt.subplot(212) # 2 rows, 1 col, 2nd row
plt.plot(t2, 'r-')
plt.show()
```

Output:

![](https://i.imgur.com/tUMPQ1O.png)


### 2 Subplots, 2 Figures

```python     
import matplotlib.pyplot as plt

plt.figure(1)  # first figure
plt.subplot(211)  # 2 rows, 1 col, 1st row
plt.title('Easy as 1, 2, 3')
plt.plot([1, 2, 3])
plt.subplot(212)  # 2 rows, 1 col, 2nd row
plt.plot([4, 5, 6], 'r-')

plt.figure(2)  # second figure
plt.subplot(121)  # 2nd subplot 1st figure
plt.plot([4, 5, 6], 'g-')
plt.subplot(122)  # 2nd subplot 2nd figure
plt.plot([7, 8, 9], 'y-')

plt.show()
```

Output:

![](https://i.imgur.com/L7fMSpy.png) 

![](https://i.imgur.com/ZrlQzKT.png)


### Changing Figure Size

`figure()` has parameters to change figsize such as `plt.figure(figsize=(width, height))`

```python
import matplotlib.pyplot as plt

plt.figure(1, figsize=(5, 5))  # first figure, 5 inches width and height
plt.subplot(211)  # 2 rows, 1 col, 1st row
plt.title('Easy as 1, 2, 3')
plt.plot([1, 2, 3])
plt.subplot(212)  # 2 rows, 1 col, 2nd row
plt.plot([4, 5, 6], 'r-')

plt.figure(2, figsize=(8, 5))  # second figure, 8 inches width and 5 inches height
plt.subplot(121)  # 2nd subplot 1st figure
plt.plot([4, 5, 6], 'g-')
plt.subplot(122)  # 2nd subplot 2nd figure
plt.plot([7, 8, 9], 'y-')

plt.show()
```

Output:

![](https://i.imgur.com/MA6ulzW.png)

![](https://i.imgur.com/OWSJ7q9.png)

### Clearing Figures

`plt.figure(figure_id).clf()` method can be used to clear a specified figure.

```python    
import matplotlib.pyplot as plt

plt.figure(1, figsize=(5, 5))  # first figure
plt.subplot(211)  # 2 rows, 1 col, 1st row
plt.title('Easy as 1, 2, 3')
plt.plot([1, 2, 3])
plt.subplot(212)  # 2 rows, 1 col, 2nd row
plt.plot([4, 5, 6], 'r-')

plt.figure(2, figsize=(8, 5))  # second figure
plt.subplot(121)  # 2nd subplot 1st figure
plt.plot([4, 5, 6], 'g-')
plt.subplot(122)  # 2nd subplot 2nd figure
plt.plot([7, 8, 9], 'y-')

plt.figure(2).clf()  # clear second figure
plt.show()
```

Outputs:

![](https://i.imgur.com/bCzBeU1.png) 

```python 
<Figure size 576x360 with 0 Axes> # empty figure
``` 

### Subplots, Figures & Axes
`plt.subplots()` is a function that returns both figure and axes objects.

```python    
# More concise
fig, ax = plt.subplots()

# Less concise
fig = plt.figure()
ax = fig.add_subplot(111)
```

`fig` object is useful when changes figure-level attributes or saving figures as images in future (e.g. with `fig.savefig('myFigImage.png')`)

`axes` object is useful when changing axis-level attributes (e.g. customize ticks, pan/zoom axis etc)

### Saving Figures

```python    
import numpy as np
import matplotlib.pyplot as plt

y = [70,30,40,90,10]
xlabels = ('Tom', 'Dick', 'Harry', 'Sally', 'Sue')
plt.xticks(np.arange(5),xlabels)
plt.ylim(0,100)
plt.plot(y)

# Save the figure as a PNG.  
# You can also save it as a PDF, JPEG, etc.  
# Just change the file extension in this call.  
# bbox_inches="tight" removes all whitespace on the edges of your plot.  
plt.savefig("mygraph.png", bbox_inches="tight")
```

mygraph.png:

![](https://i.imgur.com/1csMnIk.png)

### Working w/ Subplots, Figs & Axes

```python    
import matplotlib.pyplot as plt

x_labels = ["Test 1", "Test 2", "Test 3"]
mary = [75,89,93]
john = [67,69,73]
jack = [87,77,70]

fig,ax = plt.subplots()
fig.set_facecolor("lightblue")

ax.plot(mary,label="mary")
ax.plot(john,label="john")
ax.plot(jack,label="jack")

ax.set_xticks(np.arange(3))
ax.set_xticklabels(x_labels, rotation=45)
legend = ax.legend(loc='upper right', shadow=True)
plt.show()
```

Output: 

![](https://i.imgur.com/w70V4Fc.png)

#### Single Axis

```python  
import matplotlib.pyplot as plt

x_labels = ["Test 1", "Test 2", "Test 3"]
mary = [75,89,93]
john = [67,69,73]
jack = [87,77,70]
fig,ax = plt.subplots()
fig.set_facecolor("lightblue")
ax.plot(mary,label="mary")
ax.plot(john,label="john")
ax.plot(jack,label="jack")
ax.set_xticks(np.arange(3))
ax.set_xticklabels(x_labels, rotation=45)
legend = ax.legend(loc='upper right', shadow=True)

fig.suptitle('Figure Title', fontsize=14, fontweight='bold')
ax.set_title('Axes title')

plt.show()
```

Output:

![](https://i.imgur.com/Dyp9I8T.png)

#### Multiple Axes

```python    
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(10,5))
fig.suptitle('Figure Title', fontsize=14, fontweight='bold')

ax = fig.add_subplot(121)
ax.set_title('\nFirst title')
ax.set_xlabel('xlabel')
ax.set_ylabel('ylabel')
plt.plot([1,2,3,4,5,6])

ax2 = fig.add_subplot(122)
ax2.set_title('\nSecond title 2')
ax2.set_xlabel('xlabel 2')
ax2.set_ylabel('ylabel 2')
plt.plot([10,20,30,40,50,60])

plt.show()
```

### Adding Text 

`text()` method places text at a specified position

```python    
import matplotlib.pyplot as plt

fig = plt.figure(1)
ax = fig.add_subplot(111)

ax.text(2, 4, 'y=x', fontsize=10)
plt.text(4, 2, 'test', fontsize=10)
plt.text(3, 4, 'Annotation', style='italic',
         bbox={'facecolor': 'red', 'alpha': 0.5, 'pad': 10})

plt.plot([1,2,3,4,5,6])
plt.show()
```

Ouput:

![](https://i.imgur.com/kkVEQQP.png)

`annotate()` highlights a particular point on a plot.

```python    
import matplotlib.pyplot as plt

x1 = np.arange(1,10,2) #[1 3 5 7 9]
y1 = np.arange(1,10,2) #[1 3 5 7 9]

fig = plt.figure(1)
ax = fig.add_subplot(111)

ax.annotate('x=3,y=3', xy=(3.5, 3), xytext=(6, 4), 
            arrowprops={'facecolor':'red'})
markers_on = [1] #mark out 2nd point – (3,3)

plt.plot(x1,y1,'-gD',markevery=markers_on)
plt.show()
```

Output:

![](https://i.imgur.com/X1tlu7j.png)

## Bar Charts

__Example 1:__

```python    
import numpy as np
import matplotlib.pyplot as plt

teams = np.arange(3)
scores = (20, 35, 30)
width = 0.35
xlabels = ('Team 1', 'Team 2', 'Team 3')

plt.bar(teams, scores, width, color='#d62728')

plt.ylabel('Scores')
plt.title('Scores by Team')

plt.xticks(teams, xlabels)
plt.yticks(np.arange(0, 50, 10))

plt.show()
```

Output:

![](https://i.imgur.com/92QJGCW.png)

__Example 2:__

```python
x_labels = ["Test 1", "Test 2", "Test 3"]
mary = [75,89,93]
john = [67,69,73]
jack = [87,77,70]

fig,ax = plt.subplots()
fig.set_facecolor("lightblue")

ax.bar(np.arange(3)-0.2,mary,label="mary",width=0.2, color='r')
ax.bar(np.arange(3),john,label="john",width=0.2, color='g')
ax.bar(np.arange(3)+0.2,jack,label="jack",width=0.2, color='b')

ax.set_xticks(np.arange(3))
ax.set_xticklabels(x_labels, rotation=45)

legend = ax.legend(loc=‘upper left', shadow=True)
plt.ylim(0,120)
plt.yticks(np.arange(0, 110, 10))
plt.show()
```

Output:

![](https://i.imgur.com/9hgfcZP.png)

Reference: [matplotlib.pyplot.bar](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.bar.html)

## Pie Charts

__Example 1:__

```python   
import matplotlib.pyplot as plt

# Slices are ordered, anti-clockwise
labels = 'Frogs', 'Hogs', 'Dogs', 'Logs'
sizes = [15, 30, 45, 10]
explode = (0, 0.1, 0, 0) # Explode 2nd

fig1, ax1 = plt.subplots()
ax1.pie(sizes, explode=explode, labels=labels, autopct='%1.1f%%',
        shadow=True, startangle=90)

# Eq aspect ratio draws pie as circle
ax1.axis('equal')
plt.show()
```

Output:

![](https://i.imgur.com/ajQFPn8.png)


___Example 2:__

```python    
import numpy as np
import matplotlib.pyplot as plt

data = np.genfromtxt('data/data.csv', dtype=['i4','U50','i8'], 
                      delimiter=",", names=True)

# Extract rows containing 1965 only
data_1965 = data[data['year']==1965]

# Extract rows containing required keywords only
data_ethnic = data_1965[np.isin(data_1965['level_1'], ['Total Chinese', 'Total Malays', 'Total Indians', 'Other Ethnic Groups (Total)'])]

labels = data_ethnic['level_1']
values = data_ethnic['value']

colors = ['#FFA500', '#2CCDBD', '#CD2C7D', '#057F4A']
explode = (0.1, 0, 0, 0)
plt.figure(figsize=(5,5))
plt.pie(values, labels=labels, colors=colors, autopct='%1.1f%%')
 
plt.show()
```

Output:

![](https://i.imgur.com/Oy6dvTq.png)

Reference: [matplotlib.pyplot.pie](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pie.html)

## Histograms

__Example 1:__

```python   
# This histogram displays a count of 1000 randomly generated numbers
import numpy as np
import matplotlib.pyplot as plt

#generates normally distributed numbers
gaussian_numbers = np.random.randn(1000)
plt.hist(gaussian_numbers, bins=5)

plt.title("Gaussian Histogram")
plt.xlabel("Value")
plt.ylabel("Frequency")

plt.show()
```

Output:

![](https://i.imgur.com/aXAWITb.png)

__Example 2:__

```python    
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure()

x = 200 + 25 * np.random.randn(1000)
y = 150 + 25 * np.random.randn(1000)
n, bins, patches = plt.hist([x, y], color=['red','blue'])

plt.show()
```

Output:

![](https://i.imgur.com/Hrfhh3z.png)

References: [numpy.random.randn](https://numpy.org/doc/stable/reference/random/generated/numpy.random.randn.html), [matplotlib.pyplot.hist](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.hist.html)

## Scatter Plots

__Example 1:__

```python   
import numpy as np
import matplotlib.pyplot as plt

x = np.random.randn(100)
y = np.random.randn(100)

plt.scatter(x,y)
plt.show()
```

Output:

![](https://i.imgur.com/dJaBped.png)

__Example 2:__

```python    
import numpy as np
import matplotlib.pyplot as plt

data = np.genfromtxt("data/icecream.csv", 
		dtype=['f4', 'i4'], delimiter=",", names=True)

# split the data into x and y arrays
x = data['Temperature']
y = data['Ice_Cream_Sales']

plt.ylabel('Ice Cream Sold')
plt.xlabel('Temperature in Celsius')

plt.scatter(x,y)
plt.show()
```

Output:

![](https://i.imgur.com/JqrJDuA.png)

__Example 3:__

```python    
# Scatter Plot w/ Regression
import matplotlib.pyplot as plt

plt.ylabel('Ice Cream Sold')
plt.xlabel('Temperature in Celsius')

plt.scatter(x,y)

# add best fit line
m,b = np.polyfit(x, y, deg=1)
plt.plot(x, m*x + b, 'r-')

plt.show()
```

Output:

![](https://i.imgur.com/i9LQesb.png)

Reference: [matplotlib.pyplot.scatter](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html)

## Box Plots

__Example 1:__

```python    
# creating a box-plot that shows the median
# number of hours 6 students sleep in a week

import matplotlib.pyplot as plt
import numpy as np

# No.hours 6 students sleep in a week
data = np.array([(8,5,7,3,4,5,9),
                 (6,5,6,8,8,8,6), 
                 (4,5,7,6,6,7,9), 
                 (3,5,7,8,8,7,6), 
                 (3,6,7,7,7,6,6),
                 (8,7,6,6,7,7,9)])
labels = np.array(['Sun','Mon','Tue',
		'Wed','Thu','Fri','Sat'])

plt.boxplot(data,labels=labels)
plt.show()
```

Output:

![](https://i.imgur.com/xI30qf4.png)

__Example 2:__

```python   
import matplotlib.pyplot as plt
import numpy as np

data = np.array([(90,80,70),
                 (83,74,65),
                 (66,85,60),
                 (75,72,69),
                 (88,78,77)])
labels = np.array(['Math','English','Science'])

bplot1 = plt.boxplot(data,labels=labels, vert=False, patch_artist=True)
bplot1['boxes'][0].set_facecolor('pink')
bplot1['boxes'][1].set_facecolor('lightgreen')
bplot1['boxes'][2].set_facecolor('lightyellow')

plt.show()
```

Output:

![](https://i.imgur.com/jJiysf4.png)

__Example 3:__

```python  
import matplotlib.pyplot as plt
import numpy as np

# overlay numeric value of median and outliers in a boxplot
data = np.array([(90,80,70),
                 (83,74,65),
                 (66,85,60),
                 (75,72,69),
                 (88,78,77)])

labels = np.array(['Math','English','Science'])

bplot = plt.boxplot(data,labels=labels,
 	patch_artist=True, vert=False)

plt.show()
```

Output:

![](https://i.imgur.com/SmOj1zc.png)


```python    
import matplotlib.pyplot as plt
import numpy as np

# numeric value of medians
data = np.array([(90,80,70),
                 (83,74,65),
                 (66,85,60),
                 (75,72,69),
                 (88,78,77)])
labels = np.array(['Math','English','Science'])

bplot = plt.boxplot(data,labels=labels, vert=False)

for line in bplot['medians']:
    # get position data for top of median line
    x, y = line.get_xydata()[1]
    # overlay median value based on position value x,y
    plt.text(x, y+0.05, f'Median:{x:.1f}')
    
plt.show()
```

Output:

![](https://i.imgur.com/P1W0BF5.png)

```python    
import matplotlib.pyplot as plt
import numpy as np

# numeric value of outliers
labels = np.array(['Math', 'English', 'Science'])
data = np.array([(90,80,70),(83,74,65),(66,85,60),(75,72,69),(88,78,77),(60,60,100)])
bplot = plt.boxplot(data,labels=labels, vert=False)

fliers = []
for line in bplot['fliers']:
    ndarray = line.get_xydata()
    if (len(ndarray)>0): # will be 0 when no fliers
       max_flier = ndarray[:,0].max()
       max_flier_index = ndarray[:,0].argmax()
       x = ndarray[max_flier_index,0] #where to plot the flier text in x position
       y = ndarray[max_flier_index,1] #where to plot the flier text in y position      
 	
	plt.text(x,y+0.08,f'Flier:{max_flier}', horizontalalignment='center',
		fontsize=10,color='green')

plt.show()
```

Output:

![](https://i.imgur.com/GCiROEO.png)

Reference: [matplotlib.pyplot.boxplot](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.boxplot.html)

## Display Images

## Interactive Charts

