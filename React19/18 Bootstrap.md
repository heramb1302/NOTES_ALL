## Main Topics

- What is Bootstrap
    
- How to install Bootstrap in React JS
    
- Bootstrap examples e.g. button, alerts
    
- Interview Question e.g. button, alerts
```jsx
import React, { useState } from 'react';

import { Button, Alert, ButtonGroup } from 'react-bootstrap';

// Ensure you have the CSS imported!

import 'bootstrap/dist/css/bootstrap.min.css';

import ColorSchemesExample from './Components/Navebar';

  

function App() {

  // 1. Create a state variable to track if the alert is visible

  const [show, setShow] = useState(false);

  

  return (

    <div className="p-5">

      <ColorSchemesExample />

      <h1>Add Bootstrap in React</h1>

      <Button variant="success">Ok</Button>

      <Alert variant="danger">Hello Botstrap Installed...</Alert>

    </div>

  );

}

  

export default App;
```