
From lesson we already have implementation of function which is `createStore`. 
Codesandbox can be forked. [Link](https://codesandbox.io/s/001-redux-pi4jj?file=/src/redux.ts)

The task is to implement a combineReducer function which should be identical to the one in `https://redux.js.org/api/combinereducers`.

```
const app = combineReducer({
  counter: counter,
  counter2: counter2,
});

const appStore = createStore(app);
```

Expected result:
- Your `combineReuducer` should work as original function from library. 
- The reducer counter2 should have diffenent actions type name and they should be dispatched after counter's actions.

How to test:
Your function can be replaced by original and everything should work as well.
