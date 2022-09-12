
### Variables
all the variables is as below.   
variable is **NOT** initialized to a default value.  

Type|Represents|Range|Default Value
-|-|-|-
bool|Boolean value|True or False|False
byte|8-bit unsigned integer|0 to 255|0
char|16-bit Unicode character|U +0000 to U +ffff|'\0'
decimal|128-bit precise decimal values with 28-29 significant digits|(-7.9 x 1028 to 7.9 x 1028) / 100 to 28|0.0M
double|64-bit double-precision floating point type|(+/-)5.0 x 10-324 to (+/-)1.7 x 10308|0.0D
float|32-bit single-precision floating point type|-3.4 x 1038 to + 3.4 x 1038|0.0F
int|32-bit signed integer type|-2,147,483,648 to 2,147,483,647|0
long|64-bit signed integer type|-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807|0L
sbyte|8-bit signed integer type|-128 to 127|0
short|16-bit signed integer type|-32,768 to 32,767|0
uint|32-bit unsigned integer type|0 to 4,294,967,295|0
ulong|64-bit unsigned integer type|0 to 18,446,744,073,709,551,615|0
ushort|16-bit unsigned integer type|0 to 65,535|0  

Type|Example
-|-
Integral types|sbyte, byte, short, ushort, int, uint, long, ulong, and char
Floating point types|float and double
Decimal types|decimal
Boolean types|true or false values, as assigned
Nullable types|Nullable data types

### boxing unboxing  

Boxing: assigning value to object.  
check the use of dynamic
    any type of value can be put into dynamic.  
    c# has the pointers similar to c++  
    
```cs 
object obj;
obj =100; 
```

### the ? operator  

```Exp1? exp2 : exp3;```  
if exp1 is truee exp get evaluated  

### new operator  

object creation requires new operator.  
in c++ only for pointer new is used whereas in c# object creation for any class requires new.  


### Passing parameters in  (ref in c# vs c++)  

1. There are 3 techniques  
    a. pass by value  
        1. just regular use of passing parameters.  
    b. pass by reference.  
        1. it requires ref before the parameters  
        2. calling requires the same too.  
        3. example : public void swap(ref int x, ref int y) {  
        4. example calling: n.swap(ref a, ref b)  
    c. pass by out  
        1. its very similar but see the difference below.  
        
**Note:** Both ref and out parameter treated same at compile-time but different at run-time.  
ref keyword|out keyword
-|-
It is necessary the parameters should initialize before it pass to ref.|It is not necessary to initialize parameters before it pass to out.
It is not necessary to initialize the value of a parameter before returning to the calling method.|It is necessary to initialize the value of a parameter before returning to the calling method.
The passing of value through ref parameter is useful when the called method also need to change the value of passed parameter.|The declaring of parameter through out parameter is useful when a method return multiple values.
When ref keyword is used the data may pass in bi-directional.|When out keyword is used the data only passed in unidirectional.

### nullable.  

it is to create an opportunity to make a variable to null; 

```cs 
< data_type> ? <variable_name> = null;
int? num1 = null;  
```  

### array  

```cs 
double[] balance = new double[10];  
double[] balance = { 2340.0, 4523.69, 3421.0};  
int [] marks = new int[5]  { 99,  98, 92, 97, 95};
// two dimensional array
string [,] names;
//initialize
int [,] a = new int [3,4] {
   {0, 1, 2, 3} ,   /*  initializers for row indexed by 0 */
   {4, 5, 6, 7} ,   /*  initializers for row indexed by 1 */
   {8, 9, 10, 11}   /*  initializers for row indexed by 2 */
};
// 3 d array
int[,,]m;
// for passing para with array
average(int[] nums,int count){
}
```
	params array  
	this is used to pass multiple parameters as array.  
```cs 
public int AddElements(params int[] arr) {  //define
int sum = app.AddElements(512, 720, 250, 567, 889); //call
```
	string = char[]  
	string array  
```cs 
char []letters= { 'H', 'e', 'l', 'l','o' };
string [] sarray={ "Hello", "From", "Tutorials", "Point" };
```
	Array class  
	The Array class is the base class for all the arrays in C#. It is defined in the System namespace. The Array class provides various properties and methods to work with arrays.  
	Properties: IsFixedSize IsReadOnly Length LongLength Rank  
	Methods:  Clear Copy(Array,Array,int32)  CopyTo(Array, Int32) Sort(Array) ToString() Reverse(Array)  
	Jugged array is the mixed dimensional array. 

### struct  

	struct can be used same as c++  
	it can have methods  
	structs doesnt have inheritance  
	can not have default constructor  
	create a object requires new keyword  
``` cs 
struct Books {
   public string title;
   public string author;
   public string subject;
   public int book_id;
};  
 Books b = new Books();
```

### enum 
```cs 
enum <enum_name> {
   enumeration list 
};
enum Days { Sun, Mon, tue, Wed, thu, Fri, Sat };
//uses like this
// (int)Days.Mon = 1
```