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

```
"blocks": [
   {
      "type": "tier",
      "settings": {
               "tier_name": "free"
            }
   },
                        {
      "type": "tier",
      "settings": {
               "tier_name": "Monthly"
            }
   },
                        {
      "type": "tier",
      "settings": {
               "tier_name": "Yearly"
            }
   }
]
```
Complete pricing.liquid (from sections folder) code:
```
<div class="container">

    <div class="pricing-header px-3 py-3 pt-md-5 pb-md-4 mx-auto text-center">
        <h1 class="display-4">{{section.settings.title}}</h1>
        <p class="lead">{{section.settings.Description}}</p>
    </div>

    <div class="card-deck mb-3 text-center">
        {% for block in section.blocks %}
        {% assign description_list = block.settings.tier_description | split: ", " %}
            <div class="card mb-4 shadow-sm">
                <div class="card-header">
                    <h4 class="my-0 font-weight-normal">{{block.settings.tier_name}}</h4>
                </div>
                <div class="card-body">
                    <h1 class="card-title pricing-card-title">${{block.settings.tier_price}}<small class="text-muted">/
                        {{block.settings.tier_date}}</small></h1>
                    <ul class="list-unstyled mt-3 mb-4">
                        {% for item in description_list %}
                            <li>{{item}}</li>
                        {% endfor %}
                    </ul>
                    <a href="{{block.settings.tier_button_link}}" class="btn btn-lg btn-block
                    {% if block.settings.tier_button_style == "outline" %} btn-outline-primary 
                    {% else %} btn-primary 
                    {% endif %}"> {{block.settings.tier_button_text}}
                    </a>
                </div>
            </div>
        {% endfor %}
            <!-- <div class=" card mb-4 shadow-sm">
                <div class="card-header">
                    <h4 class="my-0 font-weight-normal">Pro</h4>
                </div>
                <div class="card-body">
                    <h1 class="card-title pricing-card-title">$15
                        <small class="text-muted">/ mo</small>
                    </h1>
                    <ul class="list-unstyled mt-3 mb-4">
                        <li>20 users included</li>
                        <li>10 GB of storage</li>
                        <li>Priority email support</li>
                        <li>Help center access</li>
                    </ul>
                    <button class="btn btn-lg btn-block btn-primary" type="button">Get started</button>
                </div>
            </div>
            <div class="card mb-4 shadow-sm">
                <div class="card-header">
                    <h4 class="my-0 font-weight-normal">Enterprise</h4>
                </div>
                <div class="card-body">
                    <h1 class="card-title pricing-card-title">$29
                        <small class="text-muted">/ mo</small>
                    </h1>
                    <ul class="list-unstyled mt-3 mb-4">
                        <li>30 users included</li>
                        <li>15 GB of storage</li>
                        <li>Phone and email support</li>
                        <li>Help center access</li>
                    </ul>
                    <button class="btn btn-lg btn-block btn-primary" type="button">Contact us</button>
                </div>
            </div> -->
    </div>
</div>

{% schema %}
    
    {
        "name": "Pricing",
        "class": "section-pricing",
        "tag": "section",
        "settings": [
                {
                "id": "title",
                "type": "text",
                "label": "Title",
                "default": "Pricing"
                }, 
                {
                "id": "Description",
                "type": "textarea",
                "label": "Section Description",
                "default": "Quickly build an effective pricing table for your potential customers with this Bootstrap example. It’s built with default Bootstrap components and utilities with little customization."
                }
            ],
        "blocks": [
            {
                "type": "tier",
                "name": "Tier",
                "limit": 4,
                "settings": [
                    {
                    "id": "tier_name",
                    "type": "text",
                    "label": "Tier Name",
                    "default": "Free"
                    }, 
                    {
                    "id": "tier_price",
                    "type": "text",
                    "label": "Tier Price",
                    "default": "0"
                    }, 
                    {
                    "id": "tier_date",
                    "type": "select",
                    "label": "Tier Date",
                    "options": [
                        {
                        "value": "dy",
                        "label": "Daily"
                        }, 
                        {
                        "value": "mo",
                        "label": "Monthly"
                        }, 
                        {
                        "value": "yr",
                        "label": "Yearly"
                        }
                    ],
                    "default": "mo"
                    }, 
                    {
                    "id": "tier_description",
                    "type": "textarea",
                    "label": "Tier Description",
                    "info": "Separate by a comma",
                    "default": "10 users included, 2GB of storage, Email support, Help center access",
                    "placeholder": "example a, example b, example c"
                    }, 
                    {
                    "id": "tier_button_style",
                    "type": "select",
                    "label": "Button Style",
                    "options": [
                        {
                        "value": "outline",
                        "label": "Outline"
                        }, 
                        {
                        "value": "filled",
                        "label": "Filled"
                        }
                    ],
                    "default": "outline"
                    }, 
                    {
                    "id": "tier_button_text",
                    "type": "text",
                    "label": "Button Text",
                    "default": "Sign Up"
                    }, 
                    {
                    "id": "tier_button_link",
                    "type": "text",
                    "label": "Tier link URL",
                    "default": "#"
                    }
                ]
            }
        ],
        "presets": [
            {
                "category": "Custom Content",
                "name": "Pricing",
                "settings": {
                    "title": "Pricing",
                    "Description": "Quickly build an effective pricing table for your potential customers with this Bootstrap example. It’s built with default Bootstrap components and utilities with little customization."
                },
                "blocks": [
                    {
                        "type": "tier",
                        "settings": {
                                "tier_name": "free"
                            }
                    },
                                        {
                        "type": "tier",
                        "settings": {
                                "tier_name": "Monthly"
                            }
                    },
                                        {
                        "type": "tier",
                        "settings": {
                                "tier_name": "Yearly"
                            }
                    }
                ]

            }
        ]
    }

{% endschema %}
```


