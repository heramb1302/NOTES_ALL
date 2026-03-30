
**Loop in JSX with Map Function**

- What is Array
    
- Make Array
    
- Make table in JSX
    
- Use map table in JSX for looping


# React Rendering Lists (Loops) with Map

**Tags:** #react #map #arrays #lists #frontend
**Description:** A React component demonstrating how to loop through an array of objects using the `.map()` method to render an HTML table. It includes the required `key` prop on the dynamically generated list items.

```jsx
export const Loops = () => {
  const userData = [
    { id: 1, name: 'Alice', age: 25 },
    { id: 2, name: 'Bob', age: 30 },
    { id: 3, name: 'Charlie', age: 35 },
  ];

  return (
    <div>
      <h1>Loops Example</h1>

      <table border="1">
        <thead>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Age</th>
          </tr>
        </thead>
        <tbody>
          {/* Mapping over the userData array to create table rows */}
          {userData.map((user) => (
            <tr key={user.id}>
              <td>{user.id}</td>
              <td>{user.name}</td>
              <td>{user.age}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
};

