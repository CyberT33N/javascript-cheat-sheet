# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..

# Input ENTER Key
```javascript
/* Method #1 */
                               $("input").on("keydown",function search(e) {

                                  if(e.keyCode == 13) { // ENTER KEY

                                     let searchValue = $(this).val();
                                     console.log( 'ENTER KEY - searchValue: ' + searchValue );
                                     if( searchValue ) filterSkills( searchValue );
                                      else {
                                          $( '.skillbarWRAP-sub-search-error' ).css( 'display', 'flex' );
                                          $( '.skillbarWRAP-sub-search-error > h2' ).text( 'Error: Search Value empty' );
                                      } // else from //  if( $(this).val() ){

                                  return false; // prevent page reload on enter
                                  } // if(e.keyCode == 13) { // ENTER KEY

                              }); //$("input").on("keydown",function search(e) {
```  

