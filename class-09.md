# Reading Notes
## Class 09
_____________________________________________________________________________________________________________________________________



### Concepts of Functional Programming in Javascript

- Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data

the first fundamental concept we learn when we want to understand functional programming is pure functions.
- It returns the same result if given the same arguments (it is also referred as deterministic)
- It does not cause any observable side effects


```
let PI = 3.14;

const calculateArea = (radius, pi) => radius * radius * pi;

calculateArea(10, PI); // returns 314.0
```
- always pass thePI value as a parameter to the function. So now we are just accessing parameters passed to the function. No external object

- If our function reads external files, it’s not a pure function — the file’s contents can change.
- Any function that relies on a random number generator cannot be pure.
-  mutability is discouraged in functional programming.


Pure functions benefits
- The code’s definitely easier to test. We don’t need to mock anything. So we can unit test pure functions with different contexts
- Given a parameter A → expect the function to return value B
- Given a parameter C → expect the function to return value D

A simple example would be a function to receive a collection of numbers and expect it to increment each element of this collection.

```
let list = [1, 2, 3, 4, 5];

const incrementNumbers = (list) => list.map(number => number + 1);
```

- When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.


The idea of functions as first-class entities is that functions are also treated as values and used as data. Functions as first-class entities can:
- refer to it from constants and variables
- pass it as a parameter to other functions
- return it as result from other functions

When we talk about higher-order functions, we mean a function that either:
- takes one or more functions as arguments, or
- returns a function as its result


### Refactoring Javascript for Readability

straightforward to implement methods that can lead to easier to read code.

- Return early from functions:

```
function showProfile(user) {
  if (user.authenticated === true) {
    // ..
  }
}

// Refactor into ->

function showProfile(user) {
  // People often inline such checks
  if (user.authenticated === false) { return; }
  // Stay at the function indentation level, plus less brackets
}

```


Cache variables so functions can be read like sentences:

```
function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    for (let j = 0; j < continents[i].length; j++) {
      for (let k = 0; k < continents[i][j].tags.length; k++) {
        if (continents[i][j].tags[k] === name) {
          return continents[i][j].id;
        }
      }
    }
  }
}

// Refactor into ->

function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    const group = continents[i]; // This code becomes self-documenting
    for (let j = 0; j < group.length; j++) {
      const tags = group[j].tags;
      for (let k = 0; k < tags.length; k++) {
        if (tags[k] === name) {
          return group[j].id; // The core of this nasty loop is clearer to read
        }
      }
    }
  }
}

```

Check for Web APIs before implementing your own functionality:

```
function cacheBust(url) {
  return url.includes('?') === true ?
    `${url}&time=${Date.now()}` :
    `${url}?time=${Date.now()}`
}

// Refactor into ->

function cacheBust(url) {
  // This throws an error on invalid URL which stops undefined behaviour
  const urlObj = new URL(url);
  urlObj.searchParams.append('time', Date.now); // Easier to skim read
  return url.toString();
}

```

