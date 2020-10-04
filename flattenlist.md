## How to make a flat list out of list of lists?

In Python, List of lists (or cascaded lists) resemble a two dimensional array - although Python doesn't have concept of array as in C or Java. Hence, flattening such list of lists means getting elements of sublists into a one dimensional array like list. For example, a list 

[[1,2,3],[4,5,6]] 

is flattened into 

[1,2,3,4,5,6]

This can be achieved by different techniques, each one of them is explained below:

Let the original list be:


```python
>>> nestedlist=[[1,2,3,4],["Ten","Twenty","Thirty"],[1.1,1.0E1,1+2j,20.55,3.142]]
```

Using **nested loop** to append each element of sublist in a flat list


```python
flatlist=[]
for sublist in nestedlist:
    for element in sublist:
        flatlist.append(element)
print (flatlist)
```

    [1, 2, 3, 4, 'Ten', 'Twenty', 'Thirty', 1.1, 10.0, (1+2j), 20.55, 3.142]
    

**List comprehension** technique gives same result in a single compact statement


```python
flatlist=[element for sublist in nestedlist for element in sublist]
print (flatlist)
```

    [1, 2, 3, 4, 'Ten', 'Twenty', 'Thirty', 1.1, 10.0, (1+2j), 20.55, 3.142]
    

Using **reduce()** function in **functools** module in standard library


First argument to **reduce()** function is a function itself with two arguments, and second argument is a list. Argument function is applied cummulatively to elements in the list. For example, 

reduce(lambda a,b:a+b, [1,2,3,4,5]) 

returns cummulative sum of numbers in the list


```python
from functools import reduce
flatlist = reduce(lambda a,b:a+b, nestedlist)
print (flatlist)
```

    [1, 2, 3, 4, 'Ten', 'Twenty', 'Thirty', 1.1, 10.0, (1+2j), 20.55, 3.142]
    

Recall that + symbol is defined as concatenation operator for sequence data types (list, tuple and string). Instead of a lambda function we can also use concat() function defined in **operator** module as argument to cummulatively append the sublists to flatten.


```python
from functools import reduce
from operator import concat
flatlist = reduce(concat, nestedlist)
print (flatlist)
```

    [1, 2, 3, 4, 'Ten', 'Twenty', 'Thirty', 1.1, 10.0, (1+2j), 20.55, 3.142]
    


```python

```
