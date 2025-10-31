# Operators
- https://www.w3schools.com/js/js_operators.asp

# Conditional Operators


<br><br>

## Ternary Operator 
- https://www.w3schools.com/js/tryit.asp?filename=tryjs_comparison

```javascript
// if under 18 voteable will be "Too young"
// if over 18 votable will be "Old enough"
voteable = (age < 18) ? "Too young":"Old enough";

// alternative you can write it like this
voteable = age < 18 ? "Too young":"Old enough";
```




<br><br>

# Spread Operator

## Guides
- https://www.youtube.com/watch?v=I5AGSH8ROSU
- https://dev.to/livecodestream/how-to-use-the-spread-operator-in-javascript-35bn
- https://medium.com/javascript-in-plain-english/how-to-deep-copy-objects-and-arrays-in-javascript-7c911359b089

<br><br>

## convert array to paramater
```javascript
let ar = [1,2]

function test(a, b) {
  console.log('a:' + a);
  console.log('b:' + b);
}

test(...ar);
```



<br><br>

## Object destructuring
```javascript
let obj1 = {a: true};
let obj2 = {b: true};

function test({a = false, b = false}){
  console.log(a);
  console.log(b);
};

test({...obj1, ...obj2});
```
	
<br><br>
	
#### Object Destructuring without let, const, var
```javascript
const objectReturningFunction = () => {
    return {a:true, b:false}
}

let a, b
;({a, b} = objectReturningFunction())

console.log(b)
	
	
	
// Example #2
let { hasChanged } = await getModel(modelName)
;({ hasChanged } = await getModel(modelName2))
```


<br><br>
	
### Remove property from object
```
// Remove placements property from obj
const { placements, ...newObj } = obj
```
	
	
	
	
	
	
	
	
	
	
	

<br><br><br><br>

## Conditions
```javascript
{
  apple: true,
  ...(cfg.path && typeof cfg.path === 'object' ? cfg.path : {})
}
```


<br><br>







# Logical Operator

## Guides
- https://www.javascripttutorial.net/javascript-logical-operators/

<br><br>

## Nullish Coalescing Operator (??)

- Syntax:
```javascript
leftExpression ?? rightExpression
```

- Example:
```javascript
/* ---- EXAMPLE #1 ---- */

// result will be 1 and is not what we want..
let count = 0;
let result = count || 1;
console.log(result); // 1

// The nullish coalescing operator helps you to avoid this pitfall. It only returns the second operand when the first one evaluates to either null or undefined.
let count = 0;
let result = count ?? 1;
console.log(result); // 0





/* ---- EXAMPLE #2 ---- */
const result = null || undefined ?? 'OK'; // SyntaxError

const result = (null || undefined) ?? 'OK'; 
console.log(result); // 'OK'
```



<br><br>

## AND Assignment (&&=)
- If the first value is true, the second value is assigned.
```javascript
let x = 10;
x &&= 5;
```



<br><br>

## OR Assignment (||=)
- If the first value is false, the second value is assigned.
```javascript
let x = 10;
x ||= 5;
```



<br><br>

## Nullish Coalescing Assignment (??=)
- If the first value is undefined or null, the second value is assigned.
```javascript
let x;
x ??= 5;
```




## Logical OR
- It is important to know that javascript will execute all stuff that is listed with those logical OR operators when something has a higher priority. This means that when you pass a Ternary Operator then it will get executed even when the first case is true because it has higher priority. You can use brackets to prevent this.

- Example:
```javascript
const res = name || lastname

// Use brackets to prevent execution of the Ternary Operator part
const res = name || (lastname || (name.startsWith('Lisa') ? await checkName() : 0))
```







<br><br>

## Condition at variable decleration
```javascript
const a = 1;
const b = 2;
const example = a > b
console.log(example); // false
```


















<br><br>

# in Operator (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Operators/in)
- The in operator returns true if the specified property is in the specified object or its prototype chain.

```javascript
/* ---- EXAMPLE #1 ----*/
const car = { make: 'Honda', model: 'Accord', year: 1998 };

if('make' in car) console.log(true);
else console.log(false);







/* ---- EXAMPLE #2 ----*/
const car = { make: 'Honda', model: 'Accord', year: 1998 };

console.log('make' in car);
// expected output: true

delete car.make;
if ('make' in car === false) {
  car.make = 'Suzuki';
}

console.log(car.make);
// expected output: "Suzuki"
```











<br><br>

# typeof Operator (https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Operators/typeof)
- The typeof operator returns a string indicating the type of the unevaluated operand.

```javascript
var test = 'aaa'
if(typeof test === 'string') console.log(true)
```












<br><br>

# Pipeline Operator
Der JavaScript-Operator `|>` ist der **Pipeline-Operator**, der in der Entwicklung ist (Stand: ES2024). Er macht Code sauberer, indem er Ausdrücke schrittweise verarbeitet, ähnlich wie in einer Pipeline.  

### So funktioniert er:  
Er nimmt das Ergebnis eines Ausdrucks und gibt es als Argument an die nächste Funktion weiter.  

### Beispiel:  
Ohne Pipeline-Operator:  
```javascript
const result = double(square(increment(2)));
console.log(result); // 18
```

Mit Pipeline-Operator:  
```javascript
const result = 2 |> increment |> square |> double;
console.log(result); // 18
```

### Erklärt:
1. `2` wird an `increment` übergeben.  
2. Das Ergebnis wird an `square` übergeben.  
3. Das Ergebnis wird an `double` übergeben.  

### Vorteil:
- **Bessere Lesbarkeit:** Es liest sich von links nach rechts, wie man denkt.  
- **Weniger Klammern:** Kein Verschachteln von Funktionsaufrufen nötig.  

