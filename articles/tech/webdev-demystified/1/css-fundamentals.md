# CSS Fundamentals

### A CSS rule  

```css
p {
   color: #414141;
}
```
P = selector  
color: = property  
#414141; = value  

property + value = a declaration  

### CSS is for?

CSS agnostic. It's based on the Open Standard Principle. In order for CSS and HTML to work in many browsers they were designed to be simple.  

The client control the display the content. People can choose settings, devices choose what they can handle and creators don't know all the variables. 

Designing for an unknown infinite canvas. Design for change, movement, adaptation. 

The cascade takes all the rules, put them together and how they will override each other. Then the browser puts everything together.

Creators have no control, they only suggest how a document should look like. The intent of the outcome, what they are pushing for.  

Devices are very important to CSS, CSS adapts itself to screen size, type of device, etc. CSS adapts to context.   

CSS works best when height are not defined at the same time and the font size chosen is going to respect the content around.  

CSS is designed to not loose content so "overflow: visible" is the default.  

### CSS global scope

The global scope is not a bug, it's a feature. The different pieces need to be available to reuse them.

### The box model - width

Declaring the width is for the content itself. The real width is equal to margin + border + padding + width + padding + border + margin.  

To simply things box-sizing can be used. So:
```css
box-sizing: border-box;
``` 
will make the width and height be determined only by the border-box.  

If we set the width (or height) = 200px with the border-box, the real width will include the actual width of the content, the padding and the border. The margin will not be included in the width.  

Margin is the space between elements. Border-box only includes the visual parts of our elements. 

A typical way to set up box-sizing:
```css
*, *::before, *::after {
   box-sizing: border-box;
}
```
The "*" is used to affect all the elements is CSS.  

With box-sizing: border-box is like having the width set to 100%. Even if you add padding and border, the container will never overflow and will adjust to window resizing. 

When you increase/decrease the padding and border the total content width will change to accomodate the changing padding and border.  

### Block level elements

Block level elements will take up the whole width of the page and they adapt when the width of the page changes. Adding padding and margin won't change this attribute.  

When the width is left out. The content will take as much room as it has available. 

When the width is set for ex:
```css
width: 100%;
```
the width is 100% of the parent.  

The problem comes when padding and border width is added because the total width increases. So if the content width is set to 100%, the total width is equal to the width of the content plus padding and plus the border width. 

## Height

Avoid setting heights. Every element has an intrinsic height by default. Height is determined by the content inside of it. 

If you need to set a height, use "min-height". Content will always retain a minimum height no matter the size of the content but the height will automatically increase when the content increases too.  

If you need to increase the background, use padding. 

## Inheritance

When you declare something on a element and it also applies to the element's descendants.

General rule:  
**Anything related to typography will be inherited. ex: font-size, font-family, font-decoration, color, etc.**  

Put most of the rules on html or body elements but if the browswer has a default value, these properties won't be inherited.  

**Nothing related to layout is inherited. ex: margin, padding, height, etc.**  

Because of the browser defaults, the following do not inherit things like you'd expect them to: ```<button>, <input>, <optgroup>, <select>, <textarea>```. In short elements you would find inside a form have browser defaults.  

At first they don't inherit text properties but you can make them inherit them if you want.  

While reseting browser default properties you can include form elements so they will inherit properties.  
```css
button, input, optgroup, select, textarea {
   font-family: inherit;
}

a {
   color: inherit;
}

h2, h3, h4 {
   font-weight: inherit;
}
```

### Font size

The font size of a browser is usually 16px. When you use the rem unit, this unit will look to the browser default that is controlled from the html selector. It is better if you change the font size from the body selector so the original default font size is unchanged and stays consistent when you create a webpage.  

### The cascade

**Embrace the cascade**

1- Origin of importance  
2- Specificity  
3- Order of appearance  

### Order of appearance

All based on "author declarations" webdevs have control over the cascade.  

1 - Linked style sheets.  
2 - Embedded styles (the ```<style>``` attribute).  
3 - Inline styles.  

### Origin of importance

Include:  
Author declarations - what we control.  

"User agent declarations" - Browser defaults.  

"User declarations" - the styles the user imposes.  

Order of importance:  
1 - Author declarations. 
2 - User declarations.  
3 - User agent declarations.    

Consideration:  
Avoid setting font size in px from html selector (CSS) because the user might have set their own default and we are overriding the font size and changing the way the browser looks.  

Another level of importance:  

When !important comes into play.  

1 - Important user declarations.  
2 - Important author declarations.  
3 - Author declarations.   
4 - User declarations.   
5 - User agent declarations.    

### Changing font size from html selector  

Using pixels (absolute unit) to set the font size can cause potential problems because the user can set their own preference and you will be overriding it.   

The user has final say about font size and don't want to strip that away.  

### Transitions and animations

Contrary to what the spec says in Firefox and Chrome browsers, the order of importance is the following:  

1 - Important user declarations.  
2 - Important author declarations.  
3 - Animations
4 - Transitions 
5 - Author declarations.   
6 - User declarations.   
7 - User agent declarations.  

### Specificity 

One way the browser chooses which style to use on an element. It is also used by the browser to choose which style has priority when there are two ore more conflicting styles.  

The browser chooses the more specific selector.

If two selector have the same specificity the selector that appears last wins.  

### Keep spcificity flat

Avoid having nested and double selectors to save yourself from frustration when you try to change CSS later.










