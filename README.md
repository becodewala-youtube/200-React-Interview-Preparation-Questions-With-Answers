# React-Interview-Preparation🔥🔥




##  1) What is React, and how is it different from other frameworks?
- React is a JavaScript library for building user interfaces, developed by Facebook. It focuses only on the view layer and provides tools for creating reusable UI components. Unlike full-fledged frameworks like Angular, which include built-in tools for routing and state management, React relies on external libraries (e.g., React Router for routing, Redux for state management).
Example:
```bash
import React from 'react';
function App() {
  return <h1>Hello, React!</h1>;
}
export default App;
```
## 2)Why use React.js for front-end development?
- Component-based architecture: Helps build reusable and maintainable UI components.
- Virtual DOM: Enhances performance by minimizing direct manipulation of the real DOM.
- Rich Ecosystem: Libraries like Redux and React Router provide additional capabilities.
#### Example:
- A button component can be reused:
```bash
function Button({ label }) {
  return <button>{label}</button>;
}
// Reused multiple times
<Button label="Save" />
<Button label="Cancel" />
```
## 3)Explain the concept of the Virtual DOM.
- The Virtual DOM is a lightweight in-memory representation of the real DOM. When the UI updates, React calculates the difference (called diffing) between the current and new Virtual DOM and updates only the changed parts in the real DOM. This reduces the performance cost of DOM manipulation.
#### Example:
- If you update only one item in a list, React avoids re-rendering the entire list and updates just that item.
## 4) What is JSX, and why is it used in React?
- JSX is a syntax extension of JavaScript that looks like HTML. It’s used in React because it makes code more readable and easier to write. JSX gets transpiled into React.createElement calls, which create React elements.
#### Example:
```bash
const element = <h1>Hello, World!</h1>; // JSX
```
#### Transpiled to:
```bash
const element = React.createElement('h1', null, 'Hello, World!');
```
## 5) What is a React component?
- A React component is a reusable piece of UI logic and markup. It can be a functional component (simpler) or a class component (more complex).
#### Example:
```bash
// Functional Component
function Welcome() {
  return <h1>Welcome to React!</h1>;
}

// Class Component
class Welcome extends React.Component {
  render() {
    return <h1>Welcome to React!</h1>;
  }
}
```
## 6) Differentiate between functional and class components.
#### Functional components:
- Simpler, written as functions.
- Use React hooks like useState and useEffect to handle state and lifecycle methods.
#### Class components:
- Written as ES6 classes.
- Use state and lifecycle methods like componentDidMount.
#### Example:
```bash
// Functional Component with Hooks
function Counter() {
  const [count, setCount] = React.useState(0);
  return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
}

// Class Component
class Counter extends React.Component {
  state = { count: 0 };
  increment = () => this.setState({ count: this.state.count + 1 });
  render() {
    return <button onClick={this.increment}>Count: {this.state.count}</button>;
  }
}
```
## 7) What is the role of render() in a class component?
- The render() method defines what to display in the UI. It returns JSX.
#### Example:
```bash
class App extends React.Component {
  render() {
    return <h1>Hello, World!</h1>;
  }
}
```
## 8) What is the difference between state and props?
### State:

- Local to a component and mutable.
- Defined using useState (functional components) or this.state (class components).
### Props:

- Passed from parent to child components.
- Immutable in the child component.
#### Example:
```bash
function Child({ message }) {
  return <h1>{message}</h1>; // Uses props
}

function Parent() {
  return <Child message="Hello from Parent" />;
}
```
## 9) How do you pass data between parent and child components?
- Data is passed via props. For passing functions, you can also use callback props.
#### Example:
```bash
function Parent() {
  const showAlert = () => alert('Button clicked!');
  return <Child onClick={showAlert} />;
}

function Child({ onClick }) {
  return <button onClick={onClick}>Click Me</button>;
}
```
## 10) What are React keys, and why are they important?
- Keys help React identify which items in a list have changed, preventing unnecessary re-renders.
#### Example:
```bash
const items = ['Apple', 'Banana', 'Cherry'];
items.map((item, index) => <li key={index}>{item}</li>);
```
## 11) How do you handle events in React?
- Events are handled using camelCase attributes and event handler functions.
#### Example:
```bash
function App() {
  const handleClick = () => alert('Button Clicked!');
  return <button onClick={handleClick}>Click Me</button>;
}
```
## 12) What is two-way binding in React?
- Two-way binding means synchronizing data between the component’s state and the UI. React does not have built-in two-way binding; you implement it manually using onChange and value.
#### Example:
```bash
function App() {
  const [text, setText] = React.useState('');
  return <input value={text} onChange={(e) => setText(e.target.value)} />;
}
```
## 13) What are React fragments, and why are they used?
- Fragments let you group elements without adding extra nodes to the DOM.
#### Example:

```bash
<>
  <h1>Title</h1>
  <p>Paragraph</p>
</>
```
## 14) Explain controlled vs. uncontrolled components.
- Controlled components: The value is controlled by React state.
- Uncontrolled components: The value is controlled by the DOM.
#### Example (Controlled):

```bash
function App() {
  const [value, setValue] = React.useState('');
  return <input value={value} onChange={(e) => setValue(e.target.value)} />;
}
```
#### Example (Uncontrolled):

```bash
function App() {
  const inputRef = React.useRef();
  return <input ref={inputRef} />;
}]
```

## 15) How do you implement forms in React?
- Forms are implemented using controlled components to track the input values.
#### Example:

```bash
function Form() {
  const [name, setName] = React.useState('');
  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Hello, ${name}!`);
  };
  return (
    <form onSubmit={handleSubmit}>
      <input value={name} onChange={(e) => setName(e.target.value)} />
      <button type="submit">Submit</button>
    </form>
  );
}
```
## 16) What is defaultProps, and how is it used?
- defaultProps provides default values for props if none are supplied.
#### Example:

```bash
function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
}
Greeting.defaultProps = { name: 'Guest' };
````
## 17) What is propTypes, and why is it used?
- propTypes validate the types of props a component receives. It’s useful for debugging.
#### Example:

```bash
Greeting.propTypes = { name: PropTypes.string.isRequired };
```
## 18) Explain the React component lifecycle.
- Mounting: Component is created (componentDidMount).
- Updating: Props or state change -(componentDidUpdate).
- Unmounting: Component is removed (componentWillUnmount).
#### Example:

```bash
class App extends React.Component {
  componentDidMount() {
    console.log('Mounted');
  }
  componentWillUnmount() {
    console.log('Unmounted');
  }
  render() {
    return <h1>Hello</h1>;
  }
}
```
## 19) What is setState, and how does it work?
- setState updates the component’s state and triggers a re-render. It works asynchronously to batch updates.
#### Example:

```bash
this.setState({ count: this.state.count + 1 });
```
## 20) Why is it important to use an updater function in setState?
- When multiple state updates happen, the previous state might not be immediately available. The updater function ensures updates are based on the latest state.
#### Example:

```bash
this.setState((prevState) => ({ count: prevState.count + 1 }));
```
## 21) What are React refs, and why are they used?
- Refs provide a way to access DOM elements or React elements directly without re-rendering the component.
- Use Cases: Managing focus, triggering animations, or integrating third-party libraries.
#### Example:

```bash
function App() {
  const inputRef = React.useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus Input</button>
    </>
  );
}
```
## 22) How does React handle DOM updates efficiently?
- React uses the Virtual DOM to optimize updates. It compares the current Virtual DOM with the previous one using a process called diffing. Only the changed parts of the real DOM are updated.

#### Example:
- When updating a list, React will only update the changed list items instead of re-rendering the entire list.

## 23) What are Higher-Order Components (HOCs)?
- An HOC is a function that takes a component and returns a new component, often used to share logic between components.
#### Example:

```bash
function withLogger(WrappedComponent) {
  return function EnhancedComponent(props) {
    console.log('Props:', props);
    return <WrappedComponent {...props} />;
  };
}

const ButtonWithLogger = withLogger(Button);
```

## 24) What are CSS modules in React?
- CSS Modules allow you to scope CSS locally to a component to avoid naming conflicts.
#### Example:

```bash
/* styles.module.css */
.title {
  color: green;
}
```
```bash
import styles from './styles.module.css';
function App() {
  return <h1 className={styles.title}>Scoped Style</h1>;
}
```
## 25) What is the difference between componentDidMount and componentWillUnmount?
- componentDidMount: Runs after the component is mounted. Used for data fetching or subscriptions.
- componentWillUnmount: Runs before the component is removed. Used for cleanup (e.g., removing event listeners).
#### Example:
```bash
class App extends React.Component {
  componentDidMount() {
    console.log('Mounted');
  }
  componentWillUnmount() {
    console.log('Unmounting');
  }
  render() {
    return <h1>Hello</h1>;
  }
}
```
## 26) Explain the significance of React.StrictMode.
- StrictMode highlights potential problems in an application by running additional checks and warnings in development mode.
#### Example:

```bash
<React.StrictMode>
  <App />
</React.StrictMode>
```
## 27) How does React handle conditional rendering?
#### React handles conditional rendering using:

- Ternary operators
- Logical && operator
- If-else statements
#### Example:

```bash
function App({ isLoggedIn }) {
  return isLoggedIn ? <h1>Welcome</h1> : <h1>Please Log In</h1>;
}
```
## 28) How do you share data between sibling components?
- Data can be shared using a common parent component and passing props. Alternatively, you can use state management like Redux or Context API.
#### Example:

```bash
function Parent() {
  const [data, setData] = React.useState('Hello');
  return (
    <>
      <Child1 setData={setData} />
      <Child2 data={data} />
    </>
  );
}
```
## 29) What is a React Portal?
- React Portals allow rendering components outside the DOM hierarchy of the parent.
#### Example:

```bash
ReactDOM.createPortal(
  <div>Portal Content</div>,
  document.getElementById('portal-root')
);
```
## 30) Explain lazy loading in React.
- Lazy loading delays loading components until they’re needed, improving performance.
#### Example:

```bash
const LazyComponent = lazy(() => import('./LazyComponent'));
function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```
## 31) What is React.memo, and why is it used?
- React.memo prevents unnecessary re-renders by memoizing the component unless its props change.
#### Example:

