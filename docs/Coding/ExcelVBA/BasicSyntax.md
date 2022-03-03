[Excel Learning](../ExcelVBA.md)  

# All basic Syntax

## variable declaration
use dim for declaring simple variable. 
```vba
Dim x As Integer
Dim y as String
Dim x As Double
Dim continue As Boolean
```
**Array** Declaration. 
These are example of integer and string array. 
```vba
Dim x() As Integer
Dim y() as String
```

## boolean operation  
use and /or for doing the boolean operation. 
```vba
If LWebsite = "TechOnTheNet.com" And LPages <= 10 Then
   LBandwidth = "Low"
ElseIf LWebsite = “google.com“ or LWebsite = “facebook.com“ 
   LBandwidth = "High"
End If

```
## String manipulation  
There are lot of ways to manipulate string here are some example commonly used functions. 
```vba
Left(“Hello”,2)  'He
Right(“hello”,2) ' lo
Mid(“hello”,2,3) ' ell
Split(“hello world”) ' {“hello” , “world”}
Split(“Hi hello-world”, “-”) ' {“Hi hello”,”world”}
Split(“A;B;C;D”, ”;” , 3) ' {“A”,”B”,”CD”}
dim x() as string
x = Split(“A;B;C;D”, ”;” , 3) 
' x(0), x(1), x(2) to access splited data. 
CStr(1) 
  ' this converts number to string. 
CInt("1")  
  ' This converts Integer to string

```
## Date manipulation
[dateadd help](https://www.techonthenet.com/excel/formulas/dateadd.php)

```vba
Date()  
  ' current date
isDate(datestring)  
  ' true if date  
DateSerial(year,month,day)   
  ' y/m/d as numeric  
DateAdd(interval , number , date) 
DateAdd("yyyy", 3, "22/11/2003")  
  ' Result: '22/11/2006'  
DateAdd("q", 2, "22/11/2003")  
  ' Result: '22/05/2004'  
DateAdd("m", 5, "22/11/2003")  
  ' Result: '22/04/2004'  
DateAdd("n", 51, "22/11/2003 10:31:58 AM")  
  ' Result: '22/11/2003 11:22:58 AM'  
DateAdd("yyyy", -1, "22/11/2003")  
  '  Result: '22/11/2002‘

```

## environ var
``` Environ(1) ``` or ``` Environ("varname")  ``` can be used to get the variables. 

## If Else statement  
This is a simple example of if else statement in vba. we can have only if  or if else or if elseif else in the code. 

```vba
IF
If a=1 Then 
debug.print “a=1”
ElseIf a=2 Then
debug.print “a=2”
Else 
debug.print “a is something else”
End If
```



## for Loop variations 
Few example shown here.   
1) This is for 1 increment. There is a loop counter.  
```vba
Dim LCounter As Integer
For LCounter = 1 To 5
   MsgBox (LCounter)
Next LCounter
```
2) This is for a custom increment here it is for 5 increment. 
```vba
For LCounter = 50 To 30 Step -5
     MsgBox LCounter
Next LCounter
```
3) This is for iterating over an array or group. 
```vba
For Each p In arrofpath
	Debug.print p
Next

```
4) Do while type loop  
```vba
Do
  ' do something and wait for x = ""
Loop Until x = “”
```

## File Handling

example of creating and writing data to a external file. 
```vba
Dim MyIndex, FileNumber
For MyIndex = 1 To 5 
FileNumber = FreeFile 
    Open "TEST" & MyIndex For Output As #FileNumber
    Write #FileNumber, "This is a sample." 
    Close #FileNumber    
Next MyIndex
```

## Function / Sub
1) functions in vba is defined as below. the return value is assigned with same as function name. and type is defined after parenthesis. 
```vba
Function Area(x As Double, y As Double) As Double
  Area = x * y
End Function
```
2) sub in vba. it can not return any value. 
```vba
Sub Area(x As Double, y As Double)
  MsgBox x * y
End Sub
```

## Input Box
Input box can be used to get the user input. 
```vba
Dim Message, Title, Default, MyValue
Message = "Enter a value between 1 and 3"    ' Set prompt.
Title = "InputBox Demo"    ' Set title.
Default = "1"    ' Set default.
' Display message, title, and default value.
MyValue = InputBox(Message, Title, Default)
' Use Helpfile and context. The Help button is added automatically.
MyValue = InputBox(Message, Title, , , , "DEMO.HLP", 10)
' Display dialog box at position 100, 100.
MyValue = InputBox(Message, Title, Default, 100, 100)
```
[Excel Learning](../ExcelVBA.md)  