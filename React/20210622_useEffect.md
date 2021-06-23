# useEffect
[Official document](reactjs.org/docs/hooks-effect.html)

With `useEffect`, you can deduct `side effect`. useEffect is similar to `componentDidMount` + `componentDidUpdate` + `componentWillUnmount`.<br/>
There are two different side effects, `clean-up` and no `clean-up`.<br/>

### Effects without cleanup
Following to the document, we want to **run some additional code after React has updated the DOM**,
such as Network request, manual DOM mutations, and logging.
```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [ count, setCount] = useState(0);
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });
  return (
    <div>
	<p>You clicked { count } times </p>
	<button onClick={() => setCount(count + 1)}>
	Click me
        </button>
    </div>
);
}
```
In this example, you tell React that your component needs to do something after render. React calls it later
after performing the DOM updates. We could also perform data fetching or call some other imperative API.<br/>
By default, useEffect run after every render.
```javascript
useEffect(() => {
  document.title = `You clicked ${count} times`;
});
```
We pass a function to the useEffect and this is **Effect**. The function passed to useEffect is going to
be different on every render. This makes *each effect* **belongs** to a particular render.

### Effects with Cleanup
We might want to set up a subscription to some external data source.<br/>
If your effect returns a function, React will run it when it is time to clean up
```javascript
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [ isOnline, setIsOnline] = useState(null);
  
  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    chatAPI.subscriberToFriendStatus(props.friend.id, handleStatusChange);
    return function cleanup() {
      chatAPI.unsubscriberFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'loading...';
  }
    return isOnline ? 'online' : 'offline'; 
  }
```
Returning a function from our effect is optional cleanup mechanism for effects. Every effect may return
a function that cleans up after it. This lets us keep the logic for adding and removing subscriptions
close to each other.<br/>
**When exactly does React clean up an effect?**<br/>
I think this is most important part of side effect. React performs the cleanup when the component unmounts.*Effects run for every render and not just once*. -> This is why React also cleans up effect from the previous render before running the effects next time.

#### Many words directly come from the official document that I cannot really replace with my word yet.


