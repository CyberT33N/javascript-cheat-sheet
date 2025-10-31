# Javascript Internal

# .setTimeout (https://www.w3schools.com/jsref/met_win_settimeout.asp)
```javascript
// -- Example 1 --
var myVar;

function myFunction() {
  myVar = setTimeout(alertFunc, 3000);
}

function alertFunc() {
  alert("Hello!");
}



// -- Example 2 --
setTimeout(() => {
  // do something..
}, 3000)
```


<br><br>

# .clearTimeout (https://www.w3schools.com/jsref/met_win_cleartimeout.asp)
```javascript
var myVar;

function myFunction() {
  myVar = setTimeout(function(){ alert("Hello"); }, 3000);
}

function myStopFunction() {
  clearTimeout(myVar);
}
```
