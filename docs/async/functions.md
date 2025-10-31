# Functions

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

<br><br>


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




<br><br>

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

<br><br>

# .call()
- The call() method is a predefined JavaScript method. It can be used to invoke (call) a method with an owner object as an argument (parameter).
```javascript
var person = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person1 = {
  firstName:"John",
  lastName: "Doe"
}
var person2 = {
  firstName:"Mary",
  lastName: "Doe"
}
person.fullName.call(person1);  // Will return "John Doe"
```



<br><br>

# .apply()
- The Difference Between call() and apply() is:
<br> The call() method takes arguments separately.
<br> The apply() method takes arguments as an array.
```javascript
// ---- EXAMPLE #1 - with Arguments ----
var person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}
var person1 = {
  firstName:"John",
  lastName: "Doe"
}
person.fullName.apply(person1, ["Oslo", "Norway"]);




// ---- EXAMPLE #2 - with Objects ----
var person = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person1 = {
  firstName: "Mary",
  lastName: "Doe"
}
person.fullName.apply(person1);  // Will return "Mary Doe"
```

	
<br><br>

## Add new variables to scope of function
- This will not work with bind only with apply
```javascript
const fn = function () {
    console.log(this.firstName)
    console.log(this.lastName)
    return this.firstName
}
	
var person = {
  firstName: "Mary",
  lastName: "Doe"
}

// This will call ne function
const res = fn.apply(person)
```


<br><br>

# .bind() (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
- The bind() method creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
- Make sure to create a new variable when you bind something.
```javascript
// Base Example
const fn = anyFn.bind(this.machine)
const data = await fn()



// Example Core - Call Function and bind any this property to it and call it:
await yourFn.bind({ yourPropName })()


// Example #0
const fn = function(apple) {
    console.log('apple:', apple)
}

const obj = {
    apple:true
}

const test = fn.bind(this, obj)

test()
	
	
	
	
	
	
// Example #1	
// a function
var something = function (a, b, c) {
  console.log(a, b, c);
};

// a binding of something with 3 defined args
var b = something.bind(null, 1, 2, 3);

// call b
b();
//=> 1 2 3
	
	
	
// Example #2
const module = {
  x: 42,
  getX: function() {
    return this.x;
  }
};

const unboundGetX = module.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope
// expected output: undefined

const boundGetX = unboundGetX.bind(module);
console.log(boundGetX());
// expected output: 42

```

<br><br>




# Use Function as variable
```javascript
/*---- EXAMPLE #1 ----*/
async _onDisconnect() {
    console.log('disconnect..');
}

createDisconnectListener() {
    this.browser.on('disconnected', this._onDisconnect )
}



/*---- EXAMPLE #2 ----*/
function greet(){
  alert('Howdy!');
}
setTimeout(greet, 2000);
```


<br><br>






# Higher-order Functions
- Higher-order functions are functions that take other functions as arguments or return functions as their results.

<br><br>

Taking an other function as an argument is often referred as a callback function, because it is called back by the higher-order function. This is a concept that Javascript uses a lot.

<br><br>

For example, the map function on arrays is a higher order function. The map function takes a function as an argument.
```javascript
const double = n => n * 2
[1, 2, 3, 4].map(double) // [ 2, 4, 6, 8 ]


// Or, with an anonymous function:
[1, 2, 3, 4].map(function(n){
    return n * 2
}) // [ 2, 4, 6, 8 ]
```












<br><br>



# Get name of function
```javascript
function test(){};
console.log(test.name); // test
```












<br><br>



# Pass Params without braces
```javascript
// ---- EXAMPLE #1 - Single Param ----
function printName(name){
  console.log('HI my name is: ' + name);
};

printName`Laura`



// ---- EXAMPLE #2 - Multiple Param ----
function printName(allDetails, name, age){
  console.log(`HI my name is ${name} and I am ${age}`);
};

const name = 'Laura'
const age = 20
printName`${name}${age}`



// ---- EXAMPLE #3 - Multiple Param but use Array ----
function printName(allDetails, ...array){
  console.log(`HI my name is ${array[0]} and I am ${array[1]}`);
};

const name = 'Laura'
const age = 20
printName`${name}${age}`
```















































<br><br>


# Generator Functions (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/function*)
- The function* declaration (function keyword followed by an asterisk) defines a generator function, which returns a Generator object.
- In easy words *yield* almost act like return. It will make the function stop. Then we you call in future time *.next()* it will start at the last yield where we finished the function last time and then continue with the code inside of this function.

```javascript
function* generator(i) {
  yield i;
  yield i + 10;
}

const gen = generator(10);

console.log(gen.next().value);
// expected output: 10

console.log(gen.next().value);
// expected output: 20
```



















<br><br>


# Lambda Function
- https://medium.com/@chineketobenna/lambda-expressions-vs-anonymous-functions-in-javascript-3aa760c958ae
```javascript
function traverseArray(arr, func) {
//..
}
```



<br><br>



# Anonymous Function
- https://medium.com/@chineketobenna/lambda-expressions-vs-anonymous-functions-in-javascript-3aa760c958ae
- An anonymous function is, as its name implies, a function without a name (no pun intended). They are most popularly used to define function expressions. An example of such usage is shown below.

<br><br>


These function expressions are created at runtime and must be declared/defined before they can be called i.e. they are not hoisted, unlike function declarations that are hoisted as soon as program execution begins and can be called before its actual declaration.
```javascript
//printName("Tom");     
//ReferenceError: printName is not defined
const printName = function (name){ 
   console.log(name);
}
printName("Tom");      
//result: Tom
```

	
	
	
	
	
	
<br><br>



# Default function parameter (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Functions/Default_parameters)
```javascript
function multiply(a, b = 1) {
  return a * b;
}

console.log(multiply(5, 2));
// expected output: 10

console.log(multiply(5));
// expected output: 5





// ---- EXAMPLE #2 - Object Destructuring ----
function getConnection({dbName, force = false, models = []} = {}) {
  console.log('dbName: ' + dbName);
}

getConnection({dbName: true})
```
