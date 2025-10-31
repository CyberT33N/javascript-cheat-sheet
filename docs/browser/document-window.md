# document/window

# remove text from url
```javascript
// http://localhost/myresume/#image1
document.location.hash = ""
// http://localhost/myresume/#
```


<br>
<br>

# Open something new window

```javascript
window.open('img/upwork/jobs/job1.jpg', '_blank', 'location=yes,height=$(window).height(),width=$(window).width(),scrollbars=yes,status=yes');
```

<br>
<br>


# Get link params from oauth popup window
```javascript
// https://gist.github.com/CyberT33N/b6077d75d25e1d728d68caeac6914dd4
// https://www.npmjs.com/package/oauth-open
oauthOpen('http://localhost:1337/oauth-dialog.html', async (err, code) => {
   console.log( 'code: ' + JSON.stringify(code, null, 4) );
});
```

```html
<html>
  <body>

    <div>Authorize OAuth Test App?</div>

    <form action="/code" method="POST">
      <button type="submit">OK</button>
    </form>

  </body>
</html>

```


	
	
<br><br>

# localStorage (https://www.w3schools.com/jsref/prop_win_localstorage.asp)

```javascript
/* ---- EXAMPLE #1 ----*/

// Store
localStorage.setItem("lastname", "Smith");
// Retrieve
document.getElementById("result").innerHTML = localStorage.getItem("lastname");



/* ---- EXAMPLE #2 ----*/
if (localStorage.clickcount) {
  localStorage.clickcount = Number(localStorage.clickcount) + 1;
} else {
  localStorage.clickcount = 1;
}
document.getElementById("result").innerHTML = "You have clicked the button " +
localStorage.clickcount + " time(s).";
```



	
<br><br>

# Extend/Add url without reload page
- https://developer.mozilla.org/en-US/docs/Web/API/History_API/Working_with_the_History_API

```javascript
// Change url by adding /search?q
window.history.pushState('search', 'search', `/search?q=${searchValue}`);
```
	
	
	
<br><br>

# Get url query paramater
```javascript
const urlParams = new URLSearchParams(window.location.search);
const myParam = urlParams.get('paramNameHere');
```
