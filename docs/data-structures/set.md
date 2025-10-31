# Set

<br><br>
   
# Guides
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Set

<br><br>
   

# Examples
```javascript
const uniqueNumbers = [1,2,3,3,4]
const set = new Set(uniqueNumbers)
console.log(set)
console.log(set.has(2)) // true
console.log(set.has(5)) // false
```

<br><br><br><br>
   


# .delete
```javascript
const uniqueNumbers = [1,2,3,3,4]
const set = new Set(uniqueNumbers)
console.log(set.delete(2))
console.log(set)
console.log(set.has(2))
```
