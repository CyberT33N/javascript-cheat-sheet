# Regex

# .replace() with regex
https://codeburst.io/javascript-the-conditional-ternary-operator-explained-cac7218beeff

	
```javascript
// method #1
var url = 'lolfoo';
url = url.replace( /foo/g, "");
console.log(url);

// method #2
var url = 'lolfoo';
url = url.replace( new RegExp("foo","g"), "");
console.log(url);
```


<br><br>

# Capturing groups
```javascript
let re = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/u;
let result = re.exec('2015-01-02');
// result.groups.year === '2015';
// result.groups.month === '01';
// result.groups.day === '02';
```
	
	
	
# Create regex with variable
```javascript
const testVar = 123
const regex = new RegExp(`ReGeX${testVar}ReGeX`);
console.log(regex)
```


<br><br>
	

# matching
```javascript
# Method #1
if (!/^test-\d+$/.test(dbName)) {
	console.warn(`Invalid project ID for migrations: ${dbName}. We will skip the migration`)
	return
}

# Method #2
const data = 'width: 480px; transform: translate3d(0px, 0px, -100px) rotateX(0deg) rotateY(3.75deg) scale(1); z-index: 1; margin-top: 0px; transition-duration: 0ms;'

let regexpNames =  /rotateY\((.*?)\)/mg;
let result = regexpNames.exec(data);

console.log(result[1]) // rotateY(3.75deg)
```
