# Scope

# You can not access variables which are defined within a function
```javascript
(function(){
  var a = 3;
})();

console.log(a);



// to access a you must define it outside of the function
let a;
(function(){
  a = 3;
})();

console.log(a);




// create global variable inside of function without declare it before
(function(){
  var a = b = 3;
})();

console.log(a);
console.log(b); // 3
```







<br><br>




# Child Objects share this of parent Object
```javascript
var myObject = {
    foo: "bar",
    func: function() {
        var self = this;
        console.log("outer func:  this.foo = " + this.foo); // bar
        console.log("outer func:  self.foo = " + self.foo); // bar

        (function() {
            console.log("inner func:  this.foo = " + this.foo); // undefined because of new function
            console.log("inner func:  self.foo = " + self.foo); // bar
        }());
    }
};
myObject.func();
```
