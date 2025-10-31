# Design Patterns

## Guides
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/

<br><br>

# Singleton Pattern

<br>

## Guides
- https://www.youtube.com/watch?v=sJ-c3BA-Ypo

<br><br>

## Singleton with Classes

<br><br>

### Example #1 **RECOMMENDED**
```typescript
class ModelManager {
    // eslint-disable-next-line no-use-before-define
    private static instance: ModelManager
    models: Array<{
        modelName: string
        model: mongoose.Model<any>
    }>

    private constructor() {
        this.models = []
    }
  
    static async getInstance() {
        if (this.instance) {
            return this.instance
        }
      
        // Create instance
        this.instance = new ModelManager()

        // ==== VARIABLES ====
        this.instance.models = []

        // ==== INITIALIZATION ====
        await this.instance.init()

        return this.instance
    }

    private async init() {
        if(!this.models) {
            const path = `${getDirname()}/**/*.model.js`
            this.models = await this.globModels(path)
        }
    }

    private async globModels(expression: string) {
        const modelPaths = await glob(expression)
 
        const models = []

        for (const path of modelPaths) {
            const file = await import(path)
            const Model = await file.default()
            models.push(Model)
        }

        return models
    }

    public async getModels() {
        const models = this.models
        return models
    }

    public async getModel(name: string) {
        const model = this.models.find(model => model.modelName === name)
        return model
    }
}

```
- This how you can reset the instance in your test:
	```typescript
	beforeEach(async() => {
	       // Reset instance before creating a new one
                ModelManager['instance'] = null
		// Reflect.set(ModelManager, 'instance', null)
		modelManager = await ModelManager.getInstance()
	})
	```





<br><br>
<br><br>

### Example #3
- Old style
```javascript
/**
 *
 */
class MongooseUtils {
    /**
     *
     * @param name
     * @returns {MongooseUtils}
     */
    constructor(name) {
        if (MongooseUtils.instance === undefined) {
            // Because we override here the instance of the class with this we can declear any first singleton init call properties here with this.
            this.base = 1234
            MongooseUtils.instance = this
        }

        // If you want to change instance properties by inherit a new instance class with properties you must override the instance which we return. If you create a new instance and do not pass params for consstructor then we will use a fallback to the last value of the singleton
        MongooseUtils.instance.name = name || MongooseUtils.instance.name

        return MongooseUtils.instance
    }

    /**
     *
     * @param data
     */
    createData(data){
        this.example = data
    }
}

const instanceA = new MongooseUtils('test1')
instanceA.createData('a')
console.log('instanceA: ' + instanceA.example) // <-- will print a
console.log('instanceA name: ' + instanceA.name) // <-- will print test1
console.log('instanceA base: ' + instanceA.base) // <-- will print 1234

const instance2 = new MongooseUtils()
console.log('instance2: ' + instance2.example) // <-- will print a
console.log('instance2 name: ' + instance2.name) // <-- will print test1
console.log('instance2 base: ' + instance2.base) // <-- will print 1234

const instance3 = new MongooseUtils('test3')
console.log('instance3: ' + instance3.example) // <-- will print a
console.log('instance3 name: ' + instance3.name) // <-- will print test3
console.log('instance3 base: ' + instance3.base) // <-- will print 1234
```



















 
# Builder Pattern

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





// ---- EXAMPLE #2 - Object Destructuring ----
function getConnection({dbName, force = false, models = []} = {}) {
  console.log('dbName: ' + dbName);
}

getConnection({dbName: true})
	
	
	
	

// ---- EXAMPLE #3 - Nested Object Destructuring ----
function doit( {arg1 = 'one', hash = { prop1: 'two', prop2: 'three' }} = {} ) {
    console.log(`arg1`, arg1)
    console.log(`hash`, hash)
}

doit()
	
const hash = {hash: {prop1: false}}
doit(hash)
```


	
	
<br><br>

## Endless loop without memory leak
```javascript
// method #1
function loginf() {
  console.log(1+1);
  process.nextTick(loginf);
}
	
loginf();
	
	
// method #2
function loginf() {
  console.log(1+1);
  setImmediate(loginf);
}
loginf();
	

// method #3
const mainLoop = async() => {
	for (;;) {
	  await main()
	}
}

mainLoop().catch(console.error)
```

	
	
	
	
	




















## Null Object Pattern

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
















## Factory Pattern
- Is in the **creation** category of design patterns which means providing object creation mechanism for flexibility and reusability. This is usefully when you want to create many types of different objects.

<br>

## Guides
- https://www.youtube.com/watch?v=kuirGzhGhyw

<br><br>

```javascript
function developer(name) {
  this.name = name;
  this.type = 'Developer';
};

