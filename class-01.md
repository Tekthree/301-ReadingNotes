# Reading Notes
## Class 01

### Introduction to React and Components

### What is React

- React is a declarative, efficient, and flexible JavaScript library for building user interfaces. It lets you compose complex UIs from small and isolated pieces of code called “components”.
- We use components to tell React what we want to see on the screen. When our data changes, React will efficiently update and re-render our components.
- A component takes in parameters, called props (short for “properties”), and returns a hierarchy of views to display via the render method.
- The render method returns a description of what you want to see on the screen.
- In particular, render returns a React element, which is a lightweight description of what to render.
- Most React developers use a special syntax called “JSX” which makes these structures easier to write.
- You can compose and render custom React components. For example, we can now refer to the whole shopping list by writing ```<ShoppingList />```. Each React component is encapsulated and can operate independently; this allows you to build complex UIs from simple components.


### Why JSX

- Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both.
- 