```bash
const MemoizedComponent = React.memo(({ count }) => {
  console.log('Rendered');
  return <div>{count}</div>;
});
```
## 32) How do you prevent unnecessary re-renders in React?
- Use React.memo for functional components.
- Use shouldComponentUpdate or PureComponent in class components.
- Avoid inline functions/objects as props.
- Use useMemo or useCallback for optimization.
#### Example (useCallback):
```bash
const handleClick = React.useCallback(() => { console.log('Clicked'); }, []);
```
## 33) How do you implement code splitting in React?
- Code splitting breaks large bundles into smaller chunks using React.lazy and dynamic imports.
#### Example:

```bash
const Component = React.lazy(() => import('./Component'));
```
## 34) What is the difference between a library and a framework? Is React a library or framework?
- Library: A collection of tools to help build applications (React).
- Framework: Provides a complete structure for application development (Angular).
- React is a library focused on UI.
## 35) How do you fetch data in React applications?
- Data can be fetched using fetch, Axios, or third-party libraries. Typically, data fetching is done in useEffect or lifecycle methods.
#### Example:

```bash
function App() {
  const [data, setData] = React.useState([]);
  React.useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then((res) => res.json())
      .then((data) => setData(data));
  }, []);
  return <ul>{data.map((item) => <li key={item.id}>{item.title}</li>)}</ul>;
}
```
## 36)Explain the purpose of the useEffect hook.
- useEffect manages side effects in functional components, like fetching data, updating the DOM, or subscribing to events. It runs after the component renders or when dependencies change.

#### Example:

```bash
import { useEffect, useState } from 'react';

function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []); // Empty array ensures it runs once after initial render

  return <ul>{data.map((item) => <li key={item.id}>{item.title}</li>)}</ul>;
}
```
## 37)How do you use React Router?
- React Router allows navigation between different pages in a React app. It provides components like Routes, Route, and Link for routing.

#### Example:

```bash
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}
```
## 38) How do you manage routing for nested components?
- Use nested <Route> elements within parent routes to define nested routing.

#### Example:

```bash
<Routes>
  <Route path="dashboard" element={<Dashboard />}>
    <Route path="profile" element={<Profile />} />
    <Route path="settings" element={<Settings />} />
  </Route>
</Routes>;
```
- Navigating to /dashboard/profile will render Dashboard and Profile.

## 39) What is the purpose of useParams in React Router?
- useParams retrieves route parameters from the URL.

#### Example:

```bash
import { useParams } from 'react-router-dom';

function Post() {
  const { id } = useParams();
  return <h1>Post ID: {id}</h1>;
}

// Route definition:
<Route path="/post/:id" element={<Post />} />;
```
- Navigating to /post/123 will display Post ID: 123.

## 40) How do you handle redirection in React?
- Use the Navigate component to redirect users programmatically.

#### Example:

```bash
import { Navigate } from 'react-router-dom';

function Protected({ isLoggedIn }) {
  return isLoggedIn ? <Dashboard /> : <Navigate to="/login" />;
}
```
## 40) How do you handle redirection in React?
- Use the Navigate component to redirect users programmatically.

#### Example:

```bash
import { Navigate } from 'react-router-dom';

function Protected({ isLoggedIn }) {
  return isLoggedIn ? <Dashboard /> : <Navigate to="/login" />;
}
```
## 41) What are dynamic routes in React Router?
- Dynamic routes contain variables that match parts of the URL.

#### Example:

```bash
<Route path="/user/:userId" element={<User />} />;
```
- Here, :userId is a dynamic segment.

## 42) How do you add default routes in a React app?
- Use the index attribute for default nested routes or specify a catch-all fallback route.

#### Example:

```bash
<Routes>
  <Route path="/" element={<Layout />}>
    <Route index element={<Home />} />
    <Route path="about" element={<About />} />
  </Route>
</Routes>
```
- Navigating to / renders Home.

## 43) What is the significance of exact routes in React Router?
- exact ensures the route matches the path precisely, preventing partial matches. It was used in React Router v5 but is no longer needed in v6 due to improved matching logic.

- React Router v5 Example:

```bash
<Route exact path="/" component={Home} />
<Route path="/about" component={About} />
```
## 44) How do you handle 404 pages in React?
- Use a catch-all route with a wildcard * path to display a 404 page for unmatched routes.

#### Example:

```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="*" element={<NotFound />} />
</Routes>
```
- Navigating to a nonexistent route will render the NotFound component.

## 45) What are React hooks, and why were they introduced?
- React hooks are functions introduced in React 16.8 to allow functional components to use state and lifecycle features, which were previously only available in class components. They make code cleaner, reduce boilerplate, and promote better organization of logic through reusable custom hooks.

#### Why Introduced?
- Simplify state management in functional components.
- Encourage sharing logic without complex patterns like higher-order components (HOCs).
- Eliminate the need for classes.
#### Example:

```bash
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0); // Declare a state variable and its updater function

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```
- Here, useState allows us to add state to a functional component, simplifying the implementation.
## 46) What is the difference between useState and useReducer?
 |Feature|	useState|	useReducer| | 
 |------| ----|----------|-
Purpose|	Manage simple states.|	Manage complex states with logic.
Syntax|	const [state, setState] = useState();|	const [state, dispatch] = useReducer();
Usage|	For counters, toggles, etc.	|For forms, app-level states, etc.|
Example|	Increment a counter.|	Handle complex state changes with actions.

#### Example for useReducer:

```bash
import React, { useReducer } from 'react';

const reducer = (state, action) => {
  switch (action.type) {
    case 'increment': return state + 1;
    case 'decrement': return state - 1;
    default: return state;
  }
};

function Counter() {
  const [count, dispatch] = useReducer(reducer, 0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
    </div>
  );
}
```
- useReducer is ideal for managing state transitions in larger applications.

## 47) How does the useRef hook work in React?
- useRef provides a way to persist values or references across renders without triggering re-renders. It’s often used for accessing DOM elements or storing mutable values.

#### Use Cases:
- Access DOM nodes directly.
- Store mutable values that do not trigger re-renders.
#### Example:

```bash
import React, { useRef } from 'react';

function InputFocus() {
  const inputRef = useRef(null);

  const handleFocus = () => {
    inputRef.current.focus(); // Directly access DOM node
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={handleFocus}>Focus Input</button>
    </div>
  );
}
```
- Here, useRef stores a reference to the input element and provides direct access to it.

## 48) What is the difference between useEffect and useLayoutEffect?
|Feature |	useEffect|	useLayoutEffect| |
 |------| ----|----------|-
When it Runs|	After rendering and painting.|	After rendering but before painting.
Use Cases|	Data fetching, subscriptions, logging.|	DOM manipulations, measurements, animations.
Performance Impact|	Less blocking of UI updates.|	Blocks painting until work is done.

#### Example of useLayoutEffect:

```bash
import React, { useLayoutEffect, useRef } from 'react';

function MeasureComponent() {
  const divRef = useRef(null);

  useLayoutEffect(() => {
    console.log(divRef.current.getBoundingClientRect()); // Accurate measurement
  });

  return <div ref={divRef}>Measure Me</div>;
}
```
## 49) How do you optimize performance in React applications?
#### Performance optimization ensures a smoother user experience and faster interactions.

#### Strategies:
- React.memo: Prevents unnecessary re-renders by memoizing components.
- useCallback and useMemo: Avoids unnecessary re-creation of functions and values.
- Code Splitting: Dynamically loads only required parts of the app.
- Virtualization: Renders only visible items in large lists (e.g., react-window).
- Avoid Reconciliation: Use key attributes and avoid changing component trees unnecessarily.
#### Example with React.memo:

```bash
import React from 'react';

const Child = React.memo(({ data }) => {
  console.log('Child re-rendered');
  return <p>{data}</p>;
});

function Parent() {
  const [count, setCount] = React.useState(0);

  return (
    <div>
      <Child data="Static Data" />
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```
- Here, Child won’t re-render unless its data prop changes.

## 50) What is React Context API, and how is it used?
- The Context API allows components to share data without passing props down every level.

#### Use Cases:
- Global themes.
- User authentication data.
- App-wide configuration.
#### Example:

```bash
import React, { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Child />
    </ThemeContext.Provider>
  );
}

function Child() {
  const theme = useContext(ThemeContext);
  return <p>Current Theme: {theme}</p>;
}
````
## 51) How do you handle global state in React?
- Global state can be managed using tools like the Context API or Redux.

#### Example with Context API:

```bash
const GlobalState = createContext();

function App() {
  const [user, setUser] = useState(null);

  return (
    <GlobalState.Provider value={{ user, setUser }}>
      <Child />
    </GlobalState.Provider>
  );
}
```
## 52) What is Redux, and why is it used with React?
- Redux is a state management library that provides a predictable way to manage state across your application. It ensures the state is centralized, immutable, and debug-friendly.

#### Core Concepts:
- Store: Single source of truth for application state.
- Action: Describes what to do.
- Reducer: Pure function defining how state changes in response to actions.
## 53) What are React.lazy and Suspense used for?
- React.lazy enables dynamic import of components for code splitting, while Suspense handles the loading state.

#### Example:

```bash
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}
```
- This setup dynamically loads LazyComponent and shows a fallback until it's ready.

## 54)What are the core concepts of Redux?
### Redux follows three core principles:

#### Single Source of Truth:
- The entire state of the application is stored in one central location, called the store.
#### Example:

```bash
const initialState = { counter: 0 };
const store = createStore(reducer, initialState);
```

#### State is Read-Only:
- State can only be changed by dispatching actions, making changes predictable.
#### Example:

```bash
store.dispatch({ type: 'INCREMENT' });
```
#### Changes are Made with Pure Functions (Reducers):
- Reducers are pure functions that take the current state and an action, and return the next state.
#### Example:

```bash
function reducer(state = { counter: 0 }, action) {
  switch (action.type) {
    case 'INCREMENT': return { counter: state.counter + 1 };
    default: return state;
  }
}
```
## 55) What is an action in Redux?
- An action is a plain JavaScript object that describes what happened. It must have a type property that indicates the action's intent.

#### Example:

```bash
const incrementAction = { type: 'INCREMENT' };
store.dispatch(incrementAction);
```
- Actions can also carry additional data (called payload):

```bash
const addTodoAction = { type: 'ADD_TODO', payload: 'Learn Redux' };
```
## 56) What is a reducer in Redux?
- A reducer is a pure function that takes the current state and an action, and returns a new state. It specifies how the state should change in response to actions.

#### Example:

```bash
function counterReducer(state = { count: 0 }, action) {
  switch (action.type) {
    case 'INCREMENT': return { count: state.count + 1 };
    case 'DECREMENT': return { count: state.count - 1 };
    default: return state;
  }
}
```
## 57) Explain the role of the Redux store.
- The store holds the entire application state. It provides methods to:

- Get the current state (store.getState()).
- Dispatch actions (store.dispatch(action)).
- Subscribe to state changes (store.subscribe(callback)).
#### Example:

```bash
import { createStore } from 'redux';

