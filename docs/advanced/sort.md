# Sort

# Sort Array by Numbers ASC
```javascript
var r = [
  {
    "id": 2,
    "name": "Hardware",
    "sorting": 2,
    "parent_id": 0
  },
  {
    "id": 1,
    "name": "Games",
    "sorting": 1,
    "parent_id": 0
  }
];
r.sort((a, b) => a.sorting - b.sorting );
```


# Sort Array by String ASC
```javascript
var r = [
  {
    "id": 2,
    "name": "Hardware",
    "sorting": 2,
    "parent_id": 0
  },
  {
    "id": 1,
    "name": "Games",
    "sorting": 1,
    "parent_id": 0
  }
];
r.sort((a, b) => a.name.localeCompare(b.name) );
```


# Sort Array by two values ASC
The first value got always priority in order. The second value will only count if the first value sort gets not destroyed.
```javascript
var r = [
  {
    "id": 1,
    "name": "Games",
    "sorting": 1,
    "parent_id": 0
  },
  {
    "id": 2,
    "name": "Hardware",
    "sorting": 2,
    "parent_id": 0
  },
  {
    "id": 4,
    "name": "XBOX One",
    "sorting": 1,
    "parent_id": 1
  },
  {
    "id": 5,
    "name": "Playstation",
    "sorting": 3,
    "parent_id": 1
  }
];
r.sort((a, b) => a.sorting - b.sorting || a.name.localeCompare(b.name));
```






# Recursively sort object keys alphabetically (case-insensitive) and array elements
```javascript
// Function to recursively sort object keys alphabetically (case-insensitive) and array elements
        const sortObjectKeys = (obj) => {
            if (_.isArray(obj)) {
                // If it's an array, remove duplicates and sort elements
                return [...new Set(obj.map(JSON.stringify))]  // Remove duplicates from arrays
                    .map(item => JSON.parse(item))
                    .map(item => sortObjectKeys(item)) // Sort each array item
                    .sort((a, b) => {
                        // If the items are objects, sort by their first key (case-insensitive)
                        if (_.isObject(a) && _.isObject(b)) {
                            return Object.keys(a)[0].localeCompare(Object.keys(b)[0], undefined, { sensitivity: 'base' });
                        }
                        // If both items are strings, sort them case-insensitive
                        if (typeof a === 'string' && typeof b === 'string') {
                            return a.localeCompare(b, undefined, { sensitivity: 'base' });
                        }
                        return 0;
                    });
            } else if (_.isObject(obj)) {
                // If it's an object, sort the object keys alphabetically (case-insensitive)
                return Object.keys(obj)
                    .sort((a, b) => a.localeCompare(b, undefined, { sensitivity: 'base' }))
                    .reduce((acc, key) => {
                        acc[key] = sortObjectKeys(obj[key]); // Recursively sort nested objects or arrays
                        return acc;
                    }, {});
            }
            return obj; // Return primitive values as they are
        };
```
