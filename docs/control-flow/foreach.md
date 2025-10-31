# forEach

# Example 	
```javascript
// ---- EXAMPLE #1 ----
var fruits = ["apple", "orange", "cherry"];
fruits.forEach(myFunction);

function myFunction(item, index) {
  console.log(`item: ${item} - index: ${index}`)
}


// ---- EXAMPLE #2 ----
var fruits = ["apple", "orange", "cherry"];
fruits.forEach((item, index) => {
  console.log(`item: ${item} - index: ${index}`)
})
```	


  
# Iterate through all keys of nested object
```javascript
function resetValuesToZero (obj) {
    Object.keys(obj).forEach(function (key) {
        if (typeof obj[key] === 'object') {  // if (typeof obj[key] === 'object' && !Array.isArray(obj[key]) && !_.isEmpty(obj[key])) {
            return resetValuesToZero(obj[key]);
        }
        obj[key] = 0;
    });
}

var stats = {
     bookServed: {
         redis: 90,
         s3: 90,
         signedUrl: 70
     },
     errors: {
         redis: {
             bookService: 70,
             mapi: 50,
             capi: 30
         },
         AWS: {
             signedUrl: 70,
             downloadBook: 50,
             searchBook: 10
         },
         decryption: 60
     }
 };

console.log(stats.errors.AWS.signedUrl); // 70
resetValuesToZero(stats);
console.log(stats.errors.AWS.signedUrl); // 0
```




# Pass function
```javascript
var fruit = ['banana', 'apple']

const whatIeat = fruit => {
  console.log(`I eat ${fruit}`)
}

fruit.forEach(whatIeat)
```
