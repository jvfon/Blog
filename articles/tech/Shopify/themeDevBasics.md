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

Then delete the code below, we no longer need it:
```
        <a class="p-2 text-dark" href="#">Features</a>
        <a class="p-2 text-dark" href="#">Enterprise</a>
        <a class="p-2 text-dark" href="#">Support</a>
        <a class="p-2 text-dark" href="#">Pricing</a>
```

At this moment the child menu item "Men's" will appear next to the parent. If you create a drop down menu you could put code for the child menu item.
```
 [{% for childlink in linklists[child_list_handle].links %}
   <a href="{{ childlink.url }}" class="p-2 text-dark">{{ childlink.title | escape }}</a>
   {% endfor %}]
```

At the end of the for loop, the code right above. Paste:
```
    <a href="/cart">cart</a>
    <a href="pages/about">About</a>
```
This code was taken from header.liquid. It code for a cart.  At the end, the code will look like:
```
    <nav class="my-2 my-md-0 mr-md-3">

        {% for link in linklists.main-menu.links %}
        {% assign child_list_handle = link.title | handleize %}
        {% if linklists[child_list_handle].links != blank %}
        <a href="{{ link.url }}" class="p-2 text-dark">{{ link.title }}</a>
        [
        {% for childlink in linklists[child_list_handle].links %}
        <a href="{{ childlink.url }}" class="p-2 text-dark">{{ childlink.title | escape }}</a>
        {% endfor %}]
        {% else %}
        <a href="{{ link.url }}" class="p-2 text-dark">{{ link.title }}</a>
        {% endif %}
        {% endfor %}
   <!-- new code below -->
        <a href="/cart">cart</a>

    </nav>
```
Delete the about page, you no longer need it.
```
    <a href="pages/about">About</a>
```

Copy the if statement from the header.liquid file.
```
    {% if shop.customer_accounts_enabled %}
    {% if customer %}
    <a href="/account">account</a>
    {{ 'log out'  | customer_logout_link }}
    {% else %}
    {{ 'log in ' | customer_login_link }}
    {{ 'register' | customer_register_link }}
    {% endif %}
    {% endif %}
```
Pasted after the code for the cart.

```
        <a href="/cart">cart</a>

        {% if shop.customer_accounts_enabled %}
         {% if customer %}
            <a href="/account">account</a>
            {{ 'log out'  | customer_logout_link }}
        {% else %}
            {{ 'log in ' | customer_login_link }}
            {{ 'register' | customer_register_link }}
        {% endif %}
        {% endif %}
```
"customer_accounts_enabled" is an object that comoes with shopify. Look it up on the shopify cheat sheet.  

Check if the customer user is enable.

"if customer" check if the customer is logged in.  

If the customer is logged in it will show up here 
```
<a href="/account">account</a>
```

If the customer is not logged in, you will get the customer login link.
```
        {% else %}
            {{ 'log in ' | customer_login_link }}
            {{ 'register' | customer_register_link }}
        {% endif %}
```
"customer_login_link" is also an object in shopify.  

Instead of using that filter you can see what the direct link looks like and copy it from the shopify cheat sheet.  
```
{% else %}
   <a href="/account/login">Login</a>
   {{ 'register' | customer_register_link }}
{% endif %}
```
The bottom code
```
...
        {% if shop.customer_accounts_enabled %}
        {% if customer %}
            <a href="/account">account</a>
            {{ 'log out'  | customer_logout_link }}
        {% else %}
            {{ 'log in ' | customer_login_link }}
            {{ 'register' | customer_register_link }}
        {% endif %}
        {% endif %}

    </nav>
    <a class="btn btn-outline-primary" href="#">Sign up</a>
</header>
```
goes here:
```
...
        {% if shop.customer_accounts_enabled %}
        {% if customer %}
            <a href="/account">account</a>
            {{ 'log out'  | customer_logout_link }}
        {% else %}
            <a href="/account/login">Login</a>
            <a class="btn btn-outline-primary" href="#">Sign up</a>
            {{ 'register' | customer_register_link }}
        {% endif %}
        {% endif %}

    </nav>
</header>
```

Search "customer_register_link" in the shopify cheat sheet. Use "register" to look for it. Replace:
```
{{ 'register' | customer_register_link }}
```

With:
```
{{ routes.account_register_url }}
```
The code will look like:
```
...
...
        {% if shop.customer_accounts_enabled %}
        {% if customer %}
            <a href="/account">account</a>
            {{ 'log out'  | customer_logout_link }}
        {% else %}
            <a href="/account/login">Login</a>
            <a class="btn btn-outline-primary" href="#">Sign up</a>
            {{ routes.account_register_url }}
        {% endif %}
        {% endif %}

    </nav>
</header>
```


