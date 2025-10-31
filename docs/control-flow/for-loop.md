# For loop

# Iterate through all keys of nested object
```javascript
function checkNPE(obj) {
  for(const name in obj){console.log('name: ' + JSON.stringify(name, null, 4));
    if (typeof obj[name] === 'object') {console.log('object name: ' + JSON.stringify(name, null, 4));
      checkNPE(obj[name]);
    } // if (typeof obj[name] === 'object') {
  } // for(const name in obj){
}; // function checkNPE (obj) {

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
             downloadBook: 'a',
             searchBook: 10
         },
         decryption: 60
     }
 };
checkNPE(stats);
```


<br><br>

  
# Do loop based on length of array
```javascript
var cars = ["BMW", "Volvo", "Saab", "Ford"];
var i = 0;
var text = "";

for (;cars[i];) {
  text += cars[i] + "<br>";
  i++;
} console.log('text: ' + text); // text: BMW<br>Volvo<br>Saab<br>Ford<br>
```

<br><br>

# Make the loop jump to the next iteration when i is 5
```javascript
for (i = 0; i < 10; i++) {
  if (i == 5) continue;
  console.log(i);
}
```

<br><br>

# break the loop when i is 5
```javascript
for (i = 0; i < 10; i++) {
  if (i == 5) break;
  console.log(i);
}
```



<br><br>

# Get key and value of object
```javascript
// Example #1
const object1 = {
  a: 'somestring',
  b: 42
};

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// expected output:
// "a: somestring"
// "b: 42"
// order is not guaranteed
	
	
	
	
// Example #2	
const documents = [ {__v: '1.2', modelName: 'test'} ]	

for (const { __v: newVersion, modelName } of documents) {
    console.log('newVersion': + newVersion)
    console.log('modelName': + modelName)
}	
```





<br><br>

# label (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/label)

<br><br>

## Using a labeled continue with for loops
```javascript
var i, j;

loop1:
for (i = 0; i < 3; i++) {      //The first for statement is labeled "loop1"
   loop2:
   for (j = 0; j < 3; j++) {   //The second for statement is labeled "loop2"
      if (i === 1 && j === 1) {
         continue loop1;
      }
      console.log('i = ' + i + ', j = ' + j);
   }
}

// Output is:
//   "i = 0, j = 0"
//   "i = 0, j = 1"
//   "i = 0, j = 2"
//   "i = 1, j = 0"
//   "i = 2, j = 0"
//   "i = 2, j = 1"
//   "i = 2, j = 2"
// Notice how it skips both "i = 1, j = 1" and "i = 1, j = 2"
```



<br><br>

## Using a labeled break with for loops
```javascript
var i, j;

loop1:
for (i = 0; i < 3; i++) {      //The first for statement is labeled "loop1"
   loop2:
   for (j = 0; j < 3; j++) {   //The second for statement is labeled "loop2"
      if (i === 1 && j === 1) {
         break loop1;
      }
      console.log('i = ' + i + ', j = ' + j);
   }
}

// Output is:
//   "i = 0, j = 0"
//   "i = 0, j = 1"
//   "i = 0, j = 2"
//   "i = 1, j = 0"
// Notice the difference with the previous continue example
```

	
	
	
	

<br><br>

## Endless loop
```javascript
for (;;) {
  //..
}
```
	
	
<br><br>

## Get index of array
```javascript
for (let [index, val] of array.entries()) {
  // your code goes here    
}
```
