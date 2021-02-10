# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..




<br><br>

# Summary
```javascript
// open all sections
for(const d of document.querySelectorAll('#readme details')){d.setAttribute('open', '');}

// close all sections
for(const d of document.querySelectorAll('#readme details')){d.removeAttribute('open', '');}
```
<details><summary>Click to expand..</summary>

# [Math](#_math)
1. Generate random number between two numbers
2. parseFloat()
3. parseInt()

# [Operators](#_operators)
1. Conditional Operators
  <br> 1.1 Ternary
2. Spread Operator
  <br> 2.1 convert array to paramater
  <br> 2.2 Object destructuring
3. Logical Operator
  <br> Nullish Coalescing Operator
4. Condition at variable decleration
 
# [Constructors](#_constructors)
1. Set()

# [Design Pattern](#_design-pattern)
1. Singleton
2. Builder
  <br> 2.1 Default function parameter
3. Null Object Pattern

# [DOM](#_dom)
1. Console clear assignment and variables
2. Add element
3. Remove element
4. Difference between .innerText & .textContent
5. Add HTML
6. Get Attribute
7. Set Attribute
8. Remove Attribute
9. Data Attribute
10. Classes
  <br> 10.1 toggle (switch) class
11. Styles
12. Event Listener
  <br> 12.1 addEventListener() / Dispatching custom events
  <br> 12.2 Listen to multiple elements with same CSS Selector
  <br> 12.3 Difference between event.target & event.currentTarget
  <br> 12.4 Event bubbling
     <br> 12.4.1 Guides
     <br> 12.4.2 event.target does not bubble
     <br> 12.4.3 Stop bubbling

# [Destructure](#_destructure)
1. Destructure instance/member variables
2. Destructure Examples

# [Switch](#_switch)
1. Add a section that will alert("Neither") if fruits is neither "banana" nor "apple"

# [forEach](#_foreach)
1. Iterate through all keys of nested object

# [For loop](#_for-loop)
1. Iterate through all keys of nested object
2. Do loop based on length of array
3. Make the loop jump to the next iteration when i is 5
4. break the loop when i is 5

# [While](#_while)
1. Do loop based on length of array
2. do/while statement

# [Functions](#_functions)
1. function to String and back to function
2. Generator functions
3. Immediately Invoked Function Expression (IIFE)

# [ESM (es-modules) and CJS (commonjs)](#_esm-es-modules-and-cjs-commonjs)
1. Examples for difference
2. CJS
  <br>3.1 export all functions
  <br>3.2 export specific function
3. ESM
  <br>3.1 Features
  <br>3.2 How to enable?
  <br>3.3 Export / Import
  <br>3.4 Client Side
  <br>3.5 No require, exports, module.exports, __filename, __dirname

# [Prototypes](#_prototypes)
1. Instantiate Object with Object.create (OLD METHOD)
2. Instantiate Object with new keyword (NEW METHOD)
3. change/add constructor value
4. Call another constructor
5. Inherit Prototype (How to access other constructor prototypes)
6. Change constructor
7. getPrototypeOf
8. hasOwnProperty
9. Iterate over all keys incl. prototypes
10. Iterate only over own properties and ignore prototypes
11. instanceof
12. Arrow functions do not have prototypes

# [Classes](#_classes)
1. Change/add constructor value
2. Static (isolated function)
3. Subclasses (Inheritance)
4. Multiple Inheritance (Mixins)
5. Event listener this inside of method

# [Time/Date](#_time)
1. format time to AM/PM
2. get current Date

# [Filter](#_filter)
1. compare 2 arrays of objects and remove duplicates

# [Sort](#_sort)
1. Sort Array by Numbers ASC
2. Sort Array by String ASC
3. Sort Array by two values ASC

# [Cookie](#_cookie)
1. Get value of specific cookie

# [Object Class](#_object-class)
1. Object.keys()

# [String](#_string)
1. .includes()

# [object](#_object)
1. Check if object is empty
2. Custom name of function chain
3. Object is not equal Object
4. Object constructor
  <br> 4.1 .assign()
  <br> 4.2 .create()
  <br> 4.3 .defineProperties()
  <br> 4.4 .entries()
  <br> 4.5 .fromEntries()
  
# [Array](#_array)
1. Clone unique
2. clone array
3. clone array with objects inside
4. get random item from array
5. .from()
6. prototype
  <br> 6.1 .values()
  <br> 6.2 .unshift()
  <br> 6.3 .splice()
  <br> 6.4 .sort()
  <br> 6.5 .some()
  <br> 6.6 .slice()
  <br> 6.7 .shift()
  <br> 6.8 .reverse()
  <br> 6.9 .reduce()
  <br> 6.10 .push()
  <br> 6.11 .pop()
  <br> 6.12 .keys()
  <br> 6.13 .join()
  <br> 6.14 .indexOf()
  <br> 6.15 .includes()
  <br> 6.16 .forEach()
  <br> 6.17 .flat()
  <br> 6.18 .flatIndex()
  <br> 6.19 .find()
  <br> 6.20 .filter()
  <br> 6.21 .fill()
  <br> 6.22 .every()
  <br> 6.23 .entries()
  <br> 6.24 .concat()
  <br> 6.25 .copyWithin()
  <br> 6.26 Map
      <br> 6.26.1 Convert Array to Array with Objects
7. .flat()


# [Link](#_link)
1. Get current link / domain

# [API](#_api)
1. Enter fullscreen

# [jQuery](#_jquery)
1. load
  <br>1.1 Insert all contents of another same origin HTML file to current page
  <br>1.2 Insert specific element of another same origin HTML file to current page
2. Check for click
3. Check browser
4. Event Listener
  <br>4.1 Manually trigger event listener
5. jQuery use !important
6. Handle form submits
7. Get scroll direction
8. Class Modification
9. Check for Touch Event (Mobile/Tablet)
10. Wait until scroll is finished
11. Scroll to bottom
12. Import scripts with callback
13. Get path of element
14. each loop
15. POST JSON to PHP file
16. clone
17. Get parent
18. Get next
19. Append HTML to current element
20. Insert HTML after specific element
21. Find element
22. Draggable
  <br>22.1 Exclude element

# [Async](#_async)
1. Create Async
2. setTimeout
3. setInterval
4. Functions - In Parallel
5. Loops (Array) - In Parallel
6. Loops - Sequential (For Loop)
7. Combine Async with promise

# [Promise](#_promise)
1. async await for promise resolve
2. Nested Functions

# [Wait](#_wait)
1. Wait until some condition is true

# [Loaded](#_loaded)
1. Wait until object is loaded
2. Wait until document ready
3. Wait until everything is fully loaded and loading icon is gone
4. Wait until element loaded
5. remove event listener from anonym function

# [Google reCAPTCHA v2](#_google-recaptcha-v2)
1. Check if user filled Captcha
2. Simulate Captcha Fail
3. Reset Captcha
4. Change width
5. PHP Backend do verify of captcha

# [:before & :after](#_before--after)
1. Add new style to :before and :after

# [Anime.js](#_animejs)
1. Remove Animation
2. Bouncing easing

# [Owl Carousel](#_owl-carousel)
1. Fix auto width problems / resize on width/height change

# [Navigator](#_navigator)
1. Get Browser Language

# [Iframe / Object Tag](#_iframe--object)
1. Embed pdf

# [Simulate](#_simulate)
1. Simulate Click
2. Simulate Hover
3. Simulate Touch events

# [document/window](#_documentwindow)
1. remove text from url
2. Open something new window
3. Get link params from oauth popup window
4. localStorage

# [Clipboard](#_clipboard)
1. Copy any text to clipboard

# [Redirect](#_redirect)
1. Prevent redirect on input search with Enter

# [Viewport](#_viewport)
1. Stop viewport resize when soft keyboard is activating on mobile

# [Before unload](#_before-unload)
1. Do something when current page / popup windows was closed

# [Os/Device Detect](#_osdevice-detect)
1. Check if tablet/smartphone
2. Check if iOS
3. Check if Safari Browser

# [Tutorials](#_tutorials)
1. The Conditional (Ternary) Operator Explained
2. Object-oriented Programming (OOP)
3. Functional Programming
4. Clean Code
5. Optional Chaining
6. Spread Operators
7. Scope and Closures
8. Difference between let, var & const
9. Destructuring
10. Microservices
  <br>10.1 Object-oriented
<br>11. YAML

</details>










































<br><br>
_____________________________________________________
_____________________________________________________
<br><br>

<a name="_math"><h1>Math</h1></a>
<details><summary>Click to expand..</summary>

# Generate random number between two numbers
```javascript
// generate random number between 1-50
Math.round(Math.random() * 50 + 1);
```

<br><br>

