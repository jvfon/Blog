# The settings schema

## Content

Open up the file "setting_schema.json" in the "config" folder.  You can change almost everything except "name".  

```
[
  {
    "name": "theme_info",
    "theme_name": "Themekit template theme",
    "theme_version": "1.0.0",
    "theme_author": "Shopify",
    "theme_documentation_url": "https://github.com/Shopify/themekit",
    "theme_support_url": "https://github.com/Shopify/themekit/issues"
  }
]
```

After that you can pass an object.
```
  {
    "name": "Colors",
    "settings": [
      {
        "type": "color",
        "id": "color_text",
        "label": "Color for text",
        "default": "#1b1b1b"
      }
    ]
  }
```   
You can use these settings if you create all the CSS and put in the assets folder. Also you can use these settings anywhere on the website.  

Go to applications.scss and put:
```
p {
    color: {{ settings.color_text }}
}
```  
You could get an error message from VS Code because the syntax is not CSS but ignore it.  

Change the file name to "application.sccss.liquid".

Go to "application.js" and put:
```
console.logp("{{ settings.color_text }}");
```
Change the file name to "application.js.liquid".  

You can also add ```{{ settings.color_text }}``` anywhere inside pricing.liquid 
ex:
``` 
<h1 class="display-4">{{section.settings.title}} {{ settings.color_text }}</h1>
``` 


