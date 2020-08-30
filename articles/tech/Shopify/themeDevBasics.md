# Theme Dev Basics

## Contents
[Sections](#Sections)  
[Add Bootstrap](#Add-Bootstrap)  


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



