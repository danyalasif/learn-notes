---
title: "JavaScript Debugging"
metaTitle: "JavaScript Debugging | DevNotes"
metaDescription: "JavaScript Debugging | DevNotes"
---


## Common JS Quirks
* Lengthis calculated based on bytes not characters
* Adding two decimals is bad precision unless fixed precision is used
* Calling ```Array(num)``` returns an array with two undefined places
* ```.sort()``` method converts each element in array to string and then sorts them
* ```Math.max()``` would return -Infinity
* ```(function foo(a, b) {}).length``` returns ```2``` -- The function prototype is set to return the number of arguments specified in function definition.
* ```+"42"``` returns 42, JS implicitly converts a string to number
* ```!!""``` will return false. Empty strings are considered false.
* By setting an arrays length to zero, you can clear it out -- ```Array.length = 0```

## Debugging Cycle
```mermaid
graph LR
A[Identify] --> B[Isolate]
B --> C[Resolve]
C --> D[Prevent]
```
## Debugging Things
* Use ```Preserve Log``` option to preserve the log between reloads
* Use ```Event Listener``` tab to see which events are listening to that specific thing
* 
* 

### Editing files directly in chrome
* Right click anywhere in the source file
* Select ```Add folder to workspace```
* Select the root folder of your project
* Right click again
* Select ```Map file to filesystem resource```

### Async Debugging
* Sources > Call Stack > Async

### Blackboxing Scripts !important
* Keeps unnecessary scripts from being shown into the console and other places -- Mutes them out
* When debugging, Blackbox'd scripts will always be stepped over.
* Blackbox scripts like JQuery and other framework specific things which don't matter.


### Cache and Logs
* Use Preserve Logs to keep network and console preserved between refreshes
* Use ```Disable Cache`` under ``Network``` panel to test things better.

### Validation
Properly validate properties that are communicated back and forth by user, they can be null or empty which can cause problems, there should be proper checks before storing and retrieving such data.

### Finding and Fixing Memory Leaks
#### Profiler
* Use Profiles tab to find different metrics about the application
* Profile Allocation Timelines to find memory allocations
* You can save memory profiles in the form of Snapshots
#### Timeline
*	It can take pictures of network requests
*	Memory is being consumed
*	Navigate it using ```WASD```
*	Blue box shows that it increased the heap size
*	Once you click on a box it'll show the total time for it to load in Summary panel