const store = createStore(counterReducer);
store.subscribe(() => console.log(store.getState()));

store.dispatch({ type: 'INCREMENT' }); // Logs: { count: 1 }
```
## 58) How do you connect Redux with React components?
- Use the connect function from react-redux to map the Redux state and dispatch to React component props.

#### Example:

```bash
import { connect } from 'react-redux';

function Counter({ count, increment }) {
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

const mapStateToProps = (state) => ({ count: state.count });
const mapDispatchToProps = (dispatch) => ({
  increment: () => dispatch({ type: 'INCREMENT' }),
});

export default connect(mapStateToProps, mapDispatchToProps)(Counter);
```
## 59) What is middleware in Redux?
- Middleware allows you to customize and extend Redux's behavior. It sits between the action dispatch and the reducer, enabling features like logging, asynchronous actions, or API calls.

#### Example with Redux Thunk:

```bash
const loggerMiddleware = (store) => (next) => (action) => {
  console.log('Dispatching:', action);
  next(action);
};
```
## 60) Explain the purpose of mapStateToProps and mapDispatchToProps.
- mapStateToProps: Maps Redux state to component props.
#### Example:

```bash
const mapStateToProps = (state) => ({ count: state.count });
```
- mapDispatchToProps: Maps dispatch functions to component props.
#### Example:

```bash
const mapDispatchToProps = (dispatch) => ({
  increment: () => dispatch({ type: 'INCREMENT' }),
});
```
## 61) What are thunks in Redux?
- A thunk is a middleware function that allows you to write asynchronous logic that interacts with the Redux store. With Redux Thunk, actions can return functions instead of objects.

- Example with Redux Thunk:

```bash
const fetchData = () => {
  return async (dispatch) => {
    dispatch({ type: 'FETCH_START' });
    const data = await fetch('/api/data').then((res) => res.json());
    dispatch({ type: 'FETCH_SUCCESS', payload: data });
  };
};
```
## 62) How do you handle asynchronous actions in Redux?
- You handle asynchronous actions using middleware like Redux Thunk or Redux Saga. These middleware tools enable actions to perform async operations before dispatching.

#### Example with Thunk:

```bash
store.dispatch(fetchData());
```

## 63) How do you implement error boundaries in React?
- Error boundaries are used to catch JavaScript errors in child components and display a fallback UI instead of crashing the entire app. They catch rendering errors, lifecycle method errors, and errors thrown in constructors.

#### Example Implementation:

```bash
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true }; // Update state so the next render shows fallback UI.
  }

  componentDidCatch(error, errorInfo) {
    // Log error details, e.g., to a monitoring service.
    console.error("Error caught by boundary:", error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}

// Usage
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```
- Error boundaries only work in class components, not in functional components.

## 64) What is React Fiber?
- React Fiber is React’s reconciliation engine introduced in version 16. It optimizes rendering by dividing the rendering process into small chunks, enabling React to pause, prioritize, and resume work efficiently.

#### Features of Fiber:

- Time-slicing: Improves rendering for high-priority tasks.
- Concurrency: Manages animations and transitions smoothly.
## 65) Explain reconciliation in React.
- Reconciliation is React’s algorithm for efficiently updating the DOM. React creates a Virtual DOM and compares it with the previous state (diffing). Only the differences are updated in the real DOM.

- Example: If a button’s text changes from "Click Me" to "Clicked", React:

- Creates a new Virtual DOM tree.
- Finds the difference (text change).
- Updates only the text node instead of re-rendering the entire DOM tree.
## 66) How does React handle hydration?
- Hydration happens in server-side rendering (SSR). It’s when React takes over static HTML from the server and attaches event listeners to make it interactive.

#### Example:

```bash
ReactDOM.hydrate(<App />, document.getElementById('root'));
```
- Hydration is efficient because it reuses the server-rendered DOM structure instead of rebuilding it.

## 67) What is server-side rendering (SSR) in React?
- In SSR, the React app is rendered on the server, and the generated HTML is sent to the client. This improves SEO and initial load performance.

#### Example (Next.js):

```bash
export async function getServerSideProps() {
  const data = await fetch('https://api.example.com');
  return { props: { data } };
}

export default function Page({ data }) {
  return <div>{data.message}</div>;
}
```
## 68) What is static site generation (SSG) in React?
- SSG pre-builds static HTML pages at build time. It’s suitable for content that rarely changes (e.g., blogs).

#### Example (Next.js):

```
export async function getStaticProps() {
  const data = await fetch('https://api.example.com');
  return { props: { data } };
}

export default function Page({ data }) {
  return <div>{data.message}</div>;
}
```
## 69) What are React Suspense and Concurrent Mode?
- Suspense: Allows React to "suspend" rendering until some asynchronous data (like a lazy-loaded component) is ready.
- Concurrent Mode: Enhances performance by breaking tasks into smaller units and prioritizing them.
#### Example of Suspense:

```bash
import React, { Suspense, lazy } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}
```
## 70) How do you implement pagination in React?
- Pagination divides data into pages, allowing users to navigate through them.

#### Example:

```bash
const itemsPerPage = 5;
const [currentPage, setCurrentPage] = useState(1);
const currentItems = data.slice(
  (currentPage - 1) * itemsPerPage,
  currentPage * itemsPerPage
);

return (
  <div>
    {currentItems.map(item => (
      <p key={item.id}>{item.name}</p>
    ))}
    <button onClick={() => setCurrentPage(currentPage - 1)}>Previous</button>
    <button onClick={() => setCurrentPage(currentPage + 1)}>Next</button>
  </div>
);
```

## 71) How do you implement infinite scrolling in React?
- Infinite scrolling loads more data when the user scrolls near the bottom of the page.

#### Example:

```bash
useEffect(() => {
  const handleScroll = () => {
    if (window.innerHeight + document.documentElement.scrollTop >= document.documentElement.offsetHeight) {
      loadMoreData();
    }
  };
  window.addEventListener('scroll', handleScroll);
  return () => window.removeEventListener('scroll', handleScroll);
}, []);
```
## 72) What is the purpose of the useCallback hook?
- useCallback memoizes a function to avoid unnecessary re-creations during re-renders.

#### Example:

```bash
const memoizedFunction = useCallback(() => {
  doSomething();
}, [dependency]);
```
## 73) How does the useMemo hook work in React?
- useMemo memoizes the result of a computation to optimize performance.

#### Example:

```bash
const computedValue = useMemo(() => expensiveCalculation(data), [data]);
```
## 74) What are custom hooks in React? Provide an example.
- Custom hooks encapsulate reusable logic.

#### Example:

```bash
function useFetch(url) {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url).then((res) => res.json()).then(setData);
  }, [url]);

  return data;
}

const data = useFetch('/api/data');
```
## 75) How do you handle authentication in React?
- Use libraries like Firebase, Auth0, or JWT for authentication. Store tokens in cookies or local storage and validate them on requests.

## 76) What are JWTs, and how do they work in React?
- JWTs (JSON Web Tokens) are a compact, self-contained way to represent authentication information.

#### Example:

- After login, the server issues a JWT.
- The client stores the token and includes it in headers for authenticated requests.
```bash
fetch('/protected', {
  headers: { Authorization: `Bearer ${token}` }
});
```
## 77) How do you implement role-based access control in React?
- Check roles before rendering components.

#### Example:

```bash
function ProtectedComponent({ role }) {
  return role === 'admin' ? <AdminPanel /> : <Unauthorized />;
}
```
## 78) How do you implement drag-and-drop in React?
- Use libraries like react-dnd or HTML5 drag-and-drop API.

#### Example:

```bash
<div draggable onDragStart={handleDrag}>Drag Me</div>
```

## 79) How do you debug React applications?
- React DevTools: Inspect the component tree and props/state.
- Console logs: Use console.log() for debugging specific values.
- Error boundaries: Catch errors in rendering or lifecycle methods.
- Debugger: Use the browser's debugging tools or debugger keyword in your code.
- Profiler: Analyze rendering performance with React DevTools.
## 80) What tools are commonly used to test React applications?
- Jest: For unit testing.
- React Testing Library: For component testing.
- Cypress: For end-to-end testing.
- Enzyme: For shallow and full rendering tests.



## 81) How do you implement error boundaries in React?
- Error boundaries catch JavaScript errors in their child components, preventing crashes and displaying fallback UIs instead.

#### Key Points:
- Can only catch errors in the rendering phase, lifecycle methods, and constructors.
- Cannot catch errors in event handlers.
#### Example:
```bash
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Update state to show fallback UI
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    // Log the error (optional)
    console.error("Error:", error, "Info:", info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}

// Usage
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```
## 82) What is React Fiber?
- React Fiber is the reimplementation of React’s rendering engine, introduced in React 16. It makes updates faster and smoother.

#### Key Features:
- Time-Slicing: Breaks rendering work into chunks for smooth UI rendering.
- Concurrency: Enables React to handle updates like animations and user input efficiently.
#### Example:
- React Fiber improves scenarios where frequent updates, like typing or animations, happen.

## 83) Explain reconciliation in React.
- Reconciliation is React’s process for determining what changes are needed in the DOM. It uses a diffing algorithm to identify minimal updates.

#### Example:
- If a button changes its text:

```bash
function App() {
  return <button>Click Me</button>;
}
// Updated to:
function App() {
  return <button>Clicked</button>;
}
// React only updates the button's text instead of re-rendering the entire component.
```
## 84) How does React handle hydration?
- Hydration happens when React attaches event listeners to server-rendered HTML. It’s common in Server-Side Rendering (SSR) to make the static HTML interactive.

#### Example:
```bash
ReactDOM.hydrate(<App />, document.getElementById('root'));
```
#### Why Use Hydration?
- It improves page load speed while still providing React’s interactivity.

## 85) What is server-side rendering (SSR) in React?
- SSR generates the initial HTML on the server, sending it to the browser for rendering. It improves SEO and reduces the time for the page to display.

#### Example (Next.js):
```bash
export async function getServerSideProps() {
  const data = await fetch('/api/data');
  return { props: { data } };
}

