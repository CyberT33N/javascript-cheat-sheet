# Object

# Naming
```javascript
// name is key

// Peter is key value and also a property
const obj = {
  name: 'Peter',
  age: 23
};
```


<br><br>






# Check if object is empty
```javascript
var obj = {};
if( Object.entries(obj).length < 1 ) console.log('empty');

var obj = {"not": "empty"};
if( Object.entries(obj).length > 0 ) console.log('not empty');
```


<br><br>


# Custom name of function chain
```javascript
// default
banane(true).read(false).write(true)

// custom
banane(true)[customName](false).write(true)
```





<br><br>


# Object is not equal Object
- Objects got own instances and this means they are not equal if you compare them with conditions.
- In order to verify that the content of two objects is the same you must do a deep check.
```javascript
var notEqual = {a: true} === {a: true};
console.log(notEqual); // false

var notEqual = Object.is({a: true}, {a: true})
console.log(notEqual);

var equal = JSON.stringify({a: true}) === JSON.stringify({a: true});
console.log(notEqual); // true
```












<br><br>
<br><br>



# Object constructor
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Object




<br><br>


## .assign() (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
- The Object.assign() method copies all enumerable own properties from one or more source objects to a target object. It returns the target object.
```javascript
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }
```




<br><br>


## .create() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
- The Object.create() method creates a new object, using an existing object as the prototype of the newly created object.
```javascript
const person = {
  isHuman: false,
  printIntroduction: function() {
    console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
  }
};

const me = Object.create(person);

me.name = 'Matthew'; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // inherited properties can be overwritten

me.printIntroduction();
// expected output: "My name is Matthew. Am I human? true"
```












<br><br>


## .defineProperties() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperties)
- The Object.defineProperties() method defines new or modifies existing properties directly on an object, returning the object.
```javascript
const object1 = {};

Object.defineProperties(object1, {
  property1: {
    value: 42,
    writable: true
  },
  property2: {}
});

console.log(object1.property1);
// expected output: 42
```






<br><br>


## .defineProperty() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)
- The static method Object.defineProperty() defines a new property directly on an object, or modifies an existing property on an object, and returns the object.
```javascript
const object1 = {};

Object.defineProperty(object1, 'property1', {
  value: 42,
  writable: false
});

object1.property1 = 77;
// throws an error in strict mode

console.log(object1.property1);
// expected output: 42
```











<br><br>


## .entries() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
- The Object.entries() method returns an array of a given object's own enumerable string-keyed property [key, value] pairs, in the same order as that provided by a for...in loop. (The only important difference is that a for...in loop enumerates properties in the prototype chain as well). 
```javascript
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
```




<br><br>


## .freeze() (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)
- The Object.freeze() method freezes an object. A frozen object can no longer be changed; freezing an object prevents new properties from being added to it, existing properties from being removed, prevents changing the enumerability, configurability, or writability of existing properties, and prevents the values of existing properties from being changed. In addition, freezing an object also prevents its prototype from being changed. freeze() returns the same object that was passed in.
```javascript
// ---- EXAMPLE #1 ----
const obj = {
  prop: 42
};

Object.freeze(obj);

obj.prop = 33; // Throws an error in strict mode

console.log(obj.prop); // expected output: 42



// ---- EXAMPLE #2 ----
const obj = Object.freeze({
  prop: 42
});

obj.prop = 33; // Throws an error in strict mode

console.log(obj.prop); // expected output: 42



// ---- EXAMPLE #3 - Nested objects are not frozen----
const obj = Object.freeze({
  prop: 42,
  adress: {
    street: "1234"
  }
});

obj.adress.street = 33; // Throws an error in strict mode

console.log(obj.adress.street );// expected output: 33
```




<br><br>


## .fromEntries() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries)
- The Object.fromEntries() method transforms a list of key-value pairs into an object.
```javascript
const entries = new Map([
  ['foo', 'bar'],
  ['baz', 42]
]);

const obj = Object.fromEntries(entries);

console.log(obj);
// expected output: Object { foo: "bar", baz: 42 }
```





<br><br>


## .getOwnPropertyNames() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyNames)
- The Object.getOwnPropertyNames() method returns an array of all properties (including non-enumerable properties except for those which use Symbol) found directly in a given object.
```javascript
const object1 = {
  a: 1,
  b: 2,
  c: 3
};

console.log(Object.getOwnPropertyNames(object1));
// expected output: Array ["a", "b", "c"]
```




<br><br>


