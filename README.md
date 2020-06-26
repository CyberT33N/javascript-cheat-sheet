# Javascript Cheat Sheet
Javascript Cheat Sheet for the most common stuff..

# DOM Search Sample
```html


<div class="skillbarWRAP">
  <div class="skillbarWRAP-sub">



<div class="skillbarWRAP-sub-search results">
  <h2></h2>
</div>


<div class="skillbarWRAP-sub-search no-results">
  <h2>We can´t find any Skill..</h2>
</div>


<div class="skillbarWRAP-sub-search error">
  <h2></h2>
</div>




<div class="layertwo-os-wrapper">
<h2 class="ui__friendsList__headline" id="ui__friendsList__headline-os">Operating Systems</h2>




<label class="skills-wrapper windows">

              <div class="skillbar-title">
                <div class="layertwo-skills-objectwrap"><object data="img/svg/windows.svg" type="image/svg+xml"></object></div>  <!-- <div class="layertwo-skills-objectwrap">  -->
                <span>Windows</span>
          </div>

              <div class="skillbar clearfix " data-percent="88%">
              	<div class="skillbar-bar"></div>
              	<div class="skill-bar-percent Count">88</div>
              </div> <!-- End Skill Bar -->

  </label> <!--<label class="skills-wrapper">  -->



    <label class="skills-wrapper linux">

              <div class="skillbar-title">
                <div class="layertwo-skills-objectwrap"><object data="img/svg/linux.svg" type="image/svg+xml"></object></div>  <!-- <div class="layertwo-skills-objectwrap">  -->
                <span>Linux</span>
              </div>

              <div class="skillbar clearfix " data-percent="65%">
              	<div class="skillbar-bar"></div>
              	<div class="skill-bar-percent Count">65</div>
              </div> <!-- End Skill Bar -->


    </label> <!--<label class="skills-wrapper">  -->






</div>  <!-- <div class="layertwo-os-wrapper">  -->


</div> <!--  skillbarWRAP-->
</div> <!--  skillbarWRAP-sub-->





```