function tester(name) {
  this.name = name;
  this.type = 'Tester';
};

function employeeFactory() {
  this.create = (name, type) => {
    switch (type) {
      case 1:
        return new developer(name);
        break;
      case 2:
        return new tester(name);
        break;
    }
  }
};

function say() {
  console.log(`Hi, I am ${this.name} and I am a ${this.type}`);
};

const factory = new employeeFactory();
const employees = [];

employees.push(factory.create("Lisa", 1)) // <-- Creates new Developer
employees.push(factory.create("Julia", 2)) // <-- Creates new Tester

for(const emp of employees){
  say.call(emp);
}
```















## Proxy Pattern
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy

<br>

## Guides
- [https://www.youtube.com/watch?v=SFTpSFQNPts](https://www.patterns.dev/vanilla/proxy-pattern)

<br><br>

```javascript
const person = {

  name: "John Doe",

  age: 42,

  nationality: "American"

};


const personProxy = new Proxy(person, {

  get: (obj, prop) => {

    console.log(`The value of ${prop} is ${obj[prop]}`);

  },

  set: (obj, prop, value) => {

    console.log(`Changed ${prop} from ${obj[prop]} to ${value}`);

    obj[prop] = value;

    return true;

  }

});


personProxy.name;

personProxy.age = 43;
```
- When accessing the name property, the Proxy returned a better sounding sentence: The value of name is John Doe.
- When modifying the age property, the Proxy returned the previous and new value of this property: Changed age from 42 to 43.



A proxy can be useful to add validation. A user shouldn't be able to change person's age to a string value, or give them an empty name. Or if the user is trying to access a property on the object that doesn't exist, we should let the user know.
```javascript
const personProxy = new Proxy(person, {
  get: (obj, prop) => {
    if (!obj[prop]) {
      console.log(
        `Hmm.. this property doesn't seem to exist on the target object`
      );
    } else {
      console.log(`The value of ${prop} is ${obj[prop]}`);
    }
  },
  set: (obj, prop, value) => {
    if (prop === "age" && typeof value !== "number") {
      console.log(`Sorry, you can only pass numeric values for age.`);
    } else if (prop === "name" && value.length < 2) {
      console.log(`You need to provide a valid name.`);
    } else {
      console.log(`Changed ${prop} from ${obj[prop]} to ${value}.`);
      obj[prop] = value;
    }
  },
});
```



JavaScript provides a built-in object called Reflect, which makes it easier for us to manipulate the target object when working with proxies.

Previously, we tried to modify and access properties on the target object within the proxy through directly getting or setting the values with bracket notation. Instead, we can use the Reflect object. The methods on the Reflect object have the same name as the methods on the handler object.

Instead of accessing properties through obj[prop] or setting properties through obj[prop] = value, we can access or modify properties on the target object through Reflect.get() and Reflect.set(). The methods receive the same arguments as the methods on the handler object.
```javascript
const person = {

  name: "John Doe",

  age: 42,

  nationality: "American"

};


const personProxy = new Proxy(person, {

  get: (obj, prop) => {

    console.log(`The value of ${prop} is ${Reflect.get(obj, prop)}`);

  },

  set: (obj, prop, value) => {

    console.log(`Changed ${prop} from ${obj[prop]} to ${value}`);

    return Reflect.set(obj, prop, value);

  }

});


personProxy.name;

personProxy.age = 43;

personProxy.name = "Jane Doe";
```







<br><br>
<br><br>





## Dependency Injection Pattern

<br>

## Guides
- https://www.youtube.com/watch?v=0X1Ns2NRfks

<br><br>

```javascript
const assert = require('assert')

function getAnimals(fetch, id) {
  return fetch('http://api.animalfarmgame.com/animals/' + id)
    .then(response => response.json())
    .then(data => data.results[0])
}

describe('getAnimals', () => {
  it('calls fetch with the correct url', () => {
    const fakeFetch = url => {
      assert(
        url ===
        'http://api.animalfarmgame.com/animals/123'
      )
      return new Promise(function(resolve) {

      })
    }
    getAnimals(fakeFetch, 123)
  })

  it('parses the response of fetch correctly', (done) => {
    const fakeFetch = () => {
      return Promise.resolve({
        json: () => Promise.resolve({
          results: [
            { name: 'fluffykins' }
          ]
        })
      })
    }
    getAnimals(fakeFetch, 12345)
      .then(result => {
        assert(result.name === 'fluffykins')
        done()
      })
  })
})
```








































## PubSub Pattern

<br>

## Guides
- https://www.youtube.com/watch?v=nQRXi1SVOow

<br><br>

```javascript
//events - a super-basic Javascript (publish subscribe) pattern

