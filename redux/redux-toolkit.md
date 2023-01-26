---
title: 'Redux Toolkit'
description: 'Redux Toolkit is the recommended toolkit for using redux'
metaDescription: 'Redux Toolkit'
date: "2019-12-27"
---

## Install

* NPM
npm install --save @reduxjs/toolkit
* Yarn
yarn add @reduxjs/toolkit

## What is redux toolkit

A wrapper/abstraction around redux, it effectively removes a lot of the boilerplate required to set up and get started with redux. For me at least, the major selling point is how intuitive the interface is. When it is already a given that if some action exists, it must have a reducer too, otherwise there's no point in having that action, then what is the point of setting all this up separately. So it makes sense in that regard.

## How to do?
* createStore() & configureStore()
```js
const store = createStore(reducer)

const store = configureStore({ reducer: rootReducer })
```
* createAction() is the one and be all of RT
```js
const loginRequest = createAction('loginRequest')
```
What this creates in the shadows is: An action-creator, proper payload setup.



