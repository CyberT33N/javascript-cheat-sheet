# Map

# Guides
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map

```javascript
const currencyMap = new Map([
  ["United States", "USD"],
  ["India", "Rupee"],
])
console.log(currencyMap);
```


 <br><br>

# .set and .get
```javascript
// ---- EXAMPLE #1 ----
const currencyMap = new Map([])
currencyMap.set("United States", "USD")
console.log(currencyMap);

const currency = currencyMap.get("United States")
console.log(currency);


// ---- EXAMPLE #2 - Use Object ----
const currencyMap = new Map([])
const usa = {name: "United States"}
currencyMap.set(usa, "USD")
console.log(currencyMap);

const currency = currencyMap.get(usa)
console.log(currency);
```


<br><br>

# loop
```javascript
var myMap = new Map();
myMap.set(0, "zero");
myMap.set(1, "one");
for (var [key, value] of myMap) {
  console.log(key + " = " + value);
}
// 0 = zero
// 1 = one

for (var key of myMap.keys()) {
  console.log(key);
}
// 0
// 1

for (var value of myMap.values()) {
  console.log(value);
}
// zero
// one

for (var [key, value] of myMap.entries()) {
  console.log(key + " = " + value);
}
// 0 = zero
// 1 = one
```




<br><br>

# .groupBy()
- The Map.groupBy() method groups elements of an object according to string values returned from a callback function.
- The Map.groupBy() method does not change the original object.
```javascript
// Create an Array
const fruits = [
  {name:"apples", quantity:300},
  {name:"bananas", quantity:500},
  {name:"oranges", quantity:200},
  {name:"kiwi", quantity:150}
];

// Callback function to Group Elements
function myCallback({ quantity }) {
  return quantity > 200 ? "ok" : "low";
}

// Group by Quantity
const result = Map.groupBy(fruits, myCallback);
```
