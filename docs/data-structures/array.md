# Array

# Clone unique
For default javascript act like this:
```js
var arr1 = ['a','b','c'];
var arr2 = arr1;
arr2.push('d');  //Now, arr1 = ['a','b','c','d']
```

In order to create unique clones check below..

<br><br>

# clone array
```js
var arr = [2,3,4,5];
var copyArr = [...arr];
```
<br><br>

# clone array with objects inside
```js
var arr = [{"a":1}, {"b":2}];
var copyArr = JSON.parse(JSON.stringify(arr));
```

<br><br>

# get random item from array
```js
var rndval=items[Math.floor(Math.random()*items.length)];
```






<br><br>

## .from() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
- The Array.from() static method creates a new, shallow-copied Array instance from an array-like or iterable object.
```javascript
console.log(Array.from('foo'));
// expected output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], x => x + x));
// expected output: Array [2, 4, 6]
```






<br><br>

# prototype


<br><br>

## .values() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/values)
- The values() method returns a new Array Iterator object that contains the values for each index in the array.
```javascript
const array1 = ['a', 'b', 'c'];
const iterator = array1.values();

for (const value of iterator) {
  console.log(value);
}

// expected output: "a"
// expected output: "b"
// expected output: "c"
```

<br><br>

## .unshift() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
- The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.
```javascript
const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// expected output: 5

console.log(array1);
// expected output: Array [4, 5, 1, 2, 3]
```

<br><br>

## .splice() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
- The splice() method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.
```javascript
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// replaces 1 element at index 4
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "May"]
```

<br><br>

## .sort() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
- The sort() method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.
```javascript
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]
```

<br><br>

## .some() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)
- The some() method tests whether at least one element in the array passes the test implemented by the provided function. It returns a Boolean value.
```javascript
const array = [1, 2, 3, 4, 5];

// checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// expected output: true
```

<br><br>

## .slice() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
- The slice() method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.
```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]
```

<br><br>

## .shift() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
- The shift() method removes the first element from an array and returns that removed element. This method changes the length of the array.
```javascript
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// expected output: Array [2, 3]

console.log(firstElement);
// expected output: 1
```

<br><br>

## .reverse() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)
- The reverse() method reverses an array in place. The first array element becomes the last, and the last array element becomes the first.
```javascript
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);
// expected output: "array1:" Array ["three", "two", "one"]
```


<br><br>

## .reduce() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)
- The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in single output value.
```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15
```

<br><br>

## .push() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
- The push() method adds one or more elements to the end of an array and returns the new length of the array.
```javascript
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// expected output: 4
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]
```

<br><br>

## .pop() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
- The pop() method removes the last element from an array and returns that element. This method changes the length of the array.
```javascript
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// expected output: "tomato"

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop();

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage"]
```

<br><br>

## .keys() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/keys)
- The keys() method returns a new Array Iterator object that contains the keys for each index in the array.
```javascript
const array1 = ['a', 'b', 'c'];
const iterator = array1.keys();

for (const key of iterator) {
  console.log(key);
}

// expected output: 0
// expected output: 1
// expected output: 2
```


<br><br>

## .join() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
- The join() method creates and returns a new string by concatenating all of the elements in an array (or an array-like object), separated by commas or a specified separator string. If the array has only one item, then that item will be returned without using the separator.
```javascript
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// expected output: "Fire,Air,Water"

console.log(elements.join(''));
// expected output: "FireAirWater"

console.log(elements.join('-'));
// expected output: "Fire-Air-Water"
```

<br><br>

## .indexOf() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
- The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.
```javascript
const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// expected output: 1

// start from index 2
console.log(beasts.indexOf('bison', 2));
// expected output: 4

console.log(beasts.indexOf('giraffe'));
// expected output: -1
```


<br><br>

## .includes() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
- The includes() method determines whether an array includes a certain value among its entries, returning true or false as appropriate.
```javascript
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// expected output: true

const pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat'));
// expected output: true

console.log(pets.includes('at'));
// expected output: false
```

<br><br>

## .forEach() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- The flat() method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.
```javascript
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// expected output: "a"
// expected output: "b"
// expected output: "c"
```



<br><br>

## .flat() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)
- The flat() method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.
```javascript
const arr1 = [0, 1, 2, [3, 4]];

console.log(arr1.flat());
// expected output: [0, 1, 2, 3, 4]

const arr2 = [0, 1, 2, [[[3, 4]]]];

console.log(arr2.flat(2));
// expected output: [0, 1, 2, [3, 4]]
```


<br><br>

## .findIndex() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
- The findIndex() method returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test.
```javascript
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// expected output: 3
```


<br><br>

## .find() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
- The find() method returns the value of the first element in the provided array that satisfies the provided testing function. If no values satisfies the testing function, undefined is returned.
```javascript
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// expected output: 12
```

<br><br>

