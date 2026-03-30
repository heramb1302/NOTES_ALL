
## Controlled Component

- What is Controlled component
    
- How to identify this is a Controlled component
    
- Error if we dont use Controlled value properly.
    
- Make form get input field values.
    
- Display input field values.

- A controlled component is a form whose input field value is controlled by React's state
    
- Here's how it works:
    
- Store input field value in State
    
- Use Change handler with input field
    
- Value attribute attached with State


**Benefits**

- Single source of truth
    
- Validation and Manipulation before submit
    
- Dynamic updates values

## Programme:

function App() {
  const [name, setName] = useState('');
  const [sirname, setSirname] = useState('');
  const [phone, setPhone] = useState('');

  return (
    <div>
      <form>
        <input
          value={name}
          type="text"
          placeholder="enter name"
          onChange={(e) => setName(e.target.value)}
        />
        <input
          value={sirname}
          type="text"
          placeholder="enter sirname"
          onChange={(e) => setSirname(e.target.value)}
        />
        <input
          value={phone}
          type="text"
          placeholder="enter phone"
          onChange={(e) => setPhone(e.target.value)}
        />
        <button>Submit</button>
        <h1>Name: {name}</h1>
        <h1>Sirname: {sirname}</h1>
        <h1>Phone: {phone}</h1>
      </form>
    </div>
  );
}





