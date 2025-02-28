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

# 📌 React Interview Questions (Moderate to Difficult)

## 🔥 Performance & Optimization

### 2️⃣0️ How does React handle re-renders, and how can you prevent unnecessary renders?

React re-renders a component when:
- The component's **state** or **props** change.
- The **parent component re-renders**.

Ways to prevent unnecessary re-renders:
- **Use `React.memo()`** to avoid re-rendering if props haven’t changed.
- **Use `useCallback()` and `useMemo()`** to optimize functions and computed values.
- **Optimize state updates** by keeping minimal and required states.

Example:

```jsx
const OptimizedComponent = React.memo(({ name }) => {
  console.log("Rendering...");
  return <h1>Hello, {name}!</h1>;
});
```

---

### 2️⃣1️ What is reconciliation in React?

Reconciliation is the **process of updating the DOM efficiently** by comparing the Virtual DOM with the previous state and applying minimal changes.

React uses the **diffing algorithm** to detect changes and update only the modified parts.

---

### 2️⃣2️ Explain React’s diffing algorithm and why it’s important.

React's **diffing algorithm** optimizes updates by:
1. **Comparing Virtual DOM changes**.
2. **Using a "key" prop** to track elements in lists.
3. **Minimizing DOM updates** by only changing the necessary parts.

Importance:
- Improves **performance**.
- Reduces **unnecessary re-renders**.

Example:

```jsx
<ul>
  {items.map((item) => (
    <li key={item.id}>{item.name}</li>
  ))}
</ul>
```

---

### 2️⃣3️ What is `React.lazy` and `Suspense`, and how do they enable lazy loading?

**Lazy loading** helps load components **only when needed**, improving initial page load performance.

- **`React.lazy()`** dynamically loads a component.
- **`Suspense`** is used to show a fallback while loading.

Example:

```jsx
const LazyComponent = React.lazy(() => import("./MyComponent"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}
```

---

### 2️⃣4️ How do error boundaries work, and why are they useful?

Error boundaries catch **JavaScript errors** in React components and prevent crashes.

- They use **`componentDidCatch`** (Class Components) or **Error Boundary HOCs**.

Example:

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error("Error caught:", error, info);
  }

  render() {
    return this.state.hasError ? <h1>Something went wrong.</h1> : this.props.children;
  }
}
```

Usage:

```jsx
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```

---

### 2️⃣5️ How do you handle authentication and protected routes in React?

React **authentication** is typically handled using JWT tokens and protected routes.

Steps:
1. Store the **auth token** in **localStorage** or **cookies**.
2. Create a **Protected Route** component.

Example:

```jsx
const ProtectedRoute = ({ children }) => {
  return isAuthenticated ? children : <Navigate to="/login" />;
};

<Route path="/dashboard" element={<ProtectedRoute><Dashboard /></ProtectedRoute>} />
```

---

### 2️⃣6️ What are render props, and how do they compare to HOCs?

**Render Props** allow components to **share logic** by passing a function as a prop.

Example:

```jsx
const MouseTracker = ({ render }) => {
  const [position, setPosition] = useState({ x: 0, y: 0 });

  return <div onMouseMove={(e) => setPosition({ x: e.clientX, y: e.clientY })}>
    {render(position)}
  </div>;
};

<MouseTracker render={({ x, y }) => <h1>Mouse at ({x}, {y})</h1>} />
```

**Comparison with HOCs:**
- **HOCs** wrap components and add extra logic.
- **Render Props** use functions to pass logic dynamically.

---

## ⚙️ Advanced React & Server-Side Features

### 2️⃣7️ What is the difference between Server-Side Rendering (SSR) and Client-Side Rendering (CSR)?

| Feature          | Server-Side Rendering (SSR) | Client-Side Rendering (CSR) |
|-----------------|---------------------------|---------------------------|
| Where it runs   | Server generates HTML     | Browser renders UI       |
| Performance     | Faster initial load       | Slower initial load      |
| SEO            | Better for SEO            | Not SEO-friendly         |

**Example: Next.js (SSR)**

```jsx
export async function getServerSideProps() {
  const data = await fetchAPI();
  return { props: { data } };
}
```

---

### 2️⃣8️ What is React Fiber, and how does it improve rendering?

**React Fiber** is the new **reconciliation algorithm** introduced in React 16 for:
- **Faster rendering** using a priority-based update system.
- **Interruptible rendering** for smoother user experience.

---

### 2️⃣9️ What is Concurrent Mode, and how does it enhance performance?

**Concurrent Mode** allows React to **pause and resume rendering**, making apps more responsive.

Example:

```jsx
import { createRoot } from "react-dom/client";

const root = createRoot(document.getElementById("root"));
root.render(<App />);
```

**Benefits:**
- **Non-blocking UI updates**.
- **Better handling of large lists**.

---

### 3️⃣0️ How do you test React components? What are the most common testing libraries?

**Common Testing Libraries:**
- **Jest** (unit testing)
- **React Testing Library** (DOM testing)
- **Cypress** (end-to-end testing)

**Example Test (Jest + React Testing Library):**

```jsx
import { render, screen } from "@testing-library/react";
import MyComponent from "./MyComponent";

test("renders the correct text", () => {
  render(<MyComponent />);
  expect(screen.getByText("Hello, World!")).toBeInTheDocument();
});
```





