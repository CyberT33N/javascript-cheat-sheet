# Math

# Generate random number between two numbers
```javascript
// generate random number between 1-50
Math.round(Math.random() * 50 + 1);
	
// generate random number between 0-4
Math.floor(Math.random() * (4 + 1))
```

<br><br>

# parseFloat() (https://www.w3schools.com/jsref/jsref_parsefloat.asp)
- The parseFloat() function parses a string and returns a floating point number. This function determines if the first character in the specified string is a number. If it is, it parses the string until it reaches the end of the number, and returns the number as a number, not as a string.
```javascript
var a = parseFloat("10") // 10
var b = parseFloat("10.00") // 10
var c = parseFloat("10.33") // 10.33
var d = parseFloat("34 45 66") // 34
var e = parseFloat(" 60 ") // 60
var f = parseFloat("40 years") // 40
var g = parseFloat("He was 40") // NaN
```



<br><br>

# parseInt() (https://www.w3schools.com/jsref/jsref_parseint.asp)
- The parseInt() function parses a string and returns an integer.The radix parameter is used to specify which numeral system to be used, for example, a radix of 16 (hexadecimal) indicates that the number in the string should be parsed from a hexadecimal number to a decimal number.
```javascript
var b = parseInt("10.00") // 10
var c = parseInt("10.33") // 10
var d = parseInt("34 45 66") // 34
var e = parseInt(" 60 ") // 60
var f = parseInt("40 years") // 40

var h = parseInt("10", 10) // 10
var i = parseInt("010") // 10
var j = parseInt("10", 8) // 8
var k = parseInt("0x10") // 16
var l = parseInt("10", 16) // 16
```



<br><br>



# Are two numbers really equal
- An educated answer to this question would simply be: "You can't be sure. it might print out 0.3 and true, or it might not. Numbers in JavaScript are all treated with floating point precision, and as such, may not always yield the expected results."

<br><br>

The example provided above is classic case that demonstrates this issue. Surprisingly, it will print out:
```javascript
console.log(0.1 + 0.2); // 0.30000000000000004
console.log(0.1 + 0.2 == 0.3); // false



// how to compare if numbers are really equal
function areTheNumbersAlmostEqual(num1, num2) {
	return Math.abs( num1 - num2 ) < Number.EPSILON;
}
console.log(areTheNumbersAlmostEqual(0.1 + 0.2, 0.3));
```
