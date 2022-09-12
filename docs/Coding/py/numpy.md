# NUMPY learning. 

## Code and explaination. 

```python 
# import the lib
import numpy as np

#generate a 2D array. 
a = np.arange(15).reshape(3, 5)

# get the array size
a.shape  

# create object from array
a.array([1,2,3,4])

#can be reshaped again size and dimension must be matched. 
b=a.reshape(2,2) 

#make zero matrix
np.zeros(3,4)

#making 1 matrics
np.ones(3,4)

#making empty
np.empty(4,5)  

#making a list / data from start end increment
np.arange(1,10,0.5)

#add subtruct will be individual element by element
c=a+b 

#elementwise product
c = a*b

# matrix product
c=a@b

# dot product
c = a.dot(b)


#for reshape the 2D array first flatten it and resize it later. 
a= a.ravel()
a = a.reshape(n,m)


```