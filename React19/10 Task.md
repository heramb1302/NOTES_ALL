
# React JS Task for Props

**Tags:** #react #props #components #task #frontend
**Description:** A practice task for understanding how to pass dynamic styling (like color) via props to a React component.

* Make Clock Component
* Where Clock color can change with Props


# React Live Clock with Color State

**Tags:** #react #useEffect #useState #setInterval #frontend
**Description:** A React component that creates a live digital clock using `useEffect` and `setInterval`. It includes a dropdown to change the clock's text color dynamically and properly cleans up the interval to prevent memory leaks.

```jsx
import { useState, useEffect } from 'react';

export const Clock = () => {
  const [time, setTime] = useState('Loading...');
  const [color, setColor] = useState('black');

  useEffect(() => {
    // Store the interval ID in a variable
    const intervalId = setInterval(() => {
      setTime(new Date().toLocaleTimeString());
    }, 1000);

    // CLEANUP FUNCTION: This is crucial! 
    // It stops the interval when the component is removed from the screen.
    return () => clearInterval(intervalId);
  }, []); // Empty dependency array means this runs once when the component loads

  return (
    <div>
      <h1>Clock Component</h1>
      
      <select onChange={(e) => setColor(e.target.value)}>
        <option value="red">Red</option>
        <option value="green">Green</option>
        <option value="blue">Blue</option>
      </select>
      
      <h2 style={{ color: color }}>Time: {time}</h2>
    </div>
  );
};