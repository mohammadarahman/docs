## simple common formating  

`<strike>stike</strike>` → <strike>stike</strike>  
`<del>strile</del>` → <del>strile</del>  
`<s>strike</s>` → <s>strike</s>  
`~~strike~~` → ~~strike~~  
`~strike~` → ~strike~  
`**bold**`-> **bold**  
`__bold__` -> __bold__  
`*italic*` -> *italic*  
`***italic***` -> ***bold italic***  

## list `- a` or `* b`
- a 
* b 
- c  

# This is a Heading h1
## This is a Heading h2  (has underline no underline after h2)
###### This is a Heading h6 (is the last header)


### Ordered list
```
1. a   
1. b   
1. c   
  1. d   
  1. e 
``` 
1. a
1. b
1. c
  1. d
  1. e

## Images

`![This is a alt text.](/image/sample.png "This is a sample image.")`  
![This is a alt text.](/image/sample.png "This is a sample image.")

## Links
`[Markdown Live Preview](https://markdownlivepreview.com/)`  
[Markdown Live Preview](https://markdownlivepreview.com/).

## Blockquotes
`>`  
`>>`
> Markdown is a lightweight markup language with plain-text-formatting syntax, created in 2004 by John Gruber with Aaron Swartz.
>
>> Markdown is often used to format readme files, for writing messages in online discussion forums, and to create rich text using a plain text editor.

## Tables
```
notice the : for allignment. 
| Left columns  | Right columns |
| -:|:-:|
| left foo      | right foo     |
| left bar      | right bar     |
| left baz      | right baz     |
```
| Left columns  | Right columns |  
| -:|:-:|  
| left foo      | right foo     |  
| left bar      | right bar     |  
| left baz      | right baz     |  

```
simple example
a|b  
-|-
1|2
```
a|b  
-|-
1|2  

## Blocks of code

```
let message = 'Hello world';
alert(message);
```

## Inline code

This web site is using `markedjs/marked`.

## html contents
```
|&copy;  |&uml; |&trade;|&iexcl; |&pound;|&amp;   |&lt;    |&gt;   |&yen;   |&euro; |&reg;    |&plusmn;|&para;| 
|&brvbar;|&macr;|&laquo;|&middot;|X&sup2;|&frac34;|&frac14;|&times;|&divide;|&raquo;|15&ordm;C|&sect;  |      | 
```

|&copy;  |&uml; |&trade;|&iexcl; |&pound;|&amp;   |&lt;    |&gt;   |&yen;   |&euro; |&reg;    |&plusmn;|&para; |
|--------|------|-------|--------|-------|--------|--------|-------|--------|-------|---------|-------|--------|
|&brvbar;|&macr;|&laquo;|&middot;|X&sup2;|&frac34;|&frac14;|&times;|&divide;|&raquo;|15&ordm;C|&sect; |        |


## Escaping for Special Characters

\*literal asterisks\*

## Markdown extras

## GFM task list
```
- [x] a
- [x] b
- [ ] c
    - [ ] c1
    - [ ] c2
    - [ ] c3
- [ ] d
    - [ ] d1
    - [ ] d2
```
- [x] a
- [x] b
- [ ] c
    - [ ] c1
    - [ ] c2
    - [ ] c3
- [ ] d
    - [ ] d1
    - [ ] d2


## TeX(LaTeX)

```
$$E=mc^2$$  
Inline $$E=mc^2$$ Inline 
$$\(\sqrt{3x-1}+(1+x)^2\)$$  
$$\sin(\alpha)^{\theta}=\sum_{i=0}^{n}(x^i + \cos(f))$$  
<img src="https://render.githubusercontent.com/render/math?math=E=mc^2">  
<img src="https://render.githubusercontent.com/render/math?math=sin(\alpha)^{\theta}=\sum_{i=0}^{n}(x^i + \cos(f))">
<img src="https://render.githubusercontent.com/render/math?math=\(\sqrt{3x-1}+(1+x)^2\)">  
```
[help link](https://gist.github.com/a-rodin/fef3f543412d6e1ec5b6cf55bf197d7b)  
$$E=mc^2$$  
Inline $$E=mc^2$$ Inline，
Inline $$E=mc^2$$ Inline。
$$\(\sqrt{3x-1}+(1+x)^2\)$$  
$$\sin(\alpha)^{\theta}=\sum_{i=0}^{n}(x^i + \cos(f))$$  
<img src="https://render.githubusercontent.com/render/math?math=E=mc^2">  
<img src="https://render.githubusercontent.com/render/math?math=sin(\alpha)^{\theta}=\sum_{i=0}^{n}(x^i + \cos(f))">  
<img src="https://render.githubusercontent.com/render/math?math=\(\sqrt{3x-1}+(1+x)^2\)">  

  
### FlowChart

```flow
st=>start: Login
op=>operation: Login operation
cond=>condition: Successful Yes or No?
e=>end: To admin

st->op->cond
cond(yes)->e
cond(no)->op
```

## code block  

```python
if(x):
  print("this is x")
```  

``` ruby 
this = "Ruby Code"
puts "This is #{this}"
```  
``` javascript 
console.log('Code Tab A');
```


## Add Image
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)  
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](http://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)  



### End