# parseFloat() (https://www.w3schools.com/jsref/jsref_parsefloat.asp)
- The parseFloat() function parses a string and returns a floating point number. This function determines if the first character in the specified string is a number. If it is, it parses the string until it reaches the end of the number, and returns the number as a number, not as a string.
```javascript
var a = parseFloat("10") // 10
var b = parseFloat("10.00") // 10
var c = parseFloat("10.33") // 10.33
var d = parseFloat("34 45 66") // 34
var e = parseFloat(" 60 ") // 60
var f = parseFloat("40 years") // 40
var g = parseFloat("He was 40") // NaN
```



<br><br>

# parseInt() (https://www.w3schools.com/jsref/jsref_parseint.asp)
- The parseInt() function parses a string and returns an integer.The radix parameter is used to specify which numeral system to be used, for example, a radix of 16 (hexadecimal) indicates that the number in the string should be parsed from a hexadecimal number to a decimal number.
```javascript
var b = parseInt("10.00") // 10
var c = parseInt("10.33") // 10
var d = parseInt("34 45 66") // 34
var e = parseInt(" 60 ") // 60
var f = parseInt("40 years") // 40

var h = parseInt("10", 10) // 10
var i = parseInt("010") // 10
var j = parseInt("10", 8) // 8
var k = parseInt("0x10") // 16
var l = parseInt("10", 16) // 16
```


</details>









































































<br><br>
_____________________________________________________
_____________________________________________________
<br><br>

<a name="_operators"><h1>Operators</h1></a>
- https://www.w3schools.com/js/js_operators.asp
<details><summary>Click to expand..</summary>

# Conditional Operators

<br><br>

## Ternary Operator
- https://www.w3schools.com/js/tryit.asp?filename=tryjs_comparison

```javascript
// if under 18 voteable will be "Too young"
// if over 18 votable will be "Old enough"
voteable = (age < 18) ? "Too young":"Old enough";

// alternative you can write it like this
voteable = age < 18 ? "Too young":"Old enough";
```

<br><br>

# Spread Operator

## Guides
- https://www.youtube.com/watch?v=I5AGSH8ROSU
- https://dev.to/livecodestream/how-to-use-the-spread-operator-in-javascript-35bn
- https://medium.com/javascript-in-plain-english/how-to-deep-copy-objects-and-arrays-in-javascript-7c911359b089

<br><br>

## convert array to paramater
```javascript
let ar = [1,2]

function test(a, b) {
  console.log('a:' + a);
  console.log('b:' + b);
}

test(...ar);
```



<br><br>

## Object destructuring
```javascript
let obj1 = {a: true};
let obj2 = {b: true};

function test({a = false, b = false}){
  console.log(a);
  console.log(b);
};

test({...obj1, ...obj2});
```





<br><br>






# Logical Operator

## Guides
- https://www.javascripttutorial.net/javascript-logical-operators/

<br><br>

## Nullish Coalescing Operator

- Syntax:
```javascript
leftExpression ?? rightExpression
```

- Example:
```javascript
/* ---- EXAMPLE #1 ---- */

// result will be 1 and is not what we want..
let count = 0;
let result = count || 1;
console.log(result); // 1

// The nullish coalescing operator helps you to avoid this pitfall. It only returns the second operand when the first one evaluates to either null or undefined.
let count = 0;
let result = count ?? 1;
console.log(result); // 0





/* ---- EXAMPLE #2 ---- */
const result = null || undefined ?? 'OK'; // SyntaxError

const result = (null || undefined) ?? 'OK'; 
console.log(result); // 'OK'
```









<br><br>

## Condition at variable decleration
```javascript
const a = 1;
const b = 2;
const example = a > b
console.log(example); // false
```




</details>













































































<br><br>
_____________________________________________________
_____________________________________________________
<br><br>

<a name="_constructors"><h1>Constructors</h1></a>
- https://www.w3schools.com/js/js_object_constructors.asp
<details><summary>Click to expand..</summary>

## Set()
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/Set
```javascript
const set1 = new Set([1, 2, 3, 4, 5]);

console.log(set1.has(1));
// expected output: true

console.log(set1.has(5));
// expected output: true

console.log(set1.has(6));
// expected output: false
```

</details>












































































 <br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>

<a name="_design-pattern"><h1>Design Pattern</h1></a>
<details><summary>Click to expand..</summary>

# Singleton

<br>

## Guides
- https://www.youtube.com/watch?v=sJ-c3BA-Ypo

<br><br>

## Singleton with Classes
```javascript
class test {
  constructor(){
    if(test.instance == null){
      test.instance = this;
    }
    return test.instance;
  };


  createData(data){
    this.example = data;
  };
};


let a = new test();
a.createData('a')
console.log('a: ' + a.example); // <-- will print a

let b = new test();
console.log('b: ' + b.example); // <-- will print a
```





 <br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>





 
# Builder

<br>

## Guides
- https://www.youtube.com/watch?v=M7Xi1yO_s8E

<br><br>

## Builder with Classes
```javascript
/**
 * Create User by passing optional data as option object (builder pattern)
 This is usefully when params are not set and you do not have to manually define this scenario.
 
 {age, city, country} = {} <-- If no params were set we set the object to empty. If
 we would not do this we would get error when using only: let Bob = new User('Bob');

 Instead of undefined we can also set a default value for our params if we do not include them at the creation process.
 So in this case scope will be always 1. (scope = 1)
*/
class User {
  constructor(name, {age, city, country, scope = 1} = {}){
    this.name = name;
    this.age = age;
    this.city = city;
    this.country = country; // <-- will be undefined because we do not include this param
    this.scope = scope; // <-- will be 1
  };
};

let Bob = new User('Bob', {
  age: 21,
  city: 'Berlin',
});
console.log(Bob);
```



<br><br>

## Default function parameter (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Functions/Default_parameters)
```javascript
function multiply(a, b = 1) {
  return a * b;
}

console.log(multiply(5, 2));
// expected output: 10

console.log(multiply(5));
// expected output: 5
```








































 <br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>


# Null Object Pattern

<br>

## Guides
- https://www.youtube.com/watch?v=D4Dja5WSZoA

<br><br>

## Null Object with Classes
```javascript
class User {
  constructor(id, name) {
    this.id = id
    this.name = name
  }

  hasAccess() {
    return this.name === 'Bob'
  }
}

class NullUser {
  constructor() {
    this.id = -1
    this.name = 'Guest'
  }

  hasAccess() {
    return false
  }
}

const users = [
  new User(1, 'Bob'),
  new User(2, 'John')
]

function getUser(id) {
  const user = users.find(user => user.id === id)
  /*
    We are now checking if the user is null before returning, and instead returning a NullUser object if the user is null. This means that we no longer need to check for null users later in the code and can treat all users that are returned from this function the same whether they exist or not.
  */
  if (user == null) {
    return new NullUser()
  } else {
    return user
  }
}

function printUser(id) {
  const user = getUser(id)
  console.log('Hello ' + user.name)

  if (user.hasAccess()) {
    console.log('You have access')
  } else {
    console.log('You are not allowed here')
  }
}
```





</details>










 <br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>

<a name="_dom"><h1>DOM</h1></a>
<details><summary>Click to expand..</summary>

# Console clear assignment and variables
- Method #1: Reload page (Manually or use window.location.reload();)
- Method #2: In ES6 you can use blocks (so long as you use let instead of var):
```javascript
{
    let example = true;
}
```

<br><br>

# Add element
```javascript
const body = document.body;
const div = document.createElement('div');
body.append(div);
```


<br><br>

# Remove element
```javascript
const div = document.createElement('div');
div.remove();
```


<br><br>

# Difference between .innerText & .textContent
- https://youtu.be/y17RuWkWdn8?t=253
```html
<div>
  <span>Hello</span>
  <span style="display:none">Bye</span>
</div>
```

```js
const data = document.querySelector('div');
console.log(data.innerText);
console.log(data.textContent); // will only print Hello because it only shows visible text
```

<br><br>

# Add HTML
```javascript
const body = document.body;
const div = document.createElement('div');

// method #1
body.innerHTML = '<strong>Example..</strong>';

// method #2
const strong = document.createElement('strong');
strong.innerHTML = 'Example..';
div.append(strong);
```


<br><br>

# Get Attribute
```html
<div title="example" id="test"></div>
```

```js
// method #1
const attribute = document.querySelector('#test').getAttribute('title');
console.log(attribute);

// method #2
const test = document.querySelector('#test');
console.log(test.title);
```


<br><br>

# Set Attribute
```html
<div id="test"></div>
```

```js
// method #1
document.querySelector('#test').setAttribute('title', 'example');

// method #2
const test = document.querySelector('#test');
test.title = 'example';
```



<br><br>

# Remove Attribute
```html
<div id="test" title="example"></div>
```

```js
document.querySelector('#test').removeAttribute('title');
```



<br><br>

# Data Attribute
```html
<div id="test" data-blue="blue" data-yellow-black="yellow"></div>
```

```js
const data = document.querySelector('#test').dataset;

// list all data attributes
console.log(data);

// get specific data attribute
console.log(data.blue);
console.log(data.yellowBlack);

// define new data attribute
data.green = 'green';
```



<br><br>

