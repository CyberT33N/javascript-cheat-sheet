# jQuery

# load (https://api.jquery.com/load/)

## Insert all contents of another same origin HTML file to current page
```javascript
$( "#a" ).load( "article.html" );
```

## Insert specific element of another same origin HTML file to current page
```javascript
$( "#a" ).load( "article.html #example" );
```

<br><br>

# Check for click
```javascript
// method #1
$(".some_class").on("click", function(e) {
  console.log("Event: ", e);
  console.log("Current Target of Event: ", e.currentTarget);
  console.log("this: ", this);
  console.log("$(this): ", $(this));
})

// method #2
$("#clicker").click(function () { /*..*/ });
```

# Check browser (https://api.jquery.com/jQuery.browser/)
```javascript
// method 1
if ($.browser.mozilla) { ... }

//method 2
const isFirefoxBrowser = navigator.userAgent.includes('Firefox');
```

	
	
	
	
	
	
<br><br>

# Check for click to a JQuery object not yet added to the DOM
- Use the parent which will always exist to register the click event
```javascript
// Method #1
$(document).on('click', '#yourid', function() { /*..*/ });
	
// Method #2
$('body').on('click', '#yourid', function() { /*..*/ });
```

	
	
	
	
	
	
	
	

<br><br><br><br>

# Event Listener (https://api.jquery.com/category/events/)
```javascript
// method 1 without css selector
  $(window).on("resize scroll click touchstart touchend mouseover mouseout focus focusout",function(e){
  console.log( "Current event class: " + $(e.target).attr('class') );
  console.log( "Current catched event: " + e.type );
  });

// method 2 with css selector
$(document).on("click touchstart touchend", ".owl-dot", function (e) {  });

// method 3
$('input').on('focusout',function(){ //.. });
```

## Manually trigger event listener
```javascript
$('#element').trigger('touchend');
```

<br><br>

# jQuery use !important
```javascript
let elem = $(".ui__downloadList__item.purple");
elem[0].style.removeProperty('z-index');
elem[0].style.setProperty('z-index', '1', 'important');
```

# Handle form submits
```javascript
$("#prospects_form").submit(function(e) {
    e.preventDefault(); // prevent page reload on form submit
});
```


# Get scroll direction
```javascript
// method 1 (for me only this worked stable)
var lastScrollTop = 0;

// Or use body as css selector
$(window).scroll(function(event){
   var st = $(window).scrollTop();
   if (st > lastScrollTop){
       // downscroll code
   } else {
      // upscroll code
   }
   lastScrollTop = $(window).scrollTop();
});

//method 2
var lastScrollTop = 0;
$(window).scroll(function(event){
   var st = $(this).scrollTop();
   if (st > lastScrollTop){
       // downscroll code
   } else {
      // upscroll code
   }
   lastScrollTop = st;
});
```

# Class Modification
```javascript
if( $(this).hasClass(animClass) ){
    $(this).removeClass(animClass);
}   $(this).addClass(animClassBlack);
```

# Check for Touch Event (Mobile/Tablet)
```javascript

$(document).on('touchstart touchend', '.skillbarWRAP', function(e) {

/*
var xPos = e.originalEvent.touches[0].pageX;
console.log( 'xPos: ' + xPos );
*/

      if( e.type == 'touchstart' ) console.log( 'TOUCH START - .skillbarWRAP' );  
      else console.log( 'TOUCH END - .skillbarWRAP' );
      
      
});

```

	
<br><br>	
	
# Wait until scroll is finished
```javascript
$('html').animate({scrollTop: $("layerone").offset().top}, 'slow', function() {
console.log('scroll done..');
});
```
	
<br><br>	


# Scroll to bottom
```html
html {
  scroll-behavior: smooth;
}
```
	
```javascript
// Scroll to a certain element
document.querySelector('.hello').scrollIntoView({ 
  behavior: 'smooth' 
});
```
	
<br><br>
	
# Scroll to specific element
```javascript
// method #1
$("a[href='#bottom']").click(function() {
  $("html, body").animate({ scrollTop: $(document).height() }, "slow");
  return false;
});

// method #2
document.querySelector(".chat").scrollTop = document.querySelector(".chat").scrollHeight;
```

<br><br>

# Import scripts with callback
```javascript

     $.when(
         $.getScript( "js/headerbig.js" ),
         $.getScript( "js/menubar.js" ),
         $.Deferred(function( deferred ){
             $( deferred.resolve );
         })
     ).done(function(){
         console.log('Scripts Load was performed.');
    });
```

