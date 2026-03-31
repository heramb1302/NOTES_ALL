## Main Topics

- What is derived state
    
- Understand derived state with example
    
- How it improve performance
    
- Interview Question
```jsx
import { useState } from 'react';

export const DerivedComponents = () => {
  const [users, setUsers] = useState([]);
  const [user, setUser] = useState('');
  
  function handleAdduser() {
    setUsers([...users, user]);
  }

  const totalUsers = users.length;
  const lastUser = users[users.length - 1];
  const uniqUsers = [...new Set(users)];
  console.log(users);
  
  return (
    <div>
      <h1>Derived Components</h1>
      <hr />
      <br />
      <h1>Total Users</h1>
      <p>{totalUsers}</p>
      <h1>Last User</h1>
      <p>{lastUser}</p>
      <h1>Uniq Users:</h1>
      <p>{uniqUsers.length}</p>

      <input
        onChange={(e) => setUser(e.target.value)}
        type="text"
        placeholder="Add user"
      />

  

      <button onClick={handleAdduser}>Add User</button>
      {users.map((user, index) => {
        return <h2 key={index}>{user}</h2>;
      })}
    </div>
  );
};
```