function Page({ data }) {
  return <div>{data}</div>;
}
```
## 86) How does SSR differ from client-side rendering (CSR)?
### SSR	
- Initial HTML is generated on the server.
- Faster initial load time.
- Better SEO.
### CSR
-	HTML is generated in the browser via JavaScript.
- Slower initial load but faster subsequent interactions.
-	SEO may require extra configuration.
## 87) What is static site generation (SSG) in React?
- SSG pre-renders pages at build time, creating static HTML files. It’s faster than SSR for content that rarely changes.

#### Example (Next.js):
```bash
export async function getStaticProps() {
  const data = await fetch('/api/data');
  return { props: { data } };
}

function Page({ data }) {
  return <div>{data}</div>;
}
```
## 88) What are React Suspense and Concurrent Mode?
- Suspense: Allows React to wait for asynchronous operations (like lazy loading) and show a fallback UI.
- Concurrent Mode: Improves responsiveness by letting React handle multiple tasks simultaneously.
#### Example with Suspense:
```bash
const LazyComponent = React.lazy(() => import('./MyComponent'));

<Suspense fallback={<div>Loading...</div>}>
  <LazyComponent />
</Suspense>
```
## 89) How do you implement pagination in React?
- Pagination splits data into smaller chunks for easier navigation.

#### Example:
```bash
function PaginatedList({ items, itemsPerPage }) {
  const [currentPage, setCurrentPage] = useState(1);
  const startIndex = (currentPage - 1) * itemsPerPage;
  const currentItems = items.slice(startIndex, startIndex + itemsPerPage);

  return (
    <div>
      {currentItems.map((item) => (
        <div key={item.id}>{item.name}</div>
      ))}
      <button onClick={() => setCurrentPage((prev) => prev - 1)}>Previous</button>
      <button onClick={() => setCurrentPage((prev) => prev + 1)}>Next</button>
    </div>
  );
}
```
## 90)How do you test React components using Jest?

- Jest is a JavaScript testing framework used for unit tests, integration tests, and snapshots in React applications.

#### Testing React Components:
- Use Jest with @testing-library/react for rendering components and testing their behavior.
#### Example:
```bash
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import Button from './Button';

test('renders the button and checks click event', () => {
  const handleClick = jest.fn();
  render(<Button onClick={handleClick}>Click Me</Button>);

  // Assert text is rendered
  expect(screen.getByText('Click Me')).toBeInTheDocument();

  // Simulate click event
  userEvent.click(screen.getByText('Click Me'));
  expect(handleClick).toHaveBeenCalledTimes(1);
});
```

## 91) What is the purpose of Enzyme in React testing?
#### Purpose:
- Enzyme, developed by Airbnb, is a React testing library that allows testing React components' output, state, and behavior. It provides shallow rendering, full DOM rendering, and static rendering.

#### Example:
```bash
import { shallow } from 'enzyme';
import App from './App';

test('renders header', () => {
  const wrapper = shallow(<App />);
  expect(wrapper.find('h1').text()).toEqual('Welcome to My App');
});
```
#### Key Difference:
- While Enzyme tests specific component internals, React Testing Library focuses on user behavior.

## 92) How do you implement Snapshot testing in React?
#### Snapshot Testing Overview:
- Snapshot testing ensures UI consistency by comparing the rendered output of a component to a saved "snapshot".

#### Example:
```bash
import { render } from '@testing-library/react';
import Header from './Header';

test('renders correctly', () => {
  const { asFragment } = render(<Header />);
  expect(asFragment()).toMatchSnapshot();
});
```
- When changes occur, the test fails, prompting you to update the snapshot.

## 93) How do you integrate TypeScript with React?
#### Steps:
- Install TypeScript and type definitions:

```bash
npm install typescript @types/react @types/react-dom
```
- Rename .js files to .tsx.

- Add a tsconfig.json:

```bash
{
  "compilerOptions": {
    "jsx": "react",
    "strict": true
  }
}
```
#### Example:
```bash
type Props = { message: string };

const Greeting: React.FC<Props> = ({ message }) => <h1>{message}</h1>;
```
## 94) What are the benefits of using TypeScript in React projects?
- Type Safety: Prevents runtime errors by catching type issues during development.
- Better Developer Experience: Autocompletion, better refactoring, and clear documentation.
- Early Bug Detection: Errors are identified at compile time.
- Improved Code Readability: Types make the codebase easier to understand.

## 95) How do you manage environment variables in React?
#### Steps:
- Create a .env file in the root directory:

```bash
REACT_APP_API_URL=https://api.example.com
```
- Access the variable in your code:

```bash
console.log(process.env.REACT_APP_API_URL);
```


## 96) How do you implement a theme switcher (dark mode) in React?
#### Example:
```bash
import { useState } from 'react';

function App() {
  const [theme, setTheme] = useState('light');

  return (
    <div className={theme}>
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Switch Theme
      </button>
    </div>
  );
}
```
#### CSS:

```bash
.light { background: white; color: black; }
.dark { background: black; color: white; }
```

## 97) How do you handle file uploads in React?
#### Example:
```bash
function FileUpload() {
  const handleUpload = (event) => {
    const file = event.target.files[0];
    const formData = new FormData();
    formData.append('file', file);

    fetch('/upload', { method: 'POST', body: formData });
  };

  return <input type="file" onChange={handleUpload} />;
}
```
## 98)How do you implement routing in React applications?

- Routing in React is managed using libraries like React Router, allowing navigation between different components or pages without refreshing the browser.

#### Example:
- Install React Router:

```bash
npm install react-router-dom
```
- Set up routing in your app:

```bash
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './Home';
import About from './About';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```
#### Here:

- / renders the Home component.
- /about renders the About component.
## 99) What is the role of the <Switch> component in React Router?

- In React Router v5, <Switch> was used to render the first child <Route> that matches the URL. It ensures only one route is rendered at a time.

#### Example:
```bash
import { BrowserRouter as Router, Switch, Route } from 'react-router-dom';

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/about" component={About} />
        <Route path="/" component={Home} />
      </Switch>
    </Router>
  );
}
```
- If the path is /about, the About component is rendered.
React Router v6 replaces <Switch> with <Routes>.
## 100) How do you implement private routes in React?

- Private routes restrict access to specific components/pages based on authentication.

#### Example:
```bash
import { Navigate } from 'react-router-dom';

function PrivateRoute({ children }) {
  const isAuthenticated = !!localStorage.getItem('token'); // Example check

  return isAuthenticated ? children : <Navigate to="/login" />;
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/login" element={<Login />} />
        <Route
          path="/dashboard"
          element={
            <PrivateRoute>
              <Dashboard />
            </PrivateRoute>
          }
        />
      </Routes>
    </BrowserRouter>
  );
}
```

- If the user is authenticated, they access the Dashboard.
- Otherwise, they are redirected to /login.


## 101) What is React StrictMode?

- React.StrictMode is a tool for highlighting potential problems in a React app. It doesn’t render anything visible to the UI but activates additional checks and warnings for its child components.

### Features:
- Detects unsafe lifecycle methods.
- Warns about using deprecated APIs.
- Highlights side effects in useEffect.
#### Example:
```bash
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```
## 102) What is the difference between the useState and useReducer hooks?
| useState|useReducer ||| 
 |------| ----|-------|-
|Simpler API for managing local state.	|Better for complex state logic.
Returns state and a state updater function.	|Returns state and a dispatch function.
Suitable for simple toggles, counters, etc.	|Suitable for managing multiple related state updates.

#### Example:
- Using useState:

```bash
const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>Increment</button>;
```
- Using useReducer:

```bash
const reducer = (state, action) => {
  switch (action.type) {
    case 'increment': return state + 1;
    case 'decrement': return state - 1;
    default: return state;
  }
};

const [count, dispatch] = useReducer(reducer, 0);

<button onClick={() => dispatch({ type: 'increment' })}>Increment</button>;
```
## 103) How does the useContext hook work?

- The useContext hook allows you to consume values from a React Context in functional components without using Consumer.

#### Example:
```bash
const ThemeContext = React.createContext('light');

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  const theme = useContext(ThemeContext);
  return <div>Current theme: {theme}</div>;
}
```
## 104) What is a compound component pattern in React?

- Compound components let you build reusable components where the parent component manages the state and logic while child components share this state.

#### Example:
```bash
function Tabs({ children }) {
  const [activeIndex, setActiveIndex] = useState(0);

  return (
    <div>
      {React.Children.map(children, (child, index) =>
        React.cloneElement(child, {
          isActive: activeIndex === index,
          onClick: () => setActiveIndex(index),
        })
      )}
    </div>
  );
}

function Tab({ isActive, onClick, children }) {
  return <button onClick={onClick} style={{ fontWeight: isActive ? 'bold' : 'normal' }}>{children}</button>;
}

function App() {
  return (
    <Tabs>
      <Tab>Tab 1</Tab>
      <Tab>Tab 2</Tab>
      <Tab>Tab 3</Tab>
    </Tabs>
  );
}
```
## 105) How do you create a reusable component in React?

- Reusable components are designed to work in multiple contexts by accepting props to customize their behavior and appearance.

#### Example:
```bash
function Button({ children, onClick, variant = 'primary' }) {
  const style = variant === 'primary' ? 'btn-primary' : 'btn-secondary';

  return (
    <button className={style} onClick={onClick}>
      {children}
    </button>
  );
}

// Usage
<Button variant="primary" onClick={() => alert('Clicked!')}>Click Me</Button>
<Button variant="secondary" onClick={() => alert('Clicked!')}>Secondary Button</Button>
```
- This Button component can be reused across different parts of the app by changing props like variant or onClick.

## 106)How would you optimize rendering performance in React?

- Optimizing performance involves avoiding unnecessary renders and reducing DOM updates.

### Techniques:
- React.memo: Prevents unnecessary renders for functional components.
- useCallback and useMemo: Optimize inline functions and computed values.
- Code splitting: Load components on demand using React.lazy.
- Virtualization: Render only visible items in a list (e.g., using react-window).
- Avoid anonymous functions: Use memoized callbacks to prevent re-renders.
#### Example:
```bash
const Button = React.memo(({ onClick, children }) => {
  console.log('Button rendered');
  return <button onClick={onClick}>{children}</button>;
});

