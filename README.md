# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..

# Input ENTER Key
```javascript
/* Method #1 */
                      $("input").on("keydown",function search(e) {
                              $( '.skillbarWRAP-sub-search' ).css( 'display', 'none' );

                                  if(e.keyCode == 13) { // ENTER KEY

                                     let searchValue = $(this).val();
                                     console.log( 'ENTER KEY - searchValue: ' + searchValue );
                                     if( searchValue && searchValue.length > 1 && searchValue.match( /[0-9a-z.]/gmi ) ) filterSkills( searchValue );
                                      else {

                                            if( !searchValue ){
                                                $( '.skillbarWRAP-sub-search.error' ).css( 'display', 'flex' );
                                                $( '.skillbarWRAP-sub-search.error > h2' ).text( 'Error: Search Value empty' );
                                            } //   if( !searchValue ){

                                              if( searchValue.length < 2 && searchValue ){
                                                  $( '.skillbarWRAP-sub-search.error' ).css( 'display', 'flex' );
                                                  $( '.skillbarWRAP-sub-search.error > h2' ).text( 'Error: too short Search Value' );
                                              } //   if( !searchValue ){

                                                if( !searchValue.match( /[0-9a-z.]/gmi ) && searchValue ){
                                                    $( '.skillbarWRAP-sub-search.error' ).css( 'display', 'flex' );
                                                    $( '.skillbarWRAP-sub-search.error > h2' ).text( 'Error: Special Character found' );
                                                } //   if( !searchValue ){

                                      } // else from //  if( $(this).val() ){

                                  return false; // prevent page reload on enter
                                  } // if(e.keyCode == 13) { // ENTER KEY

                              }); //$("input").on("keydown",function search(e) {


```  

