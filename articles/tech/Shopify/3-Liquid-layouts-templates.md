# Liquid Layouts and Templates

## Contents
[Content](#Content)
[Create a page](#Create-a-page)
[Change the default layout](#Change-the-default-layout)
[Specific tags for shopify](#Specific-tags-for-shopify)
[Snipets](#Snipets)
[Assets](#Assets)

## Content
The content for the layout is going to be located at the bottom of the "themeliquid" file on the "layout" folder.

```
        <main role="main">
            {{ content_for_layout }}
        </main>
```

## Create a page

Go to "pages" on the left panel under "Online Store" on the "Sales Channels".  

Click the "add page" button located on the top right of the main area.  

You will see a "Title" field and a "Content" field. Put a title and add content to the fields and hit "save". Type "About" on the title field and type "This is the about page" on the content field.

Hit the "view page" link located near the top left of the main area to preview the new page. 

When you look at the browser field you will find something like this: "https://timers-r-us.myshopify.com/pages/about".  

The last word "about" is the name of the page you just created.  

You can add HTML to any of the other templates to edit them. 

The template comes from the file "page.liquid" in the "templates" folder. Is a template about how we want data to be shown.  

The file "theme.liquid" in the layout folder is the default layout. 

You can create other layouts in the same folder with different settings for the background, text color, etc. 

## Change the default layout
To change the default layout, type:
```
{% layout 'new-layout-name' %}
```
on top of any pages you want to have the new layout.  

## Specific tags for shopify

Look inside theme.liquid in the layout folder.

Shopify uses the code after the tag:
```
{{ content_for_header }}
``` 
for the header.

and: 
```
{{ content_for_layout }}
```
to put the layout.  

You can move the tag for layout above the tag for header if you want to.  

One advantage of using layouts is that if you want to put a notification on every single page, you can change the layout and then display it on every single page instead of manually changing every single page.

Ex: Display a notification on every single page.
Put this code on the main theme:
```
<head>
   <style>
      notification {
         background: red;
         color: white;
      }
   </style>
</head>
<body>
   <div class="notification">
      This website will be under construction for 24hrs
   </div>
</body>
```  
Then make sure theme is used on every single page.  

## Snipets
Code snipets can be reuse. Let'say you want to put a link to the "about" page on every page of your website.

```
<a href="pages/about">About</a>
```
This link is located in the "theme.liquid" file. 
```
<body>
   <header>
      <a href="pages/about">About</a>
   </header>
</body>
```  

Move the code that's inside the ```<body>``` tag in the theme.liquid file.

On the main theme folder, create a folder called "snippets".  
Create a file called "header.liquid" inside the snippets folder.
Paste the content from the theme.liquid ```<body>``` tag into the header.liquid file.

In the theme.liquid file, put a link of the snippet, the header.liquid file
```
<body>
   {% include 'header'}
</body>
```
This code will allow you to link the ```<body>``` tag content from header.liquid back to theme.liquid.  

You can create more snippets and link them to different pages.  

## Assets

The assets are located in the folder "Assets" in the files "application.js" and "application.scss".  

Inside application.scss you can use sass but if you don't know sass, you can use regular css.  

You can always change the extension file name from "scss" to "css". At the same time you need to go inside "theme.liquid" and change the code from: 
```
    {{ 'application.scss.css' | asset_url | stylesheet_tag }}
```  
To:  
```  
    {{ 'application.css' | asset_url | stylesheet_tag }}
```  
Remove "scss" from 'application.scss.css'.  

If you have images for your theme, they need to be inside the "assets" folder.  

Once you save the image, go to theme.liquid and add a link for the image.  
```
<body>
   <img src="{{'ES-399.jpg' | asset_url}}">
</body>
```   

Instead of using the application.js folder you can directly put ```<script>``` tags and link tags in theme.liquid below the application.scss.css link.  
```
<link rel="stylesheet" href="">
``` 
to connect to a cdn.  



