# Switch

<br><br>

# Guides
- https://www.w3schools.com/js/js_switch.asp

<br><br>

```javascript
switch("Banana") {
  case "Banana":
    alert("Hello")
    break;
  case "Apple":
    alert("Welcome")
    break;
  default:
    alert("Neither");
}
```

<br><br>


# Use unique scope for each case
```javascript
// This will not work because result is already definied. (Uncaught SyntaxError: Identifier 'result' has already been declared)
switch("Banana") {
  case "Banana":
    const result = true
    console.log("Banana");
    break;
  case "Apple":
    const result = true
    console.log("Apple");
    break;
  default:
    alert("Neither");
}



// This will will work because each case got now his own scope.
switch("Banana") {
  case "Banana": {
    const result = true
    console.log("Banana");
    break;
  }
  case "Apple": {
    const result = true
    console.log("Apple");
    break;
  }
  default:
    alert("Neither");
}
```
