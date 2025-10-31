# Log

# console.log()

<br><br>

## Use CSS
```javascript
// ---- EXAMPLE #1 ----
console.log('%cHello..', 'font-weight: bold; color: red')

// ---- EXAMPLE #2 ----
console.log('%cHello..%cNew Color here..', 'font-weight: bold; color: red', 'font-weight: bold; color: green')
```


<br><br>

# console.time()
- https://developer.mozilla.org/en-US/docs/Web/API/Console/time

```javascript
console.time("Timer")
for (let i = 0; i < 100000000; i++){
  // ..
}
console.timeEnd("Timer")
```


<br><br>

# console.error()
- https://www.w3schools.com/jsref/met_console_error.asp

```javascript
console.error("You made a mistake");
```

<br><br>

# console.warn()
- https://developer.mozilla.org/de/docs/Web/API/Console/warn

```javascript
console.warn("You made a mistake");
```



<br><br>

# console.assert()
- https://developer.mozilla.org/en-US/docs/Web/API/console/assert

```javascript
let x = 3
console.assert(x === 2, 'x is not 2..')
```


<br><br>

# console.table()
- https://developer.mozilla.org/de/docs/Web/API/Console/table

```javascript
// ---- EXAMPLE #1 - Array ----
console.table(["apples", "oranges", "bananas"]);


// ---- EXAMPLE #2 - Object ----
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

var me = new Person("John", "Smith");
console.table(me);
```



<br><br>

# console.trace()
- https://developer.mozilla.org/en-US/docs/Web/API/Console/trace
- The console interface's trace() method outputs a stack trace to the Web Console.

```javascript
function foo() {
  function bar() {
    console.trace();
  }
  bar();
}

foo();
```


	
	
	
	
	
	
<br><br>

# Log every method call
- https://github.com/aigoncharov/class-logger#installation
	
```javascript
	import { LogClass, Log } from 'class-logger'

@LogClass()
class Test {
  @Log()
  method1() {
    return 123
  }

  @Log()
  async methodAsync1() {
    // do something asynchronous
    return Symbol()
  }

  @Log()
  methodError() {
    throw new Error()
  }

  @Log()
  property1 = () => null

  @Log()
  static methodStatic1(arg1) {
    return {
      prop1: 'test',
    }
  }
}

// Logs to the console before the method call:
// 'Test.methodStatic1. Args: [42].'
Test.methodStatic1(42)
// Logs to the console after the method call:
// 'Test.methodStatic1 -> done. Args: [42]. Res: {"prop1":"test"}.'

// Logs to the console before the class' construction:
// 'Test.construct. Args: [].'
const test = new Test()

// Logs to the console before the method call:
// 'Test.method1. Args: [].'
test.method1()
// Logs to the console after the method call:
// 'Test.method1 -> done. Args: []. Res: 123.'

// Logs to the console before the method call:
// 'Test.methodAsync1. Args: [].'
test.methodAsync1()
// Logs to the console after the method call (after the promise is resolved):
// 'Test.methodAsync1 -> done. Args: []. Res: Symbol().'

// Logs to the console before the method call:
// 'Test.methodError. Args: [].'
test.methodError()
// Logs to the console after the method call:
// 'Test.methodError -> error. Args: []. Res: Error {"name":"Error","message":"","stack":"some stack trace"}.'

// Logs to the console before the method call:
// 'Test.property1. Args: [].'
test.property1()
// Logs to the console after the method call:
// 'Test.property1 -> done. Args: []. Res: null.'
```
