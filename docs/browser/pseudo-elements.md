# :before & :after

# Add new style to :before and :after
```javascript
// method #1
  let styleElem = document.head.appendChild(document.createElement("style"));
      styleElem.innerHTML = ".bar:before {background-color: #fff;}";

      styleElem = document.head.appendChild(document.createElement("style"));
      styleElem.innerHTML = ".bar:after {background-color: #fff;}";
      
// method #1
var style = document.querySelector('.foo').style;
style.setProperty('--background', 'url(http://placekitten.com/200/300)');
/*
.foo::before {
  background: var(--background);
  content: '';
  display: block;
  width: 200px;
  height: 300px;
}
*/
```
