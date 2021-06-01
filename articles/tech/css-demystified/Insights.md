# Insights

### Setting the width

When you set the width in CSS, you only set the width for the content not the whole box. 

Take into account that the padding and border makes the box much bigger.  

How to fix this issue:  
Use box-sizing.  
```css
.element {
   box-sizing: border-box;
}
```
When the width (or height) is set, the total with also includes padding and border.  

```css
.element {
   box-sizing: border-box;

   width: 200px;
   padding: 20px;
   border: 5px solid red;
   marging: 20px;
}
```
The total width is: 200px.  

### Border box in action
Put this on you style sheet.  
```css
*,
*::before,
*::after {
   box-sizing: border-box;
}
```
### When you don't set the width

