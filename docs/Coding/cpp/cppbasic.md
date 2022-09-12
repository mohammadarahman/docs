# C++ basic tutorial

## Pre processor directive  

define, undef, include, if, ifdef, ifndef, else, elif, elifdef, elifndef  
endif, line, error, pragma  

Source file translation.  
	- Conditionality:  #if, #ifdef, #ifndef, #else, #elif, #elifdef, #elifndef (since C++23), and #endif  
	- replace: #undef #define  
	- include: #include other files. 

The following preprocessor can be controlled  
	implementation defined: #pragma  
	file and line information: #line  
	
###define  

	it is towrite macro.  
	multiline macro can be written using \ at the end;  
	even semicolon can be put in macro then using that will not require semicolon  
	it just replace the word with whatever defined in #define.  
	define sum(num1,num2) num1+num2; this works too. with two para  
	
###if endif elif else  

	in main if endif can change the code compilation based on condition  
	some unncessary compilation will be not compiled  
	
### ifdef endif else  

	if not defined -> ifndef  
	if defined -> ifdef  
	even code error will be ignored if condition doesnt matche.  
	
### undef  

this is just undefining previous defined macro.  

### line  

	__LINE__  current line number.  
	__FILE__ current file name  
	__DATE__ when the program was compiled  
	__TIME__ compile time  
	line 100 "text.txt"  
	this will change file and line number  