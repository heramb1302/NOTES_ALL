
## Main Topics

- What is ForwardRef in React JS
    
- Implement ForwardRef before react 19 version
    
- Implement ForwardRef in react 19
    
- Interview Question
```jsx

ForwardRef.jsx

import { useRef } from 'react';
import { InputRefForward } from './InputRefForward';

export const Forwardref = () => {
  const inputRef = useRef(null);
  const updateRef = () => {
    inputRef.current.focus();
    inputRef.current.placeholder = 'Updated';
  };
  return (
    <div>
      <InputRefForward ref={inputRef} />
      <button onClick={updateRef}>Click me</button>
    </div>
  );
};


InputRefForward.jsx
export const InputRefForward = (props) => {
  return (
    <div>
      <input type="text" ref={props.ref} placeholder="Enter" />
    </div>
  );
};
```