function App() {
  const [count, setCount] = React.useState(0);
  const increment = React.useCallback(() => setCount((c) => c + 1), []);
  return (
    <div>
      <Button onClick={increment}>Click Me</Button>
    </div>
  );
}
```
## 107)How do you manage dependencies in a large React application?
### Techniques:
- Package.json: Maintain all dependencies with clear versioning.
- Peer dependencies: Define shared dependencies for libraries.
- Monorepos: Use tools like Lerna for multi-package projects.
- npm audit: Regularly check for vulnerabilities.
## 108) How do you implement animations in React?

- Use libraries like React Spring, Framer Motion, or CSS animations.

#### Example:
- With Framer Motion:

```bash
import { motion } from 'framer-motion';

function Box() {
  return (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      transition={{ duration: 0.5 }}
    >
      Animated Box
    </motion.div>
  );
}
```
## 109)How do you implement a drag-and-drop feature in React?

- Use libraries like react-dnd or react-beautiful-dnd.

- With react-beautiful-dnd:

```bash
import { DragDropContext, Droppable, Draggable } from 'react-beautiful-dnd';

const items = [
  { id: '1', text: 'Item 1' },
  { id: '2', text: 'Item 2' },
];

function App() {
  const onDragEnd = (result) => {
    console.log(result);
  };

  return (
    <DragDropContext onDragEnd={onDragEnd}>
      <Droppable droppableId="list">
        {(provided) => (
          <div {...provided.droppableProps} ref={provided.innerRef}>
            {items.map((item, index) => (
              <Draggable key={item.id} draggableId={item.id} index={index}>
                {(provided) => (
                  <div ref={provided.innerRef} {...provided.draggableProps} {...provided.dragHandleProps}>
                    {item.text}
                  </div>
                )}
              </Draggable>
            ))}
            {provided.placeholder}
          </div>
        )}
      </Droppable>
    </DragDropContext>
  );
}
```
## 110) What is the role of CSS-in-JS libraries like styled-components in React?

- CSS-in-JS allows you to write scoped CSS directly in JavaScript files, enabling dynamic styling based on props.

#### Example:
```bash
import styled from 'styled-components';

const Button = styled.button`
  background-color: ${(props) => (props.primary ? 'blue' : 'gray')};
  color: white;
  padding: 10px;
`;

<Button primary>Primary Button</Button>;
<Button>Secondary Button</Button>;
```
## 111)What is the difference between PureComponent and React.memo?
- PureComponent: A class component that performs a shallow comparison of props and state to avoid unnecessary re-renders.
- React.memo: A higher-order function used with functional components for similar optimization by memoizing the component.
#### Example:
- Using PureComponent:

```bash
import React, { PureComponent } from 'react';

class MyComponent extends PureComponent {
  render() {
    console.log('Rendered PureComponent');
    return <div>{this.props.value}</div>;
  }
}
```
- Using React.memo:

```bash
const MyFunctionalComponent = React.memo(({ value }) => {
  console.log('Rendered Memoized Component');
  return <div>{value}</div>;
});
```
#### Key Difference:
- PureComponent works with class components.
- React.memo works with functional components.
## 112) How do you use the useImperativeHandle hook?
- useImperativeHandle customizes the instance value exposed when using React.forwardRef.

#### Example:
```bash
import React, { useRef, forwardRef, useImperativeHandle } from 'react';

const Input = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    },
  }));

  return <input ref={inputRef} />;
});

function App() {
  const inputRef = useRef();

  return (
    <div>
      <Input ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
}
```
## 113) Explain the use of the React.forwardRef function.

- React.forwardRef allows a parent component to pass a ref to a child component.

#### Example:
```bash
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref}>{props.children}</button>
));

function App() {
  const buttonRef = React.createRef();

  return (
    <FancyButton ref={buttonRef}>Click Me</FancyButton>
  );
}
```
## 114) What is the difference between React.lazy and loadable components?

- React.lazy: Built-in React feature for code splitting via dynamic imports.
- Loadable Components: A third-party library with additional features like loading indicators or error handling.
#### Example:
- React.lazy:

```bash
const LazyComponent = React.lazy(() => import('./MyComponent'));

function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```
- Loadable Components:

```bash
import loadable from '@loadable/component';

const LoadableComponent = loadable(() => import('./MyComponent'), {
  fallback: <div>Loading...</div>,
});

function App() {
  return <LoadableComponent />;
}
```
## 115) What are some best practices for structuring a React project?
#### Best Practices:
- Modular structure:
```bash
src/
├── components/
├── pages/
├── services/
├── redux/ or context/
├── utils/
├── styles/
└── App.js
```
- Reusable components: Break down the UI into small, composable components.
- Feature-based folders: Organize files by feature for larger apps.
- State management: Use Context API or Redux for global state.
- Separate concerns: Keep logic (services) separate from components.
## 116) How do you optimize bundle size in React?
#### Techniques:
- Code splitting with React.lazy and React.Suspense.
- Tree shaking to remove unused code.
- Dynamic imports for rarely used modules.
- Use libraries like webpack-bundle-analyzer to analyze and reduce bundle size.
#### Example:
```bash
const LazyComponent = React.lazy(() => import('./LargeComponent'));
```
## 117) How do you handle authentication using Firebase in React?
#### Example:
- Set up Firebase:

```bash
npm install firebase
```
- Initialize Firebase:

```bash
import firebase from 'firebase/app';
import 'firebase/auth';

const firebaseConfig = { apiKey: '...', authDomain: '...' };
firebase.initializeApp(firebaseConfig);
```
- Sign-in Implementation:

```bash
const signInWithGoogle = () => {
  const provider = new firebase.auth.GoogleAuthProvider();
  firebase.auth().signInWithPopup(provider);
};
```
## 118) How do you set up SSR using Next.js with React?
#### Example:
- Fetch data on the server:

```bash
export async function getServerSideProps() {
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();

  return { props: { data } };
}

function Page({ data }) {
  return <div>{JSON.stringify(data)}</div>;
}

export default Page;
```
## 119) What are React error boundaries, and how do you implement them?

- Error boundaries catch JavaScript errors in their child components.

#### Example:
```bash
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.error(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```
- Usage:

```bash
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```
## 120) How do you monitor performance in a React app?
#### Tools:
- React Profiler: Built-in tool to measure rendering performance.
- Web Vitals: Monitor metrics like FCP, LCP, etc.
- Third-party libraries: Use tools like Sentry or LogRocket for monitoring.


## 121) What are synthetic events in React?

- Synthetic events are React's wrapper around browser-native events, ensuring cross-browser compatibility.

#### Example:
```bash
function App() {
  const handleClick = (e) => {
    console.log(e.nativeEvent); // Access native event
    console.log(e);             // Synthetic event
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```
## 122) How do you avoid memory leaks in React?
#### Techniques:
- Cleanup in useEffect:

```bash
useEffect(() => {
  const interval = setInterval(() => console.log('Running'), 1000);
  return () => clearInterval(interval); // Cleanup
}, []);
```
- Use AbortController to cancel API requests.

## 123) What are the different lifecycle methods of React?

#### React class components have:

- Mounting: constructor, componentDidMount.
- Updating: componentDidUpdate.
- Unmounting: componentWillUnmount.
- Functional components use hooks for similar functionality.

## 124) What is Flux architecture?

- Flux is an application architecture for managing unidirectional data flow in React apps. It has:

- Actions: Dispatch actions to update the store.
- Dispatcher: Central hub for event dispatching.
- Store: Holds the state.
- View: React components.
## 125) How is Flux different from Redux?
|Feature|	Flux|	Redux||
|----|----|----|---|
|Store	|Multiple stores	|Single store
|Dispatcher|	Central dispatcher|	No dispatcher
|State mutation|	Directly in store	|Pure reducers

## 126) How do you use hooks to manage form validation?
#### Example:
```bash
function App() {
  const [email, setEmail] = React.useState('');
  const [error, setError] = React.useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    if (!email.includes('@')) {
      setError('Invalid email');
    } else {
      setError('');
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input value={email} onChange={(e) => setEmail(e.target.value)} />
      {error && <span>{error}</span>}
    </form>
  );
}
```
## 127) How would you implement caching in a React app?
#### Techniques:
- Use localStorage or sessionStorage.
- Cache API responses with libraries like axios-cache-adapter.
- Service Workers for offline caching.
## 128) What is the purpose of React.cloneElement?

- React.cloneElement clones a React element, optionally modifying its props or children.

#### Example:
```bash
const Button = (props) => <button>{props.label}</button>;

const App = () => {
  const clonedButton = React.cloneElement(<Button />, { label: 'Click Me' });
  return clonedButton;
};
```
## 129)What is the purpose of React.Children.map?

- React.Children.map is a utility method for iterating over children elements passed to a component. It ensures children are handled safely and works with fragments, null, and arrays.

#### Example:
```bash
const Wrapper = ({ children }) => {
  return React.Children.map(children, (child, index) => (
    <div key={index} className="child-wrapper">
      {child}
    </div>
  ));
};

function App() {
  return (
    <Wrapper>
      <p>First Child</p>
      <p>Second Child</p>
    </Wrapper>
  );
}
```
#### Output:

```bash
<div class="child-wrapper"><p>First Child</p></div>
<div class="child-wrapper"><p>Second Child</p></div>
```
## 130) What is the difference between React.PureComponent and React.Component?

- React.Component: Re-renders every time props or state change, regardless of whether the changes are meaningful.
- React.PureComponent: Implements a shallow comparison of props and state, re-rendering only when meaningful changes occur.
#### Example:
```bash
import React, { Component, PureComponent } from 'react';

class RegularComponent extends Component {
  render() {
    console.log('Regular Component Rendered');
    return <div>{this.props.value}</div>;
  }
}

class PureComp extends PureComponent {
  render() {
    console.log('Pure Component Rendered');
    return <div>{this.props.value}</div>;
  }
}

function App() {
  return (
    <>
      <RegularComponent value="Hello" />
      <PureComp value="Hello" />
    </>
  );
}
```
#### Difference:

- RegularComponent always renders.
- PureComp renders only if props.value changes.



## 131)How do you manage side effects in React apps?

- Side effects like fetching data, subscriptions, and manual DOM updates are handled using the useEffect hook or lifecycle methods in class components.

#### Example:
- Fetching data with useEffect:

```bash
import React, { useEffect, useState } from 'react';

function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then((res) => res.json())
      .then((result) => setData(result));

    return () => {
      console.log('Cleanup if necessary, like cancelling subscriptions.');
    };
  }, []); // Empty dependency array = run only on mount.

  return <ul>{data.map((item) => <li key={item.id}>{item.name}</li>)}</ul>;
}
```
## 132) How do you handle errors in React?

- React provides Error Boundaries and the componentDidCatch lifecycle for handling errors in class components. For functional components, error handling can involve try-catch blocks or libraries like React Query for API errors.

#### Example of Error Boundary:
```bash
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error('Error:', error, 'Info:', info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}

