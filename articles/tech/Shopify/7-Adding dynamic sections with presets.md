# Adding dynamic sections with presets

## Contents
[Set up presets](#Set_up_presets)

Sections independent of each other.  

Go to index.liquid and comment out ```{% section 'section_pricing' %}``` and add ```{{ content_for_index }}``` on the top of the page.  

### Set up presets

Default settings are useful to avoid leaving webpage sections blank. 

Go to section_pricing.liquid in the "sections" folder.

Change the name of the file to "pricing.liquid". Also go to the page.liquid (templates folder) and include ```{% section 'pricing' %}``` on the top of the page.  

Go to pricing.liquid (section_pricing.liquid) in the "sections" folder and scroll down to the end of "blocks". Put a comma and below there put the presets.  

Go to: ```https://shopify.dev/tutorials/develop-theme-use-sections``` scroll down to presets and copy the sample code.  
```
"presets": [
   {
         "category": "Custom Content",
         "name": "Text",
         "settings": {
            "heading": "Hello World"
         },
         "blocks": [
            {
               "type": "text",
               "settings": {
                     "content": "Once upon a time..."
               }
            }
         ]
   }
]
```  
The top section should reflect the schema settings section:
```
"category": "Custom Content",
"name": "Text",
"settings": {
   "heading": "Hello World"
},
```
to:
``` 
"category": "Custom Content",
"name": "Pricing",
"settings": {
   "title": "Pricing"
},
```

```{{ content_for_index }}``` allows users to see the ```"category": "Custom Content"``` you are adding to the code.  

For the blocks, you also need to use the same setting from the original schema blocks.  