## .filter() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
- The filter() method creates a new array with all elements that pass the test implemented by the provided function.
```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

<br><br>

## .fill() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)
- The fill() method changes all elements in an array to a static value, from a start index (default 0) to an end index (default array.length). It returns the modified array.
```javascript
const array1 = [1, 2, 3, 4];

// fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// expected output: [1, 2, 0, 0]

// fill with 5 from position 1
console.log(array1.fill(5, 1));
// expected output: [1, 5, 5, 5]

console.log(array1.fill(6));
// expected output: [6, 6, 6, 6]
```


<br><br>

## .every() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries)
- The every() method tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value.
```javascript
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// expected output: true
```


<br><br>

## .entries() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries)
- The entries() method returns a new Array Iterator object that contains the key/value pairs for each index in the array.
```javascript
const array1 = ['a', 'b', 'c'];

const iterator1 = array1.entries();

console.log(iterator1.next().value);
// expected output: Array [0, "a"]

console.log(iterator1.next().value);
// expected output: Array [1, "b"]
```


<br><br>

## .concat() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
- The concat() method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.
```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```



<br><br>

## .copyWithin() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)
- The copyWithin() method shallow copies part of an array to another location in the same array and returns it without modifying its length.
```javascript
const array1 = ['a', 'b', 'c', 'd', 'e'];

// copy to index 0 the element at index 3
console.log(array1.copyWithin(0, 3, 4));
// expected output: Array ["d", "b", "c", "d", "e"]

// copy to index 1 all elements from index 3 to the end
console.log(array1.copyWithin(1, 3));
// expected output: Array ["d", "d", "e", "d", "e"]
```

<br><br>

## .map() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- https://www.w3schools.com/jsref/jsref_map.asp
- The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.
```javascript
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```
	
<br><br>
	
### await
```
async function readAllJsonFiles() {
  const fs = require('fs-extra');
  const path = require('path');

  const directoryPath = './test/SchemaEntities';

  try {
    const files = await fs.readdir(directoryPath);

    const fileContents = await Promise.all(
      files.map(async (filename) => {
        const filePath = path.join(directoryPath, filename);
        const fileContent = await fs.readJson(filePath);
        return fileContent;
      })
    );

    console.log(fileContents);
  } catch (err) {
    console.error(err);
  }
}
```
















<br><br>


#### Convert Array to Array with Objects
```javascript
var years = [
  1990,
  1991,
  1992,
  1993,
];

let docs = years.map((year, idx) => ({
  title: `Mega Man ${idx + 1}`,
  year,
}));

console.log(docs);
/*
[
  {
    "title": "Mega Man 1",
    "year": 1990
  },
  {
    "title": "Mega Man 2",
    "year": 1991
  },
  {
    "title": "Mega Man 3",
    "year": 1992
  },
  {
    "title": "Mega Man 4",
    "year": 1993
  }
]
*/
```

<br><br>



<br><br>


#### .flatMap()
**Beschreibung**: `flatMap()` ist eine Methode, die auf Arrays angewendet wird. Sie kombiniert die Funktionalität von `map()` und `flat()`, um ein Array zu erstellen, das sowohl transformiert als auch flach gemacht wird.

```javascript
const zahlen = [1, 2, 3];

// Verwende flatMap, um jede Zahl zu verdoppeln und das Ergebnis zu glätten
const verdoppelt = zahlen.flatMap(x => [x * 2]);

console.log(verdoppelt); // [2, 4, 6]
```


<br><br>

#### .findLast()
- ES2023 added the findLast() method that will start from the end of an array and return the value of the first element that satisfies a condition.

```javascript
const temp = [27, 28, 30, 40, 42, 35, 30];
let high = temp.findLast(x => x > 40);
```


<br><br>


#### .findLastIndex()
- ES2023 The findLastIndex() method finds the index of the last element that satisfies a condition.

```javascript
const temp = [27, 28, 30, 40, 42, 35, 30];
let pos = temp.findLastIndex(x => x > 40);
```


<br><br>



#### .toReversed()
- ES2023 added the Array toReversed() method as a safe way to reverse an array without altering the original array. The difference between the new toReversed() method and the old reverse() method is that the new method creates a new array, keeping the original array unchanged, while the old method altered the original array.
```javascript
const months = ["Jan", "Feb", "Mar", "Apr"];
const reversed = months.toReversed();
```


<br><br>



#### .toSorted()
- ES2023 added the Array toSorted() method as a safe way to sort an array without altering the original array.

The difference between the new toSorted() method and the old sort() method is that the new method creates a new array, keeping the original array unchanged, while the old method altered the original array.
```javascript
const months = ["Jan", "Feb", "Mar", "Apr"];
const sorted = months.toSorted();
```


<br><br>



#### .toSpliced()
- ES2023 added the Array toSpliced() method as a safe way to splice an array without altering the original array.

The difference between the new toSpliced() method and the old splice() method is that the new method creates a new array, keeping the original array unchanged, while the old method altered the original array.
```javascript
const months = ["Jan", "Feb", "Mar", "Apr"];
const spliced = months.toSpliced(0, 1);
```

<br><br>




<br><br>



#### .with()
- ES2023 added the Array with() method as a safe way to update elements in an array without altering the original array.
```javascript
const months = ["Januar", "Februar", "Mar", "April"];
const new = months.with(2, "March");
```


<br><br>



#### .findIndex()
- Die findIndex()-Methode von Array-Instanzen gibt den Index des ersten Elements in einem Array zurück, das die bereitgestellte Testfunktion erfüllt. Wenn kein Element die Testfunktion erfüllt, wird -1 zurückgegeben.
```javascript
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// Expected output: 3
```

<br><br>













<br><br>
<br><br>

# remove all duplicates from an array
Method 1:
```
const _ = require('lodash')
const uniqAr = _.uniqWith(arrayHere, _.isEqual);
```


Method 2
```javascript
const a = ['name']
const b = ['name', 'weight']
	
