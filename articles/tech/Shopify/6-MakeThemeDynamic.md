# Make the theme dynamic

## Content


Go to the file "section_princing.liquid" from the "sections" folder. Cut this code out:
```
<div class="card mb-4 shadow-sm">
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
</div>
```  
Only leave one box.
```  
<div class="card mb-4 shadow-sm">
   <div class="card-header">
         <h4 class="my-0 font-weight-normal">Free</h4>
   </div>
   <div class="card-body">
         <h1 class="card-title pricing-card-title">$0
            <small class="text-muted">/ mo</small>
         </h1>
         <ul class="list-unstyled mt-3 mb-4">
            <li>10 users included</li>
            <li>2 GB of storage</li>
            <li>Email support</li>
            <li>Help center access</li>
         </ul>
         <button class="btn btn-lg btn-block btn-outline-primary" type="button">Sign up for free</button>
   </div>
</div>
```  
Start a "for" loop:
```
    <div class="card-deck mb-3 text-center">
        {% for block in section.blocks %}
        <div class="card mb-4 shadow-sm">
      ...

         {% endfor %}

```  

We want to split the text into multiple items:
```
<ul class="list-unstyled mt-3 mb-4">
   <li>10 users included</li>
   <li>2 GB of storage</li>
   <li>Email support</li>
   <li>Help center access</li>
</ul>
```  

Create a variable to do the split trick. 
```  
<div class="card-deck mb-3 text-center">
   {% for block in section.blocks %}
      {% assign descrition_list = block.settings.tier_description %}
      <div class="card mb-4 shadow-sm">
```  

```
   {% for block in section.blocks %}
```
Let's go into the section, let's go into the blocks. In there, loop the block that it has, target each block. 

```
   {% assign descrition_list = block.settings.tier_description %}
```
Every time the for loop goes over a block create the variable "description_list" and assign the block settings tier description wich is the string from:
```
<ul class="list-unstyled mt-3 mb-4">
   <li>10 users included</li>
   <li>2 GB of storage</li>
   <li>Email support</li>
   <li>Help center access</li>
</ul>
``` 

Now split the strings up, put them into an array and separate them with a comma and a space.
```
   {% assign descrition_list = block.settings.tier_description | split: ", "%}
```  

Now, bring the name of the tier.
From:
```
<div class="card-deck mb-3 text-center">
   {% for block in section.blocks %}
      {% assign descrition_list = block.settings.tier_description | split: "," %}
      <div class="card mb-4 shadow-sm">
            <div class="card-header">
               <h4 class="my-0 font-weight-normal">Free</h4>
            </div>
            <div class="card-body">
               <h1 class="card-title pricing-card-title">$0
                  <small class="text-muted">/ mo</small>
               </h1>
               <ul class="list-unstyled mt-3 mb-4">
                  <li>10 users included</li>
                  <li>2 GB of storage</li>
                  <li>Email support</li>
                  <li>Help center access</li>
               </ul>
               <button class="btn btn-lg btn-block btn-outline-primary" type="button">Sign up for free</button>
            </div>
      </div>
   {% endfor %}
</div>
```
to
```
<div class="card-deck mb-3 text-center">
   {% for block in section.blocks %}
      {% assign descrition_list = block.settings.tier_description | split: "," %}
      <div class="card mb-4 shadow-sm">
            <div class="card-header">
               <h4 class="my-0 font-weight-normal">{{block.settings.tier_name}}</h4>
            </div>
            <div class="card-body">
               <h1 class="card-title pricing-card-title">{{block.settings.tier_price}}
                  <small class="text-muted">/ mo</small>
               </h1>
               <ul class="list-unstyled mt-3 mb-4">
                  <li>10 users included</li>
                  <li>2 GB of storage</li>
                  <li>Email support</li>
                  <li>Help center access</li>
               </ul>
               <button class="btn btn-lg btn-block btn-outline-primary" type="button">Sign up for free</button>
            </div>
      </div>
   {% endfor %}
</div>
```



