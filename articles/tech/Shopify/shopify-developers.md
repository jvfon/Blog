# Shopify Developers
##  Contents
[Setting up the store environment](#Setting-up-the-store-environment)  
[Create Shopify app](#Create-Shopify-app)  


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

On the "Adim api" section click on the "Show inactive Adim API permissions" pull down.  

Scroll down until you see "Theme templates and theme assets" and change the access to "read and write". Hit save and click on "create app".  

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



