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

```
tween1 = gsap.fromTo('#box', 
{x: 400, y: 400, width: '100px', height: '100'}, 
{x: 400, y: 400, width: '200px', height: '200', rotation: '+=360', repeat: -1, rotationOrigin: '50% 50%', duration: 3});
```
Changing the width and height of the object from start to finish.  

```
tween1 = gsap.fromTo('#box', 
{x: 400, y: 400, width: '100px', height: '100', borderRadius: 0}, 
{x: 400, y: 400, width: '200px', height: '200', borderRadius: '50%', rotation: '+=360', repeat: 1, rotationOrigin: '50% 50%', duration: 1});
```
With borderRadius, the object changes from square to circle at the end of the animation.  

The "yoyo" method needs the "repeat" method.  

"paused: true", the object won't run after you hit "run" but rather will run after you hit "play".  

"runBackwards: true", the animation starts from the end to the beginning.  

```
onStart: () => {
      console.log('Started')
}
}
);
```
You can trigger a function also.  
```
button1.addEventListener('click', () => {
   tween1 = gsap.fromTo('#box', 
   {x: 0, y: 0, background: 'red', width: '100px', height: '100', borderRadius: 0}, 
   {x: 200, y: 200, background: 'black', width: '200px', height: '200', borderRadius: '50%', rotation: '+=360', repeat: 1, 
   rotationOrigin: '50% 50%', duration: 1,
   runBackwards: true,
   onStart: () => {
         console.log('Started')
   },
   onComplete: () => {
         console.log('Completed')
   }
});
})
```  
Find out more about gsap properties here: https://greensock.com/docs/v3/GSAP/Tween


## Ease
"Ease" changes the timing of the tweens. https://greensock.com/docs/v3/Eases.  Use it in conjuction with "duration".  

You can also customize ease but you need to download a zip file from greensock.com. Place the file CustomEase.min.js in the "js" folder and then link it in HTML
```
<script src="js/CustomEase.min.js"></script>
```

You can also use cubic bezier for your animation: https://cubic-bezier.com/#.17,.67,.83,.67, but it only gives you 2 points to edit.  

## Stagger
Stagger allows you to time the start of the animation. 
```
stagger: 1,
```
This will make an animation wait 1 second before it starts.  

```
<div id="container">
   <div class="box"></div>
   <div class="box"></div>
   <div class="box"></div>
   <div class="box"></div>
   <div class="box"></div>

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
   tween1 = gsap.fromTo('.box', 
   {
         x: 0, y: 0, background: 'red', width: '100px', height: '100',
         borderRadius: "50%",
         opacity: 0
   }, 
   {
         background: 'yellow',
         x: 400,
         y: 0,
         borderRadius: "50%",
         duration: 1,
         stagger: 1,
         ease: 'bounce.out',
         opacity: 1,
         onStart: () => {
            console.log('Started')
   },
```
Targeting all the elements with the class "box". Stagger will make each element take 1 second before they start. 

## Timelines
Allows you to structure how your animation goes.

Animations start one after the other and you can use all the methods.
```
<body>
   <div id="container">
      <div class="box1"></div>
      <div class="box2"></div>
      <div class="box3"></div>
      <div class="box4"></div>
      <div class="box5"></div>

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

      let boxesT = gsap.timeline({repeat: -1}
      );
      boxesT.to('.box1', { 
         x: 50
      })
      .to('.box2', { 
         x: 100
      })
      .from('.box3', { 
         x: 400,
         y: 400
      })
      .fromTo('.box4', { 
         x: 250,
         y: 250
      }, 
      {
         x: 0,
         y: 400
      })
      .fromTo('.box5', {
         x: 300,
         y: 400
      }, 
      {
         x: 0,
         y: 0,
         scale: 2
      })

      button1.addEventListener('click', () => {

      })
      button2.addEventListener('click', () => {
         boxesT.play()
      })
      button3.addEventListener('click', () => {
         boxesT.pause()
      })
      button4.addEventListener('click', () => {
         boxesT.reverse()
      })

   </script>

</body>
```

CustomEase is a plugin you can download from greensock once you register. 

Labels allow you to control where the animation appears in the timeline. Find the documentation here: https://greensock.com/docs/v3/GSAP/Timeline/addLabel().

### Barba.js
Barba.js a library that allows you to do smooth transitions between your webpages. You can find it here: https://barba.js.org/. It only load the content area of the page not the whole page every time you switch pages.  

Use the npm install if you want to use it with your own websites. Otherwise use the CDN to test websites. 

CDN: use the one that says "unpkg".
```
<!-- unpkg -->
<script src="https://unpkg.com/@barba/core"></script>
```
Copy and paste it above gsap in the index.html file.  

