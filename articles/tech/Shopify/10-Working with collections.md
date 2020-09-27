# Working with collections

## Contents

Go to index.liquid in the "templates" folder.

Move the for loop out of the comment section.
```
{% for product in collections.frontpage.products limit:4 %}
<div>
  <a href="{{ product.url | within: collection }}">{{ product.title }}</a>
  {{ product.price | money }}
  {% unless product.available %}<br><strong>sold out</strong>
  {% endunless %}
  <a href="{{ product.url | within: collection }}">
    <img src="{{ product.featured_image.src | img_url: 'large' }}" alt="{{ product.featured_image.alt | escape }}">
  </a>
</div>
{% endfor %}
```  
You are going into the "collections" object, pass in the name of the collection (frontpage), then you have access what's inside in the collection (products).  

Go to the shopify cheat sheet and search "collections" to find out more about this object. https://www.shopify.com/partners/shopify-cheat-sheet  

"collection" is useful when you are working on a specific page of the collection. 

```
{% for product in collections.frontpage.products limit:4 %}
```  
To have access to a specific collection, use the word "collections" then put the name of the collection (frontpage) and then you can have accesss to the products.  

```
<a href="{{ product.url | within: collection }}">{{ product.title }}</a>
```
For each product you are creating an anchor link. "Give me the product url within collection".  

The output ex: ```< a hreft="/collections/frontpage/produces/brown_boots"> allows you to get info about other similar products.

For example when you are shopping online and see on a page "You might also like" and then additional products are presented to you.  

You can create related loops about what an user might like.  

### Change the look of the collections page
Editing the collection.liquid file in the "templates" folder allows you to change the look of the collections page.  

```
{% paginate collection.products by 2 %}
```
Only 2 products are shown per page.

The for loop build pagination for you. 
```
{% for product in collection.products %}
   <div>
         <a href="{{ product.url | within: collection }}">{{ product.title }}</a>
         {{ product.price | money }}
         {% unless product.available %}<br><strong>sold out</strong>
         {% endunless %}
         <a href="{{ product.url | within: collection }}">
            <img src="{{ product.featured_image.src | img_url: 'large' }}" alt="{{ product.featured_image.alt | escape }}">
         </a>
   </div>
{% else %}
   <p>no matches</p>
{% endfor %}
```

"Collections" will give you access to all of the products.

"Collection" will give you access to a specific group of producs. Ex: the collection of brown boots from all brands.  










