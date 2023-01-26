---
title: "Basics"
metaTitle: "Redux Basics | DevNotes"
metaDescription: "This is the Redux Basics"
---
# Redux

## Reducer
Reducer is a function and it takes two arguments
`(action, currentState) -Process-> Returns new state`

Action creators creates an object, sends it to reducer, out comes a new state

## Redux `compose`
Takes a bunch of functions and returns a new function

`const lotsOfFuncs = compose(makeLouder, embolden, Yolo)`
It's a way of chaining functions

## Redux `createStore`


## `combineReducers`
React only has concept of one reducer. We can split up reducers then use combineReducers to combine them into one file.

## applyMiddleware

stub



#### Referrences

[useDispatch](https://react-redux.js.org/next/api/hooks#usedispatch)