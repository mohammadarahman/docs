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
	for x in dict` #here x is key only.  
	for x in dict.keys() #key  
	for x in dict.values() # values  
	for x,y in dict.items() # key values```  
	for copy `newdict = thisdict.copy` or `newdict = dict(thisdict)`  
1. **try except**  
	```python
	try:  
		print("Hello")  
	except:  
		print("Something went wrong")  
	else:  
		print("Nothing went wrong")```  
	here else will be executed if except doesnt execute.   
	try except finally can be used too finally will execute no matter exception occurs or not  
	raise can be used for throwing exception.   
	Examples: `raise Exception("Sorry, no numbers below zero")`  
	`raise TypeError("Only integers are allowed")`  
1. **Input**
	`myinput = input()` pythong 2.7 uses raw_input.   
1. **String format examples [useful]**  
	```python
	txt = "The price is {} dollars for {} itmes"  
	print(txt.format(10,5))  
	myorder = "I want {0} pieces of item number {1} for {2:.2f} dollars."  
	# 0 1 2 for index and :.2f for 2 point pafter decimal.
	myorder = "I have a {carname}, it is a {model}."  
	print(myorder.format(carname = "Ford", model = "Mustang"))```  
1. **decorator function**
	
	
1. **code example**
	### copy file from one to other  
	```python 
	with open('data') as input_file, open('result', 'w') as output_file:
    for line in input_file:
        output_file.write(parse(line))
	```
	### 
1. **common mistakes**
	- ` x =a or b` if a false x will be equal to b whatever object it is. 
	- ` x= a and b` if a true x will be equal to b whatever it is. 
	