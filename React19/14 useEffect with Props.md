
### The Checklist

- [x] **Make Component:** Create a child component that accepts props.
    
- [x] **Pass Props:** Send data from the Parent to the Child.
    
- [x] **Apply useEffect:** Use the hook to listen for changes.
    
- [x] **Dependency Array:** Pass the specific prop into the `[]` array.


```jsx
import { useEffect } from 'react';
export const CounterPropsEffect = ({ counter = 0, data = 0 }) => {

  function handleCounter() {
    console.log('COUNTING STARTED...');
  }
  
  useEffect(() => {
    handleCounter();
  }, []);

  useEffect(() => {
    console.log('Counter Updated : ', counter);
  }, [counter]);

  useEffect(() => {
    console.log('Data Updated : ', data);
  }, [data]);

  return (
    <div>
      <h1>Counter : {counter}</h1>
      <h1>Data : {data}</h1>
    </div>
  );
};
```

```jsx
app.jsx -->

function App() {
  const [count, setCount] = useState(0);
  const [data, setData] = useState(0);
  return (
    <div>
      <CounterPropsEffect counter={count} data={data} />
      <button onClick={() => setCount(count + 1)}>Increment Counter</button>
      <button onClick={() => setData(data + 1)}>Increment Data</button>
    </div>
  );
}
export default App;
```
