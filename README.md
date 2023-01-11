# React Best Practices for Software Design and Architecture

React is a popular JavaScript library for building user interfaces, and has become a staple in web development. When building applications with React, it is important to consider the design and architecture of your code in order to create a maintainable and scalable solution. In this article, I will share some best practices for software design and architecture when working with React to help you create high-quality applications.

---

## Folder Structure

If you have more than one file for your component, keep your component organized and packaged together. Keep your component, styles, and helpers in their own folder.
```
|__ YourComponent
    |-- YourComponent.jsx
    |-- YourComponent.module.css
    |-- YourComponent.helpers.js
    |-- YourComponent.test.jsx
```

---

## Naming the Components

Naming your components will help you track errors with React Dev Tools. Always name your components.
```
// Don't
function() {...}


// Do
const Counter = () => {...}

export default Counter;
```

---

## Functional Components

We want to keep our syntax consistent with the React team. The React team has moved away from class components. Functional Components have an easy to follow syntax.
```
import React from 'react';

function MyComponent() {
  return (
    <div>MyComponent</div>
  )
}

export default MyComponent
```

---

## De-structure Props

Ensure you are using what you need. Deconstruct your props in your Function component.
```
// Don't
function Component(props) {
  return <div>{props.name}</div>;
}

// Do
function Component({name}) {
  return <div>{name}</div>;
}
```

---

## Assign Default Props

Increase the readability of your component from top to bottom. Assign defaults at the time of de-structuring. Use over defaultProps.
```
// Don't
function Component({name}) {
  return <div>{name}</div>;
}

// Do
function Component({name=""}) {
  return <div>{name}</div>;
}
```

---

## Length of the Component | Single Responsibility

Think about the separation of concerns and keep the logic separate and share data between components. Divide the component into smaller components for re-usability and try to keep each component focused on a single responsibility.

---

## W.E.T. ( Write Everything Twice)

Increase productivity and speed. Limit abstraction from becoming spaghetti code, with conditionals and bugs. Do not rush into abstractions. If you are writing the same code three or four times, now it is time to think about abstraction.

---

## Nested Render Functions

Keep files easy to read and easy to understand. Do not define a component inside another component. Create another component and import.
```
// Don't
function Component() {
  function renderHeader() {
    return <Something>...</Something>
  }
  
  return <div>{renderHeader()}</div>
}

// Do
  function RenderHeader() {
    return <Something>...</Something>
  }

  import RenderHeader from "../RenderHeader.jsx";
  function Component() {

    return <RenderHeader />
}
````

---

## Organizing Helper Functions

To keep the file readable and small, place your helper functions either before or in a separate file that is within the folder structure of the component. You should only be passing the values from the state as arguments to the Helper Functions. Use your best judgement regarding when to extract your helper functions to a new file. Reference Folder Structure.
```
// Don't
function Component({date}) {
  function formatDate(cleanDate) {...}
  
  return <div>Date: {formatDate(date)}</div>
}
  
// Do
function formatDate(cleanDate) {...}

function Component({date}) {
  return <div>Date: {formatDate(date)}</div>
}
                                
// Or
import Utils from "./helperFile.js";
                                
function Component({date}) {
  return <div>Date: {Utils.formatDate(date)}</div>
}                              
```

---

## If Over Nested Ternary Operators

After the first level, Ternary operators become difficult to ready.
```
// Don't
isTest ? <Something /> : isAnotherTest ? <Different /> : <What />;

// Do
if (isTest) {
    return <Something />;
}
if (isAnotherTest) {
    return <Different />;
}
return <What />;
```

---

## Never Hard-code Markup

To keep the code clean and readable, create configuration objects and then map over the items. Do not hard-code markup for filters, navigation, lists, etc.
```
// Don't
function Component({ date }) {
    return (
        <ul>
            <li>
                <div onClick={() => {}}>Fiction</div>
            </li>
            <li>
                <div onClick={() => {}}>Fiction</div>
            </li>
            <li>
                <div onClick={() => {}}>Fiction</div>
            </li>
        </ul>
    );
}

// Do
const ITEMS = [
    {
        identifier: "Something",
        name: Something,
    },
    {
        identifier: "Something",
        name: Something,
    },
    {
        identifier: "Something",
        name: "Something",
    },
];

function Filters({ onFilterClick }) {
    return (
        <ul>
            {ITEMS.map((item) => (
                <li>
                    <div onClick={() => onFilterClick(item.identifier)}>
                        {item.name}
                    </div>
                </li>
            ))}
        </ul>
    );
}
```

---

## Inspect and Debug your React Components

Use the React Developer Tools browser extension to inspect and debug your React components.

---

## Naming Convention

Follow a consistent naming convention, such as camelCase for variables and PascalCase for components.
```
// PascalCase for Components
const MyComponent = () => {
    // camelCase for Variables
    const someVariable = // Code...
}
```

---

In summary, this article covered a range of best practices for software design and architecture when working with React. These practices include organizing your code in a logical folder structure, giving clear names to your components, using functional components and other best practices that I have learned over the years. By following these best practices, you can create maintainable and scalable React applications that are easy to understand and debug. Thank you for taking the time to read my post on React best practices for Software Design and Architecture and wishing you the best in this new year!
