# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..

# jQuery

## Class Modification
```javascript
if($(this).hasClass(animClass)){
   $(this).removeClass(animClass);
} $(this).addClass(animClassBlack);
```

<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />


# Async

## Loops - In Parallel
```javascript
  await Promise.all(
      yourArrayHere.map(async d => {
      log( 'Current array item we process: ' + d );

          let currenturl = await redirectChecker(d);
          log( 'Final url after redirect: ' + currenturl );

          tmpARtwo.push(currenturl);
      }) 
    );
```

## Loops - Sequential
```javascript
for (let d of yourArrayHere) {
    await redirectChecker(d);
 }
```


<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# Simulate Click
```javascript
document.querySelector('.ui__downloadList__item.purple').click();
```

# Simulate Hover
```javascript
var element = document.querySelector('.ui__downloadList__item.purple');

var event = new MouseEvent('mouseover', {
  'view': window,
  'bubbles': true,
  'cancelable': true
});

element.dispatchEvent(event);
```


<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# jQuery use !important with .css()
```javascript
let elem = $(".ui__downloadList__item.purple");
elem[0].style.removeProperty('z-index');
elem[0].style.setProperty('z-index', '1', 'important');
```


<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# Prevent redirect on input search with Enter
```javascript
                           // dont use input as selector or enter key will reload page.. Use always custom class/id
                          $(".searchbox-input").on("keydown",function search(e) {

                                  if( !$(this).val() ) {
                                          $( '.skillbarWRAP-sub-search' ).css( 'display', 'none' );
                                          $( '.ui__friendsList__headline' ).css( 'display', 'block' );
                                          $( '.skills-wrapper' ).css( 'display', 'flex' );
                                  }

                                  if(e.keyCode == 13) { // ENTER KEY
                                     checkSearchValue( $(this).val() );
                                       return false; // prevent page reload on enter
                                  }

                          });

```  

