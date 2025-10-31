# Async/Await

# Create Async
```javascript
// Method 1 - Catch error
(async () => {
 console.log( 'do some async stuff here..' );
})().catch((e) => {
 console.log('Error:' +  e )
}); 

// Method 3 - Do not catch error - you muste use then try inside or wrap another method 1 async function around this
(async () => {
 console.log( 'do some async stuff here..' );
})();

// Method 3 - Do not catch error - you muste use then try inside or wrap another method 1 async function around this
async function test(){
 console.log( 'do some async stuff here..' );
}
```


# setTimeout
```javascript
// method #1a ESM (Works with node 16+)
import { setTimeout } from 'timers/promises';
await setTimeout(5000)
		
// method #1a CJS (Works with node 16+)
const { setTimeout } = require('timers/promises');
await setTimeout(5000)

// method #2
await new Promise(resolve => setTimeout(resolve, 1000));
```



# setInterval
- setInterval can be **NOT** used with await. For endless loop you can use while or for
```javascript
// method #1
async function loop() {
  while (true) {
    // click yes button
    document.querySelector('span[data-automation-id="vote-yes-button"]').click();

    // create random break
    const rnd = Math.round(Math.random() * 50 + 1);
    const longBreak = 500000;
    const loopDelay = Math.round(Math.random() * 1000 + 1)
    if (rnd == 1) await new Promise(resolve => setTimeout(resolve, longBreak));
    console.log(rnd);

    await new Promise(resolve => setTimeout(resolve, loopDelay));
  }
}

loop();


// method #2
async function loop() {
  for (;;) {
    // click yes button
    document.querySelector('span[data-automation-id="vote-yes-button"]').click();

    // create random break
    const rnd = Math.round(Math.random() * 50 + 1);
    const longBreak = 500000;
    const loopDelay = Math.round(Math.random() * 1000 + 1)
    if (rnd == 1) await new Promise(resolve => setTimeout(resolve, longBreak));
    console.log(rnd);

    await new Promise(resolve => setTimeout(resolve, loopDelay));
  }
}

loop();
```

	
	
	
	
	
	
<br><br>


# Functions - In Parallel
```javascript
async function a (){
  console.log('a');
};


async function b (){
  console.log('b');
  await new Promise(resolve => setTimeout(resolve, 3000));
  console.log('b later');
};



(async () => {

  await Promise.all([a(), b()]);
  console.log('c');
  
  /*
  // to store the results you can use this..
  let [someResult, anotherResult] = await Promise.all([someCall(), anotherCall()]);  
  
 // ** IMPORTANT **
 // When any promise gets rejected then all other calls after this will get rejected too.. Use instead Promise.allSettled() which will wait for all functions to get finished if resolved or rejected

*/

})().catch((e) => {
   console.log('Error:' +  e )
}); 

```
	
	
	
		
<br><br>


## Specific amount of runs
```javascript
const sampleFunction = async () => {
  new Promise(resolve => setTimeout(() => resolve(), 100))
}


const promises = []

for (let i = 0; i < 10; i++) {
  promises.push(sampleFunction)
}

const doSomeAsyncStuff = async (funcs) => {
  const allPromises = funcs.map(func => func())
  const res = await Promise.all(allPromises)
  return res
}

doSomeAsyncStuff(promises)
```
	
	
	
	
	
	
	
	
<br><br>	
<br><br>

# Loops (Array) - In Parallel
```javascript
await Promise.all(
  yourArrayHere.map(async d => {
    console.log( 'Current array item we process: ' + d );
     //.. do something
  })    
);
```

# Loops - Sequential (For Loop)
```javascript
for (const d of yourArrayHere) {
    await redirectChecker(d);
 }
```


# Combine Async with promise
```javascript
// example #1 - await for promise resolve
function one(){return new Promise(resolve => { 
  // do something
  resolve(true); 
})};  

const result = await one();

// example #2 - async function inside of promise
return new Promise(async resolve => {
  // do something async
  resolve(true); 
})
```
