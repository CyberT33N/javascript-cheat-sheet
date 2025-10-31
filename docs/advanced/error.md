# Error

# cause
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error/cause
- The cause data property of an Error instance indicates the specific original cause of the error. It is used when catching and re-throwing an error with a more-specific or useful error message in order to still have access to the original error.
```javascript
try {
  connectToDatabase();
} catch (err) {
  throw new Error("Connecting to database failed.", { cause: err });
}
```
