# Animate the header

### Create a timeline
Set up the timeline:
```js
const headerTl = gsap.timeline();
headerTl
.fromTo(
    "header", /* targeting the element of header */
    {
        backgroundColor: "rgba(0,0,0,0)"
    },
    {
        backgroundColor: "rgba(0,0,0, 1)",
        duration: 1
    }
)
```

Now add scroll magic.   
```js