var events = {
  events: {},
  on: function (eventName, fn) {
    this.events[eventName] = this.events[eventName] || [];
    this.events[eventName].push(fn);
  },
  off: function(eventName, fn) {
    if (this.events[eventName]) {
      for (var i = 0; i < this.events[eventName].length; i++) {
        if (this.events[eventName][i] === fn) {
          this.events[eventName].splice(i, 1);
          break;
        }
      };
    }
  },
  emit: function (eventName, data) {
    if (this.events[eventName]) {
      this.events[eventName].forEach(function(fn) {
        fn(data);
      });
    }
  }
};
```















<br><br><br><br>

## Module Pattern
- Modules are an integral piece of any robust application's architecture and typically help in keeping the units of code for a project both cleanly separated and organized.

<br>

## Guides
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript

<br><br>
```javascript
var myModule = {
 
  myProperty: "someValue",
 
  // object literals can contain properties and methods.
  // e.g we can define a further object for module configuration:
  myConfig: {
    useCaching: true,
    language: "en"
  },
 
  // a very basic method
  saySomething: function () {
    console.log( "Where in the world is Paul Irish today?" );
  },
 
  // output a value based on the current configuration
  reportMyConfig: function () {​
    console.log( "Caching is: " + ( this.myConfig.useCaching ? "enabled" : "disabled") );
  },
 
  // override the current configuration
  updateMyConfig: function( newConfig ) {
 
    if ( typeof newConfig === "object" ) {
      this.myConfig = newConfig;
      console.log( this.myConfig.language );
    }
  }
};
 
// Outputs: Where in the world is Paul Irish today?
myModule.saySomething();
 
// Outputs: Caching is: enabled
myModule.reportMyConfig();
 
// Outputs: fr
myModule.updateMyConfig({
  language: "fr",
  useCaching: false
});
 
// Outputs: Caching is: disabled
myModule.reportMyConfig();
```














































<br><br><br><br>

## Revealing Module Pattern
- The main Goal of this design pattern is to isolate variabels/functions that you can not access them from outside. The only way to access/change them is by returning them.

<br>

## Guides
- https://www.youtube.com/watch?v=SKBmJ9P6OAk

<br><br>
```javascript
// Before ES6
(function() {

    // declare private variables and/or functions

    return {
      // declare public variables and/or functions
    }

})();




// After ES6
/* lib/module.js */

class ShoppingDataType {
  constructor() {
    // private properties.
    this.shoppingList = ['coffee', 'chicken', 'pizza']
  }

  // public methods
  getShoppingList() {
    return this.shoppingList.join(", ")
  }

  addItem(item) {
   this.shoppingList.push(item)
  }
}

export default ShoppingDataType;


/* main.js */
import ShoppingDataType from 'libs/module';

var shopping = new ShoppingDataType;
console.log(shopping.getShoppingList());
```

































<br><br><br><br>



## Constructor Pattern
- In classical object-oriented programming languages, a constructor is a special method used to initialize a newly created object once memory has been allocated for it. In JavaScript, as almost everything is an object, we're most often interested in object constructors.

<br>

## Guides
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/#constructorpatternjavascript

<br><br>
```javascript
function Car( model, year, miles ) {
 
  this.model = model;
  this.year = year;
  this.miles = miles;
 
  this.toString = function () {
    return this.model + " has done " + this.miles + " miles";
  };
}
 
// Usage:
 
// We can create new instances of the car
var civic = new Car( "Honda Civic", 2009, 20000 );
var mondeo = new Car( "Ford Mondeo", 2010, 5000 );
 
// and then open our browser console to view the
// output of the toString() method being called on
// these objects
console.log( civic.toString() );
console.log( mondeo.toString() );
```















































<br><br><br><br>

## Observer Pattern
- Define a one to many dependency relationship. From subject object to many other objects (observers). These observers are functions which watch the subject and wait for trigger before they run. It may reminder you to event listener.

<br><br>

## Guides
- https://www.youtube.com/watch?v=45TeJEmcqk8

<br><br>
```javascript
/*
    Observer Design Pattern -> https://www.youtube.com/watch?v=45TeJEmcqk8
    Author: DevSage (Youtube) -> https://www.youtube.com/DevSage
*/

function Subject()
{
  this.observers = [] // array of observer functions
}

Subject.prototype = {
  subscribe: function(fn)
  {
    this.observers.push(fn)
  },
  unsubscribe: function(fnToRemove)
  {
    this.observers = this.observers.filter( fn => {
      if(fn != fnToRemove)
        return fn
    })
  },
  fire: function()
  {
    this.observers.forEach( fn => {
      fn.call()
    })
  }
}

