# With

# Guides
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/with

  
# Include modules
```javascript
// app.js
const rp = require('request-promise')
const rpn = require('request-promise-native')
const axios = require('axios')

module.exports = {
  axios, rp, rpn
}



// sample.js
const requirements = require('./app')

with (testRequirements) {
  async function getUser() {
    try {
      const response = await axios.get('/user?ID=12345');
      console.log(response);
    } catch (error) {
      console.error(error);
    }
  }
}
```
