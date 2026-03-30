

# Component Life Cycle in React

- **What is life cycle in human**
- **What is life cycle in React component**
- **Phase of life cycle** 
- **How to use useEffect to handle life cycle**
- **Interview Questions**

![[Pasted image 20260326155349.png]]

# 1. Mounting -->

```jsx
export const LifeCycle = () => {
  useEffect(() => {
    console.log('Component mounted');
  }, []);
  return (
    <div>
      <h1>LifeCycle Component</h1>
    </div>
  );
};
```

# 2.Updating -->

```jsx
export const LifeCycle = () => {

  const [data, setData] = useState('Initial Data');

  useEffect(() => {
    console.log('Component mounted');
  }, []);

  useEffect(() => {
    console.log('Updating Data ...');
    console.log('Data updated:', data);
  }, [data]);

  return (
    <div>
      <h1>LifeCycle Component</h1>
      <p>{data}</p>
      <button onClick={() => setData('Updated Data')}>Update Data</button>
    </div>
  );
};
```

# 3.Unmount -->

```jsx
export const LifeCycle = () => {
  const [data, setData] = useState('Initial Data');
  const [toggle, setToggle] = useState(true);
  
  useEffect(() => {
    console.log('Component mounted');
  }, []);

  useEffect(() => {
    console.log('Updating Data ...');
    console.log('Data updated:', data);
  }, [data]);

  useEffect(() => {
    console.log('Component unmounted');
  }, [toggle]);
  
  return (
    <div>
      <h1>LifeCycle Component</h1>
      {toggle && <p>{data}</p>}
      <button onClick={() => setData('Updated Data')}>Update Data</button>

      <button onClick={() => setToggle(!toggle)}>Toggle Component</button>
    </div>
  );
};
```