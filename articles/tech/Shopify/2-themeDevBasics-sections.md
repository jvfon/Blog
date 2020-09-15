# Theme Dev Basics

## Contents

[Access settings](#Access-settings)


Go to your shopify store theme and hit "customize".  

Learn to change the store theme design through the customize editor.  

Go to index.liguid located inside the template folder.  

Comment out all the existing code.  

Create a new folder called "sections" on the layout folder.  

Go to index.liquid on the "templates" folder and put ```{% section 'section_pricing' %}``` on the top of the page.  

Take all the code from pricing.liquid on the "snippets" folder.

Create a new file called "section_pricing.liquid" on the "sections" folder and paste the code above.  

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
    "name": "pricing",
```

Every time you render a section, shopify will create a div with an id and a class.
```
<div id="shopify-section-[id]" class="shopify-section slideshow">
  [output of the section template]
</div>
```

Create a tag and a section, put them inside the code you copied from shopify.
```
{% schema %}
{
    "name": "Pricing",
    "class": "section-pricing",
    "tag": "section",
    "settings": [
        {
            "id": "header",
            "type": "text",
            "label": "Header",
            "default": "Hello world"
        }
    ]
}
{% endschema %}
```

Go to the shopify theme page and refresh the page.

On the left side panel the setting you just created are for the user to change.

### Access settings

Go to section_pricing.liquid on the "sections" folder.  On the top change this code:
```
    <div class="pricing-header px-3 py-3 pt-md-5 pb-md-4 mx-auto text-center">
        <h1 class="display-4">Pricing</h1>
```
Change "Pricing" with:
```
    <div class="pricing-header px-3 py-3 pt-md-5 pb-md-4 mx-auto text-center">
        <h1 class="display-4">{{section.settings.Title}}</h1>
``` 
In this section you want to have access to the settings.

Also change the id from the schema, from "header" to "Title":
```
{% schema %}

{
    "name": "Pricing",
    "class": "section-pricing",
    "tag": "section",
    "settings": [
        {
            "id": "title",
``` 

