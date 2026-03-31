
## Main Topics

- Make Object in state
    
- Display Object values
    
- Update object key
    
- Update nested object key
    
- Interview Questions


```jsx
import { useState } from 'react';

export const UpdateArray = () => {
  const [items, setItems] = useState(['Apple', 'Banana', 'Orange']);
  // 1. Add an item (Spread Operator)
  const addItem = () => {

    const newItem = document.getElementById('itemInput').value;

    if (newItem) {

      setItems([...items, newItem]); // Adds to the end

      document.getElementById('itemInput').value = ''; // Clear input

    }

  };

  

  // 2. Update an item (Map)

  const updateItem = (index) => {

    const updatedValue = prompt('Enter new name:', items[index]);

    if (updatedValue) {

      const newArray = items.map((item, i) =>

        i === index ? updatedValue : item,

      );

      setItems(newArray);

    }

  };

  

  // 3. Remove an item (Filter)

  const removeItem = (index) => {

    const newArray = items.filter((_, i) => i !== index);

    setItems(newArray);

  };

  

  return (

    <div>

      <h1>Update Array State</h1>

      <ul>

        {items.map((item, index) => (

          <li key={index}>

            {item}

            <button onClick={() => updateItem(index)}>Edit</button>

            <button onClick={() => removeItem(index)}>Delete</button>

          </li>

        ))}

      </ul>

  

      <hr />

      <input id="itemInput" type="text" placeholder="Add new fruit" />

      <button onClick={addItem}>Add Item</button>

    </div>

  );

};
```