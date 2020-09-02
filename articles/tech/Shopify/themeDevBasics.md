# Theme Dev Basics

## Contents
[Sections](#Sections)  
[Add Bootstrap](#Add-Bootstrap)  
[Add a menu](#Add-a-menu)  
[Another link with a submenu](#Another-link-with-a-submenu)  

## Sections

Go to any of your shops, left panel and click "themes" under "online store'. Then go to "Theme library", choose a theme and  click "customize".  

On the left panel you will see a "Sections" tab and "Theme settings" that you can use to customize the theme.  

## Add Bootstrap

Google bootstrap 4 and copy the CDN link located under CSS.    
```
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" integrity="sha384-JcKb8q3iqJ61gNV9KGb8thSsNjpSL0n8PARn9HuZOnIxN0hoP+VmmDGMN5t9UJ0Z" crossorigin="anonymous">
```  

Go to theme.liquid and paste the link right above the 'application.scss.css' link.  

Go to the bootstrap website (https://getbootstrap.com/docs/4.5/examples/), then hit "examples" and click the "Pricing" example.

Examine it, hit shift + ctrl + i. Copy the body tag and its content.  

Just before the ```</body>``` tag, put a comment ```<!--- Start Bottstrap --->```.  Then paste the code from the "Pricing" example.  

Erase the ```<body>``` tag from the code you just pasted.  

Delete the code you put inside application.scss. Also delete the code inside application.js.  

In the theme.liquid, Cut the top section of the new code with the class "d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm".  

```
    <div class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm">
        <h5 class="my-0 mr-md-auto font-weight-normal">Company name</h5>
        <nav class="my-2 my-md-0 mr-md-3">
            <a class="p-2 text-dark" href="#">Features</a>
            <a class="p-2 text-dark" href="#">Enterprise</a>
            <a class="p-2 text-dark" href="#">Support</a>
            <a class="p-2 text-dark" href="#">Pricing</a>
        </nav>
        <a class="btn btn-outline-primary" href="#">Sign up</a>
    </div>
```  
Go to the "snippets" folder and paste it in the header.liquid file below the ```</header>``` tag.  

Change "div" into "header" to make the new code part of the header.  
```
    <header class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm">
        <h5 class="my-0 mr-md-auto font-weight-normal">Company name</h5>
        <nav class="my-2 my-md-0 mr-md-3">
            <a class="p-2 text-dark" href="#">Features</a>
            <a class="p-2 text-dark" href="#">Enterprise</a>
            <a class="p-2 text-dark" href="#">Support</a>
            <a class="p-2 text-dark" href="#">Pricing</a>
        </nav>
        <a class="btn btn-outline-primary" href="#">Sign up</a>
    </header>
```
## Add a menu

Go to your shopify store website. Find "navigation" under "sales channel" on the left panel.  

Click on "Main menu" on the main area of the webpage.  

On the next page you can "add menu item".  

Fill out the "title" field and then through the "link" field link the new menu item with the folder of the page you previously created. Click on the "link" bar (field), go to the "pages" folder and find the page you previously created.  

Ex: If you created the "about" page before using code, you can link that page to the "about" menu item on shopify through the "link" field.  

### Add a link with a submenu

Click "add menu item", call the menu item "Products", click the "link" bar, choose "collections", then click on "all collections"

### Another link with a submenu

"add menu item"  
Name: "Products" 
Link: "Collections", then "all collections"  

"add menu item"  
Link: "Products", then "all products"  
Name: "Men's"

On the Men's menu item, hover the cursor over the dots on the left side of the bar. Then drag the Men's menu item to the "Products" menu item. The Men's menu item becomes the submenu of the "Products" menu item.  

Copy this code from header.liquid in the snippets file.  
```
    {% for link in linklists.main-menu.links %}
    {% assign child_list_handle = link.title | handleize %}
    {% if linklists[child_list_handle].links != blank %}
    <a href="{{ link.url }}">{{ link.title }}</a>
    [
    {% for childlink in linklists[child_list_handle].links %}
    <a href="{{ childlink.url }}">{{ childlink.title | escape }}</a>
    {% endfor %}]
    {% else %}
    <a href="{{ link.url }}">{{ link.title }}</a>
    {% endif %}
    {% endfor %}
```  
Place the code inside the navigation portion of: 
``` 
<header class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm">
    <h5 class="my-0 mr-md-auto font-weight-normal">Company name</h5>
    <nav class="my-2 my-md-0 mr-md-3">
        <a class="p-2 text-dark" href="#">Features</a>
        <a class="p-2 text-dark" href="#">Enterprise</a>
        <a class="p-2 text-dark" href="#">Support</a>
        <a class="p-2 text-dark" href="#">Pricing</a>
    </nav>
    <a class="btn btn-outline-primary" href="#">Sign up</a>
</header>
```   
This the code you cut from theme.liquid.

Place the code from header.liquid here:
```
<header class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm">
    <h5 class="my-0 mr-md-auto font-weight-normal">Company name</h5>
    <nav class="my-2 my-md-0 mr-md-3">
    <!--- copied code starts here --->
      {% for link in linklists.main-menu.links %}
      {% assign child_list_handle = link.title | handleize %}
      {% if linklists[child_list_handle].links != blank %}
         <a href="{{ link.url }}">{{ link.title }}</a>
         [
            {% for childlink in linklists[child_list_handle].links %}
            <a href="{{ childlink.url }}">{{ childlink.title | escape }}</a>
         {% endfor %}]
      {% else %}
         <a href="{{ link.url }}">{{ link.title }}</a>
      {% endif %}
      {% endfor %}
    <!--- copied code ends here --->
        <a class="p-2 text-dark" href="#">Features</a>
        <a class="p-2 text-dark" href="#">Enterprise</a>
        <a class="p-2 text-dark" href="#">Support</a>
        <a class="p-2 text-dark" href="#">Pricing</a>
    </nav>
    <a class="btn btn-outline-primary" href="#">Sign up</a>
</header>
```
---
Running a for loop and reaching out to a list of links (comes with shopify).  
```
{% for link in linklists.main-menu.links %}
```  
The "main-menu" is the main menu you created. Inside of there, there is a list of links.  

"links" is an array of objects. Inside "links", each index is a link that has info about the menu items you just created.  

You can find more info about link here: https://www.shopify.com/partners/shopify-cheat-sheet. Enter "link" in the search field.  

Every time you loop over the link you create a variable: 
```
{% assign child_list_handle = link.title | handleize %}
```  
The variable is called "child_list_handle". This variable is assigned to the link called "title" and title is converted into a handle. Handles are used to access the attributes of Liquid objects.  

If linklists has the link "title" for the variable "child_list_handle" and it is not blank...
```
{% if linklists[child_list_handle].links != blank %}
```
the link will be printed and another for loop will be done on linklists.

A loop is done over all the links we have inside de main menu to check if they have submenus. If a menu item doesn't have a child, the item menu is shown (printed). If the menu item has a child, both the menu item and the child are shown.  
---  

Take this class found right below the code you pasted in header liquid. 
```
class="p-2 text-dark"
```  
and put it in a couple of places inside the code you pasted.
```
        {% for link in linklists.main-menu.links %}
        {% assign child_list_handle = link.title | handleize %}
        {% if linklists[child_list_handle].links != blank %}
         <!-- class goes below -->
        <a href="{{ link.url }}"class="p-2 text-dark">{{ link.title }}</a>
        [
        {% for childlink in linklists[child_list_handle].links %}
        <!-- class goes below -->
        <a href="{{ childlink.url }}"class="p-2 text-dark">{{ childlink.title | escape }}</a>
        {% endfor %}]
        {% else %}
         <!-- class goes below -->
        <a href="{{ link.url }}"class="p-2 text-dark">{{ link.title }}</a>
        {% endif %}
        {% endfor %}
```  














