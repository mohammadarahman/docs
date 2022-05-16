##  Lineear Regression with Multiple Variables  



#### submit excercise:  

    atikeee@gmail.com  Token: 6W93QGQNuON0HLAY  


#### learn octave  

    operatore|meaning
    --|--
    ~=|not equal
    &&| and
    /|/|| or


generate a matrics    
 ```
a = [1 2; 3,4]
a =

   1   2
   3   4
 
 ```
 
 generate matrics and some basic commands  
 ```
 a = ones(2,3)  
 a = 2*ones(3,4)  
 a = zeros(1,3)  
 w = rand(3,3)  % everytime it will generate diff result. 
 w = randn(1,3) 
 I = eye(4) % 4x4 identity matrix. 
 size(a)   % returns size as a matrics.
 size (a,1) % show row
 size (a,2) % show column. 
 load filename.ext % this will load a file. this will save the data to a matrics with the filename without ext
 save filename.ext var % save var to a file
 who % shows list of vars. 
 whos % same as who with size and more info
 clear x % remove x var from the workspace. 
 A(2,:) % second row
 A(:,2) % second col
 A(2,3) % one element
 A([1,3],:) % first and 3rd row. 
 A(:,2) = (10; 11; 12]
 A = [A,[20; 21; 22]] % semicolon basically indicates next line. 
 A(:) % put all element in one vector
 help eye
 ```
 
 
 
 show histogram
 ```
 hist(w)
 hist(w,3)
 ```
 
Show different operations 
```
A .^2  % element wise power
log(v) % element wise log
exp(v)
abs(v) 
A' % transpose
a<3 % compare element wise comparison and return a 0/1 matrix
find(a<3) % return matr with conditions returns true. 
magic(3) % row column add to same value. 
help find % it could be useful. 
sum(a)
prod(a)
floor(a)
ceil(a)
max()
max(a,[],1) %row max
max(a,[],2) %col max
```

control statement
```
ind = 1:10
% for loop 
for i= ind,

for i = 1:10,
    disp(i);
end;
% while loop
while i<=5,
    v(i) =100;
    i=i+1;
end; 
%if statement
if i==6,
break;
end;

```
 
function  

for function need a file created to filesystem.   
this file will start with the line function keyword , function name and parameter.   
function name has to be matched with filename. extension will be functionName.m  
file should be available in the path.  addpath('c:\test') should be used to add a path for functions  

example file  square.m
```
function y = square(x)
y = x^2;
```  
another example  square_cube.m
```
function [y1,y2] = square_cube(x)  
y1 = x^2; 
y2 = x^3; 
```  
 
 
 