# Get path of element (css selector)
```javascript
// Method #1
jQuery.fn.getSelector = function() {

    if ($(this).attr('id')) {
        return '#' + $(this).attr('id');
    }

    if ($(this).prop("tagName").toLowerCase() == 'body')    return 'body';

    var myOwn = $(this).attr('class');
    if (!myOwn) {
        myOwn = '>' + $(this).prop("tagName");
    } else {
        myOwn = '.' + myOwn.split(' ').join('.');
    }

    return $(this).parent().getSelector() + ' ' + myOwn;
}
console.log( 'path: ' + $(".owl-carousel .owl-item").getSelector() );
	
	
	
// Method #2
	function getSelector(el)
        {
            var $el = jQuery(el);

            var selector = $el.parents(":not(html,body)")
                .map(function() {
                    var i = jQuery(this).index();
                    i_str = '';

                    if (typeof i != 'undefined')
                    {
                        i = i + 1;
                        i_str += ":nth-child(" + i + ")";
                    }

                    return this.tagName + i_str;
                })
                .get().reverse().join(" ");

            if (selector) {
                selector += " "+ $el[0].nodeName;
            }

            var index = $el.index();
            if (typeof index != 'undefined')  {
                index = index + 1;
                selector += ":nth-child(" + index + ")";
            }

            return selector;
        }
	

console.log( 'path: ' + getSelector($(".owl-carousel .owl-item")) );

	
	
	
	
	
// If you want to get the nth child use $(this).index()
$(elImageCSS).hover(function(){
	const selector = `${elImageCSS}:nth-child(${$(this).index()})`
	console.log(selector)
}, function(){
	const selector = `${elImageCSS}:nth-child(${$(this).index()})`
	console.log(selector)
})
```

<br><br>
	
# each loop
```javascript
$( ".owl-carousel .owl-item" ).each(function() { });
```




# POST JSON to PHP file
```javascript
let json = {
    email: emailInput,
    subject: subjectInput,
    message: messageInput,
    token: grecaptcha.getResponse()
};

$.post("php/contact.php", json, function(r) {
console.log('result after form submit:' + r);
    if(r == 1) {
        alert('Thanks for posting comment.')
    } else {
        alert('error..')
    }
});
```




# clone
```javascript
  // you can clone a element and then you got the element duplicated in DOM. If needed you can delete the first one after..
  $('#menubar-contact').clone(true).insertAfter($('#menubar-contact'));
  // $('#menubar-contact').remove();
```





# Get parent
```javascript
// vanilla javascript 
document.querySelector('.mdi-link-variant')?.parentNode?.getAttribute('href');

//jquery
$( '.element' ).parent();
```


# Get next
```javascript
// vanilla javascript 
document.getElementById("item1").nextElementSibling

//jquery
$( '.element' ).next();
```

# Append HTML to current element
```javascript
$('.right .top').append`<div class="chat" data-chat="${currentPerson}"></div>`);
```


# Insert HTML after specific element
```javascript
$('.right .top').after(`<div class="chat" data-chat="${currentPerson}"></div>`);
```

<br><br>

# Find element
```javascript
// vanilla javascript 
document.querySelector('.zp_7I-lw')?.querySelectorAll('.zp_3_fnL')[0]?.getAttribute('href')

//jquery
$( '.element' ).find( '.test' );
```


<br><br>

# Draggable
- https://code.jquery.com/ui/
```javascript
<script src="js/jquery.min.js"> </script>
<script src="js/jquery-ui.min.js"> </script>
```

<br><br>

## Exclude element
```html
$(".cardWrap").draggable({ handle: '.cardDescription', cancel: '.cloudimage-360' });
```

	
	
	
<br><br><br><br>

## Get input value for each key stroke
```html
$('#dSuggest').on("input", function() {
    var dInput = this.value;
    console.log(dInput);
    $(".dDimension:contains('" + dInput + "')").css("display","block");
});
```

		
<br><br>

## Get input value after submit
```javascript						  
$('input').on('keydown', function(e) {
	if (e.keyCode === 13) {
	    alert($(this).val())
	}
})
```

	
	
			
<br><br>

## Check if element is in viewport
```javascript
$.fn.isInViewport = function() {
	var elementTop = $(this).offset().top;
	var elementBottom = elementTop + $(this).outerHeight();
	var viewportTop = $(window).scrollTop();
	var viewportBottom = viewportTop + $(window).height();
	return elementBottom > viewportTop && elementTop < viewportBottom;
};
							  
$('.swiper').isInViewport() // returns true or false
```
