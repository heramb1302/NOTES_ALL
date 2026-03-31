
## Main Topics

- Make Object in state
    
- Display Object values
    
- Update object key
    
- Update nested object key
    
- Interview Questions

```jsx
import { useState } from 'react';

export const UpdateObject = () => {
  const [data, setData] = useState({
    name: 'John',
    age: 30,
    city: 'New York',
  });

  

  const handleUpdate = () => {

    const newName = document.getElementById('name').value;
    const newAge = document.getElementById('age').value;
    const newCity = document.getElementById('city').value;
    // 2. Update state using the spread operator
    setData({
      ...data, // Keep existing properties if some are not updated
      name: newName || data.name, // Only update if input isn't empty
      age: newAge ? parseInt(newAge) : data.age,
      city: newCity || data.city,
    });
  };

  return (

    <div>
      <h1>Update Object</h1>
      <p>Name: {data.name}</p>
      <p>Age: {data.age}</p>
      <p>City: {data.city}</p>
      <br />
      <hr />

      <h1>Update Data</h1>
      <input id="name" type="text" placeholder="update name" />
      <input id="age" type="number" placeholder="update age" />
      <input id="city" type="text" placeholder="update city" />
      <button onClick={handleUpdate}>Update Data</button>
    </div>
  );
};
```