# Promise

```javascript
const promise1 = new Promise((resolve, reject) => {
  throw 'Uh-oh!';
});

promise1.then( r => { 
  // ..
}).catch((error) => {
  console.error(error);
});
```



<br><br>

# Use then & catch with async functions where we resolve promise
```javascript
async ensureConnected() {
  const connection = await this.checkConnection()
}

this.ensureConnected().then( r => {
  // ..
}).catch((e) => {
  throw new RuntimeError(e, undefined, {httpStatus: 500})
});
```

<br><br>


# async await for promise resolve
```javascript
const load = name => new Promise( resolve => {
  name.onload = () => resolve(true);
});
await load(window);
```

<br><br>

# Nested Functions
```javascript

CheckScrollDirection().then( r => { 
console.log( 'This should come as last message and will contain the value we get from the lowest child function: ' + r );
});


function CheckScrollDirection(){return new Promise(resolve => { 
                scrollafterchangeDOWN().then( r => {  
                      console.log( 'This should come as second message' );
                      resolve(r); 
                 });                      
})};  


function scrollafterchangeDOWN(){return new Promise(resolve => { 
                console.log( 'This should come as first message' );
                resolve('direction is down..'); 
})};  

```




<br><br>

# Execute function and if it is promise wait for it
```javascript
// First execute the function. If it is not a promise it will be just be executed. If it is a promise then you land in the then.
Promise.resolve(environment()).then(() => {
    //..
})
```


<br><br>

# Promise.finally()
**Beschreibung**: `finally()` ist eine Methode, die an ein Promise angehängt wird, um Code auszuführen, nachdem das Promise abgeschlossen ist, unabhängig vom Ergebnis.

#### Funktionsweise

1. **Promise-Zustände**:
   - **Pending**: Warten auf die Ausführung.
   - **Fulfilled**: Erfolgreiche Ausführung.
   - **Rejected**: Fehlgeschlagene Ausführung.

2. **Verkettung**:
   - **`then()`**: Erfolgreiche Ausführung.
   - **`catch()`**: Fehlgeschlagene Ausführung.
   - **`finally()`**: Immer ausgeführt, unabhängig vom Ausgang.

#### Beispiel

```javascript
let myPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        const success = true; // Ändere zu false für Fehler
        success ? resolve('Erfolg!') : reject('Fehler!');
    }, 1000);
});

myPromise
    .then(result => {
        console.log(result); // Erfolgreiche Ausgabe
    })
    .catch(error => {
        console.error(error); // Fehlerausgabe
    })
    .finally(() => {
        console.log('Aufräumaktionen hier.'); // Immer ausgeführt
    });
```


<br><br>

# Promise.allSettled()
**Beschreibung**: `Promise.allSettled()` ist eine Methode, die ein einzelnes Promise zurückgibt, das erfüllt wird, wenn alle der übergebenen Promises entweder erfüllt oder abgelehnt wurden. Es ermöglicht das parallele Warten auf mehrere Promises und gibt die Ergebnisse aller Promises zurück, unabhängig davon, ob sie erfolgreich waren oder nicht.
```javascript
const promise1 = Promise.resolve(3);
const promise2 = new Promise((resolve, reject) => setTimeout(reject, 100, 'Fehler!'));
const promise3 = Promise.resolve(5);

Promise.allSettled([promise1, promise2, promise3])
    .then((results) => {
        console.log(results);
        // Ergebnis:
        // [
        //   { status: "fulfilled", value: 3 },
        //   { status: "rejected", reason: "Fehler!" },
        //   { status: "fulfilled", value: 5 }
        // ]
    });
```

<br><br>

# Promise.any()
**Beschreibung**: `Promise.any()` ist eine Methode, die ein einzelnes Promise zurückgibt, das erfüllt wird, wenn eines der übergebenen Promises erfüllt wird. Wenn alle übergebenen Promises abgelehnt werden, wird das zurückgegebene Promise abgelehnt.
```javascript
const promise1 = Promise.reject('Fehler 1');
const promise2 = new Promise((resolve) => setTimeout(resolve, 100, 'Erfolg 2'));
const promise3 = Promise.reject('Fehler 3');

Promise.any([promise1, promise2, promise3])
    .then((result) => {
        console.log(result); // "Erfolg 2"
    })
    .catch((error) => {
        console.error(error);
    });
```


<br><br>

# Promise.withResolver()

Mit **ES2024** kommt `Promise.withResolvers()`, eine neue Methode, die das Arbeiten mit Promises erleichtert.  

#### **Was macht `Promise.withResolvers()`?**
Es gibt ein Objekt mit zwei Werten zurück:  
- **`promise`** – Das Promise-Objekt  
- **`resolve`** – Die zugehörige `resolve`-Funktion  
- **`reject`** – Die zugehörige `reject`-Funktion  

Bisher mussten wir sowas umständlich so schreiben:  

```js
function getWeather() {
  let resolveFn, rejectFn;
  const promise = new Promise((resolve, reject) => {
    resolveFn = resolve;
    rejectFn = reject;
  });

  setTimeout(() => {
    resolveFn("☀️ Sunny");
  }, 1000);

  return promise;
}

getWeather().then(console.log); // Nach 1 Sekunde: "☀️ Sunny"
```

Hier müssen wir erst Variablen `resolveFn` und `rejectFn` anlegen – etwas umständlich.  

---

### **Mit `Promise.withResolvers()` geht es eleganter:**
```js
function getWeather() {
  const { promise, resolve } = Promise.withResolvers();
  
  setTimeout(() => resolve("☀️ Sunny"), 1000);
  
  return promise;
}

getWeather().then(console.log); // Nach 1 Sekunde: "☀️ Sunny"
```

✅ **Klarer, kompakter und einfacher zu lesen.**  

---

### **Anwendungsfälle**
- **Event-Listener in Promises kapseln**
- **Warten auf asynchrone Ereignisse**
- **Timeouts und Abbruchlogik** einfacher umsetzen  

**Fazit:** `Promise.withResolvers()` beseitigt Boilerplate-Code und macht asynchrone Logik sauberer! 🚀
