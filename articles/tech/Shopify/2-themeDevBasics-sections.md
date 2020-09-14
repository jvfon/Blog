# Theme Dev Basics

## Contents



Go to your shopify store theme and hit "customize".  

Learn to change the store theme design through the customize editor.  

Go to index.liguid located inside the template folder.  

Comment out all the existing code.  

Create a new folder called "sections" on the layout folder.  

Go to index.liquid on the "templates" folder and put ```{% section 'pricing' %}``` on the top of the page.  

Take all the code from pricing.liquid on the "snippets" folder.

Create a new file called "pricing.liquid" on the "sections" folder and paste the code above.  

In this case we need to define this section and tell liquid what section this is. There are two types of sections, dynamic and static. Check out this link for more info ```https://shopify.dev/tutorials/develop-theme-use-sections```.  

Currently we are working on a static section.  

Create a schema, it needs a name, a class, a tag and some settings.  

On the webpage above, scroll down to "settings" and copy the code and paste it after the container. The schema is a json file. 




Change the code, change the name from: 
```
    "name": "Slideshowpr",
```
to
```
    "name": "Pricing",
```

Every time you render a section, shopify will create a div with an id and a class.
```
<div id="shopify-section-[id]" class="shopify-section slideshow">
  [output of the section template]
</div>
```


