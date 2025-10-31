# While

# Guides
 - https://www.w3schools.com/js/js_loop_while.asp

<br><br>

# Do loop based on length of array
```javascript

var cars = ["BMW", "Volvo", "Saab", "Ford"];
var i = 0;
var text = "";

while (cars[i]) {
  text += cars[i] + "<br>";
  i++;
}
console.log('text: ' + text);
```





<br><br>

# do/while statement

Syntax:
```javascript
do {
  code block to be executed
}
while (condition);
```

<br><br>

```javascript
var text = "";
var i = 0;
do {
  text += "The number is " + i;
  i++;
}
while (i < 5);
```
