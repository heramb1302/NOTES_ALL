
**Handle Checkbox**

- Make checkbox
    
- Define state for checkbox
    
- Get checkbox value in State
    
- Remove checkbox value in State
    


# React Checkbox State Array Example

**Tags:** #react #useState #forms #checkbox #frontend
**Description:** A React component demonstrating how to manage multiple checkboxes using a single array in state.

```jsx
import { useState } from 'react';

export const CheckBoxes = () => {
  const [skills, setSkills] = useState([]);
  
  const handleChange = (event) => {
    if (event.target.checked) {
      // Add the value to the array if checked
      setSkills([...skills, event.target.value]);
    } else {
      // Remove the value from the array if unchecked
      setSkills(skills.filter((skill) => skill !== event.target.value));
    }
  };

  return (
    <div>
      <h1>CheckBoxes Component</h1>
      
      <input onChange={handleChange} type="checkbox" id="php" value="PHP" />
      <label htmlFor="php">PHP</label>

      <input
        onChange={handleChange}
        type="checkbox"
        id="python"
        value="Python"
      />
      <label htmlFor="python">Python</label>
      
      <input onChange={handleChange} type="checkbox" id="java" value="Java" />
      <label htmlFor="java">Java</label>

      {/* Displays the selected skills separated by commas */}
      <h1>{skills.join(', ')}</h1>
    </div>
  );
};

function App() {

  return (

    <div>

      <CheckBoxes />

    </div>

  );

}

  

export default App;