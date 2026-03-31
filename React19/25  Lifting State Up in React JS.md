

## Main Topics

- What is Lifting state up
    
- Make two component
    
- Share data between two component
    
- Interview Questions

```jsx
LiftingState.jsx

import { LiftAdduser } from './LiftAdduser';
import { LiftDisplayUser } from './LiftDisplayUser';
import { useState } from 'react';

export const LiftingState = () => {
  const [userName, setUserName] = useState('');
  return (
    <div>
      <h2>Lifting State</h2>
      <LiftAdduser setUserName={setUserName} />
      <LiftDisplayUser userName={userName} />
    </div>
  );
};
```

```jsx
LiftAdduser.jsx
export const LiftAdduser = ({ setUserName }) => {
  return (
    <div>
      <br />
      <hr />
      <h2>Lift Add User</h2>
      <input
        onChange={(e) => setUserName(e.target.value)}
        type="text"
        placeholder="Enter user name"
      />
      <br />
      <hr />
    </div>
  );
};
```

```jsx
LiftDisplayUser.jsx

export const LiftDisplayUser = ({ userName }) => {
  return (
    <div>
      <h2>Lift Display User</h2>
      <p>User Name: {userName}</p>
    </div>
  );
};
```