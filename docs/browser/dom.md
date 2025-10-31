# DOM

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
P (target phase, triggers two times, as we've set two listeners: capturing and bubbling)
DIV → FORM → BODY → HTML (bubbling phase, the second listener).
There's a property event.eventPhase that tells us the number of the phase on which the event was caught. But it's rarely used, because we usually know it in the handler.
-->
```

<br><br>

## Event Bubbling
- The process is called "bubbling", because events "bubble" from the inner element up through parents like a bubble in the water. Normally it goes upwards till <html>, and then to document object, and some events even reach window, calling all handlers on the path.
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
- event.target – is the "target" element that initiated the event, it doesn't change through the bubbling process.
- this – is the "current" element, the one that has a currently running handler on it.
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
// body.onclick doesn't work if you click on <button>
<body onclick="alert(`the bubbling doesn't reach here`)">
  <button onclick="event.stopPropagation()">Click me</button>
</body>
```

<br><br>

#### Stop all other handler execution on the same element (.stopImmediatePropagation())
- To stop the bubbling and prevent handlers on the current element from running, there's a method event.stopImmediatePropagation(). After it no other handlers execute.
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
