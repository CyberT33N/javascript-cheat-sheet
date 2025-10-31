# Before unload

## Do something when current page / popup windows was closed
```javascript
const popup = window.open('oauth-dialog.html', '_blank', 'width=500,height=500');

popup.onbeforeunload = function(){ /* .. */ };
```
