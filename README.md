# Advanced-Numpy-CheatSheet---From-Beginner-to-Pro


**What is Numpy?**

Numpy is a Python library for creating n-dimensional arrays.

**Why to use Numpy?**

Numpy structure look similar to standard Python lists but Numpy arrays are more efficient e.g.
1. Its broadcasting capabilities are extremely useful for quickly applying functions to any dataset.
2.  It has alot of built-in features like linear algebra, statistical distribution, trignometry and random numbers handling capabilities.

**How many methods are there to create Numpy arrays?**

There are three methods for it: 

1. Getting Numpy arrays by transforming python lists to arrays
2. Getting Numpy arrays by using builtin function
3. Getting Numpy arrays by generating random data in whatever shape you want

**Method-1:**
"""
import numpy as np

## 1D Numpy Array : Vector
mylist = [1,2,3]  # creating the list
** transforming the mylist to numpy array as below
np.array(mylist)

#directly writing mylist into np.array() function gives same result
np.array([1,2,3])

## 2D Numpy Array: Matrix 
mymatrix = [[1,2,3], [5,6,7], [8,9,10]]
np.array(mymatrix)

#directly writing 2D list(matrix) into np.array() function gives same result
np.array([[1,2,3], [5,6,7], [8,9,10]])

"""**Method-2:**

**1. Using arange function:**

**Syntax:** np.arange(start, stop, step)

**Nota bene:** 'Stop' number is not included in result
"""

np.arange(0, 10, 1)

np.arange(0, 10, 2)

"""

**2. Producing array of zeros and ones with np.zeros and np.ones function:**

**Syntax:** 
1. np.zeros(shape) 
2. np.ones(shape)

**Nota bene:** Shape = ((Number of rows, Number of columns)) : must have double brackets"""

np.zeros(5) # To get 1D array, Shape = Number of zeros needed in 1D array

np.zeros((4,5))   # Shape = (4,5) = (4 rows, 5 columns)

np.ones(5)

np.ones((4,5))

"""**3. Using linspace function:**

It gives n number of evenly spaced numbers in range min_limit to max_limit

**Syntax:** np.linspace(min_limit**,** max_limit**,** n)

**Nota bene:** 'max_limit' number is included in result
"""

np.linspace(0,10,3)

np.linspace(0,10,11)

"""**4. Using eye function to get identity matrix:**

**Syntax:** np.eye(shape)

**Nota bene:** Shape = (n) : Number of rows = n and number of columns = n
"""

np.eye(5)

"""**Method-3:**

**1. Using np.random.rand() function:**

**Syntax:** np.random.rand(shape)

**Nota bene:** 
1. Shape = ((Number of rows, Number of columns)) : must have double brackets
2. All generated numbers lie between 0 & 1
"""

np.random.rand(5) # To get 1D array of random numbers, Shape = Number of random integers needed in 1D array

np.random.rand(4,5)

"""**2. Using np.random.randn() function:**

It gives standard normally distributed random integers. It means that the variance of all produced random inetgers = 1 and mean = 1.

**Syntax:** np.random.randn(shape)

**Nota bene:** 
1. Shape = (Number of rows, Number of columns)
2. All generated random numbers lie between -1 & 1 (because we can have mean = 0 only if we have negative numbers with positive numbers to give us 0 sum so thats why limit is -1 to +1)
"""

np.random.randn(10)

np.random.randn(4,5)

"""**2. Using np.random.randint() function:**


**Syntax:** np.random.randint(min_limit, max_limit, shape)

**Nota bene:** 
1. Shape = (Number of rows, Number of columns) for 2D
2. 'max_limit' number is not included in result
3. It works like np.linspace(min_limit, max_limit, shape) but the only difference is: we can give shape like (3,4) etc. in np.random.randint to generate 2D arrays but not in np.linspace. The np.linspace just needs one number as a shape and always produces 1D array.
"""

np.random.randint(0, 10, 4) # To get 1D array of random integers, Shape = Number of random numbers needed in 1D array

np.random.randint(0, 10, (2,3))

"""**Why we need to use seed in numpy?**

