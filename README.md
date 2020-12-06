# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..


<br><br>

# Summary
<details><summary>Click to expand..</summary>
  
# [Switch](#switch)
1. Add a section that will alert("Neither") if fruits is neither "banana" nor "apple"

# [For loop](#for-loop)
1. Do loop based on length of array
2. Make the loop jump to the next iteration when i is 5
3. break the loop when i is 5

# [While](#while)
1. Do loop based on length of array

# [Functions](#functions)
1. function to String and back to function

# [ESM (es-modules) and CJS (commonjs)](#esm-es-modules-and-cjs-commonjs)
1. Examples for difference
2. ESM
  <br>2.1 Features
  <br>2.2 How to enable?
  <br>2.3 Export / Import
  <br>2.4 Client Side
  <br>2.5 No require, exports, module.exports, __filename, __dirname

# [Prototypes](#prototypes)
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

# [Classes](#classes)
1. Change/add constructor value
2. static (isolated function)
3. subclasses (extends)

# [Time/Date](#time)
1. format time to AM/PM
2. get current Date

# [Filter](#filter)
1. compare 2 arrays of objects and remove duplicates

# [Sort](#sort)
1. Sort Array by Numbers ASC
2. Sort Array by String ASC
3. Sort Array by two values ASC

# [Cookie](#cookie)
1. Get value of specific cookie

# [Object](#object)
1. Check if Object is empty

# [Link](#link)
1. Get current link / domain

# [API](#api)
1. Enter fullscreen

# [jQuery](#jquery)
1. load
  <br>1.1 Insert all contents of another same origin HTML file to current page
  <br>1.2 Insert specific element of another same origin HTML file to current page
<br><br>
2. Check for click
3. Check browser
4. Event Listener
4.1 Manually trigger event listener
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

# [Async](#async)
1. Create Async
2. setTimeout
3. setInterval
4. Functions - In Parallel
5. Loops (Array) - In Parallel
6. Loops - Sequential (For Loop)
7. Combine Async with promise

# [Promise](#promise)
1. async await for promise resolve
2. Nested Functions

# [Wait](#wait)
1. Wait until some condition is true

# [Loaded](#loaded)
1. Wait until object is loaded
2. Wait until document ready
3. Wait until everything is fully loaded and loading icon is gone
4. Wait until element loaded
5. remove event listener from anonym function

# [Array](#array)
1. Clone unique
2. clone array
3. clone array with objects inside
4. get random item from array

# [Google reCAPTCHA v2](#google-recaptcha-v2)
1. Check if user filled Captcha
2. Simulate Captcha Fail
3. Reset Captcha
4. Change width
5. PHP Backend do verify of captcha

# [:before & :after](#before--after)
1. Add new style to :before and :after

# [Anime.js](#animejs)
1. Remove Animation
2. Bouncing easing

# [Owl Carousel](#owl-carousel)
1. Fix auto width problems / resize on width/height change

# [Navigator](#navigator)
1. Get Browser Language




</details>



 <br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>


# Switch
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

# For loop
<details><summary>Click to expand..</summary>
  
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

<br>

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



 # While
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


</details>


 <br><br>


# functions
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

</details>

 <br><br>


# ESM (es-modules) and CJS (commonjs)
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

# Prototypes
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

# Classes
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


# subclasses (extends)
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

</details>


<br><br>




# time
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


# filter
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

# Sort
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


# Cookie
<details><summary>Click to expand..</summary>
  
## Get value of specific cookie
```javascript
var regex = /MyCookie=(.[^;]*)/ig;
var match = regex.exec(document.cookie);
var value = match[1];
```
</details>


<br><br>

# Object
<details><summary>Click to expand..</summary>

# Check if Object is empty
```javascript
var obj = {};
if( Object.entries(obj).length < 1 ) console.log('empty');

var obj = {"not": "empty"};
if( Object.entries(obj).length > 0 ) console.log('not empty');
```

</details>


<br><br>

# Link
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

# API
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

# jQuery
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


# Find element
```javascript
// vanilla javascript 
document.querySelector('.zp_7I-lw')?.querySelectorAll('.zp_3_fnL')[0]?.getAttribute('href')

//jquery
$( '.element' ).find( '.test' );
```

</details>



<br><br>


# Async
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
// async
await new Promise(resolve => setTimeout(resolve, 1000));

// non blocking sync with async inside
setTimeout( async () => {   await page.hover('video');    }, 5000);
```



# setInterval
```javascript
var count = 0;
var countdownInterval = setInterval(async () => {

    count++
    if( count == 10 ) clearInterval( countdownInterval );
                                
}, 1000);
```



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


# Promise
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

# Wait
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
 _____________________________________________________
 _____________________________________________________
<br><br>

# loaded
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




# array
<details><summary>Click to expand..</summary>


# Clone unique
For default javascript act like this:
```js
var arr1 = ['a','b','c'];
var arr2 = arr1;
arr2.push('d');  //Now, arr1 = ['a','b','c','d']
```

In order to create unique clones check below..

# clone array
```js
var arr = [2,3,4,5];
var copyArr = [...arr];
```

# clone array with objects inside
```js
var arr = [{"a":1}, {"b":2}];
var copyArr = JSON.parse(JSON.stringify(arr));
```



# get random item from array
```js
var rndval=items[Math.floor(Math.random()*items.length)];
```

</details>




<br><br>




# Google reCAPTCHA v2
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




# :before & :after
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





# Anime.js
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




# Owl Carousel
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





# Navigator
<details><summary>Click to expand..</summary>


## Get Browser Language
```javascript
var userLang = navigator.language || navigator.userLanguage; 
```

</details>




<br><br>




# iframe / object
<details><summary>Click to expand..</summary>


# Embed pdf
```javascript
//method #1
<object width="400" height="400" data="helloworld.pdf"></object>
```


</details>




<br><br>





# Simulate
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






# document/window
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


</details>






<br><br>





# clipboard
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






# Redirect
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






# Viewport
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





# Before unload
<details><summary>Click to expand..</summary>



## Do something when current page / popup windows was closed
```javascript
const popup = window.open('oauth-dialog.html', '_blank', 'width=500,height=500');

popup.onbeforeunload = function(){ /* .. */ };
```

</details>




<br><br>






# Os/Device Detect
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





# Tutorials
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

# Immediately Invoked Function Expression (IIFE)
- https://www.youtube.com/watch?v=eY7u388cvM4

<br><br>

# Spread Operators
- https://www.youtube.com/watch?v=I5AGSH8ROSU
- https://dev.to/livecodestream/how-to-use-the-spread-operator-in-javascript-35bn
- https://medium.com/javascript-in-plain-english/how-to-deep-copy-objects-and-arrays-in-javascript-7c911359b089

<br><br>

# Scope and Closures
- https://css-tricks.com/javascript-scope-closures/

<br><br>

# Difference between let, var & const
- https://dev.to/sarah_chima/var-let-and-const--whats-the-difference-69e

<br><br>

# Destruction
- https://dev.to/quantumsheep/all-you-need-to-know-about-destructuring-in-javascript-1hla

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

