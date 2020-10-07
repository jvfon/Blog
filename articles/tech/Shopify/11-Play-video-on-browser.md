# Play video on browser

Go to pexels.com and search for a video.

Click on the video and then hit ctrl + i to inspet the page.

Right click on the video to and click on "inspect".  

Ctrl + F to search for "iframe".

Hover on top of the iframe area and right click, choose "inspect as Html". Copy the code. That's the video player.

Put the code above the image.  
```
<section id="jumbo">
   <iframe allowfullscreen="" class="bg-video" frameborder="0" mozallowfullscreen=""
      src="//player.vimeo.com/video/353546049?title=0&amp;portrait=0&amp;byline=0&amp;autoplay=1"
      style="background: white;" webkitallowfullscreen=""></iframe>

   <div class="store-info">
      <img src="assets/jumbobg.jpg" alt="store">
   </div>
</section>
```  

After "autoplay=1" put "```&loop=1```".  

On css do:
```
#jumbo .bg-video {
    height: 100%;
    width: 100%;
    position: absolute;
    z-index: 1;
    top: 0;
    transform: scale(1.5); 
}
```
"transform: scale(1.5);" makes video fill the whole screen.  