The seed is used to set a random state so that the random results can actually be reproduced. Every time we give it the same seed, it generates the same numbers.
"""

np.random.seed(42)
np.random.rand(5)

# Reproducing the same result
np.random.seed(42)
np.random.rand(5)

"""**Nota bene:**
1. Never forget to write *np.random.seed(42)* on top each time you want to reproduce the result
2. 42 is default number in python to use as seed because it was mentioned in book 'Hitchhiker's Guide to the Galaxy' of python. you can use number '101' etc. also.

## **Useful Attributes and Methods calls in Numpy:**
"""

firstarray = np.arange(0,25) # here step = 1. By default, step = 1 so not mentioning doesn't make any difference.
print(firstarray)

firstarray.reshape(5,5)

second_array = np.arange(1,40,2)
second_array.reshape(5,4)

"""**Reshaping into wrong dimensions ---> It will raise error**"""

# reshaping into wrong dimensionality will raise error. For example, for above example, myarray.reshape(4,5) will raise error as 4 x 5 != 25

firstarray.reshape(4,5)

# to get maximum number from array
firstarray.max()

# to get minimum number from array
firstarray.min()

# to get index of maximum number from array
firstarray.argmax()

# to get index of minimum number from array
firstarray.argmin()

# to check data type of elements in array
firstarray.dtype

# to check data type of array: to check if the array is a list or its a numpy array?
type(firstarray)

# to check shape of the array
firstarray.shape

"""**Nota bene:** (25,) and (25,1) are different.

*   (25,) means 25 columns and 1 row
*   (25,1) means 25 rows and 1 column


"""

np.random.rand(5,)

np.random.rand(5,1)

# Indexing
firstarray[2]

# Slicing
firstarray[1:3]

firstarray[:4]

firstarray[3:]

"""## **Broadcasting:**

Numpy is different from the normal Python list due to its ability of broadcasting. We can broadcast a single value across a larger set of values in numpy.
"""

firstarray[0:5]

firstarray[0:5] = 100

firstarray

"""Hurrah ! Broadcasting worked !!! We can't do this with normal python lists. This is called **broadcasting reassignment**.

## ** ---- Hold on (0_0) ----**
What if we just want to take slice of array and do operations on that but not on original array?

Solution ---> Use .copy() method. Don't copy directly like did above, in case you don't want to modify your original array. If we do it directly like above, it doesn't copy the array. It just creates a pointer to the original array.
"""

array_copy = firstarray.copy()
array_copy[:] = 90
print(array_copy)

firstarray

"""## **Conditional Selection:**"""

myarray = np.arange(1,11)
print(myarray)

# to check the values greater than 4 in the array
myarray > 4

# to get the actual values of array instead of booleans
myarray[myarray > 4]

"""## **Numpy Operations:**"""

lastarray = np.arange(0,10)
print(lastarray)

# adding same number in all elements of array
lastarray + 5

lastarray - 2

lastarray * lastarray

lastarray / lastarray

"""We just caught **nan** value in case of diving array. So, just few things to remember, in Numpy:

1. 0/0 = nan
2. scalar / 0 = inf (infinity) 

Example is below to test:
"""

lastarray / 0

# to take sqaure root of all values
np.sqrt(lastarray)

np.log(lastarray) # log(0) = -inf (in Numpy)

lastarray.sum()

lastarray.mean()

# To get sum of all rows in 2D Array in Numpy:

last2darray = np.random.randint(0,20,(4,5))
print(last2darray)

last2darray.sum(axis=0)     # 4 + 16 + 17 + 2 = 39 and so on. (summing first element of each row which gives us first element of our result)

last2darray.sum(axis=1)     # 4 + 10 + 15 + 0 + 4 = 33 and so on. (summing first element of each column which gives us first element of our result)

"""## **Hope you enjoyed both flavours of Numpy: vectors (1D) and Arrays (nD)**

Keep it to your computer to use it for any Numpy related functions. Thanks.  
"""
