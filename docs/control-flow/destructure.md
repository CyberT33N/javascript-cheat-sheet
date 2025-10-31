# Destructure

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
