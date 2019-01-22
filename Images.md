How to handle Image Heavy Site? 

- cloudinary, imageKit, [Client Hints](https://developers.google.com/web/updates/2015/09/automating-resource-selection-with-client-hints), [webp](https://developers.google.com/speed/webp/)
- image size : have an image server and reszie the image real time based on the requested size. 
- image resolution 
- responsive images, deciding the image size based on the screen
```
<img srcset="image-320w.jpg 1x,
             image-640w.jpg 2x
     src="image-320w.jpg" alt="Image">
```

- lazy loading
- CDN! 