## .hasOwnProperty() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)
- The hasOwnProperty() method returns a boolean indicating whether the object has the specified property as its own property (as opposed to inheriting it).
```javascript
const object1 = {};
object1.property1 = 42;

console.log(object1.hasOwnProperty('property1'));
// expected output: true

console.log(object1.hasOwnProperty('toString'));
// expected output: false

console.log(object1.hasOwnProperty('hasOwnProperty'));
// expected output: false
```



<br><br>


## .is() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is)
- The Object.is() method determines whether two values are the same value.
```javascript
Object.is('foo', 'foo');     // true
Object.is(window, window);   // true

Object.is('foo', 'bar');     // false
Object.is([], []);           // false

var foo = { a: 1 };
var bar = { a: 1 };
Object.is(foo, foo);         // true
Object.is(foo, bar);         // false

Object.is(null, null);       // true

// Special Cases
Object.is(0, -0);            // false
Object.is(0n, -0n);          // true
Object.is(-0, -0);           // true
Object.is(NaN, 0/0);         // true
```





<br><br>


## .isExtensible() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isExtensible)
- The Object.isExtensible() method determines if an object is extensible (whether it can have new properties added to it).
```javascript
const object1 = {};

console.log(Object.isExtensible(object1));
// expected output: true

Object.preventExtensions(object1);

console.log(Object.isExtensible(object1));
// expected output: false
```



<br><br>


## .isFrozen() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isFrozen)
- The Object.isFrozen() determines if an object is frozen.
```javascript
const object1 = {
  property1: 42
};

console.log(Object.isFrozen(object1));
// expected output: false

Object.freeze(object1);

console.log(Object.isFrozen(object1));
// expected output: true
```


<br><br>


## .isPrototypeOf() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isPrototypeOf)
- The isPrototypeOf() method checks if an object exists in another object's prototype chain.
```javascript
function object1() {}
function object2() {}

object1.prototype = Object.create(object2.prototype);

const object3 = new object1();

console.log(object1.prototype.isPrototypeOf(object3));
// expected output: true

console.log(object2.prototype.isPrototypeOf(object3));
// expected output: true
```



<br><br>

## .keys() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
- The Object.keys() method returns an array of a given object's own enumerable property names, iterated in the same order that a normal loop would.
```javascript
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.keys(object1));
// expected output: Array ["a", "b", "c"]
```





<br><br>

## .values (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values)
- The Object.values() method returns an array of a given object's own enumerable property values, in the same order as that provided by a for...in loop. (The only difference is that a for...in loop enumerates properties in the prototype chain as well.)
```javascript
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.values(object1));
// expected output: Array ["somestring", 42, false]
```



<br><br>

## .values
- ES2022 provides a safe way to check if a property is the own property of an object.
- Object.hasOwn() is similar to Object.prototype.hasOwnProperty but supports all object types.
```javascript
Object.hasOwn("initProp")
```



<br><br>

## .groupBy()
- The Object.groupBy() method groups elements of an object according to string values returned from a callback function.
- The Object.groupBy() method does not change the original object.
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
const result = Object.groupBy(fruits, myCallback);
```












<br><br>
<br><br>

# Object instances
- When you pass an object as parameter and change it inside of your function then your main object will get re-assigned aswell. This is because of the object instance
```javascript
let obj = {anyvalue: true};

function test(a) {
  a.anyvalue = false;
  console.log(obj); {anyvalue: false}
};

test(obj);
```






<br><br>

# Mutability
- Objects and arrays, on the other hand, allow mutation, meaning the data structure can be changed.
```javascript
/*---- EXAMPLE #1 ----*/
let user = { name: "James Doe", location: "Lagos" }
let newUser = user
user.location = "Abia"
console.log(newUser.location) // "Abia"




/*---- EXAMPLE #2 ----*/
let obj = {
  a: {
    name: 'Peter'
  }
}

let test1 = obj
test1.a.name = 'Lisa'

console.log(obj.a.name);
console.log(test1.a.name);
```





















<br><br>

# Null is an object too
```javascript
var bar = null;
console.log(typeof bar === "object");  // logs true!

// solution
console.log((bar !== null) && (typeof bar === "object"));  // logs false
```






<br><br>

# Get name of object
```javascript
var crazyObject = {a: true}
Object.keys({crazyObject})[0] // crazyObject
```







<br><br>

# Create new variable from object
```javascript
var test = {body: "test"}
var {body: testbody} = test
console.log(testbody) // "test"
```






<br><br>

# Usage of this
```javascript
const obj = {
    multiply(x, y) {
        return x * y;
    },
    squared(x) {
        return this.multiply(x, x);
    },
};

