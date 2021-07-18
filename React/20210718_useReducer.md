# `useReducer`
Reducer: A function that returns new state when passed an action. 

### reducer function
```javascript
function exampleReducer(state, action){
   ....
}
```
First argument is current state.<br/>

### useReducer
```javascript
const [state, dispatch] = useReducer(reducer, initialArg, [init]);
// third argument init is optional
```

### useState vs useReducer
-------------------------
| useState | useReducer |
-------------------------
|Easy to implement for most cases|More scalable for complex scenarios|
|Default to use|Reason about state in isolation|
| |Testable in isolation|
| |Resusable|

* This contents is from **[Managing React State](https://app.pluralsight.com/library/courses/react-state-managing)** by [Cory House](https://www.bitnative.com/) course in Plurasight.