Then, put the code in:
```
<a class="btn btn-outline-primary" href="#">Sign up</a>
```
Where the "#" is.
```
<a class="btn btn-outline-primary" href="{{ routes.account_register_url }}
">Sign up</a>
```
The code will look like:
```
...
        <a href="/cart">cart</a>

        {% if shop.customer_accounts_enabled %}
        {% if customer %}
        <a href="/account">account</a>
        <a class="btn btn-outline-primary" href="{{ routes.account_register_url }}
        ">Sign up</a>
        {{ 'log out'  | customer_logout_link }}
        {% else %}
        <a href="/account/login">Login</a>
        {% endif %}
        {% endif %}
```

When you refresh your shop the new changes won't appear because the customer account has to be enabled.  

Go to your shopify shop settings and change it. Setting is located on the left panel at the bottom.  

Click on "checkout". Check "accounts are optional".  

The new code should look like this:
```
...
        <a href="/cart">cart</a>

        {% if shop.customer_accounts_enabled %}
        {% if customer %}
        <a href="/account">account</a>


        {{ 'log out'  | customer_logout_link }}

        {% else %}
        <a href="/account/login">Login</a>
        <a class="btn btn-outline-primary" href="#">Sign up</a>
        {{ routes.account_register_url }}
        {% endif %}
        {% endif %}

```   

Remove:
```
        {{ routes.account_register_url }}
```

Put: 
```
class="p-2 text-dark
```
in several places. 

The code should look like:
```
        <a href="/cart">cart</a>

        {% if shop.customer_accounts_enabled %}
        {% if customer %}
        <a href="/account" class="p-2 text-dark">account</a>


        {{ 'log out'  | customer_logout_link }}

        {% else %}
        <a href="/account/login" class="p-2 text-dark">Login</a>
        <a class="btn btn-outline-primary" href="#">Sign up</a>
        {% endif %}
        {% endif %}

```   

Replace the "#" in ```href="#"``` with:
```
{{ notes.account_register_url }}
```  

The new code will look like: 
```
...
        <a href="/cart">cart</a>

        {% if shop.customer_accounts_enabled %}
        {% if customer %}
        <a href="/account" class="p-2 text-dark">account</a>


        {{ 'log out'  | customer_logout_link }}

        {% else %}
        <a href="/account/login" class="p-2 text-dark">Login</a>

        <a class="btn btn-outline-primary" href="{{ notes.account_register_url }}
        " class="p-2 text-dark">Sign up</a>
        {% endif %}
        {% endif %}
```   

### Change the company name

You can search "shop" in the shopify cheat sheet and you will find this:
```  
{{ shop_locale.name }}
```  

Replace "Company name" with {{ shop.name }} the code you found.
```
</header>

<header class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm">
    <h5 class="my-0 mr-md-auto font-weight-normal">Company name</h5>
    <nav class="my-2 my-md-0 mr-md-3">
```

New code: 
```   
</header>

<header class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm">
    <h5 class="my-0 mr-md-auto font-weight-normal">{{ shop.name }}
</h5>
    <nav class="my-2 my-md-0 mr-md-3">
```

### Put a link to home

Search "route" in the shopify cheat sheet.  
Copy and paste ```{{ routes.root_url }}``` here:
```
</header>

<header class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom shadow-sm">
    <h5 class="my-0 mr-md-auto font-weight-normal"><a href="{{ routes.root_url }} ">{{ shop.name }}
    </h5>
```  

At this point you can comment out or earse the original ```<header>``` tag.

## footer.liquid

Create a snippet for the footer. Go to the snippets folder and create a new file called: "footer.liquid".

Go back to the folder "layout", to the file "theme.liquid". Copy the footer and all its content.  
```  
<footer class="pt-4 my-md-5 pt-md-5 border-top">
...
</footer>
```
Paste the code in "footer.liquid".  

Find:
```
    {% include 'header' %}
```
Copy and paste the code right above:
```
        <footer class="pt-4 my-md-5 pt-md-5 border-top">
```
Change ```{% include 'header' %}``` to:
```
    {% include 'footer' %}
```

In the footer.liquid file, create a container below
```
        <footer class="pt-4 my-md-5 pt-md-5 border-top">
```
and put the footer code inside you just moved from theme.liquid.  

Create a new file called "pricing.liquid" in the snippets folder.

Take the code you just put inside a container in footer.liquid and put it in pricing.liquid.  

### Bring pricing.liquid into the home page.

Go to index.liquid located in the templates folder. 

Erase ```<%h1>Home Page</h1>``` and put:
```
{% include 'pricing' %}
```  

Go to theme.liquid and copy part of the code starting below "Start Bootstrap".
```
    <div class="pricing-header px-3 py-3 pt-md-5 pb-md-4 mx-auto text-center">
        <h1 class="display-4">Pricing</h1>
        <p class="lead">Quickly build an effective pricing table for your potential customers with this Bootstrap
            example. It’s built with default Bootstrap components and utilities with little customization.</p>
    </div>
```  
Go to the pricing.liquid file and paste the code right below:





























