# Liquid Layouts and Templates

## Contents
[Content](#Content)
[Create a page](#Create-a-page)

## Content
The content for the layout is going to be located at the bottom of the "themeliquid" file on the "layout" folder.

```
        <main role="main">
            {{ content_for_layout }}
        </main>
```

# Create a page

Go to "pages" on the left panel under "Online Store" on the "Sales Channels".  

Click the "add page" button located on the top right of the main area.  

You will see a "Title" field and a "Content" field. Put a title and add content to the fields and hit "save". Type "About" on the title field and type "This is the about page" on the content field.

Hit the "view page" link located near the top left of the main area to preview the new page. 

When you look at the browser field you will find something like this: "https://timers-r-us.myshopify.com/pages/about".  

The last word "about" is the name of the page you just created.  

The template comes from the file "page.liquid" in the "templates" folder. Is a template of how we want data to be shown.  

The file "theme.liquid" in the layout folder is the default layout. 



