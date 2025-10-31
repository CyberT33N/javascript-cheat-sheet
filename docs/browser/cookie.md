# Cookie

## Get value of specific cookie
```javascript
var regex = /MyCookie=(.[^;]*)/ig;
var match = regex.exec(document.cookie);
var value = match[1];
```