# Classes
```html
<div class="test1 test2"></div>
```

```js
// add new class
document.querySelector('.test1').classList.add('test3'); // <div class="test1 test2 test3"></div>

// remove class
document.querySelector('.test1').classList.remove('test2'); // <div class="test1"></div>
```
<br>

## toggle (switch) class
```html
<div class="test1"></div>
```

```js
document.querySelector('.test1').toggle('test2'); // <div class="test2"></div>
```


<br><br>

# Styles
```html
<div id="test"></div>
```

```js
document.querySelector('#test').style.color = 'red'; // #test {color: red}
```



<br><br>



# Event Listener



## addEventListener() / Dispatching custom events 
```js
// method #1 - directly include function
document.querySelector('.person').addEventListener('click', event=>{
  const person = event.target; // same like jquery this
});

// method 2 - call external function
document.getElementById("myBtn").addEventListener("click", yourFunctionHere);

// method 3 - event constructor
let event = new Event("click");
document.getElementById("myBtn").dispatchEvent(event);
```

<br><br>

## Listen to multiple elements with same CSS Selector
```js
// method 1
document.querySelectorAll("whatever").forEach(elem => elem.addEventListener("input", fn))

// method 2
document.addEventListener('click', function(e){
  if(e.target.tagName=="BUTTON"){
   alert('BUTTON CLICKED');
  }
})
```

<br><br>

## Difference between event.target & event.currentTarget
- https://stackoverflow.com/questions/10086427/what-is-the-exact-difference-between-currenttarget-property-and-target-property
- target = element that triggered event; currentTarget = element that listens to event. 




<br><br><br><br>

## Phases of event propagation (https://javascript.info/bubbling-and-capturing#capturing)
1. Capturing phase – the event goes down to the element.
2. Target phase – the event reached the target element.
3. Bubbling phase – the event bubbles up from the element.
```html
<style>
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
</style>

<form>FORM
  <div>DIV
    <p>P</p>
  </div>
</form>

<script>
  for(let elem of document.querySelectorAll('*')) {
    elem.addEventListener("click", e => alert(`Capturing: ${elem.tagName}`), true);
    elem.addEventListener("click", e => alert(`Bubbling: ${elem.tagName}`));
  }
</script>

<!--
The code sets click handlers on every element in the document to see which ones are working.

If you click on <p>, then the sequence is:

HTML → BODY → FORM → DIV (capturing phase, the first listener):
P (target phase, triggers two times, as we’ve set two listeners: capturing and bubbling)
DIV → FORM → BODY → HTML (bubbling phase, the second listener).
There’s a property event.eventPhase that tells us the number of the phase on which the event was caught. But it’s rarely used, because we usually know it in the handler.
-->
```

<br><br>

## Event Bubbling
- The process is called “bubbling”, because events “bubble” from the inner element up through parents like a bubble in the water. Normally it goes upwards till <html>, and then to document object, and some events even reach window, calling all handlers on the path.
```html
<style>
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
</style>

<form onclick="alert('3')">FORM
  <div onclick="alert('2')">DIV
    <p onclick="alert('1')">P</p>
  </div>
</form>
```


```javascript
<!--  will alert the following in this oder when p tag would be clicked:
1
2
3
-->
```
<br><br>


#### Guides
- https://javascript.info/bubbling-and-capturing

<br><br>

#### event.target does not bubble (https://javascript.info/bubbling-and-capturing#event-target)
- event.target – is the “target” element that initiated the event, it doesn’t change through the bubbling process.
- this – is the “current” element, the one that has a currently running handler on it.
```html
<form id="form">FORM
  <div>DIV
    <p>P</p>
  </div>
</form>
```

```js
form.onclick = function(event) {
  alert("target = " + event.target.tagName + ", this=" + this.tagName);
};

/*
If p is clicked then: event.target = p | this = form
If div is clicked then: event.target = div | this = form
If form is clicked then: event.target = form | this = form
*/
```

<br><br>

#### Stop bubbling (.stopPropagation())
- event.stopPropagation() stops the move upwards, but on the current element all other handlers will run.
```js
// body.onclick doesn’t work if you click on <button>
<body onclick="alert(`the bubbling doesn't reach here`)">
  <button onclick="event.stopPropagation()">Click me</button>
</body>
```

<br><br>

#### Stop all other handler execution on the same element (.stopImmediatePropagation())
- To stop the bubbling and prevent handlers on the current element from running, there’s a method event.stopImmediatePropagation(). After it no other handlers execute.
```js
<body onclick="alert(`the bubbling doesn't reach here`)">
  <button onclick="event.stopImmediatePropagation()">Click me</button>
</body>
```




<br><br><br><br>


## Capturing
- Goes down from window to the event listener. So opposity of bubbling.
```javascript
// method #1
elem.addEventListener("click", e => alert(`Capturing: ${elem.tagName}`), true);

// method #2
elem.addEventListener("click", e => alert(`Capturing: ${elem.tagName}`), {capture: true});
```

<br><br>

#### To remove the handler, removeEventListener needs the same phase
```javascript
// method #1
element.removeEventListener("click", true);

// method 2
element.removeEventListener("click", {capture: true});  
```
<br><br>

</details>
















 <br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>

<a name="_destructure"><h1>Destructure</h1></a>
<details><summary>Click to expand..</summary>
  
<br><br>

# Guides
- https://dev.to/quantumsheep/all-you-need-to-know-about-destructuring-in-javascript-1hla

<br><br>

# Destructure instance/member variables
```javascript
// Method #1
class Foo {
  constructor(options) {
    ({one: this.one, two: this.two} = options);
    // Do something else with the other options here
  }
}


// Method 2
class Foo {
  constructor(options) {
    const {one, two} = options;
    Object.assign(this, {one, two});
    // Do something else with the other options here
  }
}


// Method 3
// If you want to apply all your options to the instance, you could use Object.assign without destructuring:
class Foo {
  constructor(options) {
    Object.assign(this, options);
  }
}
```

<br><br>

## Destructure Examples
```javascript
// Object Destructure - default
const { foo, bar } = { foo: 'hello', bar: 'world'}
console.log(foo) // gibt 'hello' aus
console.log(bar) // gibt 'world' aus




// Object Destructure - with variable
const test = { foo: 'hello', bar: 'world'}
const { foo, bar } = test
console.log(foo) // gibt 'hello' aus
console.log(bar) // gibt 'world' aus




// Object Destructure - with default value
const { foo, bar='myworld' } = { foo: 'hello'}
console.log(foo) // gibt 'hello' aus
console.log(bar) // gibt 'myworld' aus




// Object Destructure - with default value that gets overwritten
const { foo, bar='myworld' } = { foo: 'hello', bar: 'mybetterworld'}
console.log(foo) // gibt 'hello' aus
console.log(bar) // gibt 'mybetterworld' aus



// Object Destructure - rename key value to new variable
let obj = {a: true, b: false};
let {a: lena} = obj;
console.log(lena); // true




// Object Destructure - with default value and empty object if no param was passed
const { foo='hey', bar='myworld' } = {}
console.log(foo) // gibt 'hey' aus
console.log(bar) // gibt 'myworld' aus




// Object Destructure - with function
function add({x,y}) {
    return x+y
}

const result = add({ x:2, y:3 })
console.log(result) // gibt 5 aus



// Object Destructure - with function and spread operator
let obj1 = {a: true};
let obj2 = {b: true};

function test({a = false, b = false}){
  console.log(a);
  console.log(b);
};

test({...obj1, ...obj2});




// Object Destructure - with function and empty param z return NaN
function add({x,y,z}) {
    return x+y+z
}

const result = add({ x:2, y:3 })
console.log(result) // gibt NaN aus, weil z nicht definiert wurde




// Object Destructure - with function and default params
function add({x=0,y=0,z=0}) {
    return x+y+z
}

const result = add({ x:2, y:3 })
console.log(result) // gibt 5 aus





// Object Destructure - with function and default params but no params are passed
function add({x=0,y=0,z=0}) {
    return x+y+z
}

const result = add()
// wirft direkt einen Fehler "Uncaught TypeError: (destructured parameter) is undefined"





// Object Destructure - with function and default params but no params are passed. We use empty object to solve this problem
function add({x=0,y=0,z=0}={}) {
    return x+y+z
}

const result = add()
console.log(result) // gibt 0 aus





// same like above but more advanced example
function drawChart({size = 'big', coords = {x: 0, y: 0}, radius = 25} = {}) {
  console.log(size);
  console.log(coords);
  console.log(radius);
}

drawChart({
  coords: {x: 18, y: 30},
  radius: 30
})

