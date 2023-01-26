---
title: 'Bubble Sort'
description: 'Bubble sort is a popular sorting algorithm for sorting a list'
metaTitle: 'Bubble Sort'
metaDescription: 'Bubble sort is a popular sorting algorithm for sorting a list'
date: '2020-05-07'
tags: ['algorithms']
---

## How the algorithm works

Bubble sort works by going through the list and each time swapping an element one after another. On each pass through the list, one of the number is sorted to its corrected position. Until the whole list is traversed and it's sorted.

The complexity of this algorithm is `O(n^2)` which is really bad, and this kind of algorithm is rarely used in actual use cases, it is one of the simplest algorithms to understand, so we'll go through it.

### Implementation in Javascript

```
function bubbleSort(list = []) {
  // Avoid mutating the original array
  let listCopy = [...list]

  // first loop, grabs a number
  for(let i = 0; i < listCopy.length; i++) {

    // second loop, takes that number through the whole list and sorts it
    for (let j = i + 1; j < listCopy.length; j++) {

      // first number is greater
      if (listCopy[i] > listCopy[j]) {
        // swap it, note: this can be extracted
        let temp = listCopy[i];
        listCopy[i] = listCopy[j];
        listCopy[j] = temp
      }
    }
  }

  return listCopy
}

bubbleSort([3, 4, 1, 2]) //Expect: 1, 2, 3 4
```
