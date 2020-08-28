# Liquid Layouts and Templates

## Contents
[Content](#Content)
[Create a page](#Create-a-page)
[Specific tags for shopify](#Specific-tags-for-shopify)
[Snipets](#Snipets)

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

The template comes from the file "page.liquid" in the "templates" folder. Is a template of how we want data to be shown.  

The file "theme.liquid" in the layout folder is the default layout. 

You can create other layouts in the same folder with different settings for the background, text color, etc. 

To change the default layout, type:
```
{% layout 'new-layout-name' %}
```
on top of any pages you want to have the new layout.  

## Specific tags for shopify

Look inside theme.liquid.

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

On the main theme folder, create a folder called "snipets".  
Create a file called "header.liquid".  
Paste the content from the theme.liquid ```<body>``` tag into the header.liquid file.

In the theme.liquid file, put a link of the snipet, the header.liquid file
```
<body>
   {% include 'header'}
</body>