const subject = new Subject()

function Observer1()
{
  console.log("Observer 1 Firing!")
}

function Observer2()
{
  console.log("Observer 2 Firing!")
}

subject.subscribe(Observer1)
subject.subscribe(Observer2)
subject.fire() 

subject.unsubscribe(Observer1)
subject.fire()
```







































<br><br><br><br>

## Mediator Pattern

<br><br>

## Guides
- https://www.youtube.com/watch?v=ZuhgOu-DGA4

<br><br>
```javascript
/*
    Mediator Design Pattern -> https://youtu.be/ZuhgOu-DGA4
    Author: DevSage (Youtube) -> https://www.youtube.com/DevSage
*/


function Member(name)
{
  this.name = name
  this.chatroom = null
}

Member.prototype = {
  send: function(message, toMember)
  {
    this.chatroom.send(message, this, toMember)
  },
  receive: function(message, fromMember)
  {
    console.log(`${fromMember.name} to ${this.name}: ${message}`)
  }
}

function Chatroom()
{
  this.members = {}
}

Chatroom.prototype = {
  addMember: function(member)
  {
    this.members[member.name] = member
    member.chatroom = this
  },
  send: function(message, fromMember, toMember)
  {
    toMember.receive(message, fromMember)
  }
}

const chat = new Chatroom()

const bob = new Member("Bob")
const john = new Member("John")
const tim = new Member("Tim")

chat.addMember(bob)
chat.addMember(john)
chat.addMember(tim)

bob.send("Hey, John", john)
john.send("What's up, Bob", bob)
tim.send("John, are you ok?", john)
```









































<br><br><br><br>

## Prototype Pattern
- The GoF refer to the prototype pattern as one which creates objects based on a template of an existing object through cloning.

<br><br>

## Guides
- https://www.youtube.com/watch?v=doXpW5AD60Q
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/#prototypepatternjavascript

<br><br>
```javascript
var myCar = {
 
  name: "Ford Escort",
 
  drive: function () {
    console.log( "Weeee. I'm driving!" );
  },
 
  panic: function () {
    console.log( "Wait. How do you stop this thing?" );
  }
 
};
 
// Use Object.create to instantiate a new car
var yourCar = Object.create( myCar );
 
// Now we can see that one is a prototype of the other
console.log( yourCar.name );
```













































<br><br><br><br>

## Command Pattern
- The Command pattern aims to encapsulate method invocation, requests or operations into a single object and gives us the ability to both parameterize and pass method calls around that can be executed at our discretion. In addition, it enables us to decouple objects invoking the action from the objects which implement them, giving us a greater degree of overall flexibility in swapping out concrete classes (objects).

<br><br>

## Guides
- https://www.youtube.com/watch?v=GQzfF5EMD7o
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/#commandpatternjavascript

<br><br>
```javascript
class Calculator {
  constructor() {
    this.value = 0
    this.history = []
  }

  executeCommand(command) {
    this.value = command.execute(this.value)
    this.history.push(command)
  }

  undo() {
    const command = this.history.pop()
    this.value = command.undo(this.value)
  }
}

class AddCommand {
  constructor(valueToAdd) {
    this.valueToAdd = valueToAdd
  }

  execute(currentValue) {
    return currentValue + this.valueToAdd
  }

  undo(currentValue) {
    return currentValue - this.valueToAdd
  }
}

class SubtractCommand {
  constructor(valueToSubtract) {
    this.valueToSubtract = valueToSubtract
  }

  execute(currentValue) {
    return currentValue - this.valueToSubtract
  }

  undo(currentValue) {
    return currentValue + this.valueToSubtract
  }
}

class MultiplyCommand {
  constructor(valueToMultiply) {
    this.valueToMultiply = valueToMultiply
  }

  execute(currentValue) {
    return currentValue * this.valueToMultiply
  }

  undo(currentValue) {
    return currentValue / this.valueToMultiply
  }
}

class DivideCommand {
  constructor(valueToDivide) {
    this.valueToDivide = valueToDivide
  }

  execute(currentValue) {
    return currentValue / this.valueToDivide
  }

  undo(currentValue) {
    return currentValue * this.valueToDivide
  }
}

class AddThenMultiplyCommand {
  constructor(valueToAdd, valueToMultiply) {
    this.addCommand = new AddCommand(valueToAdd)
    this.multiplyCommand = new MultiplyCommand(valueToMultiply)
  }

  execute(currentValue) {
    const newValue = this.addCommand.execute(currentValue)
    return this.multiplyCommand.execute(newValue)
  }

