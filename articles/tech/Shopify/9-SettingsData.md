# Settings Data

## Content

Open up settings_data.json in the config folder. 

```
{
  "current": "Default",
  "presets": {
    "Default": { }
  }
}
```
```
  "current": "Default",
```
It means there is no settings. Shopify will put its own default values.  

The moment you save and start changing the theme settings from the shopify website, these changes will be reflected here.  

To view these changes, hit "Theme settings" on the left panel on the shopify website. Then hit "theme actions" on the bottom of the left panel. Choose "edit code".  

Using presets you can deliver a template that a user can edit to suit his needs. 
```
{
  "current": "Default",
  "presets": {
    "Default": {
      "color_text": "#FF0000",
      "sections": {
        "pricing": {
          "type": "pricing",
          "settings": {
            "litle": "Light Pricing"
          }
        }
      },
      "content_for_index": [
        "pricing"
      ]
    },
    "Dark": {
      "color_text": "#ffffff",
      "sections": {
        "pricing": {
          "type": "pricing",
          "settings": {
            "litle": "Dark Pricing"
          }
        }
      },
      "content_for_index": [
        "pricing"
      ]
    }
  }
}
```
The initial look of the theme can be controlled with this settings.  

With content for index, you can set the order of the sections.  
```      
"content_for_index": [
  "gallery",
  "pricing",
  "newsletter",
  "slider"
]
```


