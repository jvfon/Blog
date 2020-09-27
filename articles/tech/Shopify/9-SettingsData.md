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
      "sections": {
        "pricing": {
          "type": "pricing",
          "settings": {
            "litle": "Light Pricing"
          }
        }
      }
    },
    "content_for_index": [
      "pricing"
    ]
  },
  "dark": {
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
  }
}
```



