# Reading Notes
## Class 03
_____________________________________________________________________________________________________________________________________


### Introduction to React

### Passing Functions as Props

- To share the same data with several other components, we need to lift up state to their closest common ancestors.

```
function BoilingVerdict(props) {
  if (props.celsius >= 100) {
    return <p>The water would boil.</p>;
  }
  return <p>The water would not boil.</p>;
}
```

- add a component that renders an <input> and keeps the value in this.state.temperature

```
class Calculator extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
    this.state = {temperature: ''};
  }

  handleChange(e) {
    this.setState({temperature: e.target.value});
  }

  render() {
    const temperature = this.state.temperature;
    return (
      <fieldset>
        <legend>Enter temperature in Celsius:</legend>
        <input
          value={temperature}
          onChange={this.handleChange} />
        <BoilingVerdict
          celsius={parseFloat(temperature)} />
      </fieldset>
    );
  }
}
```

- we want to have celsius as well and keep them in sync.

```
const scaleNames = {
  c: 'Celsius',
  f: 'Fahrenheit'
};

class TemperatureInput extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
    this.state = {temperature: ''};
  }

  handleChange(e) {
    this.setState({temperature: e.target.value});
  }

  render() {
    const temperature = this.state.temperature;
    const scale = this.props.scale;
    return (
      <fieldset>
        <legend>Enter temperature in {scaleNames[scale]}:</legend>
        <input value={temperature}
               onChange={this.handleChange} />
      </fieldset>
    );
  }
}
```

- Now we can have the calculator render two separate temperature inputs

```
class Calculator extends React.Component {
  render() {
    return (
      <div>
        <TemperatureInput scale="c" />
        <TemperatureInput scale="f" />
      </div>
    );
  }
}
```

- Now we write two functions to convert from Celsius to Fahrenheit and back

```

function toCelsius(fahrenheit) {
  return (fahrenheit - 32) * 5 / 9;
}

function toFahrenheit(celsius) {
  return (celsius * 9 / 5) + 32;
}

```

- This is both temeratureInput components independently keeping their values in the local state.

```
class TemperatureInput extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
    this.state = {temperature: ''};
  }

  handleChange(e) {
    this.setState({temperature: e.target.value});
  }

  render() {
    const temperature = this.state.temperature;
    // ...  
 ```
 
 - In React, sharing state is accomplished by moving it up to the closest common ancestor of the components that need it. This is called “lifting state up”.

- Make the component “controlled”. Just like the DOM <input> accepts both a value and an onChange prop, so can the custom TemperatureInput accept both temperature and onTemperatureChange props from its parent Calculator.

```
 handleChange(e) {
    // Before: this.setState({temperature: e.target.value});
    this.props.onTemperatureChange(e.target.value);
    // ...
```


- there should be a single “source of truth” for any data that changes in a React application

- Instead of trying to sync the state between different components, you should rely on the top-down data flow.

- Lifting state involves writing more “boilerplate” code than two-way binding approaches, but as a benefit, it takes less work to find and isolate bugs. Since any state “lives” in some component and that component alone can change it, the surface area for bugs is greatly reduced
- If something can be derived from either props or state, it probably shouldn’t be in the state.
- When you see something wrong in the UI, you can use React Developer Tools to inspect the props and move up the tree until you find the component responsible for updating the state. This lets you trace the bugs to their source:

### Lists and Keys

```
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);
```

```
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);
```
- include the entire listItems array inside a <ul> element, and render it to the DOM:

```
ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);
```

- refactor the previous example into a component that accepts an array of numbers and outputs a list of elements.

```
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li>{number}</li>
  );
  return (
    <ul>{listItems}</ul>
  );
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);
```

### Spread Operators

- the … spread operator is useful for many different routine tasks in JavaScript, including the following:

Copying an array
Concatenating or combining arrays
Using Math functions
Using an array as arguments
Adding an item to a list
Adding to state in React
Combining objects
Converting NodeList to an array

```

[...["😋😛😜🤪😝"]] // Array [ "😋😛😜🤪😝" ]
[..."🙂🙃😉😊😇🥰😍🤩!"] // Array(9) [ "🙂", "🙃", "😉", "😊", "😇", "🥰", "😍", "🤩", "!" ]

const hello = {hello: "😋😛😜🤪😝"}
const world = {world: "🙂🙃😉😊😇🥰😍🤩!"}

const helloWorld = {...hello,...world}
console.log(helloWorld) // Object { hello: "😋😛😜🤪😝", world: "🙂🙃😉😊😇🥰😍🤩!" }
```

coping an array

```

const fruits = ['🍏','🍊','🍌','🍉','🍍']
const moreFruits = [...fruits];
console.log(moreFruits) // Array(5) [ "🍏", "🍊", "🍌", "🍉", "🍍" ]
fruits[0] = '🍑'
console.log(...[...fruits,'...',...moreFruits]) //  🍑 🍊 🍌 🍉 🍍 ... 🍏 🍊 🍌 🍉 🍍
```


- Adding to state in React

```

import React, { useState } from "react"
import ReactDOM from "react-dom"

import "./styles.css"

function App() {
  // React Hooks declarations
  const [searches, setSearches] = useState([])
  const [query, setQuery] = useState("")

  const handleClick = () => {
    // Add the search term to the list onClick of Search button
    // (Actually searching would require an API call here)

    // Save search term state to React Hooks
    setSearches(searches => [...searches, query])
  }
  
  // ...
  
```



