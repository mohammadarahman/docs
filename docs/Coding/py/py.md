# Basic questions  

1. **what is lambda function?**  
	in line function  
	`x= lambda a,b: a*b`  
1. **built in data types in python**  
	- text  
	- number
	- list
	- dict
	- set 
	- bool 
	- bytes
1. **DICTIONARY**  
	note : no comma at last items
```python 
	dict = {"a":10, "b":20}   
	for x in dict #here x is key only.  
	for x in dict.keys() #key  
	for x in dict.values() # values  
	for x,y in dict.items() # key values
```  
	for copy `newdict = thisdict.copy` or `newdict = dict(thisdict)`  
1. **try except**  
```python 
	try:  
		print("Hello")  
	except:  
		print("Something went wrong")  
	else:  
		print("Nothing went wrong")
```  
	here else will be executed if except doesnt execute.   
	try except finally can be used too finally will execute no matter exception occurs or not  
	raise can be used for throwing exception.   
	Examples: ```python raise Exception("Sorry, no numbers below zero")   
	raise TypeError("Only integers are allowed")```  
1. **Input**  
	`myinput = input()` pythong 2.7 uses raw_input.   
1. **String format examples [useful]**  
```python 
txt = "The price is {} dollars for {} itmes"  
print(txt.format(10,5))  
myorder = "I want {0} pieces of item number {1} for {2:.2f} dollars."  
# 0 1 2 for index and :.2f for 2 point pafter decimal.  
myorder = "I have a {carname}, it is a {model}."  
print(myorder.format(carname = "Ford", model = "Mustang"))  
```  

1. **decorator function**
	This is basically a function inside another function. and innerfunction is returned by outer function.  
	*args and **kwargs can be used to transparently pass the argument  
	example:
	```python 
	def calculate_time(func):
		def inner1(*args,**kwargs):
			begin = time.time()
			func(*args,**kwargs)
			end = time.time()
			print("total time taken: ",func.__name__,end-begin)
		return inner1
	#usage here
	@calculate_time
	def fact(num):
		print(math.factorial(num))
	fact(100)
	```  
	chaining of decorator is also possible.  
	
1. **common mistakes**  

	`x =a or b` if a false x will be equal to b whatever it is   
	`x= a and b` if a true x will be equal to b whatever it is   

## **<font color="red">code example</font>**

#### copy file from one to other  

```python 
with open('data') as input_file, open('result', 'w') as output_file:
  for line in input_file:
    output_file.write(parse(line))
```
#### args kwargs  
	
``` python 
def myFun(*args,**kwargs):
	print("args: ", args)
	print("kwargs: ", kwargs)
myFun('geeks','for','geeks',first="Geeks",mid="for",last="Geeks")
```

## my learnings.  

[Pandas](pandas.md)  
[numpy](numpy.md)  
[scipy](scipy.md)  
	
## External links: 
[pdf cheat sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)  
[shortcuts in python](https://cheatography.com/christoph-leitner/cheat-sheets/essential-shortcuts-in-python/)  
[python lists](https://www.educba.com/list-operations-in-python/)  