// gibt folgende drei Zeilen aus:
big
{ x: 18, y: 30 }
30
```

</details>




 <br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>

<a name="_switch"><h1>Switch</h1></a>
<details><summary>Click to expand..</summary>
  
<br><br>

# Guides
- https://www.w3schools.com/js/js_switch.asp

<br><br>

# Add a section that will alert("Neither") if fruits is neither "banana" nor "apple".
```javascript
switch("Ice") {
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

</details>





<br><br>



<a name="_foreach"><h1>forEach</h1></a>

<details><summary>Click to expand..</summary>
  
# Iterate through all keys of nested object
```javascript
function resetValuesToZero (obj) {
    Object.keys(obj).forEach(function (key) {
        if (typeof obj[key] === 'object') {
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
</details>

<br><br>



<a name="_for-loop"><h1>For loop</h1></a>

<details><summary>Click to expand..</summary>



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

# Make the loop jump to the next iteration when i is 5.
```javascript
for (i = 0; i < 10; i++) {
  if (i == 5) continue;
  console.log(i);
}
```

<br>

# break the loop when i is 5.
```javascript
for (i = 0; i < 10; i++) {
  if (i == 5) break;
  console.log(i);
}
```

</details>







 <br><br>





<a name="_while"><h1>While</h1></a>
  
 <details><summary>Click to expand..</summary>
  
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


</details>





 <br><br>






<a name="_functions"><h1>functions</h1></a>
  
<details><summary>Click to expand..</summary>
  
# function to String and back to function
```javascript
var myFunction = function() {
  // Any codes here
  console.log('This is myFunction');
};
 
var fString = myFunction.toString();
console.log(fString);
 
var fn = new Function('return ' + fString)(); 
fn();
```

# Generator functions
```javascript
// example #1
function* generator(i) {
  yield i;
  yield i + 10;
}

const gen = generator(10);

console.log(gen.next().value);
// expected output: 10

console.log(gen.next().value);
// expected output: 20



// example #2 It can also break the for loop and then return at the next iteration at the new line
function* generator(i) {
  
  for(let d=0;d<10;d++){
    yield d;
    yield d + 100;
  }
}

var gen = generator(10);

console.log(gen.next().value);
// expected output: 10

console.log(gen.next().value);
// expected output: 100

console.log(gen.next().value);
// expected output: 1
```



# Immediately Invoked Function Expression (IIFE)
```javascript
// sync
;(() => {/*..*/})();

// async
;(async () => {/*..*/})();


/* // we use a leading semicolon in front of our IIFE to prevent broken functions like as example:
mybrokenfunction = function(){

} //no semicolon here
(function(g){


})(this);
*/
```



</details>






































































 <br><br>




<a name="_esm-es-modules-and-cjs-commonjs"><h1>ESM (es-modules) and CJS (commonjs)</h1></a>
  
<details><summary>Click to expand..</summary>
  
# Guides
CJS vs ESM (https://redfin.engineering/node-modules-at-war-why-commonjs-and-es-modules-cant-get-along-9617135eeca1)

# Examples for difference
```javascript
// ### CJS ##
module.exports.sum = (x, y) => x + y; // @filename: util.js
const {sum} = require('./util.js');

// ### ESM ##
export const sum = (x, y) => x + y; // @filename: util.js
import {sum} from './util.js'
```

<br><br>
______________________________________________________
<br><br>


# CJS

## export all functions
```javascript
module.exports = {
    foo: ()=>{/*..*/},
    bar: ()=>{/*..*/}
};
```

## export specific function
```javascript
// example #1
module.exports.anyname = ()=>{/*..*/};
```

<br><br>
______________________________________________________
<br><br>

# ESM

## Features
- No need for **"use strict"**
- async

<br><br>

## How to enable?
```javascript
// package.json
"type": "module"

// Also rename all files where you use ESM to .mjs
```

## Export / Import
```javascript
/* ## Option 1 ##
Name your export instead of using default. It should look like this */
// add.mjs
export const add =  (a, b) =>  a + b;
// OR
// export const add = function(a, b) { return a+b };

// app.mjs
import { add } from './add.mjs';



/* ## Option 2 ##
Use the export default syntax. It looks like this */

// add.,js
export default function add(a, b) {
  return a + b;
}

// app.,js
import add from './add.mjs';



/* ## Option 3 ##
Use the export default syntax. As example for controller files*/

// controller.mjs
import {startBROWSER, openLink} from '../services/bot.mjs';
export default {
  startBROWSER: async ()=>{ return await startBROWSER(); },
  openLink: async (page, link)=>{ return await openLink(page, link); }
}


// app.mjs
import bot from './controller.mjs';
await bot.startBROWSER();



/* ## Option 4 ##
Use export on specific functions and import all available to object*/

// bot.mjs
export const getUserDetails = async (req, res)=>{ /*..*/ });
export const getRoomDetails = async (req, res)=>{ /*..*/ });

// app.mjs
import * as bot from '../services/bot.mjs';
await bot.getUserDetails(req, res);



/* ## Option 5 - export classes ##
export class startBROWSER {/*..*/};



/* ## Option 6 - export variable ##
export let pptr;
```
<br>
<br>


## Client Side
- In order to use client side ESM we use **type="module"**
```html
<!-- method #1 -->
<script type="module" src="js/utils/test.main.mjs"></script>

<!-- method #2 -->
<script type="module">
  import web from '/js/main.mjs';
</script>

<!-- method #3 -->
<script type="module">
  import '/js/main.mjs';
</script>
```

<br>
<br>


## No require, exports, module.exports, __filename, __dirname (https://nodejs.org/api/esm.html#esm_no_require_exports_module_exports_filename_dirname)
```javascript
import { fileURLToPath } from 'url';
import { dirname } from 'path';

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);
```

</details>







 <br><br>





<a name="_prototypes"><h1>Prototypes</h1></a>

<details><summary>Click to expand..</summary>
  
# Guides
- A Beginner's Guide to JavaScript's Prototype (https://www.youtube.com/watch?v=XskMWBXNbp0)
- Prototypes Example (https://dev.to/karataev/javascript-prototypes-by-example-15jh)
- New keyword in Javascript (https://www.youtube.com/watch?v=Uhp9xPCILno)
- OOP / Explain Prototype (https://www.youtube.com/watch?v=vDJpGenyHaA)


# Instantiate Object with Object.create (**OLD METHOD**)
```javascript
// METHOD #1
function Animal (name, energy){
  let animal = Object.create(Animal.prototype);
  animal.name = name;
  animal.energy = energy;
  return animal
};


Animal.prototype.play = function (length) {
  console.log(`${this.name} is playing ${length} hours`);
};

leo = Animal('Leo', 7);
console.log('leo name:' + leo.name);
console.log(leo.play(5));






// METHOD #2
const Animal = {

  play: function (length) {
    console.log(`${this.name} is playing ${length} hours`);
  },

  eat: function (length) {
    console.log(`${this.name} is eating ${length} hours`);
  }

};

var leo = Object.create(Animal);
leo.name = 'Leo';

/*
// alternative this works too
const leo = Object.create(Animal, {
  name: {value: 'Leo'}
});
*/

leo.play(2);
```

# Instantiate Object with new keyword (**NEW METHOD**)
```javascript
function Animal (name, energy){
  this.name = name;
  this.energy = energy;
};

Animal.prototype.play = function (length) {
  console.log(`${this.name} is playing ${length} hours`);
};

const leo = new Animal('Leo', 7);
console.log('leo name:' + leo.name);
console.log(leo.play(5));
```

<br>
<br>

# change/add constructor value
```javascript
function Animal (name, energy, minute){
  this.name = name;
  this.energy = energy;
  this.sleep = minute;
};

Animal.prototype.changeSleep = function (minute) {
  this.sleep = minute;
};

Animal.prototype.addEat = function (seconds) {
  this.eat = seconds;
};

var leo = new Animal('Leo', 7, 2);
console.log(`${leo.name} is sleeping ${leo.sleep} minutes and is eating ${leo.eat} seconds.`);

leo.changeSleep(3);
leo.addEat(4);
console.log(`${leo.name} is sleeping ${leo.sleep} minutes and is eating ${leo.eat} seconds.`);
```

<br>
<br>

# Call another constructor 

```javascript
function Animal (name, energy){
  this.name = name;
  this.energy = energy;
};

function Zoo (name, energy, sleep){
  Animal.call(this, name, energy);
  this.sleep = sleep;
};

var ZooGermany = new Zoo('Leo', 1, 2);
console.log(`${ZooGermany.name} is sleeping ${ZooGermany.sleep} minutes and has ${ZooGermany.energy} energy.`);
```
<br>
<br>


# Inherit Prototype (How to access other constructor prototypes)
```javascript
function Animal (name, energy){
  this.name = name;
  this.energy = energy;
};

Animal.prototype.eat = function (seconds){
  this.eat = seconds;
  console.log(`${this.name} is eating for ${seconds} seconds`);
};

function Zoo (name, energy, country){
  Animal.call(this, name, energy);
  this.country = country;
};

var Peter = new Animal('Peter', 1);

Zoo.prototype = Object.create(Animal.prototype); // get prototypes from Animal constructor
var ZooGermany = new Zoo('Peter', 1, 'Germany');

Peter.eat(1); // <-- will work
ZooGermany.eat(1); // will result in error if we delete the Object.create line cause eat prototype not avaible


