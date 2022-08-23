## Things I want to know more about

## Provider Pattern with React Context API
React’s provider pattern is a powerful concept. React uses provider pattern in Context API to share data across the tree descendant nodes. You may not find this useful when you are using plain react. However, this pattern comes handy when you are designing a complex app since it solves multiple problems.

## Components and props in React

While your application might start out with just a single component, as it grows in complexity, you must continually break it up into smaller components. With components, we can isolate individual parts of a larger application, providing a separation of concern. If anything in your application breaks, you can easily identify where things went wrong using fault isolation.

However, components are also meant to be reusable. You want to avoid duplicate logic and prevent over-abstraction. Reusing components comes with the benefits of DRY code; components usually have some data or functionality that another component needs, for example, to keep components in synchronization. In React, we can use props to make our components communicate.

Components are like JavaScript functions that can accept any number of arguments. Ideally, a function’s arguments are used for its operation. I like to think of a function as a block of code that performs a function with either zero or any number of arguments passed to it. For example, take the following function `sum` that adds two numbers, `a` and `b`:

```js
function sum(a, b) {
  return a + b;
}
```

Executing the function is fairly straightforward:

```js
console.log(sum(1, 2)); // 3
```

In React components, these arguments are called props, short for properties. An `ErrorMessage` can look something like:

```js
function ErrorMessage(props) {
  return (
    <div className='error-message'>
      <h1> Something went wrong </h1>
      <p> {props.message} </p>
    </div>
  );
}
```

Because `ErrorMessage` will be reused many times across the app, it will pass a different `message` in its props. However, this is just one component, and this example doesn’t clarify where the `message` prop came from, which is important for us to know.


[Hooks and Context example](https://medium.com/swlh/snackbars-in-react-an-exercise-in-hooks-and-context-299b43fd2a2b)