function FaultyComponent() {
  throw new Error('Intentional Error');
}

function App() {
  return (
    <ErrorBoundary>
      <FaultyComponent />
    </ErrorBoundary>
  );
}
```
## 133) What are forward refs in React?

- Forward refs allow passing a ref from a parent to a child component, granting the parent access to the child’s DOM or component instance.

#### Example:
```bash
import React, { forwardRef } from 'react';

const Input = forwardRef((props, ref) => <input ref={ref} {...props} />);

function App() {
  const inputRef = React.useRef();

  return (
    <>
      <Input ref={inputRef} placeholder="Enter text" />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </>
  );
}
```
## 134) How do you optimize API calls in React?
#### Techniques:
- Debounce/throttle API calls:

```bash
import { debounce } from 'lodash';
const fetchDebounced = debounce(() => fetchData(), 500);
```
- Use React Query:

```bash
import { useQuery } from 'react-query';

const { data, isLoading } = useQuery('fetchData', fetchData);
```
- Cache results in local state or libraries like Redux.

- Avoid unnecessary calls with proper dependency arrays in useEffect.

## 135) What are the common anti-patterns in React?
#### Examples of Anti-Patterns:
- Mutating state directly:

```bash
this.state.count = 10; // WRONG
this.setState({ count: 10 }); // Correct
```
- Overusing Redux/Context API:

- Avoid managing local component states like form inputs in Redux.
#### Excessive re-renders:

- Use React.memo or useCallback to avoid unnecessary re-renders.
- Not cleaning up side effects:

```bash
useEffect(() => {
  const interval = setInterval(doSomething, 1000);
  return () => clearInterval(interval); // Cleanup
}, []);
```
## 136) How do you improve SEO in React apps?
#### Techniques:
- Server-Side Rendering (SSR) with Next.js:

```bash
export async function getServerSideProps() {
  const data = await fetchData();
  return { props: { data } };
}
```
- Meta tags using libraries like React Helmet:

```bash
import { Helmet } from 'react-helmet';

function App() {
  return (
    <Helmet>
      <title>My App</title>
      <meta name="description" content="SEO optimized description" />
    </Helmet>
  );
}
```
- Dynamic routing with clear URLs.

- Pre-rendering and static generation.

## 137) How do you implement a carousel in React?
### Example using a library:
```bash
import Carousel from 'react-multi-carousel';
import 'react-multi-carousel/lib/styles.css';

function App() {
  return (
    <Carousel infinite autoPlay>
      <div>Item 1</div>
      <div>Item 2</div>
      <div>Item 3</div>
    </Carousel>
  );
}
```
- Custom Implementation:
```bash
function Carousel({ items }) {
  const [index, setIndex] = React.useState(0);

  return (
    <div>
      <button onClick={() => setIndex((prev) => (prev - 1 + items.length) % items.length)}>Prev</button>
      <div>{items[index]}</div>
      <button onClick={() => setIndex((prev) => (prev + 1) % items.length)}>Next</button>
    </div>
  );
}
```
## 138) How do you handle file uploads in React?
### Example:
- HTML Input and State:

```bash
function App() {
  const [file, setFile] = React.useState(null);

  const handleFileUpload = (event) => {
    setFile(event.target.files[0]);
  };

  return <input type="file" onChange={handleFileUpload} />;
}
```
- Uploading to a Server:

```bash
const handleUpload = async () => {
  const formData = new FormData();
  formData.append('file', file);

  const response = await fetch('/upload', {
    method: 'POST',
    body: formData,
  });

  if (response.ok) {
    console.log('File uploaded successfully');
  }
};
```
- Uploading to Firebase:
```bash
import { storage } from './firebase';

const uploadToFirebase = () => {
  const storageRef = storage.ref(`files/${file.name}`);
  storageRef.put(file).then(() => {
    console.log('Uploaded to Firebase');
  });
};
```
## 139) How do you design responsive components in React?

### Responsive components adjust their layout based on screen size. You can achieve this using:

- CSS Media Queries
- CSS-in-JS libraries like Styled Components
- Flexbox/Grid
- Tailwind CSS
- React libraries like react-responsive
### Example (Using Tailwind CSS)
```bash
function ResponsiveCard() {
  return (
    <div className="max-w-sm md:max-w-md lg:max-w-lg p-4 bg-gray-100 rounded-lg">
      <h2 className="text-lg md:text-xl lg:text-2xl font-bold">Responsive Component</h2>
      <p className="text-sm md:text-base">This adjusts based on screen size.</p>
    </div>
  );
}
```
## 140) What are controlled and uncontrolled components in React?

- Controlled Component: React controls the state of the input.
- Uncontrolled Component: The DOM itself maintains the state.
### Example (Controlled Component)
```bash
function ControlledInput() {
  const [value, setValue] = React.useState("");

  return <input type="text" value={value} onChange={(e) => setValue(e.target.value)} />;
}
```
### Example (Uncontrolled Component with Ref)
```bash
function UncontrolledInput() {
  const inputRef = React.useRef();

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={() => alert(inputRef.current.value)}>Get Value</button>
    </div>
  );
}
```
## 141) How do you optimize images in React?
### Techniques:
- Use optimized formats like WebP
- Lazy Loading with React Lazy Load
- Use a CDN for faster loading
- Use Image Compression Libraries
### Example (Lazy Loading with react-lazy-load-image-component)
```bash
import { LazyLoadImage } from "react-lazy-load-image-component";

function OptimizedImage() {
  return <LazyLoadImage src="image.webp" alt="Optimized" effect="blur" />;
}
```

## 142) How do you implement live chat in a React app?
### Using Firebase Firestore
```bash
import { useState, useEffect } from "react";
import { db } from "./firebase";
import { collection, addDoc, onSnapshot } from "firebase/firestore";

function ChatApp() {
  const [messages, setMessages] = useState([]);
  const [input, setInput] = useState("");

  useEffect(() => {
    const unsubscribe = onSnapshot(collection(db, "messages"), (snapshot) => {
      setMessages(snapshot.docs.map((doc) => doc.data()));
    });
    return unsubscribe;
  }, []);

  const sendMessage = async () => {
    await addDoc(collection(db, "messages"), { text: input });
    setInput("");
  };

  return (
    <div>
      {messages.map((msg, index) => (
        <p key={index}>{msg.text}</p>
      ))}
      <input value={input} onChange={(e) => setInput(e.target.value)} />
      <button onClick={sendMessage}>Send</button>
    </div>
  );
}
```
## 143) What is React PropTypes?
### Used for type checking of props in React.

### Example:
```bash
import PropTypes from "prop-types";

function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
}

Greeting.propTypes = {
  name: PropTypes.string.isRequired,
};
```
## 144) How do you integrate an API with React?
### Example (Using Fetch API)
```bash
function App() {
  const [data, setData] = React.useState([]);

  React.useEffect(() => {
    fetch("https://api.example.com/data")
      .then((res) => res.json())
      .then((data) => setData(data));
  }, []);

  return <ul>{data.map((item) => <li key={item.id}>{item.name}</li>)}</ul>;
}
```
## 145) How do you optimize React app performance?
- Use React.memo to prevent unnecessary re-renders.
- Use useCallback and useMemo for performance optimizations.
- Lazy Load Components.
- Optimize API calls using React Query.
## 146) What are React Fragments?

- Allows grouping elements without an extra DOM node.

### Example:
```bash
function App() {
  return (
    <>
      <h1>Title</h1>
      <p>Some text</p>
    </>
  );
}
```
## 147) How does React handle keys in lists?
- Keys help React identify changes in lists for efficient updates.

### Example:
```bash
const items = ["Apple", "Banana", "Cherry"];

function List() {
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{item}</li> // Bad practice, use unique ID if possible
      ))}
    </ul>
  );
}
```
## 148) How does reconciliation work in React?
- React uses a Virtual DOM and a diffing algorithm to update only the necessary parts of the UI.

## 149) What is the difference between useState and useEffect?
| Feature  | useState                               | useEffect                            |  
|----------|----------------------------------------|-------------------------------------|  
| Purpose  | Manage component state                 | Perform side effects                 |  
| Runs     | When state updates                     | After render                         |  
| Example  | `const [count, setCount] = useState(0);` | `useEffect(() => { fetchData(); }, []);` |

## 149) What are compound components in React?

- A pattern where multiple components work together within a parent.

### Example:
```bash
function Modal({ children }) {
  return <div className="modal">{children}</div>;
}

Modal.Header = ({ children }) => <h2>{children}</h2>;
Modal.Body = ({ children }) => <p>{children}</p>;

function App() {
  return (
    <Modal>
      <Modal.Header>Title</Modal.Header>
      <Modal.Body>Body Content</Modal.Body>
    </Modal>
  );
}
```
## 150) How do you design a reusable React component?
- Use props to make components flexible.
- Accept children for customization.
- Avoid hardcoding styles.
### Example:
```bash
function Button({ label, onClick }) {
  return <button onClick={onClick}>{label}</button>;
}
<Button label="Click Me" onClick={() => alert("Clicked!")} />;
```


## 151) What are dynamic imports in React?
### Example (Lazy Loading with React.lazy)
```bash
const LazyComponent = React.lazy(() => import("./HeavyComponent"));

