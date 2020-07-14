# Shopify Developers
##  Contents
[Setting up the store environment](#Setting-up-the-store-environment)  
[Create Shopify app](#Create-Shopify-app)  

[Working with an existing website](#Working-with-an-existing-website)


## Go to https://developers.shopify.com/

Create an account  
Click "Stores" on the top left side.  
Click "add store" button.  
Pick "development store".  
Put the name of your store on the store name field.  
On the login field, put the email that's going to be linked to the store.  
Put a passowrd for the store, then confirm the password.  

The section "Developer preview" is to see the latest updates from shopify to themes. Not needed right now.  
Put the physical store address.  

On the "store purpose" section choose "test app on theme".  
Hit the "save" button.  

## Setting up the store environment

### Install ThemeKit 

Go to https://shopify.github.io/themekit  
For Windows environment use chocolatey: https://chocolatey.org/ and follow the instructions to set it up.  

Open VSCode, go to extensions install liquid.  

## Create Shopify app

Go to your store: store-name.myshopify.com and click on "manage private apps" on the main window. Then click on "create new private app".  

On the "App details" section put the name of the theme you are building on the "Private app name field". Name it "nameTheme.API" end the name with "Theme.API" to make things easier.  

Put your email on the "Emergency developer email" field.  

On the "Admin api" section click on the "Show inactive Admin API permissions" pull down.  

Scroll down until you see "Theme templates" and "theme assets" and change the access to "read and write". Hit "save" and click on "create app".  

Create a folder inside your projects folder called "Shopify-theme". Go inside "Shopify-theme". Go inside the "Shopify-theme" folder and add another folder: store-nameTheme".  

Go back to the Theme Kit documentation page: https://shopify.github.io/themekit/, go to "Getting started" and scroll to the bottom.  

Where it says "Create a new theme" copy the first line of code: ```theme new --password=[your-password] --store=[your-store.myshopify.com] --name=[theme name]``` and past it on admin command prompt. 

Go to your Shopify store: https://store-name.myshopify.com/admin/apps/private/261901854222, then find the password field, copy it and replace "[your-password]" with the password you copied from your store. 

The same thing do with the store name and them name. Go the search field of the browser, copy the store name from there: store-name.shopify.com.  

"[theme-name]" Here is where you put name of your theme. Hit "enter".

Go to your store's website. On "Sales Channels" on the left side you will see "Online Store" click the link, then click "themes".

You will see a theme called "debut" as the current theme. Then on "Theme Library" you will see you new theme. 

ThemeKit looks at the files from our local environment and then uploads new changes to the Shopify store.

On the command prompt inside your theme folder type "theme watch". "Theme watch" looks at any changes within this folder and if there are any changes, it's going to upload those changes to the website.  

On VSCode, open the folder where your Shopify theme is located.  

On "templates" on the right side click on "index.liquid", that is our home page.

On "layout" and then "theme.liquid". There you will noticed HTML, CSS and some programing going on. The programing is Liquid.

Go back to your webstore on "Theme library" click the "Actions" pull down menu. Hit "publish".  

Usually you don't want to work on a theme that's live so you would hit "duplicate" under "Actions" in the "Current theme" area. But we are practicing with your own store so it's ok to test a new theme.

Once you hit "publish" Shopify will warn you not to publish your theme. Hit "ok" and you will see a new page with "Themes" on top. Hit "view your store". You will see a very basic template created for you by Shopify.  

Go back to VSCode to your Liquid theme. Scroll down until you see ```<a href="/cart">cart</a>```, between this line and the next one type "```<h1>Billy's Store</h1>'''" or anything you want. 

When you go back to your theme online and hit refresh, you should see "Billy's Store" on your store's webpage.

## Working with an existing website

Go back to your Shopify store (Shopify website). Under "Theme library", make a duplicate of the "Debut" theme. Hit "duplicate" under the "Actions" pull down menu.

You can preview the copy of Debut. You will the theme that comes with Shopify. Everything that you need to build a theme is already built in this theme. You can copy and paste want you need from Debut. There is no need to re-invent the wheel.  

To download the copy of Debut, hit "ctrl + c" on the command prompt to stop "theme watch". 

Create a folder called "Debut" just like the theme's name.

On the command prompt go inside the Debut folder.  

In VSCode open the debut folder and then create a config file, name it "config.yml" 

Next we need the ID of the copy of the theme debut. Go to your Shopify store. On the "Theme library" area hit "customize". 

The ID is located on top, on the search field of the browser after the "/theme/" section. The ID should be a series of numbers like "104345043112". Save this number.

Hit the browser's back button. On your Shopify store, go back to "Apps" on the left hand side panel. 

Hit "Manage private apps". On the next section, copy the API key and save it.

Click the theme's name. You can also copy the API number form here. 

Copy the password and save it.

Go back to the Shopify themeKit website, click on "Commands" and then click on "configure" on the left panel.

Copy the code, it starts with "development:". Then go to VSCode to the config.yml file. Paste the code in there. 

Replace "your-api-password" and "your theme id" with the password and theme id you saved. 

password has to be by itself no brackets or parenthesis, theme ide in quotes " " and store address by itself too. 

Go to the command prompt, make sure you are in the debut folder and type: "theme download", then hit "enter". 

To test things out go to VSCode again. Open the config.yml file. Hit the sections folder and click on header.  

Look for where it says "logo". You only want to make a change. Look for the class "site-header_logo-link". Add some text right before the "</a>" closing tag. 

Go to the debut folder on the command prompt. Type theme watch and then change what you put before the "</a>" tag.  

Refresh your Shopify store website and look at the change.  





