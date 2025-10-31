# String

# .includes()
```javascript
var str = "Hello world, welcome to the universe.";
var n = str.includes("world");
console.log(n); // true
```
	
<br><br>
	
# get name of string in function
```javascript
const test = (prop) => {
    var name = Object.keys(prop)[0];
    var value = prop[name];

    const obj = {}
    obj[name] = value
    return obj
}

let schema = true

console.log(test({schema}))
```




<br><br>
	
# trim(), trimStart() & trimEnd()
**Beschreibung**: Diese Methoden dienen dazu, Leerzeichen oder bestimmte Zeichen am Anfang und Ende von Strings zu entfernen.

#### Funktionsweise

1. **`trim()`**:
   - **Zweck**: Entfernt Leerzeichen (Whitespace) von beiden Enden eines Strings.
   - **Beispiel**:
     ```javascript
     const str = "   Hallo Welt!   ";
     const trimmedStr = str.trim(); // "Hallo Welt!"
     ```

2. **`trimStart()`** (auch `trimLeft()` genannt):
   - **Zweck**: Entfernt Leerzeichen (Whitespace) nur vom Anfang eines Strings.
   - **Beispiel**:
     ```javascript
     const str = "   Hallo Welt!   ";
     const trimmedStartStr = str.trimStart(); // "Hallo Welt!   "
     ```

3. **`trimEnd()`** (auch `trimRight()` genannt):
   - **Zweck**: Entfernt Leerzeichen (Whitespace) nur vom Ende eines Strings.
   - **Beispiel**:
     ```javascript
     const str = "   Hallo Welt!   ";
     const trimmedEndStr = str.trimEnd(); // "   Hallo Welt!"
     ```

#### Vorteile

- **Datenbereinigung**: Nützlich für die Bereinigung von Benutzereingaben.
- **Konsistenz**: Stellt sicher, dass Strings die gewünschte Formatierung haben, insbesondere bei Vergleichen oder beim Speichern in Datenbanken.
- **Flexibilität**: `trimStart()` und `trimEnd()` bieten mehr Kontrolle, wenn nur ein Ende bearbeitet werden soll.





<br><br>
	
# matchAll() & replaceAll()
- Normally match() or replace() only replace the first matched value. Now matchAll() & replaceAll() replaces all
```javascript
const test = text.matchAll("Cats");

const test2 = text.replaceAll("Cats", "Hello Cats are Cats");
```