```javascript



                          	const submitIcon = $(".searchbox-icon");
                          	const inputBox = $(".searchbox-input");
                          	const searchBox = $(".searchbox");
                          	let isOpen = false;
                            let OpenClick = true;






                              function submitIconClick(){
                              console.log( 'submitIconClick() - OpenClick: ' + OpenClick );
                             $( '.skillbarWRAP-sub-search' ).css( 'display', 'none' );

                                                       layertwo_preLoadTooltip_search.hide();
                                                       setTimeout(() => {  layertwo_preLoadTooltip_search.destroy(); }, 1000);




                                                          let searchvalue = $(".searchbox-input").val();
                                                          if ( isOpen && searchvalue ) checkSearchValue( searchvalue );
                                                          if( isOpen && !searchvalue && OpenClick == true ){
                                                              $( '.skillbarWRAP-sub-search.error' ).css( 'display', 'flex' );
                                                              $( '.skillbarWRAP-sub-search.error > h2' ).text( 'Error: Search Value empty' );
                                                              return;
                                                          } //   if( !searchValue ){




                                                      	if (!isOpen) {
                                                    		  	searchBox.addClass("searchbox-open");
                                                    			  inputBox.focus();
                                                    		  	isOpen = true;
                                                    		}  // if (!isOpen) {
                                                        else {

                                                            if( !searchvalue ){
                                                    		              	searchBox.removeClass("searchbox-open");
                                                                        //$(".searchbox-input").val('');
                                                    		              	inputBox.focusout();
                                                    		              	isOpen = false;
                                                                        $( '.ui__friendsList__headline' ).css( 'display', 'block' );
                                                                        $( '.skills-wrapper' ).css( 'display', 'inline-block' );
                                                            } // if( searchvalue ){


                                                    		} // else from if (!isOpen) {


                            } //   function submitIconClick(){









                          	submitIcon.click(function() {
                              OpenClick = true;
                              submitIconClick();
                            }); // submitIcon.click(function() {

                          	submitIcon.mouseup(function() {  return false;  });

                          	searchBox.mouseup(function() {  return false;  });


                          	$(document).mouseup(function() {

                          		if ( isOpen && !$(".searchbox-input").val() ) {
                                //console.log('cc');
                          			$(".searchbox-icon").css("display", "block");
                                OpenClick = false;
                          			submitIconClick();
                          		} // if (isOpen) {

                          	}); // 	$(document).mouseup(function() {



















                      function checkSearchValue(searchValue){
                      console.log( 'checkSearchValue(search) - searchValue: ' + searchValue );
                      $( '.skillbarWRAP-sub-search' ).css( 'display', 'none' );

                                    if( searchValue && searchValue.length > 1 && searchValue.match( /[0-9a-z.]/gmi ) ) filterSkills( searchValue );
                                     else {

                                              if( !searchValue ){
                                                  $( '.skillbarWRAP-sub-search.error' ).css( 'display', 'flex' );
                                                  $( '.skillbarWRAP-sub-search.error > h2' ).text( 'Error: Search Value empty' );
                                              } //   if( !searchValue ){

                                                if( searchValue.length < 2 && searchValue ){
                                                    $( '.skillbarWRAP-sub-search.error' ).css( 'display', 'flex' );
                                                    $( '.skillbarWRAP-sub-search.error > h2' ).text( 'Error: Search Value too short' );
                                                } //   if( !searchValue ){

                                                  if( !searchValue.match( /[0-9a-z.]/gmi ) && searchValue ){
                                                      $( '.skillbarWRAP-sub-search.error' ).css( 'display', 'flex' );
                                                      $( '.skillbarWRAP-sub-search.error > h2' ).text( 'Error: Special Character found' );
                                                  } //   if( !searchValue ){



                                        } //  if( searchValue && searchValue.length > 1 && searchValue.match( /[0-9a-z.]/gmi ) ) filterSkills( searchValue );


                    } // function checkSearchValue(){





                           // dont use input or enter key will reload page.. Use always custom class/id
                          $(".searchbox-input").on("keydown",function search(e) {

                                  if( !$(this).val() ) {
                                          $( '.skillbarWRAP-sub-search' ).css( 'display', 'none' );
                                          $( '.ui__friendsList__headline' ).css( 'display', 'block' );
                                          $( '.skills-wrapper' ).css( 'display', 'inline-block' );
                                  }

                                  if(e.keyCode == 13) { // ENTER KEY
                                     checkSearchValue( $(this).val() );
                                       return false; // prevent page reload on enter
                                  }

                          }); // $(".searchbox-input").on("keydown",function search(e) {










        function filterSkills(searchvalue){
        console.log( 'filterSkills(searchvalue) - searchvalue: ' + searchvalue );




              $( '.ui__friendsList__headline' ).css( 'display', 'none' );
              $( '.skills-wrapper' ).css( 'display', 'inline-block' );
              let checkEmpty = [];

              jQuery('.skills-wrapper').each(function(){

                         let currentElement = jQuery(this).attr('class');
                         //console.log( 'currentElement: ' + currentElement );

                         if( currentElement.match( searchvalue ) ){
                        console.log( 'currentElement is matching the searchvalue! currentElement: ' + currentElement );

                               checkEmpty.push( 'CyberT33n' );

                               $( this ).parent().find( '.ui__friendsList__headline' ).css( 'display', 'block' ); // activate headline of the category
                               $( '.skillbarWRAP-sub-search.results' ).css( 'display', 'flex' );
                               $( '.skillbarWRAP-sub-search.results > h2' ).html( 'Search Results for <strong>' +  searchvalue + '</strong>:' );


                         } // if( currentElement.match( searchvalue ) ){
                        else $( this ).css( 'display', 'none' );


             	}) //  	jQuery('.skillbar').each(function(){
              console.log( 'layertwo - skills each loop done..checkEmpty: ' + checkEmpty );

              if( !checkEmpty[0] ){
                   console.log( 'No results was found at skill search..' );
                   $( '.skillbarWRAP-sub-search.no-results' ).css( 'display', 'flex' );
              } // if( !checkEmpty[0] ){


        } // function filterSkills(searchvalue){


```  

