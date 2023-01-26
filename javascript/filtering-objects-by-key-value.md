---
title: "Filter Object of Objects"
metaTitle: "Javascript | DevNotes"
metaDescription: "A JS land"
---
## Get only specific objects from object of objects

In this scenario I couldn't use the vanilla `filter` method which can be used on arrays, so I had to look at other options.

Usually you are using object of objects when the id or unique identifier is being used as the key to make the search and filtering time complexity to be O(1) aka Hash Maps

### Lodash
```js
import _filter from 'lodash/filter'

let someObjects = { 
    1: {id: 1, user: 'Dan', isActive: true},
    2: {id: 2, user: 'Dog', isActive: false},
    3: {id: 3, user: 'Cat', isActive: true}
}

_filter(someObjects, {isActive: true}) // returns {{user: 'Dan', isActive: true}, {user: 'Cat', isActive: true}}

```


* https://lodash.com/docs/
* https://lodash.com/docs/#filter