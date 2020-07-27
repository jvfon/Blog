# Liquid Baiscs

## Contents
[Creating a variable](#Creating-a-variable)  
[Types](#Types)  
[Filters](#Filters)  
[Math](#Math)   
[Comments](#Comments)  
[Control flow](#Control-flow)   
[If statment](#If-statment)   
[Else statement](#Else-statement)  
[Elsif](#Elsif)  
[Case](#Case)  
[Loops](#Loops)  




On VS Code open any theme folder. Go to "layout" folder and open the file: theme.liquid.  

Comment out everything that is inside the body tag, hit ctrl + /.  

## Creating a variable

Start with ```{%```, to close use ```%}```.  

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

### If statment  
If the value is true, show it if not don't show it.  
```
{% if assign = false %}
{% if value %}
<h1>Showing Products</h1>
{% endif %}
```
In this case h1 won't show. If you change assign = true, then h1 will show.  
&nbsp;   

### Else statement 
```
{% assign value = true %}
{% if value %}
<h1>Showing Products</h1>
{% else %}
<h1>Not Showing Products</h1>
{% endif %}
```  
"Showing Products" will show if you assign = true.  
"Not Showing Products" will show if assign = false.
&nbsp;   

```
{% assign value = 2 %}  
{% if value == 2%}
<h1>2</h1>
{% else %}
<h1>Not 2</h1>
{% endif %}
```  
"Showing Products" will show if you assign = 2 
"Not Showing Products" will show if assign = false.
&nbsp;   

## Elsif

```
{% assign value = 3 %}  
{% if value == 2 %}
<h1>Showing 2 Products</h1>

{% elsif value == 3 %}  
<h1>Showing 3 Products</h1>  
{% Not Showing %}   
{% endif %}   
``` 
"Showing 2 Products" will show if you assign = 2  
"Showing 3 Products" will show if assign = 3.  
&nbsp;  

If it is not equal to what we are asking for, then show the product(s).
```
{% assign value = 3 %}  
{% unless value == 2 %}
<h1>Showing Products</h1>
{% endunless %}  
```
When both values are different ```<h1>``` will show. 
&nbsp;  

# Case
```
{% assign value = "Jose" %}  
{% case value %}
   {% when "Bill" %}
      <h1>Hey Bill</h1>
   {% when "Jose" %}
      <h1>Hey Jose</h1>
   {% when "Tom" %}
      <h1>Hey Tom</h1>
   {% else %}
      <h1>I don't know you</h1>
   {% endcase %}
```
Depending on what the value is equal to, the program will output a string.  

## Loops

```
{% assign names = "Tim, Lucas, Madison" | split: ", " %}
{% for name in names %}
   {{ names }}
{% endfor %}
```  
"name" is a temporary variable. You can use any string. 

### UL
```
{% assign names = "Tim, Lucas, Madison" | split: ", " %}
<ul>
{% for name in names %}
<li>{{ names }}</li>
{% endfor %}
</ul>
```  
Creates a list with all the names.  

### else

```
{% assign names = "", " %}
<ul>
{% for name in names %}
<li>{{ name }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
```  
If the array has no names, it outputs: "Sorry no names available."
&nbsp;

To limit the amount of names displayed use "limit".  
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for name in names limit: 2 %}
<li>{{ name }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
```  
&nbsp;

To skip a few names use "offset".  
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for name in names offset: 2 %}
<li>{{ name }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
```  
&nbsp;

To reverse the order of the names use "reversed".  
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for name in names reversed %}
<li>{{ name }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
```
&nbsp;

To print from a certain number to a certain number pass an range instead of an array. The second ```<ul>``` will print numbers.     
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for x in names offset: 2 %}
<li>{{ x }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
<ul>
{% for x in (1..10) %}
<li>{{ x }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
```    
&nbsp;

The second ```<ul>``` working with an array. Pass the name of the array and let i = to an index number
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for x in names offset: 2 %}
<li>{{ x }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
<ul>
{% for i in (0..5) %}
<li>{{ names[i] }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
``` 
&nbsp;

Break the loop, once it reaches a certain index, stop the loop.  
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for x in names offset: 2 %}
<li>{{ x }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
<ul>
{% for i in (0..5) %}
   {% if i == 3 %}
      {% break %}
   {% else %}   
      <li>{{ names[i] }}</li>
{% endif %}
{% endfor %}
</ul>
``` 
&nbsp;

To skip an index, use "continue". The 4rth name will be skipped.  
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for x in names offset: 2 %}
<li>{{ x }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
<ul>
{% for i in (0..5) %}
   {% if i == 3 %}
      {% continue %}
   {% else %}   
      <li>{{ names[i] }}</li>
{% endif %}
{% endfor %}
</ul>
``` 
&nbsp;

Assign a number within the range that can be a variable.  
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
<ul>
{% for x in names offset: 2 %}
<li>{{ x }}</li>
{% else %}
<li> Sorry no names available. </li>
{% endfor %}
</ul>
<ul>
{% assign last = 5 %}
{% for i in (0..last) %}
   {% if i == 3 %}
      {% continue %}
   {% else %}   
      <li>{{ names[i] }}</li>
{% endif %}
{% endfor %}
</ul>
``` 
&nbsp;

To skip a section of the code use "raw".  

```
{% raw %}
   code you want to skip goes here
{% endraw %}
```
&nbsp;


Controlling white space. After you print the "product" range and inspect it on the browswer. You will discover white space to get rid of it use "-" at the beginning and ending.
```
{% assign names = "Tom, Carlos, Will, Bob, Mike, Chris", " %}
{%- assign product = "Ezzy Cartridge Loader", " -%}
{{product}}
```
















