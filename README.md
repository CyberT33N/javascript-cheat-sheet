# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..

# jQuery

## Event Listener (https://api.jquery.com/category/events/)
```javascript
  $(window).on("resize scroll click touchstart touchend mouseover mouseout",function(e){
  console.log( "Current event class: " + $(e.target).attr('class') );
  console.log( "Current catched event: " + e.type );
  });
```

## Manually trigger event listener
```javascript
$('#element').trigger('touchend');
```

$(this).trigger('touchend');

## jQuery use !important
```javascript
let elem = $(".ui__downloadList__item.purple");
elem[0].style.removeProperty('z-index');
elem[0].style.setProperty('z-index', '1', 'important');
```

## Handle form submits
```javascript
$("#prospects_form").submit(function(e) {
    e.preventDefault(); // prevent page reload on form submit
});
```


## Get scroll direction
```javascript
// method 1 (for me only this worked stable)
var lastScrollTop = 0;
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

## Class Modification
```javascript
if( $(this).hasClass(animClass) ){
    $(this).removeClass(animClass);
}   $(this).addClass(animClassBlack);
```

## Check for Touch Event (Mobile/Tablet)
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

## Wait until scroll is finished
```javascript
$('html').animate({scrollTop: $("layerone").offset().top}, 'slow', function() {
console.log('scroll done..');
});
```


## Import scripts with callback
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

## Get path of element
```javascript
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

```

## each loop
```javascript
$( ".owl-carousel .owl-item" ).each(function() { });
```




## POST JSON to PHP file
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




<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />


# Async

## Create Async
```javascript
// Method 1
(async () => {
 console.log( 'do some async stuff here..' );
})().catch((e) => {
 console.log('Error:' + JSON.stringify( e, null, 4) )
}); //   })().catch((e) => {

// Method 2
async function test(){
 console.log( 'do some async stuff here..' );
}
```


## SetTimeout
```javascript
await new Promise(resolve => setTimeout(resolve, 1000));
```

## SetInterval
```javascript
var countdownInterval = setInterval(async () => {

    count++
    if( count == 10 ) clearInterval( countdownInterval );
                                
}, 1000);
```


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

## Loops - Sequential (For Loop)
```javascript
for (let d of yourArrayHere) {
    await redirectChecker(d);
 }
```


## Loops - Chain Loop
```javascript
var doSomething;
async function one(){
console.log( 'ENTER one()' );

      await new Promise(resolve => setTimeout(resolve, 5000));
      doSomething = 69;
      console.log( 'doSomething: ' + doSomething );

      // in async functions you dont have to resolve anything. When the functions reachs the end it will automatically resolve.      


}

async function two(){
console.log( 'ENTER two()' );

      // if you want you can resolve by yourself with return
      if ( doSomething == 69 ) return true;

}
               
async function three(){
console.log( 'ENTER three()' );

      // Of course you can resolve aswell any strings, arrays, ...
      return 'test'; 

}


            await one();
            console.log( 'FINISH one()' );
            
            let valuetwo = await two();
            console.log( 'FINISH two() - valuetwo: ' + valuetwo );

            let valuethree = await three();
            console.log( 'FINISH three() - valuethree: ' + valuethree );

```



<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />


# Promise

## Nested Functions
```javascript

CheckScrollDirection().then( r => { 
console.log( 'This should come as last message and will contain the value we get from the lowest child function: ' + r );
});


function CheckScrollDirection(){return new Promise(resolve => { 
                scrollafterchangeDOWN().then( r => {  
                      console.log( 'This should come as second message' );
                      resolve(r); 
                 });                      
})};


function scrollafterchangeDOWN(){return new Promise(resolve => { 
                console.log( 'This should come as first message' );
                resolve('direction is down..'); 
})};

```


<br />
<br />



 _____________________________________________________
 _____________________________________________________


<br />
<br />


# Google reCAPTCHA v2

Sandbox keys for localhost testing (will always return true):
- Site key: 6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI
- Secret key: 6LeIxAcTAAAAAGG-vFI1TnRWxMZNFuojJ4WifJWe

<br />
<br />
Alternative you can use **localhost** or **127.0.0.1** and create reCAPTCHA for localhost development

```html
<script src="https://www.google.com/recaptcha/api.js" async defer></script>
<!--  Place visible checkbox on your website  -->
<div class="g-recaptcha" data-sitekey="6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI"></div>
```

## Check if user filled Captcha
```js
// grecaptcha.getResponse() will contain the token which has to be sent to the google recaptcha for verify
if( grecaptcha.getResponse().length == 0 ) {
   alert("Please complete the I'm-not-a-robot widget before submitting your entry.");
   return;
}
```

## Simulate Captcha Fail
```js
//download extension like modheader and then change user agent to
Googlebot/2.1
```

## Reset Captcha
```js
grecaptcha.reset();
```


## Change width
```html
<!-- method 1# data-size="compact" -->
<div class="g-recaptcha" data-size="compact"></div>
```

```css
/* method 2 */
.g-recaptcha{
     transform:scale(0.77);
    transform-origin:0 0;
 }
```




## PHP Backend do verify of captcha
```php

$url = "https://www.google.com/recaptcha/api/siteverify?secret=".$secretKey."&response=".$captcha."&remoteip=".$_SERVER['REMOTE_ADDR'];
$curl = curl_init($url);

  curl_setopt($curl, CURLOPT_HTTPHEADER, array('Accept: application/json'));
  curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
  $json = curl_exec($curl);
  //echo "request data: ".$json."\n\n";

/*
    if(curl_errno($curl)){
        echo 'Curl error: ' . curl_error($curl);
    }
*/




  $json = json_decode($json);




  if(!empty($json)) {
  //echo $json['success'];
  
    $success = $json->success;
  //echo "success: ".$success."\n\n";




             if( $success == 1 ){
                  echo true;
             } else{
                  echo false;
             }


  } else {
      echo "json empty";
  }


  curl_close($curl);
  exit;
```

<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />



# Anime.js

## Remove Animation
```javascript
anime.remove( document.querySelector('#layertwo') )
```

## Bouncing easing
```javascript
{duration: 2000, easing: 'easeOutElastic(1, .2)'} // <-- change .2 to higher value for slower bounce effect
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

# document

## remove text from url
```javascript
// http://localhost/myresume/#image1
document.location.hash = ""
// http://localhost/myresume/#
```


<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />





# Copy any text to clipboard
```javascript
  function textToClipboard(text) {
      var dummy = document.createElement("textarea");
      document.body.appendChild(dummy);
      dummy.value = text;
      dummy.select();
      document.execCommand("copy");
      document.body.removeChild(dummy);
  }
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


<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# Check if tablet/smartphone
```javascript

function mobileAndTabletCheck(){
  let check = false;
  (function(a){if(/(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|iris|kindle|lge |maemo|midp|mmp|mobile.+firefox|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows ce|xda|xiino|android|ipad|playbook|silk/i.test(a)||/1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(a.substr(0,4))) check = true;})(navigator.userAgent||navigator.vendor||window.opera);
  return check;
}
const mobileCheck = mobileAndTabletCheck();
console.log( 'mobile/tablet check:' + mobileCheck );


```  


<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# Tutorials

## Immediately Invoked Function Expression (IIFE)
- https://www.youtube.com/watch?v=eY7u388cvM4

## Spread Operators
- https://www.youtube.com/watch?v=I5AGSH8ROSU
