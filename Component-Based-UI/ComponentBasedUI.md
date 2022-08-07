## Things I want to know more about

# react hello world

* What are the building blocks of a React app?
 - Elements.
 - Components.


* What is the difference between an element and a React component?
 - Elements are the smallest building blocks of React apps.

- An element describes what you want to see on the screen:

--- 
const element = <h1>Hello, world</h1>;
---

- Unlike browser DOM elements, React elements are plain objects, and are cheap to create. React DOM takes care of updating the DOM to match the React elements.

- components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.

---
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
---


* What are some advantages of React’s component based architecture?
1. Instant updates without page reloads.
2. Use conditional statements within the JSX.
3. Reuse the same components.
4. Update just one component.
5. The code is nice and stable.

# introducing JSX

* What is JSX and why do we use it?
- React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.


* Describe the process of embedding JavaScript expressions in JSX.
- JSX will only accept expressions between curly braces. The curly braces tell our transpiler to process what is between the curly braces as normal JavaScript. Note we cannot write full statements as we might expect, only bits of JavaScript that return a value. Here are a few common types of expressions you may use:

1. Variable and object values
2. Function calls and references
3. Expressions and operators
4. Loops and iteration

* Is it safe to embed user input in JSX? Explain.
---
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
---

- By default, React DOM escapes any values embedded in JSX before rendering them. Thus it ensures that you can never inject anything that’s not explicitly written in your application. Everything is converted to a string before being rendered. This helps prevent XSS (cross-site-scripting) attacks.


# rendering elements

* Explain what a React Component is to a non-technical friend.
 - React Components Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and return HTML.

- Components come in two types, Class components and Function components, in this tutorial we will concentrate on Function components.


* If changes are made to the UI, what does React update
- React Only Updates What’s Necessary.

React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

[react hello world](https://facebook.github.io/react/docs/hello-world.html)<br>
[introducing JSX](https://facebook.github.io/react/docs/introducing-jsx.html)<br>
[rendering elements](https://facebook.github.io/react/docs/rendering-elements.html)<br>