console.log(obj.squared(2)); // 4
```









<br><br>

# Intercepting method calls
- If you want to intercept method calls via a proxy, there is one challenge: you can intercept the operation get (getting property values) and you can intercept the operation apply (calling a function), but there is no single operation for method calls that you could intercept. That's because method calls are viewed as two separate operations: First a get to retrieve a function, then an apply to call that function.
- 
<br><br>

Therefore, you must intercept get and return a function that intercepts the function call. The following code demonstrates how that is done.
```javascript
function traceMethodCalls(obj) {
    const handler = {
        get(target, propKey, receiver) {
            const origMethod = target[propKey];
            return function (...args) {
                const result = origMethod.apply(this, args);
                console.log(propKey + JSON.stringify(args)
                    + ' -> ' + JSON.stringify(result));
                return result;
            };
        }
    };
    return new Proxy(obj, handler);
}


const obj = {
    multiply(x, y) {
        return x * y;
    },
    squared(x) {
        return this.multiply(x, x);
    },
};


const tracedObj = traceMethodCalls(obj);
tracedObj.multiply(2,7)
// multiply[2,7] -> 14
// 14
```


















<br><br><br><br>

# Object Accessors (https://www.w3schools.com/js/js_object_accessors.asp)

<br><br>

## get
- This example uses a lang property to get the value of the language property.
```javascript
// Create an object:
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "en",
  get lang() {
    return this.language;
  }
};

// Display data from the object using a getter:
document.getElementById("demo").innerHTML = person.lang;
```

<br><br>

## set
- This example uses a lang property to set the value of the language property.
```javascript
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "",
  set lang(lang) {
    this.language = lang;
  }
};

// Set an object property using a setter:
person.lang = "en";

// Display data from the object:
document.getElementById("demo").innerHTML = person.language;
```












































<br><br><br><br>

# Sub-classing
- Sub-classing is a term that refers to inheriting properties for a new object from a base or superclass object. In traditional object-oriented programming, a class B is able to extend another class A. Here we consider A a superclass and B a subclass of A. As such, all instances of B inherit the methods from A. B is however still able to define its own methods, including those that override methods originally defined by A.

## Guide
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/#mixinpatternjavascript

<br><br>

```javascript
var Person = function( firstName, lastName ){
 
  this.firstName = firstName;
  this.lastName = lastName;
  this.gender = "male";
 
};


// a new instance of Person can then easily be created as follows:
var clark = new Person( "Clark", "Kent" );
 
 
// Define a subclass constructor for for "Superhero":
var Superhero = function( firstName, lastName, powers ){
 
    // Invoke the superclass constructor on the new object
    // then use .call() to invoke the constructor as a method of
    // the object to be initialized.
 
    Person.call( this, firstName, lastName );
 
    // Finally, store their powers, a new array of traits not found in a normal "Person"
    this.powers = powers;
};
 
Superhero.prototype = Object.create( Person.prototype );
var superman = new Superhero( "Clark", "Kent", ["flight","heat-vision"] );
console.log( superman );
 
// Outputs Person attributes as well as powers
```










































<br><br><br><br>

# Find the count of duplicate property values in an object
```javascript
var db = [
  {Id: "201" , Player: "Nugent",Position: "Defenders"},
  {Id: "202", Player: "Ryan",Position: "Forwards"},
  {Id: "203" ,Player: "Sam",Position: "Forwards"},
  {Id: "204", Player: "Bill",Position: "Midfielder"},
  {Id: "205" ,Player: "Dave",Position: "Forwards"},
];

var counter = {};
for (var i = 0; i < db.length; i += 1) {
    counter[db[i].Position] = (counter[db[i].Position] || 0) + 1;
}

for (var key in counter) {
    if (counter[key] > 1) {
        console.log("we have ", key, " duplicated ", counter[key], " times");
    }
}
```


	
	
	
	
	
	



<br><br><br><br>

# Find duplicated properties in array of objects
```javascript
const values = [{id: 10, name: 'someName1'}, {id: 10, name: 'someName2'}, {id: 11, name:'someName3'}, {id: 12, name: 'someName4'}];

const lookup = values.reduce((a, e) => {
  a[e.id] = ++a[e.id] || 0;
  return a;
}, {});

console.log(values.filter(e => lookup[e.id]));
```






	
	
	
	
	
	




<br><br><br><br>

# Beautify object
```javascript
JSON.stringify(obj, null, 4))
```






<br><br><br><br>

# Object shorthand
- You can insert variables to objects without defining the Property name because for default js will detect the name and set it. This means for the example below you would not have to do **banana: banana**
```javascript
var banana = true
var apple = false

