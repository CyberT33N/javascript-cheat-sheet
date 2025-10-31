# filter

# compare 2 arrays of objects and remove duplicates
```javascript
var cars1 = [
    {id: 2, make: "Honda", model: "Civic", year: 2001},
    {id: 1, make: "Ford",  model: "F150",  year: 2002},
    {id: 3, make: "Chevy", model: "Tahoe", year: 2003},
];
    
var cars2 = [
    {id: 3, make: "Kia",    model: "Optima",  year: 2001},
    {id: 4, make: "Nissan", model: "Sentra",  year: 1982},
    {id: 2, make: "Toyota", model: "Corolla", year: 1980},
];

let res = cars1.concat(cars2.filter(({id}) => !cars1.find(x => x.id === id)))
             //.sort((a, b) => a.id - b.id);

console.log(res);
```










<br><br>
<br><br>

# Recursive remove empty values (empty strings, null, undefined)
```javascript
function cleanObject(obj) {
            if (Array.isArray(obj)) {
                // If it's an array, recursively clean each element
                return obj
                    .map(item => cleanObject(item)) // Recursive call for each array item
                    .filter(item => {
                        if (_.isObject(item)) {
                            return Object.keys(item).length > 0;
                        }
                        return item !== null && item !== undefined && item !== '';
                    }); // Remove empty values
            } else if (typeof obj === 'object' && obj !== null) {
                // If it's an object, clean its properties recursively
                let cleanedObj = {};
                
                for (let key in obj) {
                    if (obj.hasOwnProperty(key)) {
                        let value = obj[key];
                        let cleanedValue = cleanObject(value);
                        
                        // Only add the property if the value is not empty
                        if (cleanedValue !== null && cleanedValue !== undefined && cleanedValue !== '' &&
                            !(_.isObject(cleanedValue) && Object.keys(cleanedValue).length === 0)) {
                            cleanedObj[key] = cleanedValue;
                        }
                    }
                }
                
                return cleanedObj;
            }
            
            return obj; // Return if it's not an object or array
        }

        // Clean empty values from each object, including nested objects and arrays
        const cleanedAr = uniqAr.map(obj => cleanObject(obj))
            .filter(obj => Object.keys(obj).length > 0); // Remove empty objects

        // Output the cleaned objects as a single-line formatted JSON string
        console.log(JSON.stringify(cleanedAr));
```
