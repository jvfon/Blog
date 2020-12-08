# Simple Layout

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

Designing for an unknown infinete canvas. Design for change, movement, adaptation. 



### Starting Document

Anything related to text is inherited, anything related to layout is not inherited.  

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">    
    <title>A great blog2</title>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@900&family=PT+Serif:wght@400;700&display=swap"
    rel="stylesheet">
    <link rel="stylesheet" href="styles2.css">
</head>
<body>
    <article>
        <header>
        <h1>A really good blog article</h1>
        <p class="subtitle">A short description explaining why this is a good article and trying to get you to stick around.
        </p>
        </header>

        <div class="container">
        <p class="lead">Nam ultrices orci duis eget leo, elementum id. Pharetra ut blandit nisl aliquet <strong>morbi quam
        a viverra venenatis</strong>. Posuere quis bibendum ut nunc mauris nibh. Mauris mi sodales pretium fusce. Nulla
        scelerisque magna tincidunt aliquam, tempor, neque lobortis gravida. Tellus ante nec laoreet ullamcorper sit
        vulputate urna.
        </p>
        <p>Enim suspendisse ante scelerisque hendrerit eget vestibulum velit. Vestibulum amet a id a mattis nisl.
        <strong>Id
        sed donec vel pharetra</strong> tellus. Orci, at sed amet, enim luctus odio scelerisque. Purus vitae natoque
        in
        lacus suspendisse accumsan <a href="#">tempor faucibus nam</a>. Pulvinar nisl pellentesque congue lectus turpis
        ornare. Elementum,
        in tincidunt duis nulla sagittis. Lectus nunc velit, cursus donec magna leo massa, faucibus ac. Risus commodo eu
        urna, aenean nulla mi orci, leo.</p>
        <p><strong>Sollicitudin mi sed faucibus tellus risus, erat imperdiet nunc</strong>. Mi massa fames consequat
        nulla.
        Consectetur at
        nascetur facilisis pretium interdum gravida. Elit, nisi, ipsum fames tortor, tempor morbi et. Pellentesque sed
        risus mattis ut dictum. Lacinia aliquam habitasse in scelerisque. Tristique tincidunt vestibulum viverra sed
        tincidunt massa. Tortor facilisis malesuada ac fermentum. <a href="#">Euismod phasellus arcu</a> a, in nam.
        Mollis donec nunc orci
        tristique venenatis porttitor consectetur et, amet. Velit, tempor non sit massa gravida quam fringilla. Sodales
        est donec non arcu, volutpat. In volutpat rhoncus eget ac mi consequat. Sodales lectus adipiscing diam egestas
        ut quis id nunc. Tristique ac, nulla adipiscing viverra convallis pharetra, est, cras tempus.
        </p>
        <p>Turpis diam sit sed suspendisse. Volutpat tristique faucibus at lorem purus accumsan consectetur. Eget gravida
        ullamcorper a et. Nunc malesuada dolor ultrices mattis. Rhoncus erat curabitur aliquam vitae eget turpis. Lorem
        vitae ut metus egestas amet eget neque. Ultrices sem massa urna, cum condimentum dignissim lectus proin. Euismod
        tempor, nulla nulla diam. Quisque elit morbi proin ut auctor ipsum. Mi ut ut gravida integer a.</p>
        <p>Amet, nam turpis id dignissim tortor tempor fames convallis suscipit. Eu venenatis arcu amet diam nullam nec, a
        morbi porttitor. Nulla blandit pulvinar elementum turpis imperdiet venenatis metus. Blandit eget non, at turpis
        suspendisse elementum arcu dictum accumsan. Tincidunt porttitor pretium tellus eu, ut. Risus, aenean aliquam
        ligula rutrum pretium et, morbi risus, sit. Porta nec amet sed viverra interdum fringilla tincidunt. Aliquam
        donec
        massa venenatis libero pellentesque. At eget felis lorem felis. Blandit eget eget ultricies amet, consequat
        lacus
        hendrerit vitae. Elit auctor tincidunt tellus id mauris, posuere leo viverra.
        </p>
    </article>
    </div>
    </body>
</html>
```

Starting CSS file:
```css
/* fonts */
/* 
    font-family: 'Cinzel', serif;
    font-family: 'PT Serif', serif;
*/

/* step 1: select the body */

.container {
    width: 90%;
    max-width: 39rem;
    margin: 0 auto;
}
```

It's a good idea to change the text color and the font-size to make everything look bigger. 

```css
body {
    color: steelblue;
    font-size: 2rem;
}

.container {
    width: 90%;
    max-width: 39rem;
    margin: 0 auto;
}
```

If you are not sure what something happened, hit ctrl + shift + i and inspect the element.  

text color is inherited, font-size is not inherited. The browser's default font size takes presedence over the body tag font size.  

The "user agent styles sheet" is the browser default for text and layout. It will overide anything that's inherited from a parent.  

To override the browser default, inspect the element y see if the css you put was crossed off. If it was crossed off you can include css at the element level to override the browser default.

Here the font-size was overriden so css at the h1 tag was added.  
```css
body {
    color: steelblue;
    font-size: 2rem;
}
h1 {
   font-size: 6rem;
}
```

Added the line height and the font-size was changed to 1.125 to increase the font size of the text inside <p> to 18 (16 * 1.125). 
```css
body {
    font-size: 1.125rem;
    line-height: 1.6;
}
h1 {
   font-size: 6rem;
}
```

Think about how many styles you can put on the body so you won't have to repeat the same styling somewhere else. 

```css
body {
   margin: 0;
   font-size: 1.125rem;
   line-height: 1.6;
   color: #414141;
}
h1 {
   font-size: 6rem;
}
```
Color is inherited and is a layout rule so it will affect the whole page. Margin: 0 to get rid of the browser margin default frame. Margin is layout related and is not inherited.  







