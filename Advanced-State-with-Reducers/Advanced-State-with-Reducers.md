## Things I want to know more about

* An alternative to useState. Accepts a reducer of type (state, action) => newState, and returns the current state paired with a dispatch method.

- const [state, dispatch] = useReducer(reducer, initialArg, init);

- useReducer is usually preferable to useState when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one. useReducer also lets you optimize performance for components that trigger deep updates because you can pass dispatch down instead of callbacks.

- Example:

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
    </>
  );
}

- React guarantees that dispatch function identity is stable and won’t change on re-renders. This is why it’s safe to omit from the useEffect or useCallback dependency list.


- What are two ways to set the initial state?
- There are two different ways to initialize useReducer state. You may choose either one depending on the use case. The simplest way is to pass the initial state as a second argument:

const [state, dispatch] = useReducer(
reducer,
{count: initialCount}
);

- Lazy initialization: You can also create the initial state lazily. To do this, you can pass an init function as the third argument.

- Bailing out of a dispatch: If you return the same value from a Reducer Hook as the current state, React will bail out without rendering the children or firing effects. (React uses the Object.is comparison algorithm.)

- What does useReducer return?
- useReducer returns an array that holds the current state value and a dispatch function to which you can pass an action and later invoke it. While this is similar to the pattern Redux uses, there are a few differences.

- Bailing out of a dispatch
- If you return the same value from a Reducer Hook as the current state, React will bail out without rendering the children or firing effects.

- React uses the Object.is comparison algorithm.

- Note that React may still need to render that specific component again before bailing out. That shouldn’t be a concern because React won’t unnecessarily go “deeper” into the tree. If you’re doing expensive calculations while rendering, you can optimize them with useMemo.


[useReducer hook](https://reactjs.org/docs/hooks-reference.html#usereducer)<br>
[Ultimate Guide to useReducer](https://blog.logrocket.com/guide-to-react-usereducer-hook/)<br>