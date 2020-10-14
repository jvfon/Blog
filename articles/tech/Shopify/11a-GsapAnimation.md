# Gsap animation

File structure:
projects/ js-animations/ gsap/ css, js.  

Go to https://greensock.com/docs/v3/Installation and choose how you want to install Gsap.

If you donwloaded the zip file, unzip the zip file in the js directory.

Go to the folder "minified" copy the file "gsap.min.js" and paste it in the "js" folder.  

In the ```<body>``` tag put the script with the location of the file:
```
 <script src="js/gsap.min.js"></script>
```

Example:
```
gsap.to('h1', {duration: 1, x: 500});
```
The h1 tag is selected, moved 500 pixels horizontally and the duration of the animation is 1 second.  

With gsap.from, the animation starts at 500 pixels on the x axis.  
```
gsap.from('h1', {duration: 1, x: 500});
```

fromTo = the animation starts at a certain point and then moves to another part of the page.
```
gsap.fromTo('h1', {x: 500, y: 500}, {x: 0, y: 100, duration: 1});
```

You can put the tween in a variable
```
let tween1 = gsap.to('h1', {duration: 1, x: 500});
```  
Go to https://greensock.com/docs/v3/GSAP to read about additional methods.  

Go to https://greensock.com/docs/v3/GSAP/Tween for tween methods.  

```
<head>
        <meta charset="UTF-8">
        <meta content="width=device-width, initial-scale=1.0" name="viewport">
        <title>Gsap Course</title>
        <style>
        #container {
            background: black;
            height: 500px;
            width: 500px;
        }
        #box {
            background: red;
            height: 100px;
            width: 100px;
        }
        .button1, .button2, .button3, .button4 {
            background: grey;
            padding: 20px;
            width: 60px;
            display: inline-block;
        }
        .button1:hover, .button2:hover, .button3:hover, .button4:hover {
            background: blue;
            cursor: pointer;
        }
    </style>
    </head>
    <body>
        <div id="container">
            <div id="box"></div>
        </div>
        <div class="button1">Run</div>
        <div class="button2">Play</div>
        <div class="button3">Pause</div>
        <div class="button4">Reverse</div>

        <script src="js/gsap.min.js"></script>
        <script>

        let button1 = document.querySelector('.button1');
        let button2 = document.querySelector('.button2');
        let button3 = document.querySelector('.button3');
        let button4 = document.querySelector('.button4');
        let tween1;    
        button1.addEventListener('click', () => {
            tween1 = gsap.fromTo('#box', {x: 400, y: 400}, {x: 0, y: 0, rotation: '+=360', duration: 3});
        })
        button2.addEventListener('click', () => {
            tween1.play()
        })
        button3.addEventListener('click', () => {
            tween1.pause()
        })
        button4.addEventListener('click', () => {
            tween1.reverse()
        })

    </script>
</body>
```
0,0 is the top left corner.  

Other methods you can use are "rotation" and duration". 

The object's rotation axis is the top left corner. To change that, use "transformOrigin".  

Ex: transformOrigin: '0% 100%', it moves the rotation axis from the top left corner to the bottom left corner.  

transformOrigin: '50% 50%' will move the rotation axis to the center of the object.  







