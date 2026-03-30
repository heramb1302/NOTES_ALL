
## Main Topics

- Why we need to pass function as props
    
- Make Parent and child component
    
- Call function from parent to child component.
    
- Passing event, there is no such thing

```jsx
export const PassFunc = ({ display }) => {
  return (
    <div>
      <button onClick={display}>Click</button>
    </div>
  );
};
```

```jsx
App.jsx
import { PassFunc } from './Components/PassFunc';

  

function App() {

  function display() {

    alert('clicked');

  }

  return (

    <div className="App">

      <PassFunc display={display} />

    </div>

  );

}

  

export default App;
```