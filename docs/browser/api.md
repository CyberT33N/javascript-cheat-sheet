# API

# Enter fullscreen (https://developers.google.com/web/fundamentals/native-hardware/fullscreen/)
- Doesn´t work on ios..


```html
<button id="goFS">Go fullscreen</button>
<script>
 $("#goFS").on("click",function(){
      
   // this works with scroll -  do not use document.body.requestFullscreen();   
   const elem = document.documentElement;
   if (elem.requestFullscreen) {elem.requestFullscreen()}

      if(document.fullscreenElement) console.log('fullscreen detected');

  
 });
</script>
```
