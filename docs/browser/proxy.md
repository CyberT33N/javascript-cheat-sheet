# Proxy

<br><br>

# Guides
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy
- https://www.javascripttutorial.net/es6/javascript-proxy/#:~:text=A%20JavaScript%20Proxy%20is%20an,%2C%20and%20function%20invocations%2C%20etc.

<br><br>

```javascript
# method #1 - Mongoose Model example
js cheat sheet
import mongoose from 'mongoose';

// Dein ursprüngliches Mongoose-Modell
const OriginalModel = mongoose.model('DeinModel', {
  // Hier sind deine Modelleigenschaften
});

// Proxy für findOne() Methode
const CustomFindOneProxy = new Proxy(OriginalModel, {
  get: function (target, prop, receiver) {
    if (prop === 'findOne') {
      return function (conditions, callback) {
        // Hier kommt deine benutzerdefinierte Logik für findOne()
        console.log('Benutzerdefinierte findOne() Logik hier');
        // Du kannst auch die Original-Methode aufrufen, wenn nötig
        return target[prop](conditions, callback);
      };
    } else {
      // Für andere Eigenschaften/Methode des Modells
      return Reflect.get(target, prop, receiver);
    }
  },
});






# method #2
const target = {
  message1: "hello",
  message2: "everyone"
};

const handler1 = {};

const proxy1 = new Proxy(target, handler1);

console.log(proxy1.message1); // hello
console.log(proxy1.message2); // everyone
```

<br><br>


# Log every function call
```javascript
class TestClass {
  a() {
    this.aa = 1;
  }
  b() {
    this.bb = 1;
  }
}


const logger = className => {
  return new Proxy(new className(), {
    get: function(target, name, receiver) {
      if (!target.hasOwnProperty(name)) {
        if (typeof target[name] === "function") {
          console.log(
            "Calling Method : ",
            name,
            "|| on : ",
            target.constructor.name
          );
        }
        return new Proxy(target[name], this);
      }
      return Reflect.get(target, name, receiver);
    }
  });
};



const instance = logger(TestClass)

instance.a() // output: "Calling Method : a || on : TestClass"
```
