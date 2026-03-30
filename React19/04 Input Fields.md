

## Get Input field Value
 
• Make input field.
• Define State.
• Display value in state.
• Clear input field Value.

const [val, setVal] = useState('Heramb Shinde'); // Example state variable

return (
  <div className="App">
    <input 
      type="text" 
      placeholder="Enter text" 
      onChange={(event) => setVal(event.target.value)}
    />
    
    <h1 style={{color: 'green', padding: '10%'}}>
      <p>{val}</p>, padding: 10%
    </h1>
    
    <button onClick={() => setVal("")}>Clear</button>
  </div>
);

export default App;