const concatedArray = Array.from(new Set(a.concat(b)))
	

// single array
const b = ['name', 'name', 'weight']	
const concatedArray = Array.from(new Set(b.concat(b)))
```
	
	
<br><br>
	

## remove all duplicates from an array of objects by property
- https://stackoverflow.com/questions/2218999/how-to-remove-all-duplicates-from-an-array-of-objects
```javascript
# Find unique id's in an array.
arr.filter((v,i,a)=>a.findIndex(t=>(t.id === v.id))===i)

# Unique by multiple properties ( place and name )
arr.filter((v,i,a)=>a.findIndex(t=>(t.place === v.place && t.name===v.name))===i)

# Unique by all properties (This will be slow for large arrays)
arr.filter((v,i,a)=>a.findIndex(t=>(JSON.stringify(t) === JSON.stringify(v)))===i)
```

	
<br><br>
	

## remove all duplicates from an array of objects
- https://stackoverflow.com/questions/2218999/how-to-remove-all-duplicates-from-an-array-of-objects
```javascript
# method #1
var objects = [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }, { 'x': 1, 'y': 2 }];
_.uniqWith(objects, _.isEqual);
// => [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }]
	
# method 2
const unique = [...new Map(arr.map(item => [item[key], item])).values()]
```





<br><br>


# Destructuring
```javascript
let ar = ['banana', 'apple']

let [a, b] = ar

console.log(a); // banana
console.log(b); // apple
```





<br><br>


# Freeze Array
```javascript
const ar = Object.freeze(['banana'])
ar.push('apple')
console.log(ar)
```

	
	
	
	
<br><br>


# Compare two unsorted arrays
```javascript
var _ = require('lodash')
const checkArraysResult = _.isEmpty(_.xor(arr1, arr2))
```

	
		
	
<br><br>


# Check if type is array
```javascript
var ar = []
console.log(Array.isArray(ar)) // true
```

	
	
	
	
	
		
<br><br>


# Remove element from array by value
```javascript
// Method #1
var ary = ['three', 'seven', 'eleven'];
var filteredAry = ary.filter(e => e !== 'seven')
	
// Method #2
ary = _.without(ary, 'seven')
```

	
	
	
	
		
<br><br>


# Convert array of objects to single object
```javascript
// Method #1
const array = [
  { name: "something", value: "something" },
  { name: "somethingElse", value: "something else" },
];

const newObject = Object.assign({}, ...array.map(item => ({ [item.name]: item.value })));
// >> { something: "something", somethingElse: "something else" }
	
// Method #2
const obj = _.keyBy(arrayOfObjects, 'keyName')
```
	
	
	
	
			
<br><br>


# Replace each element of array
```javascript
const audioList = ["song1", "song2", "song3", "song3"];

const res = audioList.map(audio => ({ audio, played: false }));

console.log(res);
```
	
				
<br><br>


# Check if an array contains any element of another array
```javascript
// ES2016:
const found = arr1.some(r=> arr2.includes(r))

// ES6:
const found = arr1.some(r=> arr2.indexOf(r) >= 0)
```
	
	
	
				
<br><br>


# Check if an array contains any object of another array and then overwrite it
```javascript
let project = [{ _id: 1, name: 'Project 1' }, { _id: 2, name: 'Project 2' }];
let common = [{ _id: 3, name: 'Common 1' }, { _id: 2, name: 'Common 2' }];

let filteredCommon = common.filter(c => !project.some(p => p._id === c._id));
let result = project.concat(filteredCommon);

console.log(result);
/*
This will output:
[
  { _id: 1, name: 'Project 1' },
  { _id: 2, name: 'Project 2' },
  { _id: 3, name: 'Common 1' }
]
*/
```
