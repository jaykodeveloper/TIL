# `useRef` and `useImperativeHandle`

**Imperative** : 반드시 해야 하는 <br/>

When you are working on components, you sometimes face to directly manipulate DOM element.


### useRef
With this hook, we can use `current`
```javascript
import React, {useRef} from 'react';

const Input = ({ref} => {
    return <input type="text" ref={ref} />
});

const Parent = () => {
    const inputRef = useRef(null);

    function handleFocus() {
        inputRef.current.focus();
    }

    return(
        <>
        <Input ref={inputRef}/>
        <button onClick={handleFocus}>Click</button>
        </>
    )
}

```
In this example we can access `input` element through `ref`'s `current`.


### forwardRef
In React, `ref` is used for DOM element access, we cannot use normal prop. If you want to use `ref` for React Component, you need to use `forwardRef()`. With an example above,

```javascript
import React, {useRef} from 'react';

const Input = forwardRef((props, ref) => {
    return <input type="text" ref={ref} />
});

const Parent = () => {
    const inputRef = useRef(null);

    function handleFocus() {
        inputRef.current.focus();
    }

    return(
        <>
        <Input ref={inputRef}/>
        <button onClick={handleFocus}>Click</button>
        </>
    )
}
```
### Debugging `forwardRef`
1. Pass the function name
```javascript
const Input = forwardRef(function Input(props, ref) {
    return <input type="text" ref={ref} />;
});
```

2. Wrap up the function with `forwardRef`
```javascript
const Input = (props, ref) => {
    return <input type="text" ref={ref}/>
};

Input = forwardRef(Input);
```

3. Add it to `displayName` attribute.
```javascript
const Input = forwardRef((props, ref) => {
    return <input type="text" ref={ref} />
});

Input.displayName = "Input";
```

It is mainly translate [DaleSeo](https://www.daleseo.com/react-forward-ref/)'s blog. All codes are from his blog and I retype for learning purpose.

---------------------------------------------------------------------
From here, this is my pure study part.

`ref`, this is a reference an DOM element that stores a value. It is mutable, but it does not re-render the components.<br/>
Uncontrolled VS Controlled  <br/>
Uncontrolled component is for<br/>
- **Extreme performance requirements**
- Working with non-React libraries
<br/>
Avoiding setting state on unmounted components 

