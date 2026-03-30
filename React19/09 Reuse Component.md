

# Reuse Component in Loop

**Tags:** #react #components #map #loops #frontend
**Description:** Key steps for reusing a React component within a mapping function.

* Make Component.
* Apply Map for loop in JSX.
* Render Component in Loop.
* Pass data in component inside loop.
* Add Style.
* Interview Question
  
  
  # Passing Data via Props & Reusing Components

**Tags:** #react #props #components #map #frontend
**Description:** A complete example showing how to define an array of data in a parent component (`App`) and pass it down as a prop to a child component (`ReuseComponent`) which maps through the data to render styled list items.

### 1. The Child Component (`ReuseComponent.jsx`)
This component accepts a prop called `data`. It doesn't care where the data comes from, as long as it's an array it can loop through!

```jsx
export const ReuseComponent = ({ data }) => {
  return (
    <div>
      <h1>Reuse Component Example</h1>
      
      {data.map((user) => (
        // The 'key' prop only needs to be on the outermost wrapper element
        <div
          key={user.id}
          style={{
            border: '1px solid black',
            padding: '10px',
            margin: '10px',
            borderRadius: '5px',
            borderBlockColor: 'blue',
          }}
        >
          <p style={{ color: 'blue', fontSize: '18px' }}>
            ID: {user.id}, Name: {user.name}, Age: {user.age}
          </p>
        </div>
      ))}
    </div>
  );
};

**App.jsx
import { ReuseComponent } from './ReuseComponent';

function App() {
  // The data lives here in the parent
  const userData = [
    { id: 1, name: 'Alice', age: 25 },
    { id: 2, name: 'Bob', age: 30 },
    { id: 3, name: 'Charlie', age: 35 },
  ];

  return (
    <div>
      {/* Passing the userData array into the 'data' prop */}
      <ReuseComponent data={userData} />
    </div>
  );
}

export default App;