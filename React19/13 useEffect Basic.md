
# React useEffect Hook Overview

**Tags:** #react #hooks #useEffect #lifecycle #frontend
**Description:** Core concepts and topics to cover when learning about the `useEffect` hook in React.

* What is use of useEffect
* What example we will take in this part
* Syntax of useEffect
* Use Effect with state
* Use Effect with props
* Interview Question


# Basic Use of useEffect

**Tags:** #react #useEffect #hooks #performance #interview-prep
**Description:** The primary use case for `useEffect` and its importance in React interviews.

* Prevent Extra rendering of component on state
* Very Important for interview.

## Syntax

```jsx
useEffect(() => {
  // Your code (the "Effect") goes here
  
  return () => {
    // Optional: Cleanup code goes here
  };
}, [dependencies]); // The dependency array
```

## Programme 



```jsx
import { useState, useEffect } from 'react';

export const UseEffectDemo = () => {
  const [counter, setCounter] = useState(0);
  const [data, setData] = useState(0);
    // Logic for Counter
  function Call() {
    console.log('Call Counter:', counter);
  }
  // Logic for Data
  function Call2() {
    console.log('Call Data:', data);
  }
  // Effect 1: Fires ONLY when 'counter' changes
  useEffect(() => {
    Call();
  }, [counter]);
  // Effect 2: Fires ONLY when 'data' changes
  useEffect(() => {
    Call2();
  }, [data]);
  
  return (
    <div style={{ padding: '20px', textAlign: 'center' }}>
      <h1>UseEffectDemo Component</h1>
      
      <button onClick={() => setCounter(counter + 1)}>
        Counter : <h2>{counter}</h2>
      </button>

      <button onClick={() => setData(data + 1)}>
        Data: <h2>{data}</h2>
      </button>

      <br /><br />

      <button onClick={() => { setCounter(0); setData(0); }}>
        Reset All
      </button>
    </div>
  );
};
```

| **Dependency Array**                                 | **When it runs**                                         | **Analogy**                                                            |
| ---------------------------------------------------- | -------------------------------------------------------- | ---------------------------------------------------------------------- |
| **No Array** `useEffect(() => { ... })`              | **Every render.** (After every state/prop change)        | A gossipy neighbor who talks every time someone walks by.              |
| **Empty Array** `useEffect(() => { ... }, [])`       | **Once.** (Only when the component first appears/mounts) | A "Welcome" sign that only goes up when you move in.                   |
| **One Variable** `useEffect(() => { ... }, [state])` | **When `state` changes.**                                | A smoke alarm that only goes off when it senses smoke.                 |
| **Multiple Variables** `[prop, state]`               | **When ANY of them change.**                             | A doorbell that rings if _either_ the front or back button is pressed. |