# When does React render?
- State change
  + can skip render via shouldComponent or React.memo
- Prop change
  + can skip render via shouldComponent or React.memo or PureComponent
- Parent render
  + can skip render via shouldComponent or React.memo or PureComponent
- Context change

# Four ways to handle API calls
1. Inline Call fetch(axios/fetch/etc) in your component **Not recommended**
2. Centralized functions Call separate function
3. Custom hook Create and call your own custom hook
4. Library Call library(react-query, swr, etc...)

# Error boundary
[Error Boundary](https://reactjs.org/docs/error-boundaries.html)

### We can set React environment in **package.json**.

```javascript
"scripts": {
    "start": "run-p start-app start-api",
    "start-app": "cross-env REACT_APP_API_BASE_URL=http://localhost:3001/ react-scripts start",
    "start-api": "json-server --port 3001 --watch db.json --delay 0",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
```