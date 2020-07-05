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

Create a folder inside your projects folder called "Shopify-theme". Go inside "Shopify-theme" 

Go back to the Theme Kit documentation page: https://shopify.github.io/themekit/, go to "Getting started" and scroll to the bottom.  

Where it says "Create a new theme" 