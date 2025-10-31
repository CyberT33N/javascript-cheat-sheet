# Web API

# URL()
- https://developer.mozilla.org/en-US/docs/Web/API/URL/URL
```javascript
let test = new URL('https://developer.mozilla.org/fr-FR/toto?peter=true&lena=true')

let res1 = test.searchParams.get('peter')
console.log(res1)

let res2 = Object.fromEntries(test.searchParams)
console.log(res2)
```



<br><br

# Web Workers

JavaScript Web Workers
Was sind Web Workers?

Web Workers sind eine JavaScript-API, die es ermöglicht, Skriptausführungen im Hintergrund durchzuführen, ohne die Benutzerschnittstelle zu blockieren. Das bedeutet, dass komplexe Berechnungen oder langwierige Aufgaben in einem separaten Thread laufen können, während die Hauptseite des Browsers reaktionsfähig bleibt.

Wie funktionieren Web Workers?

    Erstellung eines Web Workers:
        Ein Web Worker wird durch das Erstellen eines neuen Worker-Objekts initiiert. Dabei wird die URL eines JavaScript-Skripts angegeben, das im Hintergrund ausgeführt wird.

    ```javascript
    let worker = new Worker('worker.js');
    ```

    Kommunikation zwischen Hauptthread und Worker:
        Die Kommunikation erfolgt über die postMessage-Methode. Der Hauptthread kann Nachrichten an den Worker senden, und der Worker kann Nachrichten an den Hauptthread zurücksenden.

    ```javascript

    // Im Hauptthread
    worker.postMessage('Hallo vom Hauptthread!');

    worker.onmessage = function(event) {
        console.log('Nachricht vom Worker:', event.data);
    };

    // Im Worker-Skript (worker.js)
    self.onmessage = function(event) {
        console.log('Nachricht vom Hauptthread:', event.data);
        self.postMessage('Hallo zurück vom Worker!');
    };
    ```

    Beenden des Workers:
        Ein Worker kann durch die terminate-Methode beendet werden.

    ```javascript

    worker.terminate();
    ```

Beispiel für einen einfachen Web Worker

Angenommen, du möchtest eine intensive Berechnung durchführen, wie das Fakultäts einer Zahl zu berechnen:

    Haupt-Skript (index.html):


```html

<!DOCTYPE html>
<html>
<head>
    <title>Web Worker Beispiel</title>
</head>
<body>
    <script>
        let worker = new Worker('worker.js');

        worker.onmessage = function(event) {
            document.getElementById('result').textContent = event.data;
        };

        document.getElementById('calculate').onclick = function() {
            let number = parseInt(document.getElementById('number').value);
            worker.postMessage(number);
        };
    </script>
    <input type="number" id="number" placeholder="Gib eine Zahl ein">
    <button id="calculate">Berechne Fakultät</button>
    <p id="result"></p>
</body>
</html>
```

    Worker-Skript (worker.js):


```javascript

self.onmessage = function(event) {
    let number = event.data;
    let factorial = calculateFactorial(number);
    self.postMessage(factorial);
};

function calculateFactorial(n) {
    if (n === 0 || n === 1) {
        return 1;
    } else {
        return n * calculateFactorial(n - 1);
    }
}
```

Nutzung von Web Workers:

    Vorteile:
        Vermeidung von UI-Blockierungen durch Hintergrundprozesse.
        Möglichkeit zur Parallelisierung von Aufgaben für bessere Leistung.
    Einschränkungen:
        Web Workers haben keinen direkten Zugriff auf das DOM, können also nicht direkt HTML manipulieren.
        Die Kommunikation zwischen Hauptthread und Worker ist asynchron, was das Debugging etwas komplizierter macht.


Mit diesen einfachen Beispielen kannst du direkt in dein JavaScript Cheat Sheet integrieren, um die Funktionsweise und Nutzung von Web Workers klar zu veranschaulichen.













<br><br

# AbortController API

Die `AbortController` API ermöglicht es, asynchrone Operationen (wie z.B. Fetch-Anfragen oder Promises) abzubrechen. Dies ist besonders nützlich, um Ressourcen zu sparen und unerwünschte Ergebnisse zu verhindern, wenn eine Operation nicht mehr benötigt wird.

## Verwendung

1.  **Erstellen eines `AbortController`:**

    ```javascript
    const controller = new AbortController();
    ```

2.  **Abrufen des `signal`:**

    Das `signal` des Controllers wird an die abzubrechende Operation übergeben.
    
    ```javascript
    const signal = controller.signal; 
    ```

3.  **Anhängen des `signal` an die Operation:**

    Das hängt davon ab, wie die Operation durchgeführt wird. Bei `fetch` wird das `signal` als Option hinzugefügt:

    ```javascript
    fetch('https://example.com/data', { signal })
      .then(response => /* ... */)
      .catch(error => {
        if (error.name === 'AbortError') {
          // Anfrage wurde abgebrochen
          console.log('Fetch wurde abgebrochen');
        } else {
          // Andere Fehler behandeln
        }
      });
    ```

    Bei Promises kann es z.B. durch einen Abort-Callback gelöst werden.

4.  **Abbrechen der Operation:**

    Mit `controller.abort()` wird die Operation abgebrochen.

    ```javascript
    // Irgendwann später
    controller.abort();
    ```

## Kern-Eigenschaften und Methoden

*   **`AbortController()`**
    *   Konstruktor: Erstellt eine neue `AbortController` Instanz.

*   **`AbortController.signal`**
    *   Eigenschaft: Gibt ein `AbortSignal` Objekt zurück, welches mit der Operation verbunden wird.
        *   **`AbortSignal.aborted` (read-only)**: Boolescher Wert, der `true` ist, wenn die Operation abgebrochen wurde.
        *   **`AbortSignal.onabort`**: Event-Handler, der aufgerufen wird, wenn die Operation abgebrochen wird.
        *   **`AbortSignal.reason`**: Ein Optionaler Wert, der dem abort-call übergeben wurde.

*   **`AbortController.abort(reason)`**
    *   Methode: Bricht die mit dem `AbortSignal` verbundene Operation ab. Kann einen optionalen Grund übergeben, der über das `signal.reason` ausgelesen werden kann.

## Anwendungsfälle

*   **Fetch-Anfragen:** Abbruch von ausstehenden Netzwerk-Requests.
*   **Asynchrone Operationen:** Abbruch von Timern, Animationen, Event-Listenern oder anderen asynchronen Prozessen.
*   **Umgang mit User-Interaktionen:** Abbruch von Operationen, die durch Benutzereingaben überholt wurden.
*   **Optimierung:** Vermeidung von unnötigen Berechnungen und Updates, wenn eine Operation irrelevant geworden ist.

## Beispiel: Fetch-Abbruch

```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://example.com/data', { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => {
    if (error.name === 'AbortError') {
      console.log('Fetch-Anfrage abgebrochen!');
    }
    else {
        console.error(error);
    }
  });

// Nach einigen Sekunden abbruch
setTimeout(() => {
  controller.abort();
}, 3000);
```
