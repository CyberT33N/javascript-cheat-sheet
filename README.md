# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..

# Input ENTER Key
```javascript
/* Method #1 */
 $("input").on("keydown",function search(e) {

       if(e.keyCode == 13) { // ENTER KEY

          if( $(this).val() ){
             console.log( 'filterSkills(searchvalue) ENTER KEY - $(this).val(): ' + $(this).val() );
             filterSkills( $(this).val() );
          }
          else $( '.skillbarWRAP-sub-search-results' ).css( 'display', 'flex' );

       return false; // prevent page reload on enter
       } 

});
```  

