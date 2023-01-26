---
title: "Filter arrays for unique objects"
metaTitle: "Javascript | DevNotes"
metaDescription: "A JS land"
---
## Get only unique objects in an array or between two arrays
```js
var arr = [
  {email: 'matthew@gmail.com', id: 10}
]

var arr2 = [
  {email: 'matthew@gmail.com', id: 10},
  {email: 'matthew@gmail.com', id: 13}
]

var mergedArray = arr.concat(arr2);
var map         = new Map(mergedArray.map(o => [o.id,o]));
var unique      = [...map.values()];

console.log(unique);
// returns [{email:  "matthew@gmail.com",  id:  10},{email:  "matthew@gmail.com" id:  13}]
```


* [https://stackoverflow.com/questions/40494853/use-new-set-to-get-only-uniques-based-off-inner-arrayobject-id](https://stackoverflow.com/questions/40494853/use-new-set-to-get-only-uniques-based-off-inner-arrayobject-id)

* [https://javascript.info/map-set](https://javascript.info/map-set)