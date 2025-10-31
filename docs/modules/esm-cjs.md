# ESM (es-modules) and CJS (commonjs)

# Guides
CJS vs ESM (https://redfin.engineering/node-modules-at-war-why-commonjs-and-es-modules-cant-get-along-9617135eeca1)

# Examples for difference
```javascript
// ### CJS ##
module.exports.sum = (x, y) => x + y; // @filename: util.js
const {sum} = require('./util.js');

// ### ESM ##
export const sum = (x, y) => x + y; // @filename: util.js
import {sum} from './util.js'
```

<br><br>
______________________________________________________
<br><br>


# CJS

## export all functions
```javascript
module.exports = {
    foo: ()=>{/*..*/},
    bar: ()=>{/*..*/}
};
```

<br><br>

## export specific function
```javascript
// example #1
module.exports.anyname = ()=>{/*..*/};
```

<br><br>

## include parameter
```javascript
// index.js
(async () => {
    await browserWrapper.connect()
})().catch(e => {
    console.error(new Error(e))
})

module.exports = require('./thumbnail')(browserWrapper)


// thumbnail.js
module.exports = (browserWrapper) => {
  //..
};
```


<br><br>

## export class
```javascript
// person.js
'use strict';

module.exports = class Person {
   constructor(firstName, lastName) {
       this.firstName = firstName;
       this.lastName = lastName;
   }

   display() {
       console.log(this.firstName + " " + this.lastName);
   }
}


// index.js
'use strict';

var Person = require('./person.js');

var someone = new Person("First name", "Last name");
someone.display();
```

	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
<br><br>
______________________________________________________
<br><br>

# ESM

## Features & Good 2 Know
- No need for **"use strict"** because it will be default
- async works without self invoked functions
	
- import statements sadly only support single or double quotes. So this is not working:
	```javascript
	import stats from `./${process.env.STATS}`
	
	// only this is allowed
        import stats from '../sample/file.js'
	```
- import statements sadly only works by writing the javascript file with extension. So this is not working:
	```javascript
	import stats from `./file`

        // this works instead
        import stats from `./file.js`
	```



<br><br><br><br>

## How to enable?
```javascript
// package.json
"type": "module"

// In some node versions you may must rename your files to .mjs
```	
- On some Node Versions you may need to use:
```javascript
node --experimental-modules app.mjs
```
	
	
<br><br>





<br><br><br><br>


## Export / Import
```javascript
	
/*
## Option 0 ##
Write like CJS but with import instead. Results will be stored inside of default
*/
	
const requirements = await import('../requirements.js')
const { getMongoConn } = requirements.default

// This works aswell
(await import('../requirements.js')).default
	
	
	
	
	
/*
## Option 1 ##
Name your export instead of using default. It should look like this
*/
	
// add.mjs
export const add = (a, b) => a + b;

// app.mjs
import { add } from './add.mjs';


	
	
	
	
	
	

/* ## Option 2 ##
Use the export default syntax. It looks like this */

// add.,js
export default function add(a, b) {
  return a + b;
}

// app.,js
import add from './add.mjs';

	
	
	


/* ## Option 3 ##
Use the export default syntax. As example for controller files*/

// controller.mjs
import {startBROWSER, openLink} from '../services/bot.mjs';
export default {
  startBROWSER: async ()=>{ return await startBROWSER(); },
  openLink: async (page, link)=>{ return await openLink(page, link); }
}


// app.mjs
import bot from './controller.mjs';
await bot.startBROWSER();


	
	
	
	
	

/* ## Option 4 ##
Use export on specific functions and import all available to object*/

// bot.mjs
export const getUserDetails = async (req, res)=>{ /*..*/ });
export const getRoomDetails = async (req, res)=>{ /*..*/ });

// app.mjs
import * as bot from '../services/bot.mjs';
await bot.getUserDetails(req, res);



	
	
	
	
/* ## Option 5 - export classes ##
export class startBROWSER {/*..*/};


	
	
	

/* ## Option 6 - export variable ##
export let pptr;
```

<br><br>
<br><br>


### Re-export default
```javascript
export * as errorMiddleware from './middleware'
```

<br><br>
<br><br>


### Re-export object
```javascript
export { default as HttpClientError } from './errors/HttpClientError'
```
	


<br><br>
<br><br>


### Re-export object as object
```javascript
export { HttpClientError } from './errors/HttpClientError'
```
	


 
<br><br>
<br><br>


### Import JSON
```javascript
import json from './foo.json' assert { type: 'json' };
console.log(json.answer); // 42
```
	


 














 
<br><br>
<br><br>
<br><br>
<br><br>



## Client Side
- In order to use client side ESM we use **type="module"**
```html
<!-- method #1 -->
<script type="module" src="js/utils/test.main.mjs"></script>

<!-- method #2 -->
<script type="module">
  import web from '/js/main.mjs';
</script>

<!-- method #3 -->
<script type="module">
  import '/js/main.mjs';
</script>
```

<br><br>


## No require, exports, module.exports, __filename, __dirname (https://nodejs.org/api/esm.html#esm_no_require_exports_module_exports_filename_dirname)
```javascript
import { fileURLToPath } from 'url';
import { dirname } from 'path';

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);
```






<br><br>


## Import script dycamic
```javascript
// If you use vanilla javascript you can use this to enable esm
// <script type="module" src="js/home/searchBar/app.js"></script>
	
// app.mjs
const loadTest = async () => {
    const {test} = await import("./app2.mjs")
    test()
}

var a = true
if (a === true) {
    loadTest()
}



// app2.mjs
export const test = async () => {
    console.log(true)
}
```
