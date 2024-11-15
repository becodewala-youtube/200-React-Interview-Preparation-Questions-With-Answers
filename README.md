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