```
<br>
<br>



# Change constructor
```javascript
function Animal (name, energy){
  this.name = name;
  this.energy = energy;
};

function Zoo (name, energy, country){
  Animal.call(this, name, energy);
  this.country = country;
};

var ZooGermany = new Zoo('Peter', 1, 'Germany');
Zoo.prototype.constructor = Zoo; // <-- for default constructor Zoo will use the Animal constructor.
console.log(ZooGermany);
```
<br>
<br>



# getPrototypeOf
- This will show all prototypes from instance
```javascript
const prototype = Object.getPrototypeOf(leo);
//prototype
```


<br>
<br>

# hasOwnProperty
- Check for objects own properties and ignore prototypes
```javascript
leo.hasOwnProperty('name'); // true
leo.hasOwnProperty('play'); // true
```


# Iterate over all keys incl. prototypes
```javascript
for(const key in leo){
  console.log(`Key: ${key} - Value: ${leo[key]}`);
}
/*
Key: name - Value: Leo
Key: energy - Value: 7
Key: play - Value: function (length) {
  console.log(`${this.name} is playing ${length} hours`);
}
*/
```


# Iterate only over own properties and ignore prototypes
```javascript
for(const key in leo){
  if(leo.hasOwnProperty(key)){
   console.log(`OWN - Key: ${key} - Value: ${leo[key]}`);
  } else console.log(`NOT OWN - Key: ${key} - Value: ${leo[key]}`);
}
/*
OWN - Key: name - Value: Leo
OWN - Key: energy - Value: 7
NOT OWN - Key: play - Value: function (length) {
  console.log(`${this.name} is playing ${length} hours`);
}
*/
```


<br>
<br>

# instanceof
- Check if object is an instance of a specific class
```javascript
function sample(){};
leo instanceof Animal // true
leo instanceof sample // false
```


<br>
<br>

# Arrow functions do not have prototypes
```javascript
const Animal = ()=>{};
const leo = new Animal();
/* Uncaught TypeError: Animal is not a constructor at <anonymous>:2:13 */
```

</details>








<br><br>










<a name="_classes"><h1>Classes</h1></a>
<details><summary>Click to expand..</summary>

```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  play(length) {
    console.log(`${this.name} is playing ${length} hours`);
  }

};

var leo = new Animal('Leo', 7);
console.log('leo name:' + leo.name);
console.log(leo.play(5));
```

<br><br>


# Change/add constructor value
```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  changeName(name, lastName) {
    this.name = name;
    this.lastName = lastName;
  }

};

var leo = new Animal('Leo', 7);
console.log('name before:' + leo.name);

leo.changeName('Peter', 'Doe');
console.log('name after:' + leo.name);
console.log('added last name:' + leo.lastName);
```



<br><br>


# static (isolated function)
```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  static getDetails(){
    const r = 'API_results'; // do as example some api calls here
    return `Details about your pet: ${r}`;
  }

};

console.log('getDetails():' + Animal.getDetails());
```


<br><br>


# subclasses (inheritance)
```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  getDetails(){
    return `${this.name} has ${this.energy} energy left` ;
  }

};

class Zoo extends Animal {
  /* 
    you can also remove the constructor and you are still able to access the sub class because we will use the subclass constructor in this case.

    If you want to use the parent class constructor your have to use super();
    https://www.w3schools.com/jsref/jsref_class_super.asp
  */
  constructor(name, energy, location){
    super(name, energy);
    this.location = location;
  }
};

var zooGermany = new Zoo('Leo', 1, 'Germany');
console.log(zooGermany);

// compared to es5 we can now use functions of the original constructor without manually inherit the object
var getDetails = zooGermany.getDetails();
console.log('getDetails: ' + getDetails);
```



<br><br>


# Multiple Inheritance (Mixins)
```javascript
class Animal {
  constructor(){ 
    Object.assign(this, new Shark(), new Clock());
  };
};

class Shark {
  // only what's in constructor will be on the object, ence the weird this.bite = this.bite.
  constructor(){ this.color = "black"; this.bite = this.bite };
  bite(){ console.log("bite") };
  eat(){ console.log('eat') };
};

class Clock{
  constructor(){ this.tick = this.tick; };
  tick(){ console.log("tick"); };
};

let animal = new Animal();
animal.bite();
console.log(animal.color);
animal.tick();
```


<br><br>

## Use always same instance (singleton)
```javascript
class test {
  constructor(){
    if(test.instance == null){
      test.instance = this;
    }
    return test.instance;
  };


  createData(data){
    this.example = data;
  };
};


let a = new test();
a.createData('a')
console.log('a: ' + a.example); // <-- will print a

let b = new test();
console.log('b: ' + b.example); // <-- will print a
```




<br><br>



## Event listener this inside of method
- Instead of this we can use event.target (http://www.w3.org/TR/DOM-Level-2-Events/events.html)
```javascript
export class User {
  personClick() {
    $(document).on('click', '.person', function(event) {
      const elem = event.target;
      $(elem).attr('data-active', 'true');
    });
  };
};
```








</details>



























<br><br>



<a name="_time"><h1>time</h1></a>
  
<details><summary>Click to expand..</summary>
  
# format time to AM/PM
```javascript
function formatAMPM(date) {
  var hours = date.getHours();
  var minutes = date.getMinutes();
  var ampm = hours >= 12 ? 'pm' : 'am';
  hours = hours % 12;
  hours = hours ? hours : 12; // the hour '0' should be '12'
  minutes = minutes < 10 ? '0'+minutes : minutes;
  var strTime = hours + ':' + minutes + ' ' + ampm;
  return strTime;
}
console.log(formatAMPM(new Date)); // <-- 8:23 pm
```

# get current Date
```javascript
var today = new Date();
var dd = String(today.getDate()).padStart(2, '0');
var mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
var yyyy = today.getFullYear();

today = mm + '/' + dd + '/' + yyyy;
console.log(today) // <-- 10/25/2020
```

</details>






<br><br>





<a name="_filter"><h1>filter</h1></a>
<details><summary>Click to expand..</summary>
  
# compare 2 arrays of objects and remove duplicates
```javascript
var cars1 = [
    {id: 2, make: "Honda", model: "Civic", year: 2001},
    {id: 1, make: "Ford",  model: "F150",  year: 2002},
    {id: 3, make: "Chevy", model: "Tahoe", year: 2003},
];
    
var cars2 = [
    {id: 3, make: "Kia",    model: "Optima",  year: 2001},
    {id: 4, make: "Nissan", model: "Sentra",  year: 1982},
    {id: 2, make: "Toyota", model: "Corolla", year: 1980},
];

let res = cars1.concat(cars2.filter(({id}) => !cars1.find(x => x.id === id)))
             //.sort((a, b) => a.id - b.id);

console.log(res);
```

</details>







<br><br>







<a name="_sort"><h1>Sort</h1></a>
<details><summary>Click to expand..</summary>

# Sort Array by Numbers ASC
```javascript
var r = [
  {
    "id": 2,
    "name": "Hardware",
    "sorting": 2,
    "parent_id": 0
  },
  {
    "id": 1,
    "name": "Games",
    "sorting": 1,
    "parent_id": 0
  }
];
r.sort((a, b) => a.sorting - b.sorting );
```


# Sort Array by String ASC
```javascript
var r = [
  {
    "id": 2,
    "name": "Hardware",
    "sorting": 2,
    "parent_id": 0
  },
  {
    "id": 1,
    "name": "Games",
    "sorting": 1,
    "parent_id": 0
  }
];
r.sort((a, b) => a.name.localeCompare(b.name) );
```


# Sort Array by two values ASC
The first value got always priority in order. The second value will only count if the first value sort gets not destroyed.
```javascript
var r = [
  {
    "id": 1,
    "name": "Games",
    "sorting": 1,
    "parent_id": 0
  },
  {
    "id": 2,
    "name": "Hardware",
    "sorting": 2,
    "parent_id": 0
  },
  {
    "id": 4,
    "name": "XBOX One",
    "sorting": 1,
    "parent_id": 1
  },
  {
    "id": 5,
    "name": "Playstation",
    "sorting": 3,
    "parent_id": 1
  }
];
r.sort((a, b) => a.sorting - b.sorting || a.name.localeCompare(b.name));
```


 </details> 







<br><br>






<a name="_cookie"><h1>Cookie</h1></a>
<details><summary>Click to expand..</summary>
  
## Get value of specific cookie
```javascript
var regex = /MyCookie=(.[^;]*)/ig;
var match = regex.exec(document.cookie);
var value = match[1];
```
</details>





<br><br>




<a name="_object-class"><h1>Object Class</h1></a>
<details><summary>Click to expand..</summary>

# Guides
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object


<br><br>


# Object.keys()
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

</details>



<br><br>














































<a name="_string"><h1>String</h1></a>
<details><summary>Click to expand..</summary>

# .includes()
```javascript
var str = "Hello world, welcome to the universe.";
var n = str.includes("world");
console.log(n); // true
```

</details>



<br><br>










































<a name="_object"><h1>object</h1></a>
<details><summary>Click to expand..</summary>

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


# .assign() (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
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


# .create() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
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


# .defineProperties() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperties)
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


# .defineProperty() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)
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


# .entries() (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
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




</details>






<br><br>






<a name="_array"><h1>Array</h1></a>
<details><summary>Click to expand..</summary>


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



# .flat()
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Array/flat
```javascript
var arr1 = [1, 2, [3, 4]];
arr1.flat();
// [1, 2, 3, 4]

