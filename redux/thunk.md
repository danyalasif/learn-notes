---
title: "Thunk"
metaTitle: "Redux Thunk | DevNotes"
metaDescription: "This is the Redux Thunk"
---

## Redux Thunk
`npm i -s redux-thunk`

Redux out of the box does not the thing to do async.

Thunk is a function that's returned from another function.

```javascript
function definitelyNotAThunk() {
	return function aThunk() {
	console.log("Hello, I'm thunk");
	}
}
```
* Regular Action Creator
```javascript
export const getAllItems = () => ({
	type: UPDATE_ALL_ITEMS,
	items,
})
```
* Thunking Abstraction
```javascript
export const getAllItems = () => ({
	return dispatch => {
		Api.getAll().then(items => {
		dispatch({
			type: UPDATE_ALL_ITEMS,
			items,
		})})}})
```

