You should create one application using CRA or not. After you create the application, do the following steps:
- [ ] install [redux package](https://www.npmjs.com/package/redux). 
- [ ] configure [redux dev tools](https://github.com/reduxjs/redux-devtools)


You don't have to implement any UI, but you can do it if you wish.
The state might have a number type, and you should create it with the following code:
```
const balance = createStore(__YOUR_REDUCER__);
```

List of actions you should create:
```
const array = [
    { type: "UPDATE_BALANCE", payload: 1000.0 },
    { type: "CREDIT", payload: 200.0 },
    { type: "CREDIT", payload: 100.0 },
    { type: "SET_BALANCE_WITH_TAX" payload: 14.0 },
    { type: "DEBIT", payload: 250.0 },
    { type: "UPDATE_BALANCE", payload: 1000.0 },
];
```

| Action | Payload type | Description |
| ------ | ------ | ------ |
| `UPDATE_BALANCE` | `number` | Should add a new amount to balance. Should replace current balance if the balance is defined |
| `CREDIT` | `number` | Should subtract payload amount to balance |
| `SET_BALANCE_WITH_TAX` | `number` | Should set a new amount of the balance in which TAX is deducted |
| `DEBIT` | `number` | Should subtract payload amount from balance |

It will be checked only using redux dev tools where I am able to see list of actions.

Example:
```
const balance = createStore(__YOUR_REDUCER__);
balance.dispatch({ type: "UPDATE_BALANCE", payload: 1000.0 }); // balance = 1000.0
balance.dispatch({ type: "CREDIT", payload: 200.0 }); // 800.0
balance.dispatch({ type: "DEBIT", payload: 50.0 }); // 850.0
balance.dispatch({ type: "SET_BALANCE_WITH_TAX" payload: 14.0 }); // 850.0 * (1 - 0.14) = 731 
```
Also, you need to publish your homework with dev tools:
```
import { createStore, compose } from "redux";

declare global {
  interface Window {
    __REDUX_DEVTOOLS_EXTENSION_COMPOSE__?: typeof compose;
  }
}
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;
const store = createStore(rootReducer, undefined, composeEnhancers());
```
