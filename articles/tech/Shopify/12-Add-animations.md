# Add animations

Use different libraries: Gsap (https://greensock.com/gsap/) and scroll magic (https://scrollmagic.io/).

Go to a html page, scroll down the page and put JS code there.  

Copy and paste the CDN from https://scrollmagic.io/  

Copy and paste gsap's CDN from cdnjs.com 

Google "scrollmagic gsap plugin cdn". 

You can find most of the code from here: https://cdnjs.com

```
    </footer>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js"></script>
    <script src="//cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/ScrollMagic.min.js"></script>
    <script src="//cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/plugins/debug.addIndicators.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/plugins/animation.gsap.min.js"></script>
    <script src="assets/app.js"></script>
</body>
```
```<script src="assets/app.js"></script>``` to connect to the your js file.  

To check if everything is working, got to your active webpage and inspect it (ctrl + shift + i). Click on the console tab.  

You can create a simple animation that targets an element from the webpage to test if all the scripts are working.
```
let tl = gsap.timeline();
tl.fromTo(
    "#jumbo .titles h1",
    {
        x: -100,
        opacity: 0
    },
    {
        x: 0,
        opacity: 1,
        duration: .5
    }
)
```
# Animate the jumbo

```
let jumboTl = gsap.timeline();

jumboTl.fromTo(
    '#jumbo .transparent-color',
    {
        opacity: 0
    },
    {
        opactiy: 1,
        duration: 1.5
    }
)
```
jumboTl = the name of the timeline.  
'#jumbo .transparent-color', = targeting an element.  
opacity: 0 = start with invisible.  
opactiy: 1 = ends with visible. 
duration: 1.5 = time the animation lasts.  

Make sure the iframe style is black
```
style="background: black;
```

Use ">-1.25" to make the animation start after the previous animation ends.  
```
).fromTo(
    '.menu',
    {
        x: 200,
        opacity: 0
    },
    {
        x: 0,
        opacity: 1,
        duration: 1.3
    },
    '>-1.25'
)
```

Use "stagger: 2" to animate each image within the element one after the other.
```
.fromTo(
    "#jumbo .store-info img",
    {
        y: 400,
        opacity: 0
    },
    {
        y: 0,
        opacity: 1,
        duration: 1,
        stagger: .5
    },
    ">-1.5"
);
```  