Check if everything is working by inspecting the page. Ctrl + shift + i to inspect, click on "network" and then press ctrl + r to do a test. 

Barba.js has a wrapper and inside, has a container. Changes occur in the container.
```
<body body data-barba="wrapper">
   <header> </header>
   <main data-barba="container" data-barba-namespace="home">
      <section> </section>
   </main>
</body>
```

### Test Barba
Copy and paste the contents of index.html into about.html.

Change the ```<title>``` tag content with "About". Change other tags if necessary to reflect the "About" page.

### Implement barba.js

**1. Step 1:**  
Create a function in the app.js file and put all the js animation code inside the function. 
```
const initialPageAnimation = () => {
   Animation code goes here
}
```

**2. Step 1:**
Set up Barba. Start the code after the function you just created and put the animation inside.  
```
barba.init(
      // passing an object.
   {
      //all the options for barba go here.
   sync: true,
   transition: [   // an array
      //passing an object
      {}
   ]
})
```
```


Controlling how barba goes to the next page. 
```
barba.init({
    sync: true,

    // controlling when barba goes to the next page.
    transitions: [   // an array
        {           // passing an object
            name: 'page-wipe',  // name of the transition
            async leave(data){   // a function
                const done = this.async();  // creating the varibale "done" and telling barba the action is complete.
                console.log('Leaving Page Animation'); // the animation
                await delay(2000); // await until the function finishes
                done(); // calling the variable "done". Barba know animation is done
            },
            async enter(data){
                console.log('Entering Page Animation');
            }     
        }
    ]
})
```  

The full code:
```
const initialPageAnimation = () => {
    let tl = gsap.timeline()
    tl.fromTo('.logo', { 
        x: -200,
        opacity: 0
    },{
        x: 0,
        opacity: 1,
        delay: .5,
        duration: 1.3
    })

    .fromTo('.menu', { 
        x: 200,
        opacity: 0
    },{
        x: 0,
        opacity: 1,
        delay: 0.5,
        duration: 1.3
    },
    ">-1.8"
    )

    .fromTo('.info-section h1', { 
        x: 0,
        y:100,
        opacity: 0
    },{
        x: 0,
        y: 0,
        opacity: 1,
        duration: 1.3
    })

    .addLabel("h1Show")

    .fromTo('.girl', { 
        height: 0,
    },{
        height: 600,
        duration: 1.4,
        ease: "power2.out"
    },
    ">-.5"
    )
    .fromTo('.boy', { 
        height: 0,
    },{
        height: 600,
        duration: 1.4,
        ease: "power2.out"
    },
    ">-1"
    )
    .fromTo('.shape1', { 
        scale: .1,
        opacity: 0
    },{
        scale: 1,
        opacity: 1,
        ease: "power2.out"
    },
    ">-1"
    )
    .fromTo('.shape3', { 
        opacity: 0
    },{
        opacity: .6,
        ease: "power2.out",
        duration: .3
    },
    ">-.1"
    )
    .fromTo('.shape3', { 
        x: -50,
        y: 500
    },{
        y: 465,
        repeat: -1,
        duration: 2.5,
        ease: "sine.out",
        yoyo: true
    },
    ">.009"
    )
    .fromTo('.shape2', { 
        
        opacity: 0
    },{
        opacity: .3,
        ease: "power2.out",
        duration: .5
    },
    ">-1.8"
    )
    .fromTo('.shape2', { 
        x: 500,
        y: -150
    },{
        y: -185,
        repeat: -1,
        duration: 1.5,
        ease: "sine.out",
        yoyo: true
    },
    ">-.1"
    )
    .fromTo('.info-section h4', { 
        x: -50,
        opacity: 0
    },{
        x: 0,
        opacity: 1,
        duration: .5
    },
    "h1Show"
    )
    .fromTo('.call-actions', { 
        x: -50,
        opacity: 0
    },{
        x: 0,
        opacity: 1,
        duration: .5
    },
    "h1Show+=1"
    );    
}

const delay = (n) => {
    return new Promise(() => {
        setTimeout(() => {
            done();  
        }, n) // passing the "n", how long the setTimeout will run.  
    })
}
barba.init({
    sync: true,

    // controlling when barba goes to the next page.
    transitions: [   // an array
        {           // passing an object
            name: 'page-wipe',  // name of the transition
            async leave(data){   // a function
                const done = this.async();  // creating the varibale "done" and telling barba the action is complete.
                console.log('Leaving Page Animation'); // the animation
                await delay(2000); // await until the function finishes
                done(); // calling the variable "done". Barba know animation is done
            },
            async enter(data){
                console.log('Entering Page Animation');
            }     
        }
    ]
})
```








