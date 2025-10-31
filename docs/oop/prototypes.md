# Prototypes

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
