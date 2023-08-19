**1. What is React?**

React.js is a library created by Facebook, it allow to build user interfaces using customised components, that mix html elements and javascript. It's based on the Single Page Application Concept, that would be to build an application with only one page, changing the elements without reloading the entire page.

Since it's a library, it does not come with all necessary tools, so it's necessary to install other libraries. This library was created to react to changes and it was developed with the purpose to specified what you want to build not how.

**2. Why use it?**

- Reusable components
- Performance
- Abstraction

**3. Requirements**

- Html
- Css
- Javascript
  - Arrow functions
  - Spread/ Rest operator
  - Map, reduce e filter

**4. Virtual DOM**

Virtual DOM is a in memory representation of the DOM, it creates a representation of the real DOM using keys to identify the elements and using them to identify which element and what has changed, this way the DOM wouldn't need to be entirely reloaded, since it will modify only what changed.

**5. JSX**

JSX stands for extended javascript, it allow us to write HTML inside javascript and it's used to facilitate the codification write.

After it's compiled, it's transformed function signature that return objects. To compile, it's used babel.

So, the code below writes a header using jsx.

```js
const header = <h1 className="header">Hello</h1>
```

After it's compiled, this will be the equivalent.

```js
const header = React.createElement(
  'h1',
  props: {
  className: 'header',
  children: 'Hello'
  }
);
```

**6. Components**

A component is a construction block that work as functions, receiving parameters and returning React elements. To create a component is necessary to use a class or a function, writing the name starting with capital letter. The components allows to isolate and reuse code, since it receive parameters, known as props, that can be different values, as functions, components, texts, numbers etc. To reuse the code it's used the composition concept, this way will be considered what the value will do and not it's type.

Components can have default props, used in case no props are passed down.

```js
element.defaultProps = {
  color: "Red",
}
```

- Functional

Functional components are built using functions, must act as pure function, so it will not modify the input values.

```js
import React from "react"

const Hello = () => <h2>Hello</h2>

export default Hello
```

- Class based

Class based components are built using es6 class, they have more functionalities that the functional ones since they extend React.Component. They must have a render method, because this is responsible for the render the data.

```js
import React, { Component } from "react"

class Hello extends Component {
  render() {
    return <h2>Hello</h2>
  }
}

export default Hello
```

This type of component has some interesting features such as the _displayName_ string, used for debug. There's also the _forceUpdate_ API that forces the component render without checking _shouldComponentUpdate_ result.

```js
component.forceUpdate(callback)
```

- Lifecycle

Lifecycles are phases related to the component life, each one has special methods available to use.

- Mounting
  In this phase the component is begin mounted in the DOM, it's ideal to request and inicialize data.
      *Available methods:*

          - constructor
          - static getDerivedStateFromProps
          - render
          - componentDidMount
- Updating
       Phase where state or props are updated.

       *Available methods:*

           - static getDerivedStateFromProps
           - shouldComponentUpdate
           - render
           - getSnapshotBeforeUpdate
           - componentDidUpdate

- Unmounting

       Component will be removed from DOM.

       *Available methods:*

           - componentWillUnmount

- Error handling

In this phase errors are handled, the errors could be from render, lifecycle methods our a children constructor.

        *Available methods:*

            - static getDerivedStateFromError
            - componentDidCatch


- Properties(props)

The components properties, more known as props, are elements passed down from parent to child. They can be from any type, since it's not necessary to specify the type, only their identification.

In class components you have to inicialize them inside the constructor, this way the _this_ will be correctly referenced and the access to them will be allowed.

```js
    constructor(super) {
        super(props);
    }
```

- State

The state is responsible to store data inside inside a component, triggering interface updates. It's asynchronous, so it should not be directly updated since the new value will only be available at the next update.

It's need to be initialised in class based components, being an object that is changed through the setState function. This function gets the name and value and appends it to the existing object. SetState also accepts that a function will be received that will update the state and a callback to be performed after the state has been set.

```js
    constructor(props){
        super(props);
        this.state: {
            message: 'Hello'
        }
    }

    this.setState({ name: 'Person' });
    this.setState(state => ({name: 'Person'}), callback);

```

In functional components, the state is initialised and updated using the hook useState, this hook receives a parameter as the initial value and returns an array with the variable that will hold the state and the function that will update it.

```js
let [message, setMessage] = useState("Hello")
let [state, setState] = useState({ message: "Hello", name: "Person" })
```

**7. Differences to React Native**

While ReactJs is a library, React Native is a framework intended to solve mobile device issues when building native applications. React native compiles to native components, rendering using the native API.

Both have different syntax, React.js uses javascript, whereas RN uses its own syntax.
