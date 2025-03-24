# React.js Core Concepts - The 20% That Delivers 80% Understanding

## 1. Component-Based Architecture

React is built around **components** - reusable, self-contained pieces of code that return markup:

```jsx
// Functional component
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Class component
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

Components can be composed together to build complex UIs from simple building blocks.

## 2. JSX - JavaScript XML

JSX is a syntax extension that looks like HTML but allows you to write JavaScript within curly braces:

```jsx
const element = <h1>Hello, {user.name}!</h1>;
```

JSX compiles to regular JavaScript function calls that return objects representing DOM nodes.

## 3. State and Props

- **Props** - Read-only data passed from parent to child components
- **State** - Component's private data that can change over time

```jsx
// Props example
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// State example (using hooks)
function Counter() {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

## 4. React Hooks

Hooks let you use state and other React features in functional components:

- **useState** - Adds state to functional components
- **useEffect** - Performs side effects (like data fetching)
- **useContext** - Accesses React context
- **useRef** - References DOM elements or persists values

```jsx
function ProfilePage() {
  // State hook
  const [user, setUser] = useState(null);
  
  // Effect hook - runs after render
  useEffect(() => {
    fetchUser().then(data => setUser(data));
  }, []); // Empty array means run once on mount
  
  if (!user) return <div>Loading...</div>;
  return <div>{user.name}</div>;
}
```

## 5. Conditional Rendering

React lets you conditionally render components:

```jsx
function UserGreeting(props) {
  return (
    <div>
      {props.isLoggedIn ? (
        <h1>Welcome back!</h1>
      ) : (
        <h1>Please sign up.</h1>
      )}
    </div>
  );
}
```

## 6. Lists and Keys

React uses keys to identify which items have changed, been added, or removed:

```jsx
function TodoList(props) {
  return (
    <ul>
      {props.todos.map((todo) => (
        <li key={todo.id}>{todo.text}</li>
      ))}
    </ul>
  );
}
```

## 7. Event Handling

React events use camelCase naming and pass functions as event handlers:

```jsx
function Button() {
  function handleClick(e) {
    e.preventDefault();
    console.log('Button was clicked');
  }
  
  return <button onClick={handleClick}>Click me</button>;
}
```

## 8. Component Lifecycle and useEffect

The `useEffect` hook replaces lifecycle methods in functional components:

```jsx
useEffect(() => {
  // Runs after every render
  document.title = `You clicked ${count} times`;
  
  return () => {
    // Cleanup function (like componentWillUnmount)
    saveData(count);
  };
}, [count]); // Only re-run if count changes
```

## 9. Forms and Controlled Components

In React, form elements keep their own state, but React can control it:

```jsx
function NameForm() {
  const [name, setName] = useState('');
  
  const handleSubmit = (e) => {
    e.preventDefault();
    alert('Name submitted: ' + name);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input 
        type="text" 
        value={name}
        onChange={(e) => setName(e.target.value)} 
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

## 10. State Management

For complex applications, consider these approaches:
- **Props drilling** - Pass state through components (simple)
- **Context API** - Avoid passing props through intermediate components
- **Redux/Zustand/Jotai** - External state management libraries for complex state

## Bonus: React Best Practices

1. Keep components small and focused on a single responsibility
2. Lift shared state up to common ancestors
3. Use functional components with hooks instead of class components
4. Always add keys to list items
5. Use immutable patterns for updating state
6. Extract reusable logic into custom hooks
7. Break complex UI into multiple components
8. Use React Developer Tools for debugging