var arr2 = [1, 2, [3, 4, [5, 6]]];
arr2.flat();
// [1, 2, 3, 4, [5, 6]]

var arr3 = [1, 2, [3, 4, [5, 6]]];
arr3.flat(2);
// [1, 2, 3, 4, 5, 6]
```







</details>






<br><br>










<a name="_link"><h1>Link</h1></a>
<details><summary>Click to expand..</summary>

# Get current link / domain
```javascript
// method #1
location.href

// method #2
window.location.href

// method #3
document.location.href

// -----------------------------

//  "#2"
window.location.hash

// "localhost:4200"
window.location.host

// "localhost"
window.location.hostname

// "http://localhost:4200/landing?query=1#2"
window.location.href

// "http://localhost:4200"
window.location.origin

// "/landing"
window.location.pathname

// "4200"
window.location.port

// "http:"
window.location.protocol

// "?query=1"
window.location.search
```

</details>






<br><br>






<a name="_api"><h1>API</h1></a>
<details><summary>Click to expand..</summary>

# Enter fullscreen (https://developers.google.com/web/fundamentals/native-hardware/fullscreen/)
- Doesn´t work on ios..


```html
<button id="goFS">Go fullscreen</button>
<script>
 $("#goFS").on("click",function(){
      
   // this works with scroll -  do not use document.body.requestFullscreen();   
   const elem = document.documentElement;
   if (elem.requestFullscreen) {elem.requestFullscreen()}

      if(document.fullscreenElement) console.log('fullscreen detected');

  
 });
</script>
```


</details>






<br><br>





<a name="_jquery"><h1>jQuery</h1></a>
<details><summary>Click to expand..</summary>
  
# load (https://api.jquery.com/load/)

## Insert all contents of another same origin HTML file to current page
```javascript
$( "#a" ).load( "article.html" );
```

## Insert specific element of another same origin HTML file to current page
```javascript
$( "#a" ).load( "article.html #example" );
```

<br><br>

# Check for click
```javascript
// method #1
$(".some_class").on("click", function(e) {
  console.log("Event: ", e);
  console.log("Current Target of Event: ", e.currentTarget);
  console.log("this: ", this);
  console.log("$(this): ", $(this));
})

// method #2
$("#clicker").click(function () { /*..*/ });

// method #3
$(document).on('click', '#yourid', function() { /*..*/ });
```

# Check browser (https://api.jquery.com/jQuery.browser/)
```javascript
// method 1
if ($.browser.mozilla) { ... }

//method 2
const isFirefoxBrowser = navigator.userAgent.includes('Firefox');
```


<br><br>

# Event Listener (https://api.jquery.com/category/events/)
```javascript
// method 1 without css selector
  $(window).on("resize scroll click touchstart touchend mouseover mouseout focus focusout",function(e){
  console.log( "Current event class: " + $(e.target).attr('class') );
  console.log( "Current catched event: " + e.type );
  });

// method 2 with css selector
$(document).on("click touchstart touchend", ".owl-dot", function (e) {  });

// method 3
$('input').on('focusout',function(){ //.. });
```

## Manually trigger event listener
```javascript
$('#element').trigger('touchend');
```

<br><br>

# jQuery use !important
```javascript
let elem = $(".ui__downloadList__item.purple");
elem[0].style.removeProperty('z-index');
elem[0].style.setProperty('z-index', '1', 'important');
```

# Handle form submits
```javascript
$("#prospects_form").submit(function(e) {
    e.preventDefault(); // prevent page reload on form submit
});
```


# Get scroll direction
```javascript
// method 1 (for me only this worked stable)
var lastScrollTop = 0;
$(window).scroll(function(event){
   var st = $(window).scrollTop();
   if (st > lastScrollTop){
       // downscroll code
   } else {
      // upscroll code
   }
   lastScrollTop = $(window).scrollTop();
});

//method 2
var lastScrollTop = 0;
$(window).scroll(function(event){
   var st = $(this).scrollTop();
   if (st > lastScrollTop){
       // downscroll code
   } else {
      // upscroll code
   }
   lastScrollTop = st;
});
```

# Class Modification
```javascript
if( $(this).hasClass(animClass) ){
    $(this).removeClass(animClass);
}   $(this).addClass(animClassBlack);
```

# Check for Touch Event (Mobile/Tablet)
```javascript

$(document).on('touchstart touchend', '.skillbarWRAP', function(e) {

/*
var xPos = e.originalEvent.touches[0].pageX;
console.log( 'xPos: ' + xPos );
*/

      if( e.type == 'touchstart' ) console.log( 'TOUCH START - .skillbarWRAP' );  
      else console.log( 'TOUCH END - .skillbarWRAP' );
      
      
});

```

# Wait until scroll is finished
```javascript
$('html').animate({scrollTop: $("layerone").offset().top}, 'slow', function() {
console.log('scroll done..');
});
```


# Scroll to bottom
```javascript
// method #1
$("a[href='#bottom']").click(function() {
  $("html, body").animate({ scrollTop: $(document).height() }, "slow");
  return false;
});

// method #2
document.querySelector(".chat").scrollTop = document.querySelector(".chat").scrollHeight;
```


# Import scripts with callback
```javascript

     $.when(
         $.getScript( "js/headerbig.js" ),
         $.getScript( "js/menubar.js" ),
         $.Deferred(function( deferred ){
             $( deferred.resolve );
         })
     ).done(function(){
         console.log('Scripts Load was performed.');
    });
```

# Get path of element
```javascript
jQuery.fn.getSelector = function() {

    if ($(this).attr('id')) {
        return '#' + $(this).attr('id');
    }

    if ($(this).prop("tagName").toLowerCase() == 'body')    return 'body';

    var myOwn = $(this).attr('class');
    if (!myOwn) {
        myOwn = '>' + $(this).prop("tagName");
    } else {
        myOwn = '.' + myOwn.split(' ').join('.');
    }

    return $(this).parent().getSelector() + ' ' + myOwn;
}


console.log( 'path: ' + $(".owl-carousel .owl-item").getSelector() );

```

# each loop
```javascript
$( ".owl-carousel .owl-item" ).each(function() { });
```




# POST JSON to PHP file
```javascript
let json = {
    email: emailInput,
    subject: subjectInput,
    message: messageInput,
    token: grecaptcha.getResponse()
};

$.post("php/contact.php", json, function(r) {
console.log('result after form submit:' + r);
    if(r == 1) {
        alert('Thanks for posting comment.')
    } else {
        alert('error..')
    }
});
```




# clone
```javascript
  // you can clone a element and then you got the element duplicated in DOM. If needed you can delete the first one after..
  $('#menubar-contact').clone(true).insertAfter($('#menubar-contact'));
  // $('#menubar-contact').remove();
```





# Get parent
```javascript
// vanilla javascript 
document.querySelector('.mdi-link-variant')?.parentNode?.getAttribute('href');

//jquery
$( '.element' ).parent();
```


# Get next
```javascript
// vanilla javascript 
document.getElementById("item1").nextElementSibling

//jquery
$( '.element' ).next();
```

# Append HTML to current element
```javascript
$('.right .top').append`<div class="chat" data-chat="${currentPerson}"></div>`);
```


# Insert HTML after specific element
```javascript
$('.right .top').after(`<div class="chat" data-chat="${currentPerson}"></div>`);
```

<br><br>

# Find element
```javascript
// vanilla javascript 
document.querySelector('.zp_7I-lw')?.querySelectorAll('.zp_3_fnL')[0]?.getAttribute('href')

//jquery
$( '.element' ).find( '.test' );
```


<br><br>

# Draggable
- https://code.jquery.com/ui/
```javascript
<script src="js/jquery.min.js"> </script>
<script src="js/jquery-ui.min.js"> </script>
```

<br><br>

## Exclude element
```html
$(".cardWrap").draggable({ handle: '.cardDescription', cancel: '.cloudimage-360' });
```


</details>








<br><br>







<a name="_async"><h1>Async</h1></a>
<details><summary>Click to expand..</summary>
  
# Create Async
```javascript
// Method 1 - Catch error
(async () => {
 console.log( 'do some async stuff here..' );
})().catch((e) => {
 console.log('Error:' +  e )
}); 

// Method 3 - Do not catch error - you muste use then try inside or wrap another method 1 async function around this
(async () => {
 console.log( 'do some async stuff here..' );
})();

// Method 3 - Do not catch error - you muste use then try inside or wrap another method 1 async function around this
async function test(){
 console.log( 'do some async stuff here..' );
}
```


# setTimeout
```javascript
// method #1
await new Promise(resolve => setTimeout(resolve, 1000));

// method #2
setTimeout(async ()=>
 // some async stuff here..
});
```



# setInterval
- setInterval can be **NOT** used with await. For endless loop you can use while or for
```javascript
// method #1
async function loop() {
  while (true) {
    // click yes button
    document.querySelector('span[data-automation-id="vote-yes-button"]').click();

    // create random break
    const rnd = Math.round(Math.random() * 50 + 1);
    const longBreak = 500000;
    const loopDelay = Math.round(Math.random() * 1000 + 1)
    if (rnd == 1) await new Promise(resolve => setTimeout(resolve, longBreak));
    console.log(rnd);

    await new Promise(resolve => setTimeout(resolve, loopDelay));
  }
}

