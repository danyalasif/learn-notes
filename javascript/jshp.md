---
title: "Javascript The Hard Parts"
metaTitle: "Javascript The Hard Parts | DevNotes"
metaDescription: "A JS land"
---


[https://frontendmasters.com/courses/javascript-hard-parts/](https://frontendmasters.com/courses/javascript-hard-parts/)

## Day 1

### 5 Capacities we look for in candidates
* Analytical problem solving with code
* Technical communication (can I implement your approach just from your explanation)
* Engineering best practices and approach (Debugging, code structure, patience, and referrence to docs)
* Non-technical communication (empathetic and thoughtful communication)
* Language and computer science experience

The first two points are the most important and these are what make or break a person applying to a job!



* JS is using Just in Time (JIT) compilation


### Principles of JS

```js
const num = 3; 
function multiplyBy2 (inputNumber) { 
	const result = inputNumber*2; 
	return result; 
} 
const output= multiplyBy2(4);
const newOutput= multiplyBy2(10);
```

|Global Memory|  |
|--|--|
| num | 3 |
| multiplyBy2| [f] |
| output | 8|
| newOutput| 20|


#### Global Execution Context
As soon as we start running our code we create a **Global Execution Context**
*	Global Memory
*	Live memory of variables with data, Global Variable environment (Memory for storing variables)


A function can be invoked by adding parens to the end, defining a function is not the same as executing it. Executing a function creates a new execution context called Local Execution Context.
#### Local Execution Context
	* Whenever a function is executed, it creates a local execution context
Basically, the value of `output` would be undefined until the `multiplyBy2` function finishes executing and closes the local execution context

#### Callstack
Callstack is a stack, a stack is a data structure in which FILO, first in last out, all the execution contexts are handled in the callstack


|Callstack|
|--|
|  |
|local()|
|global()|

In this case, when local finishes it'll be pushed out the callstack and the control will go to the global() context, callstack keeps track of all the execution contexts.


### Functional Programming
1. Pure Functions (no side effects) -- Its only consequence is the return value
2. 'High Order functions' - highly valuable tool


### Pair Programming
Answer these:
— I know what a variable is
A referrence to a memory area storing the related data
— I've created a function before
Yes
— I've added a CSS style before
Yes
— I have implemented a sort algorithm (bubble, merge etc)
Yes - Bubble, Merge, Selection, Quick Sort
— I can add a method to an object’s prototype
Using `object.prototype.method = function() {}`
— I understand the event loop in JavaScript

— I understand 'callback functions'
Callback functions are called when the given task is done, they introduce synchronous actions in an async js world
— I've built a project in React or Angular
Yes
— I can handle collisions in hash tables
No Ideos

Do these challenges:
http://csbin.io/callbacks