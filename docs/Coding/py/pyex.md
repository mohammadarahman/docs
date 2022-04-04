# coding example  

## print all prime between 100 200  

```python 
for num in range(100,200):
  if all(num%i!=0 for i in range(2,num)):
    print(num)
```

## sort large to small  
```python 
def sort1(l):
    sz = len(l);
    for i in range(0,sz-1):
        for j in range(i+1,sz):
            if (l[i]<l[j]):
                l[i] , l[j] = l[j],l[i]
```


## common function and usage  

```python  
#sort
list1.sort(reverse = True)  


```