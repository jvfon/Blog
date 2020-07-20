# Liquid Baiscs

## Contents
[Creating a variable](#Creating-a-variable)  
[Types](#Types)  
[Filters](#Filters)  
[Math](#Math)   
[Comments](#Comments)  
[Control flow](#Control-flow)  



On VS Code open any theme folder. Go to "layout" folder and open the file: theme.liquid.  

Comment out everything that is inside the body tag, hit ctrl + /.  

## Creating a variable

Start with {%, to close use %}.  

ex:   
```{% assign variable = "Hello World" %}```

to out put type:  
```{{variable}}```

You can modify the output to show h1 size font:  
```<h1>{{variable}}</h1>```

You don't have to use the word "variable" to create a variable.  
```{% assign line = "Hello" %}```
```{% assign name = "Jose" %}```

```<h1>{{line}} {{name}}</h1>```

## Types

You can use strings:  
```{% assign line = "Hello" %}```
```{% assign name = "Jose" %}```

```<h1>{{line}} {{name}}</h1>```

Numbers:  
```{% assign line = "Hello" %}```
```{% assign name = 22 %}```

```<h1>{{line}} {{name}}</h1>```

Floats:  
```{% assign line = "Hello" %}```
```{% assign name = 32.58 %}```

```<h1>{{line}} {{name}}</h1>```

Booleans:  
```{% assign line = "Hello" %}```
```{% assign name = true %}```

```<h1>{{line}} {{name}}</h1>```

Nill:  
```{% assign line = "Hello" %}```
```{% assign name = nill %}```

```<h1>{{line}} {{name}}</h1>```

Arrays:  
Use a filter to split contents inside an array.  
```{% assign line = "Hello" %}```
```{% assign name = "Jose, Bill, Lucho" | split: ', '%}```

Access each name by its index number
```<h1>{{line}} {{name[1]}}</h1>```

## Filters
Check: https://shopify.dev/docs/themes/liquid/reference/filters

A pipe "|" is used to tell when a filter is going to be used.  

ex:  Take the 3rd value from the array and add the dollar "$" symbol.  
```{% assign name = "Jose, Bill, Lucho, 2500, 78, 69" | split: ', '%}```
```<h1>{{line}} {{name[3] | money}}</h1>```

The output will be $25.00. If you use "25", the output will be $0.25.  

## Math  

```{% assign number= 2 | plus: 2 %}```

```<h2>{{number}}</h2>```

ex: represent (( 2 + 2 ) * (4 + 5))  
```{% assign number= 2 | plus: 2 %}```
```{% assign numberb= 4 | plus: 5 %}```
```{% assign number= number | times: numberb %}```

```<h2>{{number}}</h2>```

## Comments

Start a comment with: {% comment %}
End a comment with: {% end comment}  

## Control flow

Truthy is almost everythiing.  

Falsy are false and nil.  
&nbsp;    

```{% if 5 %}```
```<h1>Showing Products</h1>```
```{% endif %}```

The h1 tag content will show.
&nbsp;  

```{% if false %}```
```<h1>Showing Products</h1>```
```{% endif %}```  
The h1 tag content won't show.  
&nbsp;  

If the value is true, show it if not don't show it.  
```{% if assign = false %}```
```{% if value %}```
```<h1>Showing Products</h1>```
```{% endif %}```  
In this case h1 won't show. If you change assign = true, then h1 will show.  
&nbsp;   

```{% if assign = false %}```
```{% if value %}```
```<h1>Showing Products</h1>```
```
```{% endif %}```  





