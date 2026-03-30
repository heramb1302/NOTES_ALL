
**Handle Radio and Dropdown**

- Make Radio buttons
    
- Get Radio button value in state
    
- Default selection of Radio button
    
- Get Dropdown value in state
    
- Default selection in dropdown

# React Radio Buttons and Dropdown State

**Tags:** #react #useState #forms #radio #dropdown #frontend
**Description:** A React component demonstrating how to control radio buttons and a `<select>` dropdown menu using `useState`.

```jsx
import { useState } from 'react';

export const RadioDropdown = () => {
  const [gender, setGender] = useState('male');
  const [city, setCity] = useState('tokyo'); // Matched case to the option value

  return (
    <div>
      <h1>Radio Dropdown Component</h1>
      
      {/* --- RADIO BUTTONS --- */}
      <h2>Select Gender: </h2>
      <input
        onChange={(event) => setGender(event.target.value)}
        type="radio"
        name="gender"
        id="male"
        value="male"
        checked={gender === 'male'}
      />
      <label htmlFor="male">Male</label>
      
      <input
        onChange={(event) => setGender(event.target.value)}
        type="radio"
        name="gender"
        id="female"
        value="female"
        checked={gender === 'female'}
      />
      <label htmlFor="female">Female</label>

      <h3 style={{ color: 'green' }}>Selected Gender: {gender}</h3>
      
      <hr />

      {/* --- DROPDOWN MENU --- */}
      <h2>Select City</h2>
      <select
        onChange={(event) => setCity(event.target.value)}
        value={city} // Use 'value' instead of 'defaultValue' for controlled components
        name="city"
        id="city"
      >
        <option value="newyork">New York</option>
        <option value="london">London</option>
        <option value="tokyo">Tokyo</option>
      </select>
      
      <h3 style={{ color: 'green' }}>Selected City: {city}</h3>
      <hr />
    </div>
  );
};