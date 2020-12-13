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

CSS is design to not loose content so overflow visible is the default.  

### CSS global scope

The global scope is not a bug, it's a feature. The different pieces need to be available to reuse them.

### The box model

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

When you change the padding and border the content width will change to accomodate the changing padding and border.  

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