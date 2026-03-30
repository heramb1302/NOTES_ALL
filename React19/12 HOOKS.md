
# Hooks in React JS

**Tags:** #react #hooks #frontend #concepts #interview-prep
**Description:** Core concepts and common interview topics regarding React Hooks.

* What are hooks
* Why we need hooks
* History of hooks
* Some hooks name
* How to identify hooks
* Interview Question

# React Hooks: Core Concepts

**Tags:** #react #hooks #concepts #frontend
**Description:** A fundamental overview of what React Hooks are, why they exist, and how to identify them.

### 1. What are Hooks?
Hooks are special built-in JavaScript functions that allow you to "hook into" React state and lifecycle features directly from **functional components**. They allow you to use React's core features without needing to write a Class component.

**Tags:** #react #hooks #components #state #frontend
**Description:** A basic definition of why Hooks were introduced in React and what problem they solve.

* In older React versions, we were using **class-based components**.
* Now, class-based components are not used as much in modern React.
* To achieve **State**, **lifecycle methods**, and other features inside **functional components**, we use Hooks.
 
 Popular React Hooks

**Tags:** #react #hooks #state #frontend
**Description:** A quick reference list of the most commonly used built-in React hooks.

* **`useState`**: Manages dynamic data (state) within a functional component.
* **`useEffect`**: Handles side effects like fetching data, setting timers, or manually changing the DOM.
* **`useContext`**: Allows you to access global data (like themes or user sessions) directly, without having to pass props down through every component.
* **`useRef`**: Used to directly target and manipulate a specific DOM element, or to store a mutable value that *doesn't* trigger a re-render when it changes.
* **`useReducer`**: An alternative to `useState` that is better suited for managing complex state logic with multiple sub-values (works very similarly to Redux).
* **etc...** (There are others like `useMemo` and `useCallback` for performance optimization!)
### 2. Why do we need Hooks?
Before Hooks, complex React apps became difficult to maintain. Hooks solve several major problems:
* **Removes Class Confusion:** Classes in JavaScript require understanding how the `this` keyword works, which can be tricky and unpredictable. Hooks let you use standard functions instead.
* **Reusable Stateful Logic:** Previously, sharing logic between components required complex patterns like "Higher-Order Components" or "Render Props," leading to "wrapper hell." Hooks allow you to extract and share stateful logic easily.
* **Cleaner Code Organization:** In class components, related code (like fetching data) was split across different lifecycle methods (`componentDidMount`, `componentDidUpdate`). Hooks (specifically `useEffect`) let you group related logic together in one place.

### 3. History of Hooks
Hooks were officially introduced by the React team (led by developers like Dan Abramov and Sophie Alpert) in **React version 16.8 (February 2019)**. Before this update, functional components were known as "dumb" or "stateless" components because they couldn't hold state or trigger side effects. Hooks revolutionized React by making functional components the standard way to build apps.

### 4. Common Hooks Names
React provides several built-in Hooks. The most frequently used are:
* `useState`: For managing data/state that changes over time.
* `useEffect`: For handling side effects (fetching data, timers, updating the DOM).
* `useRef`: For directly accessing DOM elements or storing mutable values that don't trigger re-renders.
* `useContext`: For accessing global data (like themes or user auth) without passing props down manually.
* `useMemo` & `useCallback`: For performance optimization.

### 5. How to Identify Hooks
You can always identify a hook by looking at its name and where it is placed in the code.
* **The Naming Convention:** They **always** start with the word `use` (e.g., `useState`, `useEffect`, or custom hooks like `useFetch`).
* **The Rules of Hooks:** 1. They can **only** be called inside React functional components (or inside custom hooks).
  2. They must be called at the very **top level** of your component. You cannot put a hook inside an `if` statement, a `for` loop, or a nested function.