loop();


// method #2
async function loop() {
  for (;;) {
    // click yes button
    document.querySelector('span[data-automation-id="vote-yes-button"]').click();

    // create random break
    const rnd = Math.round(Math.random() * 50 + 1);
    const longBreak = 500000;
    const loopDelay = Math.round(Math.random() * 1000 + 1)
    if (rnd == 1) await new Promise(resolve => setTimeout(resolve, longBreak));
    console.log(rnd);

    await new Promise(resolve => setTimeout(resolve, loopDelay));
  }
}

loop();
```

<br><br>


# Functions - In Parallel
```javascript
async function a (){
  console.log('a');
};


async function b (){
  console.log('b');
  await new Promise(resolve => setTimeout(resolve, 3000));
  console.log('b later');
};



(async () => {

  await Promise.all([a(), b()]);
  console.log('c');
  
  /*
  // to store the results you can use this..
  let [someResult, anotherResult] = await Promise.all([someCall(), anotherCall()]);  
  
 // ** IMPORTANT **
 // When any promise gets rejected then all other calls after this will get rejected too.. Use instead Promise.allSettled() which will wait for all functions to get finished if resolved or rejected

*/

})().catch((e) => {
   console.log('Error:' +  e )
}); 

```

# Loops (Array) - In Parallel
```javascript
await Promise.all(
  yourArrayHere.map(async d => {
    console.log( 'Current array item we process: ' + d );
     //.. do something
  })    
);
```

# Loops - Sequential (For Loop)
```javascript
for (const d of yourArrayHere) {
    await redirectChecker(d);
 }
```


# Combine Async with promise
```javascript
// example #1 - await for promise resolve
function one(){return new Promise(resolve => { 
  // do something
  resolve(true); 
})};

const result = await one();

// example #2 - async function inside of promise
return new Promise(async resolve => {
  // do something async
  resolve(true); 
})
```

</details>








<br><br>









<a name="_promise"><h1>Promise</h1></a>
<details><summary>Click to expand..</summary>

# async await for promise resolve
```javascript
const load = name => new Promise( resolve => {
  name.onload = () => resolve(true);
});
await load(window);
```

# Nested Functions
```javascript

CheckScrollDirection().then( r => { 
console.log( 'This should come as last message and will contain the value we get from the lowest child function: ' + r );
});


function CheckScrollDirection(){return new Promise(resolve => { 
                scrollafterchangeDOWN().then( r => {  
                      console.log( 'This should come as second message' );
                      resolve(r); 
                 });                      
})};


function scrollafterchangeDOWN(){return new Promise(resolve => { 
                console.log( 'This should come as first message' );
                resolve('direction is down..'); 
})};

```

</details>






<br><br>





<a name="_wait"><h1>Wait</h1></a>
<details><summary>Click to expand..</summary>

## Wait until some condition is true
```javascript
const checkElement = async selector => {
  while ( document.querySelector(selector)?.textContent == 'some_name') {
    await new Promise( resolve =>  requestAnimationFrame(resolve) );
  }
  return document.querySelector(selector);
};

