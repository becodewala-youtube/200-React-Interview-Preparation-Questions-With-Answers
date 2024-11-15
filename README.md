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
## 5)5. What is a React component?
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
## 32) How do you implement code splitting in React?
- Code splitting breaks large bundles into smaller chunks using React.lazy and dynamic imports.
#### Example:

```bash
const Component = React.lazy(() => import('./Component'));
```
## 33) What is the difference between a library and a framework? Is React a library or framework?
- Library: A collection of tools to help build applications (React).
- Framework: Provides a complete structure for application development (Angular).
- React is a library focused on UI.
## 34) How do you fetch data in React applications?
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
## 35)Explain the purpose of the useEffect hook.
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
## 36)How do you use React Router?
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

## 37) What is the purpose of <BrowserRouter> in React Router?
- <BrowserRouter> provides the context for managing navigation and history in a React app. It uses the HTML5 history API to keep the UI in sync with the URL.

#### Example:
- In the example above, <BrowserRouter> wraps the app to enable routing.
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