Noch experimentell, aber ein potenzieller Game-Changer! 😊






















<br><br>
<br><br>

# Comparison Operators
- https://www.w3schools.com/js/js_comparisons.asp
- Comparison operators are used for controlling the flow of your program. They allow you to compare two values and determine whether certain conditions are met.

<br><br>

## equal to ( == )
- Compares two values for equality, but without considering the types.
```javascript
5 == '5';  // true
```

<br><br>

## equal value and equal type ( === )
- This is the preferred way of comparing values because it checks both the value and the type.
```javascript
5 === '5';  // false
5 === 5;    // true
```


<br><br>

## not equal ( != )
```javascript
x != 8 	// true
```

<br><br>

## not equal value or not equal type ( !== )
```javascript
x !== 5 	/false
```


<br><br>

## greater than ( > )
```javascript
x > 8 	// false
```

<br><br>

## less than ( < )
```javascript
x < 8 	// false
```

<br><br>

## greater than or equal to ( >= )
```javascript
x >= 8 	// false
```

<br><br>

## less than or equal to ( <= )
```javascript
x <= 8 	// false
```

















<br><br>
<br><br>

# Arithmetic Operators
- https://www.w3schools.com/js/js_arithmetic.asp
- Arithmetic operators perform arithmetic on numbers (literals or variables).

<br><br>

## Exponentiation operator ( ** )
- The exponentiation operator (**) raises the first operand to the power of the second operand.
  - x ** 2 bedeutet: 5 hoch 2.
  -Das entspricht 5×5, was 25 ergibt.
```javascript
let x = 5;
let z = x ** 2; // 25
```


<br><br>

## Modulus operator ( ++ )
- The modulus operator (%) returns the division remainder.
```javascript
let x = 5;
let y = 2;
let z = x % y;
console.log(z) // 1
```

<br><br>

## Increment operator ( ++ )
- The increment operator (++) increments numbers.
```javascript
let x = 5;
x++; // 
console.log(x) // 6
```

<br><br>

## Decrement operator ( -- )
- The decrement operator (--) decrements numbers.
```javascript
let x = 5;
x--; // 
console.log(x) // 4
```












<br><br>
<br><br>




# 10. Bitwise Operators

<br><br>

## 10.1 AND Operator (`&`)

Der `&`-Operator vergleicht die Bits beider Operanden und gibt `1` zurück, wenn beide Bits `1` sind. Andernfalls wird `0` zurückgegeben.

```javascript
let a = 5;  // 0101
let b = 3;  // 0011
let result = a & b;  // 0001 (1)
console.log(result);  // Ausgabe: 1
```

## 10.2 OR Operator (`|`)

Der `|`-Operator vergleicht die Bits beider Operanden und gibt `1` zurück, wenn eines der beiden Bits `1` ist.

```javascript
let a = 5;  // 0101
let b = 3;  // 0011
let result = a | b;  // 0111 (7)
console.log(result);  // Ausgabe: 7
```

## 10.3 XOR Operator (`^`)

Der `^`-Operator vergleicht die Bits beider Operanden und gibt `1` zurück, wenn die Bits unterschiedlich sind, andernfalls `0`.

```javascript
let a = 5;  // 0101
let b = 3;  // 0011
let result = a ^ b;  // 0110 (6)
console.log(result);  // Ausgabe: 6
```

## 10.4 NOT Operator (`~`)

Der `~`-Operator kehrt alle Bits des Operanden um (invertiert die Bits). Er entspricht der negativen Zahl des Operanden minus eins.

```javascript
let a = 5;  // 0101
let result = ~a;  // 1010 (negiert 5)
console.log(result);  // Ausgabe: -6
```

## 10.5 Left Shift Operator (`<<`)

Der `<<`-Operator verschiebt die Bits eines Operanden um eine bestimmte Anzahl nach links. Dabei werden rechts Nullen eingefügt.

```javascript
let a = 5;  // 0101
let result = a << 1;  // 1010 (10)
console.log(result);  // Ausgabe: 10
```

## 10.6 Right Shift Operator (`>>`)

Der `>>`-Operator verschiebt die Bits eines Operanden um eine bestimmte Anzahl nach rechts. Das Vorzeichenbit wird beibehalten, was bedeutet, dass für negative Zahlen `1` eingefügt wird.

```javascript
let a = 5;  // 0101
let result = a >> 1;  // 0010 (2)
console.log(result);  // Ausgabe: 2
```

## 10.7 Unsigned Right Shift Operator (`>>>`)

Der `>>>`-Operator verschiebt die Bits eines Operanden um eine bestimmte Anzahl nach rechts und fügt immer `0` an der linken Seite ein, unabhängig vom Vorzeichen des Operanden.

```javascript
let a = -5;  // 11111111111111111111111111111011
let result = a >>> 1;  // 01111111111111111111111111111101 (2147483643)
console.log(result);  // Ausgabe: 2147483643
```









<br><br>
<br><br>
<br><br>
<br><br>


# Assignment Operator

<br><br>

## Safe Assignment Operator ( ?= )
- Alternative to try catch

```javascript
async function fetchUserData(userId) {
  const [fetchError, response] = ?= await fetch(`/api/users/${userId}`);
  if (fetchError) return { error: 'Failed to fetch user data' };

  const [parseError, userData] = ?= await response.json();
  if (parseError) return { error: 'Failed to parse user data' };

  return { userData };
}

// Usage
async function displayUserProfile(userId) {
  const { error, userData } = await fetchUserData(userId);
  if (error) {
    console.error(error);
    displayErrorMessage(error);
  } else {
    renderUserProfile(userData);
  }
}
```