await checkElement('.top .name');
```

</details>







<br><br>







<a name="_loaded"><h1>loaded</h1></a>
<details><summary>Click to expand..</summary>


# Wait until object is loaded
```javascript
// async with promise resolve
const load = name => new Promise( resolve => {
  name.onload = () => resolve(true);
});
await load(window);
```
<br><br>

# Wait until document ready
```javascript
$(function(){ //.. })
```
<br><br>

# Wait until everything is fully loaded and loading icon is gone
```javascript
window.addEventListener('load', function () { //.. });
```
<br><br>

# Wait until element loaded
```javascript
 document.querySelector('.profile').onload = function(e){ //.. }
```
<br><br>

# remove event listener from anonym function
```javascript
document.querySelector('.profile').addEventListener('load', function () { 
  this.removeEventListener('load', arguments.callee);
});
```

</details>







<br><br>












<br><br>







<a name="_google-recaptcha-v2"><h1>Google reCAPTCHA v2</h1></a>
<details><summary>Click to expand..</summary>

Sandbox keys for localhost testing (will always return true):
- Site key: 6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI
- Secret key: 6LeIxAcTAAAAAGG-vFI1TnRWxMZNFuojJ4WifJWe

<br>
<br>
Alternative you can use **localhost** or **127.0.0.1** and create reCAPTCHA for localhost development

```html
<script src="https://www.google.com/recaptcha/api.js" async defer></script>
<!--  Place visible checkbox on your website  -->
<div class="g-recaptcha" data-sitekey="6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI"></div>
```

# Check if user filled Captcha
```js
// grecaptcha.getResponse() will contain the token which has to be sent to the google recaptcha for verify
if( grecaptcha.getResponse().length == 0 ) {
   alert("Please complete the I'm-not-a-robot widget before submitting your entry.");
   return;
}
```

# Simulate Captcha Fail
```js
//download extension like modheader and then change user agent to
Googlebot/2.1
```

# Reset Captcha
```js
grecaptcha.reset();
```


# Change width
```html
<!-- method 1# data-size="compact" -->
<div class="g-recaptcha" data-size="compact"></div>
```

```css
/* method 2 */
.g-recaptcha{
     transform:scale(0.77);
    transform-origin:0 0;
 }
```


```javascript
/* method 3 */

/*
We create a container around the default .g-recaptcha div and then set the witdh where we later re-scale the iframe with scale
.g-recaptcha-wrap{
  width:15vmax;
}
*/
          function scaleCaptcha() {
          console.log( 'captchaScale();' );


              let reCaptchaWidth = 300;
              let containerWidth = $('.g-recaptcha-wrap').width();
              let captchaScale = containerWidth / reCaptchaWidth;
              captchaScale = Math.round(captchaScale * 100) / 100;
              console.log( 'captchaScale: ' + captchaScale + '\ncontainerWidth: ' + containerWidth );


              $('.g-recaptcha').css( 'transform', 'scale('+captchaScale+')' )
                                            .css( '-webkit-transform', 'scale('+captchaScale+')' )
                                            .css( '-moz-transform', 'scale('+captchaScale+')' )
                                            .css( '-ms-transform', 'scale('+captchaScale+')' )
                                            .css( '-o-transform', 'scale('+captchaScale+')' );


          } 


            scaleCaptcha();
            $(window).resize( scaleCaptcha );
```



# PHP Backend do verify of captcha
```php

$url = "https://www.google.com/recaptcha/api/siteverify?secret=".$secretKey."&response=".$captcha."&remoteip=".$_SERVER['REMOTE_ADDR'];
$curl = curl_init($url);

  curl_setopt($curl, CURLOPT_HTTPHEADER, array('Accept: application/json'));
  curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
  $json = curl_exec($curl);
  //echo "request data: ".$json."\n\n";

/*
    if(curl_errno($curl)){
        echo 'Curl error: ' . curl_error($curl);
    }
*/




  $json = json_decode($json);




  if(!empty($json)) {
  //echo $json['success'];
  
    $success = $json->success;
  //echo "success: ".$success."\n\n";




             if( $success == 1 ){
                  echo true;
             } else{
                  echo false;
             }


  } else {
      echo "json empty";
  }


  curl_close($curl);
  exit;
```


</details>








<br><br>







<a name="_before--after"><h1>:before & :after</h1></a>
<details><summary>Click to expand..</summary>
  
# Add new style to :before and :after
```javascript
// method #1
  let styleElem = document.head.appendChild(document.createElement("style"));
      styleElem.innerHTML = ".bar:before {background-color: #fff;}";

      styleElem = document.head.appendChild(document.createElement("style"));
      styleElem.innerHTML = ".bar:after {background-color: #fff;}";
      
// method #1
var style = document.querySelector('.foo').style;
style.setProperty('--background', 'url(http://placekitten.com/200/300)');
/*
.foo::before {
  background: var(--background);
  content: '';
  display: block;
  width: 200px;
  height: 300px;
}
*/
```

</details>








<br><br>








<a name="_animejs"><h1>Anime.js</h1></a>
<details><summary>Click to expand..</summary>

# Remove Animation
```javascript
anime.remove( document.querySelector('#layertwo') )
```

# Bouncing easing
```javascript
{duration: 2000, easing: 'easeOutElastic(1, .2)'} // <-- change .2 to higher value for slower bounce effect
```

</details>








<br><br>








<a name="_owl-carousel"><h1>Owl Carousel</h1></a>
<details><summary>Click to expand..</summary>


# Fix auto width problems / resize on width/height change
```javascript
var carousel = $( '.owl-carousel' ).owlCarousel({
    margin: 25,
    loop: true,
    dots: false,
    autoWidth: true,
    items: 3
});

//carousel.trigger( 'refresh.owl.carousel' );


```

</details>








<br><br>







<a name="_navigator"><h1>Navigator</h1></a>
<details><summary>Click to expand..</summary>


## Get Browser Language
```javascript
var userLang = navigator.language || navigator.userLanguage; 
```

</details>








<br><br>







<a name="_iframe--object"><h1>iframe / object</h1></a>
<details><summary>Click to expand..</summary>


# Embed pdf
```javascript
//method #1
<object width="400" height="400" data="helloworld.pdf"></object>
```


</details>








<br><br>








<a name="_simulate"><h1>Simulate</h1></a>
<details><summary>Click to expand..</summary>


# Simulate Click
```javascript
document.querySelector('.ui__downloadList__item.purple').click();
```

# Simulate Hover
```javascript
// Method #1
var element = document.querySelector('.ui__downloadList__item.purple');

var event = new MouseEvent('mouseover', {
  'view': window,
  'bubbles': true,
  'cancelable': true
});

element.dispatchEvent(event);

// Method #2
$("element").mousover();  
```

# Simulate Touch events
```javascript
var e = new Event('touchend');
document.querySelector('#menubar-contact').dispatchEvent(e);
```

</details>











<br><br>









<a name="_documentwindow"><h1>document/window</h1></a>
<details><summary>Click to expand..</summary>


# remove text from url
```javascript
// http://localhost/myresume/#image1
document.location.hash = ""
// http://localhost/myresume/#
```


<br>
<br>

# Open something new window

```javascript
window.open('img/upwork/jobs/job1.jpg', '_blank', 'location=yes,height=$(window).height(),width=$(window).width(),scrollbars=yes,status=yes');
```

<br>
<br>


# Get link params from oauth popup window
```javascript
// https://gist.github.com/CyberT33N/b6077d75d25e1d728d68caeac6914dd4
// https://www.npmjs.com/package/oauth-open
oauthOpen('http://localhost:1337/oauth-dialog.html', async (err, code) => {
   console.log( 'code: ' + JSON.stringify(code, null, 4) );
});
```

```html
<html>
  <body>

    <div>Authorize OAuth Test App?</div>

    <form action="/code" method="POST">
      <button type="submit">OK</button>
    </form>

  </body>
</html>

```


<br>
<br>

# localStorage (https://www.w3schools.com/jsref/prop_win_localstorage.asp)

```javascript
/* ---- EXAMPLE #1 ----*/

// Store
localStorage.setItem("lastname", "Smith");
// Retrieve
document.getElementById("result").innerHTML = localStorage.getItem("lastname");



/* ---- EXAMPLE #2 ----*/
if (localStorage.clickcount) {
  localStorage.clickcount = Number(localStorage.clickcount) + 1;
} else {
  localStorage.clickcount = 1;
}
document.getElementById("result").innerHTML = "You have clicked the button " +
localStorage.clickcount + " time(s).";
```



</details>










<br><br>









<a name="_clipboard"><h1>clipboard</h1></a>
<details><summary>Click to expand..</summary>



# Copy any text to clipboard
```javascript
  function textToClipboard(text) {
      var dummy = document.createElement("textarea");
      document.body.appendChild(dummy);
      dummy.value = text;
      dummy.select();
      document.execCommand("copy");
      document.body.removeChild(dummy);
  }
```
</details>










<br><br>









<a name="_redirect"><h1>Redirect</h1></a>
<details><summary>Click to expand..</summary>


# Prevent redirect on input search with Enter
```javascript
                           // dont use input as selector or enter key will reload page.. Use always custom class/id
                          $(".searchbox-input").on("keydown",function search(e) {

                                  if( !$(this).val() ) {
                                          $( '.skillbarWRAP-sub-search' ).css( 'display', 'none' );
                                          $( '.ui__friendsList__headline' ).css( 'display', 'block' );
                                          $( '.skills-wrapper' ).css( 'display', 'flex' );
                                  }

                                  if(e.keyCode == 13) { // ENTER KEY
                                     checkSearchValue( $(this).val() );
                                       return false; // prevent page reload on enter
                                  }

                          });

```  
</details>











<br><br>










<a name="_viewport"><h1>Viewport</h1></a>
<details><summary>Click to expand..</summary>

## Stop viewport resize when soft keyboard is activating on mobile
```javascript
let viewheight = $(window).height();
let viewwidth = $(window).width();
let viewport = document.querySelector("meta[name=viewport]");
viewport.setAttribute("content", "height=" + viewheight + "px, width=" + viewwidth + "px, initial-scale=1.0, maximum-scale=1, minimum-scale=1, user-scalable=no, minimal-ui");
```  

</details>









<br><br>









<a name="_before-unload"><h1>Before unload</h1></a>
<details><summary>Click to expand..</summary>



## Do something when current page / popup windows was closed
```javascript
const popup = window.open('oauth-dialog.html', '_blank', 'width=500,height=500');

popup.onbeforeunload = function(){ /* .. */ };
```

</details>










<br><br>











<a name="_osdevice-detect"><h1>Os/Device Detect</h1></a>
<details><summary>Click to expand..</summary>


# Check if tablet/smartphone
```javascript
function mobileAndTabletCheck(){
  let check = false;
  (function(a){if(/(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|iris|kindle|lge |maemo|midp|mmp|mobile.+firefox|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows ce|xda|xiino|android|ipad|playbook|silk/i.test(a)||/1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(a.substr(0,4))) check = true;})(navigator.userAgent||navigator.vendor||window.opera);
  return check;
}
const mobileCheck = mobileAndTabletCheck();
console.log( 'mobile/tablet check:' + mobileCheck );
```  


# Check if iOS
```javascript
  function iOS() {
      return [
        'iPad Simulator',
        'iPhone Simulator',
        'iPod Simulator',
        'iPad',
        'iPhone',
        'iPod'
      ].includes(navigator.platform)
      // iPad on iOS 13 detection
      || (navigator.userAgent.includes("Mac") && "ontouchend" in document)
    };
    const iosCheck = iOS();
    console.log( 'iosCheck check:' + iosCheck );
```  

<br>
<br>


# Check if Safari Browser
```javascript
function checkSafari(){ return /^((?!chrome|android).)*safari/i.test(navigator.userAgent);  } 
```  

</details>










<br><br>










<a name="_tutorials"><h1>Tutorials</h1></a>
<details><summary>Click to expand..</summary>


# The Conditional (Ternary) Operator Explained
https://codeburst.io/javascript-the-conditional-ternary-operator-explained-cac7218beeff

```javascript
// -- Example 1 --
// without ternary
if (person.age >= 16) {
  person.driver = 'Yes';
} else {
  person.driver = 'No';
}
// with ternary
person.driver = person.age >=16 ? 'Yes' : 'No';

// -- Example 2 --
let person = {
  name: 'tony',
  age: 20,
  driver: null
};
person.driver = person.age >=16 ? 'Yes' : 'No';
```


<br><br>

# Object-oriented Programming (OOP)
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_JS
- JavaScript OOP Crash Course (ES5 & ES6) (https://www.youtube.com/watch?v=vDJpGenyHaA)

# Functional Programming
- https://opensource.com/article/17/6/functional-javascript

<br><br>

# Clean Code
- https://github.com/ryanmcdermott/clean-code-javascript

<br><br>

# Optional Chaining (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining)
```javascript
let el = document.querySelector('.zp_33Rq5.zp_49YQRaa')?.querySelectorAll('.mdi-linkedin')[0]?.parentNode?.getAttribute('href');
```


<br><br>

# Scope and Closures
- https://css-tricks.com/javascript-scope-closures/

<br><br>

# Difference between let, var & const
- https://dev.to/sarah_chima/var-let-and-const--whats-the-difference-69e


<br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>

# Microservices

## Object-oriented
- https://nodesource.com/blog/microservices-in-nodejs

<br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>

# YAML
https://rollout.io/blog/yaml-tutorial-everything-you-need-get-started/
```yml
--- 
 doe: "a deer, a female deer"
 ray: "a drop of golden sun"
 pi: 3.14159
 xmas: true
 french-hens: 3
 calling-birds: 
   - huey
   - dewey
   - louie
   - fred
 xmas-fifth-day: 
   calling-birds: four
   french-hens: 3
   golden-rings: 5
   partridges: 
     count: 1
     location: "a pear tree"
   turtle-doves: two
```

</details>

