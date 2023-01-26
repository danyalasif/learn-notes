---
title: "Redux Saga"
metaTitle: "Redux Saga | DevNotes"
metaDescription: "A Redux Saga land"
---

# Redux Saga
Saga let's us set up a generator function to intercept dispatched action object. Pause until we have the data and then dispatch the another action with the data to modify the UI.
Saga sits in the middle listening to actions

## Saga File
```javascript
import createSagaMiddleware from 'redux-saga';
import saga from './saga';
const sagaMiddleware = createSagaMiddleware();

const middleware = [sagaMiddleware];

const store = createStore(
	reducers,
	initialState,
	composeEnhancers(applyMiddleware(...middleware), ...enhancers),
);
//start up the generator
sagaMiddleware.run(saga);
```

## Generators
A normal function cannot be paused or stopped before its execution is completed, once it finishes execution and returns a value, that execution context is gone. 

Generators are functions that can return or `yield` values in between without exiting the current context. These functions can be paused in between and wait a while until they are needed to be called. Once it's paused/stopped, it can continue from that same place again, resuming in its current context.


Generators help us in writing async code.
```javascript
function* generateThreeNumbers() {
	yield 1; // return 1 on first next()
	yield 2;
	yield 3;
}
var numIter = generateThreeNumbers();
numIter.next() // {value: 1, done: false}
```

You can pass in more data while the generator is going. When you call `next()`

Sometimes we need to wait a bit for information!

Async Await is a syntactic sugar on Generators.

## Register, Intercept, and Put
```javascript
import { all, call, put, takeEvery } from 'redux-saga';
//all: All different events and then kick off generator
//call: Make some async request
//put: dispatch some action 

export default function* rootSaga() {
	yield all([fetchItemsFromApi()])
}

export function* fetchItemsFromApi() {
	yield takeEvery('FETCH_ITEMS', makeApiRequest);
}

export function* makeApiRequest() {
	const items = yield call(Api.getAll);
	yield put(updateAllItems(items));
}
```

`call` is a method in Redux Saga used for calling functions
`put` is used for emitting events / actions
`take` waits for an action to be emitted before going further, the function  waits for this specific action to be intercepted



### Resources
[https://medium.com/20spokes-whiteboard/getting-familiar-with-redux-sagas-5b5856c97a75]
[https://goshakkk.name/lazy-auth-redux-saga-flow/]
[https://goshakkk.name/redux-side-effect-approaches/]
