

# Nested Looping in React

**Tags:** #react #loops #nested-loops #components #arrays
**Description:** Key steps and concepts for implementing nested loops to render complex, multi-layered data structures in React.

* Understand array structure for nested looping
* Make outer loop
* Make inner loop
* Make component for outer loop
* Make component for inner loop
* Interview Question

# React Nested Loops (Mapping Arrays inside Arrays)

**Tags:** #react #loops #nested-loops #map #arrays #frontend
**Description:** A React component demonstrating how to map through a complex data structure (an array of objects, where each object contains another array) using an outer and inner `.map()` function.

```jsx
export const NestedLoop = () => {
  // Complex data structure: An array of objects containing arrays
  const collageData = [
    {
      name: 'Collage A',
      city: 'City A',
      website: '[www.collagea.com](https://www.collagea.com)',
      student: [
        { name: 'Student A', age: 20, email: 'studenta@example.com' },
        { name: 'Student B', age: 22, email: 'studentb@example.com' },
      ],
    },
    {
      name: 'Collage B',
      city: 'City B',
      website: '[www.collageb.com](https://www.collageb.com)',
      student: [
        { name: 'Student C', age: 21, email: 'studentc@example.com' },
        { name: 'Student D', age: 23, email: 'studentd@example.com' },
      ],
    },
    {
      name: 'Collage C',
      city: 'City C',
      website: '[www.collagec.com](https://www.collagec.com)',
      student: [
        { name: 'Student E', age: 20, email: 'studente@example.com' },
        { name: 'Student F', age: 22, email: 'studentf@example.com' },
      ],
    },
  ];

  return (
    <div>
      <h1>Nested Loop</h1>
      
      {/* OUTER LOOP: Mapping through the collages */}
      {collageData.map((collage, index) => (
        <div
          key={index}
          style={{ border: '1px solid black', padding: '10px', margin: '10px' }}
        >
          <h2>{collage.name}</h2>
          <ul>
            <li>City: {collage.city}</li>
            <li>Website: {collage.website}</li>
            <li>
              Students:
              <ul>
                {/* INNER LOOP: Mapping through the students inside the current collage */}
                {collage.student.map((student, studentIndex) => (
                  <li key={studentIndex}>
                    Name: {student.name}, Age: {student.age}, Email: {student.email}
                  </li>
                ))}
              </ul>
            </li>
          </ul>
        </div>
      ))}
    </div>
  );
};