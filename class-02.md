# Reading Notes
## Class 02
_____________________________________________________________________________________________________________________________________


### Introduction to React

### State and Lifecycle

- to encapsulate the clock and make it reusable. Also to set up its own timer and update itself

```
unction Clock(props) {
  return (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {props.date.toLocaleTimeString()}.</h2>
    </div>
  );
}

function tick() {
  ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('root')
  );
}

setInterval(tick, 1000);

```

- the fact that the Clock sets up a timer and updates the UI every second should be an implementation detail of the Clock. We want to write this once and have the Clock update itself

```
ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

- To implement this, we need to add “state” to the Clock component. State is similar to props, but it is private and fully controlled by the component.

- You can convert a function component like Clock to a class in five steps:
1. Create an ES6 class, with the same namem that extends React.Component.
2. Add a single empty method called render().
3. Move the body of the function into the render() method.
4. Replace props with this.props in the render() body.
5. Delete the remaining empty function declaration. 

```
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

- Clock is now defined as a class rather than a function.

- Adding local state to a class

1. Replace this.props.date with this.state.date in the render() method:

```
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

2. Add a class constructor that assigns the initial this.state:

```
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

- pass props to the base constructor:
```
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
 ```
- Class components should always call the base constructor with props.

3. Remove the date prop from the <Clock /> element:

```
ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

later add the timer code back to the component itself.


```
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);

```

### Adding Lifecycle Methods to a Class




