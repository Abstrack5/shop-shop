```
Redux is built on the following three core principles, which aren't totally unique to Redux, as we'll soon see:

Single source of truth: By having all of the application's data stored in one location that isn't tied to any single piece of the UI, we can easily manipulate our app's UI without having to affect any of it.

State is read-only: This doesn't mean state can't be updated, but rather that it cannot be directly updated. Instead, it should be overwritten with a new iteration of that state. This makes it so that the application's state is updated in a predictable fashion and the UI won't ever get out of sync with its data.

State is changed through pure functions: This means that to make an update to state, we don't actually manipulate it. Instead, we overwrite it with a new version of it. This lowers the chance of any data being accidentally affected by an action. We do this by creating what's known as a reducer, which runs as a result of an action.
```


```
The name for a global state object is often referred to as a store.
```


```
a global store is built on two important pieces when it comes to updating state:

Actions: These define the types of events that can be emitted to update state. State can only be updated if it's a predefined action.

Reducers: The actual functionality that carries out the emitted action to update state.

Because of this relationship, we'll need to create our actions before we create our reducers
```

```
Prop drilling is what happens when we manage state at a top-level component that needs to be passed through multiple child components as props. When the data is passed around too much, it becomes difficult to keep track of which components are reliant on which data. To remedy this, creating a global state object will allow any component in our application to use and update state without having to worry about receiving that information as props. This will make our component much more readable, and create data much more reusable over time.
```

```
The React Context API came from a need to have more Redux-like features built right into React. [_DOCS_](https://reactjs.org/docs/context.html)
```

```
    import React, { createContext, useContext } from "react";

{ createContext } will be used to instantiate a new Context object. The more meaningful term we can use here is that we're using it to create the container to hold our global state data and functionality so we can provide it throughout our app!

{ useContext } is another React Hook that will allow us to use the state created from the createContext function.

to actually instantiate the global state object:

    const StoreContext = createContext();
    const { Provider } = StoreContext;


When we run the createContext() function, it creates a new Context object. We touched upon that in the definition we gave earlier in the lesson. But what about this Provider thing we're pulling out of it?

Every Context object comes with two components, a Provider and Consumer. The Provider is a special type of React component that we wrap our application in so it can make the state data that's passed into it as a prop available to all other components. The Consumer is our means of grabbing and using the data that the Provider holds for us.
```


```