var obj = {
  banana,
  apple
}

console.log(obj); // {banana: true, apple: false}
```














<br><br><br><br>

# Overwrite properties
- When you define the same property then the last one will stay.
```javascript
// ---- EXAMPLE #1 ----
var b = {
  "path": false,
  "path": true
}

console.log(b)



// ---- EXAMPLE #2 ----
var a = {
  "path": false,
  "html": false
}

var b = {
  ...a,
  "path": true
}

console.log(b)
```












<br><br><br><br>

# Check if property exist
```javascript
// ---- EXAMPLE #1 ----
let obj = {
  banana: true,
  apple: false
}

if("apple" in obj) console.log('Property was found')



// ---- EXAMPLE #2 ----
let obj = {
  banana: true,
  apple: false
}

if(obj.hasOwnProperty('apple')) console.log('Property was found')
```
	
	
	
	
	
	
	
	
	
	
	
	
	



<br><br><br><br>

# Object with function
```javascript
// method #1
const obj = {
  statics: {
    test(banana) {
      return true
    },
    bla: true
  }
};

	
// method #2
const obj = {
  statics: {
    test: (banana, apple) => {
      return true
    },
    bla: true
  }
};
```
	
	
	

	
<br><br><br><br>

# Clone Object
```javascript
const obj = {"name": "test"}

	
	
// Shallow copy - Method #1
const clone = Object.assign({}, obj)

// Shallow copy - Method #2
const clone = _.clone(obj);
	
	
// Deep copy - Method #2 (https://developer.mozilla.org/en-US/docs/Web/API/structuredClone)
const cloneDeep = structuredClone(obj)
	
// Deep copy - Method #2
const cloneDeep = JSON.parse(JSON.stringify(obj)
	
// Deep copy - Method #3
const cloneDeep = _.cloneDeep(obj);
```

	
	
	
	
	
	
	
	
	
	
	
	
	
<br><br><br><br>

# Remove duplicated objects from array
```javascript
let person = [
{name: "john"}, 
{name: "jane"}, 
{name: "imelda"}, 
{name: "john"},
{name: "jane"}
];

const data = Array.from(new Set(person.map(JSON.stringify))).map(JSON.parse);
console.log(data);
```
	
	
	
	
	
	
	
	
	
	
	
	
<br><br><br><br>

# Remove properties from object recursive
```javascript
// Method #1
const _ = require('lodash')
const newObj = _.omit(obj, ['x','y']);
```
	
<br><br>

# Remove properties from array of objects recursive
```javascript
// Method #1
const _ = require('lodash')
var strippedRows = _.map(rows, function (row) {
    return _.omit(row, ['bad', 'anotherbad']);
});
```
	
	
	
	
	
	
	
	
	
// Method #2	
/**
 * Remove property from object
 * @param {Object} obj
 * @param {String} prop - Property name
 * @returns {*}
 */
const _removeProperty = (obj, prop) => {
  Object.keys(obj).forEach(key =>
      (key === prop) && delete obj[key] ||
      (obj[key] && typeof obj[key] === 'object') && _removeProperty(obj[key], prop)
  )

  return obj
}

/**
 * Remove properties from object
 * @param {Object} obj
 * @param {Array} props
 * @returns {*}
 */
const removeProperties = (obj, props) => {
    for(const prop of props){
        obj = _removeProperty(obj, prop)
    }

    return obj
}




const obj = {
name: true,
title: true,
lean: true
}


const res = removeProperties(obj, ['name', 'title'])
console.log(res)
```
	
	
	
	

	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
<br><br><br><br>

# object values to array
```javascript
let obj = {apple:true,c:false}
let obj2 = {banana:false,d:false}

let ar = Object.keys(obj)
    .map(function(key) {
        return obj[key];
    });

console.log(ar) // [true, false]
```

	
	
	
<br><br><br><br>

# do not set undefined properties in object
```javascript
// example #1
const bcc = false
const bccAddress = { test: true }
    
const email = {
apple: true,
...(bcc ? { bccAddress } : {})
}

console.log('email: ', email)




// example #2
const a = 123
const b = undefined
const obj = { a, ...(b ? { b } : {}) }

console.log(obj) // { a: 123 }
```




























<br><br><br><br>

# add fn/property to prototype of object
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/setPrototypeOf
```javascript
const obj = {};
const parent = { foo: 'bar' };

console.log(obj.foo);
// Expected output: undefined

Object.setPrototypeOf(obj, parent);

console.log(obj.foo);
```
