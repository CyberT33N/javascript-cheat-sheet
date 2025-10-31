# Wait

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
