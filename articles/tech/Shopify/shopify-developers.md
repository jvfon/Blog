# Shopify Developers
##  Contents  
[Create an account](#Create-an-account)  
[Setting up the store environment](#Setting-up-the-store-environment)  
[Create Shopify app](#Create-Shopify-app)  
[Standard Theme - debut](#Standard-Theme-debut)  
[Publish your theme](#Publish-your-theme)  
[Test your theme](#Test-your-theme)  
[Working with an existing website](#Working-with-an-existing-website)  


## Go to https://developers.shopify.com/

## Create an account  
Click "Stores" on the top left side.  
Click "add store" button that is on the right side.
Pick "development store".  
Put the name of your store on the store name field.  
On the login field, put the email that's going to be linked to the store.  
Put a passowrd for the store, then confirm the password.  

The section "Developer preview" is to see the latest updates from shopify to themes. Not needed right now.  
Put the physical store address.  

On the "store purpose" section choose "test app on theme".  
Hit the "save" button that is on top.

## Setting up the store environment

### Install ThemeKit 

Go to https://shopify.github.io/themekit  
For Windows environment use chocolatey: https://chocolatey.org/ and follow the instructions to set it up.  

Open VSCode, go to extensions install liquid.  

## Create Shopify app

Go to your store: store-name.myshopify.com, click on "Apps" on the left panel. Then click on "manage private apps" on the main window and  click on "create new private app".  

On the "App details" section put the name of the theme you are building on the "Private app name field". Name it "theme-nameTheme.API" end the name with "Theme.API" to make things easier.  

Put your email on the "Emergency developer email" field.  

On the "Admin api" section click on the "Show inactive Admin API permissions" pull down.  

Scroll down until you see "Themes" and "theme assets" and change the access to "read and write". Hit "save" and click on "create app".  

----
Create a folder inside your projects folder called "Shopify-theme". Go inside the "Shopify-theme" folder and add another folder: store-nameTheme".  

Go back to the Theme Kit documentation page: https://shopify.github.io/themekit/, click on "Getting started" on the left panel and scroll down near the bottom on the main area.

Where it says "Create a new theme" copy the first line of code: ```theme new --password=[your-password] --store=[your-store.myshopify.com] --name=[theme name]``` and paste it on admin command prompt. 

Go to your Shopify store: https://store-name.myshopify.com/admin/apps/private/261901854222, then find the password field, copy it and replace "[your-password]" with the password you copied from your store. 

The same thing do with the store name. Go the search field of the browser, copy the store name from there: store-name.shopify.com.  

"[theme-name]" Here is where you put name of your theme name that "nameTheme.API". Hit "enter".

## Standard Theme (debut)

Go to your store's website. On "Sales Channels" on the left panel you will see the "Online Store" link, click the link, then click "themes".

You will see a theme called "debut" as the current theme. Then when you scrolldown, on "Theme Library" you will see your new theme. 

ThemeKit looks at the files from our local environment and then uploads new changes to the Shopify store.

On the command prompt inside your theme folder type "theme watch". "Theme watch" looks at any changes within this folder and if there are any changes, it's going to upload those changes to the website.  

On VSCode, open the folder where your Shopify theme is located.  

In the "templates" folder on the right side click on "index.liquid", that is our home page.

Go to the "layout" and then click on the "theme.liquid" file. There you will noticed HTML, CSS and some programing going on. The code inside {% and %} tags is Liquid.

## Publish your theme

Go back to your webstore on "Theme library", scroll down to the new theme you created for the store.Click the "Actions" pull down menu and Hit "publish".  

Usually you don't want to work on a theme that's live so you would hit "duplicate" under "Actions" in the "Current theme" area. But we are practicing with your own store so it's ok to test a new theme.

Once you hit "publish" Shopify will warn you not to publish your theme. Hit "ok" and you will see a new page with "Themes" on top. Hit "view your store" on the main page. You will see a very basic template created for you by Shopify.  

## Test your theme

Go back to VSCode to your Liquid theme. Scroll down until you see ```<a href="/cart">cart</a>```, between this line and the next one type "Billy's Store" or anything you want. 

When you go back to your theme online and hit refresh, you should see "Billy's Store" on your store's webpage.

## Working with an existing website
### Make a duplicate of debut

Go back to your Shopify store (Shopify website). Under "Theme library", make a duplicate of the "Debut" theme. Hit "duplicate" under the "Actions" pull down menu.

You can preview the copy of Debut wich is the theme that comes with Shopify. Everything that you need to build a theme is already built in this theme. You can copy and paste want you need from Debut. There is no need to re-invent the wheel.  
---
To download the copy of Debut, hit "ctrl + c" on the command prompt to stop "theme watch". 

Create a folder called "Debut" just like the theme's name.

On the command prompt go inside the Debut folder.  

In VSCode open the debut folder and then create a config file, name it "config.yml" 

### Get the theme id from here:
Next we need the ID of the copy of the theme debut. Go to your Shopify store. On the "Theme library" area hit "Customize". 

The ID is located on top, on the search field of the browser after the "/theme/" section. The ID should be a series of numbers like "104345043112". Save this number.

Hit the browser's back button. On your Shopify store, go back to "Apps" on the left hand side panel. 

Hit "Manage private apps" on the main section. On the next section, copy the API key and save it.

Click the theme's name located under "Private app name". You can also copy the API number form here. 

Copy the password and save it.
---
Go back to the Shopify themeKit website, click on "Commands" and then click on "configure" on the left panel.

Copy the code, it starts with "development:". Then go to VSCode to the config.yml file. Paste the code in there. 

Replace "your-api-password" and "your theme id" with the password and theme id you saved. 

The password and store address have to be by themselves, no brackets nor parentheses, and the theme id has to be in quotes " ".

Go to the command prompt, make sure you are in the debut folder and type: "theme download", then hit "enter". 

To test things out go to VSCode again. In the xxxTheme-debut folder, open the "sections" folder and click on header.liquid.  

Look for where it says "logo". You only want to make a change. Look for the class "site-header__logo-link". Add some text right before the "</a>" closing tag. 

Go to the debut folder on the command prompt. Type theme watch and then change what you put before the "</a>" tag.  

Refresh your Shopify store website and look at the change.  