function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```
## 152) How do you manage state in React?
- Local State (useState)
- Global State (Context API, Redux)
- Server State (React Query)
### Example (Using Context API for Global State)
```bash
const ThemeContext = React.createContext();

function App() {
  const [theme, setTheme] = React.useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <ChildComponent />
    </ThemeContext.Provider>
  );
}

function ChildComponent() {
  const { theme } = React.useContext(ThemeContext);
  return <p>Current theme: {theme}</p>;
}
```
## 153)What is React Profiler?
- React Profiler is a built-in tool to measure the performance of components by tracking rendering times and identifying slow components.

### Example: Wrapping a Component with Profiler
```bash
import { Profiler } from "react";

function onRenderCallback(id, phase, actualDuration) {
  console.log(`Component: ${id}, Phase: ${phase}, Render time: ${actualDuration}ms`);
}

function App() {
  return (
    <Profiler id="MyComponent" onRender={onRenderCallback}>
      <MyComponent />
    </Profiler>
  );
}
```
## 154) How do you create dynamic forms in React?
- You can create dynamic forms using state and map() to render inputs dynamically.

### Example: Adding Dynamic Input Fields
```bash
function DynamicForm() {
  const [fields, setFields] = React.useState([""]);

  const addField = () => setFields([...fields, ""]);
  const updateField = (index, value) => {
    const newFields = [...fields];
    newFields[index] = value;
    setFields(newFields);
  };

  return (
    <div>
      {fields.map((field, index) => (
        <input key={index} value={field} onChange={(e) => updateField(index, e.target.value)} />
      ))}
      <button onClick={addField}>Add Field</button>
    </div>
  );
}
```
## 155) How do you handle asynchronous code in React?
- You can use async/await inside useEffect or handle Promises.

### Example: Fetching Data with useEffect
```bash
function FetchData() {
  const [data, setData] = React.useState([]);

  React.useEffect(() => {
    async function fetchData() {
      const response = await fetch("https://jsonplaceholder.typicode.com/posts");
      const result = await response.json();
      setData(result);
    }
    fetchData();
  }, []);

  return <ul>{data.map((item) => <li key={item.id}>{item.title}</li>)}</ul>;
}
```

## 156) How do you implement internationalization in React?
- Use libraries like react-intl or i18next.

### Example using react-i18next
```bash
import { useTranslation } from "react-i18next";

function App() {
  const { t } = useTranslation();
  return <h1>{t("welcome_message")}</h1>;
}
```
## 157) How do you debug React Hooks?
- Use React DevTools to inspect hooks.
- Use console.log() inside hooks.
- Avoid infinite loops by setting dependencies correctly in useEffect.
## 158) What are WebSockets, and how are they used in React?
- WebSockets enable real-time communication between the client and server.

### Example using WebSockets in React
```bash
const socket = new WebSocket("ws://example.com/socket");

socket.onopen = () => console.log("Connected");
socket.onmessage = (event) => console.log("Message:", event.data);
```
## 159) How do you implement breadcrumbs in React?
- Breadcrumbs show the navigation path.

### Example: Simple Breadcrumb Component
```bash
import { Link } from "react-router-dom";

function Breadcrumbs({ paths }) {
  return (
    <nav>
      {paths.map((path, index) => (
        <span key={index}>
          <Link to={path.link}>{path.label}</Link> {index < paths.length - 1 && " / "}
        </span>
      ))}
    </nav>
  );
}
```
## 160) How do you implement notifications in React?
- Use a library like react-toastify.

### Example: Toast Notifications
```bash
import { ToastContainer, toast } from "react-toastify";
import "react-toastify/dist/ReactToastify.css";

function App() {
  return (
    <div>
      <button onClick={() => toast.success("Success!")}>Show Notification</button>
      <ToastContainer />
    </div>
  );
}
```

## 161) How do you create a custom hook?
- Custom hooks allow reusing logic across components.

### Example: Custom Hook for Fetching Data
```bash
function useFetch(url) {
  const [data, setData] = React.useState(null);

  React.useEffect(() => {
    async function fetchData() {
      const response = await fetch(url);
      const result = await response.json();
      setData(result);
    }
    fetchData();
  }, [url]);

  return data;
}

function App() {
  const data = useFetch("https://jsonplaceholder.typicode.com/posts");
  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```
## 162) What is the Context API?
- Used for managing global state without prop drilling.

### Example: Using Context API for Theme Management
```bash
const ThemeContext = React.createContext();

function App() {
  const [theme, setTheme] = React.useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Child />
    </ThemeContext.Provider>
  );
}

function Child() {
  const { theme } = React.useContext(ThemeContext);
  return <p>Current theme: {theme}</p>;
}
```
## 163) How do you integrate Redux with React?
- Install react-redux and @reduxjs/toolkit.
- Create a Redux store.
- Use useSelector to get state and useDispatch to update state.
### Example: Redux Setup
```bash
import { configureStore, createSlice } from "@reduxjs/toolkit";
import { Provider, useDispatch, useSelector } from "react-redux";

const counterSlice = createSlice({
  name: "counter",
  initialState: 0,
  reducers: {
    increment: (state) => state + 1,
  },
});

const store = configureStore({ reducer: counterSlice.reducer });

function Counter() {
  const count = useSelector((state) => state);
  const dispatch = useDispatch();

  return <button onClick={() => dispatch(counterSlice.actions.increment())}>Count: {count}</button>;
}

function App() {
  return (
    <Provider store={store}>
      <Counter />
    </Provider>
  );
}
```
## 164) How do you handle multiple themes in React?
### Example: Using Tailwind CSS Themes
```bash
const themes = { light: "bg-white text-black", dark: "bg-black text-white" };

function App() {
  const [theme, setTheme] = React.useState("light");

  return (
    <div className={themes[theme]}>
      <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>Toggle Theme</button>
    </div>
  );
}
```
## 165) What is the purpose of React.Children.toArray?
- It ensures children are a flat array with keys, preventing errors.

### Example: Using React.Children.toArray
```bash
function Parent({ children }) {
  return <div>{React.Children.toArray(children).map((child) => child)}</div>;
}

function App() {
  return (
    <Parent>
      <h1>Hello</h1>
      <h2>World</h2>
    </Parent>
  );
}
```
## 166) What are React Design Patterns?
- React design patterns are best practices and reusable solutions for common problems in React applications.

### Common Design Patterns in React
- Container-Presentational Pattern → Separates logic (Container) from UI (Presentational).
- Higher-Order Components (HOC) → Reusable component logic via function wrappers.
- Render Props → Uses a function prop to render dynamic UI.
- Compound Components → Components work together by sharing state/context.
- Controlled & Uncontrolled Components → Manage form inputs effectively.
### Example: Container-Presentational Pattern
```bash
function DataContainer() {
  const [data, setData] = React.useState([]);

  React.useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((res) => res.json())
      .then(setData);
  }, []);

  return <PresentationalComponent data={data} />;
}

function PresentationalComponent({ data }) {
  return <ul>{data.map((item) => <li key={item.id}>{item.title}</li>)}</ul>;
}
```
## 167) How do you implement modals in React?
- You can use state and conditional rendering or libraries like react-modal.

### Example: Simple Modal
```bash
function ModalExample() {
  const [isOpen, setIsOpen] = React.useState(false);

  return (
    <div>
      <button onClick={() => setIsOpen(true)}>Open Modal</button>
      {isOpen && (
        <div className="modal">
          <p>Modal Content</p>
          <button onClick={() => setIsOpen(false)}>Close</button>
        </div>
      )}
    </div>
  );
}
```
## 168) How do you manage forms in React?
- Forms can be managed using controlled components, useState(), or libraries like react-hook-form.

### Example: Controlled Form with useState
```bash
function FormExample() {
  const [name, setName] = React.useState("");

  return (
    <form onSubmit={(e) => e.preventDefault()}>
      <input value={name} onChange={(e) => setName(e.target.value)} />
      <button type="submit">Submit</button>
    </form>
  );
}
```
## 169) What are Render Props in React?
- A Render Prop is a function prop that determines what gets rendered.

### Example: Render Props
```bash
function DataProvider({ render }) {
  const [count, setCount] = React.useState(0);

  return <div>{render(count, () => setCount(count + 1))}</div>;
}

function App() {
  return (
    <DataProvider
      render={(count, increment) => (
        <>
          <p>Count: {count}</p>
          <button onClick={increment}>Increment</button>
        </>
      )}
    />
  );
}
```
## 170) How do you implement lazy loading in React?
- Use React.lazy() and Suspense to load components on demand.

### Example: Lazy Loading a Component
```bash
const LazyComponent = React.lazy(() => import("./HeavyComponent"));

function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```
## 171) How do you handle forms in React?
### Forms can be handled via:

- Controlled components (useState).

- Formik (validations, form state management).

- react-hook-form (efficient form handling).

#### Example: Using react-hook-form
```bash
import { useForm } from "react-hook-form";

