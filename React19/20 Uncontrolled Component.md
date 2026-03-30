
## Main Topics

- What is Uncontrolled component?
    
- Make Uncontrolled component with querySelector.
    
- Make Uncontrolled component with useRef.

```jsx
import { useRef } from 'react';

export const UncontrolledComponent = () => {
  // --- Standard DOM Method Logic ---
  function handleForm(e) {
    e.preventDefault();
    // This looks for 'user' and 'passward' IDs in the first form
    const user = document.getElementById('user').value;
    const passward = document.getElementById('passward').value;
    console.log('Username (DOM):' + user);
    console.log('Passward (DOM):' + passward);
  }
  // --- useRef Method Logic ---
  // FIX 1: Change function calls to 'useRef()'
  const userRef = useRef(null);
  const passwardRef = useRef(null);
  
  function handleFormRef(e) {
    e.preventDefault();
    // FIX 2: Accessing .current.value
    console.log('Username (useRef):' + userRef.current.value);
    console.log('Passward (useRef):' + passwardRef.current.value);
  }
  return (
    <div>
      {/* SECTION 1: Standard JS DOM approach */}
      <h1>Uncontrolled Component (DOM ID)</h1>
      <form onSubmit={handleForm}>
        <input type="text" id="user" placeholder="Enter name" />
        <br />
        <input type="password" id="passward" placeholder="Enter password" />
        <br />
       <button type="submit">Submit</button>
      </form>
      <br />
      <hr />
      <br />
      
      {/* SECTION 2: React useRef approach */}
      <h1>Uncontrolled Component using Ref</h1>
      <form onSubmit={handleFormRef}>
        {/* FIX 3: Use the ref={} attribute instead of id */}
        <input type="text" ref={userRef} placeholder="Enter name" />
        <br />
        <input type="password" ref={passwardRef} placeholder="Enter password" />
        <br />
        <button type="submit">SubmitRef</button>
      </form>
    </div>
  );
};
```