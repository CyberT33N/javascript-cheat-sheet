# Simulate

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