  undo(currentValue) {
    const newValue = this.multiplyCommand.undo(currentValue)
    return this.addCommand.undo(newValue)
  }
}
```

























































<br><br><br><br>

## Facade Pattern
- When we put up a facade, we present an outward appearance to the world which may conceal a very different reality. This was the inspiration for the name behind the next pattern we're going to review - the Facade pattern. This pattern provides a convenient higher-level interface to a larger body of code, hiding its true underlying complexity. Think of it as simplifying the API being presented to other developers, something which almost always improves usability.



<br><br>

## Guides
- https://www.youtube.com/watch?v=fHPa5xzbpaA
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/#facadepatternjavascript

<br><br>
```javascript
function getUsers() {
  return getFetch('https://jsonplaceholder.typicode.com/users')
}

function getUserPosts(userId) {
  return getFetch('https://jsonplaceholder.typicode.com/posts', {
    userId: userId
  })
}

getUsers().then(users => {
  users.forEach(user => {
    getUserPosts(user.id).then(posts => {
      console.log(user.name)
      console.log(posts.length)
    })
  })
})

// function getFetch(url, params = {}) {
//   const queryString = Object.entries(params).map(param => {
//     return `${param[0]}=${param[1]}`
//   }).join('&')
//   return fetch(`${url}?${queryString}`, {
//     method: "GET",
//     headers: { "Content-Type": "application/json" }
//   }).then(res => res.json())
// }

function getFetch(url, params = {}) {
  return axios({
    url: url,
    method: "GET",
    params: params
  }).then(res => res.data)
}
```
































<br><br><br><br>

## Enum Pattern
- https://masteringjs.io/tutorials/fundamentals/enum

```javascript
class Direction {
  static Up = new Direction('Up');
  static Down = new Direction('Down');
  static Left = new Direction('Left');
  static Right = new Direction('Right');

  constructor(name) {
    this.name = name;
  }
  toString() {
    return `Color.${this.name}`;
  }
}
```






























<br><br><br><br>

## Decorator Pattern
- Decorators are a structural design pattern that aim to promote code re-use. Similar to Mixins, they can be considered another viable alternative to object sub-classing.

<br><br>

Classically, Decorators offered the ability to add behaviour to existing classes in a system dynamically. The idea was that the decoration itself wasn't essential to the base functionality of the class, otherwise it would be baked into the superclass itself.



<br><br>

## Guides
- https://addyosmani.com/resources/essentialjsdesignpatterns/book/#decoratorpatternjavascript

<br><br>

## Example 1: Decorating Constructors With New Functionality
```javascript
// A vehicle constructor
function Vehicle( vehicleType ){
 
    // some sane defaults
    this.vehicleType = vehicleType || "car";
    this.model = "default";
    this.license = "00000-000";
 
}
 
// Test instance for a basic vehicle
var testInstance = new Vehicle( "car" );
console.log( testInstance );
 
// Outputs:
// vehicle: car, model:default, license: 00000-000
 
// Lets create a new instance of vehicle, to be decorated
var truck = new Vehicle( "truck" );
 
// New functionality we're decorating vehicle with
truck.setModel = function( modelName ){
    this.model = modelName;
};
 
truck.setColor = function( color ){
    this.color = color;
};
 
// Test the value setters and value assignment works correctly
truck.setModel( "CAT" );
truck.setColor( "blue" );
 
console.log( truck );
 
// Outputs:
// vehicle:truck, model:CAT, color: blue
 
// Demonstrate "vehicle" is still unaltered
var secondInstance = new Vehicle( "car" );
console.log( secondInstance );
 
// Outputs:
// vehicle: car, model:default, license: 00000-000
```



## Example 2: Decorating Constructors With New Functionality
```javascript
// The constructor to decorate
function MacBook() {
 
  this.cost = function () { return 997; };
  this.screenSize = function () { return 11.6; };
 
}
 
// Decorator 1
function memory( macbook ) {
 
  var v = macbook.cost();
  macbook.cost = function() {
    return v + 75;
  };
 
}
 
// Decorator 2
function engraving( macbook ){
 
  var v = macbook.cost();
  macbook.cost = function(){
    return v + 200;
  };
 
}
 
// Decorator 3
function insurance( macbook ){
 
  var v = macbook.cost();
  macbook.cost = function(){
     return v + 250;
  };
 
}
 
var mb = new MacBook();
memory( mb );
engraving( mb );
insurance( mb );
 
// Outputs: 1522
console.log( mb.cost() );
 
// Outputs: 11.6
console.log( mb.screenSize() );
```
