# Reading Notes
## Class 10
_____________________________________________________________________________________________________________________________________


### Understanding the call stack

- The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack

- The call stack is primarily used for function invocation (call). Since the call stack is single, function(s) execution, is done, one at a time, from top to bottom. It means the call stack is synchronous.

- In Asynchronous JavaScript, we have a callback function, an event loop, and a task queue. The callback function is acted upon by the call stack during execution after the call back function has been pushed to the stack by the event loop.

- At the most basic level, a call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call).

- the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns

```
function firstFunction(){
  throw new Error('Stack Trace Error');
}

function secondFunction(){
  firstFunction();
}

function thirdFunction(){
  secondFunction();
}

thirdFunction();
```

- When the code is run, we get an error. A stack is printed showing how the functions are stack on top each other. Take a look at the diagram.

![error](https://cdn-media-1.freecodecamp.org/images/zOINLHPC8E56ac8yyINYOFWeImsjM2Wk2rdU)

![call stack](https://cdn-media-1.freecodecamp.org/images/QgR2uIk7tW0YNz0Xm8g0jAPeRFI0e4sCejsv)


### JavaScript error messages

- the first thing that indicates you that something is wrong with your code is the (in)famous error message that the one we saw just moments ago, it usually appears on your console (being developer tools of the browser, terminal or whatever else you are using).

- testing is automatically called since it’s an IIFE (immediately Invoked Function Expression)

- obj variable is declared with the function add (using ES6 shorthand for functions in objects, it would be the same having var obj = { add: add }
- the function add is called from the obj variable with two strings has parameters, there are added which makes them “12” in this scenario and then split is called before returning [“1”, “2”]

- the function add is called again, this time with number, the values are added making it 3 but then, split (which is not available for number type variables) is called which makes an error being thrown
