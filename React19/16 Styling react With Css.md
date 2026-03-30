## Styling React Using CSS

- **How many type of Style we have in React js?**
    
    - Inline Style
    - External style
    - CSS Modules
    - Styled Components
    - External CSS Library/Framework

## **1 Inline Style : 

In React, **inline styles** are written as JavaScript objects rather than plain strings. This is because React's JSX needs to differentiate between HTML attributes and actual logic.
```jsx
const MyComponent = () => {
  return (
    <div style={{ backgroundColor: 'lightblue', padding: '20px', borderRadius: '8px' }}>
      Hello, styling!
    </div>
  );
};
```



## **2 External Style:**

Overview

External CSS involves defining your styles in a dedicated stylesheet rather than inside the component file. This helps maintain a clean separation of concerns.

 Key Concepts

- **Separate Files:** Create a specific `.css` file (e.g., `styles.css`) for your styling rules.
    
- **Importing:** Use the `import` statement at the top of your React component file to apply the styles.


## **3 Styled Components in React**

Overview

**Styled-components** is a popular library for React and React Native that uses **tagged template literals** to style your components. This approach is known as **CSS-in-JS**.

 Key Concepts

- **CSS-in-JS:** Allows you to write actual CSS code directly within your JavaScript component files.
    
- **Component-Level Styling:** Styles are tightly coupled with the component, preventing global scope leaks and class name collisions.
    
- **Dynamic Styling:** You can use props to change styles dynamically using standard JavaScript logic.

Installation

To use this library, you first need to install it via npm or yarn: `npm install styled-components`

```jsx
import styled from 'styled-components';
// Create a styled component
const Button = styled.button`
  background-color: ${props => props.primary ? 'blue' : 'gray'};
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  &:hover {
    opacity: 0.8;
  }
`;

// Use it like a regular React component
function App() {
  return (
    <div>
      <Button primary>Primary Button</Button>
      <Button>Default Button</Button>
    </div>
  );
}
```



# **4.External css**
#### Utility-First & UI Libraries in React

Overview

Utility-first libraries and UI frameworks provide pre-built styling solutions that allow developers to build interfaces rapidly without writing custom CSS from scratch.

Featured Libraries

- **Material-UI (MUI):** A popular component library that implements Google's Material Design. It provides ready-to-use components like buttons, sliders, and navigation bars.
    
- **React Bootstrap:** Replaces standard Bootstrap JavaScript with React components, giving you the power of Bootstrap's grid and components without needing jQuery.
    
- **Tailwind CSS:** A utility-first CSS framework that provides low-level utility classes (e.g., `flex`, `pt-4`, `text-center`) to build custom designs directly in your markup.
  
  
  ```jsx
import './Styles/Style.css';
function App() {
  return (
    <div>
      <h1 className="heading">External Styles</h1>
      <div className="container">
        <div className="usercard">
          <div>
         <img
              className="image"
              src="https://www.algolia.com/files/live/sites/algolia-assets/files/blogs/bannerimages/how-we-unit-test-react-components-using-expect-jsx.webp"
              alt=""
            />
          </div>
          <div className="textarea">
            <h4>Heramb Shinde</h4>
            <p>React Engineer</p>
          </div>
        </div>
        <div className="usercard">
          <div>
            <img
              className="image"
              src="https://www.algolia.com/files/live/sites/algolia-assets/files/blogs/bannerimages/how-we-unit-test-react-components-using-expect-jsx.webp"
              alt=""
          />
          </div>
          <div className="textarea">
            <h4>Heramb Shinde</h4>
            <p>React Engineer</p>
          </div>
        </div>
      </div>
    </div>
  );
}
export default App;
  ```




```jsx
style.css


.heading {

  color: red;

}

.image {

  width: 130px;

}

.usercard {

  width: 130px;

  border: 1px solid #ddd;

  box-shadow: 1px 1px 1px 1px #ddd;

  margin: 10px;

}

.textarea {

  padding: 10px;

}

  

.container {

  display: flex;

  flex-wrap: wrap;

}
```