function FormExample() {
  const { register, handleSubmit } = useForm();

  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("name")} placeholder="Enter Name" />
      <button type="submit">Submit</button>
    </form>
  );
}
```
## 172) How do you manage dependencies in React apps?
- Use package managers (npm or yarn) to install/update dependencies.

- Use package.json to define exact versions (dependencies and devDependencies).

- Use npm audit to check for vulnerabilities.

- Lock versions (package-lock.json or yarn.lock).

## 173) How do you debug Redux applications?
- Use Redux DevTools Extension – Inspect actions, state, and time-travel debugging.

- Log actions in Middleware – Add logging middleware.

- Check mapStateToProps and useSelector for correct state retrieval.

- Use breakpoints in Redux reducers.

#### Example: Logging Redux Actions
```bash
const loggerMiddleware = (store) => (next) => (action) => {
  console.log("Dispatching:", action);
  return next(action);
};
```
## 174) What is the purpose of useLayoutEffect hook?
- Similar to useEffect, but runs before the browser paints the screen.

- Used when DOM measurements or synchronous updates are required.

#### Example: Using useLayoutEffect
```bash
function Example() {
  const inputRef = React.useRef();

  React.useLayoutEffect(() => {
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} />;
}
```
- Here, useLayoutEffect ensures the input is focused before the browser paints the UI.

## 175) How do you implement virtual scrolling in React?
- Virtual scrolling renders only visible elements, improving performance for large lists.
- Use libraries like react-window or react-virtualized.

#### Example: Virtual Scrolling with react-window
```bash
import { FixedSizeList as List } from "react-window";

const items = Array.from({ length: 1000 }, (_, i) => `Item ${i}`);

function VirtualizedList() {
  return (
    <List height={300} width={300} itemSize={30} itemCount={items.length}>
      {({ index, style }) => <div style={style}>{items[index]}</div>}
    </List>
  );
}
```
- This only renders visible items instead of all 1000 items.

## 176) How do you optimize performance in large-scale React applications?
- Performance optimization in React involves reducing unnecessary renders, optimizing rendering logic, and improving data fetching efficiency.

### Key Techniques for Optimization
#### Use React.memo for Pure Components

- Prevents unnecessary re-renders by memoizing components.

```bash
const MemoizedComponent = React.memo(({ data }) => {
  console.log("Rendering...");
  return <div>{data}</div>;
});

function App() {
  const [count, setCount] = React.useState(0);
  return (
    <div>
      <MemoizedComponent data="Hello" />
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```
#### Use useCallback to Memoize Functions

- Ensures the same function reference is passed to child components.

```bash
const memoizedFunction = useCallback(() => {
  console.log("Function not recreated");
}, []);
```
#### Use useMemo for Expensive Computations

- Memoizes expensive calculations.

```bash
const expensiveValue = useMemo(() => computeExpensiveValue(input), [input]);
```
#### Use Lazy Loading and Code Splitting

- Load components dynamically only when needed.

```bash
const LazyComponent = React.lazy(() => import("./HeavyComponent"));
```
#### Virtualize Long Lists

- Use react-window for efficient rendering of long lists.

```bash
import { FixedSizeList as List } from "react-window";
```
#### Optimize Context API Performance

- Avoid unnecessary context re-renders by structuring providers efficiently.

## 177) What are React Fiber and its advantages over the old reconciliation algorithm?
- React Fiber is React's reconciliation engine that improves performance, concurrency, and responsiveness.

### Advantages Over Old Reconciliation
- Time-Slicing for Non-Blocking Rendering

- Fiber splits rendering into chunks, preventing UI blocking.

- Concurrent Mode Support

- Enables Suspense, React Concurrent Mode, and Transitions.

- Error Handling with Error Boundaries

- Improves error recovery and debugging.

- Improved Animation Performance

- Animations are smoother due to incremental rendering.

## 178) How does React’s rendering mechanism work internally?
### React follows a two-phase rendering process:

- Render Phase (Reconciliation)

- Creates a virtual DOM tree.

- Uses React Fiber to determine minimal changes.

- Commit Phase

- Applies changes to the actual DOM.

## 179) How does React handle concurrent rendering with Suspense and React Concurrent Mode?
- Concurrent Mode improves responsiveness by allowing rendering to be interruptible.

#### Example: Using Suspense
```bash
const LazyComponent = React.lazy(() => import("./Component"));

function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```
## 180) How do you minimize re-renders in React applications?
- Use React.memo() for components.

- Use useCallback() for function dependencies.

- Optimize Context API usage.

- Use useReducer() for complex state management.

- Use useMemo() for derived values.




## 181) How do you handle memory leaks in React applications?
- Unsubscribe from API calls in useEffect.

- Remove event listeners in cleanup functions.

- Avoid storing large objects in state.

## 182) What is tree shaking, and how does it improve performance in React?
- Tree shaking eliminates unused JavaScript code during the bundling process.

#### Example: Removing Unused Code
```bash
// Importing only necessary functions
import { specificFunction } from "large-library";
```
## 183) What is Code Splitting, and how does it work in React?
- Code Splitting reduces initial load time by dynamically loading JavaScript.

#### Example with React.lazy
```bash
const LazyComponent = React.lazy(() => import("./Component"));
```
## 184) How do you handle expensive calculations efficiently in React?
- Use useMemo() to memoize computations.

- Move expensive logic to Web Workers.

## 185) What is a Render Prop, and how does it compare to Higher-Order Components?
- A Render Prop is a function passed as a prop that renders UI dynamically.

#### Example: Render Prop
```bash
const MouseTracker = ({ render }) => {
  const [position, setPosition] = React.useState({ x: 0, y: 0 });

  return <div>{render(position)}</div>;
};
```
## 186) How do you implement an infinite scrolling feature in React?
- Use the Intersection Observer API or react-infinite-scroll-component.

#### Example
```bash
const observer = new IntersectionObserver((entries) => {
  if (entries[0].isIntersecting) {
    fetchMoreData();
  }
});
```
## 187) Best practices for useMemo and useCallback in React
- Use useMemo() for expensive calculations.

- Use useCallback() for function dependencies.

## 188) What is whyDidYouRender, and how can it help optimize performance?
####  whyDidYouRender is a library that helps detect unnecessary re-renders.

-  Installation
```bash
npm install @welldone-software/why-did-you-render
```
## 189) How does useReducer differ from useState in managing complex state logic?
- useState() is for simple state updates.

- useReducer() is for complex state logic.

### Example: useReducer
```bash
const reducer = (state, action) => {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
    default:
      return state;
  }
};

const [state, dispatch] = useReducer(reducer, { count: 0 });
```
## 190) Difference between useRef, createRef, and forwardRef
- useRef() → Persistent references.

- createRef() → New reference on every render.

- forwardRef() → Pass refs to child components.




## 191) How to persist state across page reloads in React?
- Use localStorage or sessionStorage.

#### Example
```bash
const [data, setData] = React.useState(() => {
  return JSON.parse(localStorage.getItem("data")) || "";
});

React.useEffect(() => {
  localStorage.setItem("data", JSON.stringify(data));
}, [data]);
```
## 192) How to handle debouncing and throttling in React?
- Use lodash for debouncing.

#### Example: Debounce Input
```bash
import { debounce } from "lodash";

const debouncedSearch = debounce((query) => {
  fetchData(query);
}, 500);
```
## 193) How to implement global state management without Redux?
- React Context API

- Zustand

- Recoil

- Jotai

## 194) Differences between Redux Toolkit and traditional Redux
|Feature	|Redux Toolkit|	Traditional Redux|
|----- |----- |----- |
| Boilerplate|	Less|	More|
|Configuration|	Easy|	Manual|
|Async Handling	|createAsyncThunk	|Middleware required|

## 195) What are selectors in Redux, and how do they improve performance?
- Selectors memoize data to avoid unnecessary calculations.

#### Example
```bash
import { createSelector } from "reselect";

const selectUsers = (state) => state.users;

const selectActiveUsers = createSelector([selectUsers], (users) =>
  users.filter((user) => user.active)
);
```

## 196) How do you create dynamic forms in React?
- Dynamic forms allow you to create form fields based on data or user interaction.

#### ✅ Use Case:
- You want to render form inputs based on an array of objects.

#### 🧠 Example:
```bash
const formFields = [
  { name: 'username', label: 'Username', type: 'text' },
  { name: 'email', label: 'Email', type: 'email' },
  { name: 'age', label: 'Age', type: 'number' }
];

function DynamicForm() {
  const [formData, setFormData] = React.useState({});

  const handleChange = (e) => {
    setFormData({ ...formData, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      {formFields.map(field => (
        <div key={field.name}>
          <label>{field.label}</label>
          <input
            name={field.name}
            type={field.type}
            value={formData[field.name] || ''}
            onChange={handleChange}
          />
        </div>
      ))}
      <button type="submit">Submit</button>
    </form>
  );
}
```
## 197) How do you handle asynchronous code in React?
- Asynchronous code (e.g., API calls) is handled using async/await inside useEffect or event handlers.

#### 🧠 Example: Fetching Data
```bash
function UsersList() {
  const [users, setUsers] = React.useState([]);
  const [loading, setLoading] = React.useState(true);

  React.useEffect(() => {
    const fetchUsers = async () => {
      const res = await fetch("https://jsonplaceholder.typicode.com/users");
      const data = await res.json();
      setUsers(data);
      setLoading(false);
    };
    fetchUsers();
  }, []);

  if (loading) return <p>Loading...</p>;

  return (
    <ul>
      {users.map(user => <li key={user.id}>{user.name}</li>)}
    </ul>
  );
}
```
## 198) What is React Transition Group?
- It’s a library for adding animations/transitions to components as they mount/unmount.

#### 📦 Installation:
```bash
npm install react-transition-group
```
### 🧠 Example:
```bash
import { CSSTransition } from 'react-transition-group';
import './fade.css';

function FadeComponent({ show }) {
  return (
    <CSSTransition
      in={show}
      timeout={300}
      classNames="fade"
      unmountOnExit
    >
      <div className="fade-box">Hello with Transition!</div>
    </CSSTransition>
  );
}
```
#### 🔥 CSS (fade.css)
```bash
.fade-enter {
  opacity: 0;
}
.fade-enter-active {
  opacity: 1;
  transition: opacity 300ms;
}
.fade-exit {
  opacity: 1;
}
.fade-exit-active {
  opacity: 0;
  transition: opacity 300ms;
}
```
## 199) How do you implement internationalization (i18n) in React?
- Use libraries like react-i18next for multi-language support.

#### 📦 Installation:
```bash
npm install react-i18next i18next
```
#### 🧠 Example:
```bash
import { useTranslation } from 'react-i18next';

function App() {
  const { t, i18n } = useTranslation();

  return (
    <div>
      <p>{t('welcome')}</p>
      <button onClick={() => i18n.changeLanguage('fr')}>FR</button>
      <button onClick={() => i18n.changeLanguage('en')}>EN</button>
    </div>
  );
}
```
- 🗂 i18n Translation File (en.json)
```bash
{
  "welcome": "Welcome to our app"
}
```

## 200) What are WebSockets, and how are they used in React?
- WebSockets provide real-time communication between client and server.

#### 📦 Example with socket.io-client
```bash
npm install socket.io-client
```
#### 🧠 Example:
```bash
import { useEffect } from 'react';
import io from 'socket.io-client';

const socket = io("http://localhost:3001");

function Chat() {
  useEffect(() => {
    socket.on("message", msg => {
      console.log("New message:", msg);
    });

    return () => socket.disconnect();
  }, []);

  const sendMessage = () => {
    socket.emit("message", "Hello from React");
  };

  return <button onClick={sendMessage}>Send Message</button>;
}
```

## Thank You ❤️
