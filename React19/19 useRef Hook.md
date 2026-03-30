
# useRef Hook in React

## Main Topics

- What is useRef hook?
    
- Learn how to use useRef.
    
- Control input field with useRef.
    
- Hide and show input field with useRef.



```jsx
import { useRef } from 'react';

export const UseRefFunc = () => {
  const inputRef = useRef(null);

  const inputhandler = () => {
    console.log(inputRef);
    inputRef.current.focus();
    inputRef.current.style.color = 'red';
    inputRef.current.style.backgroundColor = 'yellow';
    inputRef.current.placeholder = 'enter pass';
  };

  

  return (
    <div>
      <h1>Use Ref </h1>
      <input ref={inputRef} type="text" placeholder="Enter name" />
      <button onClick={inputhandler}>Focus</button>
    </div>
  );
};
```