# 📌 React Interview Questions (Easy to Moderate)

## 🌱 Fundamentals & Core Concepts

### 1️⃣ What is React, and why is it popular?

React is a **JavaScript library** for building **user interfaces**. It is popular because:

- It allows **component-based development**, making code reusable and manageable.
- Uses a **Virtual DOM**, improving performance.
- Supports **declarative programming**, making UI updates easier.
- Has a large **community** and a rich **ecosystem** of tools.

---

### 2️⃣ How does the Virtual DOM work?

The **Virtual DOM (VDOM)** is a lightweight copy of the actual DOM. Instead of directly updating the real DOM, React:

1. Creates a **Virtual DOM** copy.
2. Finds the **differences** (diffing algorithm).
3. Updates only the **changed parts** in the real DOM (reconciliation process).

This improves performance by reducing unnecessary DOM updates.

---

### 3️⃣ What is JSX, and how is it different from HTML?

JSX (JavaScript XML) is a **syntax extension** that looks like HTML but allows JavaScript code inside it.

#### Differences:

- JSX needs **curly braces ****`{}`** for embedding JavaScript.
- **Class attribute** in HTML is written as `className` in JSX.
- Every JSX element must have **a single parent wrapper**.

Example:

```jsx
const element = <h1>Hello, {user.name}!</h1>;
```

---

### 4️⃣ What is the difference between functional and class components?

| Feature           | Functional Component       | Class Component              |
| ----------------- | -------------------------- | ---------------------------- |
| Syntax            | JavaScript function        | ES6 Class                    |
| State Handling    | `useState` hook            | `this.state`                 |
| Lifecycle Methods | `useEffect` hook           | `componentDidMount`, etc.    |
| Performance       | Faster (no `this` binding) | Slower due to `this` binding |

Example:

```jsx
// Functional Component
const Greeting = () => <h1>Hello!</h1>;
```

```jsx
// Class Component
class Greeting extends React.Component {
  render() {
    return <h1>Hello!</h1>;
  }
}
```

---

### 5️⃣ What are props and state, and how do they differ?

- **Props** (short for properties) are **read-only** and used to pass data **from parent to child**.
- **State** is **mutable** and managed within the component.

Example:

```jsx
// Using props
const Welcome = (props) => <h1>Hello, {props.name}!</h1>;
```

```jsx
// Using state
const Counter = () => {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
};
```

---

### 6️⃣ How do you create and use a simple React component?

```jsx
function Greeting() {
  return <h1>Hello, World!</h1>;
}
```

Usage:

```jsx
<Greeting />
```

---

### 7️⃣ What is event handling in React?

React uses **synthetic events**, which are wrappers around native events for cross-browser compatibility.

```jsx
const handleClick = () => alert("Button clicked!");
<button onClick={handleClick}>Click Me</button>
```

---

### 8️⃣ What is the significance of the key prop in lists?

- The `key` helps React **identify and update elements efficiently**.
- Each list item should have a **unique key** to avoid unnecessary re-renders.

```jsx
const items = ["Apple", "Banana", "Cherry"];
<ul>{items.map((item, index) => <li key={index}>{item}</li>)}</ul>
```

---

### 9️⃣ What is conditional rendering, and how do you implement it?

Conditional rendering allows rendering components **based on conditions**.

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

---

### 🔟 What are default props, and when are they useful?

Default props provide **fallback values** when no props are passed.

```jsx
const Welcome = ({ name = "Guest" }) => <h1>Welcome, {name}!</h1>;
```

---

## ⚡ React Hooks & Component Behavior

### 1️⃣1️⃣ What are React Hooks, and why were they introduced?

Hooks allow **state and lifecycle features** in functional components. They were introduced to avoid **class components** and make code **simpler**.

---

### 1️⃣2️⃣ Explain useState and useEffect with examples.

**useState** manages state:

```jsx
const [count, setCount] = useState(0);
setCount(count + 1);
```

**useEffect** handles side effects:

```jsx
useEffect(() => {
  console.log("Component mounted!");
}, []);
```

---

### 1️⃣3️⃣ What is the difference between controlled and uncontrolled components?

- **Controlled components**: State is handled by React.
- **Uncontrolled components**: State is handled by the DOM.

```jsx
// Controlled
<input value={text} onChange={(e) => setText(e.target.value)} />
```

---

### 1️⃣4️⃣ What is prop drilling, and how can it be avoided?

**Prop drilling** happens when data is passed **through multiple components** unnecessarily.
**Solution**: Use Context API or Redux.

---

### 1️⃣5️⃣ What is React.memo, and how does it help with performance?

**React.memo** prevents re-renders if props **haven't changed**.

```jsx
const MemoComponent = React.memo(MyComponent);
```

---

### 1️⃣6️⃣ What is the difference between useMemo and useCallback?

- **useMemo**: **Caches a computed value**.
- **useCallback**: **Caches a function**.

```jsx
const memoizedValue = useMemo(() => expensiveFunction(), []);
```

---

### 1️⃣7️⃣ What is React Router, and how does client-side navigation work?

React Router enables **single-page application (SPA) navigation** without refreshing the page.

```jsx
<BrowserRouter>
  <Route path="/home" element={<Home />} />
</BrowserRouter>
```

---

### 1️⃣8️⃣ What is Context API, and when should it be used over Redux?

Context API **shares state globally** without prop drilling. It’s best for **small apps**, whereas Redux is better for **large-scale state management**.

---

### 1️⃣9️⃣ What are Higher-Order Components (HOCs), and how do they work?

HOCs are functions that take a **component as input** and return an **enhanced component**.

```jsx
const withAuth = (Component) => (props) => {
  return isAuthenticated ? <Component {...props} /> : <Login />;
};
```

---



